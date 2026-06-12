---
title: "Emulators in Hardy"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by xphil9 on 2008-08-13
Hello fellow AMD 64 bit users, I am new to Linux environments. Ubuntu is extremely easy to use though!
I am looking for good emulation software for old video games
snes9x is not very good and I can't get zsnes to work.

Well, anyone know how to get zsnes to work?

---

### Post by Thingymebob on 2008-08-14
you could also try xmame (the arcade machine emulator)

---

### Post by Paqman on 2008-08-14
Dosbox is good fun, it's in the repos.

---

### Post by hosk on 2008-08-14
sudo apt-get install zsnes

that didn't work?

does it give you an error if you type zsnes in a terminal?

---

### Post by SunnyRabbiera on 2008-12-02
> **hosk said:**
> sudo apt-get install zsnes

that didn't work?

does it give you an error if you type zsnes in a terminal?

it probably doesnt as znes is a 32bit binary that doesnt work under 64, he is sort of stuck with snes9x.
Though he could try to run zsnes via wine as it simulates a 32bit system

---

### Post by dfreer on 2008-12-02
You're thread title is a bit misleading if all you need is help with ZSNES. ZSNES will work in hardy/intrepid 64-bit, but there are some issues. 

(1). In hardy there is no 64-bit package of ZSNES. So unless you add a 3rd party repository that contains 64-bit packages of ZSNES, *sudo apt-get install zsnes* will not work.
(2). You cannot run/compile a 64-bit binary of ZSNES, since it contains x86 assembly code. You will need to use a 32-bit binary, or compile it yourself with a 32-bit chroot or something similiar.
(3). If you try to run a binary of ZSNES that is compiled with the --enable-libao flags, you will need to install ia32-libs (needed anyways for to run ZSNES in 64-bit Hardy), and then symbolically link the shared object files in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/, make sure not to overwrite the existing files in /usr/lib/ao/plugins-2/.
(4). IIRC, in order to use OSS/ALSA instead of just SDL in Ubuntu Hardy/Intrepid, you will need to use patched build of ZSNES 1.51, called 1.51b.

Here's a link to 32-bit binaries compiled by one of the ZSNES devs of 1.51b, they should work for you:
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)
Try to download one for your CPU, if you have an Intel Core 2 Duo the "Core2" binary would be the one you want. The "i586" binary should work for any recent CPU.

If you want, you can also use this package created by me:
[http://packages.dfreer.org/pool/hardy/main/zsnes32_1.51b-3.5_hardy-amd64.deb](http://packages.dfreer.org/pool/hardy/main/zsnes32_1.51b-3.5_hardy-amd64.deb)
It will automatically create the needed symbolic links for libao, and will install a .desktop file for zsnes so it will show up in your Applications menu as well.

> **SunnyRabbiera said:**
> it probably doesnt as znes is a 32bit binary that doesnt work under 64, he is sort of stuck with snes9x.
Though he could try to run zsnes via wine as it simulates a 32bit system
Not quite true as most desktop/laptop 64-bit processors are able to execute 32-bit binaries. ZSNES runs quite well on 64-bit linux systems, has been able to for quite some time.

---

