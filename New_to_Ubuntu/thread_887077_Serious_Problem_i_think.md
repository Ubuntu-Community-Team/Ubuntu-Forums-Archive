---
title: "Serious Problem i think"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Bluangel88 on 2008-08-11
Laptop worked great this morning.  Came home from work turned it on and this is what i have  Instead of the blue screen of death its the black screen of jibberish. 

(intirams)  I hit enter figuring it was stuck at this screen. Then another line came up and said type help so I did and this is what i got.

(initramfs) 
. : alias break cd chdir command continue echo false getopts hash help let local pwd read readonly return set shift times trap true type ulimit umask unalias unset wait [ [[ ash awk basename busybox cat chmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo egrep env expr false fbset fdflush fgrep hostname ifconfig ip kill ln loadfont loadkmap ls mkdir mkfifo mknod mkswap mknod mkswap mktemp more mount mv openvt pidof printf pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stst sync tail tee test touch tr true tty unmount uname uniq wget yes

I hit enter

---

### Post by trigsenior on 2008-08-11
hi,

can you access terminal in any way ?  can you use ctr - alt - f5 to get to terminal ?

---

### Post by Bluangel88 on 2008-08-11
I restarted the machine and ubuntu started this time.  So yes I can get to the terminal now.

---

### Post by trigsenior on 2008-08-11
very weird , 

I can't really suggest much apart from looking in system > administration >  system log. Look at exact time and date in syslog and see if there are any errors or something weird. However not sure if system log logs things before Ubuntu has started so it a bit of a hit in the dark.

---

### Post by Rog-Mahal on 2008-08-11
initramfs is the basic shell that your computer uses before it boots to your kernel and starts bash. (I think that's how it works.) If you're working from it, that means that something stalled during startup. Did anything else appear on the screen before you got to that prompt?

---

### Post by Bluangel88 on 2008-08-11
No just that in I word in parenthasis

---

### Post by Bluangel88 on 2008-08-11
I do not know what i am looking for in the log but it is pages and pages of stuff. 

Ihave looked and for my beginners eyes don't see anything unusual. On further examination I have found 

lp: driver loaded but no devices found 
No dock devices
apm: Bios not found

All of this is upon start up trying to load.  Again i am about two weeks new to Linux.  So anything you could suggest that i need to check
would be appreciated.

---

### Post by Bluangel88 on 2008-08-11
I am looking in the debug, kern, sys log and it had a bit of

APIC error on CPU1: 00(40)

APIC error on CPU1: 40(40)

---

### Post by Daveski on 2008-08-31
You could try the noapic option:

Press **F6** at the boot up screen.
You should see a line ending with *"--quiet splash."*
Delete --quiet splash, add the option **noapic** after **ro** so you have **ro noapic**

Hit enter to boot.

---

