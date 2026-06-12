---
title: "Not able to install Additional Drivers in 15.04"
date: 2015-05-03
forum: New to Ubuntu
---

### Post by sivakumar-sakam on 2015-05-03
Hi, 
I have installed **15.04** on  **Dell Inspiron-1464 **and want to enable wireless drivers, so tried to enabled it(through Software & Updates), when I clicked on Apply it showing '**Applying Changes**' not moving further as shown in Snapshot
Any idea what might be the issue?

Thanks in advanc[ATTACH=CONFIG]261736[/ATTACH]e.

---

### Post by dino99 on 2015-05-03
that is always what i get in such a case, its a bug but seems harmless as the driver is installed. I'm always closing that frozen progress-bar with no drama

---

### Post by sivakumar-sakam on 2015-05-03
Thanks for your reply, but in my case it didn't happened i.e after restart also it didn't work.
I ran this command > rfkill list all output is 
> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


seems to be there is something ..

I have downloaded manually **bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb **and tried to install it, but getting attached error 
[ATTACH=CONFIG]261742[/ATTACH]

---

### Post by cariboo on 2015-05-03
> **sivakumar-sakam said:**
> Thanks for your reply, but in my case it didn't happened i.e after restart also it didn't work.
I ran this command  output is 


seems to be there is something ..

I have downloaded manually **bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb **and tried to install it, but getting attached error 
[ATTACH=CONFIG]261742[/ATTACH]

You need to install a couple of other packages before you install the driver.

[LIST]
[*]Fakeroot
[*]dkms
[/LIST]

---

### Post by buzzingrobot on 2015-05-03
I've seen it take 10-15 minutes if the mirror it's downloading from is particularly slow at the time.

---

### Post by wildmanne39 on 2015-05-03
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by gaurav5 on 2015-11-02
Guys, Any update on this ?
I'm thinking to upgrade 15.04 from Windows 10, Please let me know in case there is an issue with Wireless drivers (that means Wi-Fi & Bluetooth, I guess ??)

---

