---
title: "USB 2.0 working but USB 3.0 isn't"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by Bialetti741 on 2014-05-12
Hi,
i'm new to Linux/Ubuntu so i'm not sure how to resolve this.
I'm using Ubuntu 14.04 LTS and i have a Gigabyte mother board with several USB ports with a mixture of 2 & 3.

When i plug in an external HDD which is USB3.0 in to a 2.0 port it works fine and i can access the data, but when i plu it into any usb 3.0 it doesn't do anything. The LED on the HDD does flash and then stays on as normal,but i cant access it.

Do i need to install software for USB3 to work?


Thanks

---

### Post by WoodenWalker on 2014-05-12
You should not need to install any software for usb 3.0 to work in Linux, specifically Ubuntu. It has been included since 2009, to my knowledge. The error is most likely arising from somewhere else, but I am unsure where. I'm certain OldFred will know though. He is likely to have a pretty extensive answer for this.

---

### Post by Bialetti741 on 2014-05-19
My USB 3.0 is now working. I came across someone else who posted the resulution and i thought i too had better share to help anyone else.


Step 1: Open up Terminal (Ctrl+Alt+T)

Step 2: type: **sudo gedit /etc/default/grub**

Step 3: in the text file that opens (from running the above command), look for the line that reads **GRUB_CMDLINE_LINUX=""**

step 4: change the line of code to read: **GRUB_CMDLINE_LINUX="iommu=soft" **and then save and close the file.

Step 5: restart your computer and enter the _**BIOS**_ and _**Disable IOMMU**_ and save and exit BIOS.

Step 6: Boot into Ubuntu and USB 3.0 should now work.


NOTE: the post i found came from: [http://hardforum.com/showthread.php?t=1807755](http://hardforum.com/showthread.php?t=1807755)


Hope this helps anyone else with same issue.

---

