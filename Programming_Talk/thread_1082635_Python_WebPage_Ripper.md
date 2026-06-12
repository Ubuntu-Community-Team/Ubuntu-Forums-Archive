---
title: "Python WebPage Ripper"
date: 2009-02-28
forum: Programming Talk
---

### Post by HotelUnderSeige on 2009-02-28
im not really sure where to post but here it is, i coded a webpage ripper in python :D

Instructions:
Extract into your home folder
Then in terminal type sh getsource.sh
link: [http://rapidshare.com/files/200634153/source.tar.gz.html](http://rapidshare.com/files/200634153/source.tar.gz.html)

---

### Post by eightmillion on 2009-02-28
> **HotelUnderSeige said:**
> im not really sure where to post but here it is, i coded a webpage ripper in python :D

Instructions:
Extract into your home folder
Then in terminal type sh getsource.sh
link: [http://rapidshare.com/files/200634153/source.tar.gz.html](http://rapidshare.com/files/200634153/source.tar.gz.html)

You should really upload the .py file if you want to share your program. A .pyc file may not work on other people's computers and not many people are just going to run things blindly. I've depythoned your file, and I have a couple of suggestions. 

```
import urllib 
name = raw_input('name for file? : ')
webpage = raw_input('webpage url? : ')
filehandle = urllib.urlopen(webpage)
f = open(name, 'w')
for lines in filehandle.readlines():
    file = open(name, 'a')
    file.writelines(lines)
    print lines

filehandle.close()

```

You can move "file = open(name, 'a')" out of the loop, since you only have to open it once. In fact you can get rid of the loop altogether. You can just use the read() method on "filehandle" and write the whole thing to a file all at once.

Just for fun, this is one line that's functionally equivalent:
```
python -c 'import urllib;open(raw_input("name for file? : "),"w").write(urllib.urlopen(raw_input("webpage url? : ")).read())'
```

Edit: You might also want to make sure that webpage actually is a valid webpage that urllib can open. Something like this:

```

if not webpage.startswith("http://"):
    webpage = "http://" + webpage

```

---

