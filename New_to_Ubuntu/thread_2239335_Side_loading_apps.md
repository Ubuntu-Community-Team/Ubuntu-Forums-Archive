---
title: "Side loading apps?"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by chris272 on 2014-08-13
I have an old pc running lubuntu at home. There is no internet at home. Is there any way, other than taking the whole tower somewhere with internet, to install applications? I have a laptop running the same version of lubuntu. I took the tower to somebody's house to install lubuntu sui it is updated, but I would like to just use the laptop in the future. Is there a method where I can get the install file (like an .apk) and move it with a flash drive? Thanks all.

---

### Post by stalkingwolf on 2014-08-13
i think what you are looking for is apt on cd.  run it on the laptop then use the cd to install to the desktop.

---

### Post by Impavidus on 2014-08-13
In synaptic you can create a download script for the package files you need, which you can take to a different computer for the actual download. I'm not sure about the list of available software + updates, but I think you can get them via usb stick too.

---

### Post by ian-weisser on 2014-08-13
> **chris272 said:**
> Is there any way, other than taking the whole tower somewhere with internet, to install applications?

The apt-zip, aptoncd, and apt-offline packages all do this, plus Synaptic's scripting. And you can do it manually - transferring packages from /var/cache/apt/archives among machines.
That's five different methods.
 
> **chris272 said:**
> I have a laptop running the same version of lubuntu.

Great. Then all five will work easily.

> **chris272 said:**
> I took the tower to somebody's house to install lubuntu

Well, I suppose that's a sixth way to do it.

> **chris272 said:**
> I can get the install file (like an .apk) and move it with a flash drive?

No, you can't get an install file. Ubuntu uses *package management*, not install files. There's a big difference.
Yes, you can trivially move packages with a flash drive. That's what three of of the six methods do.

Look at those methods on your laptop and decide which one you want to try. You're not locked into any of them; you can change at any time.

---

### Post by chris272 on 2014-08-13
Great, I can't wait to try this. I think I will experiment with the first the methods first. This reminds me of the 'old' days with Windows, where I could copy a directory onto floppy and paste on another computer. When the whole 'registry' thing out that to an end, I was sad. 
So, if I move the required packages for an application, it will function? And those packages are in /var/cache/apt/archives ? That should be a piece of cake. 
I won't be able to do any scripting. I'm still learning the command line. Ok, unless somebody can share the script. If it's as simple as 'mv' _  _, I cab handle that in bash. But script implies to me several strings off command that I probably haven't learned yet. 

Thanks for all help folks!

---

### Post by tea for one on 2014-08-13
> **chris272 said:**
> This reminds me of the 'old' days with Windows, where I could copy a directory onto floppy and paste on another computer.!

If you have to use a Windows PC to download Ubuntu software, here is a useful link:-

[http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/)

---

### Post by chris272 on 2014-08-13
Thanks for that link. I have, however, ditched all my Windows for Linux. I'm trying to convert people in my family now and studying command line resources every night. So I'm going to do this without involving Windows!

---

### Post by Impavidus on 2014-08-13
> **chris272 said:**
> 
So, if I move the required packages for an application, it will function? And those packages are in /var/cache/apt/archives ? That should be a piece of cake. 

If you move the package files to /var/cache/apt/archive they won't be installed yet. You can then use the package manager to install packages and it will inform you that it doesn't have to download any more package files, so you can continue installing without network connection.

---

### Post by chris272 on 2014-08-13
Great, thanks

---

### Post by chris272 on 2014-08-16
I just wanted to add...
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
this reference that gives step-by-step explanation of everything mentioned above. 
Thanks again!

---

