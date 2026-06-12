---
title: "Install Ubuntu on external HDD"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by Raweed on 2011-09-11
Hi, im having some issues installing ubuntu 11.04 onto an external HDD. I want to install it on there because i dont want to mess with W7 on my internal HDD. 
this is what ive tried
on the install ubuntu section i click something else
select my external HDD
create the following partitions :- 
256mb, ext2 mount /boot
2 gb, Linux Swap
10gb, ext4 mount /
260gb, ext4 mount /home
there is still approx 700gb unallocated space on the disk because i dont want to use all of it
i choose the Grub isntall thing as my external HDD
then hit install now, after it installs it says it is successfull and need to restart
when i restat and go to my boot menu
i get 2 of the same options to boot from my ext HDD
when i check either of them i only get a blank screen and nothing ever happens
then when i force shutdown and restart and then check boot menu there is no option to boot from ext HDD at all
windows 7 is not changed or effected.
am i doing something wrong please help :(

My laptop can boot from usb drives and i cant take out internal hdd or deactivate it from BIOS but its not effecting it

---

### Post by corncob on 2011-09-11
As an alternative to what you're doing (which isn't working), I might,after selecting the external drive, install it using the entire drive.  If this works as you want it to, I would then boot to the live CD and use gparted to shrink the Ubuntu partition so as to get the 700 GB of unallocated space you want.
Keep in mind that your computer won't start if you disconnect the external drive because the grub files will be on it.  You could install it so that the boot loader is on the external drive (leaving the internal w7 boot sector undisturbed) but then you would have to select the boot drive in BIOS.

---

### Post by Raweed on 2011-09-11
thank you replying, im a noob at this so please bear with me :/ 
If i select the entire drive then it doesnt ask me where i want to boot loader and i think it will automatically put it so my internal one, i am doing this because any alterations to my internal hdd will void my warranty(i checked) which i have for my laptop and therefore am not dual booting either. 
the only way i can select where i want to load the boot loader is when i select do something else where i personally require to create the partitions, i have tried whilst creating the partitions to not keep and unallocated space and give aroun 900gb to the /home so its using the whole ext hdd but i still get the same problem :/ ive also made sure that the partitions are at the front of the ext hdd because i read that it causes problems as well.

---

### Post by corncob on 2011-09-11
Can you make the external drive the first boot device in BIOS (after the CD if need be)?  That way I would expect the grub boot loader would be installed there and would even pick up Windows on the boot menu.

Is there no way you can disconnect the internal drive to avoid any surprises?  After reconnecting it you can get w7 on the boot menu by running
```
sudo update-grub
```

If not, do you have another computer that you could swap drives with, install Ubuntu, and take the drive back out to your laptop.  Unlike Window$, this can be done with Ubuntu.

Finally, I should mention that the win7 MBR can be restored from your backup disk if it gets messed up.

---

### Post by Raweed on 2011-09-11
Hi, i cant take my internal hdd out theres some stupid seal on it i cant break -.- and for some reason it doesnt give me an option to disable it from BIOS either. 
I'll try doing it from another computer(removing internal HDD) but will i still be able to boot from my laptop?
and when should i run the code
sudo update-grub
and what does it do im not quiet following.
and is it a problem if im using a separate USB to install from not a LiveCD?

---

### Post by oldfred on 2011-09-11
Post this so we can see if everything is installed correctly. But it may be booting ok if you have grub menu, but then you have video issues or or some other boot parameter is required. Defaults for install are not same as liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

I do not recommend a separate /boot for most desktops, but you install looks like it should be fine as it is.

---

### Post by Raweed on 2011-09-11
@oldfred Im really sorry but as i said im a complete newbie at this, so are you trying to say that its installed correctly but some parameters need changing in the grub. if so how do i do that if i cant boot it, from the try version? and then re-install?

and more update i just found out that if i stick the ext hdd in and turn the laptop on then go to boot menu its not visible there but then if from there i go into BIOS, then change nothing save and exit so it restarts without turning the machine of then again go to the boot menu its there again twice. I find that kind of weird. and seeing as its there twice, if i choose the second one it turns black for a bit and a '_' flashes then trys and boots windows but gets stuck.
if i choose the first one a '_' flashes then after a while the 'loading' comes up on the left side of every line and it makes a loud beep if i try and press any keys, i waited 5 minutes and nothing happened so forced shut down. this is from my previous install before i started this thread.

---

### Post by corncob on 2011-09-12
> **Raweed said:**
> Hi, i cant take my internal hdd out theres some stupid seal on it i cant break -.- and for some reason it doesnt give me an option to disable it from BIOS either. 
I'll try doing it from another computer(removing internal HDD) but will i still be able to boot from my laptop?
and when should i run the code
sudo update-grub
and what does it do im not quiet following.
and is it a problem if im using a separate USB to install from not a LiveCD?

You will have to change the first boot device in BIOS to boot from the external HD.  On my eeepc pressing ESC when I turn it on gives me a menu of bootable devices but I don't know if this is universal.  
You don't have to run the code at all if that's a problem.  If you leave the first boot device set for the external drive it will give you an option to run Windows on startup without changing the BIOS settings.  You run it from Terminal in Ubuntu.
I don't know what your doing but, yes, you can install Ubuntu from a USB stick instead of a CD.  Try it.

---

### Post by oldfred on 2011-09-12
You can run the boot script from the liveCD or USB that you used to install with.

On my desktop and laptop, it is f12 in the BIOS boot screen to choose boot devices as a one time choice instead of a permanent change in BIOS, but corncob says it is different for many systems.

When booting from external that gives you just the underscore, try holding down shift key from BIOS. You then should get grub menu. Try rescue mode or other settings.

---

### Post by Raweed on 2011-11-21
For anyone visiting this post the issue was that there wasnt enough power going through the USB to power the ext HDD to boot up in time, As soon as i got one with an external power source it worked like a charm. An issue that is easily overlooked.

---

