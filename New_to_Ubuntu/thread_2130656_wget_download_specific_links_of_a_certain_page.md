---
title: "wget: download specific links of a certain page"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by Si1414 on 2013-03-30
Hi all,

Is it possible to download specific links with wget. Suppose I want to download all files of "www.example.com/page2", which start with "dl.example.com".
I can use the following code to download specific file types, e.g. jpg, but I am not sure how to specify the "dl.example.com"?

```
wget -r -p -A.jpg http://www.example.com/page2
```

Thanks for your help.

---

### Post by matt_symes on 2013-03-30
Hi

Do you have a more concrete example to work with ? (as opposed to [www.example.com](www.example.com) and dl.example.com)

You may get a better help as i'm not really sure if i understand what you want.

The -A option can take regular expressions.

> -A acclist --accept acclist                                                                                                    
       -R rejlist --reject rejlist                                                                                                    
           Specify comma-separated lists of file name suffixes or patterns to accept or reject. Note that if any of the wildcard      
           characters, *, ?, [ or ], appear in an element of acclist or rejlist, it will be treated as a pattern, rather than a       
           suffix.

Kind regards

---

### Post by schragge on 2013-03-30
@**matt_symes** IIRC, those patterns are shell globs, not regular expressions.

@**OP** If you cannot accomplish what you want with *wget*'s -A/-R, have a look at [curl]("http://manpages.ubuntu.com/manpages/precise/en/man1/curl.1.html"). It allows to do some neat things with URLs like
```
curl 'http://{one,two}.host[1-5].com' -o "#1_#2"
```

---

### Post by matt_symes on 2013-03-30
Hi

> IIRC, those patterns are shell globs, not regular expressions.

A fair point. I'll be tighter with my definitions and language.

Kind regards

---

### Post by sandyd on 2013-03-30
> **Si1414 said:**
> Hi all,

Is it possible to download specific links with wget. Suppose I want to download all files of "www.example.com/page2", which start with "dl.example.com".
I can use the following code to download specific file types, e.g. jpg, but I am not sure how to specify the "dl.example.com"?

```
wget -r -p -A.jpg http://www.example.com/page2
```

Thanks for your help.
some crafty work, but
```

wget  -qO- http://www.example.com | grep -i "http://dl.example.com" | awk -F"http://" '{print $2}' | awk -F'"' '{print $1}' | wget -i -
```

if you want to download links only```

wget  -qO- http://www.example.com | grep -i '<a href="http://dl.example.com"' | awk -F"http://" '{print $2}' | awk -F'"' '{print $1}'| wget -i -
```

There are many other combinations...

Downloading images...
```
wget  -qO- http://www.example.com | grep -i '<img' | awk -F'<img src="' '{print $2}' | awk -F'"' '{print $1}' | grep dl.example.com | wget -i -
```

but all of them will need tuning because all sites are different

---

