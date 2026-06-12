---
title: "Ubuntu BD with Win7 - Won't recognise Ubuntu"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by GaryTheCat on 2012-11-27
Hello

I've installed ubuntu 12.10 on a new laptop to dual boot with Win7.

All went well, I ran a live usb to see if there were any hardware issues, there were none - so I installed 12.10 (successfully, no error messages).

Now when I boot the machine it goes straight to Win7.

It's an Asus X401A

I think the word I'm looking for is "HELP"

Many thanks

---

### Post by oldfred on 2012-11-27
Lets see what is where:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by dannyboy79 on 2012-11-27
nevermind, oldfred ninja'd me

---

### Post by Cavsfan on 2012-11-27
> **GaryTheCat said:**
> Hello

I've installed ubuntu 12.10 on a new laptop to dual boot with Win7.

All went well, I ran a live usb to see if there were any hardware issues, there were none - so I installed 12.10 (successfully, no error messages).

Now when I boot the machine it goes straight to Win7.

It's an Asus X401A

I think the word I'm looking for is "HELP"

Many thanks


This should help. I have done it before with success. Load a live cd click "Try Ubuntu" 
and go by these commands:

[[COLOR=blue]_http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/_[/COLOR]]("http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/")

You might want to write them down unless you can get to them from the live cd which you probably can.

I guess **oldfred** ninja'd me too! That was quick! :D

---

### Post by GaryTheCat on 2012-11-27
Boot-Info says: [http://paste.ubuntu.com/1392305/](http://paste.ubuntu.com/1392305/)

I can't have made that much of a mess, the machine's been out of the box for less than 2 hours .....

---

### Post by oldfred on 2012-11-27
In your other thread you seemed to want to avoid UEFI. Sorry you have Windows UEFI and installed Ubuntu in BIOS mode. Both have to be UEFI to work. :)

Boot-Repair can fix your install by un-installing the BIOS mode grub-pc and installing the UEFI mode grub-efi.

Grub also has a bug in its os-prober. So it still creates a BIOS mode chain load to Windows which does not work in UEFI. But again Boot-Repair will add a correct entry. 

Then in your UEFI menu you can set default to boot Ubuntu and from the grub menu boot either Ubuntu or Windows.

---

### Post by GaryTheCat on 2012-11-27
I finally decided to buy this machine (foolishly - as it now seems) to avoid UEFI by having something preinstalled with windows 7.

Is it just as simple as clicking the repair button and all should be OK?

Many thanks

G

---

### Post by GaryTheCat on 2012-11-27
I now have: [http://paste.ubuntu.com/1392423/](http://paste.ubuntu.com/1392423/)

---

### Post by GaryTheCat on 2012-11-27
People, you are brilliant - all sorted.

Thanks so much:guitar:

G

---

### Post by oldfred on 2012-11-27
Glad that worked. :)

Yann is putting us out of work. :) Everything is automated.

---

### Post by YannBuntu on 2012-11-27
> **oldfred said:**
> Yann is putting us out of work. :)

For common cases only, but unfortunately new problems appear everyday (eg SecureBoot), so don't worry we'll be busy forever ;)

---

