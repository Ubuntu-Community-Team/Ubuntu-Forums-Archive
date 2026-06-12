---
title: "Getting back to Windows"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by alp2 on 2014-05-20
Hi i installed ubuntu 14.04 yesterday on my windows 8,1 ultrabook however didnt like it that much as you need coding and terminal and things which i dont understand and it made my battery life which was around 5 hours on windows to around 3 hours.

I would like to uninstall and just get back to windows but as i partioned my harddrive i have less space however i want everything back and just like i brought it new.

Please could somebody show a step by step way to uninstall and just get back to windows.

---

### Post by Chayak on 2014-05-20
Since you didn't mention dual boot I'm going to make the logical assumption and say you installed Ubuntu over Windows.  In that case your only recourse is to get a windows 8.1 install disk and re-install the system.

---

### Post by jones quest on 2014-05-20
In case you do have an intact windows partition you can use the following guides:

[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

The example is for windows 7, but the procedure is pretty much identical for windows 8.

---

### Post by alp2 on 2014-05-20
> **Chayak said:**
> Since you didn't mention dual boot I'm going to make the logical assumption and say you installed Ubuntu over Windows.  In that case your only recourse is to get a windows 8.1 install disk and re-install the system.

i did a dual boot which i forgot to mention. I also made a recovery thing for windows on my usb. I just want to get back to everything default just like I bought the laptop.

---

### Post by mörgæs on 2014-05-20
Have you considered giving Ubuntu a week for testing? I'm sure people here are ready to help with whatever problem you encounter.

---

### Post by Mark Phelps on 2014-05-20
You should check on the Windows 8 forum for details (eightforums.com) but I would suggest the following:
1)  Boot into Win8.1 and use Disk Management to remove the Ubuntu partitions
2)  Reboot into Win8.1, select the Advanced boot options, and from there select the Reset option.  That should restore the PC to its original conditition.

But, as I said, I would check with the Windows 8 forums before you do this.

---

### Post by LastDino on 2014-05-20
> **alp2 said:**
> Hi i installed ubuntu 14.04 yesterday on my windows 8,1 ultrabook however didnt like it that much as **you need coding and terminal** and things which i dont understand and it made my battery life which was around 5 hours on windows to around 3 hours.

I would like to uninstall and just get back to windows but as i partioned my harddrive i have less space however i want everything back and just like i brought it new.

Please could somebody show a step by step way to uninstall and just get back to windows.


Not the solution but funnily enough, I didn't even need to open my terminal on 13.10 when I used it for my regular use for around 6 months. 
(Apart from the time when I intentionally used it to try things out, of course)
You will be surprised to know how much of a hassle free OS Ubuntu is compared to your initial expectations. At least until 13.10, 14.04 may be little troublesome as it just came out and like a good wine, you need to let it age a little before you taste it.
Just to add to that; I still don't know anything about coding after using Linux for around a year and it  has never bothered me.

---

### Post by alp2 on 2014-05-20
> **LastDino said:**
> Not the solution but funnily enough, I didn't even need to open my terminal on 13.10 when I used it for my regular use for around 6 months. 
(Apart from the time when I intentionally used it to try things out, of course)
You will be surprised to know how much of a hassle free OS Ubuntu is compared to your initial expectations. At least until 13.10, 14.04 may be little troublesome as it just came out and like a good wine, you need to let it age a little before you taste it.
Just to add to that; I still don't know anything about coding after using Linux for around a year and it  has never bothered me.

However other than that my battery life went really bad compared to windows 8.1 too which i dont understand why as ubuntu is supposed to be lighter OS. A problem for example is theres a youtube app on ubuntu i try to use it , it says download flash where for some reason it doesnt as theres no ubuntu14.04 option and it just dont download which i checked how to get flash and you need to go through terminal and type some things which is just a hassle.I was expecting an easy OS just use like windows and update anything i need without have to do coding and stuff.

---

### Post by LastDino on 2014-05-20
> **alp2 said:**
> However other than that my battery life went really bad compared to windows 8.1 too which i dont understand why as ubuntu is supposed to be lighter OS. A problem for example is theres a youtube app on ubuntu i try to use it , it says download flash where for some reason it doesnt as theres no ubuntu14.04 option and it just dont download which i checked how to get flash and you need to go through terminal and type some things which is just a hassle.I was expecting an easy OS just use like windows and update anything i need without have to do coding and stuff.

I don't know about battery issue, I'll let someone else talk you through it but you can copy paste the thing in terminal instead of typing. It is quite hassle free and on top of it you've ability to see everything on command line window just in case something goes wrong.
Try out one of those ''things to do after installing ubuntu -your version-'' guides.  
No pressure, just a suggestion from newbie to another. ^^

---

### Post by alp2 on 2014-05-20
I will try ubuntu on my desktop again after as that has XP and support is finished. However on my laptop im looking if anyone has a guide or can help me uninstall ubuntu and get back to my normal windows use.

---

### Post by buzzingrobot on 2014-05-20
> **alp2 said:**
> However other than that my battery life went really bad compared to windows 8.1 too which i dont understand why as ubuntu is supposed to be lighter OS. A problem for example is theres a youtube app on ubuntu i try to use it , it says download flash where for some reason it doesnt as theres no ubuntu14.04 option and it just dont download which i checked how to get flash and you need to go through terminal and type some things which is just a hassle.I was expecting an easy OS just use like windows and update anything i need without have to do coding and stuff.

1.  Battery life, for better or worse, is often better out of the box on Windows because Linux support from hardware vendors is often nonexistent or half-hearted and half-baked.  However, laptop are tools available, not installed by default, that allow you to tweak fan use, etc., to mitigate battery use.

2. That business of a browser prompting to download and install Flash from the Adobe site is essentially a Windows-ism. Much better to install it directly from the Ubuntu repositories.  It's available by itself packaged as "flashplugin-installer" and it is is one component of the "ubuntu-restricted-extras" package, which also include Microsoft fonts, a number of multimedia codecs, etc.  Search for, and install, with the Software Center app.

---

### Post by mörgæs on 2014-05-20
Just download and install Google Chrome and you will get Flash automatically.

---

### Post by alp2 on 2014-05-20
is there anyone that can guide me to uninstalling ubuntu from dual boot and getting to windows by itself?

---

### Post by Mark Phelps on 2014-05-20
You could start by actually reading post #6 -- it says what to do.

---

### Post by llamabr on 2014-05-20
> **Mark Phelps said:**
> You could start by actually reading post #6 -- it says what to do.

This seems right.  Also, if the Win8 people have trouble with your particular case, you could bring that question back here again.

If you bought your laptop new, it might have brought a recovery disk in the box, or if not, instructions about how to do a "factory reinstall" (which is usually a recovery partition).  Have a look for either of those.

If you're dual booting, probably it means that, except that part of your disk has ubuntu installed on it, it's already running exactly like it was when you bought it.  Maybe be a bit more explicit about what you want to happen.

---

