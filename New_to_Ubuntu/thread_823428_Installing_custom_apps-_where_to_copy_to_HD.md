---
title: "Installing custom apps- where to copy to HD?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by HiddledyPiggledy on 2008-06-09
Ok.
2nd thread here for me asking for help....
I've got my 8.04 installed and working fine- basic stuff.
Now I want to install my some custom software.
**So how do I do it?**

I got a CD with some linux apps on it, organized (not sure yet how we type file structures without a picture link) like

application> bin
   "       > some folders 
   "       > a bunch more folders

...I.E. a "program" folder with a bunch of folders in it, with names like "bin", and then two non-folders in it, one named *.pl


***So my question is, how do I install this app?***
Do I copy it somewhere? I tried the usual 2 normal methods and couldn't find it. I wasn't able to get my windows-burned CD to be recorgnized as something useful within Ubunto, so it couldn't read it off the original CD. So I copied it TO my HD, into the "tmp" folder, and that ended that- I wasn't able to even move it anywhere else (I'm NOT using command line stuff yet though, hopefully I won't need to do much of that yet)...

**what's the trick to installing custom apps? What folder do I move things to so my installer can find the app and data???**

Thank you again in advance.

:KS

---

### Post by hyper_ch on 2008-06-09
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by 3rdalbum on 2008-06-09
I think I understand how it's organised - the program directory contains folders of the same names as in the Filesystem ("/"). It sounds like you'd copy the files to the appropriate places in your filesystem - for instance, any directory within "/usr/share" should be copied to the same place in your filesystem.

Who made this CD? If I'm understanding things correctly, that's a very unusual, dumb/naive way of distributing Linux software. Are you sure those aren't Slackware packages?

Chances are, you don't need to install this custom software from the CD. Just use the Synaptic Package Manager to find the same software, or equivilant. It will be much easier.

---

### Post by HiddledyPiggledy on 2008-06-13
Thank you for the help so far

Well it isn't working. Here is why. 
**I don't have permissions on my own OS to install it.** 
So how do I change that? (LOL)

Also, I am using CD's because I am not on-line. The CD's work on other systems according to my friends, and they have done and added nothing special, so they said if I know how to install it then I can.

So I try and copy (there is no packages to install, just folders and the *.pl files for each app) the bin folder from the CD to the bin folder on my HD and I am denied.

do I have to run and learn some commands then (well of course)???

Thanks again!
:)

---

### Post by ET! on 2008-06-13
the problem is you need to be root to perform some functions.....here is how you do it

type sudo su

and type the password....

---

### Post by avtolle on 2008-06-13
> **HiddledyPiggledy said:**
> Thank you for the help so far

Well it isn't working. Here is why. 
**I don't have permissions on my own OS to install it.** 
So how do I change that? (LOL)

Also, I am using CD's because I am not on-line. The CD's work on other systems according to my friends, and they have done and added nothing special, so they said if I know how to install it then I can.

So I try and copy (there is no packages to install, just folders and the *.pl files for each app) the bin folder from the CD to the bin folder on my HD and I am denied.

do I have to run and learn some commands then (well of course)???

Thanks again!
:)
I'm not entirely clear here, but from what you have posted, these are linux apps which work for Ubuntu? Are these apps d/l from the Ubuntu repositories that your friends are passing on to you for installation?
If the latter, it sounds like this is the use of Apt on CD. One thought (I've not used this, so have absolutely no experience with it, and this would be at your own risk): insert the CD into the drive, go into Synaptic and reload the sources, and see whether you can install from it. You might need to identify the CD as a "source"; perhaps a Google on Apt on CD Ubuntu might help here.

---

