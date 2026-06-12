---
title: "I have Windows 8. I'm considering switching. I have a couple of questions."
date: 2014-06-14
forum: New to Ubuntu
---

### Post by Daniel_Comellas on 2014-06-14
Hi forum:

I'm considering switching to Ubuntu from Windows 8. I just have a few questions before I make the commitment.

1) I use a remote desktop client to connect to a server that hosts Quickbooks for my work. Is there a client I can use for Ubuntu?
2) I have my music saved on an external hard drive that uses the NTFS file system. Can I read/write onto it with Ubuntu?
3) Do I need an antivirus software of any kind?
4) I know I can't use MS Office. How does Libre Office compare?

Thanks,
Danny

---

### Post by yancek on 2014-06-14
1)If you mean a remote desktop client see this link:  [https://apps.ubuntu.com/cat/applications/precise/grdesktop/](https://apps.ubuntu.com/cat/applications/precise/grdesktop/)
2)Yes
3)Probably don't "need" it but I believe there are anti-virus programs in the Ubuntu repositories.  If not, they are available
4)I would say favorable but I guess it depends upon exactly what you expect from it.

---

### Post by 3rdalbum on 2014-06-14
1. Yes, there is a remote desktop client preinstalled and several others available
2. Yes, NTFS drives are mounted as read/write
3. No viruses on Ubuntu means no need for antivirus at the moment.
4. Libre office is capable, but not 100% compatible with the latest MS Office file formats. I don't think Libre office has all the features of Office but it has a decent subset. You can try Libre office on Windows now, or keep Windows 8 as a dual-boot with Ubuntu. If you need MS Office for anything you can boot into Windows.

---

### Post by gaxfax on 2014-06-14
> **3rdalbum said:**
> 1. Yes, there is a remote desktop client preinstalled and several others available
2. Yes, NTFS drives are mounted as read/write
3. No viruses on Ubuntu means no need for antivirus at the moment.
4. Libre office is capable, but not 100% compatible with the latest MS Office file formats. I don't think Libre office has all the features of Office but it has a decent subset. You can try Libre office on Windows now, or keep Windows 8 as a dual-boot with Ubuntu. If you need MS Office for anything you can boot into Windows.

I run MS Word, Excel & Powerpoint office 2007 on Mint 17 Cinnamon 64bit with Playonlinux no problem.

---

### Post by Impavidus on 2014-06-15
NTFS is supported by Ubuntu for both read and write. Using a Linux native file system may be slightly better in terms of speed and reliability, but keeping the music on an external ntfs drive will be fine. With a native Linux file system you can't access the drive from a Windows computer.

Note that Ubuntu (or any other Linux) is far from a drop-in replacement for Windows. Most people who decide to wipe Windows and install Linux without any Linux experience (the so-called cold-turkey conversion) are disappointed and end up reinstalling Windows. I recommend that you dual boot or install Ubuntu on a spare computer. Then you can get more Linux experience before fully relying on it.

---

### Post by Toby_Hubbard on 2014-06-15
1 for sure is you can dual boot (have 2 Os's) just select Install Ubuntu and install alongside windows

---

### Post by cwmoser on 2014-06-15
I support PCs and I know how people dislike Windows 8.1.
I think you will be well served to bite the bullet and learn Ubuntu Linux.
I've been using Ubuntu Linux for 7 or 8 years and have no problems with 
Libre Office.  If you are a power use of Microsoft Office, then you might
run into some compatibility issues.  There is Crossover product for ~ $50
that allows one to run Microsoft Office on Ubuntu Linux.

When I was a System Administrator for a local company, I was successful in using
a remote client to log into the companies computers.  There are several remote clients
with Linux and certainly one should work.  In addition, I was able to remote to my
home Ubuntu PC from work -- for this I used NXServer - very nice.

With Ubuntu Linux you don't need an Antivirus program -- I don't and have not be infected yet.
That might change in the future but right now hackers have made Microsoft their bulls eye.

Go for it.  Now is the time to make the switch.

Carl

---

### Post by bertan2 on 2014-06-15
Danny, a possibility for you is to first install Virtual Box under Windows 8, and then try out Ubuntu in a virtual machine. That way you can get to know its capabilities, while retaining your W8 system.

If you like it, a second step would be to try dual boot Windows 8 and Ubuntu.

---

### Post by Odyssey1942 on 2014-06-15
It might also be helpful to know why you are considering the switch. I "started" my switch several years ago by running Ubuntu on a second computer until I got familiar enough to switch over completely (didn't take long). Now I would not even consider switching back. Wife threw up her hands on Win 8.0 and now she is a happy 14.04 user. Neither of us like or use Ubuntu Unity, so if the appearance of Win 8 puts you off, there are alternative interfaces to Unity.

There is an old saying that 98% of MS Office users use no more than 2% of Office's features/capabilities, so if you are like us 98% you will be fine. If you are a power user and especially if you are one of several (they using Office) working on a project, then you will need to run Office under one of the programs that so enable (needs to be subject of a different thread, and already much to read in the Forums). There can be differences and incompatibilities on more advanced features (again many threads already in the Forums.)

While you can read from and write to a NTFS partition from Ubuntu (or another linux distro), I think that the files will not be readable from a Windows computer (don't know if this limitation applies only to files written from linux or whether once the writing starts (from linux) that all files on that partition will not be readable by Windows. So if this is important you need to follow this to a conclusion.) If you will not want/need to read and write to those files from a Win computer also, it will be better to format as EXT4 and move the files into the new format (you may need guidance on the best way to do that.)

I am still a noob, so any/all of the above subject to correction by more knowledgeable members.

---

### Post by Rob Sayer on 2014-06-15
The best way to try it is just download all the desktop versions and burn them to USB stick and then just boot them and try the desktops.  Don't use wubi.  USB stick live boot is much faster than optical disk so you can get a much better feel.

A lot of linux newbies don't seem to realize there are 4 different GUI interface versions of ubuntu.  Unity may be the 'default' version but I don't like it myself.  I use Kubuntu (KDE DE) 12.04 mostly at home and Xubuntu (Xfce) 14.04 on this netbook.  KDE is considered a heavy DE like Unity but you can configure it to lighten/speed it up, which you can't do with Unity.

XFCE (or LXDE based Lubuntu) is better for netbooks or older machines.  Some people like XFCE anyway even on faster machines.  I ran Lubuntu on this netbook before but it's just too clunky for me, though it's definitely fastest.  I don't really consider Lubuntu noob friendly either.

Definitely install dual boot especially if you don't have a lot of windows boxes lying around.  I rarely use Windows anymore but still have one Win 7 partition.  There *are* some tools that you can't find linux equivalents for.  They usually involve some kind of proprietary standard that's not available in open source.

For example, the Gimp image editor is fine for hobbyists.  But if you're publishing professionally it doesn't cut it.  You need to use a proprietary format used by publishers that isn't supported.  Same for Pantone support.  If you're a professional content creator you'll need Photoshop.

This isn't an issue for me except that if I want to rip/encode a DVD, linux tools won't handle newer copy protection schemes so I use a windows program.

Actually switching from windows 7 was pretty easy for me because I had mostly switched to apps that were linux ports.  I got sick and tired of installing windows programs (esp media) that installed crappy 3rd party codec packs that had compatibility issues.  All of a sudden everything's using these codecs.  This is largely because Windows permission levels stink.

Linux ported programs don't generally do this in windows because in linux the permissions work better.  You can't install something all that easily that makes system wide changes without warning.

Linux/unix is designed for security much more than windows.  For example, if you enter your user password incorrectly there's a 2 second delay before requesting it again.  This is mildly annoying but it makes it *much* harder for crackers to hack your password.  They generally use brute force methods so it's probably exponentially harder.

I do have a linux antivirus program installed (clamtk) but only because I still have a windows partition and I don't want a virus equipped file on there, or to give the file to a windows user.  But while I've only actually had linux installed for 2 or 3 years I know geeks who've been using it at home for 20 years.  Not one has an antivirus program running in the background like you need to in windows.

Hell, most personal computer linux users don't even run the firewall.  You don't need one like you do in windows unless you're running a server.

I'd definitely recommend installing ubuntu.  Actually windows 8 was, truth be told, mostly the reason I bit the bullet and installed ubuntu.  It wasn't even officially released yet but there was a guy in tech support at the local univ beta testing it and I didn't like what I heard.

Many noobs want to try to recreate their windows experience in linux.  Don't fall for that trap.  It's not windows ... it's actually more like Mac OS.  OS X is also derived from Unix and it's very linux like underneath.

---

### Post by Mark Phelps on 2014-06-15
LibreOffice provides many of the same features as the commonly used MS Office components -- but there are a few important considerations if you're going to switch to using it:
1) It doesn't work well in an environment where you're going to be exchanging Office files created by other folks using MS Office 2010 or newer.  While .docx files work some of the time, and .xls files work some of the time, there are compatibility issues.
2) Some Office components just plain don't work, or work so poorly as to be useless -- examples being Outlook and Project (to name just two)
3) The newer the Office product, the worse it works in Linux.  While some Office 2007 components work well (IF you force the files into the OLDER Office 2003 format!), less works well in Office 2010, and (AFAIK) Office 2013 doesn't work at all.

---

### Post by GrouchyGaijin on 2014-06-15
> **gaxfax said:**
> I run MS Word, Excel & Powerpoint office 2007on Mint 17 Cinnamon 64bit with Playonlinux no problem.

I run Office using Crossover - basically the same thing as PlayonLinux - a "more user friendly" version of WINE.
I have not had any problems, but I only run Word and PowerPoint.  I have no idea how Outlook would work.

---

