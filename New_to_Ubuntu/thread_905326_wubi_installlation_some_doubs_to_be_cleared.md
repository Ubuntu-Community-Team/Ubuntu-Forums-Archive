---
title: "wubi installlation some doubs to be cleared"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by ronferds on 2008-08-30
hi,

I plan to install Ubuntu 8.04 through wubi

I need you'll to help me with certain points.

1. Can I install my ubuntu (through wubi) on D drive? If yes. wil it take the whole d drive? or will it alocate a certain part of it to linux? and the rest to windows?

2.Now since ubuntu is installed, it will change my bootscreen right? with win xp as the 1st option and ubuntu as the second. We are all aware of how the computer boots up when windows is the sole OS. Considering the fact, that i uninstall ubuntu, for some reason (I love ubuntu, but am assuming the case to understand the process :)), then how can i remove the GRUB screen and remove the ubuntu boot option, i mean can i get my bootscreen to that state, as i was in windows?

3. I have 2 disks, of ubuntu and kubuntu, i install ubuntu 1st, if i wish to install the KDE later, what do i do next, Keeping Wubi in mind?

Thanks

---

### Post by roelpeeters on 2008-08-30
Hi!

1. You can install WUBI anywhere you want, it just requires a directory somewhere in your Windows partition (could be in Program Files, My Documents, etc)
2. You will use the boot manager of Windows which is controlled by a file in your C:\ directory (forgot the name for now). Theoretically it is enough to remove the entry from that file and you will not see the option any more.
3. You can install kde simply in an existing installation of ubuntu using synaptic without reinstalling kubuntu. (You only have to install the kde specific desktop packages).

Hope this helps,

Roel

---

### Post by ronferds on 2008-08-30
Hi there roel...

thanks for replying,

So you are saying that if i uninstall ubuntu, the windows "native" bootsceen will be back?

also, i am new to this forum, can u tell me how to post a new thread?

---

### Post by durand on 2008-08-30
It doesn't use grub, with wubi, the windows boot loader is used so if you remove ubuntu, you won't see ubuntu in your boot menu. If windows is the only os, then it should just boot straight away. What do you mean by new thread? You posted a new thread...

---

### Post by ronferds on 2008-08-30
hi durand,

i appreciate you replying to my query,thank you for the help. I was actually implying posting a new thread, in the main section titled new posts, why is it that i cannot see what i have posted there? i must be doing something wrong :)

could you please elaborate the steps that you take inorder to post, in this forum.

i just wanted to know i was doing the right thing :)

---

### Post by durand on 2008-08-30
You have already posted a new thread in the Absolute Beginner Talk forum: [http://ubuntuforums.org/showthread.php?t=905330&highlight=post](http://ubuntuforums.org/showthread.php?t=905330&highlight=post)

Read the stuff there.

---

### Post by Tom--d on 2008-08-30
With KDE, use this command to install it.
```
sudo apt-get install kde
```

For KDE4,
```
sudo apt-get install kde4
```

---

### Post by ronferds on 2008-08-30
hi durand...

Thank you for replying again. Boy! do i get mixed up with the structure of the forum. well I needed to know one more thing.

I got a cd of Kubuntu from canonical too, thanks to your guidance, wubi installation was a breeze, but can i install KDE to the Ubuntu OS? If you have notice the wubi's main screen on the lower left hand corner there is a drop down box and it says Gnome by default ( I think its ubuntu) 

How would you recommend me to install KDE to my present Ubuntu OS?

---

### Post by durand on 2008-08-30
I think this is easy.

Boot ubuntu, then put the kubuntu cd in. You should get a dialog asking you if you want to add the cd to software sources, something like that.

If it doesn't ask you, go to System > Administration > Software Sources.

Then click on third party software, add cdrom button at the bottom and that should work. When you have added the cdrom, open a terminal (Applications > Accessories > Terminal) and type:

```
sudo aptitude install kubuntu-desktop
```

This will install everything that kubuntu uses which means that you get kubuntu applications even if there is a good ubuntu application which does the same thing. I doubt that you want that so the easiest way is to just install the stuff that you need.

Go to System > Administration > Synaptic Package Manager, then just use the search tool to find kde programs that you want by typing kde and selecting the ones that you need or by looking through the side tabs. I usually just get kde and kde games but you can experiment :)

Tom--d replied above about installing kde and kde4. They would work but you need a good internet connection to download kde4 unless it's on the kubuntu cd. I'm not sure, just check.

I hope that helps...

---

