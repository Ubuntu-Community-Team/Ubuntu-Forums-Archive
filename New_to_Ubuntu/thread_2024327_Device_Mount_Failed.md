---
title: "Device Mount Failed"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by tonsil on 2012-07-13
I have kubuntu installed on my external HD which is connected via USB. It was working perfectly until yesterday when right after logging in, it showed the notification: Device Mount Failed. I can't truly say what is going wrong; when I open Dolphin file manager I can access the filesystem. The only trouble I ran across is all my icons vanished in the activities bar. I can change from one activity to the other, but the icons have returned to the their circular default shapes and cannot be changed any longer. From what I can say the rest of the system works fine.

Do you think my external HD is alright? What can I do about this message? It keeps popping up every time I boot into kubuntu.

---

### Post by robtygart on 2012-07-13
Do you have any files located on a different harddrive then the Kubuntu installation?

Also you should be able to edit the activity icons.

---

### Post by tonsil on 2012-07-13
I'm running this on an Acer laptop. It came with windows, so it is installed on the main HD. The external drive where kubuntu is, is an IDE ATA drive connected via 3.5" External Storage Case through USB, and has several parrtitions. It has kubuntu, windows xp (that does not work with my 64 bit laptop), an ntfs partition without an OS and the swap partition.

As for activity icons, I can go and pick an icon of my choice, however when I click Accept Changes the icons do not change. I just tried it, and it accepts a different name for the activity. The activities work fine too.

---

### Post by tonsil on 2012-07-15
It turns out the error message is in a different wording. It pops up and then it is gone, so here is exactly what it says. I had none of this a few days ago.[IMG]http://i302.photobucket.com/albums/nn113/zlvrz/IMG_0797.jpg[/IMG]

---

### Post by tonsil on 2012-07-22
Help, anyone?

---

### Post by tonsil on 2012-07-22
Ok, so I thought I should check out what the OS is doing on startup. I went into system settings -> startup and shutdown and clicked "on login start with an empty session". When I restarted the system, the annoying message disappeared. That is a relief!

That said, my icons for activities are still not there. They are in their default and I can't change them either. And I wish I could move those activities and switch places. It is needed so obviously. Click+hold, drag the activity...

---

### Post by bobsan on 2012-07-22
So what is the 40G hard drive that it complains does not mount? Did you have a 40G hard drive connected before you power off last time?

---

### Post by tonsil on 2012-07-23
Ok, I turned on my laptop this morning and I have the same message again. The 40 GiB partition it is supposedly unable to mount is where Kubuntu is actually installed. I didn't want to mess up my main hard disk where windows 7 is installed. So I installed it to my external drive which has 4 partitions.

---

