---
title: "Problem installing Ubuntu on my PC"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by krivins_a on 2014-08-04
Hello! Recently I got a new PC - Lenovo Ideapad G505 with DOS on it. I thought I should install Linux Ubuntu on it. 
What I did was download the latest available Ubuntu version and used this [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) to apply it to my USB stick.
When I plug it in, all is okay, it shows me 4 options: Try Ubuntu without installing, Install Ubuntu, OEM install (for manufacturers), check disc for defects. 
I tried installing it and this is what I got (sorry about reflection) (I will just provide picture links because when I insert the picture in this article, it makes the picture gigantic) [http://img.exs.lv/p/a/painfoinmr/20140803_181613.jpg](http://img.exs.lv/p/a/painfoinmr/20140803_181613.jpg) - it appears like there is the installation window but everything is messed up. If you look at the cursor it seems I could type in something. Nothing happened though when I tried to press something.
Next I tried Ubuntu without installing and everything appears like this - [http://img.exs.lv/p/a/painfoinmr/20140803_182324.jpg](http://img.exs.lv/p/a/painfoinmr/20140803_182324.jpg) . I tried to use some applications like firefox and settings, it would open new window but all is still messed up.
My friend suggested me to delete all data from my USB stick and try installing Ubuntu on it again. Did it twice, nothing changed. But when I pick the option to check disc for defects, it says it has found 2 errors (I dunno if it has anything to do with Ubuntu).
Lastly my friend suggested to get in BIOS. I tried F1 to F12 and delete button when starting PC without usb stick pluged in. Nothing worked. I couldn't get into BIOS even with stick pluged in. 
Friend said that is is most likely because of integrated graphics card (PC has another, better graphics card). I am quite desperate, don't know what to do. Help me please.
Sorry about my english mistakes.

---

### Post by yancek on 2014-08-04
The third image you posted with all the weird horizontal lines is due to a problem with the graphics card.
First off, how old/new is this computer?  Can you post some information on the hardware such as processor speed, RAM, graphics card. 

>  But when I pick the option to check disc for defects, it says it has found 2 errors 

Could you check what they are and post them here?

I don't have a Lenovo Ideapad but, the last time I used one it was the F2 key to get into the BIOS.  It should show at the bottom of the initial Lenovo screen.  You don't need the usb/CD/DVD/ or even a hard drive to get into the BIOS as it is on the system board.

---

### Post by Impavidus on 2014-08-04
If there are errors on the live disk, problems can be expected. Check the .iso file you downloaded using its md5 hash ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) and compare it to the published version ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)). If you downloaded using the torrent it should be OK, if not OK, download the .iso again. The torrent is the most reliable way. Create a new live disk.

If the problem doesn't go away, it's likely your graphics card that's not supported out of the box on Ubuntu. This can usually be fixed. The remarkable thing is that the dock on the left looks OK.

The latest available version, I assume that is 14.04 LTS? Because there is also 14.10, which is the development version, and if you found it via an old link it may have led you to an older version. It happens.

---

### Post by krivins_a on 2014-08-04
Yancek, thanks for your answer. This is what I found out:
It showed mismatch (i supposed that's the error) for /boot/grub/grub.cfg and /boot/grub/loopback.cfg.
I still can't get into BIOS with F2.
I bought this computer 2 days ago, it should be new. It's hardware: CPU - AMD A4-5000 1.5GHz quadcore, 4GB RAM, 500 HDD, graphics card - *AMD Radeon HD 8570M 1 GB.*

---

### Post by yancek on 2014-08-04
> It showed mismatch (i supposed that's the error) for /boot/grub/grub.cfg and /boot/grub/loopback.cfg.

Not sure what you mean by that.  Both those files should be on the flash drive.  Are you referring to the md5sum not matching?  If that's the case, download the iso file again and check it before putting it on the flash drive.

You should see something at the bottom of the BIOS screen with the Lenovo logo telling you to use a specific key to enter setup.  If you can't do that, it's the hardware.

---

### Post by Henrik_R on 2014-12-10
Actually I got the same problem with my new Lenovo Y50 with preinstalled Win 8.1 where I want dual boot. 

I downloaded Universal USB Installer 1.9.5.8 and burned ubuntu-14.04.1-desktop-amd64.iso to the flash drive. Afterwards booted with this device where I got same message as the ther guy. It will not load the graphic interface but will just load the 4 options as for the other guy. When choosing option 4: check disk for defects it says 2 errrs detected and I can see that it is the exact same files files having a mismatch: boot.cfg and loopback.cfg. I tried to download and burn the iso file several times and even as a bittorrent but same error each time.

---

### Post by Darth Riker on 2014-12-10
> **krivins_a said:**
> I still can't get into BIOS with F2.
I bought this computer 2 days ago, it should be new. It's hardware: CPU - AMD A4-5000 1.5GHz quadcore, 4GB RAM, 500 HDD, graphics card - *AMD Radeon HD 8570M 1 GB.*

[s]Did you start tapping the F2 key repeatedly, and quickly, as soon as you turn it on?

According this page - [http://support.lenovo.com/gb/en/products/laptops-and-netbooks/lenovo-g-series-laptops/lenovo-g505-notebook/documents/HT101636?tabName=Solutions#2](http://support.lenovo.com/gb/en/products/laptops-and-netbooks/lenovo-g-series-laptops/lenovo-g505-notebook/documents/HT101636?tabName=Solutions#2) - the F2 key is what is needed to enter the BIOS.[/s]

Sorry. Ignore this. Refer to the post below mine  ... although if you have issues with the link its here as well: [http://download.lenovo.com/consumer/mobiles_pub/lenovo_g400g500g405g505g410g510_ug_english.pdf](http://download.lenovo.com/consumer/mobiles_pub/lenovo_g400g500g405g505g410g510_ug_english.pdf)

---

### Post by Gordonbp531 on 2014-12-10
> **krivins_a said:**
> Y
I still can't get into BIOS with F2.


That's because the G505 doesn't do it that way.
Look at the User Manual here :
[http://www.lenovo.com/shop/americas/content/user_guides/g410_g510_ug_en.pdf]("http://www.lenovo.com/shop/americas/content/user_guides/g410_g510_ug_en.pdf")
Go to Page 2, and you'll see a reference to a "Lenovo" button next to the Power button.
With the machine switched off, press that button and you'll get a menu with BIOS as an option.

---

### Post by Henrik_R on 2014-12-11
I think just start your Lenovo and press F12 but anyway why change the subject? It is not an Ubuntu issue and should be solved elsewhere. 

The question is still why it can not boot with the Ubuntu flash drive with an error of mismatch in boot.cfg and loopback.cfg? Is it the graphics card?

---

### Post by Gordonbp531 on 2014-12-11
> **Henrik_R said:**
> I think just start your Lenovo and press F12 but anyway why change the subject? It is not an Ubuntu issue and should be solved elsewhere. 

The question is still why it can not boot with the Ubuntu flash drive with an error of mismatch in boot.cfg and loopback.cfg? Is it the graphics card?

Maybe the software you used for creating the bootable USB stick didn't work properly.
I've had mixed results with various utilities until I found this:
[Rufus bootable USB creator.]("http://rufus.akeo.ie/")

I've had no problems ever since.
Another  thought - I've also had problems using USB3 ports - USB2 work perfectly.

---

### Post by Henrik_R on 2014-12-17
I have just tried to make the flashdisk in USB2 with Rufus and it helped! I do not get any errors about grub.cfg and loopback.cfg mismatch anymore. So it really helped what you proposed ;-)

I though still got a problem :-( Just after booting it gives an error which quickly disappears from the screen (to fast for me to see the error) and then the 4 options still appears:
Try Ubuntu without installing, Install Ubuntu, OEM install (for manufacturers), check disc for defects.

Shouldnt it at this point instead load the graphics interface automatically to ask whether to make dual or single boot system?

---

### Post by oldfred on 2014-12-17
If booting in UEFI mode which you want if Windows is UEFI, then you get the grub boot menu.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

