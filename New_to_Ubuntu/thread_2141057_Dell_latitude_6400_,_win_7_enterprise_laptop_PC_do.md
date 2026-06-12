---
title: "Dell latitude 6400 , win 7 enterprise laptop PC does not select USB drive"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by AdamTudor on 2013-05-01
Hi

I have a win 7, laptop  PC per specifications mentioned above 

I stick in the linux live USB in the laptop, ( this USB has worked on older machines ),  then switch on the machine, .....while it is about to boot,
 
Edit : The bios at start says bios revision A 20 .... Just noticed it now 

while it is about to boot, I quickly press (3 trials explained below )
-----------------------------------------------------------------------------
(a) escape key.....That leads me to the windows boot manager that just shows " choose operating system to start " and gives the one and only windows 7 " , but does NOT seem to recognize the USB !!!

(B) I try again, press f12 for boot options, again get dozen options all within " advanced options for windows 7" like safe mode , safe mode with networking etc  !!!! None to select the USB 

(C) try again press F10 ( each trial during rebooting, before reaching windows !! ) f10 shows boot options and shows path : \windows\system32\winload.exe and  partition : 2 ...hard disk ...not USB 

there is a blank space below the hard disk, andi guess I should enter the right option for USB 

**what should I do / what should  i type in boot options, to include the USB As a boot option ?**


TIA 

regards

---

### Post by MaZaMo on 2013-05-01
Sorry for the edit i replied to the wrong post ...

---

### Post by Tom 6 on 2013-05-01
Hi :)
I just went to the Hp site and found this link
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=5060880&prodNameId=5060882&swEnvOID=4053&swLang=13&taskId=135&swItem=ob-98935-1&mode=3](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=5060880&prodNameId=5060882&swEnvOID=4053&swLang=13&taskId=135&swItem=ob-98935-1&mode=3)
I'm not sure if upgrading your bios might help.  I generally recommend avoiding it because it's a nightmare if it goes wrong.  

When your machine is first switched on it should display a splash screen showing off the mbords logo and usually at the bottom it shows how to get into the bios.  It vanishes a tad quickly tho!  Typically it's the Del key or F2, F8, F10, F12.  Usually the Del key though.  Usually when you get the right one you have to use the keyboard to navigate around a weirdly ancient looking gui but can change all sorts of interesting things, or at least look at them and wonder what they do.  

If you can't get it to boot Usb can you try to get it to boot a Cd/Dvd-drive?  Does it have one? n It might be worth trying to get a LiveCd session working rather than a LiveUsb.  Also it might be worth trying an extremely light-weight distro such as SLiTaZ
[http://distrowatch/slitaz](http://distrowatch/slitaz)
just to see if you can.  If that works then try again with Ubuntu.   Knoppix used to be well regarded for being able to boot-up on any weird hardware and recognise all sorts of strange peripherals.  It might be worth a shot too if you can.  

Regards from 
Tom :)

---

### Post by AdamTudor on 2013-05-01
Thanks Tom 



 (a) I have already tried f12, f10 and f8 .....but missed f2.... !!! 
(b) as I mentioned I do NOT have the admin password for this machine

U  got  that f2 right ...yes it was f2

But....but...Press f2 and and I see That changing ANY option (under f2 ) requires an admin password !!!!

smart move m$

is **there a way to boot from USB after windows has started ? **

Or 

ok ...try some other computer 


Thanks Tom  you sorted out one important doubt I had


Best regards

---

### Post by Tom 6 on 2013-05-12
Hi :)
Sorry for the delay in replying!  :(

So you got to the bios but the bios wanted a password before really letting you in?  
1.  Is it your own machine or does it belong to a company, organisation, university or something?  If it belongs to something like that you might be able to talk to their IT department about what you want to do.  It's not standard so you might have to escalate up to their supervisor or boss or something.    
2.  If it is your own machine then it's going to be tricky.  Can you contact the shop where you bought it or person you bought it from?  They might not know though.  Most people are fairly clueless about crucial things like that.  I only learned how to turn off the gas & water in my house yday and i've lived here 5 years!  If the person or shop can't help you then is there a local computer repair shop you could take it to?  They might be able to crack it.  

How recently did you get the machine?  MS have started a cunning scheme to block people from being able to edit their own bios for "security reasons".  It's to prevent rootkits and stuff (i think) and to prevent people booting up unapproved operating systems.  It's called something like "Secure boot"
[http://www.zdnet.com/microsoft-windows-8-uefi-secure-boot-complaint-the-case-for-and-against-7000013248/](http://www.zdnet.com/microsoft-windows-8-uefi-secure-boot-complaint-the-case-for-and-against-7000013248/)
[http://technet.microsoft.com/en-us/windows/jj737995.aspx](http://technet.microsoft.com/en-us/windows/jj737995.aspx)

It's really only on Win8 machines but someone might have managed to upgrade from Win8 back to Win7.  There are still a lot of people who don't like Win 8.  It happened with Vista too.  People went out and bought Xp to avoid having to suffer Vista for long.  


Errr, did you manage to try out a different machine?  

If you are new to all this messing around with the bios and stuff then it often helps to try it out on an old machine that no-one cares much about anymore.  If you can disconnect the hard-drive then it ensures you won't accidentally damage any data or files or anything on it.  I was lucky and got a ton of machines off work when they were chucking them in a skip.  Actually 2 of those became really useful with Gnu&Linux on.  They went from being unbearably slow to knocking the socks off my bosses brand new swish machine.  Plus i was able to get the data off one of them once i'd got the hang of booting up and using Gnu&Linux.  


I think what i am suggesting is that it might be best to keep the Win7 as a Win7 machine and use an older machine for Ubuntu.  That might give this UEFI thing time to get resolved and give you time to explore Ubuntu without worrying about what happens if you need to take the hardware back to the shop or something.  
Regards from 
Tom :)

---

