---
title: "looking for some views on suse ans arch"
date: 2008-02-15
forum: Other OS Talk
---

### Post by Cew27 on 2008-02-15
as the title says above what is open suse and arch like compared to ubuntu? avantages/disavantages 
thanks

---

### Post by LaRoza on 2008-02-15
OpenSuSE: Comes with almost anything one could want, DE's and nice tools for everything. It comes with Flash and Java too. It is (in my experience) a good distro wanting to install and not need to configure anything. A very good distro for those wanting an "out of the box" experience.

Arch: Comes with very little, and lets you make your own distro. Very good distro for those who know what they want and don't want extra.

---

### Post by smartboyathome on 2008-02-15
I don't know about OpenSUSE, but the advantages of Arch are that it is really fast and very customizable compared to Ubuntu. The disadvantages are that it is harder to install and set up.

---

### Post by Rumor on 2008-02-15
Well, Suse and Arch are very, very different from each other. I'll let someone else go into the advantage and disadvantages of Suse as my experience with it is very limited.

Arch is different from Ubuntu in many ways.
[LIST]
[*]Arch does not offer a live CD for you to "see it in action" so to speak. You have to install it and set it up before you can see what it is like.
[*]An initial install of Arch will leave you with a command prompt login screen. There is no default desktop or window manager. You have to set those up.
[*]Arch puts the control over what is installed on your system and what is running on your system completely in your hands.
[*]Arch's package manager, pacman, is (IMO) better than apt-get in both its simplicity and its usefulness.
[*]Arch is a rolling release meaning that there are no periodic monolithic distro upgrades. You install Arch one time only and then use one command to keep your system up to date. 
[*]Arch uses packages that are more current than Ubuntu and can be made as bleeding edge as you like.
[*]Arch puts the tools for building your own packages in your hands and gives you a community managed repository so that you can share your packages with other users.
[*]Arch is fast. Very, very fast.
[*]Arch is what you make it. Ubuntu is what the Ubuntu devs make it. Yes, Ubuntu can be made to be what you want it to be, but Arch starts out that way.
[/LIST]

These are just a few of the differences. There are others. These are enough for me to remain a happy Arch Linux user.

---

### Post by Cew27 on 2008-02-15
thanks for those views, that ahs frightened me, about arch not having a desktop enviroment how do you install this from the command line ?

---

### Post by bonzodog on 2008-02-15
Simply put, you need to be comfortable in the terminal if you want to use arch.
I have just installed it, and it's a core install, which means that when you install, you get a working command line, then it's up to you to configure the system by editing the rc.conf file, then you update the system for the first time using the pacman package manager, then **you** decide what you want to install using pacman.

The system will configure somethings straight away for you, often the net connection, but I would say that arch ranks as a Linux Power User distro, for those that can work without X comfortably, like using command line tools to do stuff, and don't feel they need their hand holding. Basically, you need to install *everything* via the package manager including X, then you have to configure X as well using the command line tool for it. Then you install the login manager, the WM/De of your choice, then decide what applications you would like. All from the command line. What you end up with is a system *precisely* tuned to your own personal tastes, with *only* the applications that you want. Lets put it this way; the beginners install manual is 42 pages long if printed to A4.

Suse, on the other hand, is the other end of the spectrum; it has a full set of tools, a graphical installer, and will install gnome by default and configure X for you. It's a very heavy distro compared to Arch.

---

### Post by Cew27 on 2008-02-15
ok i think arch is out of the question for now, what does suse have over ubuntu
also what is the difference between suse and open suse

---

### Post by LaRoza on 2008-02-15
> **Cew27 said:**
> ok i think arch is out of the question for now, what does suse have over ubuntu
also what is the difference between suse and open suse

Use OpenSuSE, it is free and a rename of SuSE.

OpenSuSE:
* Up to date
* Very complete, like Ubuntu + Restricted Extras
* Pretty by default
* Comes with KDE and GNOME on DVD, and comes with GNOME and KDE CD's. Live and Install disks available.
* It is slightly slower than Ubuntu in most cases, but it isn't drastic.
* It comes with Compiz also

The only thing I that it has over Ubuntu (in my opinion) is that it is more complete when installed, but it has non free software in it, like Flash and Java.

I just put it on my laptop recently, and it works with it fine. After the install, I installed Opera (my web browser of choice) and it worked fine with no work. I used 64 bit. Although I didn't find it to be better than Ubuntu, its ease of use and completeness would appeal to someone who doesn't want to worry about configurations.

It has a custom menu, but you can add the typical GNOME menu if you don't like it.

---

### Post by Cew27 on 2008-02-15
thanks for that 
what does ubuntu have over open suse

---

### Post by LaRoza on 2008-02-15
> **Cew27 said:**
> thanks for that 
what does ubuntu have over open suse

Ubuntu:

* Completely Free (beer and speech)
* More versions, like Kubuntu, Edubuntu, Xubuntu and Ubuntu
* Slightly faster in most cases, shouldn't make a difference really.
* Faster to install, OpenSuSE takes a longer time.
* Ubuntu (I imagine) will work on lower spec machines.
* Codecs, Flash, and Java are easy to install.
* Its package manager is better in my opinion.

Ubuntu is uses .debs and OpenSuSE uses RPM's. Both are easy to use.

---

### Post by Cew27 on 2008-02-15
ah thanks for that

---

### Post by igknighted on 2008-02-15
> **LaRoza said:**
> Ubuntu:

* Completely Free (beer and speech)
* More versions, like Kubuntu, Edubuntu, Xubuntu and Ubuntu
* Slightly faster in most cases, shouldn't make a difference really.
* Faster to install, OpenSuSE takes a longer time.
* Ubuntu (I imagine) will work on lower spec machines.
* Codecs, Flash, and Java are easy to install.
* Its package manager is better in my opinion.

Ubuntu is uses .debs and OpenSuSE uses RPM's. Both are easy to use.

1) Wrong.  Ubuntu includes non-free pieces (mainly drivers) by default.  OpenSuse does not.  OpenSuse, Debian and Fedora are the three

2) Suse has a default Gnome, KDE, Xfce and fluxbox install... and you only need one disk.  Or you can install from a single CD installer.

3) Debatable... but suse is probably a hair slower

4) Install time is always bashed with suse... it is a bit slower than others.  But you install once, I've never understood why this matters.  For what its worth... suse's installer lets you custom select every package installed if you choose, so I consider it a superior installer to Ubiquity.

5) Suse can run just as well if not better on low spec systems... just download the net install disk like Debian, and choose a WM like Flux or Ice (or use Xfce)

6) If you leave the default options, you will get flash and java-plugin installed (using the single CD installs at least).  Codecs are easily available with the pacman repository.  Plus the Hacking Suse 10.3 guide that is all over the net walks you through installing everything you could ever need.  I think it is the single best post-install guide available for any distro.  Concise, accurate and simple.

7) Zypper and the related YaST2 plugin aren't great, but they are certainly usable.  Smart is a good option if you choose to replace it, as is Yum.  Synaptic/Apt is available but apt4rpm really isn't good.  This is certainly Suse's weak point, but (imo) not even close to a deal-breaker.

EDIT: I don't mean to be rude, LaRoza... you're usually spot on.  I just think in this instance you are misinformed on Suse.

---

### Post by LaRoza on 2008-02-15
> **igknighted said:**
> 1) Wrong.  Ubuntu includes non-free pieces (mainly drivers) by default.  OpenSuse does not.  OpenSuse, Debian and Fedora are the three


It doesn't enable them unless you select them.

I wrote that post in response to a question. I did SuSE first.

I use OpenSuSE also, and am not fully up on it.

I am mainly refering to the default Ubuntu and default OpenSuSE, and I only installed OpenSuSE once recently with a CD version. (GNOME)

I don't think the install time is important, but it was a difference.

---

### Post by Cew27 on 2008-02-16
thanks for all this info :)

---

### Post by cprofitt on 2008-02-17
Arch is very easy to install... and to install KDE all you have to do is:
 
logon on to the system as root when it first boots; make a user account
```

adduser

```
it will walk you through making a user - add your user to the following groups
 
> 
floppy - Allows access to any floppy drives.
network - Enables the user to change network settings.
optical - Enables the user to access the CD drive. 
storage - Enables the user to mount storage devices through hal and dbus.
video - Allows direct access to video components. (Note: X can be used without being in this group)
wheel - Allow access to the root account through tools like sudo (if you enabled it via visudo).

 
Edit your pacman mirrors list
```

nano /etc/pacman.d/mirrorlist

```
 
Then run a the following code
 
```

pacman -Sy
pacman -S xorg kde

```
 
if you have an nvidia card you can install the drivers as well. I have nvidia so my initial pacman command is:
 
```

pacman -Sy
pacman -S xorg nvidia-96xx kde

```
 
You then have to configure X
 
```

xorg-configure
rm /root/xorg.conf.new /etc/X11/xorg.conf
nvidia-xconfig

```
 
There is an error in the current installer (if you use the ftp method in my case) so you have to correct the permission on the tmp directory
 
```

chmod 1777 /tmp

```
 
You also need to add some entries to the rc.conf file under DAEMONS. You will need to add dbus hal kdm to the end of the DAEMONS=() entry in rc.conf
 
```

nano /etc/rc.conf

```
 
reboot your machine and logon to a KDE machine.
 
The Arch Wiki is a very solid resource: [http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)

---

### Post by Cew27 on 2008-02-17
is that all the code i need to know before i am met with a desktop interface?

---

### Post by fwojciec on 2008-02-17
> **Cew27 said:**
> is that all the code i need to know before i am met with a desktop interface?

No.  If you're not comfortable with the command line or if you're not willing to put up with the steep learning curve until you master the basics then don't bother with Arch -- you'll hate it.  Installing Arch by copying and pasting commands just misses the point completely.

---

### Post by RedSquirrel on 2008-02-17
@Cew27: These two documents might help you decide if Arch Linux is for you:

[http://wiki.archlinux.org/index.php/FAQ](http://wiki.archlinux.org/index.php/FAQ)
[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

I think you would benefit from some more Linux experience on Ubuntu or elsewhere before trying Arch, but it's entirely up to you, of course. ;)

---

### Post by snakeeyes on 2008-02-19
I don't have experience with Arch, but openSUSE is my favorite Linux distribution and I will tell u why:

1. Its very polished, every little detail in suse makes it look as professional as Windows and OS X.

2. Its very stable, a lot more stable than Gutsy cause and many people on these forums found Gutsy to be very unstable. SUSE on the other hand has never randomly frozen or crashed at all for me.

3. OpenSUSE developers deal with bugs instantly meaning SUSE is almost bug free and u don't have to wait till the next release for the bugs to be fixed like they do with Ubuntu, and trust me its true, I no longer report Ubuntu bugs cause its totally pointless. 

4. OpenSUSE has a GUI tool for everything and Yast is awesome and configuring your system is simple on SUSE.

5. They have excellent documentation, thats something even Ubuntu is good at as well.

6. The forums r great just like these forums and they will help u till your problem gets solved.

7. All the applications which most people end up installing r already included in SUSE u have everything there out of the box.

8. Novell's has good support for the boxed version of opensuse as well.

9. OpenSUSE has the one click install technology as well, meaning u install a program with just one click as the name says.

10. All desktop environments r given equal importance unlike Ubuntu, we all know how inferior Kubuntu is to Ubuntu.

11. I find it odd when people ask whether opensuse has compiz fusion or compiz seeing that they r the ones who started the xgl/compiz project.

12. Thanks to their Microsoft deal they have better support for Microsoft Office 2007 file formats as well compared to other distros, just try opening a .docx file in opensuse and then Ubuntu and see what happens.

13. Someone here said opensuse is slower than Ubuntu, wrong, it was equally fast for me in loading applications and its boot time with the release of 10.3 is even faster than Ubuntu.

14. Yast has improved a lot in package management and there is always zypper as a command line package manager in suse. There r promises of even better package management in opensuse 11, u can install the apt system and synaptic in suse as well.

15. Its pretty by default.

I will have to say opensuse is better, I have used it for a long time and I liked every release.

---

### Post by LaRoza on 2008-02-19
> **snakeeyes said:**
> 
13. Someone here said opensuse is slower than Ubuntu, wrong, it was equally fast for me in loading applications and its boot time with the release of 10.3 is even faster than Ubuntu.

15. Its pretty by default.

I will have to say opensuse is better, I have used it for a long time and I liked every release.

Well, it is known for being slower. It may not be in every case.

Although I never keep defaults, OpenSuSE was good looking by default...no brown.

I liked OpenSuSE as well, although I won't say it is better. It was a very complete distro, and I could see someone using it without changing it at all. (Unlike Ubuntu where installing a few things is almost always needed, flash and such)

---

### Post by snakeeyes on 2008-02-19
> **LaRoza said:**
> Well, it is known for being slower. It may not be in every case.

Although I never keep defaults, OpenSuSE was good looking by default...no brown.

I liked OpenSuSE as well, although I won't say it is better. It was a very complete distro, and I could see someone using it without changing it at all. (Unlike Ubuntu where installing a few things is almost always needed, flash and such)
I agree but comeon opensuse loads apps as fast as ubuntu and 10.3's boot time is very fast, u must have noticed the boot time at least if u used 10.3.

---

### Post by LaRoza on 2008-02-19
> **snakeeyes said:**
> I agree but comeon opensuse loads apps as fast as ubuntu and 10.3's boot time is very fast, u must have noticed the boot time at least if u used 10.3.

Actually, I used it on my laptop, and was using my desktop at the same time, so I wasn't attentive.

It didn't seem slow to me, and it booted fast enough for me not to notice it.

I used 64 bit, and it was zero hassle to set up. Flash was already there, I just installed Opera and everything worked.

It is a very good distro, and I would recommend it to anyone.

---

### Post by kazuya on 2008-02-19
I would give opensuse a run again sometime. I have tried the last one. It was comparable to Ubuntu; But Ubuntu via Linux Mint still beats it for me. 
Opensuse for me has the look of polish, but not the ease of getting things I want. It is more a matter of familiarity. 

I would give opensuse a try tonight. I would see what has stopped me in the past from using it.

Archlinux on the other hand, while challenging at first is on of the fastest installs and upon completion is very feature rich, easy to use like any other distro, but what places Arch higher for me than any of the other distros {at least for a while now} besides the speed, is the ease of upgrading the distro and apps without requiring to reinstall a new OS.

It is very easy to maintain and very bleeding edge while remaining very stable. I still use arch and it is one of my favorite OS for about 3 months now. Vectorlinux is now what I use for now. Simple to install and gives the speed of arch.

---

