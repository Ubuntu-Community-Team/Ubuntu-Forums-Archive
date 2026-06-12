---
title: "Enabling USB devices and wireless"
date: 2007-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by dkaddict on 2007-06-18
This is my first attempt at writing a how 2 for (K)Ubuntu so if I leave anything out or don't make sense, please correct me.

Ok, for the first few months after switching to Linux last year, I couldn't get ubuntu to recognise any of my USB devices if I plugged one in while the OS was up and running. I could only read/write to these devices if I first powered down, plugged in a device while my computer was off, and rebooted with said device plugged in. Even that frustratingly inconvenient action didn't agree with (K)Ubuntu so my USB devs' had a fraction of their potential functionality.

I couldn't find an answer to my woes anywhere. None of my posts here and in other forums helped either. Then, one day I came across a post here which discussed APCI and told how to turn it off by way of editing the /boot/grub/menu.lst directory. Because I had been instructed by people in the past to open a terminal and enter 'dmesg' in an attempt to work out why my devices, I realised that APCI was referred to a lot in the output of dmesg so decided to try disabling APCI at boot as per the instructions in the post.

Here's what I did.

Open terminal and enter command>

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

To create back up of original dir.

Next, to amend /boot...menu.lst

```
sudo gedit /boot/grub/menu.lst 

```
(for Kubuntu I use>"kdesu kate /boot/grub/menu.lst"

Gedit or Kate will then open the file.

Next, scroll down to the line which begins with the word 'kernel'

Mine looks like this>

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash
```

Next, after the word 'splash' I entered 'noapic'

So it looks like this>

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash noapic
```

I saved the file quit Kate, quit my terminal, and rebooted (dunno if that's necessary).

When (K)Ubuntu was running again, I plugged in a flash drive and Bingo, it was recognised and mounted. I was well pleased. Now my (K)Ubuntu was as functional as the OS I was trying to escape. Or so I thought.

A couple of months later, I signed up to a new ISP who provided a wireless router with their broadband package.
My notebook has a built in wireless card. When, however, I turned it on, it wouldn't work without a reboot, and when I did that, the 'noapic' option was removed from my /boot/grub/menu.lst. USB and Wireless, it seemed, could not be utilised at the same time on my notebook. I had knowledge of the /boot...menu.lst file now, however, and a quick search with Google bore fruit. I came across a post (can't remember URL or which forum, sorry) which told of another option for /boot/grub/menu.lst called irqpoll.

I gave it a try.

I opened a terminal and followed the same instructions as those above.

On the line which I had amended, I erased 'noapic' and entered 'irqpoll' in its place.

It then looked like>

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash irqpoll

```
Yippeeee, it worked. Now I have wireless and USB

I really hope the above guide can help someone. My time trying to get USB to work in Ubuntu was frustrating to say the least. I haven't yet came across a post or how2 which addresses the problem I had with USB. This post would have saved me a lot of time. In searching for answers, however, I learnt a fair bit about Linux etc so t ain't all bad.

Please make sure you have a good idea of what to do before attempting messing about with /boot/grub/menu.lst
I am the sole user of my comp, back my system up regularly, and have a seperate 'home' partition so a reinstall is not a great drama for me if I screw anything up.

It has been a while since I discovered the 'noapic' 'irqpoll' options and have forgotten the URLs of the posts/sites which helped me. I shall endeavour to find them.

Here are a couple of maybe useful links.

[http://www.acpi.info/](http://www.acpi.info/)

[http://ubuntuforums.org/showthread.php?t=386173&highlight=APCI+USB+devices](http://ubuntuforums.org/showthread.php?t=386173&highlight=APCI+USB+devices)  (this is close to the 'dmesg' outputs I used to get.

[http://ubuntuforums.org/showthread.php?t=475763&highlight=noapic](http://ubuntuforums.org/showthread.php?t=475763&highlight=noapic)  (similar problem to mine)

---

