---
title: "USB Flash Drive Format - Need Help"
date: 2009-05-24
forum: Philippine Team
---

### Post by Johnaray on 2009-05-24
Hi Guys,

This time my Flash drive got infected with a RECYCLE Folder and a Autorun.inf file. ( Thanks to INTERNET CAFES )

Unfortunately, my PC which has a Licensed Winxp SP2 was Infected as usual and everytime I plugged a USB on the Computer it infect the Flash Drive. ( I consider reformatting my PC but activating it need me to connect to internet as usual but I only have a VERY Slow internet connection Thanks to GLOBE VISIBILITY USB, good only for reading email...sometimes)

Then I have my ever reliable PC which has a SUSE Linux 10.5 installed. I plugged the USB and I was able to read contents (Thank GOD I thought my important files was gone) but my problem is Im not able to delete the RECYCLE Folder and Autorun.inf

I haven't able to install a UBUNTU on that PC since my CD/DVD Rom was only able to read DVD but unable to read CD's (huhuhuhu pity me) 

Could anybody help me please! could I format the flash drive using Sudo code :D

Thanks in advance 

Brb

Johnaray

---

### Post by whoop on 2009-05-24
[http://ubuntuforums.org/showthread.php?t=700132](http://ubuntuforums.org/showthread.php?t=700132)

---

### Post by dodimar on 2009-05-24
> **Johnaray said:**
> Hi Guys,

This time my Flash drive got infected with a RECYCLE Folder and a Autorun.inf file. ( Thanks to INTERNET CAFES )

Unfortunately, my PC which has a Licensed Winxp SP2 was Infected as usual and everytime I plugged a USB on the Computer it infect the Flash Drive. ( I consider reformatting my PC but activating it need me to connect to internet as usual but I only have a VERY Slow internet connection Thanks to GLOBE VISIBILITY USB, good only for reading email...sometimes)

Then I have my ever reliable PC which has a SUSE Linux 10.5 installed. I plugged the USB and I was able to read contents (Thank GOD I thought my important files was gone) but my problem is Im not able to delete the RECYCLE Folder and Autorun.inf

I haven't able to install a UBUNTU on that PC since my CD/DVD Rom was only able to read DVD but unable to read CD's (huhuhuhu pity me) 

Could anybody help me please! could I format the flash drive using Sudo code :D

Thanks in advance 

Brb

Johnaray

You can actually call a number (Philippines) for microsoft. It's an automated system that will give you the activation code after you answer some questions..

Back up your files from that flash drive then format that drive, that might work..

BTW, don't blame INTERNET CAFES in general...

---

### Post by Johnaray on 2009-05-24
> **whoop said:**
> [http://ubuntuforums.org/showthread.php?t=700132](http://ubuntuforums.org/showthread.php?t=700132)


Thanks whoop, will definitely gonna read it. Thanks again dude.

@dodimar, thanks for the reply as well. I guess its about time for me to part ways with Window$... since my brain cells are about to tell me to learn more on LINUX :D

About the INTERNET CAFES... well lets say that Im not in good luck when renting Internets on some Internet cafes since this is the 20th time I take home a FREE VIRUS on my flash drive :D and again infect my PC...hope I won't suffer the nth time of being infected from a Internet Cafe otherwise its a big SHAME ON ME! :D

Again Thanks a lot and if there are any suggestions, please feel free to advise me. Thanks again

---

### Post by dodimar on 2009-05-24
> **Johnaray said:**
> Thanks whoop, will definitely gonna read it. Thanks again dude.

@dodimar, thanks for the reply as well. I guess its about time for me to part ways with Window$... since my brain cells are about to tell me to learn more on LINUX :D

About the INTERNET CAFES... well lets say that Im not in good luck when renting Internets on some Internet cafes since this is the 20th time I take home a FREE VIRUS on my flash drive :D and again infect my PC...hope I won't suffer the nth time of being infected from a Internet Cafe otherwise its a big SHAME ON ME! :D

Again Thanks a lot and if there are any suggestions, please feel free to advise me. Thanks again

Hahaha.. I am going to ditch my XP next month.. 

And everytime I am forced to use USB drives on an iCafe, I never open it on my Windows system without scanning it first or reformatting it (if I don't have any files on there)...

---

### Post by leipogs23 on 2009-05-24
I also got this virus once and I deleted it using this.

[http://www.ziddu.com/download.php?uid=Zq2fnJioa6yenOKnZKqhkZSnYaudm5es4](http://www.ziddu.com/download.php?uid=Zq2fnJioa6yenOKnZKqhkZSnYaudm5es4)

Just download then plug the USBs infected then double click. Pag di natanggal yung sa USB, Kopyahin mo sa loob ng USB then run. Good luck!!!!

---

### Post by Johnaray on 2009-05-24
> **leipogs23 said:**
> I also got this virus once and I deleted it using this.

[http://www.ziddu.com/download.php?uid=Zq2fnJioa6yenOKnZKqhkZSnYaudm5es4](http://www.ziddu.com/download.php?uid=Zq2fnJioa6yenOKnZKqhkZSnYaudm5es4)

Just download then plug the USBs infected then double click. Pag di natanggal yung sa USB, Kopyahin mo sa loob ng USB then run. Good luck!!!!


Yup! Thanks I forgot nga pala si Gian... sya ang gumawa nyang Kaizer antivirus... ;) a known member of Elab and he runs his own forum Ehub.

Thanks for reminding me leipogs23 

anymore ideas guys? :D

---

### Post by leipogs23 on 2009-05-24
Oooopsa!!! Me nakalmutan pala ako. If I recall it correctly, babalik pa din yung recycler kasi ginagamit nya yung system restore capabilities ng PC mo. So better turn off the System restore of your PC for now.

---

### Post by Nhatz on 2009-05-25
Guys ang ginagawa ko sa RECYCLER na makulit... ay lagay mo lang yung USB then change mo lang permission ng RECYCLER folder at pag may recycler automatic may autorun.ini yan...

```
sudo chmod -R a+rwx /media/<name ng USB Drive>
```

Presto!!! tanggal ang makulit na RECYCLER folder at autorun.ini. hehehe :D

ASTIG!!! :guitar:

---

### Post by Mike_tn on 2010-11-22
> **Johnaray said:**
> 
This time my Flash drive got infected with a RECYCLE Folder and a Autorun.inf file. ( Thanks to INTERNET CAFES )
Johnaray

Not sure if this is what you mean. If not just ignore me....

Windows automatically puts a recycle folder called $RECYCLE.BIN with a desktop.ini file nested in a folder in that. Also a folder that is called "System Volume Information". Both hidden to Windows users but visible to Linux.

From tech support forums
"You cannot prevent the System Volume Information and Recycler Folders/Files from being placed on external Drives.
These two are essential for Windows® to recognise the size and makeup of the Drive; with the 'Recycler' for any files/folders that are intentionally deleted by you on the particular Drive.
Without these two Folder/Files your external Drive/s would not operate."

---

