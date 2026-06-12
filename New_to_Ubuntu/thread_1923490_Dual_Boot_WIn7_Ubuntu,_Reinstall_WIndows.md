---
title: "Dual Boot WIn7 Ubuntu, Reinstall WIndows?"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by cheatos on 2012-02-10
Hi,

probably there has been a million of threads with the exact same problem, but I just don't want to dig through the other billions of posts not concerning this, which I'd find with the search...

I'm actuallly running a dual-boot with Win7 and Ubuntu 11.04 32bit an which I first installed Win7 an then Ubuntu (like it was recommended on the various ubuntu websites)

I somehow managed to mess up all my *.lnk files on my Win7 admin account and while this isn't a really big problem as I rarely use Win7 and even less often use my admin account, I'd still like to know wether it is possible (and with how much effort) to reinstall Win7 on my computer without messing up my Ubuntu system.

Thanks for all input!

---

### Post by Cheesemill on 2012-02-10
[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

---

### Post by cheatos on 2012-02-10
Thanks for the quick respone!
And how likely will I destroy half of my system?
Because I have some important stuff in my Windows partition, which I don't want to loose (and everytime I backup my data I still forget something of which I then think, man, you could use this right now)

---

### Post by Jerry N on 2012-02-10
> **cheatos said:**
> Thanks for the quick respone!
And how likely will I destroy half of my system?
Because I have some important stuff in my Windows partition, which I don't want to loose (and everytime I backup my data I still forget something of which I then think, man, you could use this right now)

Back that stuff up before you do anything!  Assume that you will destroy your system and go from there.  And your backups should always be up to date anyway.

Jerry

---

### Post by Scott Baker on 2012-02-10
OK, I (along with others I'm sure) have to know. By your own admission, you've said that you don't use Windows 7 all that much. Why not just take the plunge, and go all Ubuntu?? You state that you're already familiar with it. The newest versions are easy to set up, easy to use. If there is something that you ABSOLUTELY have to do through Windows, you could add virtualboxOSE, then install a "borrowed" copy of Windows through this. (I have 1 bill and some of my wifes college homework that I have to address this way). As to other tasks, I've used Ubuntu exclusively for several years on several machines with very few issues, and just recently converted my wife. Sleep on it tonight, talk to your REAL friends (other Ubuntu users, not those Windows freaks), and soon, you too will find your way to the light of UBUNTU.  [-o<

---

### Post by cheatos on 2012-02-11
@Scott:
I have already thought about that, but I really want to keep Outlook and as far as I know, there is absolutely no equivalent in Ubuntu (especially the exporting via .pst files is awesome, I have used Thunderbird for a while and when I reinstalled Windows all my old Mails were gone, because of the stupid mbox format or whatever they had...)

Furthermore I sometimes need to use iTunes for my iPhone which I already tried running 
through a VM but that didn't really work.

So I'd like to stick to my dual boot for a while.


Ok, so I will back up all data, wait two weeks and back up everything I forgot during the first try ;)

Thanks to all!

---

### Post by Learning Linux 2011 on 2012-02-11
Responding to your first question, it isn't a big deal to reinstall Windows without hosing your Ubuntu installation.  Assuming you don't accidentally delete your Ubuntu partition during your Windows install, the only minor problem you will run into is that Windows will overwrite the master boot record/GRUB (the boot menu that Linux uses when you first boot your computer).  This isn't a big deal, as the boot menu/GRUB can be reinstalled by using an Ubuntu Live CD or Live USB.

---

### Post by cheatos on 2012-02-11
Ok, thank you!
I'll maybe come back here for help reinstalling GRUB ;)

---

### Post by Mark Phelps on 2012-02-12
This is the Ubuntu forums, not the Win7 forums.  For detailed assistance on options you have for recoverying or saving your data from Win7 when it is not booting, you would do better going to a Windows 7 forum: sevenforums.com.

They have technical threads and tutorials for this kind of thing.

---

### Post by cheatos on 2012-02-13
It's booting just fine, I just wanted to reinstall Win7 and as I also have ubuntu on my machine I thought it'd be better to ask someone here first because I've heard that installing Win7 after ubuntu can cause various issues.

---

