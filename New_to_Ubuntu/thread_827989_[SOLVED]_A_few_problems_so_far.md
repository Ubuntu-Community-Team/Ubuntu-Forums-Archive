---
title: "[SOLVED] A few problems so far"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by swaknight on 2008-06-13
ok, I am new with Ubuntu, obviously, and I have experienced a few problems that have become annoying lately.

first: when I boot, about 75% of the time I get a ac_et_wait timeout error or something like that and have to restart. I do not get this error when I boot from recovery mode however.

Second: I have had my computer freeze a number of times. nothing that is not on the desktop responds, ie. firefox, pidgin, evolution, the shutdown process (either via the button on screen or the laptop it self) etc...

I have a Sony Vaio VGN-N320E with Intel everything it appears. I am also dualbooting with Vista Home Premium (yuck lol)

If anyone can help, I would be thankful.

---

### Post by _sphinx_ on 2008-06-13
When exactly does your computer freezes. Is it totally random?

---

### Post by swaknight on 2008-06-13
As far as i can tell, though one time it was because of the Avant manager I just installed. Other then that, it has been pretty random.

---

### Post by ukripper on 2008-06-13
> **swaknight said:**
> ok, I am new with Ubuntu, obviously, and I have experienced a few problems that have become annoying lately.

first: when I boot, about 75% of the time I get a ac_et_wait timeout error or something like that and have to restart. I do not get this error when I boot from recovery mode however.

Second: I have had my computer freeze a number of times. nothing that is not on the desktop responds, ie. firefox, pidgin, evolution, the shutdown process (either via the button on screen or the laptop it self) etc...

I have a Sony Vaio VGN-N320E with Intel everything it appears. I am also dualbooting with Vista Home Premium (yuck lol)

If anyone can help, I would be thankful.

go to terminal and  post output of the following:
```
dmesg | tail
```
```
cat /var/log/messages | grep '(EE)'
```
```
uname -a 
```

---

### Post by _sphinx_ on 2008-06-13
Are you able to hit Alt+Ctrl+F1 . If you are, then login there and type ```
top
``` and see which process is consuming your resources, and kill that process.

---

### Post by swaknight on 2008-06-13
andrew@andrew-laptop:~$ dmesg | tail
[   86.679692] CPU1 attaching NULL sched-domain.
[   86.689139] CPU0 attaching sched-domain:
[   86.689148]  domain 0: span 03
[   86.689152]   groups: 01 02
[   86.689162] CPU1 attaching sched-domain:
[   86.689166]  domain 0: span 03
[   86.689171]   groups: 02 01
[   91.116482] NET: Registered protocol family 17
[  124.378409] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  145.027151] ath0: no IPv6 routers present
andrew@andrew-laptop:~$ cat /var/log/messages | grep '(EE)'
andrew@andrew-laptop:~$ uname -a
Linux andrew-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

--------------------------------------------------------------------------

nothing came up when i did cat /var/log/messages | grep '(EE)'

---

### Post by ukripper on 2008-06-13
> **swaknight said:**
> andrew@andrew-laptop:~$ dmesg | tail
[   86.679692] CPU1 attaching NULL sched-domain.
[   86.689139] CPU0 attaching sched-domain:
[   86.689148]  domain 0: span 03
[   86.689152]   groups: 01 02
[   86.689162] CPU1 attaching sched-domain:
[   86.689166]  domain 0: span 03
[   86.689171]   groups: 02 01
[   91.116482] NET: Registered protocol family 17
[  124.378409] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  145.027151] ath0: no IPv6 routers present
andrew@andrew-laptop:~$ cat /var/log/messages | grep '(EE)'
andrew@andrew-laptop:~$ uname -a
Linux andrew-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

--------------------------------------------------------------------------

nothing came up when i did cat /var/log/messages | grep '(EE)'

re-boot and use 2.6.24-16 generic kernel. test whether you get anymore lockups.

---

### Post by swaknight on 2008-06-13
I did and I got the same error :(

the error is:
> [  18.184044] ACPI: EC: acpi_et_wait timeout, status = 0, expect_event = 1
[  18.184096] ACPI: EC: read timeout, command = 128

---

### Post by ukripper on 2008-06-13
> **swaknight said:**
> I did and I got the same error :(

the error is:

[https://bugs.launchpad.net/ubuntu/+bug/222864](https://bugs.launchpad.net/ubuntu/+bug/222864)
On launchpad there is bug filed against the laptop you are using and solution is to disable splash quiet.

i can guide you how to disable boot splash screen in grub.

Follow the steps below:
1.go to terminal and type```
sudo gedit /boot/grub/menu.lst
```
2. find  your kernel 2.6.24-18
something like below :
> /boot/vmlinuz-2.6.24-18-generic root=UUID=97ed331d-6aab-4953-af1f-d0b66e4f0003 ro quiet splash
and remove > quiet splash from the end .
so that line should end at > ro save and exit
3. in terminal type > sudo update-grub
4.and reboot your machine and see if that fixes your errors.
:)

---

### Post by swaknight on 2008-06-13
Thank-you

I will try it when I switch back to Ubuntu.
Also, Ubuntu as locked up twice on me today, forcing me to shutdown manually. I dont know if it has something to do with what you mentioned.

> Are you able to hit Alt+Ctrl+F1 . If you are, then login there and type
Code:
top
and see which process is consuming your resources, and kill that process.

I followed your advice, but i was only using about 700 MB out of 2GB RAM and the process using the most cpu was the Top.

All I was doing was chatting on pidgin and surfing the web.

---

### Post by ukripper on 2008-06-13
first try the workaround i have posted after that we can see if it still locks up

---

### Post by swaknight on 2008-06-14
thank you, it booted without a problem. 

As for the locking up, it still seems random, but if it doesn't happen today, I don't think i will worry about it too much more.

---

### Post by ukripper on 2008-06-14
> **swaknight said:**
> thank you, it booted without a problem. 

As for the locking up, it still seems random, but if it doesn't happen today, I don't think i will worry about it too much more.

great it worked out for you. Can you mark this thread as solved if you don't get lockups and error messages.:)

---

### Post by swaknight on 2008-06-14
okay, i thought that this was completely solved, but alas, it was not.

It just froze up on me for no reason again. but i think i am noticing a pattern, first firefox hogged the sound, and when i closed it, I could not restart it. Then pidgin died on me, then it froze.

---

### Post by ad_267 on 2008-06-14
You could try switching to another browser like Opera or Epiphany and see if that stops this from happening.

---

### Post by swaknight on 2008-06-14
nope, i switched to the new Opera, which is very nice by the way, and i still have the same problem. Is there any way besides the systems moniter to check if firefox is still somehow running in the background?

---

### Post by prshah on 2008-06-15
> **swaknight said:**
> Is there any way besides the systems moniter to check if firefox is still somehow running in the background?

Open a terminal (Applications-Accessories-Terminal), then give the following command ```

ps -e | grep -i firefox

```

---

### Post by ukripper on 2008-06-15
> **swaknight said:**
> okay, i thought that this was completely solved, but alas, it was not.

It just froze up on me for no reason again. but i think i am noticing a pattern, first firefox hogged the sound, and when i closed it, I could not restart it. Then pidgin died on me, then it froze.

If you got effects enabled then disable then see if it still freezes. compiz had been great cause of these lockups and also could you try 2.6.24-19 generic kernel. you can update that enabling proposed repos. go to system-->administration-->software sources and find proposed updates and tick it and reload.
then just go to terminal and type:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
you will be see 2.6.24-19 generic kernel will available for you.
after updates just run:
```
sudo update-grub
```
and then reboot and select taht new kernel during bootup.

---

### Post by swaknight on 2008-06-15
ok, will i still need to get rid of the ```
Quiet splash
``` leaving it to end in ```
ro
``` in the menu.lst?

---

### Post by ukripper on 2008-06-15
> **swaknight said:**
> ok, will i still need to get rid of the ```
Quiet splash
``` leaving it to end in ```
ro
``` in the menu.lst?

yes you will need to get rid of that as well for time being and end line with ro.

until new kernel is available from main repos.

---

### Post by swaknight on 2008-06-15
okay, i have been running the .19 kernel all day with no problems *gulp*
I did not turn off the desktop effects either, which are running at full by the way, and still no issue.

I think it is safe to say this is solved, thank you everybody for you're help

---

### Post by ukripper on 2008-06-16
> **swaknight said:**
> okay, i have been running the .19 kernel all day with no problems *gulp*
I did not turn off the desktop effects either, which are running at full by the way, and still no issue.

I think it is safe to say this is solved, thank you everybody for you're help

Great. Next release of kernel should sort your acpi errors as well hopefully then yu won't need to take splash off from your grub menu.

:)

---

### Post by swaknight on 2008-06-16
cool, thanks, looking forward to it

---

