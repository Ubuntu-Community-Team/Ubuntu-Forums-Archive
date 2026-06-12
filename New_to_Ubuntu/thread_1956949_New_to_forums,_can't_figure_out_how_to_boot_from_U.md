---
title: "New to forums, can't figure out how to boot from USB."
date: 2012-04-11
forum: New to Ubuntu
---

### Post by denialofservice on 2012-04-11
Hey guys, first post. Sup everyone.

So, I have Ubuntu installed on my laptop but I'm trying to install Windows instead (blasphemy, I know, but my desktop will still be running Ubuntu). I used Unetbootin to write the .ISO to my USB flash drive, but when I restart my computer and make it boot from USB, it comes up with an options page that only has the option of "Default," that doesn't do anything when I select it. It also says "Automatic Boot 10... 9... 8..." etc. When it gets to 1, it just restarts at 10. 

Could someone help me? Thanks :)

Edit [SOLVED]:
Here's what I did.

I used the Windows ISO USB tool from Microsoft's website to put my Windows ISO on my USB in NTFS format. This was done from a Windows 7 computer.
Then I inserted my Ubuntu CD into my laptop and pressed "try Ubuntu," and used Gparted from there to format my drive to NTFS. 
I then booted from USB and viola. Hope this helps someone in the future.

---

### Post by PhantomTurtle on 2012-04-11
Welcome to the forums. Just so we're clear, you are trying to make a bootable Windows USB with Unetbootin? If so I don't think Unetbootin even supports Windows. I'm not going to ask you where you got the iso from, but your going to have to burn it to a DVD and do the install the normal. Additonally after you install Windows it will overwrite grub, so you either have to add Ubuntu to the Windows boot menu using easybcd or reinstall grub.

---

### Post by daslinkard on 2012-04-11
I think you would be better off to have Windows loaded first on your machine and then load Linux so you do not have any issues with the GRUB and the MBR.  It is my understanding that if you load Linux first and then you load Windows, once you install Windows it will overwrite the MBR only allowing Windows to load.

Someone please correct me here if I'm wrong.

---

### Post by denialofservice on 2012-04-12
Thanks for the replies guys. I'm trying to fully replace Ubuntu with Windows via a Windows 7 ISO file (don't worry, I have a genuine key, just not a disc). Phantom, Unetbootin has an option to load any ISO file to a USB drive, so why would it matter if it's a Windows ISO? Also, what are some programs other than Unetbootin I can use to write an ISO to a USB drive?

---

### Post by anewguy on 2012-04-12
> **denialofservice said:**
> Thanks for the replies guys. I'm trying to fully replace Ubuntu with Windows via a Windows 7 ISO file (don't worry, I have a genuine key, just not a disc). Phantom, Unetbootin has an option to load any ISO file to a USB drive, so why would it matter if it's a Windows ISO? Also, what are some programs other than Unetbootin I can use to write an ISO to a USB drive?

I think people were saying be wary of where you got the ISO.  The key just makes it legal - the ISO may still be full of viri, trojans, keyloggers, who knows what.

Dave

---

### Post by denialofservice on 2012-04-12
Oh. Well if that's the case, thanks, but the ISO is private & secure. :)

---

### Post by anejo on 2012-04-12
If you're wanting to write a Windoze iso (actually any iso) to a usb then use **Windows7-USB-DVD-tool**.
It's a free download at MS. Perfect for those situations!

---

### Post by mastablasta on 2012-04-12
> **denialofservice said:**
> Phantom, Unetbootin has an option to load any ISO file to a USB drive, so why would it matter if it's a Windows ISO? Also, what are some programs other than Unetbootin I can use to write an ISO to a USB drive?
 
it matters because to make it bootable you need to set a few options. such as bootflag and such. you might be able to do that manually, but hard to say.
 
but you could get away with, for example, some game iso on usb.

---

