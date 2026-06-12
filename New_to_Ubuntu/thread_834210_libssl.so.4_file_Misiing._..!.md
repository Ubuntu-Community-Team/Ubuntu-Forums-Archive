---
title: "libssl.so.4 file Misiing. ..!"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by ganyboy on 2008-06-19
Hi ...
i am having problem installing my internet connection.
i downloaded the Broadband client from my ISP and tried installin it. i Installed it sucuessfully.

when i tried connecting it gives  me error 


Error while loading shared library : libssl.so.4 cannot open 
shared object file : No such file or directory 


well i referred to some of the posts related to this problem
they give the link of this file which is a RPM file and then tell
to convert it to .DEb file by using ALien software

since i am new to Ubuntu and trying to Get connected to Internet
i dont have alien software in my Ubuntu 7.10

plz give me a link frm where i can download this field also it will be gr8 if u showed me the steps to start my Internet conection

   ..waiting for reply..!

---

### Post by ganyboy on 2008-06-19
i wanna fix this issue..Plz reply ...!

---

### Post by druid23 on 2008-06-19
Hi, it looks as if you should be able to create symbolic links to the version of that library you have installed.

A quick search of the forums revealed this post (amongst others) which should help you along. It also suggests that once you have resolved libssl.so.4 their may be one or two others which it covers as well.

Have a look at:
[http://ubuntuforums.org/showthread.php?t=460874](http://ubuntuforums.org/showthread.php?t=460874)

---

### Post by hyper_ch on 2008-06-19
better is to find out in what package that file is:

(1) install apt-file
```

sudo apt-get install apt-file

```

(2) update the apt-file db
```

sudo apt-file update

```

(3) search the apt-file db
```

apt-file search KEYWORD

```
e.g.
```

apt-file search libssl.so.4

```

---

### Post by Prakash Premkumar on 2010-06-12
ya.. thanks for the info..creating a soft link for the libssl.so.4 worked..
i had the same problem while installing my broadband client.. can u please tell me.. what libssl or libcrypto files are

---

