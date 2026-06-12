---
title: "IDE drive not spinning up or seen in bios"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by mrlabor1 on 2012-05-30
Hello,

I had an IDE  hitachi 500 GB in a Dell 2400.  I took it out and put it in a Dell 4800.  The 4800 only had SATA so I plugged the drive in question into the CD ROM IDE cable.  It still did not show up in the bios of the 4800, even after fiddling with the setup utility and jumpers. 

So I put it back into the 2400 and it will not show up on the bios of original computer.  I have tried new cables, different power cords (verified voltage with meter) and it won't spin.  I then tried it in a different computer that has an ide cable.  Still not spin, no bios recognition

It was working yesterday just fine, did I wait a day too long to back up/clone this drive?   Is there any way to temporarily breathe life into it to have UBCD and clonezilla work their magic?:confused:

Thanks if you can help,  if you are the bearer of bad news, I still need to hear it

Best regards,

Lee

---

### Post by tiosus on 2012-05-30
I have same problem, many years ago
check your drive with some other system
also make trust about IDE cable connector , many problem of IDE device , refer to IDE cable
you must check your device by changing all parameters
in the first step your parameters is : power(no matter what kind) , IDE Cable , and IDE Slot on your board

---

### Post by tiosus on 2012-05-30
> **tiosus said:**
> I have same problem, many years ago
check your drive with some other system
also make trust about IDE cable connector , many problem of IDE device , refer to IDE cable
you must check your device by changing all parameters
in the first step your parameters is : power(no matter what kind) , IDE Cable , and IDE Slot on your board
it's better to run test by using new IDE and Power connectors
so just go and find a pc that can run test on it

---

### Post by tiosus on 2012-05-30
Oh , i forgot to say that also  the jumpers count as parameters

---

### Post by jmore9 on 2012-05-30
Check your master / slave settings if you changed them.  If you rememner what the orginal ones were set them back and try again.  I use the middle connector on an ide cable as master connector and set the device to master ( on rear of device a little connector is changed to select rhis ).

Hope this helps a little.

---

### Post by tiosus on 2012-05-30
finally you have 1 IDE device + 2 IDE cable + 2 power + 2 IDE Slot on motherboard + at least 3 jumper position
and by changing this parameters you can create  1*2*2*2*3= 24 situation
if no change made during this 24 situation , Probably your device is gone! or you can contact whit support center of device Warranty

---

### Post by mrlabor1 on 2012-05-31
Ok guys! 

I have tried it in the original computer again, the Dell 2400.  It only has one IDE slot, and came with a single cable for master only.  I tried it with the jumpers in the master as well as the cable select positions. I then tried it with a different cable, with jumpers in both master and cable select positions. 

I then tried it in another tower that supports IDE drives.  with the same as above two different cables in both the master and cable select jumper positions.

It still says no drive 0 found press f1 to continue or f2 to enter utility. I can tell it is not even spinning up.

 I will try an ide to sata adapter tomorrow. 

Thanks for the quick replies, hopefully someone knows what i did wrong to the drive

Regards,

Lee

---

### Post by gnusci on 2012-05-31
Try some tools to repair/recover the data:

[http://en.wikipedia.org/wiki/List_of_data_recovery_software](http://en.wikipedia.org/wiki/List_of_data_recovery_software)

---

### Post by poettone on 2012-05-31
It sounds like something has either happened to this drive (mechanically) or the controller board has failed.

I know something I tried years ago on a drive was to put it in the freezer (yes, I said freezer) for 1 hour. I'm not sure this would work in your scenario or not considering you have no "spin up" on the drive. 

You can and should simply connect this drive to power and turn the system on.. Does it spin up? This removes from the equation any other settings, jumper, bios, etc from the drive and is strictly power.. If you get no spinny, then you can, as the other poster stated, try to get some warranty or disk drive recovery on it. That is big money though.. I only had to do one in my career and it was over $1600 dollars.. Make sure it's worth it:)

Regards,
Poettone.

---

### Post by poettone on 2012-05-31
Also, they sell relatively cheap conversion kits for drives, that convert any type of interface, ide, sata, laptop into USB.. It has saved me many times over.. Very easy as well.. Cost around $25.. But again that is on a drive that is powering up.. 

Try the drive as noted with just the power connection and see if you get anything, forget the data connection and bios settings.. just see if it will spin..

---

### Post by mrlabor1 on 2012-05-31
Oh I almost forgot.

I used UBCD went to parted magic.  It also had troubles booting because it could not find the drive.  Once into parted magic, it still would not spin up or be recognized.  

Just in case that would be helpful.

Regards,

Lee

---

### Post by mrlabor1 on 2012-05-31
@Poettone,

I almost forgot.  I read in several of the other threads about bad drives, to just plug in the power, and not the IDE cable.  Tried that in the first iteration trying to get spin.  No Dice.

again thanks for all the responses so quick.

Lee

---

### Post by davecotefilm on 2012-05-31
I'm new to Ubuntu and must say, I love it!!!

---

### Post by mrlabor1 on 2012-05-31
Question for the more mechanically/ solid state type knowledgeable persons out there,  If it is the driver/controller board, can I Get a T8 remove it and replace with another? or does it have to be from the same make and model?

regards,

mrlabor1

---

### Post by Dave_in_MD on 2012-05-31
> **jmore9 said:**
>   I use the middle connector on an ide cable as master connector

Hope this helps a little.
This is true for a 40 wire ribbon cable, with an 80 wire ribbon the far connector is the master.  both cables use a 40 pin connector to further confuse the issue.

---

### Post by roelforg on 2012-05-31
Try setting the master/slave to cableselect.
The IDE controller of my server's broken and only recognises slave devices and only when on cableselect.

---

### Post by mikechant on 2012-05-31
If it's not even spinning up with just the power cable connected, you may have damaged it slightly when removing it from the original PC.
The damage could be quite minor, i.e. one of the pins in the power connector becoming unsoldered where it joins the controller board due to the pin movement when you removed the power cable. The pin connections should be fully accessible from the underside of the drive in most models so you may be able to check (visually or with a simple circuit tester) if the power pins are properly connected to the controller board and possibly resolder if one is not.

---

