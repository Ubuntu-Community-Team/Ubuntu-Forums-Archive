---
title: "trying to install xmms and.."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by fignig on 2008-05-10
pete@pete:~$ sudo aptitude install xmms
[sudo] password for pete: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for xmms
No candidate version found for xmms
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   

does this mean i already have xmms? then why can i not run it?

---

### Post by shifty_powers on 2008-05-10
nope it means it is not in the repositories you have enabled for some reason.

edit: seems to have moved onto xmms2

try

```
sudo apt-get install xmms2
```

edit again: yup tried on my command line and xmms is obsolete according to apt ;) try xmms2 :D

---

### Post by Xiong Chiamiov on 2008-05-10
You don't already have it installed; if you did, it would tell you you have the latest version.

Do you have all the [extra repositories installed]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")?

EDIT: [maybe better link]("http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

---

### Post by shifty_powers on 2008-05-10
nah, like i said, xmms has been taken out of the normal repos because it has been replaced by xmms2 ;)

---

### Post by Xiong Chiamiov on 2008-05-10
> **shifty_powers said:**
> nah, like i said, xmms has been taken out of the normal repos because it has been replaced by xmms2 ;)
Ah, I see.  Though, in my defense, I was still typing while you were posting.

---

### Post by shifty_powers on 2008-05-10
heh, yes, people are very quick to reply in these forums. that's something i've always loved about ubuntu and linux in general, but especially ubuntu, and thats the community around it ;)

---

### Post by Malta paul on 2008-05-10
I presume you are using Ubuntu 8-04 as 'shifty_powers' said Xmms will not work,Xmms2 will.
Xmms did worked with Gusty. But has not been updated for a long time.
[http://www.xmms.org/](http://www.xmms.org/)

---

### Post by wevsler on 2008-05-10
Have you tried Audacious its probably the nearest replacement to xmms. Small fast media player

---

