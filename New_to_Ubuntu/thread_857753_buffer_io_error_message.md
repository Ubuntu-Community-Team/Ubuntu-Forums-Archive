---
title: "buffer i/o error message"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by sparkyee on 2008-07-12
Hello, can some please explain what this means? I start up 8.1 of Ubuntu and then i get this message of  lots numbers  and buffer i/o error on device fdo  logical block 0

 I have no floppy disk in my computer. I put Ubuntu on a brand new seagate 80gb hard drive today to run in the same computer as windows xp. So i am typing out this message on windows xp.

---

### Post by Mister.Vash on 2008-07-12
When you start your computer, and before Ubunutu starts, can you go into the BIOS options and disabled the Floppy Drive and see if it makes any difference?

Also, does it get past the errors at all?  Do they just keep scrolling or start, or does it eventually boot?

---

### Post by sparkyee on 2008-07-13
Helo , i disabled the floppy disk this morning and still the same. Hmm don,t know what is wrong? Is this a bug?

---

### Post by spiderbatdad on 2008-07-13
The image you have burned may be bad. It is not a bug. 

Do you get to the boot prompt screen, where you select to start Ubuntu?
Assuming you do, and what you described above follows...press F6 at that screen. A line of text ending with --quiet splash will appear delete --quiet slpash; type in: noapic nolapic and hit enter.

---

### Post by sparkyee on 2008-07-13
well i got Ubuntu to boot up by changing the sata cord from number 2 to number 1 on the motherboard and on  the hard disk,  and windows xp on number two. But now when i boot up it just boots right into Ubuntu and does not show me a window if i want windows xp or ubuntu. something about boot order i guess. I did disable the floopy disk even though it was not even used and i don,t have a floopy drive. 

I am just a dummy on Linux as i am new to it and i don,t understand. I might have a flawed cd disk. I was trying to check if that was it but i can,t get seem to chek it out right now.

---

### Post by spiderbatdad on 2008-07-13
it sounds like everything went ok installation wise...I'm a little confused regarding your set up. You have two discs? Obviously you would not have chosen to use the entire space for your installation, and overwrite windows.

You can run, in a terminal ```
sudo fdisk -l
```  Post that here please, so we can see where you windows might be.

---

### Post by sparkyee on 2008-07-13
I do have 2 hard disks. number one i had before i tried ubuntu is either a wd 320gb or seagate. number 2 i set up on Sat is a seagate 80gb. I built this computer back in June as my other one is having trouble , bad ide connector or something. Any way i bought the parts from tigerdirect.com.

  i burned a cd disk of ubuntu last weekend. took about 2.5 hours to download it off the web and burn a copy. 

  So any way yesterday i tried this after work. i got ubuntu on disk 2 installed and then i tried to boot up a while later and it where it should boot up and then it went to a blank screen and lots of writing of a buffer error on i/o fdo device. 

  and lots of numbers down the page. Ha i say to my self Oh great. 
  i did go and disable the floppy disk after that and that did nothing. still the same problem. 

   i typed in help at the bottom of the numbers when it said to and up comes all these words and i think they are about commands. I have never did anything with commands. So i am lost.

  i did switch around the wires from one hard disk to the opposite slot on the motherboard . to reverse order to see what would happen. and it did work fine in ubuntu but would not boot up in windows xp. I might just go out and buy another barebones kit and put this hard disk in it for ubuntu. 

 Make any sense?

---

### Post by sparkyee on 2008-07-13
can someone also explain what "initramts" mean. it is also on this message 

at the end of the numbers is a message saying

alais break cd chdir command continue echo exec exit export false getops hash help let local pwd read readonly return set shifttimes trap true type ulimit umask unalias unset wait   ash awk basename busybox cat chmod choot chut clear cmp cp cut deallocvt dumpkmap echo eggrep evv expr false fbset fdflush fgreep grep hostname ifconfig ip kill in loadfont loadkmap is mkdir mkfifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwn readlink reset rm rmdir sed setkeycodes sh sleep sort sync tail tee test touch tr true tty umount uname uniq wget yes

 what does all of that mean? Ha i am lost. sometime of commands?

---

