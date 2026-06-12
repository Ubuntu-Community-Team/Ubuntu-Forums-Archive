---
title: "how run a program?"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by nycap on 2012-11-14
hi.  i have installed a program but i cant figure out how to run it.  please excuse me i just started unbuntu yesterday.  any help will be much appreciated.

---

### Post by drmrgd on 2012-11-14
You might have a look at this tutorial:

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial)

You can just basically search the dash for the program and run it from there.

---

### Post by arpanaut on 2012-11-14
What program?
How did you install it?
What version of Ubuntu are you running?

This would help us to answer your query.

---

### Post by nycap on 2012-11-14
i have latest ubuntu. the program is gnuradio.  i ran the program using alt F2.  is this generally a good way to start programs?

---

### Post by drmrgd on 2012-11-14
Sure, that way will work fine.  In fact, that's my preferred method to launch programs, if I'm not launching them with the terminal :)

---

### Post by Paqman on 2012-11-14
> **nycap said:**
> i have latest ubuntu. the program is gnuradio.

I can't find anything in the Ubuntu repos with that name. Where did you install it from?

If you install genuine Ubuntu packages through the Software Centre then you can launch them by hitting the Windows key and typing the name. Once they're running you can pin them to the launcher if you want quick access.

> 
i ran the program using alt F2.  is this generally a good way to start programs?

Yep, that's fine.

---

### Post by mastablasta on 2012-11-14
well since the programme is not running it might be worth opening terminal and running it there to see if there is any error output shown. then continue the troubleshooting from there.

---

### Post by nycap on 2012-11-14
> **Paqman said:**
> I can't find anything in the Ubuntu repos with that name. Where did you install it from?

i ran a command found on gnuradio.org that downloaded it, compiled it, and installed it.  

thanks.

---

### Post by Paqman on 2012-11-14
> **nycap said:**
> 
i ran a command found on gnuradio.org that downloaded it, compiled it, and installed it.  


Actually, scratch what I wrote earlier, gnuradio is available in the Ubuntu repos, just not on Precise.

On Ubuntu the normal way to install software is to go to Software Centre, search for it, and click to install. We generally don't download software from websites like you do on Windows.

The problem with downloading from a website and compiling is you won't get any updates and if you install any dependencies to make your software work, it can break other software on your system.

If I were you I'd consider deleting your manually installed copy of it and install the one from Software Centre. It'll be much easier to manage.

---

### Post by mike acker on 2012-11-14
> **Paqman said:**
> Actually, scratch what I wrote earlier, gnuradio is available in the Ubuntu repos, just not on Precise.

On Ubuntu the normal way to install software is to go to Software Centre, search for it, and click to install. We generally don't download software from websites like you do on Windows.

The problem with downloading from a website and compiling is you won't get any updates and if you install any dependencies to make your software work, it can break other software on your system.

If I were you I'd consider deleting your manually installed copy of it and install the one from Software Centre. It'll be much easier to manage.

+1

as I understand it the software we have in our library has all been checked. stuff you dig up on the net -- :confused: on windows i always downloaded stuff first and then checked it with Symantec/endpoint.  this is better than nothing but as we all know: virus scanning is always looking for known problems. while the hack industry has automated the process of obfuscating or re-disguising their "warez" -- and then testing -- to be sure current a/v products do not detect their malware.

---

### Post by mastablasta on 2012-11-15
from gnu radio web site [http://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGR](http://gnuradio.org/redmine/projects/gnuradio/wiki/InstallingGR):
> 
**NOTE: that if you do use pre-compiled binaries (through apt-get or yum), you will probably not get the most current version, and GNU Radio is changing a lot at the moment. So don't expect any help on the mailing list! These binaries are very old, and we are no longer putting new version into the standard repositories for apt-get and yum installation. We will be adding our own support for this in the near future. Meanwhile, please follow the instructions for building from source or using the build-gnuradio script (see next two sections).**

 
basically the one in the repos is not supported. so installing it via script seems ot be the way to go or you can alweays try building it manually if the script is maybe dated.

---

### Post by Paqman on 2012-11-15
If soemthing is "changing a lot", then getting the latest version might not be a good idea unless you specifically want to help out with testing.

Even if you did want the latest version, the best way to get it would be a PPA so that you go the updates without having to manually reinstall every five minutes. There are PPAs available such as [this one]("https://launchpad.net/~kamalmostafa/+archive/gnuradio") that seem to be up to date. They guy who owns it even has a beard, so is probably down with the Gnu crew.

---

