---
title: "Problems with Lubuntu 12.04.4 update; User present files and settings do not!"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by Esalybz on 2014-04-07
Hi all,

I have two old laptops running (perfectly until now) Lubuntu 12.04; I use one for professional uses (text, spreadsheets, email and basic internet navigation) and the other I dedicate to personal use.

As said before, both laptops (from different brands) were running perfectly until the last software update (now it says is Lubuntu 12.04.4). With this update, the user is there, but when I log in, all my information and settings have disappeared. The wallpaper is gone, my email (thunderbird) is present but empty (no accounts). Also my browser (Firefox) is empty (lost all my saved links as well as my certificates) and in addition to that I have lost all my files (*.odt; *.pdf; et alia).

The (not so) funny thing is that I think all the information is in the disk; it is just that it doesnt display the info corresponding to the user login. 

I think that after the update, the system does not correlate the files and settings with the user, probably because I think the user privileges has beed downgraded with the update. 

I have tried booting in safe mode; booting a previous version; checking the disk; etc. nothing seems to work. I just have now a brand new installation, but the info and settings are still there, I know this because of the space of the disk.

And this has happened in my two laptops, with different hardware, and the only common link that this has happened after the last update.

Can you give me any guidance on this?

Thanks so much in advance!

---

### Post by claracc on 2014-04-07
Lubuntu 12.04 has reached its end of support life. As it shares ubuntu repositories from 12.04 release, part of your software will receive automatic security updates but for software packages related only to lubuntu as lxde desktop you haven't received and won't receive any update anymore. Perhaps the removal of specifically lubuntu repositories from server would be the cause you have lost your files?

Some people recommends to add the lxle ppa in order to have a "supported" lubuntu release, or upgrade to 13.10 or 14.04.

---

### Post by sudodus on 2014-04-07
Welcome to the Ubuntu Forums :-)

Lubuntu 12.04 has passed end of life. Unlike standard Ubuntu, Xubuntu and Kubuntu, it had no long time support. The only current version of Lubuntu is 13.10, and in a couple of weeks the new 14.04 LTS will be released, where Lubuntu will get long time support for the first time.

There may be problems with some desktop package that is not maintained for Lubuntu 12.04. If you can run the computer in text mode or maybe as root via recovery mode, you might be able to install xubuntu-desktop and log in to Xubuntu instead of Lubuntu.

```
sudo apt-get install xubuntu-desktop
``` If you run as root you need no ***sudo***

-o-

If the files are there, you might also be able to find them when you boot from a live CD/DVD/USB drive, for example a Lubuntu or Xubuntu install drive, and mount the internal drive and view, copy, backup the files (and groups of files in directory trees).

---

### Post by Impavidus on 2014-04-07
+1 to claracc, but first you want your files back. Did your have a separate home partition? Maybe it wasn't properly mounted. This could cause all kinds of problems. Have you checked the contents of /lost+found or /home/lost+found? They contain files leftover from repairing a damaged file system. What do these terminal commands return```
ls -ld $HOME
sudo parted -l
mount
```Just guessing here, this isn't a very well known problem.

---

### Post by Esalybz on 2014-04-07
Gracias Claracc,

I understand that you suggest to install the lxle repository; but will that recover my files and settings? I have no objection to swap to lxle, but I woud like to be sure that this change will not ruin my files. Otherwise, I rather search for the files in the disk with some forensic software and once I recover my files, then I can take that venue.

More opinions wellcome!

---

### Post by Esalybz on 2014-04-07
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Lubuntu 12.04 has passed end of life. Unlike standard Ubuntu, Xubuntu and Kubuntu, it had no long time support. The only current version of Lubuntu is 13.10, and in a couple of weeks the new 14.04 LTS will be released, where Lubuntu will get long time support for the first time.

There may be problems with some desktop package that is not maintained for Lubuntu 12.04. If you can run the computer in text mode or maybe as root via recovery mode, you might be able to install xubuntu-desktop and log in to Xubuntu instead of Lubuntu.

```
sudo apt-get install xubuntu-desktop
``` If you run as root you need no ***sudo***

-o-

If the files are there, you might also be able to find them when you boot from a live CD/DVD/USB drive, for example a Lubuntu or Xubuntu install drive, and mount the internal drive and view, copy, backup the files (and groups of files in directory trees).

Thank you Sudodu,

In fact xubuntu was one of the first distros I tried years ago as an alternative to the standard Ubuntu which was very heavy for my old and venerable laptops. But Xubuntu seemed to be as heavy as the standard Ubuntu, that is why I decided to swap to Lubuntu with excellent result until now.

I tried yesterday with a live cd, but I wasn't able to check the contents of the disk; it was displaying basically the same than when I login with my user name, but I am not big expert on this type of task but the contrary. 

Just in case I did not explain myself too well on my first post, the sequence in both laptops have bee this:

1.- System workin well
2.- System updates
3.- Relogin
4.- Same user, same password
5.- My files are not there any more, neither my settings and programs
6.- But the space of these files is still occupied in the disk; it is just that i have no access to them
7.- Why being the same user, I have no access, its my problem.
8.- This has happened in my two laptops with 24 hours of difference; different laptops with different hardware
9.- Finally, i think my user permits have been downgraded; I think this can be a key parameter.

Is there a way to scale my permits to the highest level allowing me access to all the files in the disk? Perhaps this will allow me to retrieve my data and settings.

Thanks you all for your help

---

### Post by sudodus on 2014-04-07
> **Esalybz said:**
> Thank you Sudodu,

In fact xubuntu was one of the first distros I tried years ago as an alternative to the standard Ubuntu which was very heavy for my old and venerable laptops. But Xubuntu seemed to be as heavy as the standard Ubuntu, that is why I decided to swap to Lubuntu with excellent result until now.

While Lubuntu has an ultra light desktop environment, Xubuntu is medium light, still much lighter than standard Ubuntu, but obviously too heavy for your computers.
> 
I tried yesterday with a live cd, but I wasn't able to check the contents of the disk; it was displaying basically the same than when I login with my user name, but I am not big expert on this type of task but the contrary. 

Just in case I did not explain myself too well on my first post, the sequence in both laptops have bee this:

1.- System workin well

- For how long? An hour, a day, a month, a year?

- Is there any backup of your personal files?
> 
2.- System updates
3.- Relogin
4.- Same user, same password
5.- My files are not there any more, neither my settings and programs

As stated before by *Impavidus*, this is *not* a well known problem.
> 
6.- But the space of these files is still occupied in the disk; it is just that i have no access to them
7.- Why being the same user, I have no access, its my problem.
8.- This has happened in my two laptops with 24 hours of difference; different laptops with different hardware
9.- Finally, i think my user permits have been downgraded; I think this can be a key parameter.

Is there a way to scale my permits to the highest level allowing me access to all the files in the disk? Perhaps this will allow me to retrieve my data and settings.

Thanks you all for your help

If you raise your privileges using sudo (before the command) and gksudo for GUI programs, you get top permissions, and can 'see all files and do what you want with them'. This can be done from the installed system (if it works properly) and it can be done from a live system (booted from CD).

---

### Post by Esalybz on 2014-04-07
Thanks again sudodus

Replying to your questions:

- The system was working well before the update for more than a year. After the update, the system malfunctioned almost instantly (just after reboot).

- There are no backup copies from my personal files (yes, I know.....). The info potentially lost is not super-critical, mainly interesting pdfs that I collected over the years related to my work. These I think I could recover with a phorensic tool in a worst case scenario, and I dont need them for my day to day work. The real important data I keep in a NAS centralized and adequately backed up. But I would not like to go the hard way, if I can sort the issue typing a couple of commands. As well, my purpose posting this is to warn the community about this malfunction on the update process from 12.04 to 12.04.4 in Lubuntu. Folks, backup everything before going through this update!

To me it seems that the system is considering me something like a new user after the update, despite I am the same user with same password, and that is why it doesnt displays my files and settings to me.

I will try the sudo path first. Second option will be phorensic recover. Once recovered, I will try the third one (lxle repository) and I will post the outcome.

Thanks to all the community!

---

### Post by sudodus on 2014-04-07
This problem might be because Lubuntu 12.04 end of life was October 2013, half a year ago. But still, it is hard to understand how it could turn out like that. I was running Lubuntu 12.04 is a few computers and converted to Xubuntu to get a longer life. I have had no problems with user IDs or your kind of loss of data.

The last resort would be ***PhotoRec*** to recover those files, but in that case I recommend strongly, that you do not use the drive in the meantime, because you might overwrite the data sitting without any pointer to it.

Did you check in the **.Trash*** and **lost+found** directories?

---

