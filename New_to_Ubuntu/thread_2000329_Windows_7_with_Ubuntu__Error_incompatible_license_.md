---
title: "Windows 7 with Ubuntu : Error incompatible license Grub rescue"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by julien9259 on 2012-06-09
Good morning, 

I work on windows 7 but I needed linux for my studies so I installed it on a partition of my hard disc.
Yesterday I downloaded an update of Ubuntu and in the evening I realized that my computer could neither start on Windows nor on Ubuntu.
When I start it, I see the usual first screen on which I can press "F2" for Setup, and then I have a black screen with :
"Error incompatible license
Grub rescue>
"
written on it. 

I read on some forums that some people already had this kind of problem but contrary to my, they were used to linux and I did not really understand what things like a "boot" are. 
The thing is that the files I want to rescue are on Windows, if I need to delete Ubuntu from my pc, it is not a problem (I would like to be able to use again the partition one what I installed Ubuntu if it is possible.)
A friend's dad thinks it is a problem linked with the "Master Boot Record" but he was'nt here to solve the problem, so if you have any idea of what it could be and especially of how I could solve it, it would be great ! Thank you.

Julien

---

### Post by Journeyman1962 on 2012-06-09
Do you get the grub menu up, with a list of os to load, with latest linux kernel on top and windows somewhere down the bottom? If so, you can choose an earlier version of ubuntu to load - the one that worked before.

Alternatively, you should be able to save (and backup) the windows files by loading the ubuntu live cd you first installed it from.

---

### Post by Mark Phelps on 2012-06-09
> **julien9259 said:**
> Good morning, 

I work on windows 7 but I needed linux for my studies so I installed it on a partition of my hard disc. 

...  and in the evening I realized that my computer could neither start on Windows nor on Ubuntu.
IF you made the mistake of using the SLIDER to shrink your Win7 partition to install Ubuntu, you most likely corrupted the Win7 boot loader in the process -- a common side-effect of installing this way.

If you had bothered to use the Backup feature of Win7 to create and burn a Win7 Repair CD BEFORE you installed Ubuntu, you would have a CD now that you could use to repair Win7.  But, you probably did not do that.

> The thing is that the files I want to rescue are on Windows, 
You can boot from an Ubuntu LiveCD, or LiveUSB, plug in an external drive, or USB stick, and copy the Windows files you want to save to that.
> A friend's dad thinks it is a problem linked with the "Master Boot Record" but he was'nt here to solve the problem, so if you have any idea of what it could be and especially of how I could solve it, it would be great ! Thank you.
When you installed Ubuntu to its own partition, it overwrote the MBR with new code, forcing it to boot into Ubuntu, now.

What MIGHT work, is using the link below to create a Boot-Repair CD and seeing if you can boot using that, and repair Win7 boot:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by julien9259 on 2012-06-10
> **Journeyman1962 said:**
> Do you get the grub menu up, with a list  of os to load, with latest linux kernel on top and windows somewhere  down the bottom?

No, this was before my computer broke down.

---

### Post by wilee-nilee on 2012-06-10
boot a live ubuntu cd and run this command set, a results.txt will be in the ubuntu home. Copy and paste all the text from it to a reply. While the reply is still open highlight all the text and click on the # in the reply panel, then submit reply.
```

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by julien9259 on 2012-06-10
> **Mark Phelps said:**
> IF you made the mistake of using the SLIDER to shrink your Win7 partition to install Ubuntu, you most likely corrupted the Win7 boot loader in the process -- a common side-effect of installing this way.

If you had bothered to use the Backup feature of Win7 to create and burn a Win7 Repair CD BEFORE you installed Ubuntu, you would have a CD now that you could use to repair Win7.  But, you probably did not do that.

Ubuntu was installed on my computer about a year ago by a reliable (for computers) friend. I don't remember of any slide. No I did not burn a cd to save my data on windows before installing Ubuntu, but even if I did, it was a year ago and there are now a lot of other important files into m hard disc.

---

### Post by julien9259 on 2012-06-10
> **Mark Phelps said:**
> You can boot from an Ubuntu LiveCD, or LiveUSB, plug in an external drive, or USB stick, and copy the Windows files you want to save to that.

Is this something called "Knoppix" ? Or are there different "live versions" of ubuntu ? If yes, which one do you recommend ?

---

### Post by julien9259 on 2012-06-10
> **Mark Phelps said:**
> 
What MIGHT work, is using the link below to create a Boot-Repair CD and seeing if you can boot using that, and repair Win7 boot:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ok I will try it tomorrow when I have bought cd's.

> **wilee-nilee said:**
> boot a live ubuntu cd and run this command set, a results.txt will be in the ubuntu home. Copy and paste all the text from it to a reply. While the reply is still open highlight all the text and click on the # in the reply panel, then submit reply.
```

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

Is that it ? 
[http://www.ubuntu-fr.org/telechargement](http://www.ubuntu-fr.org/telechargement) 

Ok , I will also try this tomorrow, the computer I am borrowing is no longer available..

Anyway thank you three for answering as fast ! (and sorry for my english)

---

### Post by wilee-nilee on 2012-06-10
> **julien9259 said:**
> Ok I will try it tomorrow when I have bought cd's.



Is that it ? 
[http://www.ubuntu-fr.org/telechargement](http://www.ubuntu-fr.org/telechargement) 

Ok , I will also try this tomorrow, the computer I am borrowing is no longer available..

Anyway thank you three for answering as fast ! (and sorry for my english)

Any Ubuntu disc is okay to get the bootscript, which is what the commands are for. It is best to have cd of the installed OS though, for ease of repair in some circumstances, but best to just have really.

---

### Post by roelforg on 2012-06-10
You could, of course, reinstall grub.
That would most likely allow at least one OS (ubuntu) to boot.

---

### Post by julien9259 on 2012-06-17
> **roelforg said:**
> You could, of course, reinstall grub.
That would most likely allow at least one OS (ubuntu) to boot.

Hi. Yes, I reinstalled Grub (not exactly me ^^) with a live version of ubuntu and it worked great. I also got rid of the ubuntu partition from my computer so now I only have windows with which I never had a problem !

Thank you, 

Julien

---

