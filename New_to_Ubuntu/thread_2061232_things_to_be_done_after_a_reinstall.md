---
title: "things to be done after a reinstall"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by Yezinki on 2012-09-22
Hi there,

What are the usual things to be done after a reinstall, updating & installing drivers?

Thanks.

---

### Post by Yezinki on 2012-09-22
When does one use a janitor or Bleach bit?

Thanks.

---

### Post by zombifier25 on 2012-09-22
By "reinstall" did you mean "fresh install" or "upgrade"? If the latter, then it might be a good idea to use BleachBit to clean the redundant packages of the old install.
(and please don't use the Janitor. It was removed from Ubuntu's default install for a reason, which is "messing up people's systems to the point of unrecoverable error)

---

### Post by Yezinki on 2012-09-22
Thankszombifier25. yes I mean a fresh install........so not to use Bleachbit?

---

### Post by 3rdalbum on 2012-09-22
> **Yezinki said:**
> Thankszombifier25. yes I mean a fresh install........so not to use Bleachbit?

Bleachbit is fine. Computer Janitor is not.

After a reinstall, just run the updates and reinstall the programs and multimedia playback codecs you want. There's nothing else to do. I don't even think there's much value to Bleachbit unless you're running very low on disk space. Bleachbit will not make your computer faster, it will only free up a small amount of disk space.

---

### Post by whatthefunk on 2012-09-22
On a new install you really shouldnt have to do anything, other than download the programs you want.  I only use Bleach Bit once every few months or so to clean up the unused logs and dependencies.  With a fresh install there shouldnt be anything for it to clean up.

---

### Post by Yezinki on 2012-09-22
Thanks for your replies.

Btw which BleachBit is for Ubuntu [http://bleachbit.sourceforge.net/?](http://bleachbit.sourceforge.net/?)

Is there anything equivalent to windows CCleaner in Ubuntu?

---

### Post by wojox on 2012-09-22
Download it from the repo's:
```
sudo apt-get update; sudo apt-get install bleachbit
```

---

### Post by mörgæs on 2012-09-22
After applying all updates, rebooting and verifying that everything works I run the commands

```
sudo apt-get clean
sudo apt-get autoclean
```

to save some hard disk space, that's all.

---

### Post by Yezinki on 2012-09-22
Does this give both the root & standard one?

Thanks.

---

### Post by daslinkard on 2012-09-22
> **Yezinki said:**
> Does this give both the root & standard one?

Thanks.

What do you mean the root & standard one?  You're running the command as root.

---

### Post by Yezinki on 2012-09-22
When I used to install from the site used to get 2 on my desktop.......one wrtitten as BleachBit root & other only BleachBit?

---

### Post by pompel9 on 2012-09-22
I think he means if this version includes the option to run this software as root.

Yes it does. When you search in dash, there will come up two choices: BleachBit and BleachBit (root).

This can also be installed in ubuntu softwarecenter (I think that is the name, I have my own language on so I can't see the English name).

---

### Post by daslinkard on 2012-09-22
Jumping into the conversation here....which is the best option to run and why?

---

### Post by Yezinki on 2012-09-22
They say root 1st & standard after that leaving aside 3 options. Don't know the logic behind it...........

---

### Post by pompel9 on 2012-09-22
> **daslinkard said:**
> Jumping into the conversation here....which is the best option to run and why?

If you are talking about BleachBit, then using it as root is necessary , as there are limits to what you can do when you use it as not root.

---

### Post by daslinkard on 2012-09-22
> **pompel9 said:**
> If you are talking about BleachBit, then using it as root is necessary , as there are limits to what you can do when you use it as not root.

Thank you....I figured as much but wanted further clarification....thank you!

---

### Post by Yezinki on 2012-09-22
I read some where that memory, localizations & some other should be left unchecked.

Is there a counter part of windows CCleaner in Ubuntu?

Thanks.

---

### Post by pompel9 on 2012-09-22
> **Yezinki said:**
> I read some where that memory, localizations & some other should be left unchecked.

Is there a counter part of windows CCleaner in Ubuntu?

Thanks.
 
Yes, there is. BleachBit.

As ubuntu and windows are so different, then BleachBit will be the closest thing you'll get CCleaner. And CCleaner is mostly for deleting obsolete  reg keys (sadly, sometimes it does more than that and removes vital reg keys, leaving your OS crippled).

---

### Post by Yezinki on 2012-09-22
Thanks can you post a link to the latest version of BleachBit compatible with ubuntu 12.04?

---

### Post by daslinkard on 2012-09-23
You can do the following sudo commands from what I have found to install the program

```
sudo apt-get update
```
```
sudo apt-get install bleachbit
```

But there seems to be some concern over how well it works with 12.04.

---

### Post by Yezinki on 2012-09-23
Thanks daslinkard, what sort og concerns could you care to be more specific?

---

### Post by daslinkard on 2012-09-23
> **Yezinki said:**
> Thanks daslinkard, what sort og concerns could you care to be more specific?

The concern I mentioned stems from this link [here]("http://askubuntu.com/questions/141115/how-can-i-install-bleachbit-in-ubuntu-12-04-lts").

---

### Post by Yezinki on 2012-09-23
uncheck free disk space, memory & localizations.

---

### Post by Yezinki on 2012-09-24
Which option should I leave unchecked , keeping myself on the safe side that the OS/Grub doesn't get corrupted.

Have only Ubuntu running on this machine.

Thanks.

[IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_005_zpsf0163f91.png[/IMG]

Amin:

[IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_004_zpsc8f4d009.png[/IMG]

Standard:

---

### Post by Yezinki on 2012-09-25
Any recommendations?

Thanks.

---

### Post by daslinkard on 2012-09-25
Personally I would recommend opening a new thread in regards to Bleach Bit as this one is marked solved so you are able to get more eyes on your question.

---

