---
title: "[SOLVED] How can I download an application and store it on disc for later installatio"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by davwar on 2008-04-22
I'll be looking at Linux for the first time after this new release on Thursday, I know nothing about it - yet.

At the moment I'm stuck on dial-up so I'm getting a friend to download Ubuntu to disc for me when it's released - along with the apps that I need.

I'm going to start by using the Wubi (virtual?) installation to see if it will work for me and then install it in a partition later - so I wanted to have the OS and my needed apps stored on disc('s)

In addition to Ubuntu, I need 'Gimp' and a 'virtual windows' app (to see if I my one non-linux app can run). I was told that a 'virtual windows' app does exist - but this could be wrong.

1. Is it possible to download an application independently of the OS installation - for later installation?

2. Can anyone recommend a 'virtual windows'  application?

3. I looked at the Gimp web site for a Ubuntu version download but found it very confusing:
          Can anyone supply a link to the correct Gimp download?
          Can anyone supply a link to the correct 'virtual windows' application download?

In the places I have looked, I have not been able to answer the above - maybe I'm just looking in the wrong places.

I know that I don't fully understand the concepts around Linux yet but any help would be appreciated.

Thankyou.

---

### Post by aeiah on 2008-04-22
there are several ways to do this, although it might not be as simple as you'd have hoped. ubuntu does have installation packages, similar to windows, which have the .deb file extention (ubuntu is based on debian, which is where the .deb name comes from) and these can be double clicked and installed. the problem is, some need shared dependancies which still might need to be grabbed from the internet. foruntatley, most software for linux isnt very big, so even though you're on dial up, it shouldnt take you days to download things.

most of the software for ubuntu, however, is installed via synaptic. basically, you search a database for what software you want to install, and synaptic will fetch it from a repository online, and download and install it for you. very convenient, but only if you have the internet. since this is the preferred way for installing software in ubutu, it makes things difficult for you.

your friend could install ubuntu, and install all the stuff you need and then backup all those bits with APTonCD, which can archive the software installation files onto a cd or dvd.

another option is to get your friend to download ubuntu ultimate, which is a dvd that should have almost all the software you're likely to need all on one disc. this is large and unofficial, however.

as for 'virtual windows', what this really is is a virtual machine. on this virtual machine, you install windows, and windows thinks that its on a normal machine, and so you can run it in a window on your ubuntu desktop whenever you wish and install what you wish to it (although it doesnt support graphics card accelleration, so games are largely a no go). virtualbox is a decent virtual machine that runs on linux. what is the software you need that only runs on windows? there may be alternatives, or you may be able to run it with wine (which, when it works, tends to give better performance, but it doesnt work with everything)

---

### Post by aeiah on 2008-04-22
ps; a good place for getting .deb files is from [http://www.getdeb.net](http://www.getdeb.net) . gimp is on there, and if you have a look you'll see it lists several different files:
>  (gimp (3.9 MB) , libgimp2.0 (951.0 kB) , gimp-data (9.2 MB) , gimp-python (192.2 kB) , gimp-libcurl (5.8 kB) , gimp-helpbrowser (25.1 kB) , gimp-gnomevfs (7.3 kB))

you'll need all of these. you'll be able to install them by double clicking much like a setup.exe file in windows (although some will need to be installed before others. it'll tell you this if you do it in the wrong order though so dont worry)

---

### Post by Steveway on 2008-04-22
> **aeiah said:**
> ps; a good place for getting .deb files is from [http://www.getdeb.net](http://www.getdeb.net) . gimp is on there, and if you have a look you'll see it lists several different files:


you'll need all of these. you'll be able to install them by double clicking much like a setup.exe file in windows (although some will need to be installed before others. it'll tell you this if you do it in the wrong order though so dont worry)

Not needed! Gimp comes preinstalled and ready to go with Ubuntu.
There is no need to install anything.

---

### Post by aeiah on 2008-04-22
haha of course it does :lolflag: sillymeeeh

---

### Post by sayakb on 2008-04-22
As Steveway said, Gimp comes preloaded and you don't need to download it. For Virtual Windows, you can either:
1. Use Wine for running Windows apps. Though some apps may not run. Check appdb.winhq.org 
2. Use VirtualBox or VMWare to install Windows on a virtual machine for full functionality.

---

### Post by davwar on 2008-04-22
Hmmmm - a lot to take on board and not as straight forward for an 'XP' thinker.

My 'one windows app' is a proprietary stockbroker execution package - so no chance for an alternative app.

I really want to get away from Microsoft so I'll try 'Wine' first, before installing XP into a virtual environment.

GIMP - I looked at the Ubuntu Features page and I didn't see Gimp listed - sorry I missed it - glad it's part of the package, I've been using it for some time.

UBUNTU ULTIMATE - I just looked at the web site, lots of stuff - I'm guessing that there won't be a version based on Ubuntu v8 for some time;
    - I was hoping that v8 is a more refined and developed release more suited for an absolute beginner in Linux - is this correct?
    - as an absolute beginner would I be creating a rod for my own back by considering ULTIMATE which is an older version with so much stuff making it more complicated?

Thankyou for all the replies with their options for me to think about - I now have a starting place.

---

