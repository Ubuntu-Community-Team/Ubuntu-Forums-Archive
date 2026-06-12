---
title: "Sunbird in 8.04"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Stegga on 2008-05-08
I am trying to install a shared calendar system, and would like to have sunbird running with Google calendar.
There is all thsi talk of using sunbird and google calendar, but when I use Synaptic Package MAnager, it downloads Sunbird version 0.5 and the Google Calendar Extension requires Sunbird 0.8.
I can download Sunbird 0.8 from the Mozilla site, but am struggling to install it.
I have been advised to only use the apt-get tool for installing additional applications, for stability purposes in my office (there are 9 of us and I am looking after the IT and call a consultant in to help when there is a problem) so how do I get Sunbird 0.8 installed through Synaptec Package Manager?

Help.

Andrew

---

### Post by Stegga on 2008-05-08
Is the Sunbird that comes down in Hardy version 0.8? Does anyone know?

Regards,
Andrew

---

### Post by Joeb454 on 2008-05-08
If it's in the repositories then Synaptic should tell you. That said I'll look for you anyway :)

No it's version 0.7 that comes in Hardy.

If you want Version 0.8 you'll have to download it from Mozilla, though that may also require compiling it from source.

---

### Post by adwatkin19 on 2008-05-08
I have just looked and from where i am it appears to be the 0.7 version of sunbird in the repos. i have enabled multiverse, and i have added the medibuntu repos.

Adam

---

### Post by logos34 on 2008-05-08
> **Stegga said:**
> 
I can download Sunbird 0.8 from the Mozilla site, but am struggling to install it.
> 
[Linux/GTK2 and Solaris/GTK2]("http://www.mozilla.org/projects/calendar/releases/sunbird0.8.html")

Extract the tarball in the directory where you want to install Sunbird:

tar -xzvf sunbird-0.8.en-US.linux-i686.tar.gz

This will create a sunbird subdirectory of that directory.

Then just do:

alt + F2

type:

/home/user/sunbird/sunbird

(assuming it's in your home directory)

Create a launcher by right-clicking on Applications menu>edit menus

---

### Post by spotteddog on 2008-05-09
I'm trying to get Sunbird 0.8 also.

I downloaded 0.8, created the /home/joe/sunbird/sunbird directory, tarred the downloaded tar.gz file. Everything is there (in that directory), but I can't find anyway to start sunbird. :(

I tried:

 " alt + F2

type:

/home/joe/sunbird/sunbird"

But that just opens the directory. 

How do I start Sunbird? How do I create a shortcut for Sunbird in Apps> Office? 

Thanks,

Spot

---

### Post by logos34 on 2008-05-09
> **spotteddog said:**
> I downloaded 0.8, created the /home/joe/sunbird/sunbird directory, tarred the downloaded tar.gz file. 

you don't need to create a directory --just extract the tarball in /home/joe.

/home/joe/sunbird/**sunbird** -- the bold is the app executable.

right-click Applications (panel)>edit menus>office>new item.  For the command   browse to sunbird folder and point it at the executable

---

### Post by Joeb454 on 2008-05-09
How dare you use my home directory without my permission?!

* Goes to remove permissions on ~/ *

:lol:

---

