---
title: "Acer Aspire 5553: Internal keyboard does not work with Linux distros"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by rob84 on 2014-07-27
[COLOR=#000000][FONT=Verdana]I have an Acer Aspire 5553 running Windows 7[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I have tried all these:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Ubuntu 14.04 both 32 bit and 64 bit[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ubuntu 12.04.03[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Xubuntu 14.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]and Linux Mint 17 Cinammon[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]and unable to use my internal keyboard.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Only because Ubuntu 14.04 has onscreen keyboard could I continue the installation but I tried all the others on a pen drive.

[/FONT][/COLOR]When the installed 14.04 (0n dual boot) starts up it says  'disabling irq 18)

[COLOR=#000000][FONT=Verdana]I am not sure what to do next or abandon thoughts of Linux. My BIOS has no setting for keyboard. I cannot update drivers as this is only done via windows updates so already done.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have tried the setting the keyboard in Ubuntu to English UK which is what I want.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have tried the language support setting keyboard input to in Ubuntu to INBUS and then NONE and neither worked.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]It is pointless I think trying a USB keyboard because it is not practical for me to use with a laptop and neither is the onscreen keyboard.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I might add I succesfully installed first time Ubuntu on my older Acer laptop[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Any help appreciated.[/FONT][/COLOR]

---

### Post by kira-yamato-2008 on 2014-07-27
Have you tried running an update in Ubuntu it self? You might have a better time with another distro such as Fedora, ArchLinux, Knoppix, or a similar Non-Ubuntu Linux distro. You might also want to check out the Debian version of Linux Mint rather than Cinammon. Also you should check out the Repository of apps through the internal software installer you might find a utility that can recognize your keyboard. In fact if you have an Ubuntu version installed you should try that first.

---

### Post by rob84 on 2014-07-28
Thanks your advice.

I looked and tried some stuff in internal software installer but nothing was suitable or worked.

I looked at some of the non ubuntu based options but they all seem a bit daunting to a newcomer like me and I would love to have Ubuntu or Xubuntu as I have them working on my older laptop.

I did try 14.04.1 and using boot repair advanced options added  acpi=off     and when I booted back up was able to log in using the keyboard - but that is as far as I get and the screen just changes to all purple with no menus or icons.

Is there anything else I can try?

---

### Post by kira-yamato-2008 on 2014-07-28
Apparently updating your bios fixes the problem with this series of Laptops [as shown here]("http://ubuntuforums.org/showthread.php?t=1555029") Just be very careful about bios updating as it can backfire horribly. Your bios updates should be available through Acer's site, if not there, then from the site who made the Motherboard in the Laptop. Be aware that a bios update/flashing your bios has the potential to screw up horribly.

Also thank you for adding yet another reason to keep Acer on my black-list of computer makers.

---

### Post by rob84 on 2014-07-29
Thanks - I have read that about updating BIOS, I have seen the updated version on the Acer site but I am scared to update in case I screw it up.

As mentioned before my older Acer laptop - 3 years older than my current 3 years old one - loaded up Ubuntu like a dream.

---

### Post by kira-yamato-2008 on 2014-07-29
Well installing a new bios version isn't too difficult a process, just fallow the instructions. However if for whatever reason it fails you could easily brick the computer through no fault of your own. That's just how bios flashing is.

---

### Post by mörgæs on 2014-07-29
We have several positive indications that a new BIOS works. I wouldn't hesitate to try it.

It's fine to be cautions when dealing with BIOS updates but that should not lead to paralysis.

---

### Post by rob84 on 2014-07-30
Thanks for your advice, googling about BIOS updates everyone seems so cautious and says do not do unless absolutely necessary.  The updates are on the official Acer site and they give clear instructions so I wonder myself what could go wrong.

By the way I did try Linux Mint Debian yesterday but still no keyboard.

In all these distros I have tried none have ever asked what keyboard I have or attempted to detect it.

Maybe I try with a usb, maybe I explore the acpi=off again, or install within Windows, or attempt the BIOS - plenty of choices....

---

### Post by rob84 on 2014-07-30
quote

Maybe I try with a usb, maybe I explore the acpi=off again, or install within Windows, or attempt the BIOS - plenty of choices....[/QUOTE]

Sorry I meant  ...try with a usb keyboard,.....

---

### Post by kira-yamato-2008 on 2014-07-30
When they say use caution, it's for good reason, but only because of a relatively remote chance of the BIOS flash actually failing for whatever reason. I've actually done it a few times and never encountered a problem. So the question is Linux necessary for you? The other question is this: Is your laptop still under warranty? If yes then go ahead and use the official update to flash the BIOS if it does fail and kills the BIOS, it's an official update, so Acer should cover it if it fails. Possibly even if the Warranty is up, but you'd have to see their customer service about to confirm or disprove that.

Another consideration is weather or not you consider using Linux necessary, if you do, then go ahead and update the BIOS. It's actually a fairly common thing to do and most manufacturers recommend it rather heartily. Most people never have an issue with a BIOS update, failure isn't all that common. Ultimately it's up to youbut as mörgæs said, don't let the question of a BIOS update scare you in to indecision either way.

---

### Post by kurt18947 on 2014-07-30
I've done a number of BIOS updates, usually via Windows with no issues.  Do be sure that the machine is plugged in, don't try it on battery only.  You do not want any interruption part way through the process.  I don't know about Acer Aspire but some machines have a backup copy of the BIOS to recover in case of a failed upgrade.

---

### Post by rob84 on 2014-08-03
Thanks for all your help and advice.

I have just tried Ubuntu and Kubuntu on a virtual machine and they both work fine and obviously the keyboard works.  So I think I will go down this route rather than update my BIOS and carry on using a dual boot.

---

### Post by makki76 on 2015-01-29
Wow, I'm really astonished how broken things can be done (a keyboard not working??!!??)
I solved it with an USB one on an Acer I had to "repair" (Update Windows 0.7 to Ubuntu 14.04 :)
So, acer isn't on my blacklist anymore, it just went to the "no-go-never-ever"-list..

Michael

---

