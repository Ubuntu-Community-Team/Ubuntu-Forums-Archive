---
title: "Lots of problems"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Brennagan on 2008-09-22
My goal is to eventually install Ubuntu on an external hard drive. Ive done a lot of stuff so far with some advice from other board members.

First off some information. My internal hard drive has vista installed. My external hard drive is 80 gbs and completely empty.

Right now i continually get error 17 whenever i try to boot up without the external hard drive in so how can i fix that. And if I do have it plugged in and select vista i get another menu that shows windows vista and 2 ubuntus that dont work so how can i fix that?

Thanks in advance for all the help

---

### Post by Brennagan on 2008-09-22
I installed ubuntu on my external hard drive and everything is fine except when i actually try to boot linux but making it first in priority it shows the menu with safe mode and such but any of them i select i get a grub error 17. How do i fix this? Im kind of a noob at this so the more detailed the better thanks in advance.

---

### Post by overdrank on 2008-09-22
Hi and please do not make multiple threads on the same issues. I have given you all the info I had on the issue in your previous thread on installation. I have moved your thread to ABT Absolute Beginner Talk. Good luck! :)

---

### Post by willca on 2008-09-23
I just wonder, when you installed Ubuntu onto your external drive...where did you tell it to install the bootloader to? root or mbr?

From experience, I would rather use Grub than use Windows own bootloader. So basically I would have installed it on the 1st drives MBR if given a choice.

---

### Post by kansasnoob on 2008-09-23
> **Brennagan said:**
> My goal is to eventually install Ubuntu on an external hard drive. Ive done a lot of stuff so far with some advice from other board members.

First off some information. My internal hard drive has vista installed. My external hard drive is 80 gbs and completely empty.

Right now i continually get error 17 whenever i try to boot up without the external hard drive in so how can i fix that. And if I do have it plugged in and select vista i get another menu that shows windows vista and 2 ubuntus that dont work so how can i fix that?

Thanks in advance for all the help

Well first, if you're hardware savvy, you should have done this:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/#more-372)

If you're not hardware savvy you should have someone else do it, but we're past that.

Now you need to restore Vista's bootloader. Make sure your external drive is disconnected before doing this:

If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

or here:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

You want to "fix boot" and "fix mbr"!

Then we'll have to see if Ubuntu boots upon restarting with the external drive plugged in.

---

