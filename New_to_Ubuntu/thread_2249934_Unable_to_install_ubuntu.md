---
title: "Unable to install ubuntu"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by nargent on 2014-10-25
I am a complete beginner to Linux. I have a 7 year old Dell laptop - 32 bit with 1 Gig RAM currently with no operating system (its a long story). I tried to install ubuntu (32 bit version) 14.04.1 LTS from a CD (I downloaded from ubuntu).
I get the following messages:

Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100

CPU: 1 PID: 1 Comm: run-init Not tainted 3.13.0-32-generic #57-Ubuntu
Hardware name: Dell Inc. MXC061                        /OMG532, BIOS A10 04/02/2007
00000000 00000000 f585ff34 c1650cd3 (and similar for three lines total - let me know if you need all the numbers)

Call Trace:
[<c1650cd3>] dump_stack+0x41/0x52
[<c164be0c>] panic+0x87/0x181
[<c105911f>] do_exit+0x8ef/0x8f0
[<c117943c>] ? vfs_write+0x13c/0x1b0
[<c1059156>] Sys_exit+0x16/0x20
[<c1657da7>] syscall_call+0x7/0xb
drm_kms_helper: panic occurred, switching back to text console


Now none of that means much to me, so I am hoping someone could help me with my next step. Incidentally, I tried loading Linux Lite on the same machine with similar results. I was able to load Lite on another laptop using the same CD so I don't think its a download/writing issue.

Thanks very much in advance.

---

### Post by Bucky Ball on 2014-10-25
Welcome. With 1Gb of RAM it wouldn't be a pleasant computing experience, even if you could get it running. Unity needs some fairly severe graphics and a machine that old might be doubtful on that count also. What sort of processor is that machine using? It is 32bit?

I suggest you try Xubuntu, see how/if that runs ok, and if you need to go lighter still go for Lubuntu and see how that runs. Good luck.

(See the last link in my signature for how to use [code] tags for code in your posts. ;))

---

### Post by Iowan on 2014-10-25
> **nargent said:**
> I tried to install ubuntu (32 bit version) 14.04.1 LTS from a CD (I downloaded from ubuntu).
Thanks very much in advance.CD or DVD?

---

### Post by nargent on 2014-10-25
Thanks very much for the quick replies. Its a 32 bit processor and I used a DVD.

I am going to try lubuntu this afternoon and hopefully get a better result.

---

### Post by yancek on 2014-10-25
Make sure you do an md5 checksum on the Lubuntu download to verify the download.  Burning to a DVD at a slow speed also helps.

---

### Post by nargent on 2014-10-25
Update.

I got slightly further with Lubuntu in that I was able to choose a language and had the option to try without installing or install to the HD. I tried both, but ended up with the same error messages that I posted above. I am assuming there is something more sinister going on with my hardware and I'm not sure whether its worth it to keep trying. Too bad, because I was hoping to just use this old laptop as a base for learning to play with the arduino microcontroller without tying up my regular PC/laptop.

C'est la vie I suppose.

If anyone has any other ideas I would definitely like to try something else. Thanks for the help.

For completeness, here are  the specs of the old laptop:

Intel Core Duo, with 1.60 GHz clock (minimum 800 MHz)
1 Gig RAM DDR2 @ 533 MHz
Intel 945GM graphics with 8 Meg

---

### Post by ajgreeny on 2014-10-25
All I can suggest is that you try Ubuntu 12.04.1 from [http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-desktop-i386.iso](http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-desktop-i386.iso) which may boot properly.

I have an old Acer laptop which simply refuses to boot from any of the ubuntu 3.13.0-# kernels (for no obvious reason) but booted fine using 12.04 until I tried updating to the trusty (14.04) hardware stack.  I have also tried booting to an updated 3.14, 3.15 and 3.16 kernel on that machine but al without success.

I agree that xubuntu or lubuntu would be better but unfortunately xubuntu 12.04 has only another 6 months support, and Lubuntu 12.04 has already lost support so they are much less appropriate.  You may find that Ubuntu 12.04 with a 2D desktop instead of the default 3D will work better, or you could use the classic gnome desktop by installing gnome-panel to a default Ubuntu, and the choosing classic at login.
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

