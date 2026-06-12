---
title: "Laptop in suspend: later does it go in &quot;deeper sleep&quot; that could disturb NDISwrapper?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by swarup on 2008-06-06
For a year now I've been using NDISwrapper for my Netgear wg111v2 dongle with Ubuntu. With Feisty, once on-line I could not remove the dongle or go into suspend mode. If I tried to do so, it would freeze the computer. 

Now with Hardy, the problem is largely solved. In Hardy I am able to remove the dongle (first unchecking "enable wireless" in Network Manager) without the computer freezing, and am able to then go in suspend mode fine. And I can come out of suspend mode, plug in the dongle, recheck "enable wireless", and get right back on-line. This ability to get off-line, go in suspend mode, then come out of suspend later and get back on-line, is a wonderful improvement from Feisty which has literally changed my life! 

However, there is one caveat: it only works if I've been in suspend mode for around two hours or less. Which is all I need during the day. But at night when I myself go to sleep, then I keep it in suspend mode. In the morning when I awaken the laptop, it is fine until I plug in the Netgear dongle. This throws the computer into a state in which it works only very, very slowly and the cursor only moves with great halts and jerks. And the computer will not go online. If I remove the dongle, the computer will be again fine. 

But this is the problem, that after being in suspend mode for more than two hours or so, upon awakening the computer I cannot plug the dongle back in without having the computer go into a fit and become unable to get online. So my question is this: NDISwrapper works fine on awakening so long as the computer has been in suspend for less then two hours. But is there something that could change--perhaps regarding the "depth of sleep" in suspend mode-- after a certain amount of suspend time (perhaps 2 hours or so), which would then cause NDISwrapper to no longer function normally on the computer's awakening?

(I know the problem is related with NDISwrapper, because when after >2 hours of suspend I plug in the dongle and get the problem, if I then remove NDISwrapper (using "sudo modprobe -r ndiswrapper"), then the computer's fitfull activity ends and it works fine-- but of course will not go online because NDISwrapper has been removed. And if in that situation I then restore NDISwrapper (using "sudo modprobe ndiswrapper"), then the computer again goes into its state of slow and fitful activity.)

What happens to the computer during suspend modes of >2 hours that causes this dysfunctionality with NDISwrapper?

---

### Post by jbrown96 on 2008-06-07
Not sure I can help with the >2 hour issue. But you might want to force Ubuntu to unload the module. Even though network devices are supposed to automatically unload, I've had problems with them before. 
add ndiswrapper to this line in /etc/default/acpi-support

> MODULES=""

It should now be> MODULES="ndiswrapper"
 unless you have added other modules (they should be separated by spaces only).

Just something to try

---

### Post by swarup on 2008-06-07
I see-- so here the idea is that perhaps NDISwrapper is not getting unloaded properly by the power management scheme (acpi) when going into suspend mode, and so is unable to again function properly out of coming out of suspend? 

One related question here: my laptop I do not believe has acpi, because it is a 1999 machine, and acpi came out after 2002. According to my understanding, due to my laptop's age, its power management scheme would be APM, and not ACPI. Would this affect your instructions at all?

---

### Post by jbrown96 on 2008-06-08
I think that is precisely the problem. The all-mighty Wikipedia says that ACPI was released in '96, so it may or may not be on your computer. ACPI is implemented in the OS and APM in BIOS, so there must be something in the BIOS if APM is the system in charge. Check that out. I don't have any experience with APM. 
Again forcing the unloading of ndiswrapper won't hurt anything, so you might as well try. The most that would happen is that the module is unload "twice."

---

