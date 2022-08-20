## Xadara - Your multi purpose APi 

[![Discord](https://img.shields.io/discord/823720615965622323.svg?style=for-the-badge)](https://discord.gg/UDNcTrBagN)
[![Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/vkxni)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)](https://github.com/alelievr/Mixture/blob/master/LICENSE)

<p align="center">
<img src="https://media.discordapp.net/attachments/967869551293370451/1010519748607483955/Koni_Xadara_54d57904-8c74-4db9-8772-ba87027de4b8.png?width=627&height=627"  alt="xadara" width="210" height="200"/></a>
<p>

### Endpoints

All Endpoints have the same Rate Limit, and are available in the following format:
```
1.) https://xadara.fly.dev/api/ip

2.) https://xadara.fly.dev/api/epoch

3.) https://xadara.fly.dev/api/qr/<url here>

4.) https://xadara.fly.dev/api/geo/<ip here>

5.) https://xadara.fly.dev/api/disposable/<email>
```

1.) Returns the IP of the requester.

2.) Returns the current epoch time.

3.) Returns a QR code of the given url.

4.) Returns the geolocation info of the given IP.

5.) Checks if an email is disposable or not.

> Are there any packages that you can use to make this easier?

Yes, there are. But not for every Endpoint.

Elixir
- Disposable Emails (Mailify) [https://hex.pm/packages/mailify](https://hex.pm/packages/mailify)

- Ranwords (Ranwords) [https://hex.pm/packages/ranwords](https://hex.pm/packages/ranwords)

NodeJS
- Disposable Emails (Mailify) [https://www.npmjs.com/package/mailify](https://www.npmjs.com/package/mailify)

- Ranwords (Ranwords) [https://www.npmjs.com/package/ranwords](https://www.npmjs.com/package/ranwords)

... more soon


### Examples 

JavaScript
```js
const fetch = require("node-fetch");

async getData() {
    const response = await fetch("https://xadara.fly.dev/api/ip");

    const data = await response.text();
    return data;
}

getData().then(console.log);
``` 

Python 
```python
import requests

response = requests.get("https://xadara.fly.dev/api/ip")
print(response.text)
```

Java
```java
import java.net.URL;
import java.net.HttpURLConnection;

public class Main {
    public static void main(String[] args) {
    URL url = new URL("https://xadara.fly.dev/api/ip");
    HttpURLConnection httpConn = (HttpURLConnection) url.openConnection();
    httpConn.setRequestMethod("GET");

    httpConn.setRequestProperty("Accept", "application/json");
       
    InputStream responseStream = httpConn.getResponseCode() / 100 == 2
        ? httpConn.getInputStream()
        : httpConn.getErrorStream();
    Scanner s = new Scanner(responseStream).useDelimiter("\\A");
    String response = s.hasNext() ? s.next() : "";
    System.out.println(response);
}
```

Go 
```go
package main

import (
    "fmt"
    "net/http"
    "net/url"
    "io/ioutil"
)

func main() {
	resp, err := http.Get("https://xadara.fly.dev/api/ip")
    if err != nil {
        fmt.Println(err)
    }

    body, err := ioutil.ReadAll(resp.Body)
    if err != nil {
      log.Fatalln(err)
    }
    sb := string(body)
    log.Printf(sb)
}
```

Perl
```perl
use HTTP::Request;
use LWP::UserAgent;
use URI::Escape;

my $url = "https://xadara.fly.dev/api/ip";

my $req = HTTP::Request -> new(GET => $apiUrl);
my $ua = LWP::UserAgent -> new();

my $res = $ua -> request($req);
print $res -> decoded_content;
``` 

Elixir 
```elixir
defmodule Xadara do
  def getData() do 
    %{body: body} = HTTPoison.get!("https://xadara.fly.dev/api/ip")
    body
  end
end
```

Rust
```rust
use error_chain::error_chain;

error_chain! {
    foreign_links {
        Io(std::io::Error);
        HttpRequest(reqwest::Error);
    }
}

#[tokio::main]
async fn main() -> Result<()> {
    let res = reqwest::get("https://xadara.fly.dev/api/ip").await?;
    
    let body = res.text().await?;
    println!("Body:\n{}", body);
    Ok(())
}
```

Julia
```julia
using HTTP

url = "https://xadara.fly.dev/api/ip"
res = HTTP.get(url)

println(String(res.body))
```

C#
```cs
using System.IO;
using System.Net;

namespace Xadara
{
    class Program {
        static void Main(string[] args) 
        {
            string apiUrl = String.Format("https://xadara.fly.dev/api/ip");

            WebRequest req = WebRequest.Create(apiUrl);

            if (req != null)
            {
                req.Method = "GET";
                req.ContentType = "application/json";
                req.Headers.Add("Authorization");

                using (Stream s = req.GetResponse().GetResponseStream())
                {
                    using (StreamReader sr = new StreamReader(s))
                    {
                        Console.Write(sr.ReadToEnd());
                    }
                }
            }
        }
    }
}
```

Dart 
```dart
import 'package:http/http.dart' as http;


void main() async {
  var url = Uri.parse('https://xadara.fly.dev/api/ip');
  var res = await http.get(url);
  if (res.statusCode != 200) throw Exception('Xadara APi error occurred');
  
  return(res.body);
}

print(main())
``` 

V
```v
import net.http
import net.urllib

fn main() {
    api_url := "https://xadara.fly.dev/api/ip"

    response := http.fetch(
        method: .get,
        url: api_url,
    ) or {
        println(err)
            return
    }

    println(response.text)
}
```

Ruby 
```ruby 
require 'uri'
require 'net/http'

uri = URI('https://xadara.fly.dev/api/ip')
res = Net::HTTP.get_response(uri)
puts res.body if res.is_a?(Net::HTTPSuccess)
``` 

C
```c
#include <curl/curl.h>

int main(int argc, char *argv[])
{
  CURLcode ret;
  CURL *hnd;
  struct curl_slist *slist1;

  slist1 = NULL;
  slist1 = curl_slist_append(slist1, "Accept: application/json");

  hnd = curl_easy_init();
  curl_easy_setopt(hnd, CURLOPT_BUFFERSIZE, 102400L);
  curl_easy_setopt(hnd, CURLOPT_URL, "https://xadara.fly.dev/api/ip");
  curl_easy_setopt(hnd, CURLOPT_NOPROGRESS, 1L);
  curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, slist1);
  curl_easy_setopt(hnd, CURLOPT_USERAGENT, "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.64 Safari/537.36");
  curl_easy_setopt(hnd, CURLOPT_MAXREDIRS, 50L);
  curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "GET");
  curl_easy_setopt(hnd, CURLOPT_FTP_SKIP_PASV_IP, 1L);
  curl_easy_setopt(hnd, CURLOPT_TCP_KEEPALIVE, 1L);

  ret = curl_easy_perform(hnd);

  curl_easy_cleanup(hnd);
  hnd = NULL;
  curl_slist_free_all(slist1);
  slist1 = NULL;

  return (int)ret;
}
``` 

Swift 
```swift
import UIKit

let url = URL(string: "https://xadara.fly.dev/api/ip")!

var request = URLRequest(url: url)

let task = URLSession.shared.dataTask(with: url) { data, response, error in
    if let data = data {
        let image = UIImage(data: data)
    } else if let error = error {
        print("HTTP Request Failed \(error)")
    }
}

task.resume()
```

### Contributing

Unfortunately - due to personal reasons - Xadara isn't open source. 

But don't worry, you can still help by submitting ideas for Endpoints (through issues), fix typos or implement new language examples. 

New, better versions for exisiting languages are also welcome!

© Xadara 2022, [MIT Licence](/LICENSE), Powered by [@vKxni](https://github.com/vKxni).