---
title: "Lynx update and then upgrade to Ubuntu 12"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by Chuck_N on 2013-01-05
help. This laptop has not been run in over a year. I have 400-some important updates which will not run no matter how much I've tried.  The check button does nothing. I've gone through and un-checked manually all but a few. Tried Install Updates and they still don't install. 
  I would like to upgrade to Ubuntu 12, but can't get my updates done first.

  I would not mind deleting Lynx, then doing a clean install of 12, if that's the only way to go. I'm unsure how to proceed..........

---

### Post by Pjotr123 on 2013-01-05
Do a clean and easy upgrade to 12.04.1 LTS, like this:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Should you prefer a more traditional desktop over Unity, then consider Xubuntu 12.04.1 LTS: [https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

---

### Post by Chuck_N on 2013-01-05
> **Pjotr123 said:**
> Do a clean and easy upgrade to 12.04.1 LTS, like this:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Should you prefer a more traditional desktop over Unity, then consider Xubuntu 12.04.1 LTS: [https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

I read through it. I think it requires Windows, too. I don't have Windows on this machine.

---

### Post by Pjotr123 on 2013-01-05
> **Chuck_N said:**
> I read through it. I think it requires Windows, too. I don't have Windows on this machine.

It most certainly does *not* require Windows! :shock:

Whatever gave you that idea? :)

---

### Post by Chuck_N on 2013-01-05
the partition thing.
I thought that implied dual-boot.

also in step 6 it mentions installing alongside windows.


how will I identify the Ubuntu partitions
and the swap partition
will this be entirely obvious if I follow those steps ?

I'd hate to get 1/2 way through and get lost.........

---

### Post by Chuck_N on 2013-01-05
so I'd be booting from my original Ubuntu CD  and not really using the Ubuntu that was installed on the hard-drive, right?

---

### Post by coldcritter64 on 2013-01-05
> **Chuck_N said:**
> the partition thing.
I thought that implied dual-boot.

how will I identify the Ubuntu partitions
and the swap partition
will this be entirely obvious if I follow those steps ?

I'd hate to get 1/2 way through and get lost.........
To Identify your partitions, in a terminal,
```
sudo fdisk -l
``` That is a lower case L in the code. You can post the output here if you like, but if Ubuntu is the only OS installed there will likely only be 2 or maybe 3 partitions (swap and / OR swap and / and /home - depending on how you originally set up Lynx).

Edit: the guide posted earlier is using gparted, you could just as easily attach a screenshot of the gparted interface here if you are more comfortable with doing that.

---

### Post by Chuck_N on 2013-01-05
okay, I decided to do it........
here's how far I got.

Kernel requires  x86-64 CPU
only detected  i686 CPU

so the only UBUNTU DVD I have, I apparently made on my 64-bit Sony.

how do I proceed now?  I assume I have to create a new Ubuntu Boot disk but you may think of another option..........?

---

### Post by Chuck_N on 2013-01-05
can I download Ubuntu 12 and create a boot disk
(that's that ISO stuff, etc., right?)
then use that to install (replace the Ubuntu Lynx on my laptop)

---

### Post by Wim Sturkenboom on 2013-01-05
It's not so much that it's created on your Sony, but that you downloaded the X64 version.

Download the i386 desktop iso from e.g. [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04.1/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04.1/). Direct link to the 12.04LTS 32bit version: [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04.1/release/ubuntu-12.04.1-dvd-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04.1/release/ubuntu-12.04.1-dvd-i386.iso)

After the download, check the md5sum using the md5sum command line program _md5sum_; the correct md5sume can be found on [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04.1/release/MD5SUMS](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/12.04.1/release/MD5SUMS)

If you have a pen-drive (2GB or bigger), there is an option in the menus (administration menu?) to create a bootable USB disk.
Else burn the iso to DVD (to my knowledge, 12.04 still fits on CD but not 100% sure).

If you have a separate home directory, your documents are reasonable safe. But things can go wrong, so make backups.

Start from DVD/USB and from the menu choose the option to 'check the disk for defects'. Next testdrive to check if your hardware is supported. Reboot and from the menu select to install Ubuntu; you however can also directly install while running in live mode. I prefer not to install updates during the install (there is a tickbox on one of the install screens) as it takes much longer (2 hours in my experience versus something like 20 minutes); install updates afterwards.

I can not help with the partitioning as, for me, it's self explanatory. The only error message you can get is that you have to define a '/' (root) partition of you did not specify that.

PS
love your signature

---

### Post by Chuck_N on 2013-01-05
thanks, yes, obviously I downloaded the wrong file, back whenever I did that. Thanks for clearing up my thinking.   And, I love your signature, too.  Mine has been a favorite throughout my teaching career and most of my students had lots of exposure to it.

I'll let you know how those directions did for me, sometime soon.  For now, it's bedtime.

---

### Post by Chuck_N on 2013-01-06
okay, I'm gonna work at it for a while. I just downloaded  the iso and will now head for a verify.

one thing I'm wondering is the sequence of things.  Do I still need to do the partitioning thing with GpartEd mentioned by  Pjiotr123 a couple days ago

Am I deleting my present Ubuntu, and installing a fresh new ver.12

or am I upgrading my present to 12 ?

---

### Post by Chuck_N on 2013-01-06
Houston, we've got a problem
in order to run the mdssum, I have to get to command
line, right?
after ctrl-alt-F2 (that's command line, right,.? )
it asks for Login and Password.
I know my password,  but not my Login.

is there a different way to get to command line
or a different way to get to the mdssum to run it?

---

### Post by coldcritter64 on 2013-01-06
> **Chuck_N said:**
> Houston, we've got a problem
in order to run the mdssum, I have to get to command
line, right?
after ctrl-alt-F2 (that's command line, right,.? )
it asks for Login and Password.
I know my password,  but not my Login.

is there a different way to get to command line
or a different way to get to the mdssum to run it?

Ctrl + Alt + F? is for a tty terminal. For md5sum checks you just need a plain terminal like gnome-terminal. Ctrl + Alt + t, will get you a terminal in Ubuntu, or open it from dash/menus etc.

---

### Post by Chuck_N on 2013-01-06
> **coldcritter64 said:**
> Ctrl + Alt + F? is for a tty terminal. For md5sum checks you just need a plain terminal like gnome-terminal. Ctrl + Alt + t, will get you a terminal in Ubuntu, or open it from dash/menus etc.

okay, ctrl-alt-t gets me a plain terminal.
then  I type  md5sum and
the cursing-blinker (blinking-cursor) sits on the next line and does nothing.
I assume I might identify there, the iso on the desktop, but I don't know how.

I also tried  Applications/Accessories/Terminal and it gets me to the same thing.

I have an Ubuntu Pocket Guide to TRY and figure these things out for myself, but I'm not being very successful.

---

### Post by coldcritter64 on 2013-01-07
If you have a file to check the md5sum,
1. open terminal and  input md5sum (as you did) and ONE space (spacebar).
2. "Drag and Drop" your iso file into the terminal. The address will be automatically inputted.
3. Press "Enter"/Return
4. Copy/paste the md5sum generated from the terminal into a text file on your desktop. Hit enter, for a new line. Copy and paste the source md5sum you got off the net for the download to the file.
5. If the 2 md5sums in the text file match perfectly, your download is good.

---

### Post by Chuck_N on 2013-01-07
> **coldcritter64 said:**
> If you have a file to check the md5sum,
1. open terminal and  input md5sum (as you did) and ONE space (spacebar).
2. "Drag and Drop" your iso file into the terminal. The address will be automatically inputted.
3. Press "Enter"/Return
4. Copy/paste the md5sum generated from the terminal into a text file on your desktop. Hit enter, for a new line. Copy and paste the source md5sum you got off the net for the download to the file.
5. If the 2 md5sums in the text file match perfectly, your download is good.

I am tickled by the primitiveness of some of the necessities in Linux/Ubuntu.  Never in my computer life have I heard of typing a basic RUN command, an Assembler-type command, then SPACE, and then drag and drop (a newer Windows concept) an icon to that window. This is a hoot.  BTW, I taught computer programming from the Assembler, DOS, days for decades, before retiring. I will give it aa shot.

---

### Post by Chuck_N on 2013-01-07
okay, I'm over the mountain, I did the md5sum  drag-and-drop  run  maneuver.
the output includes a dozen folders and a few more files.
Having looked through them "all" the only one that includes data that resembles what I'm looking for is  md5sum.txt which is a 9.5K file with a hundred or so lines of the format I wish to match.  Using the FIND function  I do not find a single one of them that has 855 in it, which is the first three digits of the number I got off the web to match that files-name's md5sum. I tried the first three digits, assuming that if there were a minor download error, the results would be off on the low end, the right hand digits. 

 I would assume the one value I'm looking for should be in its own TXT file, but I find no such thing.  What now? I hate to assume the downloaded file is incorrect and try another one-hour download, when I don't know for sure that I've matched it yet.
The file is   ubuntu-12.04.1-dvd-i386.iso  which I'm quite sure was the appropriate download.

---

### Post by Impavidus on 2013-01-07
> **Chuck_N said:**
> I am tickled by the primitiveness of some of the necessities in Linux/Ubuntu.  Never in my computer life have I heard of typing a basic RUN command, an Assembler-type command, then SPACE, and then drag and drop (a newer Windows concept) an icon to that window. This is a hoot.  BTW, I taught computer programming from the Assembler, DOS, days for decades, before retiring. I will give it aa shot.
Well, it isn't really a necessity. You can just type the entire command and I don't really see why you would have to put the md5 sum in a text file on your desktop. But you probably understood so already.

---

### Post by Impavidus on 2013-01-07
Oops, so that's```
md5sum ~/Desktop/ubuntu-12.04.1-dvd-i386.iso
```assuming it's on your desktop. Else substitute the correct path. It will give you the md5 sum in the terminal.

---

### Post by coldcritter64 on 2013-01-07
> **Chuck_N said:**
> .....the output includes a dozen folders and a few more files.....The output should be 1 single md5 sum for the file you checked, what does that mean ?
I gave you a drag and drop method to save you some typing, weird as it may seem, it works. Impavidus has given the full command, substitute the correct path. The copying to a text file was for easy manual comparison with the source md5, that's all.

Edit: to clarify after re-reading post 18. When you download an iso from the net also source and copy the md5 checksum published with it. This is what you compare to the one for the downloaded file you checked in terminal. 

Here is a list of md5 hashes for Ubuntu,
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
Your installers hash will be in there for comparison.

---

### Post by Chuck_N on 2013-01-07
man, oh man. Remember this is an Ubuntu-only machine.
now when I bootup into Ubuntu, when I try FireFox it comes up checked Offline.
I uncheck, and find that I cannot get to ANY website. Nor with Chrome.
I can reboot from CD with ANTIX (a small version of Linux) and use Firefox 
and Chrome with no problems. I updated some Facebook.  Then reboot to 
Ubuntu and I can get nowhere.  SO......somehow Ubuntu has lost internet communications capability.  Any ideas?  I don't recall doing anything today to affect it. Should I start a new thread for this ?

---

### Post by coldcritter64 on 2013-01-07
I think a new thread in networking to fix that 1st may help you Chuck_N

Edit: Networking and Wireless sub forum : [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
and use "New Thread" button

**OR** Post a new thread in this forum with networking specified as part of the title. Either way is OK as far as i know.

---

### Post by Chuck_N on 2013-01-07
> **coldcritter64 said:**
> I think a new thread in networking to fix that 1st may help you Chuck_N
  

  I'll close this thread for now.

lots of troubles..........

---

### Post by oldos2er on 2013-01-07
> **Chuck_N said:**
> okay, I will go see if I can figure out how to put a new thread in networking
whatever that means.

Go to [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
click 'New Thread'.

---

### Post by Chuck_N on 2013-01-07
> **oldos2er said:**
> Go to [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
click 'New Thread'.

Thanks. I was a bit confused.

---

### Post by oldos2er on 2013-01-07
You're welcome.

---

