---
title: "Curl"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by jimbo12d on 2008-06-16
Hi, I have apache, php5, and mysql running. I have a forum running and it all works. I cant find any tutorials to get curl to work with these. I did "sudo apt-get install curl" and it is installed. But it doesn't seem to work with the other server programs. I know there was something I did to make php and mysql work with apache (but I don't remember).

What should I do to make them work together? I already tried restarting the server. The reason I ask is to get glype to work.

Thanks

---

### Post by cariboo on 2008-06-16
Here is a link to the curl man page:

[http://curl.haxx.se/docs/manual.html](http://curl.haxx.se/docs/manual.html)

Jim

---

### Post by juliakm on 2010-03-16
Took me way to long to realize that while cURL was installed, I actually wanted the php5-curl package. 

```
sudo apt-get install php5-curl 
```

---

### Post by Choc_Salties on 2010-10-27
Thanks Juliakm, your answer was exactly spot-on for what i needed, thanks!

---

