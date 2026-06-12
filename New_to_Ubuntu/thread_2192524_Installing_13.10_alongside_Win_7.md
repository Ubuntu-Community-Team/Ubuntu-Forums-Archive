---
title: "Installing 13.10 alongside Win 7?"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by arushi8295 on 2013-12-08
I have been trying to install ubuntu 13.10 alongside win7 from the past 3 days.
The utter confusion comes in when i run the bootable usb and it gives me no option of installing ubuntu alongside win7. It says "no OS detected" and gives me 2 options of either erasing the disk and install ubuntu or "something else"........
I learned dat this is either bcoz i have 2 drives only(c: and d) or coz there is no free space allocated.....
I dont want to do the partitions myself coz it's risky and i am green at ubuntu installation.....
Wen i chose the "something else" option it showed 500 gb free space and that's the size of my HDD....why did it not detect my already installed win7?
I dont wanna give up......
Somebody pls help me......
note: I want to give ubuntu partition in d: drive so dat it doesn't interfere with win7 installed in c: drive...
thanks in advance

---

### Post by oldos2er on 2013-12-08
Moved to Absolute Beginners.

---

### Post by oldfred on 2013-12-08
Almost all Windows 7 installs use all 4 primary partitions.

Best to fully backup first.
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by amjjawad on 2013-12-08
Hello and welcome to Ubuntu Forums!

Few basic steps that you need to do before anything else:

1- Backup your important files/data
2- Please refer to #1
3- Check [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") for the downloaded ISO of Ubuntu that you have downloaded
4- Make sure to check your LiveUSB for errors before anything else and that can be done on the LiveUSB Menu - See:

[IMG]https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME?action=AttachFile&do=get&target=2.png[/IMG]

Please, choose "Check Disc for defects" - better safe than sorry. Don't waste your time with installation and take any risk of a bad installation unless you check this. Won't take much of your time :)

5- Always choose "Try without installation"
6- Run GParted
7- Check how many 'Primary Partitions' do you have?

If you have 4 Primary Partitions, then you can NOT install Ubuntu - you need to get rid of one partition (by saving whatever data saved on that partition on an external HDD for example OR burning the data to CD/DVD) and then carry on

If you have LESS than 4 Primary Partitions (I doubt that in your case), then you need to prepare the needed partitions for your Ubuntu Installation - from here: [https://help.ubuntu.com/12.04/installation-guide/i386/index.html](https://help.ubuntu.com/12.04/installation-guide/i386/index.html) check: [https://help.ubuntu.com/12.04/installation-guide/i386/partitioning.html](https://help.ubuntu.com/12.04/installation-guide/i386/partitioning.html)

Usually, you need (/) which is Root and (swap) partition. It is highly recommended to have (/home) partitions too.

See: [http://askubuntu.com/questions/142695/what-are-the-pros-and-cons-of-having-a-separate-home-partition](http://askubuntu.com/questions/142695/what-are-the-pros-and-cons-of-having-a-separate-home-partition)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

> **arushi8295 said:**
> I have been trying to install ubuntu 13.10 alongside win7 from the past 3 days.
The utter confusion comes in when i run the bootable usb and it gives me no option of installing ubuntu alongside win7. It says "no OS detected" and gives me 2 options of either erasing the disk and install ubuntu or "something else"........
I learned dat this is either bcoz i have 2 drives only(c: and d) or coz there is no free space allocated.....

This means you have already 4 Primary Partitions and you can NOT carry on unless you get rid of one of these - check above.


>  I dont want to do the partitions myself coz it's risky and i am green at ubuntu installation.....
If you ask me, I would suggest to take 'more control' over the installation process and 'learn' how to use 'Something Else'. This will give you more control and soon enough, you will learn how to install any Ubuntu based system. This is how I became expert with installing Ubuntu.

> Wen i chose the "something else" option it showed 500 gb free space and that's the size of my HDD....why did it not detect my already installed win7?

Explained above.

>  I dont wanna give up......
+1
That is the spirit, keep it up!

>  Somebody pls help me......
I hope I just did :)

>  note: I want to give ubuntu partition in d: drive so dat it doesn't interfere with win7 installed in c: drive...
That would be the easiest way:

1- Make sure to backup Partition "D:"
2- Remove all the Temp Files on your machines - you can use CCleaner or the normal way to remove the temp files
3- Do a Disk Defragement
4- Reboot 
5- Boot from the LiveUSB
6- Run GParted
7- Make sure you are looking at Partition "D:" which will NOT be named as "D: but most likely will be "/dev/sda3".
8- You can delete it and create the needed partitions for Ubuntu - check above
9- Once done from GParted, you can start the installation 
10- Choose 'Something Else'

You can use Drive "C:" after shrinking it but that is a bit of a headache. If you are interested, I can explain that but better to go for the above plan because it is the easiest. After all, one partition 'must' be deleted to carry on.

By the way, when you delete "/dev/sda3" which is Partition "D:" in Windows, you need to create an Extended Partition and inside that, you need to create 3 'Logical' Partitions:

/dev/sda5 = for root
/dev/sda6 = for home
/dev/sda7 = for swap


> thanks in advance
You most welcome!
Please do ask if you are in doubt!

Thank you!

---

### Post by fantab on 2013-12-09
Make sure your Windows is actually shutdown and not 'hibernating'. Hibernating Windows can also issue a similar error, like 'no os detected'.

---

### Post by amjjawad on 2013-12-09
> **fantab said:**
> Make sure your Windows is actually shutdown and not 'hibernating'. Hibernating Windows can also issue a similar error, like 'no os detected'.

Actually, it can lead to a much worse issue :)
I had Input/Output Error, GParted was showing ZERO Partitions and I was unable to do anything so had to use a Windows 7 disc, fixed MBR and then logged in to Windows:

1- Removed the temp files
2- Scan Disc
3- Defragement
4- Disc Manager to check the partitions
5- Booting from the LiveUSB of Xubuntu 12.04.3
6- Run GParted
7- Everything was perfect
8- Started to create the needed partitions for my Linux System

So, HUGE +1 for this suggestion!!!

Thank you :)

---

### Post by Impavidus on 2013-12-09
In case you want to share data between Ubuntu and Windows (for example, if you handle all your email on Ubuntu but want to process attached MS office documents on Windows, or you want to share your firefox profile with all bookmarks between both systems) it's best to add another partition, type ntfs, for shared data. It's recommended to not put that shared data on the Windows C partition. So that would make:
- root, also knows as / (but not /root), type ext4
- /home, type ext4 (optional)
- shared data, type ntfs (optional)
- swap, type swap
The sizes of these partitions are a matter of personal preference, how you use your computer, and the amount of disk space you have available for Ubuntu.

---

### Post by amjjawad on 2013-12-09
> **Impavidus said:**
> In case you want to share data between Ubuntu and Windows (for example, if you handle all your email on Ubuntu but want to process attached MS office documents on Windows, or you want to share your firefox profile with all bookmarks between both systems) it's best to add another partition, type ntfs, for shared data. It's recommended to not put that shared data on the Windows C partition. So that would make:
- root, also knows as / (but not /root), type ext4
- /home, type ext4 (optional)
- shared data, type ntfs (optional)
- swap, type swap
The sizes of these partitions are a matter of personal preference, how you use your computer, and the amount of disk space you have available for Ubuntu.

[ATTACH=CONFIG]248452[/ATTACH]

This another good advice :)
Attached is my partitions which I created just yesterday. These were a mess before but had to clean up the mess and keep two systems only rather than 4 or not sure how many I had on that machine!

---

### Post by mastablasta on 2013-12-09
actualyl there is no need to remove any partition. but one of those (for example D partition) can be converted into extended using mini partition tool. then you just shrink it and in the new created space install Ubuntu

---

### Post by amjjawad on 2013-12-09
> **mastablasta said:**
> actualyl there is no need to remove any partition. but one of those (for example D partition) can be converted into extended using mini partition tool. then you just shrink it and in the new created space install Ubuntu

From experience, and from a very recent one (less than 24hours), I'd advice to follow the steps I explained on my long post earlier and make sure to do everything inside Windows before you even use GParted. Better safe than sorry ;)

As long as these are 'Windows' Partitions, better let Windows handle that job. Again, speaking of experience, I tried to play with GParted and it gave me a nasty error so had to restore MBR using Windows Disc, login to Windows, did what I explained on my previous post and then used GParted to create the partitions then installed.

As long as there is Windows installed, one needs to be careful more. If Windows is not installed, I am one of those who feel like FREE Bird and do whatever fun to install Linux in less than 5 mins without worrying about anything.

---

### Post by codenine75a on 2013-12-09
> **oldfred said:**
> Almost all Windows 7 installs use all **4 primary partitions**.

Best to fully backup first.
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

that is all you can have is 4 primary partitions.  That is why LVM was made.

---

### Post by arushi8295 on 2013-12-12
Thanks a lot for guiding.......successfully installed ubuntu 13.10.....
Now i have another issue...
I am not able to change the screen brightness in the power "brightness and lock options" and not even manually using keyboard keys......what cud be the problem ?
also, do i need antivirus for this OS ?
How do i turn the firewall on?
Thanks a lot....: )

---

### Post by arushi8295 on 2013-12-12
Thanks a lot for guiding.......successfully installed ubuntu 13.10.....
Now i have another issue...
I am not able to change the screen brightness in the power "brightness  and lock options" and not even manually using keyboard keys......what  cud be the problem ?
also, do i need antivirus for this OS ?
How do i turn the firewall on?
Thanks a lot....: )

---

### Post by amjjawad on 2013-12-12
> **arushi8295 said:**
> Thanks a lot for guiding.......successfully installed ubuntu 13.10.....
Good, well done :)

>  also, do i need antivirus for this OS ?
You alraedy have the strongest Anti-Virus on the world, that is your Linux Kernel so the short answer is NO. You do not need any anti-virus :)

---

### Post by fantab on 2013-12-12
> **arushi8295 said:**
> 
I am not able to change the screen brightness in the power "brightness  and lock options" and not even manually using keyboard keys......what  cud be the problem ?
also, do i need antivirus for this OS ?
How do i turn the firewall on?


Turning on the firewall is very simple, however you will have to configure it as well.
```
sudo ufw enable
```

To configure UFW (Uncomplicated Firewall) read below:
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/UFW?action=show&redirect=Uncomplicated_Firewall_ufw)

UFW has a GUI front end called [**GUFW**]("https://help.ubuntu.com/community/Gufw").

Regarding Antivirus you'll get good info @ [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus).
More Info on Ubuntu Security..[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security).

Also I suggest you start a new thread for your Graphics and keyboard issue, and any other issue... the objective of this thread seems achieved.

---

