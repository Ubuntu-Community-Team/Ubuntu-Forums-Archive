---
title: "How to Downgrade gdm 2.28 to 2.20"
date: 2009-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by TWhyman on 2009-11-11
<rant>
IMHO the new gdm 2.28 shipped by default with Ubuntu 9.10 is really just work in progress. It's fine for what it currently supports, but it does not support the range of functionality that gdm 2.20 does. Perhaps the biggest issue is Multiseat X. Multiseat X is one of the best things about Linux. You can have several independent workstations all on the same computers, each with their own X Server. Apart from anything else, this can reduce a group of users' carbon footprint by needing fewer computers and should be something that Ubuntu is shouting about and not hiding in some "legacy package" with all its negative implications.

Not only that, the gdm-2.20 package shipped with Ubuntu 9.10 is broken!

See [https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/475281](https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/475281)
</rant>

I would certainly recommend downgrading to gdm 2.20 to get the most out of your Ubuntu installation and the following is how you do it:

1. Start up 9.10 and login.

2. Open up a command line console (Applications->Accessories->Terminal) and enter:

sudo /etc/init.d/gdm stop

This will both stop gdm and the GUI and drop you back into a command line console. A necessary step for downgrading.

3. Login to the command line console and enter:

sudo apt-get install gdm-2.20

This will do the necessary work of removing gdm 2.28 and replacing it with 2.20. When prompted to select the default display manager, select "gdm-2.20".

4. Now you have to fix the broken gdm.conf. Enter

cd /etc/gdm
sudo sed 's|X11R6/||' gdm.conf >/tmp/gdm.conf
sudo mv /tmp/gdm.conf .

(note the period character at the end of the line - you really do need it)

This will edit out the offending entries and replace the broken gdm.conf

5 Restart gdm

/etc/init.d/gdm start

---

### Post by ilGuccino on 2009-11-15
it worked for me, except for the last line
"/etc/init.d/gdm start" returned a fail status
it worked with "sudo gdm" (but I think that a reboot would have been enough)
thanks for the hack
ilGuccino

edit: I have a radeon 9200 and fixed a black screen issue with the workaround explained here by SteveE (#3) [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139)
when I reboot X didn't work anymore complaining about a bad configuration
I removed the workaround and used the xorg.conf posted by bagl0312 (#41)
now both compiz and gdm 2.20 work

---

### Post by scorp123 on 2009-11-19
> **TWhyman said:**
>  Not only that, the gdm-2.20 package shipped with Ubuntu 9.10 is broken!  Actually ... it's not. 

What they did is that they no longer create the symbolic link between **/usr/X11R6/bin** and **/usr/bin** ...

On Ubuntu Jaunty 9.04 you can ....
```
cd /usr/X11R6
ls -al
lrwxrwxrwx   1  root root   6   2009-08-25  17:12   bin -> ../bin

```

On Ubuntu 9.10 however ...
```
cd /usr/X11R6
-bash: cd: /usr/X11R6: No such file or directory
```

So not GDM's config file is broken ... but rather they left out the symlink between **/usr/X11R6/bin** and **/usr/bin**

**/usr/X11R6/bin** is usually something of a "standard" on Unix/Linux, e.g. all X11 binaries such as "xclock", "xterm", "rxvt" should go in there. Instead of sticking to that standard or instead of at least providing a symlink they left it all away this time.

Thanks for your posting BTW .... I didn't see it in time and "re-discovered" your posting via UbuntuGeek. :D

---

### Post by majortom117 on 2010-04-16
Hi,

I had the same problems that there are two xserver startet after downgrading to gdm 2.20.

I think the problem is that there is a /etc/init/gdm.conf wich affects upstart to start gdm and because of the runlevel startscripts in rc* the gdm is started twice...

so I moved the /etc/init/gdm.conf to a temporary folder, rebooted and everything works fine now.

hope this could help, cause it helped for me

greets

Majortom117

---

### Post by g003y on 2010-05-07
It doesn't work on Lucid. I get stuck when I run the command

sudo apt-get install gdm-2.20

where it says that the package is not found. Is this a repository issue? If so, how can I solve this?

---

### Post by suicidejack on 2010-05-16
I noticed that there is only an option for gdm and there are no legacy packages available in 10.4...

This new gdm is horrible.  Unfortunately there doesn't appear to be any way to avoid using it right now.

---

### Post by jes-13 on 2010-06-13
> **g003y said:**
> It doesn't work on Lucid. I get stuck when I run the command

sudo apt-get install gdm-2.20

where it says that the package is not found. Is this a repository issue? If so, how can I solve this?

Try this...
from: [[COLOR="Blue"]Download Page for gdm-2.20[/COLOR]]("http://packages.ubuntu.com/karmic/i386/gdm-2.20/download")

[COLOR="DimGray"]"You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) karmic main universe

Replacing cz.archive.ubuntu.com/ubuntu with the mirror in question."[/COLOR]

I added my local mirror to the list and then used the package manager to install gdm 2.2

---

### Post by iceman_ch on 2010-12-13
I know this is an older post but, I have to say that this worked great for me.  There is a definitely a difference in load times.  It definitely takes longer to log in.  However I wanted to be able to customize the log in screen.  

The one problem I had is when I logged in all of my desktop effects were gone. I tried to re enable them and it said there was no driver available.  I check additional drivers and it still showed that nvidia was active. So I went in to edit the nvidia settings and it said there was no x-conf file. It gave instructions on how to fix that.  Once it was fixed everything works well.

---

### Post by LordDelta on 2011-03-27
Thanks iceman_ch!

I'm glad to hear it worked for you, hopefully it'll work for me too...

I can hardly believe someone of all-knowing knowledge somewhere decided to force a choice for 3 extra seconds of boot speed on all ubuntu users. Hardware seems to be getting faster, not slower, I'll take my chances.

---

