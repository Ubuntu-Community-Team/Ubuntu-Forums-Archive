---
title: "Good news and a new problem"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by elzorroviejo on 2008-06-28
The good news is that I did a clean re-install of Ubuntu 8.04 off a Linux Magazine dvd, and then immediately updated the Linux kernel to 2.6.24-19-generic. And now my RTL8187 wireless card is working like a champ using the native drivers which are either in the -19- kernel or the Ubuntu distro. Whichever, I am happy as a pig in...well, it's a G-rated forum. 

The problem is with getting the *hibernate* function to work. When I try to hibernate this laptop from the power button at the right of the top toolbar, I get the following error message: 

[CENTER]984.195520 i8042 aux 00:08: activation failed[/CENTER]

This is a [Gateway mX8738 laptop]("http://support.gateway.com/s/Mobile/2007/SonicC/1014556R/1014556Rsp2.shtml")that is otherwise doing great. 

Any help would be greatly appreciated.

---

### Post by jbrown96 on 2008-07-01
Does the same problem happen when you try to suspend? Could you atttach your /etc/default/acpi-support (I think this is the path. The /etc/default might not be right but the file name is.)? Some more info on your network hardware would be appreciated (lspci).

Just wondering why you are hibernating? There really isn't any purpose because it's simply a shutdown that saves the state of your session. There is a setting for Gnome to remember what is open, bypassing the need to hibernate at all.

---

### Post by DSL5 on 2008-08-06
Hey, I have just installed Ubuntu 8.04 to dual boot with my Windows XP Professional.

I am having the exact same Hibernation problem. I have recently expanded my swap partition to 1GB (it was half a gig before) because when I tried to hibernate, i got an error saying that I didn't have enough swap. Now that I fixed that problem, I get this one. Ugh....

My laptop is a Toshiba Satellite A105. I am running the -19 Kernal

---

### Post by strypey on 2008-08-13
Kia ora

I also have a Toshiba Satellite, running Hardy (upgraded from Feisty), and I am also having issues with hibernate and suspend. I was using hibernate because if I shut down, and did a cold boot, or when I tried to restart, I would get a black screen and have to hard shutdown, boot in safe mode, and run the command to fix the X server. Hibernate and suspend would work, but they made strange, loud noises when I reactivated, and gave me similar error messages:
'38.568700: i8042 aux activation failed'
'38.654576: i8042 kbd activation failed'

I tried installing the Powersaved package, which replaced APMD. It's not making funny noises anymore, but it's still giving me similar error messages on both suspend and hibernate, both while going down, and coming back up. I restarted after installing Powersaved and it didn't give me a black screen. Not sure that this will happen each time though as the black screen didn't happen *every* time with APMD.

Na
Strypey

---

### Post by roadrun777 on 2008-09-08
I know this may not be an option, but I haven't seen stable suspend/hibernate until kernel 2-6-27 on my gateway laptop. Which is in the latest Intrepid testing.

With the newer kernel I can finally resume from a suspend, where before I just got some errors about certain drivers not re-initializing.

The only issue I have now is that the longer you leave it in suspend mode the more likely it will not come back up. Having it suspended for more than 24 hours usually results in a hard lock upon resume. There are no error messages in the logs either, so I suspect it's some kind of timing problem. My laptop is a Gateway ML6720.

Btw, can you see any channels other than 1 to 11 ? I have a RTL8187b (0x8189) and with the windows drivers it sees all channels because the domain is set to Europe. The built in RTL8187.ko open source driver only allows you to use channels 1 through 11 no matter what domain.

Does anyone know how to force this driver to use another domain?

---

