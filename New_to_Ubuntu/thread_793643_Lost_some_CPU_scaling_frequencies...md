---
title: "Lost some CPU scaling frequencies..?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by samdavid6 on 2008-05-13
Hey everyone.  Firstly, thank you for all the help you give..

I have alaptop with an AMD Athlon 3200 which runs at 1.8Ghz.

In Windows, I get the option to run it at 800Mhz, 1Ghz, 1.2Ghz, 1.4Ghz, 1.6Ghz and 1.8Ghz.

In Ubuntu, I only get 800Mhz, 1.6Ghz and 1.8Ghz.  Where did all the other levels go..?  And how do I get them back..?

I would like a little more processing power, but I'm trying to do this without the fan kicking in.  Either 1.6 or 1.8Ghz and my fan starts up in less than a minute..

Sam

---

### Post by Bigtime_Scrub on 2008-05-14
In order to be able to change the operating frequency, your processor should support changing it. You can find out if your processor has scaling support by seeing the contents of files in the /sys/devices/system/cpu/cpu0/cpufreq/

On the Ubuntu Forums, I read that one can manually change the frequency by executing commands like:
$ cpufreq-selector -f 1300000
which will set the frequency to 1.3 GHz.

There is a known bug to work around with this too.[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/23768](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/23768)

Also check out this read me

$cat /usr/share/doc/gnome-applets-data/README.Debian

and as suggested in it, do:

$ sudo dpkg-reconfigure gnome-applets
and answered “Yes” to the question regarding setting the suid of the cpufreq-selector executable. Now, by left-clicking on the CPU Frequency Monitor Applet, you can choose the frequency for your processor.

---

### Post by Canis familiaris on 2008-05-14
In terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

To view the tutorial with screenshots, visit:
[http://dogbuntu.wordpress.com/2008/05/12/enable-cpu-frequency-applet-to-manually-select-clock-speed/](http://dogbuntu.wordpress.com/2008/05/12/enable-cpu-frequency-applet-to-manually-select-clock-speed/)

---

### Post by Canis familiaris on 2008-05-14
> **samdavid6 said:**
> Hey everyone.  Firstly, thank you for all the help you give..

I have alaptop with an AMD Athlon 3200 which runs at 1.8Ghz.

In Windows, I get the option to run it at 800Mhz, 1Ghz, 1.2Ghz, 1.4Ghz, 1.6Ghz and 1.8Ghz.

In Ubuntu, I only get 800Mhz, 1.6Ghz and 1.8Ghz.  Where did all the other levels go..?  And how do I get them back..?

I would like a little more processing power, but I'm trying to do this without the fan kicking in.  Either 1.6 or 1.8Ghz and my fan starts up in less than a minute..

Sam

Did you mean you have already done this and it does not work?

---

### Post by samdavid6 on 2008-05-14
No I havent tried anything.  I am a bit of a noob so I didnt know what to do.  Will try and let you know..

Sam

---

### Post by samdavid6 on 2008-05-14
Ok.. The suggestions given are to enable CPU frequency scaling. I can already do that.

I just seem to be unable to select 1Ghz and 1.2Ghz speeds in Ubuntu, but I can do so in Windows..

---

### Post by kernalsanders123 on 2008-05-15
Hello all, got a similar problem myself.

I followed the directions in the link that Anurag_panda posted, and the cpu frequency applet now has the pulldown menu to select various frequencies, but my frequency is stuck on 1ghz, no matter which one I select.

Any help would be greatly appreciated, thanks!

---

### Post by kernalsanders123 on 2008-05-15
Update

Please disregard my previous post, installed the powernowd package, worked like a charm.

---

