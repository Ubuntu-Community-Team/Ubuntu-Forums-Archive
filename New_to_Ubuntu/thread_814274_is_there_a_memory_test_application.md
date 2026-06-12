---
title: "is there a memory test application?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by robalcorn on 2008-05-31
My mother board has 4 module slots. The 1st 2 banks where 512mb each. Today I bought 2 1gb sticks and installed them in the remaining 2 slots. But my bios mem check and Ubuntu sysinfo both show only 2.7gb on memory.So I want to test the memory to see if one is defective. I dont want to test each stick seperatley because its alot of work to get at them with all the cables from pwr supply,4 hd's,2 dvds.spectrum analyzer,sound card,etc..real nasty wiring scene i created.

---

### Post by shifty_powers on 2008-05-31
do you have the live-cd for ubunt? it has one on there. boot from it.

otherwise look up memtest86 in google ;)

---

### Post by robalcorn on 2008-05-31
> **shifty_powers said:**
> do you have the live-cd for ubunt? it has one on there. boot from it.

otherwise look up memtest86 in google ;)


Yes I do will give that a shot.

---

### Post by shifty_powers on 2008-05-31
good. this also means thta the memory test will be run without anything resident in the memory from the os.

---

### Post by WRDN on 2008-05-31
memtest86 is one of the things installed during installation, and you can run it at bootup by selecting it from the GRUB menu.

---

### Post by shifty_powers on 2008-05-31
heh that's very true.

never use the grub menu, have it hidden on a 3 sec timeout so don't notice ;)

---

### Post by robalcorn on 2008-05-31
> **shifty_powers said:**
> heh that's very true.

never use the grub menu, have it hidden on a 3 sec timeout so don't notice ;)

Yes I completly forgot about that while I was looking for my Cd. Anyways still testing and no errors. So guess I am going to try something I don't want to and try the memory modules in a different order and see if that resolves my problem.

Thaks Shifty and WRDN for your help !!!!

---

### Post by Xiong Chiamiov on 2008-05-31
2.7 is an odd number to get from adding 512 + 512 + 1024 + 1024.  Have you checked to make sure that your mobo supports 4 gigs?

---

### Post by shifty_powers on 2008-05-31
how long have you let the test run? you should let it run for at least a couple of hours.

and glad to help ;)

---

### Post by sayakb on 2008-05-31
Even if you use the LiveCD, it should show the full RAM, though RAM usage may be high. Do you have onboard graphics?

---

### Post by robalcorn on 2008-05-31
> **Xiong Chiamiov said:**
> 2.7 is an odd number to get from adding 512 + 512 + 1024 + 1024.  Have you checked to make sure that your mobo supports 4 gigs?


No i didnt but it should its about 2 yrs old. Problem is like my original post there is alot stuff in my box so I cant see much of the board to try to find the model number of it and google for it's specs.

---

### Post by robalcorn on 2008-05-31
> **shifty_powers said:**
> how long have you let the test run? you should let it run for at least a couple of hours.

and glad to help ;)

Over an hour now

---

### Post by robalcorn on 2008-05-31
> **LinuxIsInnovation said:**
> Even if you use the LiveCD, it should show the full RAM, though RAM usage may be high. Do you have onboard graphics?

Nope running nvidia pci-e

---

### Post by Kevbert on 2008-05-31
Out of interest, what's your PC make, model ?  And are you using 32 or 64 bit Ubuntu ?  If the memtest program is passing on boot and no failures it may be due to the fact that you have some shared resources (read memory) which are being used by various system devices.  This can actually be worse if you are using 4Gb on a 64 bit machine due to the fact that in the past no one ever thought that you'd need more than 3,2Gb on a PC (memory hole reassignment required in order to use more than 3.2Gb).
Another thing you could check is in terminal with the command
```
free -m
```
This will give your memory as seen by Ubuntu in Megabytes.

---

### Post by robalcorn on 2008-05-31
> **Kevbert said:**
> Out of interest, what's your PC make, model ?  And are you using 32 or 64 bit Ubuntu ?  If the memtest program is passing on boot and no failures it may be due to the fact that you have some shared resources (read memory) which are being used by various system devices.  This can actually be worse if you are using 4Gb on a 64 bit machine due to the fact that in the past no one ever thought that you'd need more than 3,2Gb on a PC (memory hole reassignment required in order to use more than 3.2Gb).
Another thing you could check is in terminal with the command
```
free -m
```
This will give your memory as seen by Ubuntu in Megabytes.

My pc is home made and the o/s is 32 bit hardy. I will try your code in a bit and see what it says.

---

### Post by robalcorn on 2008-05-31
Here's my free-m

---

### Post by mister_pink on 2008-05-31
I don't think you'll get it to see any more with 32bit. Not easily anyway. There's an upper limit on how much RAM a 32-bit system can use due to the addressing of it. I *think* thats the issue here anyway.

[http://en.wikipedia.org/wiki/Conventional_memory#The_32-bit_3.2_gigabyte_barrier](http://en.wikipedia.org/wiki/Conventional_memory#The_32-bit_3.2_gigabyte_barrier)

---

### Post by Kevbert on 2008-06-01
> **robalcorn said:**
> My pc is home made and the o/s is 32 bit hardy. I will try your code in a bit and see what it says.

My PC too with 64 bit Gutsy Ubuntu, Hardy Kubuntu, Fedora 8, openSuse and XP. 
OK, what's the motherboard make and model and the bios make ?  You should have a manual on just this.
The maximum memory you are likely to see is about 2.9 Gb, so it might be possible to squeeze out a little bit more.

---

