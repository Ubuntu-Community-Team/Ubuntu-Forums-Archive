---
title: "[SOLVED] Which Linux distribution?"
date: 2008-12-13
forum: Other OS Talk
---

### Post by Newuser1111 on 2008-12-13
[LIST=1]
[*]I don't like Arch. The fonts don't look right and I don't like pacman. It also has a lot of other problems I'm not going to list here.
[*]Kubuntu 8.10 started getting to many glitches and broke.(But it was very good when it was working correctly.)
[/LIST]

Requirements:
[LIST]
[*]Would work on a Compaq Presario F756NR
[*]Does not require me to use the terminal very much.
[*]Uses KDE or GNOME
[*]Has a lot of good programs available.
[*]Easy to mount other partitions/drives (As easy as Ubuntu does it.)
[/LIST]

---

### Post by Bachstelze on 2008-12-13
If you don't mind getting your hands (a bit) dirty at the beginning, I would recommend installing a command-line Ubuntu and building up from there. Systems built like that tend to be much more stable and light than those done with the default installers. I've just done that tonight and I was happily running KDE4 in well under an hour.

---

### Post by Newuser1111 on 2008-12-13
> **HymnToLife said:**
> If you don't mind getting your hands (a bit) dirty at the beginning, I would recommend installing a command-line Ubuntu and building up from there. System built like that tend to be much more stable and light than those done with the default installers. I've just done that tonight and I was happily running KDE4 in well under an hour.
No.
> Does not require me to use the terminal very much.

---

### Post by Bachstelze on 2008-12-13
If running three [font="Courier New"]apt-get install[/font] commands is "very much" for you, you're not going to find easily..

---

### Post by Newuser1111 on 2008-12-13
> **hymntolife said:**
> if running three [font="courier new"]apt-get install[/font] commands is "very much" for you, you're not going to find easily..I thought it would be alot because of the,
> If you don't mind getting your hands (a bit) dirty at the beginning,

---

### Post by Bachstelze on 2008-12-13
> **Newuser1111 said:**
> I thought it would be alot because of the,

Hence the "a bit". ;) Really, once you have a command-line system installed, and if you want KDE4, it's just

```
sudo apt-get install xorg
sudo apt-get install kde-core kdm konsole konqueror
sudo /etc/init.d/kdm start
```

And then do as you would do in a normal Ubuntu system.

---

### Post by Newuser1111 on 2008-12-13
Where would I get "command-line Ubuntu"?

---

### Post by Bachstelze on 2008-12-13
If you have a fast Internet connection, download the minimal ISO, and type "cli" at the prompt when you boot it.

[http://fr.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso](http://fr.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by Newuser1111 on 2008-12-13
> **HymnToLife said:**
> If you have a fast Internet connection, download the minimal ISO, and type "cli" at the prompt when you boot it.

[http://fr.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso](http://fr.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso)Is 80-90 KB/sec fast enough?

---

### Post by Bachstelze on 2008-12-13
It will take some time (with this, all the components of the system are downloaded from the Internet). If you can get a faster connection somewhere else download a [Kubuntu Alternate CD](http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/kubuntu/8.10/kubuntu-8.10-alternate-i386.iso), it will save you some time when installing (it will have most of the packages on it).

Maybe you can even install with the Alt CD, I'll try.

---

### Post by tashmooclam on 2008-12-13
Kiwilinux is Ubuntu but it has the little things already so you do not have to do a thing and it will play dvds, etc. So does Linuxmint, but it looks unique. Both use Gnome.  I use kiwilinux on my old HP laptop, works fine for me. PC/OS also is based on Ubuntu but is ready to go.

---

### Post by cardinals_fan on 2008-12-13
> **Newuser1111 said:**
> [LIST=1]
[*]I don't like Arch. The fonts don't look right and I don't like pacman. It also has a lot of other problems I'm not going to list here.
[*]Kubuntu 8.10 started getting to many glitches and broke.(But it was very good when it was working correctly.)
[/LIST]

Requirements:
[LIST]
[*]Would work on a Compaq Presario F756NR
[*]Does not require me to use the terminal very much.
[*]Uses KDE or GNOME
[*]Has a lot of good programs available.
[*]Easy to mount other partitions/drives (As easy as Ubuntu does it.)
[/LIST]
I would try **Fedora 10** first.  It's a very good release and has lots of graphical tools.  Here are some other choices:

* **Zenwalk**: this Slackware derivative uses Xfce, but it's easy to install KDE or GNOME if you prefer.  Fairly automated with simple tools.
* **Vector**: another Slackware-derived Xfce distro, with KDE available.  Lots of GUI tools and a remarkable amount available right off the bat.  Small, quasi-outdated repos.
* **SliTaz**: Hit or miss.  If it works, you'll love the speed and simplicity.  If it doesn't, you'd better know what you're doing.  Small repos, but growing very quickly.  If you decide to chance it, download the [latest Cooking]("http://www.slitaz.org/en/get/#cooking") iso (only 28 MB; how can you lose?)
> **HymnToLife said:**
> If you have a fast Internet connection, download the minimal ISO, and type "cli" at the prompt when you boot it.

[http://fr.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso](http://fr.archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso)
Only if you have an ethernet connection.  The mini CD doesn't work with wireless connections.

You can install a minimal system with the alternate cd (use Google).

---

### Post by Newuser1111 on 2008-12-13
> **cardinals_fan said:**
> I would try **Fedora 10** first.Ok. I'll try that.
(The download says it will take 2 hours.)

---

### Post by tommcd on 2008-12-13
I second the vote for Zenwalk. Zenwalk is fast, light, up to date, and stable. It is easy to use also, and has a lot of GUI tools available for system administration.

Ever try Slackware? If you can handle Arch you will have no problem with Slackware. The new Slackware 12.2 that just came out is excellent, and Slackware includes KDE. 
For extra programs that don't come with Slackware you can get slack-builds at slackbuilds.org. You can also get pre-compiled binary packages for Slackware at linuxpackages.net or slacky.eu.

---

### Post by cardinals_fan on 2008-12-13
> **tommcd said:**
> 
Ever try Slackware? If you can handle Arch you will have no problem with Slackware. The new Slackware 12.2 that just came out is excellent, and Slackware includes KDE. 
For extra programs that don't come with Slackware you can get slack-builds at slackbuilds.org. You can also get pre-compiled binary packages for Slackware at linuxpackages.net or slacky.eu.
I adore Slack, but I wouldn't recommend it in this case.  Slackware is superb for those who are interested in learning the details about how their system works and want to get their hands dirty.  Arch is significantly easier, in my opinion.

---

### Post by Sorivenul on 2008-12-13
I actually second hymntolife's suggestion.  

However, if you feel like apt-getting may be too much, I may suggest [Mandriva]("http://www.mandriva.com/en/download/"). There are both versions available for you to pick from, and the graphical tools available on Mandriva are, IMO, second to none.  To pick one version over another, I would suggest the GNOME version, but that's also personal preference.

EDIT: If you go with Fedora and are having problems downloading, use the torrents, I usually have better luck.

Cheers!

---

### Post by Newuser1111 on 2008-12-13
Currently Downloading:
zenwalk-5.2.iso
VL6.0-STD-B2.iso
mandriva-linux-one-2009-KDE4-int-cdrom-i586.iso
F10-i686-Live.iso

So this will take a long time.

---

### Post by SomeGuyDude on 2008-12-13
MEPIS, anyone? It uses Debian repos so I'd imagine it's pretty spot on.

Sidux gets a lot of love, though I have no idea how hard it is to set up.

---

### Post by Newuser1111 on 2008-12-14
> **SomeGuyDude said:**
> MEPIS, anyone? It uses Debian repos so I'd imagine it's pretty spot on.

Sidux gets a lot of love, though I have no idea how hard it is to set up.I'll try it after the other ones are finished downloading.

---

### Post by mentallaxative on 2008-12-14
> **SomeGuyDude said:**
> 
Sidux gets a lot of love, though I have no idea how hard it is to set up.

Sidux is easy to set up. Maintaining it is not so simple. Debian Sid can trash your installation if you're not reading the apt-get output properly.

---

### Post by mips on 2008-12-14
Try Mepis, Mandriva, OpenSuse, Linux Mint, PCLinuxOS.

One of them should suit your needs.

---

### Post by Newuser1111 on 2008-12-14
The Fedora 10 CD gets stuck at a flashing line in the top-left corner.

EDIT:
Mandriva is good, but the Network stuff keeps on disconnecting and the thing to install programs keeps on crashing.

Currently Downloading:
pclinuxos-2007.iso
LinuxMint-5-r1.iso
openSUSE-11.0-DVD-x86_64.iso
SimplyMEPIS-CD_7.0-rel_32.iso

---

### Post by Twitch6000 on 2008-12-14
PClinuxOS 2008 gnome edition or 

PClinuxOS 2008 minime might fit your needs.

You might also like Dream Linux 3.5.

---

### Post by Newuser1111 on 2008-12-14
PCLinuxOS 2007 Is having a problem,
On starting the CD, it says that it couldn't mount the LiveCD. How can I fix that?

---

### Post by Newuser1111 on 2008-12-15
Almost done downloading SimplyMEPIS-CD_7.0-rel_32.iso
openSUSE-11.0-DVD-x86_64.iso is at 32%

I still want to know how to fix Fedora's and PCLinuxOS's problems.

EDIT:
Finished downloading SimplyMEPIS-CD_7.0-rel_32.iso but can't write it to a CD because I don't have any CD-RWs right now.
So I'll try it in VirtualBox.
EDIT:
So far, it's good! I might install this if I get a CD-R and If it works with my computer.

---

### Post by alex.rayu on 2008-12-16
Use Ubuntu. It is the best Linux there is objectively (you need to work least to start working) that any other distro and it has the largest driver base, software repository that is largest of all, and a very active community that won't say things like "Don't you Google answers to your stupid questions yourself or read manual or recompile the core you lamer" =)

---

### Post by namegame on 2008-12-16
> **alex.rayu said:**
> Use Ubuntu. It is the best Linux there is **subjectively** (you need to work least to start working) that any other distro and it has the largest driver base, software repository that is largest of all, and a very active community that won't say things like "Don't you Google answers to your stupid questions yourself or read manual or recompile the core you lamer" =)

Fixed it for you...

---

### Post by Newuser1111 on 2008-12-16
> **alex.rayu said:**
> Use Ubuntu. It is the best Linux there is objectively (you need to work least to start working) that any other distro and it has the largest driver base, software repository that is largest of all, and a very active community that won't say things like "Don't you Google answers to your stupid questions yourself or read manual or recompile the core you lamer" =)Will Kubuntu 8.10 work now without problems?
Because I want KDE4.

---

### Post by sertse on 2008-12-16
I don't understand this thread a bit.

You want absolutely no problems, yet want KDE 4? KDE is still constantly evolving imo. I personally don't mind, but for someone who wants complete no fuss...you're asking a bit much. 

MEPIS still uses KDE3, which I think is a positive feature, and overall quite a polished distro for your needs. :)

---

### Post by kk0sse54 on 2008-12-16
Just curious really why don't you like Arch and pacman?

---

### Post by Newuser1111 on 2008-12-16
> **C!oud said:**
> Just curious really why don't you like Arch and pacman?[LIST]
[*]The Fonts and Font Sizes
[*]Didn't know how to mount other partitons
[*]Almost destroyed Windows Vista while installing Arch
[*]Pacman doesn't tell me the size of each file it's downloading.
[*]Pacman didn't find anything most of the time.
[*]It did not work with my laptop's WiFi.
[*]The X server had too many problems.
[*]My CD drive didn't work with it.
[*]I think the FN key didn't work.
[*]It would not correctly turn off the computer.
[/LIST]
There might be some things I forgot to add.

> I don't understand this thread a bit.

You want absolutely no problems, yet want KDE 4? KDE is still constantly evolving imo. I personally don't mind, but for someone who wants complete no fuss...you're asking a bit much.

MEPIS still uses KDE3, which I think is a positive feature, and overall quite a polished distro for your needs. If KDE4 still has problems, then KDE3 will work also.

---

### Post by Changturkey on 2008-12-16
> **Newuser1111 said:**
> 
If KDE4 still has problems, then KDE3 will work also.
?????

---

### Post by Newuser1111 on 2008-12-16
> **Changturkey said:**
> ?????Did I spell something wrong?

---

### Post by Changturkey on 2008-12-16
> **Newuser1111 said:**
> Did I spell something wrong?

I would not use KDE4 till atleast 4.2/4.3, and I really like KDE4. KDE3 will suit you fine, and MEPIS/PCLOS will do that for you.

---

### Post by Newuser1111 on 2008-12-16
> **Changturkey said:**
> I would not use KDE4 till atleast 4.2/4.3, and I really like KDE4. KDE3 will suit you fine, and MEPIS/PCLOS will do that for you.Ok, PCLinuxOS doesn't work on my computer, So I'll see if MEPIS does.
I still don't have any CD-RWs so I'm erasing the PCLinuxOS one and will put MEPIS on that one.

MEPIS works and it's good, I'll stay with that until I find a better one. I just need to get the WiFi working.

---

### Post by kk0sse54 on 2008-12-16
> **Newuser1111 said:**
> [LIST]
[*]The Fonts and Font Sizes
[*]Didn't know how to mount other partitons
[*]Almost destroyed Windows Vista while installing Arch
[*]Pacman doesn't tell me the size of each file it's downloading.
[*]Pacman didn't find anything most of the time.
[*]It did not work with my laptop's WiFi.
[*]The X server had too many problems.
[*]My CD drive didn't work with it.
[*]I think the FN key didn't work.
[*]It would not correctly turn off the computer.
[/LIST]


- Fonts are easily changed by just downloading a new set

- Could have edited your fstab so that your drives are auto mounted otherwise it's just as easy as mount /dev/sda<some #> /media/<whatever folder>

- Almost destroying another partition is not Arch's fault and can be otherwise remedied if need be by pre partitioning through another liveCD ie Ubuntu and Gparted

- While pacman does not give each individual file size (nor does apt and most package managers) it does provide the size of all the effected packages (package you want installed + dependencies)

- While I agree that pacman's repo are on the smaller side compared to a distro like debian it still has pretty much all the popular software for linux but when used in combination with the AUR repo and tools such as yaourt the size is greatly increased.

- I don't have a laptop so I don't have any experience with Arch and wifi

- You are not the only one experiencing problems with X [http://ubuntuforums.org/showthread.php?t=998273](http://ubuntuforums.org/showthread.php?t=998273) however rare and uncommon breakage is sometimes to be expected in Arch since it is a lot more bleeding edge than most distros.

- Don't know your cd drive so can't help you there

- Having specific keys on your keyboard not working (I'm assuming you mean the F and N keys) sounds more like a hardware problem but again I don't know what your keyboard is and if you are have compatibility issues with it in Arch you are most likely going to have that in a lot more linux distros unfortunately

- You'd have to be more specific than it would not turn off the computer correctly, for example instead explain what specifically happens (ie error messages)

---

### Post by Newuser1111 on 2008-12-17
> **C!oud said:**
> - Having specific keys on your keyboard not working (I'm assuming you mean the F and N keys) sounds more like a hardware problem but again I don't know what your keyboard is and if you are have compatibility issues with it in Arch you are most likely going to have that in a lot more linux distros unfortunatelyIt's the key to the right of Ctrl and to the left of the Windows key that says "fn" on it.
Does it really matter anyways? I don't have Arch anymore and don't plan on ever installing it again.

And, this thread is marked as SOLVED, so I will not be reading it anymore and if anyone replies then I will not see your post.

---

### Post by Antman on 2008-12-17
> **Newuser1111 said:**
> 
MEPIS works and it's good, I'll stay with that until I find a better one. I just need to get the WiFi working.
Good choice! Mepis 8 will be even better.

---

