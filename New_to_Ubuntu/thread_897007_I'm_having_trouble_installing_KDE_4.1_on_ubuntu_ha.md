---
title: "I'm having trouble installing KDE 4.1 on ubuntu hardy"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by student21 on 2008-08-21
I have a 64 bit wubi hardy installation on my HP dv6833 laptop.  I just pasted the following code reading from this forum in the terminal: 

sudo aptitude install kubuntu-desktop

but it installed kde 3.5.9.

Then realising the error I searched on forums again, I gave 

sudo aptitude remove kubuntu-desktop

to remove it for further installation of kde 4.1, but everytime i choose the session from login screen, I guess KDE 3.5.9 still  remains because the session goes to KDE.

Then I even added 

[http://ppa.launchpad.net/kubuntu-members-kde4/Ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/Ubuntu) Hardy main 

to software sources after reading on this forum and then pasted 

 sudo aptitude install kubuntu-kde4-desktop

but still I don't get to access kde4.1, I get to see the same 3.5.9.  How can this situation be rectified??

---

### Post by youthforlinux on 2008-08-21
hey did you make sure to run

```
sudo aptitude update
```

after editing /etc/apt/sources.list

also double check to see if you have it on one line in /etc/apt/sources.list like this

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

then try:

```
sudo aptitude install kubuntu-kde4-desktop
```

it should install KDE 4.1

---

### Post by nynoah on 2008-08-21
KDE 4.1 is still very buggy....so use it with caution.

---

### Post by natman on 2008-08-21
If you want to know if you have KDE4.1 have a look in your home for the "./kde4" directory. Also at the login screen you will have to select the KDE4 option ( it ill default to the last used session KDE 3.5 for you ) just click on the little icon beside the password box, and hit session type, and select KDE4.
Have fun it a nice desktop, but not everything works, fingers crossed for KDE4.2 :)

---

### Post by student21 on 2008-08-22
Hi guys thanks for your replies.

I checked and following line is there in /etc/apt/sources.list 

 ```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

oops, I didn't run
```

sudo aptitude update
```

May be that was an error.

Now I have run Sudo aptitude update and sudo apt-get update.  So I guess now 

```
sudo aptitude install kubuntu-kde4-desktop
``` will work.

But before that I'm not sure what should I do with KDE 3.5.9.  Should I be removing this manually or kde 4.1 installation will take care of that?  I don't know why ```
sudo aptitude remove kubuntu-desktop

``` has not worked and what would be the best way to remove it?

And I don't find anything like "./kde4"  in my home.  Should I look for that in something else?
> 
KDE 4.1 is still very buggy....so use it with caution

That looks scary, because the usual stable hardy ubuntu gnome itself is giving me headaches/stability issues now and then.

And I'd also like to keep my splash screen the orange progressive bar of ubuntu rather than kubuntu's.  How can I do that in a simplified way?

---

### Post by coffeecat on 2008-08-22
> **student21 said:**
> [http://ppa.launchpad.net/kubuntu-members-kde4/Ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/Ubuntu) Hardy main 

You've made two tiny errors which have big consequences. That should be 'ubuntu', not 'Ubuntu', and 'hardy' not 'Hardy'. Have a look at [this softpedia howto]("http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml"). Correct that source line and all you should have to do now is to click on the Install KDE 4.1 link in the howto.

Happy KDE-ing. :)

---

### Post by youthforlinux on 2008-08-22
Um, I'm running KDE4.1 right now and it's been great...only thing i would do is to keep 3.5.9 for now, just to be sure you're ok with 4.1,

To remove KDE 3.5.9, go to this link and run the 3rd command, titled remove kubuntu:
[HTML]http://www.psychocats.net/ubuntu/puregnome[/HTML]

Also to make usplash orange ubuntu do this:

```
sudo update-alternatives --config usplash-artwork.so
```

and select the ubuntu one from the list by specifying the number.

---

### Post by student21 on 2008-08-23
Hi Thanks for the replies.

At last KDE 4.1 installed on ubuntu hardy with the command 

```
sudo aptitude install kubuntu-kde4-desktop

```
This desktop looks cool and alluring--  better than gnome and kde 3.5.9.  But I've got a handful of Sigsegv messages with this desktop.  Also my laptop's touch panel controls like mute volume and volume tuner aren't working on kde 4.1, but they worked on gnome.

Can anybody point to a resource to some 'how to' where I can learn a few tips, tweaks, additions (including 3d desktop effects, wallpapers, multimedia codecs, tools or whatever that can improve the performance aesthetically and productivity wise) that will enhance my experience with kde 4.1 and make my work less complicated?

Since 

```
sudo aptitude remove kubuntu-desktop

```
didn't work to remove the kde 3.5.9, I guess I'll have to resort to apt-get command that includes many more programs.  But I'm wondering if the package installed with 'aptitude install' will be removed with 'apt-get remove'?

Any way for some days I'm going to keep this too.  But I've got two two programs in same names like ark, dolphin etc on my menus.  

I did choose a number for ubuntu splash work after giving this command on terminal

```
sudo update-alternatives --config usplash-artwork.so

```
but this works only when the system is shutting down.  When it boots again I get kubuntu splash work.  How can I make it work for both boot and shut down?

And somehow I've got my spelling wrong while posting on forum about

[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

 but in 'software sources' the spelling was right.

---

### Post by coffeecat on 2008-08-23
> **student21 said:**
> I did choose a number for ubuntu splash work after giving this command on terminal

```
sudo update-alternatives --config usplash-artwork.so

```but this works only when the system is shutting down.  When it boots again I get kubuntu splash work.  How can I make it work for both boot and shut down?


Have a look [here]("https://help.ubuntu.com/community/USplash"). Ignore 1 and 2 unless you want to install more usplash themes. After the update-alternatives line, do:

```
sudo update-initramfs -u
```

---

### Post by eightmillion on 2008-08-23
> KDE 4.1 is still very buggy....so use it with caution.
KDE 4.1 is not "very buggy". I've been using it exclusively for quite a while and have had only very minor issues. It is quite stable.

---

### Post by psycosmyth on 2008-08-23
I wish I saw a post like this a week ago! I made a MESS of my system.
To be honest from someone who has done everything you just did, it's easier to download the community edition of Kubuntu with KDE4 and put it on another partition. I like to have my 4 apps separate from the 3.5.9 ones.
To appreciate 4, it's nice to see it in it's raw form free from GTK and KDE3. There are apps and the like for KDE4 being written right now like mad so be patient and enjoy. You would make a great addition to the Brainstorm team too!

---

### Post by student21 on 2008-08-24
Hi all

```
sudo update-initramfs -u
```

I typed this code in terminal and properly turned off the system some hours ago.  But from next boot, system has gone crazy :(:(.

When I select ubuntu from boot screen, it displays a message:

```
Unrecognised Partition table for drive 81.  Rebuild the file system using windows file system tool fdisk, err=22
```then displays ubuntu orange progress bar for a few seconds and then gets to a message on blank screen saying:

```
Busybox v1.1.3 (initramfs) [41.152962] sd 0:0:0:0 [sdb] Assuming drive cache:write through [41.156219] sd 0:0:0:0 [sdb] Assuming drive cache:write through

(initramfs)[type help for initramfs commands].
```

How hard I try or how many times I try I get to see the same message with slight variation in numbers enclosed in square brackets above.  If I keep trying many times at a stretch, even I can't boot into windows vista it just hangs.  Fortunately I was able to boot into this time after a gap and I'm typing this message.  Please help in simple terms how can I rectify this situation??

---

### Post by youthforlinux on 2008-08-24
using wubi right?

if that is the case boot into Windows.

Go to My Computer and right click on you hard drive(probably C) and go to properties...then go to the tools and go to scandisk....its menu will pop up then make sure automatically fix errors is checked...then press ok and it will tell you that the computer needs to reboot before the disk check can take place, then reboot windows, and choose to boot into windows again, then after the disk check occurs reboot into ubuntu...to prevent this problem do not incorrectly shutdown windows, because wubi uses your windows partition, but will not mount if it is not shut off properly! :) :) good luck post any questions

---

### Post by student21 on 2008-08-24
Hi **youthforlinux ** 	


Thanks for your reply--yes I use wubi installation.  My last post was from windows vista.  Now when I booted after some hours, it's booting Ubuntu and I'm posting this from KDE 4.1 desktop.  I guess last windows boot resolved the issue and I'm keeping my fingers crossed. 

Before that windows boot, last windows boot was a couple of days ago and it indeed was a proper shutdown and only today that too after giving the command(update initramfs) on terminal(I gave this command choosing terminal from KDE 4.1) this has happened.  Was this error caused by the terminal access from KDE 4.1 or if it was something to do with the command itself??

Sometimes on KDE 4.1 I get windows(everything including firefox, konqueror, amarok etc) without minimise, maximise and close buttons for the entire session.  Not sure if it's to do with bugs. Also many icons look with "?"(question mark).  But one fantastic thing about  KDE 4.1 is the presence of some video player  'dragon player' that's competitive to VLC.

And yes I've 2 questions:
 
1) When I gave sudo aptitude remove kubuntu-desktop for the first time after installing 3.5.9, it said it's removing the desktop and leaving some packages intact.  But whenever I choose a KDE session it goes to 3.5.9 KDE, how can I make sure what I have is full intact 3.5.9 KDE and not some stripped down thing and if its stripped down thing how can I fix it, till I decide to remove it entirely??

2) And if I want to remove KDE 4.1 what command should I use? When will this KDE 4.1 be patched?

And **psycosmyth** what do you mean by brainstorm team?  Yes its a bit annoyance to keep applications of KDE 3.5.9 and 4.1 together, some 4.1 applications don't work in 3.5.9, but I've heard that every application is common to gnome, XFCE and KDE and why this incompatibility for some 4.1 applications?

---

### Post by youthforlinux on 2008-08-24
Hey.  Sometimes wubi can act a little funny depending on the state of your NTFS partition...maybe if you are ok with ubuntu, later you could attempt a normal dual-boot system.

Question 1:

well, you are asking if you want a full KDE 3.5.9 right?  If so then ```
sudo aptitude install kubuntu-desktop
``` should work ok

Question 2:

If you used aptitude to install KDE 4.1 then ```
sudo aptitude remove kubuntu-kde4-desktop
``` should remove all of KDE4.1, though update for KDE 4.1 are in the process, if you keep yourself updated you should notice bugfixes!

I've never had those max, min, close, button problems before, something might be wrong with your installation, try to see if anyone else has a similar prolbem, because i have never had that problem, even with KDE 4.o

---

### Post by student21 on 2008-08-24
Hi youthforlinux

I'm also thinking of moving wubi installation to dedicated partition, but I'm just overwhelmed of the tasks involved besides my being newbie in this area.  First I need to create primary partition, then should figure out home and root and swap partitions. All this after readjusting NTFS size.  Then use LVPM to move this partition.  But I'm not sure if gparted can be used from gnome or kde to adjust existing NTFS and create new partition??  Some say it's only possible using live cd?  Can you please throw some light on this?  Also can you tell me if I would be required to allot space for home and root in dedicated install when i have not alloted for them in wubi installation?  Is there a windows alternative to do all these jobs?



```
well, you are asking if you want a full KDE 3.5.9 right? If so then

```

No, I already have working KDE 3.5.9 despite removal commands, but I'm not sure if its full package that got downloaded initially or it's a stripped one after my ```
sudo aptitude remove kubuntu-desktop
```?  Is it possible if I again gave that aptitude install for kubuntu-desktop --it'll fix if anything is missing?

Should I give aptitude update before removal?

> I've never had those max, min, close, button problems before, something might be wrong with your installation, try to see if anyone else has a similar prolbem, because i have never had that problem, even with KDE 4.o

Don't know what could be wrong with the installation, but adept says its up to date and has no errors.  Also when it was installed it didn't give me any error.

---

### Post by youthforlinux on 2008-08-24
Well the transfer of Wubi to a dedicated partition isn't too simple, so if you are ok with it, you could just use windows to uninstall wubi, and then reinstall ubuntu with the live cd, if that really doesn't appeal to you and you are ok with going ahead with the LVPM method, 

[http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")

is a great tutorial to get this all done:)

> ? Is it possible if I again gave that aptitude install for kubuntu-desktop --it'll fix if anything is missing?

yes running that command should make sure that the dependencies are installed, someone correct me if i'm wrong.

also that tutorial shows you how to get your hard drive resized, but it might be too complicated for you to do, just post if you have any questions about the lubi tutorial.


oh i forgot before, make sure if you do resize your windows parition that you back up your important windows files, as their is always a chance of messing up your drive and such.

---

### Post by student21 on 2008-08-26
Hi Youthforlinux

Some queries I hope you'll be able to answer:

1)  Should I install same version of programs separately in gnome and KDE?  like should I install applications marked with kubuntu on update managers?  There are some weird things happening on my system.  Like a text file on KDE 4.1 tries to open with Mplayer and ends up with an error saying can't play this file. But it opens very fine on gnome.  So what should I do with such file association inconsistencies?

2)  Sometimes I notice that booting process comes to halt just with splash screen and no other controls.  I'm only left to turn off the system by pressing power button for few seconds.  How can I avoid this?

3)  I've found out that windows lose min, max and close buttons after a windows decoration error with sigsev message.  I don't know if any body else is experiencing this.  But if any moderator happens to see this message please mark it a bug.  

4)  I want to know for sure, if I can use gparted from my wubi because I've installed it now but I want to know if it will work from wubi?

5)  Is this transfer by LVPM not safe?  Because I've never backed up things unless system goes for full format.  

6) Tutorial's videos are not working for me.  So my doubt is, how will I find an ext3 formatted partition----if its sda3 or sdb2 or hda3?  Where should I find this information?

---

### Post by youthforlinux on 2008-08-27
Hey student21, after reading your post, I think that it may be best for a complete reistsall.  It will help you to address problems more easily than tweaking your current system.  And i mean a regular install because if you're planning on using ubuntu properly, a regular system is going to have better performance anyways.  But, you definitely should reinstall ubuntu, wubi or not.

Let me try to answer your questions from above:

1.  Those bizarre file association problems are not normal.  U don't need to install the same programs twice as gnome programs should run on KDE and vice versa.  So if you get kubuntu and you want pidgin, then install pidgin will allow you to use it in gnome and in KDE.

2.  This could be caused by a variety of factors.  When i use wubi and this happens it sometimes has to do with my ntfs partition being corrupt.  Basically a regular install doesn't use your windows partition, so it is not dependent on it to function.

3.  The sigsev error is probly a kde4.1, i use it a lot now, but there are bugs, and even though KDE 4.1 looks cool and all, a newbie might be better off to wait until Intrepid for KDE 4.1 to be fully integrated.  Right now your priorityis to get a useful system and gnome and KDE 3.5.9 can do that beautifully.

4.yes gparted will work from wubi, but as i will describe below it might be better to scrap wubi for now.

5.  Resizing partitons is never a 100% guaranteed success, and whenever you resize a partition, you need to be aware that data could be lost--Trust me it has happened to me.

6.  Finding out your drives is done through the command:

```
sudo fdisk -l
```

It lists your disks for you.

But here is what I personally would recommend to you.  Basically, wubi is allowing you to use your windows partition so you don';t need to resize your NTFS partition to make room for linux.  But the LVPM idea needs that free space, but since you have all these problems, I will give you a couple of options here:

Option 1:

Uninstall wubi from windows.  Then if you are using Vista, use its Disk Manager to shrik theVista Partition(however, I have never been able to get Vista to properly shrink mypartito, to the size i wanted--also defragment first).  If you have XP, then you have no choice but to use gparted from the Live CD to try to shrink.  But remeber this, shrinking partitons is dangerous business!  You have to be ready to assume that your data will get corrupted.  So you should do a backup even thought it will work.  So after using the live CD to shrink windows, you just do a regular install.

Option 2:

Use LVPM to do this, so you don't need to do another install.  I would not recommend this because it is difficult for newbie's to understand partitioning that much, also since your install has so many problems, it is defintley better to do a regualr install, also this way needs to resize the partition, so if you're ok with resizing, you'll probably be better off with Option 1.

Option 3:

Reinstall wubi.  Basically uninstall it and reinstall it in windows, and have me or someone else give you better tips on maintaining the system, I would gladly help you to manage your system better to prevent conflicts between gnome and KDE.  Only thing is that this way, you are still dependent on a clean windows partition, but correctly shutting down can always help.  Also you hard drive performance is not as good as a regular installation.

If I made any mistakes with this post, I'm sorry, but if you have any other questions, just ask.  But if you decide for regular install, you MUST BACKUP what you need off windows.

ttyl,
youthforlinux :)

---

### Post by student21 on 2008-09-02
Hi **youthforlinux**

Sorry for the delayed response.  I appreciate that you're giving me the suggestion of scrapping this installation in good intentions, but still personally I'd like to keep it because of many reasons.  Is there a way to back up "Bookmarks" in firefox, configurations and other things that would have to be backed-up so that I can have some things intact for fresh install??.  Even if I want to install I'll install from hardy 8.04 as I've a live cd for it and not for 8.04.1.  I can't download 8.04.1 for I have limited net connection.  So there's a possibility that new install could also be unstable:(

> 1) Should I install same version of programs separately in gnome and KDE? like should I install applications marked with kubuntu on update managers? There are some weird things happening on my system. Like a text file on KDE 4.1 tries to open with Mplayer and ends up with an error saying can't play this file. But it opens very fine on gnome. So what should I do with such file association inconsistencies?

I have had success in working around this issue;  Right clicking the file and choosing 'Properties' and then 'Edit File type' icon and choosing Kate,gedit for text files, openoffice.org word processor for document files and choosing 'document viewer' and 'Kpdf' for .pdf files showed some dialog box telling me that system configuration was being updated.....from then onwards text, document and pdf files open in appropriate software and not in mplayer or pdf opening with error in word processor.  But still I've trouble with .rar files as I don't know what association will be used in Kde 4.1 but in kde 3.5.9 it opens with 'ark'.  **Except this rar issue I don't have much conflict of applications(like pidgin etc) between gnome and KDE 4.1.**

> 2) Sometimes I notice that booting process comes to halt just with splash screen and no other controls. I'm only left to turn off the system by pressing power button for few seconds. How can I avoid this?  This is happening frequently in KDE 4.1. and only once in gnome.  A recent error in KDE 4.1 is:

[I]Dcop communication error(KWD)
There was an error setting up inter-process communication for KDE. The message returned by the system was:

Could not open network socket. Please check that the 'dcop server' program is running!
[/I]
> 3. The sigsev error is probly a kde4.1, i use it a lot now, but there are bugs, and even though KDE 4.1 looks cool and all, a newbie might be better off to wait until Intrepid for KDE 4.1 to be fully integrated. Right now your priorityis to get a useful system and gnome and KDE 3.5.9 can do that beautifully.

I get sigsev error in KDE 4.1; I get KDE crash error or KDE window crash error in KDE 3.5.10(it's the same with 3.5.9) especially if I use configuration options from right click on desktop.

Whatever the option I think I'll have to resize NTFS option because I don't have any spare partition or additional hard disk so somehow I'll have to learn simple and safe way to resize NTFS and then create a partition it seems.:(

I don't understand what should be backed-up from windows.  I've got a default partition named "Recovery"  I hope its intact and has all files necessary for windows.  But I don't know how to recover windows using this.  if you can please guide me to a resource---will be helpful in future anyway.  

Thanks for all the help buddy you're giving me continously.:)

---

### Post by student21 on 2008-09-08
Bump!

---

### Post by student21 on 2008-09-11
'Youthforlinux' if you're around please take a look at my post.

---

### Post by youthforlinux on 2008-09-17
hey student21, sorry i've been on vacation for the last 2 weeks or so, so i just got to read ur post.  Basically here's the scoop.

Using the original hardy disk is ok for what you are doing, just update when you install, it could take a while though.  Er, i would seriously recommend with that new isntall that u just ignore kde4.1 for the time being.  It would be a wise decision on your part, because it is not completely ready to go for hardy usage.  I would wait until Intrepid to use KDE4.1 as ur main kde desktop.  I owuld say use gnome or kde3.5.9 after installing from that 8.04 disk.  If you dont wanna reinstall twice, you could wait til intrepid is realeased t give ubuntu another shot.  But for now definetley stick with kde3.5.9 or gnome in a new isntall.  Not sure on the bookmarks and such things but i think its in ur .mozilla folder somehwere.

Oh and for backing up windows, the recovery partiton is provided by your manufacture.  Don't use it, it will wipe everything off, adn things u wanna save from windows would be ur documents and such, so if this fails you can reinstall windows but have ur importnat files available.

---

