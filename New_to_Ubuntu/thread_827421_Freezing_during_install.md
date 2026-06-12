---
title: "Freezing during install"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Lazer08 on 2008-06-12
Hello,

I've been trying to experience Ubuntu for the past two days now and have come across so many initial problems that I'm at the point of being frustrated. I am an experienced Windows user that wanted to see what I could in Ubuntu/Linux that I couldn't do in Windows, mainly for security reasons.

I want to install Ubuntu on my laptop, which is a few years old and has only 256MB of RAM but it still runs XP like a champ for all intents and purposes (Reading, chatting, writing and researching). I was hoping to only have to download and burn Ubuntu 8.04 Desktop to at least get into a GUI environment then iron out various driver issues and such, but I have not been able to get past installation. I tried the "test but do not install" feature on the laptop and everything worked fine, a little slow but still functional. 

Anyway, after poking around Google I found out about Xubuntu, which seemed to be right up my alley for a lower-end system. The installation froze again, so then I found out about the alternate version that has lower system requirements, but the installation still freezes. Googling around more I read that disabling ACPI worked for some people. It worked to some extent, which got me further into the installation process, but freezes during the software install part at 2%. I'm out of ideas now after reinstalling again and again disabling the other features, but not getting anywhere new. Any ideas?

I burned all my ISOs at 1x, ran a MD5Sum and even tested it with the feature on the CD at bootup. 

Thanks for the help, I can't wait to get this up and running!

---

### Post by gr4nf on 2008-06-12
The ubuntu live install cd tends to be slow. try the alternate cd.

---

### Post by Lazer08 on 2008-06-12
> then I found out about the alternate version that has lower system requirements, but the installation still freezes

I tried that.

Oh and just to add, by freezing I mean my whole system freezes and I have to turn it off and back on to attempt the install.

---

### Post by gr4nf on 2008-06-12
Have you tried another distro? Maybe Debian? This could be a genuine BIOS or hardware problem.

---

### Post by Lazer08 on 2008-06-12
Have only tried Ubuntu and Xubuntu, along with their alternate versions. Was hoping to start learning off of an "easier" distro since I don't have any previous experience.

I guess I could try one, but having the installation go farther disabled ACPI makes me wonder what other options might be causing this.

---

### Post by nkri on 2008-06-12
Did you verify the integrity of the disk, i.e, confirm the checksum, before trying to install?  If not, boot from the CD and there should be a "check disk integrity" option, or something along those lines, on the initial boot screen.  If it tells you the disk is defective, DO NOT TRY TO INSTALL FROM IT (it could really screw up your computer)!  You can always re-download if you have to.  Good luck!

---

### Post by Lazer08 on 2008-06-12
Yep, I've done that on each ISO I've downloaded/burned. The disc works fine on my primary machine, my laptop is just not appreciating Xubuntu!

---

### Post by nkri on 2008-06-12
Oops, sorry, didn't see that in your original post.

Well, then, gr4nf is probably right about the hardware.  It takes a ton of ram to run an installation, and with a small amount it takes forever; I have 2GB and the install used ~90% of it, but that was Ubuntu, not Xubuntu.

---

### Post by Lazer08 on 2008-06-13
I ended up installing Xubuntu 6.06 LTS and upgraded to 8.04 LTS. A person with the same laptop as me had a similar problem: [http://ge.ubuntuforums.com/showthread.php?t=804385](http://ge.ubuntuforums.com/showthread.php?t=804385).

Well, this method is taking a lot longer, but at least I can run something :)

---

### Post by hyper_ch on 2008-06-13
are 256mb ram enough for the desktop cd? I have my doubts on that.

I was right:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)
> System Requirements

The minimum memory requirement for Ubuntu 8.04 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed. Low-memory systems may be able to use the desktop CD to install by selecting "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop started by selecting "Try Ubuntu without any change to your computer".

---

### Post by Lazer08 on 2008-06-13
Which is why I said I tried the Xubuntu alternate release instead.

[quote=http://www.xubuntu.org/get]
The Alternate Install CD only requires you to have 64 MB RAM.[/quote]

---

### Post by roger_1960 on 2008-06-13
> **Lazer08 said:**
> Hello,

I've been trying to experience Ubuntu for the past two days now and have come across so many initial problems that I'm at the point of being frustrated. I am an experienced Windows user that wanted to see what I could in Ubuntu/Linux that I couldn't do in Windows, mainly for security reasons.

I want to install Ubuntu on my laptop, which is a few years old and has only 256MB of RAM but it still runs XP like a champ for all intents and purposes (Reading, chatting, writing and researching). I was hoping to only have to download and burn Ubuntu 8.04 Desktop to at least get into a GUI environment then iron out various driver issues and such, but I have not been able to get past installation. I tried the "test but do not install" feature on the laptop and everything worked fine, a little slow but still functional. 

Anyway, after poking around Google I found out about Xubuntu, which seemed to be right up my alley for a lower-end system. The installation froze again, so then I found out about the alternate version that has lower system requirements, but the installation still freezes. Googling around more I read that disabling ACPI worked for some people. It worked to some extent, which got me further into the installation process, but freezes during the software install part at 2%. I'm out of ideas now after reinstalling again and again disabling the other features, but not getting anywhere new. Any ideas?

I burned all my ISOs at 1x, ran a MD5Sum and even tested it with the feature on the CD at bootup. 

Thanks for the help, I can't wait to get this up and running!
Hi
I recently installed Xubuntu 8.04 on my old laptop with 256M ram from the alternate CD.  It took hours - several times I was close to turning it off.  The process appeared to stop several times for up to 15mins but did eventually carry on.  Perhaps this is the problem?

---

### Post by tysonh on 2008-06-13
I had the exact same problem.  Mine would freeze at 15% and I'd have to hold the power button in to restart the machine.  I'm using a laptop with only 256 memory.  It seems ubuntu doesn't like that much memory.  Are you sure you got the right alternate cd?  I downloaded the text based alternate version and it installed with no problems.

Don't let text based scared you because its not a command line like install.  Its a step by step install you can figure out easy if you don't know much about computers in general.

I tried other distro's too. Freebsd and fedora both installed.  Fedora popped up a warning saying I didn't have enough memory to continue and it need to create a swap file to continue.

So when I ran the text install I resized my windows xp partition to allow about half the space to xp and the other half to ubuntu I also made a swap file equal to double my maximum memory I can have in this machine.

I'd say it took about a hour to install and be up and running.  Not counting updates.

---

