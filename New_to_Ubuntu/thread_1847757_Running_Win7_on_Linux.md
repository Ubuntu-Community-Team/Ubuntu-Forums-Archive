---
title: "Running Win7 on Linux"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by cheatos on 2011-09-21
Hi,

I want (much more of need) to install iTunes, but don't want to spam my normal Win7 partition with this product, so I was looking for a Sandbox program which would emulate Win7 on Linux.
I've already found Virtualbox, but I've seen in one thread, that it is possible to trash the original Win7 partition if I use the Virtualbox to open up a Windows session in Linux.

Has anyone tried to do that and can help me about this?

Thanks

---

### Post by rcayea on 2011-09-21
I believe the program PlayOnLinux has an itunes version that works. I think it is itunes7. And, I have never heard of trashing your window partition in the manner that you mention. I think that was user error.

---

### Post by orange2k on 2011-09-21
Installing Windows in Virtual box can do no harm. It will just take some hard disk space on your Linux partition.

---

### Post by cheatos on 2011-09-21
ok, thanks for your info.
I'll try it then

---

### Post by haqking on 2011-09-21
> **cheatos said:**
> Hi,

I want (much more of need) to install iTunes, but don't want to spam my normal Win7 partition with this product, so I was looking for a Sandbox program which would emulate Win7 on Linux.
I've already found Virtualbox, but I've seen in one thread, that it is possible to trash the original Win7 partition if I use the Virtualbox to open up a Windows session in Linux.

Has anyone tried to do that and can help me about this?

Thanks

Windows in a VM runs fine, i think the trashing you are referring to is when people try to mount an existing Windows partition into a VM and run it.

However a fresh install into Virtualbox is fairly straight forward and satisfies your needs.

cheers

---

### Post by wildmanne39 on 2011-09-21
+1 haqking is exactly correct again.

---

### Post by cheatos on 2011-09-21
Hi,

I've tried it and it works really good.
What I wanted to do next is connect my iPod to the Windows-Computer but the system wasn't able to get the right drivers, what can i do with that problem?
Windows even searched the net and didn't find anything.

---

### Post by wildmanne39 on 2011-09-21
Hi, I am not sure, I have not used windows in years, I do have it in virtualbox but I rarely boot it, and I have never used an Ipod.

The question is how did you install it in your normal windows? it should be the same. 

Did you install guest additions and the extension pack for virtualbox from there website?

Guest additions you must have to use any usb device in virtualbox.
Thank you

---

### Post by haqking on 2011-09-21
> **wildmanne39 said:**
> Hi, I am not sure, I have not used windows in years, I do have it in virtualbox but I rarely boot it, and I have never used an Ipod.

The question is how did you install it in your normal windows? it should be the same. 

Did you install guest additions and the extension pack for virtualbox from there website?

Guest additions you must have to use any usb device in virtualbox.
Thank you

+1

Make sure you download the extension pack on the same download page as virtualbox

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following:

```
sudo usermod -a -G vboxusers username
``` 

Then  you are set to go.

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions

Both the additions and the extension pack and being in the vboxusersgroup should solve any USB related issues, then plug in your Ipod and choose it from the devices menu in your VM to mount it

Have fun

Regards

haqking

---

### Post by cheatos on 2011-09-21
Okay, I have one everything wrong then, I suppose :(
Do I have to reinstall Windows or the Virtualbox if I have not installed the Additions yet, or can I add them now?
The terminal command I haven't executed as well, I'll try again ;)

---

### Post by wildmanne39 on 2011-09-21
Hi, you just add them go to the link that was given in the previous post, it has been my experience with the newer releases of virtualbox that it has added me to the user group automatically that is why I did not mention it.
Thank you

---

### Post by haqking on 2011-09-21
> **wildmanne39 said:**
> Hi, you just add them go to the link that was given in the previous post, it has been my experience with the newer releases of virtualbox that it has added me to the user group automatically that is why I did not mention it.
Thank you

yeah that should be the case, if the OP experiences USB issues it is a good thing to check that they are a member in that group though.

Probably not needed.

@OP once your VM is up and running then from the devices menu choose install vboxadditions, it is detailed in the link to the manual i posted.

The extension pack can be added also preferably without any VM running.  You dont need to redo anything

---

### Post by cheatos on 2011-09-22
I have done that, but still it won't find a USB-Stick I plug into my USB-Port, Linux always finds the drive but I cannot choose the drive in the menu on the bottom right corner, where all external devices are listed.
Is there a specific part where I have to mount the device to the Windows patition, or what am I doing wrong?
I have also executed the terminal command given above, but no change happened...

---

### Post by technosysind on 2011-09-22
Check your USB Port? Is the hardware working fine??

---

### Post by haqking on 2011-09-22
> **cheatos said:**
> I have done that, but still it won't find a USB-Stick I plug into my USB-Port, Linux always finds the drive but I cannot choose the drive in the menu on the bottom right corner, where all external devices are listed.
Is there a specific part where I have to mount the device to the Windows patition, or what am I doing wrong?
I have also executed the terminal command given above, but no change happened...

If the device is being seen in Linux and not available in the VM, right click on the device in Linux and choose safely remove drive, it may appear on the VM menu then, i have had that before though now common but it may work.

---

### Post by wildmanne39 on 2011-09-22
Hi, I see haqking beat me to it again, but I have to sleep sometime.

Here are 2 screenshots to look at, and I suggest you read the documentation again at virtualbox so you get the most out of using it.

You need to add an empty filter as shown in the screenshot, and in windows click on the little icon I the other screenshot,and do what haqking recommended sometimes it is needed also.
Thank you

---

### Post by wildmanne39 on 2011-09-22
My screenshot got lost here they are I hope.

---

### Post by cheatos on 2011-09-22
OK, thanks for your advice, after a few tries it worked, although I don't really know why it worked when I removed the Drive the 3rd time with Linux, but the two times before it didn't...

I suppose that the Virtualbox needed a reboot after adding myself to the Guestuser directory, thereafter all the external Drives have been shown by default in Virtualbox.

Thank you very much, I'll mark this as solved.

---

### Post by haqking on 2011-09-22
> **cheatos said:**
> OK, thanks for your advice, after a few tries it worked, although I don't really know why it worked when I removed the Drive the 3rd time with Linux, but the two times before it didn't...

I suppose that the Virtualbox needed a reboot after adding myself to the Guestuser directory, thereafter all the external Drives have been shown by default in Virtualbox.

Thank you very much, I'll mark this as solved.

cool, glad we could help and glad you got it sorted.

cheers

---

### Post by wildmanne39 on 2011-09-22
Hi, I am glad you got it working, enjoy ubuntu and the community.

---

### Post by cheatos on 2011-09-22
thanks to you two, I really enjoy the support its pretty awesome how fast questions get answered here on the forums.

---

### Post by wildmanne39 on 2011-09-22
Always happy to help and I try to be quick in my responses but sometimes things get in the way.

---

### Post by haqking on 2011-09-22
> **cheatos said:**
> thanks to you two, I really enjoy the support its pretty awesome how fast questions get answered here on the forums.

you are very welcome.

The spirit of Ubuntu is we are who we are thanks to who we all are ;-)

It is a great community, enjoy.

cheers

---

### Post by technosysind on 2011-09-22
Mark this thread as Solved (thread tools)

---

### Post by cheatos on 2011-09-23
> Mark this thread as Solved (thread tools)     already have done that

---

