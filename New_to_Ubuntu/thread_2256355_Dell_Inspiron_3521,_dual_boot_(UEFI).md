---
title: "Dell Inspiron 3521, dual boot (UEFI)"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by john335 on 2014-12-11
My parents are in their sixties and it seems no amount of basic internet training and antivirus software can keep their (Win 8) laptop in acceptable working order.  I am far from competent to clean the thing for them, and also live out of town.

I was thinking that Linux might be an answer.  Question: if I have near-zero experience with Linux, will I be able to install Lubuntu from a flash drive or cd and get things working enough to create a couple user accounts and get them online?  Is this doable for someone in my position?

Would appreciate any advice here.

---

### Post by nerdtron on 2014-12-11
Yes of course, as long as they know what a computer is and how to open a program like a web browser, they certainly can use it.

As for your case, I would suggest installing Xubuntu which is  more user friendly (and a little prettier than Lubuntu).
Just create a bootable USB using any tool you like unetbootin or Live Linux USB creator. Then boot from USB on the laptop and start the installation of the OS.

Any problem you encountered, you can ask here and people will help.

---

### Post by john335 on 2014-12-11
Thanks.  

So if they have a Win 8 machine now that I'll be installing this on, do I want the 64-bit?

---

### Post by nerdtron on 2014-12-11
Wooahh, careful... is it a newish laptop with UEFI and windows 8 secure boot? Installation may not be straight forward as you'd expect.
64bit is good, especially if it came already with a 64 bit OS.

---

### Post by john335 on 2014-12-11
I confess I have no idea how to answer your questions.  

Should I abandon this idea?  Or will it be simple to get a fresh laptop for this?

---

### Post by ajgreeny on 2014-12-11
If you , as your parent's Linux administrator, are totally new to Linux, which is what I think you're saying, you may find it more difficult that you believe if the Win8 is a new UEFI machine.

Star by reading and hopefully understanding everything said in [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

If you have more questions come back here aagin and we'll try to help.
How easily you will be able to help them with questions they may have after installation of an OS that you nothing about only you can know, but be prepared to try the OS yourself which will give you a lot more experience when they do, and they most certainly will have lots of questions.

Don't forget, Linux is not a straight alternative to Windows that works the same way; it is different, in my opinion much better, but if they have managed to break windows, and get viruses in that it does not bode too well for their ability to keep any OS completely clean.

Sorry if this sounds as if I'm pouring cold water on what you think is a good idea, but it sounds a bit like the poorly sighted leading the blind, if you see what I mean. (No pun intended).

Whatever you choose to do I wish you very good luck!

---

### Post by john335 on 2014-12-11
It is indeed the poorly sighted leading the blind.

Thank you for the link and advice.  I was hoping that their limited uses of the computer would mean they just wouldn't have that many questions, or that those quesitons would be less troubling than their constantly breaking windows.  

I will reappear after reading what you sent if and only if I decide to go through with this in some form.  Appreciate the help.

---

### Post by mörgæs on 2014-12-11
There are plenty of experienced UEFI people here (not myself, but others). Don't give up on the idea of a dual boot, just ask.

---

### Post by nerdtron on 2014-12-11
You can post here the model of the laptop, and experts on UEFI, usb booting, etc will reply. Just be patient and people will help you install ubuntu on that machine.

---

### Post by john335 on 2014-12-11
[FONT=arial]It's an [/FONT]Inspiron 3521, refurbished.  

Would happily take any advice about getting anything installed on that machine that will be even somewhat less susceptible to the kind of trouble they're having (I think malware, viruses).

---

### Post by ManyBeers on 2014-12-12
Before you do anything else fix their current Windows setup and only then think about dual-booting
(which i do) or running Ubuntu in a virtual machine. There is no good reason for that machine 
not to run perfectly. Millions of others do why can't theirs? Virus infection on modern Windows
systems are very rare.

---

### Post by sudodus on 2014-12-12
What are your parents doing with the computer? Would it be enough, if they can use a read-only system (booted from a fast USB drive)? They could save files in a data partition, they can install program packages temporarily, but at reboot the system will be fresh and free from virus and there should be no problems with conflicts between different programs and no destroyed settings.

In that case they can use either of Lubuntu and Xubuntu. You can make read-only systems with mkusb according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

See more general details in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mörgæs on 2014-12-12
Dells are often easy to work with. I suggest that you shrink Windows from a Windows boot and after that just try to install. Seems like noone here has considered that it could actually work in first attempt. 

Remember to choose 'something else' during install and to use a 64 bit ISO.

---

### Post by john335 on 2014-12-12
I'm thinking USB drive.  They don't need to (don't know how to, maybe) save anything.  Getting the machine to go online and do web-browsing and YouTube smoothly would be quite enough.  Doable, right?

---

### Post by sudodus on 2014-12-12
Yes :-)

Maybe you will have time during Christmas to teach them how to use a pendrive (that you have prepared and tested already).

---

