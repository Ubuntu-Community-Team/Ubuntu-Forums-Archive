---
title: "Ubuntu won't power off at shutdown."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by foreverlastd on 2008-07-29
Okay, I'm in the process of ditching Windows and I'm SO close to getting Ubuntu to behave correctly. My only obstacle now is to get it so I can shut it down!

So the situation is that whenever I attempt to shut down through the log off window or even go into hibernation it will go to the Ubuntu "loader bar" and when it finishes...nothing.

I've done some searching through the forums and tried the following:

I've added the acpi=force to the kernel, added noapic nolapic, added acpi=off apm=power_off, but nothing. I even added apm power_off=1 to the modules but same result. 

This is from my grub menu.lst hoping that somebody can spot an error here.


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9a3a7169-e3a2-4e43-a5fd-ec0dad5e29c2 ro quiet splash acpi=force noapic nolapic
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
acpi=off apm=power_off


If anybody can help or needs more information on my system (which is custom built, so part information) or anything that can help please let me know.


Thanks in advance,

-Mike

---

### Post by tuxxy on 2008-07-29
Try shutting down from terminal;

```
sudo shutdown -h now
```

---

### Post by ibuclaw on 2008-07-29
Press **Alt+Ctrl+F1** and make a note of the laste couple of lines of output on the screen.

Then **Alt+Ctrl+F8** and do the same again, then cite the output out in your next post.

Regards
Iain

---

### Post by foreverlastd on 2008-07-29
> **tinivole said:**
> Press **Alt+Ctrl+F1** and make a note of the laste couple of lines of output on the screen.

Then **Alt+Ctrl+F8** and do the same again, then cite the output out in your next post.

Regards
Iain

I attempted to do the command sequence at the shutdown process but the loader bar still remains (assuming the shutdown freezes).

I did the "sudo shutdown -h now" at command and same result.

I took pictures (SEE ATTACHED) of the shutdown (if it helps).

---

### Post by phidia on 2008-07-29
It looks like this is a [reported bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/234578").

---

### Post by foreverlastd on 2008-07-29
> **phidia said:**
> It looks like this is a [reported bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/234578").

Is there no known solution as of yet? Should I subscribe to that bug posting and wait it out?

---

### Post by kool_kat_os on 2008-07-29
i guess

---

### Post by foreverlastd on 2008-07-29
Okay, well thanks for the help anyways people.

-Mike

---

### Post by phidia on 2008-07-29
> **foreverlastd said:**
> Is there no known solution as of yet? Should I subscribe to that bug posting and wait it out?

You can do that-it can't hurt to add your input.
You can also try Gutsy in the meantime.

---

### Post by kool_kat_os on 2008-07-29
hmm....just goes to say....there is no perfect OS :)

---

### Post by cariboo on 2008-07-29
I get the same error at shutdown in intrepid alpha3, but is does shutdown after a bit.

Jim

---

### Post by unutbu on 2008-07-29
You might be able to get rid of the Network Manager messages before shutdown by doing this:
[http://ubuntuforums.org/showpost.php?p=5322302&postcount=9](http://ubuntuforums.org/showpost.php?p=5322302&postcount=9)

but I doubt it will improve the shutdown situation.

---

