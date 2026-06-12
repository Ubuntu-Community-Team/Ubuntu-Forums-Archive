---
title: "Auto Replace Help!"
date: 2009-07-30
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-07-30
What's Up?

OK, So im gonna explain this the bets i can, My goal is to append a word onto the end of a url, via terminal, so far i use  a various sequence of SED commands. To put it into words what those commands do. after obtaining the url, the executable text file then searched for "m/" and replaces it with "m/append.txt" the m is from .com/"

So i have a way that is currently working to append a word on the _root_ of the webpage, But, some of the urls im working with use folders.

```
Example
http://www.nonrealwebsite.com/folder/
```

And their is my problem, Since their is a folder in this url, my "bot" replaces the wrong section of the url, the end result is 
```
http://www.nonrealwebsite.com/append.txt/folder/
```

All the urls are are seprate lines, so if their was a way to tell my file to replace the last "/" on everyline with "/append.txt " then id be in business. unfortunately as for as i know their isent a way.

Anyone know of either a way around this, or perhaps another method?

Thanks Bye.

---

### Post by kaibob on 2009-07-30
The following sed command will do what you want:

```
sed 's/$/append.txt/'
```

To see this, enter the following in a terminal window:

```
echo http://www.nonrealwebsite.com/folder/ | sed 's/$/append.txt/'
```

> kaibob@dell:~$ echo [http://www.nonrealwebsite.com/folder/](http://www.nonrealwebsite.com/folder/) | sed 's/$/append.txt/'
[http://www.nonrealwebsite.com/folder/append.txt](http://www.nonrealwebsite.com/folder/append.txt)

---

### Post by Chamillionaire2 on 2009-07-30
> **kaibob said:**
> The following sed command will do what you want:

```
sed 's/$/append.txt/'
```

To see this, enter the following in a terminal window:

```
echo http://www.nonrealwebsite.com/folder/ | sed 's/$/append.txt/'
```

Ah i see thanks, one last thing to throw into the mix, the urls may have index.html or index.php, Some may even have differ their name, i could before hand search and remove any index.html's their may be, However some which may differ their names that I may have to miss.

is their perhaps a way around that?

---

### Post by Chamillionaire2 on 2009-07-30
Bumpers!

---

### Post by unutbu on 2009-07-30
Save this as ~/bin/test.py

[PHP]#!/usr/bin/env python
from urlparse import urlsplit,urlunsplit
import sys
for url in sys.stdin:
    url=url.strip()
    url_tuple=urlsplit(url)
    path=url_tuple.path
    idx=path.rfind('/')
    if idx>=0:
        path=path[:idx]
    path+='/append.txt'
    print(urlunsplit((url_tuple.scheme,url_tuple.netloc,path,url_tuple.query,
                      url_tuple.fragment)))
[/PHP]
Use it like this:```


% cat URLS
http://www.nonrealwebsite.com/
http://www.nonrealwebsite.com
http://www.nonrealwebsite.com/index.html
http://www.nonrealwebsite.com/index.php
http://www.nonrealwebsite.com/folder/
http://www.nonrealwebsite.com/folder/index.html
% test.py < URLS
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/folder/append.txt
http://www.nonrealwebsite.com/folder/append.txt

```
or 
```

% echo http://www.nonrealwebsite.com/folder/index.html | test.py
http://www.nonrealwebsite.com/folder/append.txt

```

---

### Post by Chamillionaire2 on 2009-07-30
> **unutbu said:**
> Save this as ~/bin/test.py

[PHP]#!/usr/bin/env python
from urlparse import urlsplit,urlunsplit
import sys
for url in sys.stdin:
    url=url.strip()
    url_tuple=urlsplit(url)
    path=url_tuple.path
    idx=path.rfind('/')
    if idx>=0:
        path=path[:idx]
    path+='/append.txt'
    print(urlunsplit((url_tuple.scheme,url_tuple.netloc,path,url_tuple.query,
                      url_tuple.fragment)))
[/PHP]
Use it like this:```


% cat URLS
http://www.nonrealwebsite.com/
http://www.nonrealwebsite.com
http://www.nonrealwebsite.com/index.html
http://www.nonrealwebsite.com/index.php
http://www.nonrealwebsite.com/folder/
http://www.nonrealwebsite.com/folder/index.html
% test.py < URLS
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/append.txt
http://www.nonrealwebsite.com/folder/append.txt
http://www.nonrealwebsite.com/folder/append.txt

```
or 
```

% echo http://www.nonrealwebsite.com/folder/index.html | test.py
http://www.nonrealwebsite.com/folder/append.txt

```
Whoa, Looks like some heavy coding is needed, i placed it into the bin folder but when i run "sudo test.py < Finished.txt" i get command test.ty
not found

---

### Post by soltanis on 2009-07-30
That's because ~/bin/ is in your home folder and not in the superuser's path. Solution:

```

cd ~/bin/
ls -l
# confirm that the file exists here with permissions rwxr-xr-x
chmod +x test.py # if it is not executable
sudo ./test.py < ~/path/to/test.txt

```

---

### Post by unutbu on 2009-07-30
Edit: soltanis has got this covered. I'd recommend however not running the script with sudo. Using sudo when unnecessary is (in general) a security risk.

------------------------------------------------------

Hm. Maybe the script has not been made executable:

To make the file executable run:
```

chmod 755 ~/bin/test.py
```

Then try running 
```

test.py < Finished.txt
```

---

