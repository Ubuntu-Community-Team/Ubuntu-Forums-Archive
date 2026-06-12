---
title: "cant access ntfs filesystem..help plz..tried evrythin from forum..tht i found.."
date: 2008-11-28
forum: New to Ubuntu
---

### Post by ooopslucky on 2008-11-28
Dear people ,
i want to access NTFS filesystem from ubuntu intrepid that i recently installed..i screw up my windows n thts y i installed ubuntu..the windows was installed on this partition...tho now i cannot mount it on..n i want to access sum files on it..i cannot login into windows..cuz  virus logs me out evrytime..n now tht i have installed ubuntu..there is a conflict btween linux and windows..n thts y i get an error when trying to start windows..tht im missin hal.dll..however i learnt how access the FAT32 systems in the linux..only prob is the ntfs system

when i try to mount the volume thru Places i get this error below..

i tried to mount it thru terminal..but i needed root account...so i used sudo in front of the command..tho it still dint work..i already have the ntfs-3g installed as i have the latest ubuntu..it said..on the terminal tht the line im entering is not found in /etc/fstab file...

ny ideas on how to mount this volume...here below is the eroor i get when i try to mount it thru GUI..thru the PLACES toolbar..

----------------------------------
Cannot mount volume.(*blabla is not the real name of the volume)

Unable to mount the volume 'blabla'.

$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda5': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action : Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda5 /media/blabla -o force Or add the option to the relevant row in the /etc/fstab file : /dev/sda5/ /media/blabla ntfs-3g force 0 0
----------------------------------

thnx in advance.
Umair.

---

### Post by DiscoKiller on 2008-11-28
Sorry I can't be bothered reading this thread. I`ve tried to understand it but I dont expect to have to put this much effort into reading 'english'.
 
DK

---

### Post by eternalnewbee on 2008-11-28
> Dear people ,
i want to access NTFS filesystem from ubuntu intrepid that i recently installed..i screw up my windows n thts y i installed ubuntu..the windows was installed on this partition...tho now i cannot mount it on..n i want to access sum files on it..i cannot login into windows..cuz virus logs me out evrytime..n now tht i have installed ubuntu..there is a conflict btween linux and windows..n thts y i get an error when trying to start windows..tht im missin hal.dll..however i learnt how access the FAT32 systems in the linux..only prob is the ntfs system

when i try to mount the volume thru Places i get this error below..

i tried to mount it thru terminal..but i needed root account...so i used sudo in front of the command..tho it still dint work..i already have the ntfs-3g installed as i have the latest ubuntu..it said..on the terminal tht the line im entering is not found in /etc/fstab file...

ny ideas on how to mount this volume...here below is the eroor i get when i try to mount it thru GUI..thru the PLACES toolbar..

----------------------------------
Cannot mount volume.(*blabla is not the real name of the volume)

Unable to mount the volume 'blabla'.

$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda5': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action : Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda5 /media/blabla -o force Or add the option to the relevant row in the /etc/fstab file : /dev/sda5/ /media/blabla ntfs-3g force 0 0
----------------------------------

thnx in advance.
Umair.
I remember this. Try to start up windows and shutting it down normally. Then you should be good to go.

---

### Post by eternalnewbee on 2008-11-28
> Sorry I can't be bothered reading this thread. I`ve tried to understand it but I dont expect to have to put this much effort into reading 'english'.

My apologies my lord. (or would you prefer Your Highness?)

---

### Post by Bucky Ball on 2008-11-28
> **eternalnewbee said:**
> Try to start up windows and shutting it down normally. Then you should be good to go.

That should work. A clean *shutdown*, not restart. Don't ask me why.

---

### Post by NewJack on 2008-11-28
> **DiscoKiller said:**
> Sorry I can't be bothered reading this thread. I`ve tried to understand it but I dont expect to have to put this much effort into reading 'english'.
 
DK

Agreed, I got a headache after reading that too, but let me see if I can help.  

@OP- 

1- Ok, so your Windows had a virus so you installed Ubuntu.  Is that right?

2- When you installed Ubuntu, did you install it OVER Windows or did you make a separate partition for Ubuntu?  

2a- If you installed Ubuntu over Windows, then you can end here.  Your Windows install is gone.

2b- If you created a separate partition for Ubuntu, read on.

3- Now, Ubuntu should be able to read your Windows Partition.  Whether or not there is a virus on your Windows partition.  I don't think that would keep you from viewing it from Ubuntu, since it is a Windows virus it shouldn't affect Linux.

4- You could try and enter Window in Safe Mode and do a proper shutdown.

5- If all else fails, looking at the error message you posted below, you can open a Terminal and type the following from the command line: 

> mount -t ntfs-3g /dev/sda5 /media/blabla -o forceApparently, once you got the virus you were unable to properly shutdown Windows.

Hope this helps!

P.S.- When asking for help in the forums, please try and clearly and fully type your request for help.  It will go a long way in getting you help in the future.

---

### Post by Bucky Ball on 2008-11-28
> **NewJack said:**
> 

P.S.- When asking for help in the forums, please try and clearly and fully type your request for help.  It will go a long way in getting you help in the future.

Yes, the mobile phone message is not particularly condusive to us understanding what the heck your problem is. :-k :)

---

### Post by ooopslucky on 2008-11-28
sorry. i did not realise that. i cant shutdown the windows because I cannot access it anymore. I installed the ubuntu on a separate partition from the Windows directory in which I had installed the windows XP.

I had Windows XP in D:/ which is NTFS filesystem.

However when I got the virus, I could not log in the Windows, I used to get logged out, after multiple failed attempts, I installed Ubuntu on some other partition such as G:/.

After I installed Ubuntu. The windows system apparently the Windows was not working good with the GRUB loader because whenever I tried to enter the Windows, I got an error stating that the Windows is missing hal.dll.

This is worse than before because now I cannot even get to the Windows login screen to shut it down cleanly. This error also happened to me long back when I had Ubuntu installed, and when I removed it long back, the Windows at that time started working fine.

All my partitions are accessible right now because they are in the format of FAT32, however the D:/ partition is in NTFS and I cannot access it.

thank you guys,
Umair.

---

### Post by ooopslucky on 2008-11-28
thank you very much for your help. I used the command you gave me, though I put sudo in front of it, because in ubuntu I dont have all the privileges, as u might know.

It has worked fine because the log has been reset. The log about the unclean shutdown. Everythings fine now.

Thank you very much,
appreciated your help,
Umair.

---

### Post by PocketDog on 2008-11-28
I haven't been so emotional since I saw ET when I was twelve. I love you guys

---

### Post by Bucky Ball on 2008-11-29
Excellent news, ooopslucky! Could you mark your thread as 'solved' please from the Thread Tools drop down menu and welcome to the forums and Ubuntu.

You are now much more descriptive and understandable! \\:D/

---

### Post by reddyschintu on 2008-11-29
i could not get u clearly if u can please explain in detail

---

