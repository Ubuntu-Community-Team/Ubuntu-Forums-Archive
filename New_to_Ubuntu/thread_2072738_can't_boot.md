---
title: "can't boot"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by tomyummmm on 2012-10-18
Hi people i really need help. Im a 14 year old noob so yea i screw things up a lot. Anyways,  my laptop is a Lenovo U260 with specs so bad i feel like puking, so i have had windows 7 home premium installed at first, then i installed Ubuntu alongside with the windows 7. Afterwards i installed Linux mint and Fedora, which i then wiped out fedora from a partition of 40 GB in my hard drive. Then the GRUB 2 started to conk up, i cant't boot to anything, it always comes to a "error unknown filesystem. Entering rescue mode... Grub rescue>" and now im stuck there forever. The worst part is, when my bios loads up the part where i could choose which device to boot from isn't there anymore, it just zooms past my bios lol. I really need help! Oh and linux mint was also wiped out, then ubuntu crahed and couldn't start up, so when i tried to restart it ended up like this. Thanks in advance

---

### Post by mörgæs on 2012-10-18
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tomyummmm on 2012-10-18
> **mörgæs said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

After reading it, i notice it still requires the computer to be able to use linux or be able to use a terminal to access it, but since i am not able to boot anything nor choose a media device to boot from, how would i go about doing so?

---

### Post by tomyummmm on 2012-10-18
Ummm i really need help! Somebody? Anybody? I have made the bootable repair usb, but my computer isnt able to select the device boot up order!

---

### Post by audiomick on 2012-10-18
> **tomyummmm said:**
> ...but since i am not able to boot anything nor choose a media device to boot from, how would i go about doing so?

Hmm, that is tough. Your best chance of getting help in your situation is that. Either the boot repair itself will fix it so that you can boot at least one OS, or the boot information summary will tell people here what state the machine is in and aid in providing suggestions to help you out.

When you boot up, do you see a  message on the screen that says something like "press F10 to enter setup"? Or one for a boot deivce menu?

edit: it is considered polite to wait a day or so before bumping your thread. Give people a chance to find your question. Remember, the people trying to help you here are all volunteers working in their free time, and there is generally not that much activity here at this time of day...

---

### Post by tomyummmm on 2012-10-18
> **audiomick said:**
> Hmm, that is tough. Your best chance of getting help in your situation is that. Either the boot repair itself will fix it so that you can boot at least one OS, or the boot information summary will tell people here what state the machine is in and aid in providing suggestions to help you out.

When you boot up, do you see a  message on the screen that says something like "press F10 to enter setup"? Or one for a boot deivce menu?

edit: it is considered polite to wait a day or so before bumping your thread. Give people a chance to find your question. Remember, the people trying to help you here are all volunteers working in their free time, and there is generally not that much activity here at this time of day...

Nope, my bios options are not available. :( would i have to send my laptop to a service center?
So sorry ><

---

### Post by malangaman on 2012-10-18
I would insert an Ubuntu Live Disk and thereby gain access to your HDD. You then can copy your documents to a thumb drive (or another such external device), edit Grub and/or re-install Ubuntu.

check:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by audiomick on 2012-10-18
@ malangaman: the OP has already confirmed that he can't boot from any medium, including CD or USB.

@ tomyummm: I think perhaps all is not quite lost. There are things you can do at a grub rescue prompt, i.e. where you are landing. Unfortunately I don't know how to do them. Hang in there for a bit. Maybe someone will come along who has a better idea. If no-one has answered by this time tomorrow, bump the thread again.

---

### Post by Redzky on 2012-10-18
> **tomyummmm said:**
> Hi people i really need help. Im a 14 year old noob so yea i screw things up a lot. Anyways,  my laptop is a Lenovo U260 with specs so bad i feel like puking, so i have had windows 7 home premium installed at first, then i installed Ubuntu alongside with the windows 7. Afterwards i installed Linux mint and Fedora, which i then wiped out fedora from a partition of 40 GB in my hard drive. Then the GRUB 2 started to conk up, i cant't boot to anything, it always comes to a "error unknown filesystem. Entering rescue mode... Grub rescue>" and now im stuck there forever. The worst part is, when my bios loads up the part where i could choose which device to boot from isn't there anymore, it just zooms past my bios lol. I really need help! Oh and linux mint was also wiped out, then ubuntu crahed and couldn't start up, so when i tried to restart it ended up like this. Thanks in advance

did you try pressing f8 right when it restarts, over and over til the bios appears? And also make sure the boot disks are squeaky clean.

---

### Post by AndyOpie150 on 2012-10-18
> **mörgæs said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
+1 ^
If your stuck in grub rescue it will work. I ended up having to use my neighbors computer to burn the .iso to a CD. Worked great.

If the first option doesn't work go to the advanced section and choose to install a generic MBR to sda.

---

### Post by audiomick on 2012-10-19
You might find something that could help here.

[https://help.ubuntu.com/community/Grub2/Troubleshooting#grub_rescue.3E]("https://help.ubuntu.com/community/Grub2/Troubleshooting#grub_rescue.3E")

---

### Post by tomyummmm on 2012-10-19
> **audiomick said:**
> You might find something that could help here.

[https://help.ubuntu.com/community/Grub2/Troubleshooting#grub_rescue.3E]("https://help.ubuntu.com/community/Grub2/Troubleshooting#grub_rescue.3E")

Hmmm... So to say that all i would need to do is have a bootable flash drive with ubuntu on it, put the grub 2 system files in the flash drive as well, set the root and prefix to my flash drive in the grub rescue command line, and hopefully boot from it?

---

### Post by tomyummmm on 2012-10-20
Im thinking about asking lenovo whether my warranty covers the operating system, i have tried for a whole 2 days but to no avail. I tried using a livecd of ubuntu 12.04 on flashdrive, i have tried using the grub rescue command prompts, setting the root and prefix and whatsoever, it just doesnt work.... Well thanks people, unless someone can help me here with similar experiences?

---

