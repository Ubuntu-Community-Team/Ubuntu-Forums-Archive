---
title: "Recover .xsessions-errors from redirect?"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by Peterlorre on 2013-07-31
Hi All, 

I have a somewhat embarrassing problem and I'm not sure how to solve it. 

When I was much newer to Ubuntu, I had a lot of trouble with my .xsessions-errors file filling up and googled a lot to figure out what to do with it. Being a bit uncritical at the time, I ran across lots of pages advising how to redirect the file to dev/null without realizing that this severely limits your ability to troubleshoot problems later. I foolishly followed the instructions on these pages without really understanding what I was doing, and now my .xsessions-errors redirects to dev/null as expected. Now I'd like to be able to look at this file for troubleshooting and am not sure how to do so. As far as I can tell they are linked symbolically, but I am not able to remove the symbolic links through the usual ways (or perhaps they are rebuilt immediately after I do so).

```
russ@Daedalus:~$ ls -la
total 420
drwxr-xr-x 59 russ russ     4096 Jul 30 14:08 .
drwxr-xr-x  3 root root     4096 Aug 10  2012 ..

...

-rw-------  1 russ russ       53 Jul 24 09:53 .Xauthority
lrwxrwxrwx  1 russ russ        9 Jul 24 09:53 .xsession-errors -> /dev/null
lrwxrwxrwx  1 russ russ        9 Jul  2 16:48 .xsession-errors.old -> /dev/null
-rw-------  1 russ russ        0 Jun 20 03:13 ZoLDlq
```


Can anyone suggest a course of action to fix this? I assure you that I am well aware of how stupid this was, and I am wearing my virtual hair shirt as I type this. Running 12.04 LTS.

---

### Post by powder on 2013-07-31
Why can't you remove the symbolic links? How are you trying to remove them?

---

### Post by VMC on 2013-07-31
Could _**[this]("http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable")**_ be what your looking for.

I never knew this could be done. There's something wrong somewhere and best to try an locate it. I know because I am/was having xsession filling using Kubuntu.

---

### Post by Peterlorre on 2013-07-31
powder: 

cd ~
rm .xsessions-errors

VMC: 

Thanks, I'll start going through the various fixes listed there and see if I can figure out what I did.

---

