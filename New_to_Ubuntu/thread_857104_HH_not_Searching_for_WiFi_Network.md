---
title: "HH not Searching for WiFi Network"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by TopFan on 2008-07-12
My Dell laptop with HH has stopped searching for my home wifi signal.

When I switch on the computer I have a 'Double Monitor' icon with an orange warning triangle where I used to get the 4 bar signal strength icon.

If I click the double monitor icon I get a [two-item] menu with 'Wired Network' greyed out and 'Manual Configuration' which is selecteable, but of no use.

The computer used to just 'see' my wifi network and link to it. My wifi is working normally with my desktop, so no problems there.

Any ideas?

---

### Post by TopFan on 2008-07-12
I'm totally stumped on this. I've re-installed the whole Operating System and still have the same problem.

I can't even work out how to set up HH to join my wireless network. Can someone point me in the right direction for setting up a wireless network connection from scratch?

Any help much appreciated.

---

### Post by TSS on 2008-07-12
Reinstalling the whole operating system is quite extreme!  Let's see if we can figure this out though...

First, right click the double monitor icon and make sure "Enable Wireless is checked".  Also, go to System > Administration > Network and see if there is a Wireless connection listed.

If not, please post the output of:
```
lspci
```

---

### Post by TopFan on 2008-07-12
> **TSS said:**
> First, right click the double monitor icon and make sure "Enable Wireless is checked".
It is.

> Also, go to System > Administration > Network and see if there is a Wireless connection listed.
No networks listed.

> If not, please post the output of:
```
lspci
```
Yikes! The output is about 30 lines long. Normally I'd copy it, email it to my desktop and post it here. But since the laptop ain't connected to the net...

Which part are you interested in?

Cheers for your help. It is much appreciated.

---

### Post by TSS on 2008-07-12
We need to know what your Wireless card is.  Can you look it up in your laptopp specs?

---

### Post by TopFan on 2008-07-12
It's whatever comes with a bog standard Dell Inspirion 1525. I'll have a look through the lines of output (from above) ...

The only time the word 'Wireless' appears in the output is this:

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Does that help?

---

### Post by TSS on 2008-07-12
I would try what this particular post suggests first: [http://ubuntuforums.org/showpost.php?p=4448436&postcount=9](http://ubuntuforums.org/showpost.php?p=4448436&postcount=9)

This guide should get the job done: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I have a Broadcom card myself, and they can be a pain :-).  Good luck!

---

### Post by TopFan on 2008-07-13
No luck at all. The 'Restricted Drivers Manager' referred to in your link doesn't exist on my computer.

I'm sure it's a software problem because it was working fine then suddenly stopped. The hardware was all in place and working two days ago. Bizarre...

I'll take the machine to my local Ubuntu specialist later in the week. Then put it on Ebay with no reserve. :(

---

### Post by lisati on 2008-07-13
This *might* help: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

### Post by TopFan on 2008-07-21
Oh dear. How much of a plonker do I feel?

The nice chap form the computer shop has just phoned me to let me know that there is a little switch on the side of the computer that controls the wireless function.

Apparently the wirless doesn't work when the wireless switch is in the "O F F" mode. :lolflag:

Thank you all for your help. Do I get a prize for dumbest Ubuntu (ab)user?

---

