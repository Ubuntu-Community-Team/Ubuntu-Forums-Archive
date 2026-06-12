---
title: "Is it possible to use &quot;pre-boot authentication&quot; on GRUB?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Jabbadahut on 2008-05-28
I am hoping someone here can answer a question I have about encryption.

Truecrypt now allows users to encrypt the operating system (Windows XP, Vista, Server 2003 & 2008 ) using its own bootloader.  From what I read on their forum and documentation, it will overwrite GRUB, thus Ubuntu will not boot from the hard disk.  There are ways of getting around this, but they sound a bit complicated to me, & I'd probably end up with a computer that does not boot.

I could also encrypt Ubuntu, but from what I read here in the forum, I need to uninstall the desktop version of Ubuntu (currently using the 8.04 LTS 64-bit), download & burn the alternative version, and chose to encrypt the OS from the install option.  I don't wish to do this, either.

Then I thought, *"What if I used some kind of tool that would prompt me to put in a password then load the bootloader (in this case GRUB)?  This way, the computer will not boot without the proper password, otherwise, it boots normally."*

Can this be done?

---

### Post by Dr Small on 2008-05-28
Set a BIOS user password. The system will not boot without first entering the password.

---

### Post by Golem XIV on 2008-05-28
First you should 
```
sudo apt-get install startupmanager
```
Now go to System -> Administration -> StartUp Manager
Go to Security tab, select what you want to password protect (the bootloader, rescue mode or old boot options), enter the password and close.

---

### Post by Jabbadahut on 2008-05-28
Thank you for your suggestions, guys. :)

Dr. Small, A BIOS password is good to have to stop the typical snooper, but let's say an attacker was knowledgeable enough to bypass it by typing in the backdoor password, or resetting it by popping out the CMOS battery for example?  The key to encryption, IMO, is to prevent unauthorized access.

Golem, I tried your suggestion, and all seemed to go well, but after booting, I didn't get any screen or prompt by the system to put in a password.  It just loaded GRUB as before.  Is this how it works, did I miss something in the startup manager's configuration?  I chose all 3 options in the advanced tab, (bootloader, rescue mode, & old boot options).

I have also heard of using a device, such a USB drive stick (for lack of a better term) for example, that connects to the PC, making booting without it almost impossible.

 - Jabba

---

### Post by Oldsoldier2003 on 2008-05-28
> **Jabbadahut said:**
> Thank you for your suggestions, guys. :)

Dr. Small, A BIOS password is good to have to stop the typical snooper, but let's say an attacker was knowledgeable enough to bypass it by typing in the backdoor password, or resetting it by popping out the CMOS battery for example?  The key to encryption, IMO, is to prevent unauthorized access.

Golem, I tried your suggestion, and all seemed to go well, but after booting, I didn't get any screen or prompt by the system to put in a password.  It just loaded GRUB as before.  Is this how it works, did I miss something in the startup manager's configuration?  I chose all 3 options in the advanced tab, (bootloader, rescue mode, & old boot options).
[I]
[COLOR="Red"]I have also heard of using a device, such a USB drive stick (for lack of a better term) for example, that connects to the PC, making booting without it almost impossible[/COLOR].[/I]

 - Jabba

Honestly, passwording grub is even easier to bypass than the bios password. If you assume physical access to the machine then you pretty much have encryption as your only useful security measure.


*[COLOR="Red"]that doesn't stop someone from using a live cd or their own bootable usb to boot the system[/COLOR]*

---

### Post by Jabbadahut on 2008-05-29
Yeah, I forgot about booting with the Live CD.  Well, things are working fine for now, so when the next time comes to reinstall XP & Ubuntu, I'll have to remember to install GRUB somewhere else other than the MBR, so that Truecrypt won't overwrite it with its own bootloader when I encrypt the Windows partition.

 - LL

---

### Post by hyper_ch on 2008-05-29
> **Jabbadahut said:**
> I could also encrypt Ubuntu, but from what I read here in the forum, I need to uninstall the desktop version of Ubuntu (currently using the 8.04 LTS 64-bit), download & burn the alternative version, and chose to encrypt the OS from the install option.  I don't wish to do this, either.

You can encrypt ubuntu in it's current state... it's just a lot of manual work... it's way simpler to just backup all your data, install an encrypted ubuntu from alterntae and put the data back on.

---

### Post by Jabbadahut on 2008-05-29
> **hyper_ch said:**
> You can encrypt ubuntu in it's current state... it's just a lot of manual work... it's way simpler to just backup all your data, install an encrypted ubuntu from alterntae and put the data back on.

I am a firm believer in the 'KISS principle.' ;)

 - Jabba

---

### Post by Major Crash on 2008-05-29
You can actually move grub from where it was originally installed to a different partition, and then have your windows partition encrypted with Truecrypt.

This [thread]("http://ubuntuforums.org/showthread.php?t=689579&highlight=combine+grub+truecrypt") talks about it, while this [post]("http://ubuntuforums.org/showpost.php?p=4287308&postcount=9") deals with moving grub specifically.

This way you have encrypted windows, but you can hit the ESC key to access GRUB and start Ubuntu.

---

