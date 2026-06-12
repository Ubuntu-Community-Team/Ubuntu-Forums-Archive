---
title: "Changing Default OS to boot first"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2011-09-11
I just finished reading the information found here:
[https://help.ubuntu.com/community/Grub2#File_Structure](https://help.ubuntu.com/community/Grub2#File_Structure)
twice and still don't understand what I am supposed to do so I can change the default boot in my dual boot system from Lubuntu to Ubuntu. Any help will be appreciated.

---

### Post by ubudog on 2011-09-11
For Grub, I recommend installing Grub Customizer.  

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
```
```
sudo apt-get update
```
```
sudo apt-get install grub-customizer
```

Hope that helps,
ubudog

---

### Post by Rex Bouwense on 2011-09-11
Thanks ubudog.  I installed and save and will now reboot to see if it works.

I rebooted and the default boot order was not saved even though I saved it.  Must I do something else?  The same thing happened when I used Startup Manager.

---

### Post by ubudog on 2011-09-11
Hmm, did you edit it like this?:
Grub Customizer > Preferences > "General" tab > default entry > Predefined: 

And then click the "Save" button?

---

### Post by Rex Bouwense on 2011-09-11
Not until you told me to do that, but it didn't make any difference.  The default boot is still Lubuntu even after I performed the edit that you told me and rebooted.

---

### Post by ubudog on 2011-09-11
Try this:
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)

So, an example command would be:
```
sudo grub-set-default 3
```

Assuming your Ubuntu install is third in the list.

Then, make sure to do:
```
sudo update-grub2
```

And reboot!  Hope that works.

---

### Post by Rex Bouwense on 2011-09-11
That didn't work either.  This is getting a wee bit frustrating, but if everything ran perfectly we wouldn't have anything to do.

---

### Post by ubudog on 2011-09-11
Yeah, this is strange.  Can you please post the output of:
```
sudo update-grub2
```

---

### Post by Quackers on 2011-09-11
Are you using 11-04? Last I heard Grub Customizer wasn't working with 11-04's grub version. Startup Manager neither.
You could do it the old way by editing /etc/default/grub and changing 
GRUB_DEFAULT=0
to
GRUB_DEFAULT=  ## the number of the item you want to be default in the present grub menu - but don't forget to subtract 1 from the menu item number as the first entry is entry 0 not 1
Then save the new file and run sudo update-grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by oscarivera9 on 2011-09-11
I've got the same exact problem here.
Neither Grub Customizer nor Start-Up Manager work with the Grub2 version that comes with Natty.  I used to use Start-Up Manager just fine in the past and it always worked.  I first discovered Start-Up Manager when I was using Ubuntu 10.04 and it worked then just as it worked with 10.10 but there were lots of changes to Grub2 by the time that 11.04 came out.  I also had difficulties changing my Grub2 Splash Image because none of the examples online about how to change the splash images are relevant now that Grub2 has changed.  Somehow I was able to figure that one out and since then I have not taken the time to figure out how to change the Default Startup OS but maybe I'll give it a shot right now since I've got a bit of time on my hands.
As soon as I figure out how to do it I'll post it here, unless someone else beats me to it.  So please Rex, if something you try works for you, let us know because I'm sure there are more people besides you and me who would like to know how to do that.

---

### Post by ubudog on 2011-09-11
> **Quackers said:**
> Are you using 11-04? Last I heard Grub Customizer wasn't working with 11-04's grub version. Startup Manager neither.
You could do it the old way by editing /etc/default/grub and changing 
GRUB_DEFAULT=0
to
GRUB_DEFAULT=  ## the number of the item you want to be default in the present grub menu - but don't forget to subtract 1 from the menu item number as the first entry is entry 0 not 1
Then save the new file and run sudo update-grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

+1

Let us know if that works.

---

### Post by Quackers on 2011-09-11
See
"New for Natty - Grub 1.99 (RC) - Drag & Drop GRUB Background"
in this guide by drs305 for Natty grub background changes

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Rex Bouwense on 2011-09-12
> **ubudog said:**
> Yeah, this is strange.  Can you please post the output of:
```
sudo update-grub2
```

Sorry this took so long.  Here is the output:
```
rex@rex-laptop:~$ sudo update-grub2
[sudo] password for rex: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda6
done
```
As you can see I am using Natty, but only in Lubuntu.  The Ubuntu OS is Lucid.

---

### Post by ubudog on 2011-09-12
Hmm, did the old way Quackers posted work?

---

### Post by Rex Bouwense on 2011-09-12
> **Quackers said:**
> Are you using 11-04? Last I heard Grub Customizer wasn't working with 11-04's grub version. Startup Manager neither.
You could do it the old way by editing /etc/default/grub and changing 
GRUB_DEFAULT=0
to
GRUB_DEFAULT=  ## the number of the item you want to be default in the present grub menu - but don't forget to subtract 1 from the menu item number as the first entry is entry 0 not 1
Then save the new file and run sudo update-grub.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

There is no place in /etc/default/grub that reads GRUB_default=0.  See attachment.  Do I have a problem because I have a Lucid (Ubuntu) which plays well with Startup Manager and Natty (Lubuntu) which apparently does not.

---

### Post by ubudog on 2011-09-12
> **Rex Bouwense said:**
> There is no place in /etc/default/grub that reads GRUB_default=0.  See attachment.  Do I have a problem because I have a Lucid (Ubuntu) which plays well with Startup Manager and Natty (Lubuntu) which apparently does not.

See GRUB_DEFAULT="Ubuntu, with Linux 2.6.32-33-generic"?  

Change that to:
GRUB_DEFAULT="4", if your Ubuntu Lucid install is the third on the list, then run:
```
sudo update-grub
```

---

### Post by Rex Bouwense on 2011-09-12
Don't go away before I ask one quick question, please.  When I count down (from 0) do I count the Memory Test stuff as well as the Recovery Options?  If that is the case, I would enter 5.

---

### Post by ubudog on 2011-09-12
> **Rex Bouwense said:**
> Don't go away before I ask one quick question, please.  When I count down (from 0) do I count the Memory Test stuff as well as the Recovery Options?  If that is the case, I would enter 5.

Yep.

---

### Post by Rex Bouwense on 2011-09-12
Well, that didn't work either.  Thank you for trying.  I may have to live with this inconvenience probably because of Lucid/Natty not playing well together.  Since I want Ubuntu 10.04 and Lubuntu 11.04, I may have to put up with it.

---

### Post by SeijiSensei on 2011-09-12
One problem I've encountered is that kernel updates will rewrite /boot/grub/grub.cfg with entries for the new kernel at the top.  If you want to boot a particular OS unconditionally, it's better to use the "GRUB_DEFAULT=title" method rather than numerals.  See [https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2) for details.

For instance, my daughter dual-boots Win7 and Kubuntu, but at school she needs Windows because her campus wifi network won't work with Linux.  I set GRUB_DEFAULT to reference the Windows partition, so it will remain unchanged even if there's a kernel update.

---

### Post by Quackers on 2011-09-12
Are you sure that you are changing the /etc/default/grub file in the correct system? Which system has control of grub? What does it say for the grub version number at the top of your grub menu?
Normally the system which has control of grub (where more than one grub is installed) is the first entry in your grub menu. However, your /etc/default/grub file has been previously edited so it is not clear.

---

### Post by ubudog on 2011-09-12
> **Quackers said:**
> Are you sure that you are changing the /etc/default/grub file in the correct system? Which system has control of grub? What does it say for the grub version number at the top of your grub menu?
Normally the system which has control of grub (where more than one grub is installed) is the first entry in your grub menu. However, your /etc/default/grub file has been previously edited so it is not clear.

Good point.

Rex, you might want to install Grub to MBR.  (this can be done with Grub Customizer, File > Install to MBR)  Then, you can probably use Grub Customizer with no problems.

---

### Post by Rex Bouwense on 2011-09-12
> **Quackers said:**
> Are you sure that you are changing the /etc/default/grub file in the correct system? Which system has control of grub? What does it say for the grub version number at the top of your grub menu?
Normally the system which has control of grub (where more than one grub is installed) is the first entry in your grub menu. However, your /etc/default/grub file has been previously edited so it is not clear.

When I typed sudo grub-install -v, I discovered that the grub version is
(GNU GRUB 1.98-1ubuntu12).  Does that mean that I should be trying to change the default boot in Lubuntu?

---

### Post by Quackers on 2011-09-12
If the other installed system is 11-04, then yes you need to be editing Lubuntu.

---

### Post by ubudog on 2011-09-12
If you want to have Ubuntu Lucid as the default entry, boot into it, open Grub Customizer, Install Grub to MBR, make your modifications, and reboot.  ;-)

---

### Post by Rex Bouwense on 2011-09-12
> **ubudog said:**
> If you want to have Ubuntu Lucid as the default entry, boot into it, open Grub Customizer, Install Grub to MBR, make your modifications, and reboot.  ;-)

Ubudog and Quackers, you guys are great.  I booted into Lucid made the changes and saved to MBR and the computer wanted to boot to Memory Test.  Then I remembered that I had previously changed the Default to 5, so I changed it back to 1 and bingo bang-go, it works just like you guys always knew it would.  Being a little older than the average bear, it took me a little longer to absorb the information that you two were trying to provide me.  I just hope that this will help others who find themselves in a similar:popcorn: situation.

---

### Post by ubudog on 2011-09-12
Great!  Glad you got it working Rex.

---

### Post by Quackers on 2011-09-12
Changed it to 1 ? I would have thought 0.
Anyway, glad to see things are working. It can get confusing with more than one grub installed :-)

---

### Post by ubudog on 2011-09-12
> **Quackers said:**
> Changed it to 1 ? I would have thought 0.
Anyway, glad to see things are working. It can get confusing with more than one grub installed :-)

Sure can.  :P

---

### Post by Rex Bouwense on 2011-09-12
> **Quackers said:**
> Changed it to 1 ? I would have thought 0.
Anyway, glad to see things are working. It can get confusing with more than one grub installed :-)

Normally it would be, but I was using the grub customizer so it is listed as 1.

---

### Post by Quackers on 2011-09-12
Thanks for clearing that up :-)
Happy Ubuntuing!

---

