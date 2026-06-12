---
title: "[SOLVED] How to: Install Cinelerra CV 2.1 in Feisty"
date: 2007-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Amazona aestiva on 2007-08-30
[SIZE="3"]***[COLOR="Red"]I warn you that here is no support, and the guide is to be used at your own risk![/COLOR]***[/SIZE]

First need to know that Cinelerra's dependencies often [COLOR="Red"]conflicts[/COLOR] with other packages.

[COLOR="RoyalBlue"]First step:[/COLOR]
Make sure you have universe, multiverse and restricted repositories enabled

[COLOR="RoyalBlue"]Second step:[/COLOR]
Add the following repository to your /etc/apt/sources.list file, according to your CPU type:
This means which architecture of Ubuntu You have installed (x86/amd64), so I don't know who needs pentium4?
An example: I have an AMD64 CPU but I've installed x86 Ubuntu, so I need i386 or i686. (I don't know the difference, both is working for me)

- i386:
```
deb http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/ ./
```

- i686:
```
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./
```

- athlonxp:
```
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/ ./
```

- pentium4:
```
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/ ./
```

[COLOR="RoyalBlue"]Third step:[/COLOR]
Type these:
```
sudo apt-get update
```
```
sudo apt-get install cinelerra
```

[COLOR="red"]**Troubleshoot:**[/COLOR]
When got the attached picture/window, try this:
Type:
```
gksudo gnome-terminal
```

A new terminal appears and type this into it:
```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```


Now Cinelerra should work correctly.:)

[COLOR="SeaGreen"]This solution was checked/updated: 30-08-2007[/COLOR]

An [COLOR="Red"]important[/COLOR] thing about Cinelerra:
Not all of .avi files can be opened!

---

### Post by SZF2001 on 2007-09-08
I'm kind of confused - my machine sees itself as i686, but my processor is Pentium 4.

What should I do?

---

### Post by Amazona aestiva on 2007-09-09
Hmmm

If You have installed a x86 version of Ubuntu use i686.

For example:
My CPU:
AMD 64bit X2 Dual Core 5200+

BUT I installed a x86 Ubuntu:
So I need i686.


So use i686.

---

### Post by RJP on 2007-09-10
Something that may help some people having trouble installing Cinelerra....
I found this out the hard way after many hours of trying to install. Go through your source list and make sure you don't have more than one source for Cinelerra.
In fact, I would uncheck all xtra repositories you may have added besides the repo for cinelerra AND universe, multiverse and restricted repositories enabled. 
The Repo for Ubuntu AMD64's is what did the trick for me...
[http://cv.cinelerra.org/getting_cinelerra.php#ubuntu]("http://cv.cinelerra.org/getting_cinelerra.php#ubuntu")

This may sound confusing but what I encountered was two repositories that had different versions of Cinelerra . After I told myself to go back to basics in repo's and leave just the  Cinelerra repo and universe, multiverse and restricted repositories, to my amazement, Cinelerra loaded  without a hickup!

My machine is home built system with..
AMD Athlon FX-55
2 Gigs of Ram
Ubuntu Feisty Fawn 64 bit

Hope this helps some people and they're frustrations.

---

### Post by Shlomir on 2007-09-11
Mine failes as it can't find libguicast..any repositories that have the whole bundle?..and then

cinelerra:
  Depends: libquicktimehv (=1:2.1.0-2svn2007424ubuntu3) but 1:2.1.0-2svn20070520 is to be installed

---

### Post by Amazona aestiva on 2007-09-11
> **Shlomir said:**
> Mine failes as it can't find libguicast..any repositories that have the whole bundle?..and then

cinelerra:
  Depends: libquicktimehv (=1:2.1.0-2svn2007424ubuntu3) but 1:2.1.0-2svn20070520 is to be installed

Have You followed my instructions?
Do You need i386?

---

### Post by Shlomir on 2007-09-12
I''m running a P4 Prescott 3.2 mhz on a socket 478 mobo..So I'm assuming I need the p4 repo?

I'll unistall everything and try yr instructions again...

I finally got KDENLIVE and KINO working again..The problem I find is that you need su privilidge to capture and write to folder, as the standard Ubuntu users won't do it, even if you tick 'administer system'

It's been taking me hours to find it would be easier if I can have root privilidge for my logon, but I'm not sure how to do it...Doing it via the 'User admin' applet' doesn't seem to work, it probabyl needs a command line, but I'm a n00b and don't understand.

---

### Post by Shlomir on 2007-09-12
> **Amazona aestiva said:**
> Have You followed my instructions?
Do You need i386?

Yes follwoed your instructions and used the i386 repo, got the following error when trying to install:

The following packages have unmet dependencies:
  cinelerra: Depends: libquicktimehv (= 2.1.0+svn20070109-0ubuntu1) but 1:2.1.0-2svn20070520 is to be installed
             Depends: libmpeg3hv (= 2.1.0+svn20070109-0ubuntu1) but 1:2.1.0-2svn2007424ubuntu3 is to be installed
E: Broken packages


Any ideas on how to clean-up and try again?

---

### Post by Amazona aestiva on 2007-09-12
> **Shlomir said:**
> Yes follwoed your instructions and used the i386 repo, got the following error when trying to install:

The following packages have unmet dependencies:
  cinelerra: Depends: libquicktimehv (= 2.1.0+svn20070109-0ubuntu1) but 1:2.1.0-2svn20070520 is to be installed
             Depends: libmpeg3hv (= 2.1.0+svn20070109-0ubuntu1) but 1:2.1.0-2svn2007424ubuntu3 is to be installed
E: Broken packages


Any ideas on how to clean-up and try again?


Try [this]("http://ww2.fs.ei.tum.de/%7Edr/cinelerra-cv-2.1_2.1-1_i386.deb").

---

### Post by Shlomir on 2007-09-12
> **Amazona aestiva said:**
> Try [this]("http://ww2.fs.ei.tum.de/%7Edr/cinelerra-cv-2.1_2.1-1_i386.deb").

FANTASTIC! That works!  Two last things:

1. How do you make an icon in Applications>sound&video?

2. How do you capture and preview footage of a SOny PD170 using Firewire?

Cheers and thanks:popcorn:

---

### Post by Amazona aestiva on 2007-09-13
The icon should be there after a reboot.
or
see the attached pictures, how to add a new icon to menu.

Firewire... I've tried configure it, but I can't. Someones have asked this here too, but nobody knows... You should go to a Cinelerra forum. The answer should be there.

---

### Post by bac on 2007-09-26
Troubleshoot:
When got the attached picture/window, try this:
Type:
Code:
gksudo gnome-terminal

A new terminal appears and type this into it:
Code:
echo "0x7fffffff" > /proc/sys/kernel/shmmax

I tried doing sudo gnome-terminal
then 
sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax

but I got permission error.

Do you know how to go around this?

---

### Post by bac on 2007-09-26
I went around to do vim to the file and I got this

WARNING: The file has been changd since reading it!!!
Do you really want to write to it (y/n)
"/proc/sys/kernel/shmmax" E667: Fsync failed

---

### Post by Amazona aestiva on 2007-09-26
> **bac said:**
> I went around to do vim to the file and I got this

WARNING: The file has been changd since reading it!!!
Do you really want to write to it (y/n)
"/proc/sys/kernel/shmmax" E667: Fsync failed

I advise only those solutions, which I tried.
So...
it works for me.

Could You post what Cinelerra said? Because if it isn't the same which I got, you will need another command!

---

### Post by Amazona aestiva on 2007-09-26
> **bac said:**
> Troubleshoot:
When got the attached picture/window, try this:
Type:
Code:
gksudo gnome-terminal

A new terminal appears and type this into it:
Code:
echo "0x7fffffff" > /proc/sys/kernel/shmmax

I tried doing sudo gnome-terminal
then 
sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax

but I got permission error.

Do you know how to go around this?
[COLOR="Red"]
YOU MADE A BIG MISTAKE!!!!!![/COLOR]
You typed:
sudo gnome-terminal

BUT You have to type:
**_gk_**sudo gnome-terminal

Do You understand now?
Try it again...

---

### Post by bac on 2007-09-26
Alright...thanks... it works now.... 

What is the diff between gksudo and sudo? 

Is it then only it logged you as root so you have permission to change the file?

---

### Post by Amazona aestiva on 2007-09-26
> **bac said:**
> Alright...thanks... it works now.... 

What is the diff between gksudo and sudo? 

Is it then only it logged you as root so you have permission to change the file?

I don't know the exact difference but I think...

sudo -------> do as superuser
gksudo ---> do as root

Yes I found that only root user can modify that file.

---

### Post by cmf04 on 2007-12-11
> **RJP said:**
> Something that may help some people having trouble installing Cinelerra....
I found this out the hard way after many hours of trying to install. Go through your source list and make sure you don't have more than one source for Cinelerra.
In fact, I would uncheck all xtra repositories you may have added besides the repo for cinelerra AND universe, multiverse and restricted repositories enabled. 
The Repo for Ubuntu AMD64's is what did the trick for me...
[http://cv.cinelerra.org/getting_cinelerra.php#ubuntu]("http://cv.cinelerra.org/getting_cinelerra.php#ubuntu")

This may sound confusing but what I encountered was two repositories that had different versions of Cinelerra . After I told myself to go back to basics in repo's and leave just the  Cinelerra repo and universe, multiverse and restricted repositories, to my amazement, Cinelerra loaded  without a hickup!

My machine is home built system with..
AMD Athlon FX-55
2 Gigs of Ram
Ubuntu Feisty Fawn 64 bit

Hope this helps some people and they're frustrations.

The AMD64 repo also worked for my AMD64 machine. After installing I had to run
echo '0x7fffffff' >/proc/sys/kernel/shmmax

---

### Post by anewguy on 2008-02-06
Many, many thanks for this!  I have fought trying to get Cinelerra installed in 7.10, gave up, reinstalled 7.04 and tried again, still no luck.  Had pretty much given up until I found your how-to.  Works great!!

Now all I have to do is figure how to actually USE the program!

Thanks again SO MUCH!!:)

---

