---
title: "Hal Will Not Install"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by Acinnatirb on 2013-07-04
Hi, I'm trying to install HAL for Ubuntu:

*Sudo apt-get install hal*

And I get the error: 

[I]Unable to locate package hal
[/I]
Where can I install hal/why is this not working? Sorry, quite new to Ubuntu...

I am in Ubuntu 12.10, 64-bit

Thanks in advance.

---

### Post by Zill on 2013-07-04
Acinnatirb: AIUI hal is now [deprecated]("http://en.wikipedia.org/wiki/Udev"):
> By the middle of 2011 HAL had been deprecated by most Linux distributions as well as by the KDE, GNOME and XFCE desktop environments, among others. The functionality previously embodied in HAL has been integrated into udev itself, or moved to separate software such as udisks and upower.
See [Halsectomy]("https://wiki.ubuntu.com/Halsectomy") for more details.

---

### Post by slickymaster on 2013-07-04
Hal is deprecated, since it has become a large monolithic unmaintainable mess, and also duplicates a lot of functionality which are nowadays provided by **udev** and the kernel itself.
If you want to install Microsoft fonts, see this link for more detailed instructions: [http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/](http://www.howtogeek.com/howto/15495/add-microsoft-core-fonts-to-ubuntu/)

---

### Post by Acinnatirb on 2013-07-04
OK, any ideas on how to get 4OD playing on Ubuntu without Hal?

---

### Post by Zill on 2013-07-04
Acinnatirb:  Presumably you are referring to UK [Channel 4 On Demand]("http://www.channel4.com/programmes/4od") (don't forget that Ubuntu Forums has a worldwide userbase!).

4OD (and BBC iPlayer) just uses a standard flash player so if you have flash installed it should run fine.  This can easily be installed along with many other goodies if you run the following code:
```
sudo apt-get install ubuntu-restricted-extras
```

ps. Welcome to Ubuntu Forums. :-)

---

### Post by Acinnatirb on 2013-07-04
Thanks :P 

Already done that, got Flash. For some reason I can't play 4OD though (I live in the UK, in case u thought it was an IP problem and I'm not using a proxy), here they said it was because I needed HAL: [http://m.jguk.org/2012/10/resolved-channel4-4od-working-with.html](http://m.jguk.org/2012/10/resolved-channel4-4od-working-with.html) 

Any ideas what to do now?

Thanks in advance

---

### Post by slickymaster on 2013-07-04
[COLOR=#000000]Acinnatirb, [/COLOR]see this [post]("http://ubuntuforums.org/showthread.php?t=2144347&p=12709644&viewfull=1#post12709644"), here in the forum, about a similar issue.

---

### Post by Zill on 2013-07-04
Acinnatirb:  OK - you seem to have highlighted an "anomaly" with the deprecation of HAL. ;-)  I have now looked into this and it seems that you *do* need to have HAL installed to play 4OD flash videos - something to do with DRM although what ties flash and HAL together is beyond me!  Adobe have issued a document entitled "[Problems playing protected video content]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html")" which helps to explain this.

To cut a long story short, you do need to install [hal]("http://packages.ubuntu.com/quantal/hal") and, as you tried but failed to do this earlier I suggest this may be because the ubuntu "universe" repository is not enabled in your sources list.  If you know how to enable this repo then you can do this, either directly by editing the sources.list or using a GUI such as the Software Center or Synaptic.  Otherwise, just post back here with the full output of the following command:
```
cat /etc/apt/sources.list
```

Once the "universe" repo is enabled you should be able to install hal with your original command:
```
sudo apt-get install hal
```

BTW, I just noticed that your original command in post [#1]("http://ubuntuforums.org/showthread.php?t=2159754&p=12717511#post12717511") actually started with "Sudo", not "sudo".  Note that Linux is case sensitive and so "THIS" is different to "This" which is different to "this".  The "sudo" command must *always* be lower-case.

On this basis, first try to install hal again using the correct command.  If this still fails then try enabling the universe repo as described above.

---

