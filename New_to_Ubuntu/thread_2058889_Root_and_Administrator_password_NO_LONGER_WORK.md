---
title: "Root and Administrator password NO LONGER WORK"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by RockOut on 2012-09-16
My husband called tech support for something on his computer. The tech support guy had NO idea what he was doing, and told my husband to "disable the user password" and reboot.

So, my husband goes to  Administration>Users&Groups, finds his user name -- the only user on the machine -- (this is on his laptop, so user/root are supposed to be the same thing), and Disables his password.

Now he cannot install ANYTHING. He can't get updates, it's a huge problem.

How can we change it back? He's overseas in Brazil at the moment and very freaked out by this.

(our household is now at 100% Linux use).and Skyping me for tech support. 

We're running Ubuntu 12 on an Acer laptop.

---

### Post by steeldriver on 2012-09-16
you can reset the password from the recovery console:-

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by RockOut on 2012-09-16
THANK YOU! This is definitely going to come in handy.

HOWEVER, When he reboots his laptop, then hits SHIFT, he says nothing happens -- the computer boots into Ubuntu normally.

When he boots and hits ESC, he's taken straight into the BIOS menu.

Can we access the Ubuntu boot menu from BIOS? Any help is much appreciated.


We also have an installation of Ubuntu (same flavor) on a USB stick. Perhaps this could come in handy?

---

### Post by deadflowr on 2012-09-16
Tell him to try to rapidly tap the shift key after the bios and before Ubuntu's boot screen. Sometimes a single click won't work, because it needs to be hit at a certain time during the loading period.
Hopefully that should work.

---

### Post by gnometorule on 2012-09-16
I haven't used it, but came recently across this (free) recovery disk which also mentions it has a feature to use it to reset your Linux passwords, if the other suggestions don't work. You would need to burn it on another machine, then boot from the optical drive (go to boot order in the bios, or in the special boot order option at startup - if this makes no sense, google 'change boot order').

Rescatux
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by NikTh on 2012-09-17
> **RockOut said:**
> 
HOWEVER, When he reboots his laptop, **then hits SHIFT,** he says nothing happens -- the computer boots into Ubuntu normally.

Hi , 

he must _hold down_ SHIFT until grub menu loaded. Not just hit it. 

Thanks

---

