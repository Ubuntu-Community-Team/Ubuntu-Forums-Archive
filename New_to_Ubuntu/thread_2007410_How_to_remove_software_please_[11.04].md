---
title: "How to remove software please [11.04]"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Filthy Stockings on 2012-06-20
Since downloading updates yesterday, found my GET IPLAYER failed to function so searched and updated it again but don't like the new version.

So need to know how to find and remove the latest version.

Also how can I find the list of the UBUNTU 11.04 UPDATES I would have downloaded yesterday so I might be able to post them here and find out which one affected my GET-IPLAYER functions.

Hope someone can guide me and then will be that more informed to action more for myself rather than pester this forum.

Thanks in advance.

---

### Post by wilee-nilee on 2012-06-20
If you install and use synaptic there will be a history there.

---

### Post by codemaniac on 2012-06-20
> **Shia Asininity said:**
> Since downloading updates yesterday, found my GET IPLAYER failed to function so searched and updated it again but don't like the new version.

So need to know how to find and remove the latest version.

Also how can I find the list of the UBUNTU 11.04 UPDATES I would have downloaded yesterday so I might be able to post them here and find out which one affected my GET-IPLAYER functions.

Hope someone can guide me and then will be that more informed to action more for myself rather than pester this forum.

Thanks in advance.

You might be interested in the file **/var/log/dpkg.log** .

open up a terminal alt+ctrl+T and place the below command to see the latest upgrades .

```
awk '$3 == "upgrade"{print}' /var/log/dpkg.log
```

---

### Post by Filthy Stockings on 2012-06-20
Thanks for both replies. Used CODEMANIAC's code to get list going back to 1/6/12 UBUNTU UPDATES but am not clever enough to read through the ones for yesterday which I suspect had something that messed up my year long working GETIPLAYER.

What i did see was the last two entries, copied below

  	 	 	 	 	 	   [SIZE=3]2012-06-19 11:47:45 upgrade atomicparsley 0.9.2~svn110-4 0.9.4-hg91.472d5fe6fb04-0ppa2~oneiric [/SIZE]
  [COLOR=#000000][SIZE=3]2012-06-19 11:47:50 upgrade get-iplayer 2.79-2 2.82+n0-git9503c03-ppa6~oneiric [/SIZE][/COLOR]
  
which must be something to do with my downloading the newer version of GETIPLAYER which I would prefer not to have.

So how do I delete it?

Thanks in advance for anyone who can guide me a bit further in the general method of HOW TO DELETE software/programs

---

### Post by tuxtout on 2012-06-20
You could try to completely remove it and then install it again.
Open a terminal and issue this command,

sudo apt-get remove get-iplayer --purge && sudo apt-get install get-iplayer

---

### Post by edeneen on 2012-06-20
I am still a newbie, so I've always used synatic package manager to remove stuff

---

### Post by Filthy Stockings on 2012-06-20
Thanks for further replies.

I followed the TUXTOUT procedure but still ended up with the latest version 2.82 whereas I think I would be happier with the old 2.79 which have used for the last year.

Found that version elsewhere, saved to file but extracting it does not seem to get it to work.

So currently have version 2.82 but want version 2.79...any idea how to get 

get_iplayer-2.79.tar.gz

to now work on my system.

Also re EDENEEN advice....how do I find SYNAPTIC PACKAGE MANAGER?

Boy do I feel dumb!

---

### Post by edeneen on 2012-06-20
Also re EDENEEN advice....how do I find SYNAPTIC PACKAGE MANAGER?

you can download it from the Ubuntu Software Center

---

### Post by ajgreeny on 2012-06-20
> **Shia Asininity said:**
> Since downloading updates yesterday, found my GET IPLAYER failed to function so searched and updated it again but don't like the new version.

So need to know how to find and remove the latest version.

Also how can I find the list of the UBUNTU 11.04 UPDATES I would have downloaded yesterday so I might be able to post them here and find out which one affected my GET-IPLAYER functions.

Hope someone can guide me and then will be that more informed to action more for myself rather than pester this forum.

Thanks in advance.
I am very interested to know in what way it failed to function.

I installed version 2.79 from the repos of Lucid 10.04 a long time ago and ever since I have simply been manually updating the **get_iplayer** perl script in /usr/bin by downloading the tar.gz file from [http://git.infradead.org/get_iplayer.git](http://git.infradead.org/get_iplayer.git), extracting the perl script, and using that in place of version 2.79.  It has never failed me so far, and I just wonder what is happening for you to make you wnat or need to go back to the previous version.

---

### Post by Filthy Stockings on 2012-06-21
To Ajgreeny, thanks for reply. What happened was that soon as downloaded the week's UBUNTU updates [33 of them] I then found I couldn't  download any radio programmes via GET-IPLAYER....the prog was matched correctly and 'connecting' and flashing cursor appeared as normal but then the cursor froze and nothing would happen so not 1kb was downloaded. BUT the TV download did seem to work!?

So asked for help here, got no replies and googled elsewhere for advice. Found page to install new GETIPLAYER version and seems like my 2.79 now replaced by 2.82.

All seemed fine in that could now download both radio/TV BUT there were now changes I did not want

1 radio progs arrive as m4a and not aac files, and with a thumbnail picture which shows as a blurred static image during playback via MOVIEPLAYER whereas before I could see the player animations; which is my preferred choice

2 The TV downloads are 70% larger files than before for the same runtime which is something I do not want as this just uses up more of my fixed monthly ISP download quota. If they produce better quality that is not something I need as for a year the previous sizes sufficed ie 

169.1MB for a 30 min prog with 2.79 rather than 308.3MB  for the same prog's next same length episode with 2.82

I googled last night and saved 

get_iplayer-2.79.tar.gz

but despite extracting was still being told GETIPLAYER not installed so searched more and found this code sequence, posted on these forums from SHANTIQ 3/2/11

 	Code:
 	wget [ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.79.tar.gz](ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.79.tar.gz) 
Code:
 	Code:
 	tar -xvf get_iplayer-2.79.tar.gz 


Code:
 	Code:
 	sudo mv get_iplayer-2.79/get_iplayer /usr/bin/ 
then to terminal    enter     	Code:
 	get_iplayer 
 which seemed to install get-iplayer and allowed me to immediately download a radio prog as aac and without the static image; RESULT!

BUT when tried TV download was still finding the LARGER files I do not require were being downloaded.

So it is like I had 2.79 for radio downloads but 2.82 for TV....OR maybe since I never used any updates during a year of using 2.79...perhaps the TV = LARGER FILES aspect was built into later versions of GET-IPLAYER and is now a default.

SO.....any advice how to get SMALLER TV  file sizes; as I was happy to receive for a year? 2.79 worked fine for me and do not need any advance on that.

And yet am wondering what interfered with the radio downloading on 19/6/12 and if this was down to something in those UBUNTU updates or just  a BBC site fault. I have been told here how to view a list of the updates and cannot see anything that refers to get-iplayer ...though as stated, I am not very clever with ubuntu; yet.

Thanks for any pointers anyone might suggest.

---

### Post by ajgreeny on 2012-06-21
I think any change must be down to the BBC's own changes, not the get-iplayer version update.

I have just recorded/downloaded both a TV and radio programme using both the 2.79 and 2.82 versions of get-iplayer and the resulting files were identical, whichever I used.  I think therefore that you may as well stick with the 2.82 version as there will be no changes to what is actually avaiable to download.

The TV progs arrived as .mp4 files and the radio as your preferred .aac files (which are still shown as audio/mp4 files in file properties).  All provided thumbnails which you can always not use in movie-player if you prefer not to; I use vlc to play them so can't comment about how you do that.

---

### Post by Filthy Stockings on 2012-06-21
Thanks for reply and info, Ajgreeny.

That is interesting and depressing....will reduce what I can watch if files now 3/4 large than June 2011 - 19/6/12; the period I have been using GETIPLAYER...unless pay for a larger monthly download limit.

I am back on 2.82 as that is the only one which loaded with the pasted codes I used. The 2.79 code install from Ashantiq did not work anymore.

My radio downloads since show the same static image and are marked as m4a in my HOME folder whereas all other radio progs DL'd this month before 19/6 show 'aac' and have no thumbnail attached.

Have code to remove the thumbnails but having to do that for every single one takes more time than can spare.

Think there's a code to NOT have any thumbnails attached to the audio files?

Also checked getiplayer messageboards at 

[http://lists.infradead.org/pipermail/get_iplayer/2012-June/date.html#3038](http://lists.infradead.org/pipermail/get_iplayer/2012-June/date.html#3038)

and seems others reported lost connection on same date as I experienced it so was likely to be a BBC fault after all....and I could have kept 2.79 after all....

Thanks again for taking time to read and advise.

---

