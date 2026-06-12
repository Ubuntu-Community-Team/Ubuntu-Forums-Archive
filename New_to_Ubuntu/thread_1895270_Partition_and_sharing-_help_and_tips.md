---
title: "Partition and sharing- help and tips"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by 1childish1 on 2011-12-14
Well, I am testing out Ubuntu and Windows 7 installations on a VM (VBox)

So what I did was I first created a 90 GB virtual disk and used GParted to make a Primary partition for Win7 [NTFS] (and Ubuntu I think) and an Extended with a Logical one for data [NTFS]. I then installed Win 7 Ultimate in the primary and then Ubuntu 11.10 Alongside Windows (I couldn't install it in a Primary partition for some reason). I also edited the GRUB settings to make Windows default choice when boot up.

What I want to do is give equal amounts to both OS (20 GB each) and the rest for the Logical "data" partition... the problem I am having is that I think Windows used up the 40 GB Primary partition and Ubuntu installed in a Logical partition of 20 GB, so how do I make it so they both have 20 GB?

Also, I have tested to see if I can use the NTFS data partition and it seems to work, the only thing is that whenever I make a new empty document in Ubuntu and make it a ".txt", in Windows it creates the ".txt" file and a ".TXT~" file along with it. How do I fix that? I have read something about user mapping (ntfs-3g.usermap) but I have no clue how to do it correctly or what it's really for, I've read something about it fooling Windows into thinking that the files made by Ubuntu were made by Windows.

My end goal here is to have Windows with 20 GB, Ubuntu with 20 GB and share the files between them without any corruption or problems (if possible). That way, I just have all my documents (like music) in 1 folder and am able to use it with both OS. And how do I make it so anyone who uses my Ubuntu profile can't see what I have in my Windows partition or certain folders in my "Data" partition?

Sorry if I made too many questions, but I figured it's better to ask them in 1 post than in many different ones. Thanks in advance!!

---

### Post by Megaptera on 2011-12-14
A useful guide to a Windows & Ubuntu shared data partition here:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Hope this is a start anyway ...

---

### Post by cortman on 2011-12-14
Try this thread too. [http://ubuntuforums.org/showthread.php?t=1888149]("http://ubuntuforums.org/showthread.php?t=1888149")

---

### Post by 1childish1 on 2011-12-15
> **Megaptera said:**
> A useful guide to a Windows & Ubuntu shared data partition here:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Hope this is a start anyway ...

Thanks!!! This is what I was looking for!! I tried it out and it seems to be working fine!!!

> **cortman said:**
> Try this thread too. [http://ubuntuforums.org/showthread.php?t=1888149](http://ubuntuforums.org/showthread.php?t=1888149)

I'm looking at this thread as well... thanks for sharing!!

Well, that solved my major problem, now all I need is to know how to install Ubuntu properly to a Primary partition, or must it only have a Primary for Windows and then a Logical for Ubuntu? And something I honestly don't get is the swap partition, do I create it myself or do I let Ubuntu handle that?

Thanks again!!

---

### Post by cortman on 2011-12-15
Re .txt~ files: depending what program you're using to create the file, that's a backup file that the program automatically creates. Emacs is one program that comes to my mind, that does that. Nods if you're already using emacs!
I would leave your Ubuntu installation as it is, and shrink the Windows partition down to create 20 gig of free space for your NTFS "my stuff" partition.
I would do this with Windows, to ensure it's visible to Windows. Go Conrol Panel-Administrative Tools-Computer Management-Disk Management. Find your Windows partition, right click, and select "Shrink volume". Then you can use the same tool to create a new 20 gig NTFS partition.
Ubuntu will find the new partition automatically.
Hope this helps.

---

### Post by Ms. Daisy on 2011-12-15
> **1childish1 said:**
> Well, that solved my major problem, now all I need is to know how to install Ubuntu properly to a Primary partition, or must it only have a Primary for Windows and then a Logical for Ubuntu? And something I honestly don't get is the swap partition, do I create it myself or do I let Ubuntu handle that? If you burn an Ubuntu installation iso and install from that, it will create the swap partition itself.

---

### Post by 1childish1 on 2011-12-15
> **cortman said:**
> Re .txt~ files: depending what program you're using to create the file, that's a backup file that the program automatically creates. Emacs is one program that comes to my mind, that does that. Nods if you're already using emacs!
I would leave your Ubuntu installation as it is, and shrink the Windows partition down to create 20 gig of free space for your NTFS "my stuff" partition.
I would do this with Windows, to ensure it's visible to Windows. Go Conrol Panel-Administrative Tools-Computer Management-Disk Management. Find your Windows partition, right click, and select "Shrink volume". Then you can use the same tool to create a new 20 gig NTFS partition.
Ubuntu will find the new partition automatically.
Hope this helps.

I used 2 methods and they both gave me the same result:
1) gedit- opened it up and saved a .txt file with Windows extension.
2) right-click > create new document > empty document- I then renamed it with a .txt extension and edited with gedit as well. They both gave me the .txt~ file in Windows
So, is there a way to work around that so I don't see both files?

Also, I created a .txt file from windows and edited it with gedit in ubuntu, it all seemed fine, but when I opened it up with Windows, it DID save the text but in a weird way (I made a space pressing <enter> in ubuntu and it made no space in Windows).

I'm just worried that this could happen with any other file (not only text files) and that's what I want to avoid. I once edited a text file in my actual computer using the BT 5 live CD and it corrupted such text files that I had to use chkdsk to delete them files.

And I used GParted to resize my Windows partition and added more space to my data partition. It worked fine!

Thanks!

> **Ms. Daisy said:**
> If you burn an Ubuntu installation iso and install from that, it will create the swap partition itself.

Thanks for the info!! I also see that if I make it encrypted (when asked) that every time at boot up, it shows:

"The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
 Continue to wait; or Press S to skip mounting or M for manual recovery"

I have searched about it and I found that it's apparently a timing issue and nothing else is wrong. However, I've read somewhere that with such swap encryption, you can't hibernate Ubuntu. Is that true? Should I opt for encryption or is it not necessary? 

Thank you all for helping me out!!

And sorry for all the questions... I'm just a little too careful when it comes to my computer. I just want to do this right with little or no regrets or errors (if possible). :P

---

### Post by Megaptera on 2011-12-16
> **1childish1 said:**
> Thanks!!! This is what I was looking for!! I tried it out and it seems to be working fine!!! 

You're welcome!

---

### Post by Ms. Daisy on 2011-12-16
> **1childish1 said:**
> 
Thanks for the info!! 
You're welcome.

> **1childish1 said:**
>  I also see that if I make it encrypted (when asked) that every time at boot up, it shows:

"The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
 Continue to wait; or Press S to skip mounting or M for manual recovery"

I have searched about it and I found that it's apparently a timing issue and nothing else is wrong. However, I've read somewhere that with such swap encryption, you can't hibernate Ubuntu. Is that true? Should I opt for encryption or is it not necessary? 
Encrypting swap & home are entirely a personal decision.  Ask yourself what you are storing on the computer. If you'll have information that's valuable to thieves, then you may want to encrypt.  But if you're just storing music & photos, then there may be less need for encryption (depending of course on what you've got photos of LOL).  Then you must weigh this against the risks of encryption. If you lose the password then your data is lost (otherwise what would be the point of encryption).  [This]("https://help.ubuntu.com/community/EncryptedHome") will get you started with understanding encryption.

I'm afraid I don't know if it affects hibernation.

---

### Post by cortman on 2011-12-16
> **1childish1 said:**
> I used 2 methods and they both gave me the same result:
1) gedit- opened it up and saved a .txt file with Windows extension.
2) right-click > create new document > empty document- I then renamed it with a .txt extension and edited with gedit as well. They both gave me the .txt~ file in Windows
So, is there a way to work around that so I don't see both files?

Also, I created a .txt file from windows and edited it with gedit in ubuntu, it all seemed fine, but when I opened it up with Windows, it DID save the text but in a weird way (I made a space pressing <enter> in ubuntu and it made no space in Windows).

I'm just worried that this could happen with any other file (not only text files) and that's what I want to avoid. I once edited a text file in my actual computer using the BT 5 live CD and it corrupted such text files that I had to use chkdsk to delete them files.

We're all glad to help! It's wise to make sure you understand what you're doing with computers, before diving right into it.

Gedit creates backup files too (*.txt~). To disable that open gedit and go >edit - preferences - editor tab, and uncheck "create a backup copy of files before saving". You may want also to check the "autosave" box beneath it too.
I don' know of many other programs that create this type of backups.

---

### Post by 1childish1 on 2011-12-16
> **Ms. Daisy said:**
> You're welcome.


Encrypting swap & home are entirely a personal decision.  Ask yourself what you are storing on the computer. If you'll have information that's valuable to thieves, then you may want to encrypt.  But if you're just storing music & photos, then there may be less need for encryption (depending of course on what you've got photos of LOL).  Then you must weigh this against the risks of encryption. If you lose the password then your data is lost (otherwise what would be the point of encryption).  [This]("https://help.ubuntu.com/community/EncryptedHome") will get you started with understanding encryption.

I'm afraid I don't know if it affects hibernation.

Thanks again for the link!! I think I'll just not use encryption... don't really have anything anyone would like (including my pictures LOL).

> **cortman said:**
> We're all glad to help! It's wise to make sure you understand what you're doing with computers, before diving right into it.

Gedit creates backup files too (*.txt~). To disable that open gedit and go >edit - preferences - editor tab, and uncheck "create a backup copy of files before saving". You may want also to check the "autosave" box beneath it too.
I don' know of many other programs that create this type of backups.

I tried the solution and it did work!! However, I'm still confused about it no making the space whenever I edit a Windows created text file. It seems that no matter what encoding I save the text file in Windows (ANSI, Unicode, UTF-8, etc.) whenever I edit it with Ubuntu and make a space (press the "enter" key), that space doesn't show up in Windows since it puts everything in just one line. But when I check it back with Ubuntu, it reads normally with spaces and everything! Is there something wrong with the encoding or is that something unavoidable? Thank you very much again!!

---

### Post by cortman on 2011-12-17
> **1childish1 said:**
> Thanks again for the link!! I think I'll just not use encryption... don't really have anything anyone would like (including my pictures LOL).



I tried the solution and it did work!! However, I'm still confused about it no making the space whenever I edit a Windows created text file. It seems that no matter what encoding I save the text file in Windows (ANSI, Unicode, UTF-8, etc.) whenever I edit it with Ubuntu and make a space (press the "enter" key), that space doesn't show up in Windows since it puts everything in just one line. But when I check it back with Ubuntu, it reads normally with spaces and everything! Is there something wrong with the encoding or is that something unavoidable? Thank you very much again!!

Your welcome! It's a pleasure to help, especially people who are eager and willing to learn!

If you're opening the text file with Notepad in Windows, you're right things like line breaks won't show up. Notepad just lumps everything together when opening any text file not created with it.
For instance, I used to do some Java programming in Windows. I used Notepad++, which allows you to easily insert line breaks and tabs. If I opened one of my files in Notepad, it was just a huge 1 or two line mess.
If you want to edit text files for any purpose in Windows, I would highly recommend forgetting Notepad and downloading and using Notepad++. A terrific, solid little program, and completely free as well.

---

### Post by 1childish1 on 2011-12-17
> **cortman said:**
> Your welcome! It's a pleasure to help, especially people who are eager and willing to learn!

If you're opening the text file with Notepad in Windows, you're right things like line breaks won't show up. Notepad just lumps everything together when opening any text file not created with it.
For instance, I used to do some Java programming in Windows. I used Notepad++, which allows you to easily insert line breaks and tabs. If I opened one of my files in Notepad, it was just a huge 1 or two line mess.
If you want to edit text files for any purpose in Windows, I would highly recommend forgetting Notepad and downloading and using Notepad++. A terrific, solid little program, and completely free as well.

Thanks once again!! I tried using Notepadd++ and I found no problems!! I can now (and will) format my laptop and install Windows and Ubuntu (I will make a back-up first, obviously)!!

Thank you all for the help given, I've never would have done it without any of you guys!! I'm just so happy that people are willing to help newbies like me in understanding Ubuntu. Thanks once again for your patience and input!

=P

---

