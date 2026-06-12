---
title: "Funny behaviour with sound"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by gornomatic on 2008-10-02
I know that sound issues have been posted on the forum. I'm posting this because even though the problem is a trivial one, it strangely sorted itself out and I'm curious to know how!

Well, the sound suddenly stopped working. So here are the things I did
1) Checked lspci to check for my driver
2) Opened alsamixer to check if anything was mute, it wasn't
3) Installed gnome-alsamixer and did (2), same result :P
4) Opened preferences from the speaker button and tried the different devices till I came back to the one I was using initially
5) Was about to give up when voila! The sound suddenly restarted!

Any ideas as to why this happened?

---

### Post by whizbaby on 2008-10-02
Have you checked all cablings?^^
I once had a really weird graphics problem which disappeared as I replaced the monitor cable.,.
and as a(n amateur) musician I can tell you those cables can mess up quite some recordings.
If the cables are ok then maybe
-the PCI controller on the mainboard isnt working well with linux (try booting with the 'noapic' kernel option if the problem appears again.)
-the soundcard is a wreck (hope its not that)
-your computer is placed on native american burial grounds or influenced by a bad constellation of stars :P ;)

---

### Post by gornomatic on 2008-10-02
Here's the latest update:
It suddenly stopped again!
In frustration, i clicked on the speaker bar and moved the volume up and down like a maniac, upon which it started for five seconds again and then stopped again!! 
Now, it's not turning on. 
There really seems to be some sort of a problem, will look at it more seriously now.
Any suggestions?

---

### Post by gornomatic on 2008-10-02
Turns out my speakers have some loose wiring .. How embarrassing .. All's well now. Thank you. Closed.

---

### Post by whizbaby on 2008-10-02
Yes, try turning off acpi and see if the problem persists.
```
sudo nano /boot/grub/menu.lst
```
and then add noapic to the line of your default boot kernel :
```
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=8a1db39f-a2ad-4818-9c2b-0dc768cdc500 ro quiet splash noapic
```
[COLOR="Red"]/!\WARNING/!\[/COLOR] please do not copy-paste from the code-section above because your disks UUID is different from mine and your system will not boot anymore[COLOR="Red"]/!\WARNING/!\[/COLOR]
then reboot and good luck!

---

### Post by whizbaby on 2008-10-02
> **gornomatic said:**
> Turns out my speakers have some loose wiring ..
Yeah I win :guitar:
> 
 How embarrassing 
Not really...the god of cables just happens to not like mankind.

---

### Post by gornomatic on 2008-10-02
Lol! Thanks man :)

---

