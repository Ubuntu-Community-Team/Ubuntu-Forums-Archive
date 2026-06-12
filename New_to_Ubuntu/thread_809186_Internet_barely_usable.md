---
title: "Internet barely usable"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by portach king on 2008-05-27
Hi guys,
I'm having major trouble with my wireless at the moment. I'm using a Edimax Eg7318Ug USB dongle to connect online. I plugged it in and it worked fine, however suddenly as of this morning it's been acting strangely. It connects but whenever it starts to download anything my computer slows down to a chugging speed to the point hat I can't use it at all. This happens with websites that use flash etc and is is extremely unsettling.
Can anyone help? The only thing I can think that has changed is a 59Mb system update I got yesterday, but I don't remember having any troubles after my initial reboot after that.
I'd hugely appreciate some insight. Thanks guys!

---

### Post by Charbo00 on 2008-05-27
I am having the same problem on a linksys wireless pci card :(

---

### Post by portach king on 2008-05-27
Well lets hope that someone can help us out. Did it just start doing this to you today too Charbo00?

---

### Post by philinux on 2008-05-27
Yesterday there was a kernel update that broke some nvidia drivers and wifi.

Reboot and when grub stage 1.5 appears hit the esc key.

Choose the previous kernel to load. See if that makes any difference.

---

### Post by portach king on 2008-05-27
Thanks Philinux, I owe you one again. That fixed my problem. :)

EDIT:
I spoke too soon. The problem still exists. :(

---

### Post by Charbo00 on 2008-05-27
I just installed yesterday and it was slow the whole time. I had read that a fresh install might fix it so I did a fresh install booting from the live cd and my internet was fast on the live desktop and for a bit after I installed but it slowed down alot. I only get about 40kbs dl max like on package downloads and pages load slowly. I have an 8mb conn so I know its not that cause it works fine on my windows pc :(.

---

### Post by portach king on 2008-05-27
Likewise, if I boot from a live CD my wireless works perfectly fast. Have you tried what Philinux suggested? It didn't work for me, but it may in your case.
I should also point out again though, that it's not just the wireless that's slows down, my entire computer grinds to a halt when it tries to download. I can't even use nautilus.

---

### Post by philinux on 2008-05-27
Try this to test your connection.

[http://www.speedtest.bbmax.co.uk/](http://www.speedtest.bbmax.co.uk/)

---

### Post by Charbo00 on 2008-05-27
I didnt try his first suggestion because I'm also trying to fix my stuttering audio playback so I'm downloading the restricted acess stuff to see if that helps and I dont want to restart mid dl. I cant use that site because it says I need version 7 of flash but I installed flash alredy... My whole pc seems to slow down too, it takes longer to open windows and the stuttering audio gets worse...

---

### Post by portach king on 2008-05-27
Results from BBMax:
Wired Connection: 
Download:1741kbps
Upload: 215kbps

Wireless:
Download:755 kbps
Upload: 208kbps

Yesterday, the results would have been the same. The problem seems to be that as soon as I begin to download anything, it triggers something in my computer that slows the entire system down. Just as Charbo00 pointed out, my audio too begins to stutter when any downloading begins and even if I try to shut it off of press the mute button is takes upwards of ten seconds to react and even bring up a menu.

---

### Post by Charbo00 on 2008-05-27
I rebooted into the older kernal and at first I thought the internet problem was fixed, but after browsing for a few minutes, its as slow as ever. Like I said I cant use that test site, but testmy.net is giving me:

390 Kbps or 0.4 Mbps (48 kB/s)

That is awful for my connection, on this same computer when I had xp on it, I was getting no less than 1mb on a bad day.

---

### Post by philinux on 2008-05-27
There is this thread.

[http://ubuntuforums.org/showthread.php?t=768301](http://ubuntuforums.org/showthread.php?t=768301)

You could start one in networking and wireless quoting your network card etc.

---

### Post by portach king on 2008-05-27
Thanks Philinux. I created a thread in there this morning too. as of yet, it has gotten no attention. :(
It's heartbreaking, no matter what I always have trouble with wireless and Ubuntu. I even bought the usb dongle because it was "Linux compatible". What else can I do? :(

---

### Post by Charbo00 on 2008-05-27
This fixed it for me:

macafyc

I had the same problem. That's because the bit rate is set to 1 Mb/s

Type iwconfig. If you see in your wireless interface Bit Rate 1 Mb/s type sudo iwconfig xxxxxx rate 54M

xxxxxx should be the name of your wireless interface

Thanks alot to both philinux and macafyc.

Sorry this is off topic, but can anyone also help me with my sound stuttering? I cant even play audio on amarok it shows the progress moving but no sound...i have to play audio in movie player.

---

### Post by philinux on 2008-05-27
Sound stutter, I'd start a new thread.

But you could try System>Prefs>Sound and change it all to alsa instead of pulse audio, if you've not already tried that.

---

### Post by Charbo00 on 2008-05-27
how can I set it so I dont have to do this every time I restart?

---

### Post by portach king on 2008-05-30
I just want to bump this thread as I've still got the same problem since Monday.
Any help, guys, I'd seriously appreciate it.

---

### Post by Charbo00 on 2008-05-30
Setting the rate to 54M didnt work for you? That worked for me but I have to do it every time I reboot.

---

### Post by portach king on 2008-05-31
Hey Charbo00, thanks for the advise, but it already is set to 54M so clearly I'm having a different problem to yourself. One that seems to have only effected me by the looks of the responses I *haven't* been getting...  :(

---

### Post by portach king on 2008-06-02
*sad bump*

---

