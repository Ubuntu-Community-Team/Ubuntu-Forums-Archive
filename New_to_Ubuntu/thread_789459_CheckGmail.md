---
title: "CheckGmail"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by cool_penguin on 2008-05-10
Hi Guys, 

So far everything seems to be working great on my Ubuntu 8.04 except one small annoyance. I use checkgmail notifier and I have also added it to startup so that it loads on the Gnome panel on start up. However when I boot my system, everything on my panel loads quickly except checkgmail notifier. It loads almost after a minute. And when it is still loading (during the one minute wait period) the CPU usage is 100 %. 

This makes me feel that my Ubuntu seems to be loading up slowly similar to VISTA or XP. However, I will never switch back to Windoz. I just want this small bug to be fixed. Any help from all you Ubuntu experts will be greatly appreciated.

Thanks a lot in advance. 

Cheers,
Harry

---

### Post by cool_penguin on 2008-05-10
BTW, I forgot to mention. I had checkgmail installed in Gutsy (7.10) and it worked just fine. 

Cheers,
Harry

---

### Post by cool_penguin on 2008-05-10
Anybody?

---

### Post by malathion on 2008-05-10
This sounds like a bug with that software. Your best bet is to contact the developer directly.

---

### Post by avtolle on 2008-05-10
I have checkgmail installed and loading as do you. I've no answer to your particulary query, but I don't have the same problems that you do, although, as expected on a slower computer, the panel loads slowly. I wonder if the slowness of checkgmail has anything to do with the time it takes to connect to gmail, etc.? Just a thought (as sometimes directly checking my Gmail account seems to take forever, or at least a minute or two.)

---

### Post by cool_penguin on 2008-05-10
I tried the following since i would get errors on the terminal when i would fire up checkgmail manually.

   1. Install Perl ExtUtils dependencies:
      $ sudo apt-get install libextutils-depends-perl libextutils-pkgconfig-perl
   2. Install Libsexy, including header file:
      $ sudo apt-get install libsexy2 libsexy-dev
      The header files will pull in many other libraries.
   3. Install Gtk2-Sexy, the Perl bindings for Libsexy
      $ sudo perl -MCPAN -e 'install Gtk2::Sexy'
   4. Install Crypt:Simple:
      $ sudo perl -MCPAN -e 'install Crypt::Simple'

Even this does not seem to help. It still takes long to load :(

---

### Post by cool_penguin on 2008-05-11
Somebody? Anybody? Nobody?

---

### Post by tr333 on 2008-05-11
Last time I checked, the CheckGmail program was a single (python?) file.  You should be able to go directly to [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/) and download the latest version, replacing the file installed by Ubuntu.  There should be no problems doing this as there are no associated library files that are specific to CheckGmail, only standard language libraries.

I'm not sure if this will solve your problem though, but it's worth a try.

---

### Post by whitethorn on 2008-05-11
> **cool_penguin said:**
> Hi Guys, 

So far everything seems to be working great on my Ubuntu 8.04 except one small annoyance. I use checkgmail notifier and I have also added it to startup so that it loads on the Gnome panel on start up. However when I boot my system, everything on my panel loads quickly except checkgmail notifier. It loads almost after a minute. And when it is still loading (during the one minute wait period) the CPU usage is 100 %. 

This makes me feel that my Ubuntu seems to be loading up slowly similar to VISTA or XP. However, I will never switch back to Windoz. I just want this small bug to be fixed. Any help from all you Ubuntu experts will be greatly appreciated.

Thanks a lot in advance. 

Cheers,
Harry

I don't know why it's not working, but I could suggest some alternatives.  I used to use mail-notification to check my gmail account.  Never had any problems with it and it didn't slow my bootup time. It's available in synatics. Right now I've set up my conky to check my gmail account.  There are a couple guides out there I used this one

[http://ubuntuforums.org/showthread.php?p=4219577](http://ubuntuforums.org/showthread.php?p=4219577)

---

