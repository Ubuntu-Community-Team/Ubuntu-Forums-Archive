---
title: "Mandriva One Spring 2008"
date: 2008-07-17
forum: Other OS Talk
---

### Post by ofb on 2008-07-17
I've just taken the LiveCDs of KDE and Gnome out for a test, and I'm very impressed. 

Right from GO the display is correctly configured with the Nvidia driver. The same Ubuntu experience here starts with a flickering display that's far too large, making the menus almost too tiny to read. After installing Ubuntu you have to install the Nvidia driver, reboot, and then install & use nvidia-settings before you can finally set the proper refresh rate.

Mandriva has no trouble with the CDRW on my second box. That drive hasn't worked with Ubuntu since the 7.10 IDE debacle.
[http://ubuntuforums.org/showthread.php?t=599878](http://ubuntuforums.org/showthread.php?t=599878)

And then there's the Mandriva Control Center. Just /wow/. Why doesn't Ubuntu have something like that?

Everything else just works. Everything else just works with Ubuntu's LiveCD too.

I've been using U since 6.06 and I'm used to it. I've got my little collection of configuration notes for making installs work, and I know where things are. It's fine, and yes of course so much better than the messing around I used to do for Win installs.

But now I've seen Mandriva perform flawlessly from the LiveCD and I have to wonder why Ubuntu doesn't. I like Ubuntu but the niggling issues with display setup, the few IDE devices it doesn't like & still hasn't patched nine months later, and getting networking set-up, hold me back from recommending it to anyone that I'm not willing to spend an evening helping. You do not just 'install & go' reliably enough for me to recommend it to people who don't want a mild adventure. But it's looking like you can with Mandriva.

I've also read that the Mandriva installer defaults to setting up a separate /home partition. Ubuntu is still working on that.

Guess I'll be dual-booting one of my boxes with it to find out more. Anyone else done that with the current release? What gotchas should I be looking out for? Either Mandrake related or just switching from a Debian-based distro to a Red Hat based one for the first time?

---

### Post by Morty007 on 2008-07-18
I've always liked Mandriva. 

My only gripe is that the startup time seemed much longer than others, but then again if it does all the other things so nicely, well that's fine. 

I'm using Mint exclusively now, but have downloaded the gnome version and will give it a spin tonight.

---

### Post by wolfen69 on 2008-07-18
as far as ubuntu not working perfect for you, not every distro will work perfect for everyone. there are just too many different types of computers for that to happen.

and yes, i agree that mandriva is an excellent distro. if ubuntu wasnt around anymore, i would probably go with mandriva. it has worked well for me, and the package management is tolerable compared to most i've tried. not as fast and efficient as debian based, but good.

---

### Post by ofb on 2008-07-18
Did a quick install to a small partition. You just click the Installer on the desktop of the LiveCD.

The first difference is the Mandriva installer does not ask you to choose a user name. Language, location, keyboard, & time enquiries were all handled when booting the LiveCD, along with an EULA. There are a few other well-phrased questions that I just selected default for, except partition choice.*

On first boot after install it asks for a root pwd, username, & user pwd. These are well phrased. It doesn't ask you to choose a computer name.

Then there's a requested registration for hardware feedback. On the first click of this portion all the menu choices turned to Russian Cyrillic. I clicked back by guessing, tried again and got English. From there I just clicked Decline for all the choices to get on with the install.

And then it hung, not completing the boot. This was very possibly because I use the ScrLk key to KVM between machines; after ten minutes I hit ScrLk and was given a terminal login. I logged in and asked for reboot.

Rebooted, and found the new install remembered Nautilus & background preferences I'd set during the LiveCD session. That's a nice time-saver.

During the install one of the selections I defaulted through was the GRUB. Result is a nice graphical GRUB to dual-boot this Mandriva/Ubuntu computer.

I don't mind text GRUB, but I can see a graphical one being reassuringly modern to people new to computers. Ubuntu should probably do it by default too. Text GRUB was an option, had I not selected default.

I do note that the intial GRUB choices are Mandriva, Mandriva Safe Mode, and Ubuntu. You no longer have Ubuntu Safe Mode, and you do not get it as a choice if you select Ubuntu; Ubuntu simply boots.


* I didn't select default for partitions because this was dual-boot, and I meant to use a single small partition. By default Mandriva wanted to put / and /home on the first two partitions of the first drive, which would have overwritten my Ubuntu. So anyone dual-booting needs to have an idea of what partitions are, and specifically needs know what they have in terms of sda1 sda2 etc. I already had an extra partition handy, so can't comment on Madriva's partitioner.

Otherwise that was all I had to do to deal with dual-boot. Further choices like GRUB were simply default clicks.

Except for that, a reasonable but inexperienced person could install Mandriva fine. The only upset was that Cyrillic glitch. Not having to configure video is a big plus for the Linux-curious.

After running the first set of updates the install was less that 2.5 Gigs.

The computer is fully functional at this point. No messing with configuration for anything.

I'm using the Gnome version and it's quite similar to Ubuntu. The package manager is different but entirely as easy to use.

Next I suppose will be finding out what's involved with getting Opera and Konqueror since they are not choices on the package manager. (Opera makes sense I guess, but why not Konqueror? There are plenty of other KDE apps listed.) And I need to play with the Mandriva Control Center to see if it works as well as it looks. It's very encouraging to have networking choices like SMB and NFS right up front in a single central GUI.

Also I'll have to play a bunch of different types of media to see how well Mandriva has handled codec-heck.


Overall? It's looks slick and well-organized, as does Ubuntu, except for a lacking a feature like the Mandriva Control Center. 

If I /have/ to criticize, I personally find the few Mandriva-specific graphic design choices, like their logo & background, discouragingly clumsy. They really need to hire a designer. But that's only branding - the theme, fonts, icons etc are just fine and very similar to Ubuntu. Ubuntu's brand design isn't a favorite of mine, but it is definitely well done.

Mandriva uses a tighter smaller bolder default font. It works fine, but I do prefer Ubuntu's Bitsream choice. If I was converting from Windows, I might prefer Mandriva's.

---

