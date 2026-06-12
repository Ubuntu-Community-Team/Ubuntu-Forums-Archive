---
title: "Bluetooth with Ubuntu 11.10"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by fairliedaft on 2012-02-10
Hi folks, this is my first post on the forum, although I have been a regular visitor since switching from Windows to Ubuntu around a year back. 

My problem, to which i have been unable to find a solution for is this. I am trying to use a Livewire H-28236 bluetooth USB dongle, but it wont show up anywhere on the system.

I have tried 'lsusb' and it doesnt show up at all, only card reader shows up, and my Blackberry if it is plugged in. Bluetooth manager doesn't show the bluetooth device either. i have tried many fixes i have found through many Google searches, yet none have yielded any results. I was using Ubuntu 11.04, but today i performed a clean install of 11.10 hoping for better results.

This is really bugging me, as it seems this dongle usually has no issues on Ubuntu systems, as most information i have seen seems to suggest its pretty much just plug in and go. 

I am using an Acer Aspire 5810t.

Any help on this matter would be greatly appreciated because I am completely stumped as to how to fix this issue. other than this, I have found Ubuntu to be relatively problem free thanks to the threads I have read on this forum.

---

### Post by lechien73 on 2012-02-10
Hi & welcome to the forums,

What output do you get from running:

```
dmesg
```

after plugging in the dongle?

---

### Post by fairliedaft on 2012-02-10
Hundreds of lines of stuff appears. Is there anything in particular I should be looking for to help narrow it down a little?

---

### Post by lechien73 on 2012-02-10
Maybe you could try filtering the output. Try:

```
dmesg | grep -i usb
```

You can post the output here between CODE tags - use the **#** button on the post toolbar.

---

