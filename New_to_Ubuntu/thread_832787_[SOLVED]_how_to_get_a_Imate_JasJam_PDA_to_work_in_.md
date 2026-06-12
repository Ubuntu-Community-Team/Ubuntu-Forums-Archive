---
title: "[SOLVED] how to get a Imate JasJam PDA to work in ubuntu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by fr.theo on 2008-06-18
hello, all


I have an IMATE JASJAM and want to use it with the contacts in Evolution, however the device is not recognized by the system. The PDA is running a Windows platform I think Version 6, does anyone know how to get it to work in Ubuntu.


Kind Regards

FR. T.

---

### Post by fr.theo on 2008-11-15
old thread just seeing if any new ideas.

---

### Post by fr.theo on 2008-12-02
Finally got my Imate Jas Jam with Window Mobile 5 to work in ubuntu, however it only syncs with Evolution, no support for fire fox yet.


here is how I did it:

```

1. Go to System -> Administration -> Software Sources 

2. Click on Third Party software

3. Click Add...

3. Add : deb http://ppa.launchpad.net/synce/ubuntu hardy main 

4. Click Close

5. Click Reload 

6. Load Terminal : Applications >> Accessories >> Terminal


(note: this next step is apparently for older kernels so if you have the latest one skip this step, I did it by mistake but I have not had any troubles yet.)

7. a) sudo rmmod rndis_host cdc_ether usbnet 

   b) sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb  
      {rndis_host,cdc_ether,usbnet}.ko

   c) sudo apt-get install usb-rndis-source cdbs
    
   d) sudo module-assistant auto-install usb-rndis
 


8. sudo apt-get install synce-hal librra0-tools librapi2-tools

(note this next step I had a problem because I did not have a service called odccm if you do not have it you will receive a error message enter the following in terminal "sudo apt-get install odccm". 

before you proceed. once installed you can check to see if it is working by typing the following "sudo odccm -f" make sure you run this before you plug in your device, you should get an output but be patient it takes a while.)

9. synce-pls

(note you should get an entire listing of your WM device should look something like this) :

[CODE]root@Ubuntu:/usr/lib/evolution/2.22# synce-pls
Directory               2007-05-06 17:18:18  Personal/
Directory               2006-04-30 23:00:18  Templates/
Directory               2007-05-06 17:18:18  Pocket Dictate/
Directory               2007-05-06 17:18:48  My Pictures/
Directory               2006-04-30 23:00:22  My Videos/
Directory               2007-05-06 17:18:52  My Music/
Directory               2007-05-06 17:18:58  My Midlets/
Directory               2007-05-06 17:18:58  eAV Logs/
Directory               2006-04-30 23:00:22  UAContents/
Directory               2007-05-06 17:18:58  Dictionaries/
Archive              0  2005-07-12 01:16:58  bjavatar.storage
Archive              0  2008-08-28 15:14:00  poolavatar.storage
Archive             60  2007-05-25 02:48:50  back.gif
Archive           3850  2007-05-25 02:48:50  Cannot find server.html
Archive           7168  2007-05-06 17:18:14  Doc1.doc
Archive            187  2007-05-25 02:48:52  pagerror.gif
Archive             82  2007-05-25 02:48:52  refresh.gif
Archive            685  2007-05-06 17:18:16  _setup.xml
Directory               2007-05-06 17:18:58  Laridian Books/
Directory               2007-05-06 17:18:58  Calls/
Directory               2007-05-06 17:18:58  Business/
Archive           1248  2007-05-25 02:48:52  ding.amr
Directory               2007-06-18 02:15:40  ImageDec/
Normal          676168  2007-11-08 14:00:12  07112007660.jpg
Normal          804224  2008-01-24 23:26:58  kireyae leyson.mp3
Normal          101762  2008-01-26 00:44:18  wife warning.mp3
Normal           36410  2008-02-10 17:29:54  Me.jpg
Normal            7286  2008-03-02 19:18:30  Photo0040.jpg
Normal            7703  2008-03-02 19:18:44  Photo0039.jpg
Normal            8547  2008-03-02 19:18:56  Photo0038.jpg
Normal            7097  2008-03-02 19:19:14  Photo0037.jpg
Normal            7041  2008-03-02 19:19:26  Photo0036.jpg
Normal            6766  2008-03-02 19:19:38  Photo0035.jpg
Normal            7692  2008-03-02 19:19:52  Photo0034.jpg
Normal            8084  2008-03-02 19:20:02  Photo0033.jpg
Normal            7961  2008-03-02 19:20:14  Photo0032.jpg
Normal            8043  2008-03-02 19:20:26  Photo0031.jpg
Normal            7793  2008-03-02 19:20:38  Photo0030.jpg
Normal            7339  2008-03-02 19:20:50  Photo0029.jpg
Normal            8782  2008-03-02 19:21:02  Photo0018.jpg

```

10. sudo apt-get install multisync-tools opensync-plugin-evolution 
    opensync-plugin-synce

11. synce-sync-engine

12. synce-create-partnership "Linux desktop" "Contacts,Calendar"

13. msynctool --listplugins;  note: you should get a list like this: 


```
root@Ubuntu:/usr/lib/evolution/2.22# msynctool --listplugins
Available plugins:
evo2-sync
synce-opensync-plugin
synce-opensync-plugin
```


14.  msynctool --sync synce-sync (your device should be now uploading its contacts list to evolution)
 
[/CODE]


Getting it to work with Kitchensync:

I used kitchensync as a gui front end you can install this from the Applications >> Add Remove Programs >> do a search for kitchensync and install it or in terminal  sudo apt-get install kitchensync.


1. open kitchensync, should be under Applications >> Accessories >> Kitchensync.

2. kitchensync should open

3. if there are any groups delete them using the delete groups button

4. with you mouse select "add group" a pop up window requesting a name for the group should pop up give it a name you desire.

5. once you have given a name with your mouse select add member, in this section you will need to add both "evolution 2.x" and a "plugin to synchronize with windows ce device" you may have to select add member twice to add both.

6. you will not need to edit the "evolution 2.x" member it is set to default just the "Plugin to synchronize with windows ce device" member.
give the member a name and add the following to the synce-sync member:

addgroup synce-sync
addmember synce-sync synce-opensync-plugin
addmember synce-sync evo2-sync 

select ok.

7. now you should be able to sync, just select the Synchronize now hyperlink or text that is underlined as synchronize and it should start to sync.

(note you may recive an error message just select use item or click on the use item button and it should not appear again.)


for the full installation guide go here it has more detail than mine.

Link: [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

---

