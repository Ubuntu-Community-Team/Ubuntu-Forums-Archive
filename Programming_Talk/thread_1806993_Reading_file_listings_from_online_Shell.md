---
title: "Reading file listings from online Shell"
date: 2011-07-18
forum: Programming Talk
---

### Post by bcooperizcool on 2011-07-18
Is it possible to read a folder from online hosting using shell?   What I would like to do it get the info from online into a text file, then when you enter in something that is the name of a file in that folder online, it will download it.

Example of contents of file created by listing:
```
File.txt
      Waffle.deb
      README.txt
```

Just that sort of thing.


Also, this would be done on an iPhone/iPod touch, so please keep that in mind ;)  (jailbroken of course)

Thanks!

---

### Post by Habitual on 2011-07-18
```
ssh user@host.com cat file.ext
```

---

### Post by bcooperizcool on 2011-07-18
> **Habitual said:**
> ```
ssh user@host.com cat file.ext
```


Is that for reading the file online?    Say the web server has a folder that anyone can access, such as waffle.com/openfolder

the contents of files in that folder would be 
```
File1.pdf
      Cookie.deb
      Somethingelse.txt
```

I would like to get a listing of that folder from online, into a file I specify.   Then, how do I download files I know the name of from that folder to a location on the device?

Thanks for the response though!  :)

---

