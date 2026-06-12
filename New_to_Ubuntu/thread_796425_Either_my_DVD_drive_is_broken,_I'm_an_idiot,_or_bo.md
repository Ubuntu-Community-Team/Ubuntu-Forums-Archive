---
title: "Either my DVD drive is broken, I'm an idiot, or both (installaion question)"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by adamgram on 2008-05-16
Ok, so here's the deal:  My 6 month old IBM Thinkpad stopped working.  It wouldn't connect to my wireless network, it wouldn't recognize my CD/DVD drive or USB devices, and the 'safely remove hardware' icon was always at the bottom of the screen saying it's safe to remove my CD/DVD drive.

My intended solution was to do what I've been meaning to do anyway and install Ubuntu on it.  Since no specific physical harm was done to the computer to make me think all 3 things would break at once, I thought this might fix the problem.  So I downloaded the .iso file, burned it to a CD using Windows (not using the 'Image Burner' software recomendded on the Ubuntu website), and booted the computer.  It started up in Windows.

So I figured Windows wasn't recognizing the CD/DVD drive at startup.  It wasn't recognizing it in Windows Explorer either.  So I did a full system restore on the machine to get Windows back to the way it was when I bought it.  Windows now DOES recognize the wireless network, USB drives, and the DVD drive, but the 'safely remove hardware' icon still refers to my CD/DVD drive, even though it otherwise appears to be working fine. I still want to put Ubuntu on it, though, now that I have a fresh start with the computer.  

The problem is when I put the CD in the drive and start the computer, it still starts in Windows.  Once it's started up, I see the the CD is there through Windows Explorer, but it just shows the .iso file and dosen't know what to do with it.

So, finally here's my question:  Is there something I might have to do to tell the computer to look at the disk in the drive while booting before starting Windows?  Or do you have to burn the .iso using the 'Image Burning' software (as opposed to just using Windows to make a data disk) to make it a boot disk? I have Windows XP Proffesional edition.

Thanks in advance.

---

### Post by Tom--d on 2008-05-16
You need the Image Burning software.

As Windows just dumps the .iso file on the disk. Image Burning will burn the image on the disk. Making it bootable. 

Do that and you will be able to boot from the disk.

---

### Post by Grishka on 2008-05-16
man, just putting the file on a CD won't do. .iso files are disc images, they have to be recorded as one. you have to use a 'burn image' option in a cd-burning software.

---

### Post by mkoehler on 2008-05-16
An .iso is simply an image of a disk stored in a specific file format - You cannot run this image without getting some type of mounting program or burning it with an .iso burner as instructed on the ubuntu website. :)

---

### Post by shifty_powers on 2008-05-16
get imgburn, (google it, it's free and one of the best dvd/cd burners around), and use that to burn the downloaded iso file. then boot from cd.

voilà ;)

---

### Post by adamgram on 2008-05-16
Thanks guys!  I'll try it that way when I get home!

---

### Post by nicedude on 2008-05-16
Also if still boots to windows with a proper install CD you will need to change your BIOS settings for boot device priority and set the CD drive to boot before your hard disk does.

---

### Post by adamgram on 2008-05-19
Also good to know, I knew there was something like that.  Thanks for the help.  The CD I made with the image burner worked, thanks again.

---

