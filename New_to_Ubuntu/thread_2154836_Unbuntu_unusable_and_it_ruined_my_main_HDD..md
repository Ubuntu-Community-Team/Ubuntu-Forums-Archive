---
title: "Unbuntu: unusable and it ruined my main HDD."
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Benny and the jets on 2013-06-16
So yea, I decided to try unbuntu12.04 alongside win7. Unbuntu was terrible so I go to load win7. Error messages from unbuntu's load screen, so i had to load win7 via bios. 

...I get into win7 only to find that my main storage drive is corrupted. Thanks, Unbuntu. But I'd really like my data back. 

[IMG]http://i44.tinypic.com/jtuf14.png[/IMG]
[IMG]http://i40.tinypic.com/2ms23xs.png[/IMG]

Seriously, what am I supposed to do now!? All I want is Unbuntu gone and my drive back, is this a common problem with linux or..? 

Also, how on earth can you guys roll out such an unstable OS!? I mean FFS, it's just not responsible to push something as stable when in reality it's so unstable that it ruins people's computers. And y'all wonder why people don't consider Unbuntu a serious OS? Worse. Than. Vista.

---

### Post by HiImTye on 2013-06-16
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
is E: the drive you installed Ubuntu onto? I don't see another drive. you do know that *nix filesystems &#8800;  Windows filesystems, right?

---

### Post by prodigy_ on 2013-06-16
Like **HiImTye** said, Windows can't read Linux file systems. If you don't have any data on E:, just reformat it to NTFS. If you do, first boot into Ubuntu and copy your data to a Windows partition.

In any case make sure you have a Win 7 installation disk at hand. You'll need it to restore MBR/BCD as they were most likely replaced with Grub when you installed Ubuntu:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

And on behalf of the Linux community: we're sorry to hear about your bad experience with Linux. You should realize, however, that you were not born with the knowledge of how to use Windows. If you'll look back you'll recall that you had to learn some basics things about Windows at some point and that you had to deal with issues from time to time. Too bad you don't want to offer Linux the same courtesy but it's your choice. :)

Most of what you've said stems from frustration which is not uncommon among people who look for a drop-in replacement for Windows and get severely disappointed when they see that Linux isn't one. Linux does have genuine issues and shortcomings but, believe it or not:
- it is stable
- it does not corrupt Windows file systems
- [it supports DLink WLAN cards (though not all of them)](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink), for unsupported cards you can try [Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Benny and the jets on 2013-06-16
So basically, it'll install alongside windows, but effectively ruin whatever HDD it installs on. Great. I didn't install it in a partition because it never gave the option - it just installed on my storage drive. Why in seven hells did unbuntu not think it'd be a nice idea to say: 
"Install alongside windows WARNING: whatever hard drive unbuntu decides to install on will be ruined" or something like that? 

My computer is screwed now.   

I reformatted the file, but somehow grub has infected my main SSD and won't let windows load. So far linux is worse than any virus I've ever had. 

Why do people even bother with this horrible garbage? Moreover why is such unstable software promoted!?

---

### Post by fantab on 2013-06-16
deleted.

---

### Post by Benny and the jets on 2013-06-16
Oh, and I had a whole bunch of data on E (formally called S: storage) - some of it I have backed up but all of my movies etc are gone now.

This is why unbuntu will never be competitive. 

I am seriously shocked at how bad Unbuntu turned out to be. Even running Unbuntu was painful - even the worst apps I've ever made threw fewer exceptions than the desktop OS did.
And seriously, why does the install CD not either give a warning or create a partition!? 

I mean.... I actually used to defend linux OS (I was trying unbuntu as I didn't like the direction microsoft is taking) but now all I can say is that unbuntu is...a nightmare.

---

### Post by ajgreeny on 2013-06-16
I am also sorry you have had a bad experience, but in all honesty, I feel you should have investigated in a great deal more detail, how to carry out what you were intending to do before you made the jump and installed.

Regrettably windows talks about Disks, when it really means partitions, and many users get frustrated by that naming difference, and the potential problems it can cause.

If you can bear to do so, and somehow I doubt that, it would be helpful if you ran a live ubuntu system, and from that open a terminal (Ctrl+Alt+T) and show us the output of ```
sudo parted -l
``` which will let us see a bit more detail of your disk hardware, and give us a chance of helping you more.

---

### Post by Benny and the jets on 2013-06-16
So it's my fault for trusting that the information given by Unbuntu would be accurate? I simply assumed that when Unbuntu said it could install alongside win7 without affecting my data or anything that it meant it. I mean, you wouldn't tell a customer who got sold faulty goods that they should have googled whether or not the store was dodgy would you? 


If the default installer (again, not that there were any option other than time zone, and user profile) is going to claim an entire disk and format it as linux - there should be a warning of some kind. It's just polite to tell a user when you're going to wreck their HDD.

---

### Post by prodigy_ on 2013-06-16
/sigh

I wish the Ubuntu maintainers never added the "alongside" option. Now that we finally got rid of Wubi there's a whole new source of confusion and unnecessary frustration.

Simply put, partitioning for a dual boot setup will never be fool-proof and thus should never be fully automated. The installer should offer a possible configuration but with a clearly visible warning [COLOR="#FF0000"]in red[/COLOR] about possible data loss and the necessity of making a backup first. This is the only sane approach, really.

Sorry for offtopic.

---

### Post by buzzingrobot on 2013-06-16
You haven't provided much information about how you installed.  It appears you installed Ubuntu on one drive and are upset because it overwrote whatever was there previously?

The Ubuntu LiveCD provides the "Try Ubuntu" option if you want to try it out without touching your drive(s).

The partitioning section of the standard Ubuntu installer provides explicit warnings about the impact of each selection, with the exception of the "Something Else" option,  That selects complete manual partitioning, and assumes, as it must, that the user knows what he is doing.

---

### Post by Benny and the jets on 2013-06-16
Prodigy, 

That's my point entirely. If the product cant be trusted not to ruin an entire drive, and chooses a drive seemingly at random (fortunately it didn't "chose" my C drive), then it shouldn't be pushed as if it is safe and stable and should at the very least come with warnings. Now, because I wanted to give linux a chance I have to spend literally hours trying to fix my main computer/minimize damages. Of course I've lost 3 days work (since my last backup) and 500G of media. Thx linux. 

Unbuntu needs to learn that if you can't do something - don't say you can; that way fewer people end up hating you.

Also, for what it's worth the experience within unbuntu was god-awful - within 20 minutes I had two complete crashes and >=10 error messages. Not to mention the multi-monitor support is broken to say the least. Hence when I saw that I couldn't access any files on my S (now E) drive I thought it was just linux being horrible for a desktop OS and rebooted to windows (again, requiring bios tweaking to make it work) only to find that the drive was in fact screwed. In device manager it showed a ~20g partition and a ~900g partition of "free space". 

I reformatted it thinking it'd get rid of unbuntu. That was foolish.

Now grub wont let me load windows. 

Even that old windows dialer virus for XP was easier to fix than linux. 

Now I'm going to try this (after pirating a win7 iso -_- [http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html](http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html) - it seems like quite a few people have had their rigs trashed by Unbuntu.

Perhaps the forum should sticky a thread on fixing dual installs and removing Unbuntu. That is, if the majority of the linux community could just admit to problems without resorting to either the blame-the-user or just-keep-using-our-stuff gambit (seriously, almost every forum I find on google results in linux fanboys attacking the person who got duped into downloading Unbuntu. it reminds me of Microsoft's handling of complaints about Windows 8).  

/rage

---

### Post by user_of_gnomes on 2013-06-16
You can probably repair the boot loader with a few simple commands if you load the Windows 7 repair console: [http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by oldfred on 2013-06-16
I think you ran into the 4 primary partition limit and with manual install you have to delete one primary partition. Most Windows 7 installs use all 4 primary partitions just to create this type of confusion so users will stay with Windows.

 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by prodigy_ on 2013-06-16
> **Benny and the jets said:**
> If the product cant be trusted not to ruin an entire drive
Windows installer will install Windows on any partition you choose and will gladly wipe and overwrite it should you select one of the "Format ..." options. Absolutely any OS installer is like that.

Instead of ranting you should learn from the experience however painful it might be. Make a full backup at least every time you're about to make a significant change to your system (OS installation, service pack installation or OS upgrade, hardware installation or upgrade, major OS reconfiguration and so on). Or some day you'll be crying on a Windows forum that Windows ruined your data.

---

### Post by sanderj on 2013-06-16
> **Benny and the jets said:**
> So yea, I decided to try unbuntu12.04 ... Unbuntu ... unbuntu's ....Thanks, Unbuntu. ... All I want is Unbuntu gone ...

... And y'all wonder why people don't consider Unbuntu a serious OS? 

You speak of "Unbuntu". This that something like "undead", and so "Unbuntu" is "buntu" but not anymore?

;-)

---

### Post by buzzingrobot on 2013-06-16
Gotta say it sounds to me that the OP installed Ubuntu onto a Windows machine, set up a dual-boot configuration, yet somehow expected the Ubuntu install to leave untouched everything on the drive it installed to, and that, as well, the boot loader wouldn't be touched.

The Ubuntu installer does, in fact, provide specific warnings about the impact of the chosen automatic partitioning scheme, so I'm confused by the assertions that those warnings were not seen.

---

### Post by oldos2er on 2013-06-16
> **Benny and the jets said:**
> 
Now I'm going to try this (after pirating a win7 iso

And with that, this thread is closed. From the Code of Conduct: "Material that suggests illegal activity or contains illegal content is also forbidden."

Thank you everyone for trying to help.

---

