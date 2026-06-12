---
title: "Unable To Print From mtpaint."
date: 2013-03-17
forum: New to Ubuntu
---

### Post by BlueKite on 2013-03-17
Hello,

I am using Lubuntu 11.10 on an Acer Aspire One Netbook, and it was my great pleasure to get my netbook printing this weekend, having failed with previous Linux os's.:D
And it was a great surprise that I could get a scan from the same machine - all wirelessly.:D:D

But, I am unable to print a picture from mtpaint. The option to print is in the File Menu: File>Actions>Print
But nothing happens. It doesn't even show up in the print queue.

Is there any way of rectifying this?

Any help would be appreciated, especially a step-by-step guide if anything complicated is required.

Many thanks,

BlueKite.

---

### Post by BlueKite on 2013-03-23
Hello,

Well, I've managed to fix this myself after some further googling.

Basically you need to install gtklp, which can be found in Synaptic Package Manager.

Then open mtpaint, go to File>Actions>Configure and click on Print image.

Then in the Command box, replace [FONT=Courier New]kprinter %f,[/FONT] with[FONT=Courier New] gtklp %f .

[FONT=verdana]And then you can print your picture. 

I haven't figured out how to print a reasonably sized picture yet, (a scanned cd cover printed over 4 A4 sheets!) but it will probably become obvious with some experimentation.

I found the above information on the Puppy Linux Discussion Forum
[http://www.murga-linux.com/puppy/viewtopic.php?t=59939](http://www.murga-linux.com/puppy/viewtopic.php?t=59939)

which links to the helpful Puppy Linux: Using mtpaint page
[http://puppylinux.org/wikka/UsingMtPaint](http://puppylinux.org/wikka/UsingMtPaint)

So many thanks to all involved there for the information.

BlueKite.[/FONT][/FONT]

---

