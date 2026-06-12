---
title: "Load Ubuntu Server inside VMPlayer on Win 7 Errors"
date: 2015-01-07
forum: New to Ubuntu
---

### Post by wannbenixdude on 2015-01-07
A picture is worth a thousand words. [U]
[B]
My laptop .. the host .. [/B][/U]

-- removed base64 image --

[U][B]
The Virtual machine setup. [/B][/U]

-- removed base64 image --


_**The Ubuntu iso being used  the guest :**_

-- removed base64 image --

and 

-- removed base64 image --

I did run the Vmware compatibility check which reported, ofcourse, that the laptop was able to support a Ubuntu 64b version. 

Does anyone have any ideas ? 

Thanks alot Chris

---

### Post by wannbenixdude on 2015-01-07
TSCH ....guess we cant past direction into the post ...

---

### Post by bapoumba on 2015-01-07
> **wannbenixdude said:**
> TSCH ....guess we cant past direction into the post ...
Yes you can :)
Edit post > Go advanced > upload a pic and attach it as thumbnail (better than huge img in posts).

---

### Post by wannbenixdude on 2015-01-07
The host is a 

> OS :Win 7 SP1 64-bit
Proc : Intel Core i7 2.6ghz
Ram : 24G
 

I am trying to load Ubuntu-14.04-server-amd64.iso insided a VM created that has been assigned 15g of disk space and 4g of Ram. 

When I point towards the ISO, I receive 2 popups 

The first 
> Binary translation is incompatible with long mode on this platform. Long mode will be disabled in this virtual environment and applications requiring long mode will not function properly as a result. See [http://vmware.com/info?id=152](http://vmware.com/info?id=152) for more details.

The second which actually shows as an error with the typical white x in a red circle 
> This virtual machine is configured for 64-bit guest operating systems. However, 64-bit operation is not possible.

This host supports Intel VT-x, but Intel VT-x is disabled.

Intel VT-x might be disabled if it has been disabled in the BIOS/firmware settings or the host has not been power-cycled since changing this setting.

(1) Verify that the BIOS/firmware settings enable Intel VT-x and disable 'trusted execution.'

(2) Power-cycle the host if either of these BIOS/firmware settings have been changed.

(3) Power-cycle the host if you have not done so since installing VMware Player.

(4) Update the host's BIOS/firmware to the latest version.

For more detailed information, see [http://vmware.com/info?id=152](http://vmware.com/info?id=152).


I also ran the VMPlayer compatibility test which returned 
> 
"This host is capable of running a 64-bit guest operation system under this VMware product."

Im wondering if anyone else experienced this issue and arrived at a fix.  ... and solrry about the first post. 

Thanks Regards 
Wanna

---

### Post by sandyd on 2015-01-07
Side note:
If you click 'Manage Attachments', you can attach the images to your post -  don't drag them onto the post, it creates a massive wall of text :)

---

### Post by wannbenixdude on 2015-01-08
Yeah thanks I know that sandy not sure what Iwas thinking.  

And the resolution to the problem is a hardware setting. get into bios and enable virtualization.

Regards
Wanna

---

### Post by yancek on 2015-01-08
In post 4, you give four message suggestions to try to get it to work.  Are you saying you have done all and it still doesn't work?

> enable Intel VT-x and disable 'trusted execution
reboot the computer
possibly update firmware

---

