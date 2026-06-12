---
title: "Python requests - code takes minutes to run but work on other platforms than linux."
date: 2019-03-11
forum: Programming Talk
---

### Post by micsku on 2019-03-11
Hello there,
I have small issue with my (very) simple code.
```

import requests

url = "https://api.coinmarketcap.com/v1/ticker/bitcoin"
webObj = requests.get(url)
webJson = webObj.json()
print(webJson[0]["price_usd"])
```

While running with python3 filenamy.py command this code takes minutes to start. Now I'm waiting 10 minutes for this script to run, same code on MacOS and Windows run without a problem. I guess the problem is with coinmarketcap page but I don't know - what kind of problem this is. If I put any other domain in url variable - everything is working fine.

---

### Post by norobro on 2019-03-12
Does adding the following line help?```
import json
```

---

### Post by again? on 2019-03-12
Runs fine here.
```
#!/usr/bin/env python3

import requests

url = "https://api.coinmarketcap.com/v1/ticker/bitcoin"
webObj = requests.get(url)
webJson = webObj.json()
print(webJson[0]["price_usd"])
```

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] /home/glen/scripts/aatest.py**
3907.41865656

```
Try going to web api in your browser.
[https://api.coinmarketcap.com/v1/ticker/bitcoin/](https://api.coinmarketcap.com/v1/ticker/bitcoin/)

---

