---
title: "I need a program that will nuke my drive if the correct password is not entered 3  ti"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by venom104 on 2012-01-09
I'm looking for some type of program (that possibly includes it's own boot loader) that will SECURELY format all of the data on my hard drive if the correct password isn't entered in 3-5 times. I've been asking a bunch of people this and they say that it can't be done because formats aren't secure; my response is this [http://www.dban.org/](http://www.dban.org/) . I use that iso to erase my hard drive every so often (whenever a new version of ubuntu comes out). 

I'm running windows 7 on one partition on my hard drive (it's encrypted via truecrypt) and I run ubuntu 10.04 LTS on the other partition. I need something that will work with the ubuntu side, although if it doesn't exist, I could start using windows again.

Does anything like this exist, or do I have to create it myself? I would have tried googling this, but I honestly don't know what to google!

I forgot to mention, I need it to work if the hard disc is ripped out and used in another machine that is examining it. I need the program to run and destroy the drive in this case.

EDIT:

I've been thinking about this, if something like this doesn't exist, I may have to write my own firmware for the drive. If that's the case, what do I need to know in order to do that?

---

### Post by Basher101 on 2012-01-09
you should use encryption, but not the normal way. Skilled people can tell you have an encrypted volume, but they cannot tell how many volumes you got inside that encrypted volume. So you create one big encrypted volume in which you create others, which, you encrypt too. This way, if anyone tried to decrypt the bigger one, all the data inside the smaller ones will get lost. You must encrypt the ones inside first, and then the bigger one to get the data readable. 

thus you set it up like this:
HDD ----> |encryption|--> Big Volume ---> |encryption| --> smaller volumes

---

### Post by Double.J on 2012-01-09
programs like dd can be used - however the only way to securely erase is to write to every sector, not just format. If you've ever used Apple's disk utility's erase feature, you'll understand just how long this takes, so my concern - other than you endind up in a mission impossible situation 1 password attempt from disaster is how long it will take - an intruder would simply see what's happening and pull the power cord, remove the drive and mount if on another machine.

I'd just use encryption - strong encryption is so strong that authorities have had to pass legislation making it an offence not to tell them the password.

hope you find this useful?

Edit:

> **Basher101 said:**
> you should use encryption, but not the normal way. Skilled people can tell you have an encrypted volume, but they cannot tell how many volumes you got inside that encrypted volume. So you create one big encrypted volume in which you create others, which, you encrypt too. This way, if anyone tried to decrypt the bigger one, all the data inside the smaller ones will get lost. You must encrypt the ones inside first, and then the bigger one to get the data readable. 

thus you set it up like this:
HDD ----> |encryption|--> Big Volume ---> |encryption| --> smaller volumes
^^^ plus one ^^^

Got me again Basher101 - saw you over at membership requests; when you do apply you'll have my vote :)

---

### Post by venom104 on 2012-01-09
> **Basher101 said:**
> you should use encryption, but not the normal way. Skilled people can tell you have an encrypted volume, but they cannot tell how many volumes you got inside that encrypted volume. So you create one big encrypted volume in which you create others, which, you encrypt too. This way, if anyone tried to decrypt the bigger one, all the data inside the smaller ones will get lost. You must encrypt the ones inside first, and then the bigger one to get the data readable. 

thus you set it up like this:
HDD ----> |encryption|--> Big Volume ---> |encryption| --> smaller volumes


This is a good idea, but I'm kind of wanting to stick with my own idea. I may end up doing this though. I guess what I'm asking is, is there anything that will destroy the drive if either the user cannot enter a password correctly or if the drive is used on an unauthorized machine, then what do I need to know to create it? I'm guessing I'd have to write some type of firmware/bootloader patch, so I'm guessing I need to know assembly and the anatomy of hard drives?

---

### Post by imachavel on 2012-01-09
> **Basher101 said:**
> you should use encryption, but not the normal way. Skilled people can tell you have an encrypted volume, but they cannot tell how many volumes you got inside that encrypted volume. So you create one big encrypted volume in which you create others, which, you encrypt too. This way, if anyone tried to decrypt the bigger one, all the data inside the smaller ones will get lost. You must encrypt the ones inside first, and then the bigger one to get the data readable. 

thus you set it up like this:
HDD ----> |encryption|--> Big Volume ---> |encryption| --> smaller volumes

where do you keep the encryption key? the usb drive??

---

### Post by Double.J on 2012-01-09
> **venom104 said:**
> This is a good idea, but I'm kind of wanting to stick with my own idea. I may end up doing this though. I guess what I'm asking is, is there anything that will destroy the drive if either the user cannot enter a password correctly or if the drive is used on an unauthorized machine, then what do I need to know to create it? I'm guessing I'd have to write some type of firmware/bootloader patch, so I'm guessing I need to know assembly and the anatomy of hard drives?

The unix command to securly erase a drive with dd is

```

dd if=/dev/urandom of=dev/sd[COLOR="Red"]X[/COLOR]

```

Where X is the designation of the drive to be erased. This doesn't just zero out a disk, but creates a random pattern of 1's and 0's across the surface of the disk - contrary to csi, there's no way back from this - you can reformat the drive and use again, you can surface scan, but the data doesn't exist. 

I've been told the fbi recommends a a 7 pass erase, I don't know about this - but I do know that a secure erase writes data acrosee the disk - the old data does not exist anymore.

In terms of instantly destroying the drive... C4? :D

---

### Post by Basher101 on 2012-01-09
> **imachavel said:**
> where do you keep the encryption key? the usb drive??

dunno that one, i guess it depends on the encryption software. You should look at the different encryption software around.

Anyway, even if you TOLD "them" the FIRST password for the BIGGER volume, all the data will be corrupted and therefore lost. Still one of the best protections. This way they cannot access your data digitally, nor physically (like removing the HDD from your computer).

> In terms of instantly destroying the drive... C4?
you got a lol from me.

regards

---

### Post by anewguy on 2012-01-10
Unless you are an electrical engineer and have all of the internal docs for a drive, you'll never write firmware for a drive - you need to get a good understanding of how a drive actually works to understand the difficulty, if not impossibility of doing what you want at the drive level.  Look at the drive password routines in some BIOS.  Password doesn't match - no access to drive.  But there are technical ways around most of these things.  If you have no idea of the command set to your drive, the internal commands on the drive, etc., are you are trying to bite off more than you can accomplish.

The people here are giving you suggestions based on operating system tools, as this is where this really needs to be handled.

Dave ;)

---

### Post by venom104 on 2012-01-10
> **gnu/mirow said:**
> The unix command to securly erase a drive with dd is

```

dd if=/dev/urandom of=dev/sd[COLOR=Red]X[/COLOR]

```Where X is the designation of the drive to be erased. This doesn't just zero out a disk, but creates a random pattern of 1's and 0's across the surface of the disk - contrary to csi, there's no way back from this - you can reformat the drive and use again, you can surface scan, but the data doesn't exist. 

I've been told the fbi recommends a a 7 pass erase, I don't know about this - but I do know that a secure erase writes data acrosee the disk - the old data does not exist anymore.

In terms of instantly destroying the drive... C4? :D

I have a few questions here. If I man dd, it gives me this, NAME
```

 dd - convert and copy a file

SYNOPSIS
       dd [OPERAND]...
       dd OPTION


``` Is this what you meant? Is this the right shell command? If this is a unix tool, I could easily set something up in the file that handles password authentication (what file(s) is(are) that?), BUT, BUT is there a way of securing my drive if someone rips it out without my knowledge, put's it in another machine (doesn't boot into ubuntu) and tried to access the drive with some type of software cracking program? How can I set it up to nuke the drive in this case?

---

### Post by mastablasta on 2012-01-10
> **venom104 said:**
> This is a good idea, but I'm kind of wanting to stick with my own idea. I may end up doing this though. I guess what I'm asking is, is there anything that will destroy the drive if either the user cannot enter a password correctly or if the drive is used on an unauthorized machine, then what do I need to know to create it? I'm guessing I'd have to write some type of firmware/bootloader patch, so I'm guessing I need to know assembly and the anatomy of hard drives?
 
 
what password are we talking about here? the user password? you can circumvent that by using livedisk or simply reseting the pasword.
 
if disk is encrypted with true crypt then using format would be useless as truecrypt is nearly impossible to break. unless maybe with a hardware hack of some sort.
 
>  
"In July 2008, several TrueCrypt-secured hard drives were seized from a Brazilian banker Daniel Dantas, who was suspected of financial crimes. The Brazilian National Institute of Criminology (INC) tried unsuccessfully for five months to obtain access to TrueCrypt-protected disks owned by the banker, after which they enlisted the help of the FBI. The FBI used dictionary attacks against Dantas' disks for over 12 months, but were still unable to decrypt them"
 
also explosives (as suggested) or some extremely hot fast burning chemical elements that is inert unless specificall< triggered would do the trick destroying the drive completely.

---

### Post by Double.J on 2012-01-10
> **venom104 said:**
> I have a few questions here. If I man dd, it gives me this, NAME
```

 dd - convert and copy a file

SYNOPSIS
       dd [OPERAND]...
       dd OPTION


``` Is this what you meant? Is this the right shell command? If this is a unix tool, I could easily set something up in the file that handles password authentication (what file(s) is(are) that?), BUT, BUT is there a way of securing my drive if someone rips it out without my knowledge, put's it in another machine (doesn't boot into ubuntu) and tried to access the drive with some type of software cracking program? How can I set it up to nuke the drive in this case?

Yes dd is a unix tool, common to all unix derrivatives. It copys bit for bit from one location to another and possesses the ability to convert.

The syntax is 
> dd if=input/directory of=out/put directory
We usually use this to copy and convert an iso to a usb stick, or copy an entire hard drive to an image file, but in the example I gave you, I list the /dev/urandom file as the input diretory and the hard drive as the output - dd will then use the /dev/urandom file as a random number generator and write to the disk.

I'm unclear what block size argument you would use following the command above. for backups I use -bs=64 to get a good balance of speed - I've seen other online guides use 512, that would be much faster still, but I suspect if it's data destruction, you'd want to go with bs=1... this would take a VERY long time for a large 2tb drive.

---

