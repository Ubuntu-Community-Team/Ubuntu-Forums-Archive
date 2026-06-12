---
title: "How to get to &quot;boot menu screen&quot; for ASUS Eee PC 1015 Netbook? (to install Ubuntu)"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by swarup on 2011-10-17
Just bought a ASUS Eee PC 1015 Netbook. Here are the specs:

ASUS Eee PC 1015PEB-BK603 Refurbished Netbook - Intel Atom N450 1.66GHz, 1GB DDR2, 160GB HDD, 6-Cell, 10.1" SVGA, Windows 7 Starter, Black.

I've downloaded Ubuntu 11.10 and made a bootable USB pendrive using unetbootin. 

I thought that by hitting F12 or F1 at startup, I should get a boot menu. But as soon as I hit the power button, it opens a screen called "ASUS Express Gate Cloud".

My hope is to be able to get to a boot menu, boot to the pendrive, and have Ubuntu set up a dual boot with Winoows 7 Starter & Ubuntu 11.10.

---

### Post by cavh on 2011-10-17
I haven't got an Asus to test - but does it get to the BIOS if you hit the Del key when starting? If that doesn't work,suggest searching the Asus website for the product manual if nobody else on this forum knows the answer offhand.

---

### Post by swarup on 2011-10-17
I tried the DEL key just now-- that doesn't get to the bios/boot menu either. The same ASUS Express Cloud screen comes.

---

### Post by mcduck on 2011-10-17
Every Asus laptop I've used has opened the boot device menu with the Esc key.

---

### Post by swarup on 2011-10-17
> **mcduck said:**
> Every Asus laptop I've used has opened the boot device menu with the Esc key.

Just tried the Esc key-- that didn't work either. 

This Express Cloud screen opens literally the moment you hit the power key, as a sort of mini OS where you can go on-line without booting to the full OS. On the Express Cloud screen there is a button, clicking of which boots the computer to Winders 7 Starter.

---

### Post by mcduck on 2011-10-17
I tried searching Google for the correct key, and according to every web site I found the keys on Eee PC 1015 are F2 for BIOS and Esc for boot device selection.

Perhaps you could try holding down the key while powering the device? Or the traditional trick of repeatedly tapping the key immediately when you turn on the power?

---

### Post by swarup on 2011-10-17
I tried both holding down and tapping, with ESC and with F2, and neither worked. Then I thought-- perhaps these functions are meant to work AFTER the Express Cloud utility appears, when one selects to go from there to the OS. So I tried pressing ESC there, and found that it makes the screen flash to something that looks like a DOS sort of screen, but as soon as I let go of the ESC button, it boots right up into Win 7 Starter. 

I tried going to the ASUS website in search of the manual, but looked throughout the website including the support section, and could not find where the manuals are located...

---

### Post by roger_1960 on 2011-10-17
Hi

Let it boot into win7 starter.

There should be an enable/disable button for express cloud OS on the desktop.  Select disable.  Then the ESC key should give you a boot option screen on the next boot.

(The Express Cloud OS is in fact a linux OS but no use for anything except browsing)

I have installed 11.10 as a dual boot with win7 on my EeePC 1011PX and it all works fine.

Manuals are here:

[http://support.asus.com/Download.aspx?SLanguage=en&m=Eee+PC+1015PE&p=20&s=1](http://support.asus.com/Download.aspx?SLanguage=en&m=Eee+PC+1015PE&p=20&s=1)

Roger

---

### Post by swarup on 2011-10-17
Roger, sounds great. Thanks! I can't check it just now, but sounds like you've given the solution.

And if you are French-born, your English is amazing. :)

---

### Post by roger_1960 on 2011-10-17
Hi again

Hopefully the "widget" for enable/disable" is still there. I found I had to do multiple presses on ESC for boot option (and F2 for BIOS) while booting.  My Eeepc had a largely empty "d:" partition which I deleted to use for Ubuntu.  I left the Asus cloud partition and now I have the choice of 3 (but only win7 and Ocelot in the grub boot option)  My English is OK because I moved to France 10 years ago!

---

### Post by swarup on 2011-10-17
I see-- sounds very good. When you say "only win7 and Ocelot in the grub boot option", is that because the cloud OS boots up automatically as a "pre-OS" for win7 when you select win7 in grub?

Yes, it makes sense that you're from elsewhere, England I suppose. Nobody in France writes English like that... :p

add: I have looked on the desktop, and do not find any option there for disabling cloud. I also looked in all the locations I could think of in the OS there for such an option, but did not find it. If there was such an option on your desktop, then even if it is not on my desktop, it should be available somewhere shouldn't it? If you are familiar with Win7, perhaps you may have some idea where I should look for that. Seems like this is a must if I want be able to get to the boot menu.

---

### Post by restless on 2011-10-19
Hey, interesting topic.
I've been trying for the last few hours to install ubuntu on the same netbook, but without success. the problem for me is also that i can't get in the bios to change the boot order (i tried all the keys you suggested as well). infact i managed to get into it once, and managed to change the boot order to 'other devices' if i remember correctly, but then i just can't get it to boot from the usb key, where the ubuntu iso is.

problem is also that i don't have any windows installed, and i don't really want it anyway.

any suggestions?

thank you
lor

---

### Post by swarup on 2011-10-19
I got mine installed now, and it works great! To get into the bios, just hit the F2 key at startup, and that should take you right in. Also, I found that on save and exit from bios if I then hit the "ESC" key, it gives me the boot menu. And the USB stick showed up there. When I selected it, it installed 11.10 perfectly. 

[Here]("http://ubuntuforums.org/showthread.php?t=1864795") is another thread I had opened on the topic, for more info.

And [here]("http://askubuntu.com/questions/18763/install-10-10-netbook-edition-on-eee-pc-1015-using-a-usb-hdd") is a helpful link noting another's experience installing Ubuntu on the same netbook.

Good luck!

---

### Post by noctropolis on 2012-02-02
I know this is an old thread, and it says its solved, but I haven't seen anyone mention that before you're able to bring up the boot menu uing the ESC key, most (if not all) EeePC's from ASUS have a feature that speeds up the boot process called Boot Booster, and you need to disable that in the BIOS (Press F2)first. Once that's done, you should be able to get the Boot Menu displayed with the ESC key.

Hope that helps.

---

### Post by prajwalcshetty on 2012-07-02
> **swarup said:**
> I tried the DEL key just now-- that doesn't get to the bios/boot menu either. The same ASUS Express Cloud screen comes.


insert the  disk then restart the computer ,after that  hold the enter key:p:p:p

---

