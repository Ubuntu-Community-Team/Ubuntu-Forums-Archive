---
title: "Can not connect to the internet"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by newbee. on 2008-06-28
Serious beginner here. Just installed ubuntu for the first time ever. I'm trying to access the internet, but I can't. I'm on a hardwired connection, not wireless. How do I go about doing this?

---

### Post by wrtpeeps on 2008-06-28
[http://ubuntuforums.org/showthread.php?t=843454](http://ubuntuforums.org/showthread.php?t=843454)

:confused:

---

### Post by newbee. on 2008-06-28
> **wrtpeeps said:**
> [http://ubuntuforums.org/showthread.php?t=843454](http://ubuntuforums.org/showthread.php?t=843454)

:confused:

That was when I had kubuntu. It was suggested that I switch to ubuntu, I did so, and still a no go.

---

### Post by ConMan318 on 2008-06-28
I assume you have network manager installed, what happens when you click on that?  It's in the upper right, near the clock, by default.  Does it not show any networks available to connect to?  Or will it just not connect to it when you try?

Or maybe it says you're connected, but won't let you access the internet.

Basically, we just need more information :p

Like answering the questions above, and telling us what you have tried already.

---

### Post by newbee. on 2008-06-28
> **ConMan318 said:**
> I assume you have network manager installed, what happens when you click on that?  It's in the upper right, near the clock, by default.  Does it not show any networks available to connect to?  Or will it just not connect to it when you try?

Or maybe it says you're connected, but won't let you access the internet.

Basically, we just need more information :p

Like answering the questions above, and telling us what you have tried already.

Not sure about network manager. I've got a network settings thing in the system tab.. I haven't tried much, because I don't know what I'm doing..

---

### Post by wrtpeeps on 2008-06-28
By the way, by "hardwired connection", you mean ethernet cable, right?

---

### Post by newbee. on 2008-06-28
> **wrtpeeps said:**
> By the way, by "hardwired connection", you mean ethernet cable, right?

Correct. It's connected to a hub, which is connected to a router.

---

### Post by wrtpeeps on 2008-06-28
And if you open network manager, what do you see?

---

### Post by ConMan318 on 2008-06-28
What happens when you go to System > Administration > Network?  When that opens, click unlock and enter your password.  Then, if "Wired Network" is there, right-click it and click properties, and check to see if it is enabled.  If not, enable it.

So is there something in the upper right corner that shows something that looks like a network icon?  It may look like two computer monitors overlapping eachother, probably with an 'X' over them since you aren't connected.  Is that missing from your taskbar?

---

### Post by newbee. on 2008-06-28
> **ConMan318 said:**
> What happens when you go to System > Administration > Network?  When that opens, click unlock and enter your password.  Then, if "Wired Network" is there, right-click it and click properties, and check to see if it is enabled.  If not, enable it.

So is there something in the upper right corner that shows something that looks like a network icon?  It may look like two computer monitors overlapping eachother, probably with an 'X' over them since you aren't connected.  Is that missing from your taskbar?

I have "Wireless Connection - Roaming Mode Enabled" and "Point to Point Connection - This network interface is not connected"

The icon in the top right is two computers overlapped with a triangle with a ! in it.

---

### Post by wrtpeeps on 2008-06-28
I may be mistaken, but is the yellow ! not "limited connection" as opposed to no connection?

---

### Post by newbee. on 2008-06-28
> **wrtpeeps said:**
> I may be mistaken, but is the yellow ! not "limited connection" as opposed to no connection?

It's orange. Mouseover says "No network connection"

---

### Post by ConMan318 on 2008-06-28
Well since Sys > Admin > Network does not show a 'wired connection', it means that either Ubuntu is not recognizing the ethernet port you are plugged in to, or that your wired connection is not working correctly.

So, do you know that you are getting internet through that port, i.e. can you connect another computer through it?

If so, it means Network Manager is not taking any input from your ethernet port.  Are you sure you are using an ethernet cord?  The port your ethernet cord is plugged into your computer should have three squares and a line on it, not a picture of a phone.  I've seen people try to plug in directly through the phone line and not be recognized.

If your internet is working, and you are plugged in through an ethernet port, then we have to figure out how to get it recognized.  Can you post the results of
```

ifconfig

```

---

### Post by newbee. on 2008-06-28
> **ConMan318 said:**
> Well since Sys > Admin > Network does not show a 'wired connection', it means that either Ubuntu is not recognizing the ethernet port you are plugged in to, or that your wired connection is not working correctly.

So, do you know that you are getting internet through that port, i.e. can you connect another computer through it?

If so, it means Network Manager is not taking any input from your ethernet port.  Are you sure you are using an ethernet cord?  The port your ethernet cord is plugged into your computer should have three squares and a line on it, not a picture of a phone.  I've seen people try to plug in directly through the phone line and not be recognized.

If your internet is working, and you are plugged in through an ethernet port, then we have to figure out how to get it recognized.  Can you post the results of
```

ifconfig

```

I double checked, and it's def. an ethernet port, not the telephone port. Also, this is a super noob question. How do I run the ifconfig command?

---

### Post by ConMan318 on 2008-06-28
Go to Applications > Accessories > Terminal.  Then type "ifconfig" and hit enter.  Then just paste those results, please.

---

### Post by newbee. on 2008-06-28
> **ConMan318 said:**
> Go to Applications > Accessories > Terminal.  Then type "ifconfig" and hit enter.  Then just paste those results, please.

Best I can do is take a picture. I have no way of transferring between these two computers, but I do have a pretty decent SLR to take pictures with. :)

[IMG]http://i32.tinypic.com/1zfiro7.jpg[/IMG]

---

### Post by ConMan318 on 2008-06-28
Alright, so it seems that your ethernet driver is not recognized by default, since there should be another block with "eth0" instead of "lo".  If you go to "System > Administration > Hardware Drivers", does anything show up that looks like it might be for an ethernet driver?  It will probably have a red circle next to it since it is obviously not enabled.  If one shows up, try to enable that.

If there is nothing relevant there (like if there are only video drivers and such, which we aren't worried about at the moment), try going to "System > Administration > Software Sources".  Then click the "Third-party sources" tab and check those boxes.  Hopefully there is a source made for your connection type that just isn't in the default repositories.

---

### Post by newbee. on 2008-06-28
> **ConMan318 said:**
> Alright, so it seems that your ethernet driver is not recognized by default, since there should be another block with "eth0" instead of "lo".  If you go to "System > Administration > Hardware Drivers", does anything show up that looks like it might be for an ethernet driver?  It will probably have a red circle next to it since it is obviously not enabled.  If one shows up, try to enable that.

If there is nothing relevant there (like if there are only video drivers and such, which we aren't worried about at the moment), try going to "System > Administration > Software Sources".  Then click the "Third-party sources" tab and check those boxes.  Hopefully there is a source made for your connection type that just isn't in the default repositories.

Only driver in the hardware drivers was nvidia, so that would be a video driver. In the software sources, both boxes were already checked.

---

### Post by newbee. on 2008-06-28
I've also got a CD here that contains drivers, though I don't know if they'll work with linux. I have to head to work now, but I will check this thread after work to see if I can find any more help.

Thanks a lot guys!

---

### Post by ConMan318 on 2008-06-28
There were only 2 boxes in Software Sources?  What were they?  You seem to be missing some.

---

### Post by newbee. on 2008-06-28
> **ConMan318 said:**
> There were only 2 boxes in Software Sources?  What were they?  You seem to be missing some.

[http://archive.canoical.com/ubuntu](http://archive.canoical.com/ubuntu) hardy partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner source code

---

