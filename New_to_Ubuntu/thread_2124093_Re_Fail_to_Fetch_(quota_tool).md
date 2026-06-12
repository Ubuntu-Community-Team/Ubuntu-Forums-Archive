---
title: "Re: Fail to Fetch (quota tool)"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by mkVR32 on 2013-03-09
Hi All -  I'm a newb, :D  Anyways, my instructor is failing to get back to me -  here's the problem - I'm trying to run sudo apt-get update and sudo apt-get install quota quotatool  after that -- screen shots attached-

---

### Post by Old_Grey_Wolf on 2013-03-09
So, you have done sudo apt-get update.

Did you do sudo apt-get upgrade before entering sudo apt-get install quota quotatool?

Enter ```
sudo apt-get update
``` and post any errors you get.

---

### Post by mkVR32 on 2013-03-09
> **Old_Grey_Wolf said:**
> So, you have done sudo apt-get update.  Did you do sudo apt-get upgrade before entering sudo apt-get install quota quotatool?  Hi Grey -  I didn't -  should i give that a try?  thank you

---

### Post by Old_Grey_Wolf on 2013-03-09
Yes, and post any errors you get.

---

### Post by mkVR32 on 2013-03-09
thanks!  I will.

---

### Post by mkVR32 on 2013-03-09
In order -     [http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/upgrade_zps2a3a37b8.png](http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/upgrade_zps2a3a37b8.png)   [http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/upgrade2_zps2c012847.png](http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/upgrade2_zps2c012847.png)

---

### Post by Old_Grey_Wolf on 2013-03-09
It may be an intermittent problem with the repo mirror server you are using. If you haven't already tried this, you could try switching mirror servers. Open "Update Manager", click the "Settings..." button, then select "Other..." from the "Download from menu", then click the "Select Best Server" button, let it run its tests, then click the "Choose Server" button. It will then ask you to reload.

Edit: I will be going to sleep in about 8 minutes. Someone else may have to help you after that.

---

### Post by mkVR32 on 2013-03-09
I see, just a note, not running a GUI :-/

---

### Post by sandyd on 2013-03-09
can you post the output of
```

ifconfig
cat /etc/resolv.conf
route -n
```

thanks!

---

### Post by mkVR32 on 2013-03-09
> **sandyd said:**
> can you post the output of ```
 ifconfig cat /etc/resolv.conf route -n
```  thanks!  [http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/ifconfig_zpsff85956d.png](http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/ifconfig_zpsff85956d.png)  [http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/route_zps2bcd7bab.png](http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/route_zps2bcd7bab.png)  [http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/cat_zps9804dd1e.png](http://i118.photobucket.com/albums/o90/dubswithmohawks/linux/cat_zps9804dd1e.png)   Thanks!

---

### Post by mkVR32 on 2013-03-10
attaching the Lab PDF  file to show what I'm doing --  Step 23 is where I changed the interface file and step 53 is where I'm stuck now.  [https://www.dropbox.com/s/dth35yjnts7r6h8/ITSEC_136_Lab_5.pdf](https://www.dropbox.com/s/dth35yjnts7r6h8/ITSEC_136_Lab_5.pdf)   Let me know if you have trouble with the pdf - and thanks for all the help - due at midnight tonite so i'm starting to grip.

---

### Post by mkVR32 on 2013-03-10
bump TTT

---

### Post by sandyd on 2013-03-11
Everything looks correct - are you connected to the internet properly?

If this is plugged into your school's internet, it may require a login page and/or such to access the internet.

---

