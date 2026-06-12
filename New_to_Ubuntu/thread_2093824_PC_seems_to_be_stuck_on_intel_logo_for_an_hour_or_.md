---
title: "PC seems to be stuck on intel logo for an hour or more"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by mrnewtothis on 2012-12-11
I have looked around the net and it is coming up with all sorts of reasons and ways to fix it but most make no sense.

I had just updated new updates for ubuntu and came back and had to restart and then it just hangs there on the Intel inside logo.

If I kill it with the off switch on the front of PC and leave it plugged in it starts up by itself now also. But is still stuck on the logo for an hour.

I have a Dual boot of Ubuntu 10 4 and XP pro and have already ran antivirus and malware searches on xp just in case.

The only thing I plugged in new was my printer which I have now unplugged, which was no biggie as I had not added the drivers. Still searching for the printer disc.

Any ideas or any way to find out what those updates were just to check they are not to blame?

I'll be back eventually to check answers, once it lets me on.

---

### Post by oldfred on 2012-12-11
Lets first see what this says. It will only tell us about Boot Configuration or possibly file corruption.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by mrnewtothis on 2012-12-12
> **oldfred said:**
> Lets first see what this says. It will only tell us about Boot Configuration or possibly file corruption.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

I did what was suggested on the first link twice and I get a pop up box that tells me it needs pastebinit.

I can't find it but I do load another set of tools that I found in the software center.

When I hit continue I get a box and a terminal window. The box reads:

Boot successfully repaired.

A new file (~/Boot-Info_2012-12-12__16h00.txt) will open in your text viewer.

In case you still experience boot problem, indicate its content to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (500GB) disk!

And in the terminal it is too big for the page so I can either break it up or point me in the direction of the important bits that you would need to see.

Still doing the hold when I restarted

---

### Post by bogan on 2012-12-12
Hi!,** mrnewtothis**,

Here is another 'solution' that makes no sense, but often works with this sort of hang-up.

[COLOR=Red]A Cold-Finger Reset[/COLOR]:
Shut down & Switch Power switch off, remove power cable - if a Laptop, disconnect battery,- remove all external devices, except the Monitor.

Hold Power button down for at least 30 seconds, or longer if you do not get a flash from the Disk activity light.

Reconnect and reboot with crossed fingers.

I got this originally from the AMIGA, and later from the Medion official Help line. It is something to do with discharging condensors and cleaning corrupted Handshaking memory -especially with Monitors.

Good Luck! & a belief in Magic also helps.

Chao!,** bogan.**

---

### Post by oldfred on 2012-12-12
If Bogan's suggestion does not work, post the BootInfo report.

If Internet is working when you run the BootInfo report it should just put a copy in pastebinit to make it easy to access.

You can copy it into a message (or as parts if necessary) just be sure to use code tags to preserve formatting and make it easy to review. To easily get code tags, hightlight like copy and click on # in edit panel above message.
       Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by mrnewtothis on 2012-12-12
> **oldfred said:**
> If Bogan's suggestion does not work, post the BootInfo report.

If Internet is working when you run the BootInfo report it should just put a copy in pastebinit to make it easy to access.

You can copy it into a message (or as parts if necessary) just be sure to use code tags to preserve formatting and make it easy to review. To easily get code tags, hightlight like copy and click on # in edit panel above message.
       Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

I was going to show the info in the file but the file belongs to root and I'm to allowed to open it. Tried to change it through permissions.

When I tried it I did not have pastebinit and it does not show up software centre.
Anyone knows where to get it it may help for a third try of this.

I will try Bogans method and see if that works. and if that does not work I will try do it again and see if there is another way to save the data if no one has the pastebinit link by then.

---

### Post by oldfred on 2012-12-12
I have not seen nor have I had to install pastebinit as part of Boot-Repair, it just installed it I think. Was an error posted as it needs Internet to download several utilitys? Or a bug in Boot-Repair?

[https://launchpad.net/ubuntu/+source/pastebinit](https://launchpad.net/ubuntu/+source/pastebinit)

---

### Post by mrnewtothis on 2012-12-12
> **bogan said:**
> Hi!,** mrnewtothis**,

Here is another 'solution' that makes no sense, but often works with this sort of hang-up.

[COLOR=Red]A Cold-Finger Reset[/COLOR]:
Shut down & Switch Power switch off, remove power cable - if a Laptop, disconnect battery,- remove all external devices, except the Monitor.

Hold Power button down for at least 30 seconds, or longer if you do not get a flash from the Disk activity light.

Reconnect and reboot with crossed fingers.

I got this originally from the AMIGA, and later from the Medion official Help line. It is something to do with discharging condensors and cleaning corrupted Handshaking memory -especially with Monitors.

Good Luck! & a belief in Magic also helps.

Chao!,** bogan.**

I don't know how and your post did make me laugh but it did work.

I have restarted about ten times so far and it has worked each time.

Thanks

And thanks for that link OldFred I am sure I will need that in the future.

Can someone mark this as answered

---

### Post by bogan on 2012-12-13
Hi!,** mrnewtothis,**

Great! Another magical cure!

> Can someone mark this as answered     Select: 'Mark Thread as Solved' in the drop-down menu of 'Thread Tools', at the top of the Thread display.

Only you, as the 'OP', or a Moderator, can do it.

Chao!, bogan.

---

### Post by mrnewtothis on 2012-12-31
> **bogan said:**
> Hi!,** mrnewtothis,**

Great! Another magical cure!

Select: 'Mark Thread as Solved' in the drop-down menu of 'Thread Tools', at the top of the Thread display.

Only you, as the 'OP', or a Moderator, can do it.

Chao!, bogan.

thanks for that.

---

