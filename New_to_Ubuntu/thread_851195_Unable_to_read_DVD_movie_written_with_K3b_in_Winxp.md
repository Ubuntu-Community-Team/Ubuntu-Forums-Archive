---
title: "Unable to read DVD movie written with K3b in Winxp"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Henry10 on 2008-07-06
Hi all,

I am using Ubuntu 8.04 and have used K3b to write a dvd movie to a dvd. It writes without any errors and plays pefectly on my DVD player. However, when I try and access the DVD within Windows Xp, I am unable to see the contents at all.

Any help?? Appreciated!

---

### Post by wolfen69 on 2008-07-06
what app in xp are you using?

---

### Post by kellemes on 2008-07-06
> **Henry10 said:**
> Hi all,

I am using Ubuntu 8.04 and have used K3b to write a dvd movie to a dvd. It writes without any errors and plays pefectly on my DVD player. However, when I try and access the DVD within Windows Xp, I am unable to see the contents at all.

Any help?? Appreciated!

What mediaplayer are you using on XP?
Have you tried [VLC]("http://www.videolan.org/vlc/"), it plays just about everything out of the box.

---

### Post by Henry10 on 2008-07-06
I am using Windows Media Player 11. Only problem is when I open the DVD I cannot see any files on the DVD. I open the DVD in Ubuntu and I can see all the files.

Winxp do not show any files on the DVD and thus cannot proceed in reading the DVD to start any player.

It does work though on my DVD player connected to my TV.

---

### Post by jualin on 2008-07-06
You need to have a DVD codec in Windows Xp to play DVDs. Windows Media Player will not play the DVD if you don't have another applications such as PowerDVD or IntervideoDVD. Try playing another DVD in XP.

---

### Post by fatality_uk on 2008-07-06
You need a dvd decoders in XP don't you? At least that is my memory! You will need a DVD player in XP to try I think VLC

---

### Post by jualin on 2008-07-06
> **kellemes said:**
> What mediaplayer are you using on XP?
Have you tried [VLC]("http://www.videolan.org/vlc/"), it plays just about everything out of the box.

I think that VLC is the best option since you need to pay for most DVD decoders and VLC is free. :guitar:

---

### Post by Henry10 on 2008-07-06
What codec will be needed so that I can view the contents of the DVD movie written with K3b inside Winxp with Windows Explorer??

I can use any other DVD movie and it works perfectly inside XP. I can play the DVD via Windows Media Player. I can even view all the contents of the the DVD inside Windows Explorer. I do have PowerDVD installed as well.

My problem with the DVDs that I have written using K3b is that when I use it on the XP machine, and I want to look at the files, you know the AUDIO_TS and the VIDEO_TS folders and files inside, I do not see any folders on the DVD. It shows a blank DVD although the used space shows correct when viewing the properties of the DVD.


Any help??

---

### Post by jualin on 2008-07-06
Oh ok, in that case then I have no idea, sorry pal. Maybe recheck the format that you are burning the DVD in k3B. Now if you can play it in a DVD Player then I guess it may be another of the mysterious Windows XP problems.

---

### Post by cariboo on 2008-07-06
The only other thing I can think of is that the DVD is not being finalized. If I remember correctly finalize is not selected by default in k3b.

Jim

---

### Post by kellemes on 2008-07-06
> **Henry10 said:**
> My problem with the DVDs that I have written using K3b is that when I use it on the XP machine, and I want to look at the files, you know the AUDIO_TS and the VIDEO_TS folders and files inside, I do not see any folders on the DVD. It shows a blank DVD although the used space shows correct when viewing the properties of the DVD.


Any help??

Maybe you should check your Explorer settings, and search for the option to show system files or special files or something..
Surely Explorer has something like that.

---

### Post by ChildOfMana on 2008-07-06
> search for the option to show system files or special files or something..
Surely Explorer has something like that.

Off the top of my head it's View > Folder Options > Show Hidden Files (or something close to that anyway - it's been a while since I've dusted off my XP installation).

---

### Post by jualin on 2008-07-06
I think the "disc not finalize" answer can be a good solution. K3B is not going to make the DVD files hidden, plus if they are hidden Windows Media Player should be able to play it. Some DVD Players have the feature to play unfinalized DVDs, but maybe Windows can't read them.

---

### Post by real.africa on 2008-07-07
> **cariboo907 said:**
> The only other thing I can think of is that the DVD is not being finalized. If I remember correctly finalize is not selected by default in k3b.

Jim

I'd agree with making sure that DVD's are finalized so they will play in WinXP. Another thing to check is that you have an mpeg decoder that can deal with Audio/Video TS folders/files. Try TMPGencoder.
I had a problem seeing my DVD Ram contents [recorded from TV by RAM recorder] in WINXP until I got TMPG encoder. There are editing programs to buy from them, but they also have fully working trials to be sure they are what you need, AND also a FREE decoder codec.

---

### Post by Henry10 on 2008-07-08
Thanks everyone for all the help and input. I have found the solution, tested it, and it works perfectly.

Here is the problem and solution:

the bug lies somewhere in the patches between 1.1.6-1ubuntu3 and 1.1.6-1ubuntu6, that very release being part of Hardy.

I had to enable the gutsy repositories, downgrade genisoimage to the gutsy version (locking it, otherwise the system would re-install the newest version) AND to install mkisofs.

Solution: Open the Synaptic Package Manager and uninstall genisoimage-1.1.6-1ubuntu6.

If you have the following installed it will also be uninstalled:

brasero
dvd+rw tools
k3b
nautilus-cd-burner
ubuntu-desktop


Download genisoimage_1.1.6-1ubuntu3_i386.deb from 
[http://archive.ubuntu.com/ubuntu/pool/main/c/cdrkit/](http://archive.ubuntu.com/ubuntu/pool/main/c/cdrkit/)

You can choose to directly install it or download it to a folder. When complete, right click the file and choose the first option in the menu to install.

When the installation is complete you can reinstall the software that were uninstalled above.

---

### Post by fatality_uk on 2008-07-08
Good to see you got it sorted! However, still not 100% that I understand the issues. If it plays on your DVD player fine, and under Linux, then the issue is with Windows not being able to see the files! If there was an error in the DVD file structure, then a DVD player wont read it surely?

Anyway, mar the thread as solved please ;)

---

### Post by jualin on 2008-07-08
Glad it worked!

---

