---
title: "USB key"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-04-19
My friend wants to install Ubuntu on her comp without her family know about it. So she wants some arrangement done so that no one gets to know about her migration to Linux.

She wants the entire installaion done in the comp except grub. She wants when any one boots the comp it would normaly boot in to Windows without anyone geting any idea that there is another OS in the HDD. When ever she wishes to boot in to Ubuntu she will have to insert a USB pen drive and that will enable her to directly boot in to Ubuntu without going for Windows. 

I feel the boot sequence priority can be changed so that if the USB pen drive is present then it would boot first through that but beyond that I am not sure what we should do in the pen drive to make it boot from the other partition in the HDD that has Ubuntu ?

Can any one help ?

---

### Post by zemega on 2013-04-19
Well, instead of installing Ubuntu on the computer hard disk, where someone might be suspicious over missing/mismatch hard disk size, she has the option of installing it onto a USB drive or an external hard drive.

On the other hand, she can install Ubuntu on the comp. Remove the grub part. Install grub on a USB using unetbootin.

Note, if she formats a partition for ubuntu using ext3/4, Windows will not be able to access that partition voluntarily. Other user might realise the the changes in the partitions, well, not your average user though. If she use FAT or NTFS as the file system, people will be able to see the Ubuntu structure from Windows, thus its not longer a secret. So, if she really want to keep it a secret, installing it externally (USB, SSD, external hard disk) is better. If the computer is using BIOS, its pretty simple. If its UEFI, well that makes things some what harder.

---

### Post by DuckHook on 2013-04-19
Conceptually easily done, but I wish you hadn't gone into such detail, as I am not sure I'm comfortable advising on Linux by stealth. Could your friend not just have a frank conversation with her family, lay out her (very good) reasons for wanting to try it, and get where she wants by concensus? Here are the dangers:

1. She is talking about repartitioning. Always a dangerous exercise.
2. The partition will be visible to all Windows users who have at least an inkling of system knowledge.
3. Her "stealth" partition could very well set off Windows anti-malware alarm which is notorious for crying wolf when Linux is detected.
4. If she gets caught, it's a thousand times more serious in terms of relationship with her family.

This is life-advice and not technical advice, I know, but someone has to say it.

---

### Post by 3dmatrix on 2013-04-19
> **DuckHook said:**
> Conceptually easily done, but I wish you hadn't gone into such detail, as I am not sure I'm comfortable advising on Linux by stealth. Could your friend not just have a frank conversation with her family, lay out her (very good) reasons for wanting to try it, and get where she wants by concensus? Here are the dangers:

1. She is talking about repartitioning. Always a dangerous exercise.
2. The partition will be visible to all Windows users who have at least an inkling of system knowledge.
3. Her "stealth" partition could very well set off Windows anti-malware alarm which is notorious for crying wolf when Linux is detected.
4. If she gets caught, it's a thousand times more serious in terms of relationship with her family.

This is life-advice and not technical advice, I know, but someone has to say it.

Her family memebers are TOO non technical (technical illerates) and that is the main problem. Perhaps you have not come across such people. They are themselves too scared and make life hell for others too. She is afraid that for every lil prob in windows she (her adventure with Linux) will be held responsible.

Partitioning is never a difficult or scary thing i have been doing it since more than 10 years.

The partitions will certainly be Ext3/4 so no one can make out its presence, unless has some system knowledge which unfortunately no one in her family has.

So these issues are not a prob i just need tech advise regarding the USB pendrive.

---

### Post by 3dmatrix on 2013-04-19
> **zemega said:**
> 

On the other hand, she can install Ubuntu on the comp. Remove the grub part. Install grub on a USB using unetbootin.
.

I have tried installing it on USB pen drive but its not the same experience.
So it would be nice if you could kindly help me with UNETBOOTIN or somthing similar. What is this ?
Can it install grub in pendrive, if I use a boot repair disk ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) ?

---

### Post by pinballwizard on 2013-04-19
> **DuckHook said:**
> Conceptually easily done, but I wish you hadn't gone into such detail, as I am not sure I'm comfortable advising on Linux by stealth. Could your friend not just have a frank conversation with her family, lay out her (very good) reasons for wanting to try it, and get where she wants by concensus? Here are the dangers:

4. If she gets caught, it's a thousand times more serious in terms of relationship with her family.

This is life-advice and not technical advice, I know, but someone has to say it.

The whole thing smells.

---

### Post by zemega on 2013-04-19
I'm not an expert here, but since you plan to do this, its best if you ask the GRUB forum/mailing list. [https://lists.gnu.org/mailman/listinfo/help-grub](https://lists.gnu.org/mailman/listinfo/help-grub) .Unetbootin is just a popular program that allows you to boot from USB. You can load many things into Unetbootin, such as live Linux, the old DOS programs, and in some version Windows.

---

### Post by DuckHook on 2013-04-19
If my daughter installed something unknown to me on my computer and purposefully kept it from me by sneaking it onto my HDD without my knowledge or approval, my trust in her would take a beating from which it might never recover.

You got better advice just now than anything possible of the technical variety that you set out for. If others feel like advising further, that's their call. I've given you the best advice I know just now and have nothing with which to trump it.

---

### Post by mastablasta on 2013-04-19
otherwise simply during manual parittioning select to put grub on USB key and that should do it. you will then always need to stick USB in to get grub.

though it might be better to get install it to external drive.
pa
rittioning is nothing scary, but things can always go wrong. and since oyu mess with the disk data....

anyway** DuckHook **gave the best advice.

---

### Post by zemega on 2013-04-19
Here's a different advice perspective. Tell her to say along this line. Microsoft Windows and Office plus other stuff are not free and open. Ubuntu and Libreoffice and many other things are free. You want to walk the path of minimalism, or less spending or whatever you want to call it, and going with Microsoft is not the way. 

On another note, if its a desktop, you can just put in another harddisk in there and says, what ever happen to the Windows does not involves her harddisk and Ubuntu at all. Partition it to ext3/4. Then you can set up in Windows to recognise the boot to include Ubuntu. This way instead of using GRUB and cause panic to others, they will see Windows boot screen. And then maybe timeout is just 3 seconds, so it pass by quickly without them realising or need to choose any.

---

### Post by blackbird34 on 2013-04-19
Couldn't she (a) just get a cheap second hand computer of her own or (b) install Ubuntu on a big fat USB stick/drive that she could boot to? I agree with DuckHook, if it's not HER computer, there could be problems down the line...

Seeing as your idea is that she insert a USB stick on boot anyway (b) would not be much of a change.

---

### Post by 3dmatrix on 2013-04-20
Well, my dear friends, why trouble some one in her personal life ? She is a grown up person (rather among the elder ones in the family, not a kid) and in fact the computer belongs as much to her as it is to other members in the family. She asked for a technical help from me and i just wish to give her technical help. I am not interested in poking my nose in her family life. I know very well if i do not help her some one else will.

Moreover, there are millions of people who keep encrypted files or folders on their computer, what we are doing, is it not bigger way of doing that ?
There are so many softwares available that can make your personal folders hidden . . . . Why do we have passwords for everything starting from emails right up to login to linux. There are people who keep serarate accounts for different groups of people. There is some level of privacy that every one needs and if people close to you are not able to accept that then its their problem.

She could easily have two seperate HDD in that comp (without the knowledge of anyone) or have an external HDD (and keep hiding it in her wardrob) then what is the problem if she hides a small partition in that same HDD ?

Anyway my friends i was here for some technical help i am not here for relationship advises. So kindly do not waste my and your time.

Zemega : she is simply not interested in going in for arguments with people and as i said it is her and her family member's problem. I am not interested in interfering in any one's person life. So no need to explain so much to them why Linux is better or . . . . she can always find lots of resources on the net and read out to her family members, IF she really wishes to.

blackbird34 : buying a seperate comp is even worse in her case. As i wrote many times i do not wish to discuss her family prob here. 

mastablasta : i have never installed grub separate from the hdd where linux is installed and if that can be done then it would be perfect for this problem. Regarding partitioning, the way i deal with it, there should not be any problem. And in case of any problem, i know how to break the story to non-technical people.

---

### Post by C.S.Cameron on 2013-04-20
I can't see the potential problem with the family being worth the price of an external drive.
Why not do a full install to a flash drive or external hard drive.
Now a days, they are almost as fast as running from internal drive.
Especially if the computer has USB3.

---

### Post by pfeiffep on 2013-04-20
> **3dmatrix said:**
> My friend wants to install Ubuntu on her comp without her family know about it. So she wants some arrangement done so that no one gets to know about her migration to Linux.

She wants the entire installaion done in the comp except grub. She wants when any one boots the comp it would normaly boot in to Windows without anyone geting any idea that there is another OS in the HDD. When ever she wishes to boot in to Ubuntu she will have to insert a USB pen drive and that will enable her to directly boot in to Ubuntu without going for Windows. 

I feel the boot sequence priority can be changed so that if the USB pen drive is present then it would boot first through that but beyond that I am not sure what we should do in the pen drive to make it boot from the other partition in the HDD that has Ubuntu ?

Can any one help ?

When I tried installing to a USB stick I was successful, but really dis-satisfied with the speed and totally gave up using the usb stick.

This isn't exactly what you asked but here goes ......... I have had excellent success installing Ubuntu along with GRUB2 on a USB2 hard drive! The speed is almost as fast as the internal drive. 

I just did a quick check on Amazon under $60 for a 320GB.

---

### Post by 3dmatrix on 2013-04-20
Thanx for your suggestion. Her comp does not has USB 3 it has USB 2.
I would ask her if she would change her mind and go for an external HDD.
But i would personally like to try installing Grub on a usb pen drive and make it boot the Ubuntu partition in MY comp.
I wish to check how different it can be if Grub is installed on the same HDD.
Thanx again.

---

### Post by pfeiffep on 2013-04-20
> **3dmatrix said:**
> Thanx for your suggestion. Her comp does not has USB 3 it has USB 2.
I would ask her if she would change her mind and go for an external HDD.
But i would personally like to try installing Grub on a usb pen drive and make it boot the Ubuntu partition in MY comp.
I wish to check how different it can be if Grub is installed on the same HDD.
Thanx again.

My USB installation in on USB2 not 3. If the intent is to be clandestine then having nothing on the internal drive would be preferable:)

---

### Post by C.S.Cameron on 2013-04-20
If she is really intent on booting her own partition on the internal drive using grub on an USB, then when you get to partitioning use "Something else" and select the USB for location of the boot loader.

---

