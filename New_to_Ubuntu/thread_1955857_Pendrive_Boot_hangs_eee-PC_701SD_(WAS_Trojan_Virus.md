---
title: "Pendrive Boot hangs eee-PC 701SD (WAS Trojan Virus?)"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by whatsaterminal on 2012-04-10
okay, thanks to the advice of kDane i got past the initial obstacle of anxiety about rumors of a virus embedded in the PendriveLinux USB tool. (has someone already thought of calling it USBootu? i guess that only works when you're using it for a Ubuntu derivative)

so i downloaded the Tool and the Ub 11.10 ISO onto my little USB. maybe i pushed my luck a bit, attempting to cram all this onto a nominal 2G flashdrive, and specifying a 1.2somethingG space for persistence on the drive. the loading process paused for a few seconds on a line that said something about an Error for insufficient space, but it then resumed with some lines that talked about somebody's openSource code and i wondered if it might be some appended subroutine that was intended to fix the space problem by backing off the persistent space spec. less than a minute later it announced that the flashdrive was ready for installation or Live Boot. 

so i plugged it into the target machine, hey presto the power button and F2 and away we went. i don't recall the exact sequence of events, i think i managed to get into the BIOS boot priority menu the first time around and after a bit of puzzlement figured out how to get the USB into the top boot priority.  to my amazement it booted into the standard desktop Ubuntu screen (the one i was expecting from this USB). (on a couple of subsequent retrials i discovered my amnesic little 701SD apparently forgot it had this flashdrive plugged into the USB port and needed to be reminded).
after a bit of playing around i discovered this thing thought it was not connected to my LAN even though i did have a patch cable running from the LAN port to my router (which was actively running my main desktop quite competently). so i bypassed the router by running the modem-to-router cable directly to my target machine to rule out some weird router problem, with the same result. i never got internet connectivity and i did manage to stumble across a network menu on my Ubuntu desktop that said under the Wired menu "cable not plugged in" with a cute little icon of a RJ-45 plug dangling in midair. 

another thing i noticed was that in the shutdown menu "hibernate" is INactive, only Suspend and ShutDown are allowed. wonder if this is because this hardware has such a small SSD (8G)?

after a shutdown or 2 in the course of trying to resolve the connectivity problem, bootup hung at the "Ubuntu" screen, with the five orange dots of death marching across under the "Ubuntu". and after repeated re-trials, that's * all* i now get. 

ADDENDUM 10 hours later: when it first starts to boot Ub, it displays a couple of lines that start with something like 'loading casper initrd....'
then it flashes a bunch of scrolling lines that i can't pick out for a few seconds, then progresses to the five marching dots of death.



i find that while viewing the orange dots of death, i can get the screen to toggle to another display by pressing any fn key, or esc, or any arrow key, and the display shows a bunch of lines that scroll by so fast i can't make them out, followed by "mountall: connection is closed" repeated about 27 times. i can't make out all of the line above that , but it has something like "...the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Addendum 12 hours later : rechecked the lines displayed when toggling  with fn key: this time i pressed ALT-F1 and the lines of script had all  kinds of stuff like <usbcore: registered new interface driver  usb-storage> and <drm: registered panic notifier> and sd  2:0:0:0: [sdb] No Caching mode page present> and <EXT2-fs (loop1):  warning: mounting unchecked fs, running e2fsck is recommended> and  <EXT2-fs (loop1): error:ext2_lookup: deleted inode  referenced:216876>
sorry about the formatting.  also some stuff about can't umount device, storage device busy, etc. 

i've thought of a lot of options to approach this but i don't really know where to place my troubleshooting priorities. Build a whole new USB tool from scratch and start over? maybe it's a mistake to try to run this OS on a teeny little 701SD? (originally had Xandros)  in the course of researching this problem i stumbled on Psychocats' most informative Ubuntu primer. reading it led me to reflect maybe i should have selected K-, X-, or Lubuntu for this hardware. 

any advice? thanks

---

### Post by whatsaterminal on 2012-04-11
more additional info:

the screen i get is similar to what is described in the first post under
**Login Screen is not Coming**

IOW it looks like this:
[http://www.sucka.net/wp-content/uplo...oot.png?cda6c1]("http://www.sucka.net/wp-content/uploads/2010/03/boot.png?cda6c1")

apparently when i hit esc what i am seeing is the bootlog? but short of imaging it with a digital cam, then laboriously downloading the image and attaching it to a message like this one, i am not sure how to put the contents of the log on view. since the computer in question is by definition incapable of making its own screen shot at the moment. 

thanks for any help.

whats

---

### Post by wojox on 2012-04-11
I have the asus 900 eeepc and it installed okay with some work arounds.

How much memory do you have?

You still haven't gotten past the boot screen to install it?

---

### Post by whatsaterminal on 2012-04-11
> **wojox said:**
> I have the asus 900 eeepc and it installed okay with some work arounds.

How much memory do you have?

You still haven't gotten past the boot screen to install it?


as noted in my original, it did boot a couple times at first, then hung on successive tries. 

this is the  701 SD with an advertised 8G solid state drive. if you read the fine print on **[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)** this should be sufficient. 
what workarounds did you find necessary. and were you using oneiric or precise.

thanks

---

### Post by wojox on 2012-04-11
Right 8Gb. is great. I had the 4Gb. ssd and had to use some workaround. What about memory? More than 1 Gb. good.

I've run all versions to see if they will work. The last two I tried where Ubuntu 12.04 and Lubuntu 12.04.

Try going into Bios (F2) and reset it to the defaults. Reboot with your flash drive and hit Esc. to choose which drive to boot off of.

---

### Post by whatsaterminal on 2012-04-11
> **wojox said:**
> Right 8Gb. is great. I had the 4Gb. ssd and had to use some workaround. What about memory? More than 1 Gb. good.

I've run all versions to see if they will work. The last two I tried where Ubuntu 12.04 and Lubuntu 12.04.

Try going into Bios (F2) and reset it to the defaults. Reboot with your flash drive and hit Esc. to choose which drive to boot off of.


thanks i will try that. 
yeh, this has only 1G of RAM. thinking of upgrading. 
did both 12.04's work for you?

---

### Post by wojox on 2012-04-11
> **whatsaterminal said:**
> thanks i will try that. 
yeh, this has only 1G of RAM. thinking of upgrading. 
did both 12.04's work for you?

Yup, L/Ubuntu 12.04 both ran great.

---

### Post by whatsaterminal on 2012-04-12
okay, i tried making a whole new removable boot drive on a Kingston 16G SDHC card
(see my discussion on thread titled 
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Okay to use SDHC card instead of USB stick?]("http://ubuntuforums.org/showthread.php?t=1956794") )

and this time per the kind advice of another user i temporarily disabled my AVG virus blocker while the  USB-builder tool was  writing to the card.  however i got essentially the same result that i did when attempting to boot from a USB flashdrive. 
except this time, when it did boot successfully for the first and only successful attempt, i *did*
have LAN connectivity. but of course i couldn't resist shutting down and rebooting just to see 
what would happen. and of course...got the same result as previously described. 



hmm. guess i will try my luck with Kubuntu. after all this little 701SD is supposed to be based on 
KDE code. about which i know absolutely nothing....

any suggestions? thanks for your comments
-What's

---

