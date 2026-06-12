---
title: "Difference between Fedora and Ubuntu?"
date: 2009-09-29
forum: Recurring Discussions
---

### Post by snakeman21 on 2009-09-29
Hi all.  I'm a fairly experienced Linux user.  I've tried many flavors in my time, but have stayed mostly true to Ubuntu.  As of now, I'm running Jaunty.

Fedora is one that seems to be pretty renowned, and I realized that I've never tried it.  I'm downloading it right now, but it's gonna take about an hour, according to Firefox.  (My download speed usually maxes out at about 325 kb/s)  

In the meantime, maybe someone could tell me what to expect.  From the screenshots I've seen, it looks very aesthetically pleasing, and I haven't heard anything bad about it.  

What are some key differences between Fedora and Ubuntu?  Does Fedora use .deb packages?  What desktop (GNOME, KDE, XFCE, etc.) does it use?

Whoa, make that like two or three hours... My speed is fluctuating between 50 and 200 kb/s

---

### Post by Hetor on 2009-09-29
Fedora uses RPM for package management and GNOME as primary DE. KDE version is also available.

---

### Post by Psycho.mario on 2009-09-29
Fedora uses Gnome, It looks pretty similar to Ubuntu apart from colouring. Im not sure on package type, but i think it works pretty similar to Ubuntu. IIRC

---

### Post by ackley on 2009-09-29
[FONT=Verdana]Fedora allows root access. You can use sudo as it comes preinstalled. Just add your username to the /etc/sudoers file.

Instead of apt-get, Fedora uses yum although apt is available for Fedora.


Personally, I don't find Fedora as user friendly as Ubuntu, but it's still a good distro.__[]("https://admin.fedoraproject.org/pkgdb/packages/name/apt?_csrf_token=26e06dc305c4d39824cf86aea4854537d14fa186")[/FONT]

---

### Post by mick222 on 2009-09-29
I really like fedora there are a few differences like fedora using rpm instead of deb . The only thing that puts me off is trying to get codecs for mp3 and dvd playback is a bit more trouble.Aso yum isn't as friendly as synaptic as a package manager.Of all the other distros i've tried i like mandriva best the "mandriva control centre is really good, nice distro if you want to try  out Kde"  but always come back to ubuntu.

---

### Post by sedawk on 2009-09-29
I'm using Fedora/RedHat at work and Ubuntu as desktop at home,
so let's see what comes to my mind ...

* Ubuntu uses *.deb packages, Fedora/RedHat/Suse use rpm packages
  I have to admit that I like the combo of yum+rpm more than
  the Ubuntu/debian jungle of tools (aptitude+apt-get+dpkg+...).
  What I like about rpm is "rpm --verify" which tells you if
  you/someone broke permissions on files or replaced files.
  But both are missing a repair option for permissions ...

* I think Ubuntu has a more complete set of desktop tools.
  E.g. the default user has the Administration menu to start
  "Users and Groups", "Synaptic Package Manager", or 
  "Update Manager".

* Unlike the Ubuntu-DVD the Fedora-DVD is full of extra
  software. So the Fedora-DVD is a much better choice
  for offline PCs.

* Ubuntu's way of discouraging root-logins and running
  "sudo" to get temporary root-access and integrate admin
  tools into the default desktop is a nice feature for
  desktops.

* Once in a while I have to struggle with Ubuntu while
  knowing that the same task would have been easy for
  me with Fedora. (VNC server setup, networking, runlevels,
  ...).

* Depending on the release date one distro might have newer
  versions of software packages than the other, but there
  is no real winner here as it seems to depend on the release
  cycle not the distro itself.

---

### Post by slakkie on 2009-09-29
Hi, see also: [http://ubuntuforums.org/showthread.php?t=1275103](http://ubuntuforums.org/showthread.php?t=1275103)

---

### Post by mick222 on 2009-09-29
Most distros i've tried are very similar under the bonnet it's just the choice of software desktop manager etc that separates them .

---

### Post by R3DHA7user on 2009-09-29
Hey guys,

I'm new here obviously...and I'm sure you can tell from the name that I'm coming from the RH/Fedora world. 

Sedawk pretty much covered what RH/Fedora and that whole .RPM camp is about. I'm here because I'm looking to go the opposite way. I'm getting a copy of Ubuntu today and a book to read up on the differences that I'm sure exist. From there I hope to be contributing to the community as all of you are. For now, I'll keep my head down, eyes open, and ears tuned into everything said here. I'm hoping Ubuntu will be all that I'm hoping for. Running redhat at home and work for 10-11 yrs. and not once had I "ventured" away from them. For the server it is cool, but I'm looking to have more fun at home and hopefully Ubuntu can offer that difference and put the fun back into computing. If you like tinkering then RH is for you, but I just want to see if I can have things work without doing so much work for a change. I'm certainly NOT going the Windows route so I thought I'd give Ubuntu a chance.

---

### Post by snakeman21 on 2009-09-29
Thanks, guys!  Firefox is telling me that Fedora should be done in under a minute, so as soon as I finish typing this, I'll plug in a USB stick and create a startup disk.  Perhaps I'll log on here from Fedora with some questions/opinions!

---

### Post by grturner on 2009-09-29
fedora started back in 2003/2004 and replaced Redhat 9. It is regarded as a more 'cutting edge' than ubuntu. Redhat uses it as a testbed for its enterprise level linux. It uses Gnome, KDE is offered as well. Fedora, like ubuntu comes with no proprietary software, and even with wireless drivers, ubuntu makes it easier to setup and use them, expect nothing of the sort from fedora. Fedora uses RPM(Redhat package manager) and uses yum(yellowdog update manager) instead of .deb and apt-get respectively. Fedora is a good system, i'm not discounting it at all, but i find that ubuntu plays to my needs better.

---

### Post by snakeman21 on 2009-09-29
Hmmm... I'm on Fedora 11 right now.  I used Unetbootin to make a live USB, and it worked with no issues (as I expected).  The interface is pleasantly familiar, due to it being GNOME.  One thing that's annoying me:  I'm on a laptop, and Fedora isn't recognizing when I tap the trackpad to click.  I have to actually use the buttons.  Ubuntu allows it out-of-the-box.  Strike one.  Fedora also isn't allowing me to use two-finger scrolling, while Ubuntu does.  Strike two.  It also won't let me use any visual effects.  Strike three.

On a positive note, it's very quick, especially considering that I'm running it from a flash drive.  

All things considered, it seems like a good system, and I'm sure it would be great with some tweaking, but I think I'll stick with Ubuntu for now.

---

### Post by slakkie on 2009-09-29
> **snakeman21 said:**
> Hmmm... I'm on Fedora 11 right now.  I used Unetbootin to make a live USB, and it worked with no issues (as I expected).  The interface is pleasantly familiar, due to it being GNOME.  One thing that's annoying me:  I'm on a laptop, and Fedora isn't recognizing when I tap the trackpad to click.  I have to actually use the buttons.  Ubuntu allows it out-of-the-box.  Strike one.  Fedora also isn't allowing me to use two-finger scrolling, while Ubuntu does.  Strike two.  It also won't let me use any visual effects.  Strike three.

On a positive note, it's very quick, especially considering that I'm running it from a flash drive.  

All things considered, it seems like a good system, and I'm sure it would be great with some tweaking, but I think I'll stick with Ubuntu for now.

I'm overruling one strike by a ball. Karmic has disabled tap-to-click as well. You can edit it by.. see this thread for all the details: [http://ubuntuforums.org/showthread.php?t=1267706](http://ubuntuforums.org/showthread.php?t=1267706)

The count is 2-1.

---

### Post by slakkie on 2009-09-29
> **R3DHA7user said:**
> Hey guys,

I'm new here obviously...and I'm sure you can tell from the name that I'm coming from the RH/Fedora world. 

Sedawk pretty much covered what RH/Fedora and that whole .RPM camp is about. I'm here because I'm looking to go the opposite way. I'm getting a copy of Ubuntu today and a book to read up on the differences that I'm sure exist. From there I hope to be contributing to the community as all of you are. For now, I'll keep my head down, eyes open, and ears tuned into everything said here. I'm hoping Ubuntu will be all that I'm hoping for. Running redhat at home and work for 10-11 yrs. and not once had I "ventured" away from them. For the server it is cool, but I'm looking to have more fun at home and hopefully Ubuntu can offer that difference and put the fun back into computing. If you like tinkering then RH is for you, but I just want to see if I can have things work without doing so much work for a change. I'm certainly NOT going the Windows route so I thought I'd give Ubuntu a chance.

Welcome btw :) Fedora is that bad when it comes to home computing? ;)

---

### Post by snakeman21 on 2009-09-30
I wouldn't say it's bad, it's just not my cup of tea.

---

### Post by cubdukat on 2009-09-30
For me, it's that Ubuntu works both on my desktop machine and my laptop, and Fedora 11 works right on neither of them.

To be fair, they both hate the NVidia accelerated drivers. They really need to look at that.

In fact, if it weren't for the fact that I can't get the NVidia drivers to work reliably on Mythbuntu Jaunty, I'd be using that.

---

### Post by Yellow Pasque on 2009-09-30
The last time I tried Fedora (10), it wouldn't boot the second time I used it (black screen of death). I really don't like package management with .rpm or PackageKit. I also have a wireless card than can only use ndiswrapper (rtl8180 chipset), and setting that up on Fedora is a pain compared to doing it on Ubuntu, any other Debian-based distro, or even Arch Linux.

That said, I do know people that really like Fedora, and it's a great playground if your goal is to eventually get Red Hat experience or certification.

---

### Post by snakeman21 on 2009-09-30
It looks like it has a lot of potential, I just don't care for it.  For someone that's not an eye-candy nut like I am, it seems like a great system.  I just prefer Ubuntu.

---

### Post by MisfitI38 on 2009-09-30
> **grturner said:**
> ...Fedora uses RPM(Redhat package manager) and uses yum(yellowdog update manager) instead of .deb and apt-get respectively. Fedora is a good system, i'm not discounting it at all, but i find that ubuntu plays to my needs better.
For accuracy, RPM actually now stands for (R)PM (P)ackage (M)anager, (somewhat of a misnomer nowadays since RPM is no longer a package manager itself, but a package file format).

Yum is not yellowdog update manager, but rather, (y)ellowdog (u)pdater, (m)odified.
Just F.Y.I.

OP: As for Fedora, it is quite a different experience from *buntu in many ways. It is very much a development distro, which relies on the users' competence much more heavily. 
Try it and see if you like their approach; it could be fun.

---

### Post by rookcifer on 2009-10-01
Differences off the top of my head:

1) Ubuntu uses DEB, Fedora uses RPM

2) Ubuntu has more packages in the default repos, though one can add extra Fedora repos.

3) Fedora has better security -- SELinux is enabled out of the box and Fedora compiles many of its apps with PIE/ASLR.  Also, Fedora utilizes Exec-Shield for executable space protection.  To my knowledge, Ubuntu is lacking most of these features.  The downside of this is that compiling these apps with these memory hardening features will degrade performance by about 5% (which is why you often see Fedora being slower on benchmarks).

4) Fedora enables root account by default.

There are other differences, but most of them are transparent to the user.

---

### Post by R3DHA7user on 2009-10-07
> **slakkie said:**
> Welcome btw :) Fedora is that bad when it comes to home computing? ;)

It's not "bad" it's just not really meant for home use. I know that sounds stupid, but it's not really the purpose of Fedora/RH. That concept came later when they tried desperately to compete for the desktop. It's still a server, developers tool, and a sys admin's dream come true. I got nothing bad to say about it...just ready to have some fun with something new.

For the record, started using Ubuntu 9.04 Jaunty Jackalope and LOVE IT!
,My wife passed the screen and said..."Wow that's a nice desktop theme " 
I had to explain I didn't change the theme...I changed the whole OS

---

### Post by hoppipolla on 2009-10-07
I couldn't get into Fedora 11 ._.

I tried, I really wanted to like it, but it just ran into too many hiccups and made me realize why Ubuntu is still the dominant distro despite many people's dislike of the brown colour scheme!

Fedora errored on me quite a few times, failed to install a few times, I never saw the fancy graphical boot I'd heard so much about, it didn't seem as friendly as Ubuntu...

I don't know, I just really went in there expecting to love it and came out itching to return to Ubuntu! :)

---

### Post by JDShu on 2009-10-07
Ahhh Fedora... or Fedora Core 3 when I used it :D

I was a total Linux beginner and had no idea what I was doing. Still, I didn't have any major troubles with it that I can remember. If its up to 11 now, I can only imagine that its better and very usable.

---

