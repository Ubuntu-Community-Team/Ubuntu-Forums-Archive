---
title: "Installing Ubuntu with 2 Internal HDDs"
date: 2012-08-18
forum: New to Ubuntu
---

### Post by boberts32 on 2012-08-18
Hey Everyone,

I'm a relative noob here. I have been using Ubuntu and it's variants for a couple years now, and have really enjoyed it compared to the days of Windows. Anyway, I have an interesting question/predicament. 

This afternoon I received a 2TB internal HD and installed it alongside my other internal HD that has Xubuntu installed on it. Formatting the drive was a breeze, but since I have installed the second HD I need to enter the boot menu (F12) upon restarting the computer to tell the computer which HD to boot from. If I don't hit F12, the screen goes black and Xubuntu doesn't load. My first question is, what did I do wrong? Can it be corrected? 

Lastly, if I decide that I want to uninstall Xubuntu and go back to Ubuntu do I need to clear both HDs? I know that whatever HD I install to the drive will need to be cleared, but does the OS need to be installed on both HDs? That wouldn't make sense, but then again I am a relative beginner. 

I know those are two different scenarios. I guess if I could do the second option without losing data that would be ideal. Any input would be greatly appreciated.

---

### Post by oldfred on 2012-08-18
Welcome to the forums.

Which drive have you set in BIOS to boot from? And does it have a grub2 boot loader in the MBR of that drive?

May be best to post the link to the BootInfo report that this creates, so we can see what is where:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Dr. Nick on 2012-08-18
You will not have to erase both drives to install a different version. I would look in the BIOS and make sure that the hard drive with Grub on it has a higher boot priority then your new hard drive.

---

### Post by boberts32 on 2012-08-19
Thanks for the responses. I installed Boot Repair and ran a summary, which gave me this link:

[http://paste.ubuntu.com/1155659/](http://paste.ubuntu.com/1155659/)

I should note that I have two usb external HDs connected as well. Thanks for any help you can offer.

---

### Post by oldfred on 2012-08-19
It looks like you plugged your new 2TB drive into a lower port on the motherboard and it became sda.

You should just go into BIOS and set BIOS to boot from the 320GB drive by default.

---

### Post by boberts32 on 2012-08-19
> **oldfred said:**
> It looks like you plugged your new 2TB drive into a lower port on the motherboard and it became sda.

You should just go into BIOS and set BIOS to boot from the 320GB drive by default.

Was this caused because I crossed the SATA cables that connect to the motherboard when I installed the new HD? Dumb question, but how do I access the BIOS and set it to boot from the 320GB?

---

### Post by oldfred on 2012-08-19
Usually you get a quick BIOS menu and it will flash by saying to get into BIOS press some key, often del or one of the f keys. Also most have a one time boot key that also does selection but just for one boot, mine is f12, some again that varies by vendor.

You should have manual from motherboard/computer vendor or can get one on line if not.

Also once in BIOS you have to find the choice. Sometimes it is part of device as a sub menu and sometimes just another entry.

---

### Post by boberts32 on 2012-08-19
Ok great. Between entering the BIOS and using Boot Repair the issue seems to have solved itself. Thanks for the help.

---

### Post by oldfred on 2012-08-19
Glad that worked. :)

---

