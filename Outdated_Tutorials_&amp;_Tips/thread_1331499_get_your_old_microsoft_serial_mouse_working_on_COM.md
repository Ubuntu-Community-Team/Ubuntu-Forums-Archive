---
title: "get your old microsoft serial mouse working on COM1 with 9.10"
date: 2009-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by raygj on 2009-11-19
to get your old microsoft serial mouse working on COM1 with 9.10 you need to install the gpm package.so in a terminal enter
Quote:
> sudo apt-get install gpm
then ,after it is installed, you enter in terminal

Quote:
> sudo inputattach --microsoft /dev/ttyS0
now move your mouse around to see that your serial mouse is working ok.
OK?
now you need to set you computer to run it on startup.
so in a terminal enter
Quote:
> sudo gedit /etc/rc.local
an editer window opens with
Quote:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
now enter


Quote:
> inputattach --microsoft /dev/ttyS0
so that the **/etc/rc.local** file contains
Quote:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B]## added serial mouse input ##
inputattach --microsoft /dev/ttyS0[/B]

exit 0
now save this file and close editer.
now ,when you re-boot, your serial mouse will work.

---

### Post by jakaspaka on 2010-01-12
Thanks! Works great. Only that I use Logitech mouse so I used different switch. 

```
inputattach --mouseman /dev/ttyS0
```

I recomend typing:

```
inputattach --help
```

to see all mouse devices available.

---

### Post by derrick81787 on 2010-01-25
That's awesome! A while back, I had been looking for a way to get a serial mouse working and couldn't find a way.  This is so simple.  Thanks.

---

### Post by ankitduseja on 2010-02-03
My terminal window appears blank. I googled a little and When using xterm and passing this command it just jumps to next blank line and nothing happens.

Also my xorg.conf file is blank! Please help!

---

### Post by TheOldestNoob on 2010-02-23
Thanks a lot *raygj* for your help! I tried it locally and it worked nicely.

What about extending this capability to an (a bunch of, actually...) old 233 MHz Pentium terminal, which has no other mouse input than a serial port? I've been googling for a whole day about how to make it work, with no success. I've found [this]("http://ufpr.dl.sourceforge.net/project/ltsp/Docs-Admin-Guide/LTSPManual.pdf") manual (among other articles, which stated the same, more or less) but it does not seem to get it to work, either.

Any advice?

Thanks again.

---

### Post by anthony.cirelli on 2010-04-20
thank you for a simple explanation for this problem, it worked like a charm for me, just a tip for other noobie users, if ttys0 doesn't work then try ttys1 or ttys2 (as was my situation), also, I did not have to go thru the install apt-get part, I just went straight to inputattach

---

### Post by mobilediesel on 2010-04-21
My wife's computer has a keyboard with a serial touch pad built in. The keyboard is at least 10 years old. We're both running 8.04 and this worked perfect for getting that touch pad working!

Now the crappy mouse she's been using can be disposed of.

---

### Post by oldspammer on 2010-04-28
My computer had its MS Serial wheel mouse going at one point, and then after I had booted up without it attached, its functionality went away even after I reconnected it and rebooted.

See thread: [http://ubuntuforums.org/showthread.php?t=1464591](http://ubuntuforums.org/showthread.php?t=1464591) 

What configuration files were updated by the system to remove this functionality?

My computer did not have gpm installed to my knowledge, so how was the Serial Mouse with wheel activated and useful without this package installed--ie., what was operating it instead?

The rc.local illustrated above did not activate my wheel on my serial mouse -- the wheel was not working, so I performed a

  inputattach --help 

that displayed all of its options, one of which was

inputattach --intellimouse /dev/ttyS0

and by rebooting my computer with this in my rc.local file, the wheel functionality was restored.

---

