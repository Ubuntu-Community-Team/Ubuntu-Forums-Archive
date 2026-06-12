---
title: "corrupted picture from google (wget)"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by joehc on 2014-11-15
Hello, I am fairly new to wget, but I am trying to write my own script. The script should get the first picture from google image based on a searh term.

I use the following:
```
wget -U chrome -O test.jpg http://images.google.com/images?q=hotdog\&as_filetype=jpg
```

It does download a file, but not an image. It appears to be the html file? 

Can any one help?

This is the log from one of my tries:
```
--2014-11-15 20:14:12--  http://images.google.com/images?q=hotdog&as_filetype=jpg
Resolving images.google.com (images.google.com)... 212.10.212.121, 212.10.212.123, 212.10.212.79, ...
Connecting to images.google.com (images.google.com)|212.10.212.121|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://images.google.com/images?q=hotdog&tbm=isch&tbs=ift:jpg [following]
--2014-11-15 20:14:13--  http://images.google.com/images?q=hotdog&tbm=isch&tbs=ift:jpg
Reusing existing connection to images.google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;test.jpg&#8217;


    [  <=>                                                                        ] 38,782       112KB/s   in 0.3s   


2014-11-15 20:14:13 (112 KB/s) - &#8216;test.jpg&#8217; saved [38782]

```

---

### Post by Vaphell on 2014-11-15
it is the code of the search page and looking at it says the results are obfuscated, with no direct links to the source images in plain view.
You'd need to figure out how to extract proper data from the webpage code or find some tool that solves that problem for you.

---

### Post by joehc on 2014-11-16
You're right.. Do you have any idea how you get the first picture?

---

