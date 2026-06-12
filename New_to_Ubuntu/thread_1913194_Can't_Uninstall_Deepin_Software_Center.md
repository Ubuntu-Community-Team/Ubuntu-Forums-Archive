---
title: "Can't Uninstall Deepin Software Center"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by sunewbie on 2012-01-22
I need help. 

I installed DSC in Ubuntu 10.04. I know it is for 11.10, my mistake.

Now it is stuck up at 'setting up deepin software center 2.0.5'

I can't run synaptic or update manager. Synaptic asks to reconfigure dpkg and again i am stuck up at 'setting up DSC'

Even update manager prompts for partial upgrades and then it's stuck up at same point

I have left it for 30 mins still nothing is happening.

I have installed 2 dependences libc-area2 and aria2 before manually installing deb file

source: [http://www.omgubuntu.co.uk/2012/01/how-to-easily-install-the-slickest-software-center-on-linux/](http://www.omgubuntu.co.uk/2012/01/how-to-easily-install-the-slickest-software-center-on-linux/)

Please help

---

### Post by derrickruthless on 2012-01-23
I'm attempting to remove Deepin Software Center as well. See if this gives you any luck:

sudo dpkg --purge --force all deepin-software-center

---

### Post by sunewbie on 2012-01-23
> **derrickruthless said:**
> I'm attempting to remove Deepin Software Center as well. See if this gives you any luck:

sudo dpkg --purge --force all deepin-software-center

Thank you.I also read your other post.

I will try when I get back to home.

---

### Post by Keeg64 on 2012-01-29
Aye, Yes. I am having the same problem. I have 10.04 and I installed DeepIn Software Center and now I cannot install anything through the Ubuntu Software Center nor through Synaptic. I ran the Purge line you mentioned earlier through the Terminal but It did not work and I am told 
"dpkg: status database area is locked by another process"

---

### Post by sunewbie on 2012-01-30
There is also another thread talking about same topic.

[10.04 tried to install deepin software center. Cant remove it now :(]("http://ubuntuforums.org/showthread.php?t=1913315&highlight=deepin")


I could not find any permanent solution. Instead of wasting time in troubleshooting, I downloaded xubuntu 11.10, Linux Mint and Bodhi Linux. 

I installed Xubuntu (as I do not like Unity) and installed apps that I wanted to. Sometimes, it is better to re-install or upgrade. it took 1 1/2 hours to create partition, install (35-40 mind with updates), then run update manager. Installed necessary apps (more time if you install more apps) like libreoffice, gparted, k3b, synapse, clementine (added ppa to get version 1.0.1, etc).

I installed XP + all 3 linux. If one crashes, other one is there.

Mint 12 has gnome 3 + cinnamon (in repos), works well, but bodhi is my favourite. You need to install apps separately, but you can also download them and save them. So just in case something goes wrong, then, I have ISO and all the apps. Again Bodhi installs very fast(5-10 mins) and operates very fast.

I like mint 12 + cinnamon also.

In xubuntu, I wont be doing anything stupid. It will be my backup distro.

---

### Post by cortman on 2012-01-30
> **Keeg64 said:**
> Aye, Yes. I am having the same problem. I have 10.04 and I installed DeepIn Software Center and now I cannot install anything through the Ubuntu Software Center nor through Synaptic. I ran the Purge line you mentioned earlier through the Terminal but It did not work and I am told 
"dpkg: status database area is locked by another process"

See posts 17 and 19 of [this thread]("http://ubuntuforums.org/showthread.php?t=1913315&highlight=deepin") (same as sunewbie posted). Sunewbie doesn't say if they tried that or not, but others said the procedure worked for them.
You shouldn't need to do a complete reinstall if you'd rather not.

And as far as dpkg being locked, apparently you have some other package managing software going. For info on how to resolve that, see [this thread.]("http://ubuntuforums.org/showthread.php?t=1911838") In your case you'd substitute "dpkg" for "apt".

Any more questions, ask!

---

### Post by sunewbie on 2012-01-30
> **cortman said:**
> See posts 17 and 19 of this thread (same as sunewbie posted). Sunewbie doesn't say if they tried that or not, but others said the procedure worked for them.
You shouldn't need to do a complete reinstall if you'd rather not.

And as far as dpkg being locked, apparently you have some other package managing software going. For info on how to resolve that, see [this thread.]("http://ubuntuforums.org/showthread.php?t=1911838") In your case you'd substitute "dpkg" for "apt".

Any more questions, ask!

Well my answer was similar to that of post no 18 - not working, same as that of author of that thread, so it's still not marked as solved. I searched for 'deepin' and waited for 10 mins. No results returned. So I lost my patience and thought that everytime I run something related to apt, I had to reboot and troubleshooting takes some time, while new installation takes 30 mins and I dont know anything about coding, so why not have a fresh install.

I was also having Grub problem, which I had posted in forums about a year back. It took 23 seconds to start with. Some other problems too (it's a long story). So I decided to replace 2 320 GB old HDD with one 1 TB. Now everything is normal and I have XP + 3 linux distros installed and grub loads without delay. At some point of time, I think most Linux user becomes distro hopper.

somehow, I did not figure out your last reply, post 19. I admit that I did not try your last option. Less patient + some more complications + wish to install multiple distros made me to take this step.

I also have ubuntu 10.04 inside virtualbox and always tried anything on this install and when system remains stable, I do it on my main system. 

This time I missed it, I carelessly tried it, knowing that Deepin is not officially supported by ubuntu and that too it's not for 10.04, it's for 11.10. So my mistake, my stupidity. Only good thing I did was to point keeg64 to the thread you had replied :)

In short my system was a mess, which I cleaned up.

As time passes my I am getting more familiar with Linux and it's culture and now I am regularly using it, unlike before  years when I occasionally used it and sometimes after 2 months. 

Anyways, thanks for the help.

---

### Post by cortman on 2012-01-30
> **sunewbie said:**
> 

In short my system was a mess, which I cleaned up.


Sure- in some cases reinstallation simply is the best solution- from what you describe, I'd say it probably was in your case.
Nice to see someone using Bodhi- I rather like that distro, with it's rather odd (by 2012 standards) E17 DE.
Keep learning and "acculturating" into the world of Linux, and good luck!

---

### Post by sunewbie on 2012-01-31
> **cortman said:**
> Sure- in some cases reinstallation simply is the best solution- from what you describe, I'd say it probably was in your case.
Nice to see someone using Bodhi- I rather like that distro, with it's rather odd (by 2012 standards) E17 DE.
Keep learning and "acculturating" into the world of Linux, and good luck!

I thought that Bodhi would also become slow after making it ful-fledged system, with all the apps installed that I needed, still it is very fast.

For day - 2 - day use, I only surf net, listen to mp3s, and occasionally burn DVDs. I wanted to keep Bodhi minimal, but ended up installing all apps I needed like inkscape and gimp :)

It sure has a learning curve and has some issues like changing mouse to left handed does not work, so you have to run  script and make it run at startup, either manually or through .desktop file.

I like to run app from keyboard and use synapse, so mint menu makes little difference when you want to launch anything, E17, has everything, which does same thing. E17 is different, but I like it.

I would never be away from *buntu and in future, I will definitely ask and try something weird in virtualbox, before implementing on main system.

---

### Post by sunewbie on 2012-01-31
@Keeg64

if you are able to solve this issue, do reply, so that I can remove the [unsolved] tag in the title.

---

### Post by arexsekerat on 2013-03-09
hye,

1) open terminal
2) gedit /var/lib/dpkg/status
3) CTRL+F 
4) Type "deepin" ... then u delete all deepin words and save .. 

Work For ME :-\"




regards,
kejunGs

---

### Post by lisati on 2013-03-09
Much can change in the space of a year.

Old thread closed.

---

