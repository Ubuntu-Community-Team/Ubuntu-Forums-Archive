---
title: "migrazione a lubuntu"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by basilico51 on 2013-02-16
[I]A cordial greeting to the whole community. ):P

I will write in my language, Italian, but if necessary, I will try to express myself in English.

I have a question: I own an old Pentium III with 600 mega of ram.
I do not use it often because it is rather slow. In 2010 I installed Ubuntu in a partition on the same hard disk where Windows XP is running. Of course, the choice of operating system is managed by Grub.
Even Ubuntu runs hard on this PC. I saw that there is a "light" version of Ubuntu, ie Lubuntu, which might work for my case.
How do I replace Lubuntu version of Ubuntu that I installed in the simplest way?
Thanks to those who will respond.
[/I]
Un cordiale saluto a tutta la comunità. ):P

Scriverò nella mia lingua, l'italiano, ma, se necessario, cercherò di esprimermi in inglese. 

Ho un quesito: posseggo un vecchio Pentium III con 600 mega di ram. 
Non lo uso frequentemente perchè è piuttosto lento. Nel 2010 ho installato Ubuntu in una partizione dello stesso hard-disk sul quale gira Windows XP. Naturalmente, la scelta del sistema operativo è gestita da Grub.
Anche Ubuntu gira faticosamente su questo pc. Ho visto che esiste una versione "light" di Ubuntu, cioè Lubuntu, che potrebbe fare al mio caso. 
Come posso sostituire Lubuntu alla versione di Ubuntu che ho installato nella maniera più semplice?
Grazie a chi mi risponderà

---

### Post by sudodus on 2013-02-16
Welcome to the Ubuntu Forums :-)

Check if your cpu has pae capability.

```
grep --color pae /proc/cpuinfo
```

- ***Do you have personal files*** in your installed Ubuntu system? (Documents, pictures, video clips, ...)

Then ***backup these files*** to an external drive!

- ***Is there a lot of special programs installed or a lot of configurations (tweaking)?***

Then (if Ubuntu 10.04 LTS or 11.10) consider upgrading to a new version, otherwise it will be better to wipe your installation and install a fresh version of Lubuntu 12.04, if you need the non-pae kernel, otherwise you can also try Lubuntu 12.10. But before wiping, download the iso files of Lubuntu, and try them before installing: "Try Lubuntu live" running a live session booted from CD.

***Lubuntu 12.04 has end of life in October 2013***. After that there will be no security updates for the Lubuntu specific program packages. However the flavour ***Xubuntu 12.04 LTS has long time support until April 2015***, and it might also be interesting for you to try.

---

### Post by mörgæs on 2013-02-16
No, the Pentium 3's had PAE. It will not cause problems using the newest Buntu versions.

Just grab an ordinary Lubuntu 12.10 and you will be fine.

Adding Flashblock to the browser and other adjustments might be necessary to get a decent speed.

---

### Post by sudodus on 2013-02-16
> **mörgæs said:**
> No, the Pentium 3's had PAE. It will not cause problems using the newest Buntu versions.

Just grab an ordinary Lubuntu 12.10 and you will be fine.
OK, I will change my previous post to avoid confusion.

---

### Post by basilico51 on 2013-02-16
> Just grab an ordinary Lubuntu 12.10 and you will be fine.[I]Well, I agree.
Just want to know how to override the easiest way Lubuntu 12.10 to Ubuntu 10.10.
I have no particular files saved nor programs that serve me in the Ubuntu partition. On the partition Win, I set up a satellite card that works with ProgDVB and, moreover, I use a program, SlingPlayer, which does not have a Linux version that I know of. 
For the rest, I make a moderate use of the computer: browser, email, some little program for managing firmware of set-top boxes, word processor. Stop.

Is it best to start from the installation CD? Or may I ask to Ubuntu of changing to Lubuntu by itself?

If I should use the installation CD, how should I configure the partition for Lubuntu overlapping the previous installation of Ubuntu, to be cancelled at all?

The PC is old, Windows XP limps. Ubuntu seemed like a good solution, but it may be too complex, so why I do not use it. 
If Lubuntu will prove to be faster in everyday use and more "comfortable" than Ubuntu and XP, I will cut off also the Windows partition later.

[/I]Bene, concordo. 
Solo vorrei sapere come sovrapporre nella maniera più semplice Lubuntu 12.10 a Ubuntu 10.10. 
Non ho particolari files salvati nè programmi che mi servano nella partizione Ubuntu. Nella partizione Win, ho configurato una scheda satellitare che funziona con ProgDVB e inoltre uso un programma, Slingplayer, che non ha una versione Linux, che io sappia. Per il resto, faccio un uso moderato del pc: browser, posta elettronica, qualche programmino per la gestione di firmware di decoder satellitari, word processor. Stop.

E' opportuno partire dal cd di installazione? O posso chiedere a Ubuntu di modificarsi in Lubuntu direttamente? 
Usando il cd di installazione, come dovrei configurare la partizione per Lubuntu sovrapponendola alla precedente installazione di Ubuntu, da annullare? 

Il pc è vecchiotto, Windows XP arranca. Ubuntu sembrava una buona soluzione, ma è forse troppo complesso, ragion per cui non lo uso. Se Lubuntu si rivelerà nell'uso quotidiano più rapido e "comodo" di Ubuntu e XP, eliminerò anche la partizione Windows, in seguito.

---

### Post by sudodus on 2013-02-16
> **basilico51 said:**
> [I]Well, I agree.
Just want to know how to override the easiest way Lubuntu 12.10 to Ubuntu 10.10.

Do you mean upgrading from 10.10 to 12.10? Upgrading means

10.10 --> 11.04 --> 11.10 --> 12.04 --12.10

four major upgrade steps to new versions and a considerable risk to break something at each step. I really discourage you to do that. It is much simpler to save your personal data and reuse the partition by installing Lubuntu directly. And I do recommend that you try not only 12.10, because 12.04 is much more stable (it has been debugged for 6 more months). So if you have a good broadband connection to the internet, I suggest that you download the following iso files for 32-bit systems.

Lubuntu 12.04
Lubuntu 12.10
Xubuntu 12.04 LTS
> 
I have no particular files saved nor programs that serve me in the Ubuntu partition. On the partition Win, I set up a satellite card that works with ProgDVB and, moreover, I use a program, SlingPlayer, which does not have a Linux version that I know of. 
For the rest, I make a moderate use of the computer: browser, email, some little program for managing firmware of set-top boxes, word processor. Stop.

Is it best to start from the installation CD? Or may I ask to Ubuntu of changing to Lubuntu by itself?

Start from the installation CDs, and ***test running live systems before installation***, to get the look and feel of the versions 12.04/12.10 and/or flavours Lubuntu/Xubuntu.
> 


If I should use the installation CD, how should I configure the partition for Lubuntu overlapping the previous installation of Ubuntu, to be cancelled at all?

1. Save your personal files.

2. From a live session booted from the install disk, run ***gparted*** and delete Ubuntu (delete the file system of that partition, and create an ext4 file system. Keep the swap partition and of course keep the Windows partition.

3. Then install. At the screen about partitioning, select '***Something else***' and select manually the partition with the newly created ext4 file system as the root partition. Swap will be selected automatically. Install grub to the head of the drive (I guess you have only one internal drive (letter a), so it should probably be ***/dev/sda*** (not any digit afterwards).

---

### Post by mörgæs on 2013-02-16
Before going to installation please test 12.10 in a live boot.

---

### Post by basilico51 on 2013-02-16
Thank you, sudodus. :popcorn:

Which is the correct release for a processor AMD? 
As it is surely not at 64 bits, I suppose that it should be Xubuntu-12.04.2-desktop-i386.iso
and the same for Lubuntu.

---

### Post by sudodus on 2013-02-16
> **basilico51 said:**
> Thank you, sudodus. :popcorn:

Which is the correct release for a processor AMD? 
As it is surely not at 64 bits, I suppose that it should be Xubuntu-12.04.2-desktop-i386.iso
and the same for Lubuntu.
I guess you are now talking about another computer and processor than the one in post number one. Yes, the same 32-bit system 'i386' or 'i686' should work.

---

### Post by mörgæs on 2013-02-16
'AMD' in the name AMD64 and 'i' (for Intel) in i386 are misleading. Both are leftovers from way back. 

Just focus on the bus width (32 or 64 bit).

If you find that Xubuntu is too heavy, Lubuntu (or even better a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")) is the way to go.

---

### Post by basilico51 on 2013-03-06
I tried several times to install Lubuntu 12.04, which seemed to me that could rely on for my AMD64 with only 650 mega of ram memory. I used rewritable cdrom, dvd rewritable, cdrom new, writing with low speed, using a laptop with CD burner. At the end of the installation always appear signs of internal errors that bring the installation to hang. Exceeded alerts, remains the icon rotating endlessly. The final situation is that the computer is locked on a Grub error 17 which also prevents me from using Windows XP. Are perhaps the 650 mega to be insufficient for the installation of Lubuntu 12.04?

---

### Post by sudodus on 2013-03-06
> **basilico51 said:**
> I tried several times to install Lubuntu 12.04, which seemed to me that could rely on for my AMD64 with only 650 mega of ram memory. I used rewritable cdrom, dvd rewritable, cdrom new, writing with low speed, using a laptop with CD burner. At the end of the installation always appear signs of internal errors that bring the installation to hang. Exceeded alerts, remains the icon rotating endlessly. The final situation is that the computer is locked on a Grub error 17 which also prevents me from using Windows XP. Are perhaps the 650 mega to be insufficient for the installation of Lubuntu 12.04?

When you have so little RAM, it is more efficient to use a 32 bit (i386 or i686) version (just to make sure). Furthermore, yes, more than 512 MB is certainly enough to run Lubuntu, but it might be hard to install from the standard live iso image with less than 700 MB, because the installation itself needs a lot of RAM. There is a good alternative. Download the lubuntu alternate iso file, and make a CD or USB boot drive.

[[COLOR=#ff0000]https://help.ubuntu.com/community/Lubuntu/Alternate_ISO[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")

[[COLOR=#ff0000]http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/[/COLOR]]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/")

Good luck :-)

---

### Post by mörgæs on 2013-03-06
Did you follow the advice in the link I posted above?

---

### Post by mastablasta on 2013-03-06
AMD64 is a 64bit image of the OSit will not work on Pentium III processor. it doesn't even work on some pentium 4.

you need i386 image.

650MB are enough to install Lubuntu.

---

### Post by basilico51 on 2013-03-06
> **mörgæs said:**
> Did you follow the advice in the link I posted above?

Thank you, but it seems a little too much difficult for me. I'll try before with the alternate install as suggested by sudodus, after that I'll study how to install minimal lubuntu. :)

---

### Post by basilico51 on 2013-03-06
Very well. 
I am writing from the browser of Lubuntu, Chrome. 
The install with the alternate ISO has gone without any further problem.
Thank you for your help. :) Good night.

---

