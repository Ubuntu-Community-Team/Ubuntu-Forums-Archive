---
title: "Make programs executeable?"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by Neferti on 2012-06-24
Hey, 

I'm  new to ubuntu so even the most simple predicaments appear quite advanced to me. What I want to do is to open a program which I frequently use on win7. However, when I try to enter the program I get an error message saying the program is not executeable, eventhough it is an .exe-file. When I enter the properties of the file, the box "Allow the file to start" is unchecked. And I can't check it.. 

Why can't I? Haven't I got the rights on my user, even though it's the only one on the computer? 


Thanks,

---

### Post by lisati on 2012-06-24
In general, Windows .exe files don't work in Ubuntu. You might want to either look for a Linux equivalent, or check out a compatibility aid such as [Wine]("https://help.ubuntu.com/community/Wine").

---

### Post by NikoC on 2012-06-24
If I understand correctly you want to run windows software on ubuntu? That's not possible without installing an extra package called wine!
[Wine hompage]("http://www.winehq.org/")

It's available via the repositories!

Briefly: you install wine and run the windows software as 'wine name_of_the_windows_exe'

---

### Post by Neferti on 2012-06-24
Yes, I do have wine, but it seems like I can't run it anyway. At least not by clicking the file and selecting "Run with Wine", but perhaps there is another way?

---

### Post by Neferti on 2012-06-24
Will I have to reinstall all the programs installed on my windows os? I think I have been able to run programs like Spotify before, but maybe I isntalled while I was on the ubuntu os.

---

### Post by Paqman on 2012-06-24
> **Neferti said:**
> Will I have to reinstall all the programs installed on my windows os?

Yes, you're using a whole new operating system. Make sure you check for Linux alternatives for your apps before you try installing Windows ones through Wine. A native Linux app will always work better than a Windows one app using Wine.

---

### Post by 3rdalbum on 2012-06-24
> **Neferti said:**
> Will I have to reinstall all the programs installed on my windows os?

No, only the programs that you absolutely MUST use on Ubuntu.

It's no secret that Wine is not compatible with many Windows programs; not the developers' fault, but the reality of trying to be compatible with a closed-source operating system.

But yes, you will have to install them on Ubuntu if you want to use them with Wine, otherwise the programs won't be able to find the files they need.

BTW, to run a program in Wine, the easiest way is to open a terminal, type 'wine' and leave a space, and then drag the program into the terminal and press Enter.

---

### Post by oldos2er on 2012-06-24
> **Neferti said:**
> Will I have to reinstall all the programs installed on my windows os? I think I have been able to run programs like Spotify before, but maybe I isntalled while I was on the ubuntu os.

Might I suggest, if you wish to run Windows' applications, run Windows and not Linux? I don't intend for that to sound rude or flippant, just practical. Wine may work well for a few Win* apps, but it's always going to be playing catch-up with real Windows.

There is a database of Win* apps and how well they perform under Wine,  [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Neferti on 2012-06-24
> **oldos2er said:**
> Might I suggest, if you wish to run Windows' applications, run Windows and not Linux? I don't intend for that to sound rude or flippant, just practical. Wine may work well for a few Win* apps, but it's always going to be playing catch-up with real Windows.

There is a database of Win* apps and how well they perform under Wine,  [http://appdb.winehq.org/](http://appdb.winehq.org/)


Yes, well I do wish to use windows but I the windows on this computer is currently not usable due to a virus. So figured I should use an anti-virus to make it work again, and the only one I had was for windows. I actually also had to use a few other programs as well, so i figured i could as well try to learn something about ubuntu. 

But I think I'll just reinstall everything and run win7 only. I guess I won't have this computer for a very long time so I'll manage. And I guess it's not really that complicated.

---

### Post by Mark Phelps on 2012-06-25
Don't mean to be rude by saying this -- but Linux is not Windows.  Some folks come here expecting to find that Ubuntu is a free version of MS Windows when, in reality, it is a free alternative to MS Windows.  You will need to learn entirely new ways of doing things, with very different desktops, and new applications.  Not everyone wants to put in that effort.

If you want to continue using Win7, you should go to the Kaspersky site and download their Antivirus Rescue CD image, burn that to CD, boot from that -- and do an antivirus scan using that.

Also, you should visit the Windows 7 forums (sevenforums.com) for further recommendations on "cleaning" your PC and which antivirus products to use.

---

