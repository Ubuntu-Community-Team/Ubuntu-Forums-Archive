---
title: "[SOLVED] Anyone had any succes with Fujitsu Siemens Esprimo and Ubuntu?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by RobHK on 2008-05-19
Has anyone got Ubuntu working OK on Fujitsu Siemens Esprimo?

The best resolution I can get is 800x600 and the wireless adapter won't work. 

Seems a bit ironic as F-S claim to actively promote Linux:
[http://www.fujitsu-siemens.com/solutions/it_infrastructure_solutions/linux/](http://www.fujitsu-siemens.com/solutions/it_infrastructure_solutions/linux/)

---

### Post by lescarlin on 2008-05-20
I installed Ubuntu on my Esprimo with no problems.  However like you i had a bitch of a deal with the wireless networking adaptor.  The problem turned out to be that the manufacturers, Atheros have mislabelled their adaptor chipset, which results in Ubuntu loading the incorrect drivers.  Their chipset label claims the adaptor to be a R242x 802.11abg Adapter, whereas it is in fact an AR5007EG.  There is a solution for this in a thread i posted to... [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

Look for the solution supplied by Tom-X labelled "Atheros AR5007EG for hardy"

This worked perfectly first time

HTH
les

---

### Post by RobHK on 2008-05-20
> **lescarlin said:**
> I installed Ubuntu on my Esprimo with no problems.  However like you i had a bitch of a deal with the wireless networking adaptor.  The problem turned out to be that the manufacturers, Atheros have mislabelled their adaptor chipset, which results in Ubuntu loading the incorrect drivers.  Their chipset label claims the adaptor to be a R242x 802.11abg Adapter, whereas it is in fact an AR5007EG.  There is a solution for this in a thread i posted to... [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

Look for the solution supplied by Tom-X labelled "Atheros AR5007EG for hardy"

This worked perfectly first time

HTH
les

I'll check this out, though I won't have time today. 
What screen resolutions could you get?

---

### Post by lescarlin on 2008-05-20
> **RobHK said:**
> I'll check this out, though I won't have time today. 
What screen resolutions could you get?

Same as you.  Acc to the spec the display is 1280 x 800 WXGA, so this may well be a driver problem.  I havnt time now, as i'm still configuring and learning about Ubuntu.  Its something i'll get round to eventually, however you might try the Hardware & Laptops  or Multimedia & Video sections in the Main categories.

les

---

### Post by RobHK on 2008-05-21
> **lescarlin said:**
> Same as you.  Acc to the spec the display is 1280 x 800 WXGA, so this may well be a driver problem.  I havnt time now, as i'm still configuring and learning about Ubuntu.  Its something i'll get round to eventually, however you might try the Hardware & Laptops  or Multimedia & Video sections in the Main categories.

les
I tried alternative settings in Screens and Graphics and could manage proper definition for width but too deep, so that I had to scroll down (this was with a VirtualBox) to get the full screen.:( 

My Ubuntu normal installation (i.e. not VirtualBox) has now been replaced with Mint (Ubuntu with a different skin), and there I don't even see the Screens and Graphics item in the menu (though its there in the VirtualBox Mint installation).

Think I have to stick with Bill on this machine. I don't have any problems with Vista, but I like to support competition. :)

---

### Post by RobHK on 2008-05-22
> **lescarlin said:**
> Same as you.  Acc to the spec the display is 1280 x 800 WXGA, so this may well be a driver problem.  I havnt time now, as i'm still configuring and learning about Ubuntu.  Its something i'll get round to eventually, however you might try the Hardware & Laptops  or Multimedia & Video sections in the Main categories.

les

Haven't tried the wireless yet because of the resolution issue.

Firstly, Screens and Resolutions seems to have gone from the Administration tab in Hardy. But even in Gutsy I couldn't find one that worked. The odd thing though is that I have a copy of Mint 4, which is just Gutsy with a slightly different interface, on a VirtualBox under Vista and there I managed to find a 1280x800 res that worked (also gets wireless connection automatically, presumably leeching it from Windows). But on an installation of Mint direct to the hard drive I can't get that resolution, not even after all the updates have installed.:confused: Neither could I get it on Gutsy on VirtualBox.

Shame. I was looking forward to using Ubuntu and Mint on this laptop. I'll continue using them on the 5-year-old desktop (also Fujitsu-Siemens). The VirtualBox works but it stutters a bit. Maybe because there's not enough memory to support Vista and Ubuntu at the same time.

BTW I do recommend Mint. I find the layout more intuitive than Ubuntu.

---

### Post by RobHK on 2008-05-24
> **lescarlin said:**
> Same as you.  Acc to the spec the display is 1280 x 800 WXGA, so this may well be a driver problem.  I havnt time now, as i'm still configuring and learning about Ubuntu.  Its something i'll get round to eventually, however you might try the Hardware & Laptops  or Multimedia & Video sections in the Main categories.

les

Got the wireless working and have given you an official Thank you. One for Tom as well.

Have to see if we can get the screen right now. If I find anything I'll post it here. Could you do the same?  

Thanks

Rob

---

### Post by RobHK on 2008-05-25
> **RobHK said:**
> Got the wireless working and have given you an official Thank you. One for Tom as well.

Have to see if we can get the screen right now. If I find anything I'll post it here. Could you do the same?  

Thanks

Rob

Cracked it :)

[http://ubuntuforums.org/showthread.php?t=615094&highlight=Esprimo](http://ubuntuforums.org/showthread.php?t=615094&highlight=Esprimo)

---

