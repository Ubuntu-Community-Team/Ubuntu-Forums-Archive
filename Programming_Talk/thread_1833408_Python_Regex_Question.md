---
title: "Python Regex Question"
date: 2011-08-26
forum: Programming Talk
---

### Post by shawnjones on 2011-08-26
Hello everyone,

I am putting together a script that scrapes data from a web page and then writes that data to a file. Easy enough, right? The data is a list of socks servers and the file will eventually be proxychains.conf. The idea is to run this script everytime I wish to have a fresh list of servers in my proxychains. 

The code is very messy, but here is what I have so far. 

```
import urllib2
from BeautifulSoup import BeautifulSoup
import re

base_url = "http://www.socks5list.com/"
#data = urllib.urlopen(base_url)
data = open("/home/shawn/dev/default.htm")
text_file = open("/home/shawn/dev/write_text.txt", "w")

soup = BeautifulSoup(data)
listOut = soup.find(attrs= {"class" : "entry"})
a = listOut.textarea
b = a.string
ips = re.findall(r'(?:[\d]{1,3})\.(?:[\d]{1,3})\.(?:[\d]{1,3})\.(?:[\d]{1,3})\:(?:[\d]{1,4})', b)
port = re.findall('(?:[\:])(?:[\d]{1,4})', b)
clean_port = re.sub("\:", " ", port)
country = re.findall(r'(?:[\t])[A-Z][A-Z]', b)

#for x in range (len(ips)):
for x in range (10):
    this = ips[x]
    that = country[x]
    print this, that
print clean_port[0]
lines = ["#dynamic_chain\n",
         "strict_chain\n",
         "#random_chain\n",
         "#chain_len = 2\n",
         "#quiet_mode\n",
         "#proxy_dns\n",
         "tcp_read_time_out 15000\n",
         "tcp_connect_time_out 8000\n",
         "[ProxyList]\n"]
text_file.writelines(lines)
text_file.write(ips[0]) # eventually add all of the ip's, here just the first
text_file.close()
```

What I need to do is strip the ':' from between the ip address and the port number. Basically convert the colon to a whitespace so that it will work with proxychains. For those who are not familiar with the proxychains.conf file what it is expecting is:
```
socks5 127.0.0.1 1234
```
So I need to remove the colon:
```
socks5 127.0.0.1:1234
```

The line that I have been working with to do that is ```
port = re.findall('(?:[\:])(?:[\d]{1,4})', b)
```

which does isolate the port from the ip address, but it includes the colon. I looks like this ```
:1080
``` when what I need is ```
1080
```

Is there a way to match a pattern in the regex but omit the initial pattern (in this case, look for the ':' and print everything else after it but not including the ':')

Thanks for the help,
Shawn

---

### Post by Smart Viking on 2011-08-26
```
>>> "socks5 127.0.0.1:1234".replace(":"," ",1)
'socks5 127.0.0.1 1234'

```?

---

### Post by ofnuts on 2011-08-26
Move the parenthesis to after the colon, so that the group only contains the port. 

Side note: I would use one singular regexp for the whole thing and extract IP and port (and other info) all at the same time. For instance:
```

url='trash 111.222.333.444:6666 trash 11.22.33.44:99 trash'

urlre='\D(\d{1,3}(?:\.\d{1,3}){3}):(\d{1,5})'

all=re.findall(urlre,url)

print all
[B]
[('111.222.333.444', '6666'), ('11.22.33.44', '99')][/B]

```

---

