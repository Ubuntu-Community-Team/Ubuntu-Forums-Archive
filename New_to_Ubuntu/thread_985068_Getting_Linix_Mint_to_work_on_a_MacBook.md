---
title: "Getting Linix Mint to work on a MacBook"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by kragof on 2008-11-17
Hello this is my first time using any sort of Ubuntu. I am trying Linix Mint first because a friend recommended it to me. I am putting it on my MacBook. Here are the steps i've taken so far and i need help getting the rest to work. Please bare with my technical terms, i have no idea what them mean. I made a partition using Disk Utilities. I downloaded Linix Mint and burned it to a blank disk. When i run run the disk, it logs onto a "live preview session"-i think thats what its called- anyways then i double clicked on the install icon and its started to run fine. My friend helped me make sure i was using the right partition and got the "swap area" for free space. Then i hit install and it gets to about 90% and then an error pops up. Error: Grub is not installed/running on this partition -i think- Then it fails and quits the download. So how do i fix this problem? Any help would be really helpful and i appreciate the effort.

Please correct me if anything i've said is wrong. As i stated above, this is the first time i've used this and not sure of anything. 

Thanks in advance.

---

### Post by redseventyseven on 2008-11-17
I've not tried it before, but this thread looks like it might help:
[http://ubuntuforums.org/showthread.php?t=233243](http://ubuntuforums.org/showthread.php?t=233243)

---

### Post by jpoRS on 2008-11-17
Hey kragof, welcome to the forums,

Thought Mint is related to Ubuntu, they are not the same thing.  Your odds of getting the help you need will be much better if you go to the Mint forums, as the people there will be more experienced in your particular distribution.  [[LINK]]("http://linuxmint.com/forum/")

That said, did you check the integrity of the disc before you tried to install?  I don't know if Mint has the option on the disc, but there could be an option on the menu when you first boot from the CD, something along the lines of "Check Disc Integrity" or something like that.  Does that make any sense?

Either way, good luck, and enjoy!
jim

---

### Post by redseventyseven on 2008-11-17
> **jpoRS said:**
> Hey kragof, welcome to the forums,

Thought Mint is related to Ubuntu, they are not the same thing.  Your odds of getting the help you need will be much better if you go to the Mint forums, as the people there will be more experienced in your particular distribution.  [[LINK]]("http://linuxmint.com/forum/")

That said, did you check the integrity of the disc before you tried to install?  I don't know if Mint has the option on the disc, but there could be an option on the menu when you first boot from the CD, something along the lines of "Check Disc Integrity" or something like that.  Does that make any sense?

Either way, good luck, and enjoy!
jim

I disagree. Although Linux Mint is not Ubuntu, they have a lot in common. Although I prefer to use Linux Mint, the Ubuntu forums have more users which is good for both those who are looking for support and for those who are offering it. Feel free to use both forums!

---

### Post by kragof on 2008-11-17
Ok well, i ran it again and the true error is: Executing 'grub-install (hd0) failed' This is a fatal error! and then it quits. Maybe some of you know what this means? i sure don't and need help.

thanks for the advice Joe, but i couldn't find that option anywhere. Also thanks for letting me know there is a mint forum, i really didn't know.

Thanks for letting me know i can use both.

---

### Post by kragof on 2008-11-17
bump

---

### Post by jpoRS on 2008-11-17
> **redseventyseven said:**
> I disagree. Although Linux Mint is not Ubuntu, they have a lot in common. Although I prefer to use Linux Mint, the Ubuntu forums have more users which is good for both those who are looking for support and for those who are offering it. Feel free to use both forums!

I know they have a lot in common, I was just suggesting the Mint forums because what little differences there are could be a significant difference in how a problem is solved.  I doubt that is the problem here, but just in case.  Plus future readers of this post may find the information useful.

jim

---

### Post by LowSky on 2008-11-17
this old thead should help
[http://ubuntuforums.org/showthread.php?t=469807](http://ubuntuforums.org/showthread.php?t=469807)
maybe this
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I also want to say that Mint and Ubuntu are very simular, the only thing is an added repos for mint's extras like preinstalled codecs and such

---

### Post by kragof on 2008-11-17
alright man i'll check em out ant tell you if they helped

---

### Post by kragof on 2008-11-17
OK well i tried both (multiple times) and it couldn't find the file stage1 anywhere on my computer or the disk. I personally looked through all the floders starting at /boot, and still found nothing. Do i have a faulty disk? I got it from [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php) and took the first link on the Main Edition. And then stuck it straight onto a disk. I have been trying all day long. I've tried both ubuntu and linux mint forums. Please help!

---

### Post by jpoRS on 2008-11-17
I don't know if this is an option for you, but maybe re-download, re-burn, and install a brand new disc?  It is worth a shot if nothing else works.

jim

---

### Post by kragof on 2008-11-17
alright i'll try that as soon as i can and i'm not even sure whats wrong with mine, maybe i just have to install grub, but i don't know how.

---

### Post by jpoRS on 2008-11-17
Is OS X (or whatever your running already) working fine?  If so GRUB is fine (I think, someone please verify) and the problem lies elsewhere.

jim

---

### Post by kragof on 2008-11-17
yes i'm running OS X and as far as i can tell its running fine.

---

