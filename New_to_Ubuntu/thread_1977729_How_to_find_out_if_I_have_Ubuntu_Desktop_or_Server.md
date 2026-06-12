---
title: "How to find out if I have Ubuntu Desktop or Server Version?"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by graphicpower on 2012-05-10
I have download Ubuntu 10.04 LTS and installed it, using the option **Erase and ue the entire disk** ..  and just Click, Click until the end ...
 
I am wondering, how can I know which version or class of Ubuntu I am using!!
 
[COLOR=red]Is it Desktop or Server ?!   :confused:[/COLOR]

---

### Post by CharlesA on 2012-05-10
What version did you download and burn to a cd?

Desktop has a GUI, server does not.

---

### Post by jerome1232 on 2012-05-10
> **graphicpower said:**
> I have download Ubuntu 10.04 LTS and installed it, using the option **Erase and ue the entire disk** ..  and just Click, Click until the end ...
 
I am wondering, how can I know which version or class of Ubuntu I am using!!
 
[COLOR=red]Is it Desktop or Server ?!   :confused:[/COLOR]

Did you have a graphical installer? Desktop.

Was it a Blue screen reminiscent of 1990? Server.

edit: That fact that you said "click" actually decides it, you installed the desktop version. There's no clicking in the server installer.

---

### Post by graphicpower on 2012-05-10
I don't remember which version I have downloaded
 
 
[SIZE=2]uname  a[/SIZE]
**Linux MyHost 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux**

[SIZE=2]uname -r[/SIZE]
** 2.6.32-41-generic**

 
Yes, I have used a GUI during the installation, exactly the same what is documented in this link:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
 
 
THANK YOU Both

---

### Post by graphicpower on 2012-05-10
Here is another way ,,, by: [[COLOR=royalblue]woolmilkporc[/COLOR]]("http://www.experts-exchange.com/M_1730518.html")
[COLOR=royalblue] [/COLOR]
 
**dpkg --get-selections | grep linux-image | grep -v deinstall**
 
 
linux-image-...... -[COLOR=red]generic [/COLOR]# = **desktop**
 
linux-image-.......-[COLOR=red]server[/COLOR] # = **server**

---

### Post by CharlesA on 2012-05-10
That doesn't work with 12.04, but it does work for versions up until it.

Easier way to check is to run:

```
uname -a
```

---

### Post by CatKiller on 2012-05-11
Just so you know, there isn't any fundamental difference between the two versions; it's not like Microsoft's market segmentation efforts. The server version comes with server-y applications & no GUI. The desktop version comes with a GUI and desktop-y applications. You can install any application from one on the other, including a GUI.

---

### Post by sadaruwan12 on 2012-05-11
If you had a graphic dialogs to guide you through that means you've the desktop version of Ubuntu not the server version.

---

### Post by 3rdalbum on 2012-05-11
Ubuntu 10.04 is getting pretty old now... are you aware that there have been four newer versions since 10.04?

The current version of Ubuntu is 12.04.

If you look on Google for instructions on how to upgrade from 10.04 to 12.04, you will be able to do this without reinstalling.

---

### Post by CharlesA on 2012-05-11
> **3rdalbum said:**
> Ubuntu 10.04 is getting pretty old now... are you aware that there have been four newer versions since 10.04?

The current version of Ubuntu is 12.04.

If you look on Google for instructions on how to upgrade from 10.04 to 12.04, you will be able to do this without reinstalling.
Yep. On a clean install there shouldn't be any problems with upgrading either.

---

### Post by grahammechanical on 2012-05-11
When upgrading the update manager will tell you that is is going to take hours. But the downloading of packages takes less than 15 mins (unless you are on dial up)  and the estimated 4 hours quickly drops to less the 90 minutes.

I upgraded my 11.10 to 12.04 early this morning. All done in just over an hour. No problems.

I have even tested a few times the upgrade path from 10.04 to 12.04. It will not take long and should work flawlessly. Especially as this is a new, default 10.04 install.

Regards.

---

### Post by graphicpower on 2012-05-11
I am not sure if we can upgrade to 12.04 LTS as the curent 10.04 LTS is a dedicated host configured by our system integrator ..
 
I believe we will have to live with it for some time 
 
THANK U All

---

### Post by jerome1232 on 2012-05-11
Nothing wrong with 10.04 LTS, It's still supported for another year.

---

