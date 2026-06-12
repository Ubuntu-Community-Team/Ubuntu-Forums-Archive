---
title: "install jack for latest idjc"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Sevy on 2008-06-25
Im just starting out with Ubuntu and want to eventually replace windows to stream my internet radio.
I currently want to try out IDJC but need to install JACK.
I need the latest IDJC to play mp3s and so too the latest JACK.
I have the following instructions

How do I install JACK?
Prerequisites

    * 2.4, 2.5 or 2.6 series kernel with tmpfs turned on (CONFIG_TMPFS)
    * Shared memory file system mounted on /dev/shm. add the following to /etc/fstab to get it mounted at boot:

      	shmfs       /dev/shm     shm    defaults        0       0

            (Note: you may have to make the /dev/shm directory)

Once you have the correct shmfs support, you should be able to build jack with the following sequence of commands:

sh ./autogen.sh
./configure
make
make install

I understand how to build jack but not the prerequisites.Can someone explain?
cheers

---

### Post by PinkFloyd102489 on 2008-06-25
```
sudo apt-get install jack jackd libjack*
```


That's all you need. Then just enter the jackd code that's on IDJC's site.

---

### Post by Sevy on 2008-06-25
i cant find any jackd code on the idjc website

---

### Post by Sevy on 2008-06-27
OK Ive successfully installed idjc 0.7.6 on two of my pcs for testing.
I previously installed an earlier version and was able to stream mp3s but not play them.On this 0.7.6 version I can play mp3s but not stream in mp3.
On the idjc website it says it supports streaming mp3.What else do I need to install?

---

### Post by Sevy on 2008-06-27
Is there a specific version that supports mp3 streaming? I just cant find enough info on this

---

### Post by StephenF on 2008-06-27
[http://ubuntuforums.org/showthread.php?p=5200135&highlight=idjc#post5200135](http://ubuntuforums.org/showthread.php?p=5200135&highlight=idjc#post5200135)

---

