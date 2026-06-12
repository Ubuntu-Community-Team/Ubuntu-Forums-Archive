---
title: "Drivers"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Adeel156 on 2008-05-28
I just installed Ubuntu 8.something a few days ago. Getting the compatible drivers has been a real pain in the neck for these 2 - 

My motherboard (Verrry Old! I found the link in the archives. :p)- 

[http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=1065](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=1065)

Kindly let me know which one is compatible with my version of Ubuntu. :)

And - 

My Sony DVD RW DRU-830A

[http://sony.storagesupport.com/product/128](http://sony.storagesupport.com/product/128)


Could somebody please find me the compatible drivers for these two? 
Will Be highly appreciated. :)

Edit - I installed Ubuntu with a partition with Windows XP SP2, I gave the 15GB i had free at the time to Ubuntu. I now have 33GB free, how do I put this into Ubuntu partition? ALso, is there a way I could transfer my files from XP to Ubuntu?

---

### Post by quelx on 2008-05-28
Is something not working?  The drivers for both of these devices are most likely already loaded.

---

### Post by Adeel156 on 2008-05-28
Well the DVD RW isnt working, that much I know.

---

### Post by quelx on 2008-05-28
Open a terminal (**ALT-F2** > **gnome-terminal**) and type ```
ls -l /dev/{cd,dvd}*
``` you should see things like ```
/dev/dvdrw -> scd1
``` indicating the system recognized the drive and that it was a CDRW.

Are you not able to burn CD's or DVD's or both?

Do you have a cd burning package installed, **System** > **Administration** > **Synaptic Package Manager**

I think the default application is **brasero** but you may like **k3b** or **xcdroast** try installing those and see what you get.

---

### Post by Adeel156 on 2008-05-28
Well, my drive wont read CD's or DVD's, i think need to get that fixed first. :p

But ill try what u said anyway.

Anything for the 2nd problem? :)

---

### Post by Adeel156 on 2008-05-28
Location of file not found, I probably typed it wrong.

In the mean time I'll get the internet and my Graphics card working through the usb(I'm typing this from Windows).

---

### Post by Adeel156 on 2008-05-28
Damnit!!!

It now seems that the cd which contains my modems configuration is too scratchy too work...And the download for it looks to take a few hours.... :@ :@ :@ :@

---

### Post by quelx on 2008-05-28
Your network card should produce output from ```
ifconfig
``` (other than lo) what about ```
dmesg|grep CD
```?

---

### Post by Adeel156 on 2008-05-28
Is that to be done from the terminal as well?

Is there anyway I can open Ubuntu through Windows? because if I restart it would permanently close my Modem download...

What a situation... :S

---

### Post by quelx on 2008-05-28
Ahhh, you are dual booting, well no... it's not possible to run Ubuntu while Windows is already loaded, maybe someday when hardware virtualization really takes off. When you get back into Ubuntu run those commands and post the output here.  Is the network working in Ubuntu?

---

### Post by Adeel156 on 2008-05-28
Umm, I've seen a friend of mine opening Ubuntu through Windows - So there has to be a way? 

From what I see, its still a few hours until I can open Ubuntu again. :(

---

### Post by quelx on 2008-05-28
Your friend is using a virtual machine; vmware, virtualbox, or the like.  They are essentially running a second computer inside Windows, where you have Ubuntu installed on the actual machine.

---

### Post by Adeel156 on 2008-05-28
Dang.

---

### Post by Adeel156 on 2008-05-29
Turns out the drivers for my DVD RW were akready loaded.

BUT the configuration for modem is in exe format, I cant use the internet without configuring? What do I do?

From 1st post --- I installed Ubuntu with a partition with Windows XP SP2, I gave the 15GB i had free at the time to Ubuntu. I now have 33GB free, how do I put this into Ubuntu partition? ALso, is there a way I could transfer my files from XP to Ubuntu?

---

