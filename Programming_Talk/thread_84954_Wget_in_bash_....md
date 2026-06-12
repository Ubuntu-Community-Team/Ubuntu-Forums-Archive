---
title: "Wget in bash ..."
date: 2005-11-01
forum: Programming Talk
---

### Post by dbee on 2005-11-01
Having some wget troubles ... it can't find the index.html pages of the site I'm trying to download off. And yes the index.html file is definitely there and I have tried it with other sites.

```

wget -r -l 2 -v -np -O raw.txt http://www.webpage.com

```

The code returns this only ...

```

root@ubuntu:/home/babo/Desktop/spider_proj # ./spider
--15:09:01--  http://www.websie.com/xx/xx
           => `raw.txt'
Resolving www.website.com... 207.171.1.2
Connecting to www.website.com[207.171.1.2]:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.website.com/xxx/xxx/ [following]
--15:09:02--  http://www.website.com/xxx/xxx/
           => `raw.txt'
Connecting to www.website.com[207.171.1.2]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [      <=>                            ] 98,655        59.67K/s

15:09:04 (59.61 KB/s) - `raw.txt' saved [98,655]

Loading robots.txt; please ignore errors.
--15:09:04--  http://www.website.com/robots.txt
           => `raw.txt'
Connecting to www.website.com[207.171.1.2]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:09:05 ERROR 404: Not Found.

www.website.com/xxx/xxx/index.html: No such file or directory

FINISHED --15:09:05--
Downloaded: 98,655 bytes in 1 files

```

---

