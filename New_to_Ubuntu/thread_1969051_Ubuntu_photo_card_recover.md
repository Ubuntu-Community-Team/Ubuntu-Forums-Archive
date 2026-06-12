---
title: "Ubuntu photo card recover"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-04-29
My sister and her huby went to England to a vintage car show then to Spain, on the return home here to northern Ireland they discovered the camera they have is misbehaving and the photos they took have disappeared from the Scandisk SD card, which was bought in Tesco's cheap "could be a fake"

All the photo recovery programs that I have looked at are win or mac based does any one know of a program that will run on ubuntu 10.04 64bit which I am running

Thanks
Dave

---

### Post by Cheesemill on 2012-04-29
```
sudo apt-get install testdisk
photorec
```

Photorec should allow you to recovery any photos if they have not already been overwritten.
If the card is a fake though I'm afraid you are out of luck.

---

### Post by coffeecat on 2012-04-29
@DaveMcC, if the photos are recoverable then photorec will recover them, but it is not the most user-friendly application around. This is a useful howto:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

It covers both testdisk and photorec, but you probably only need photorec. Scroll down to about half-way for the photorec instructions. The howto mentions running from a live CD, but for recovering from an SD card, you can install testdisk to your permanent Ubuntu installation.

---

### Post by DaveMcC on 2012-04-30
> **Cheesemill said:**
> ```
sudo apt-get install testdisk
photorec
```Photorec should allow you to recovery any photos if they have not already been overwritten.
If the card is a fake though I'm afraid you are out of luck.

Got them recovered
Burnt to DVD,

Thank you both
One wee problem
Just will not come off my hard drive now? there is a wee padlock on the recup folder, how do I remove? 

Thanks

Dave

---

### Post by Cheesemill on 2012-04-30
Open nautilus with root privileges, you'll then be able to delete the folder.
```
gksudo nautilus
```

---

### Post by audiomick on 2012-04-30
> **Cheesemill said:**
> Open nautilus with root privileges, you'll then be able to delete the folder.
```
gksudo nautilus
```

Yes, this will let you delete a folder that doesn't belong to you, the user.

Just bear in mind that this instance of Nautilus, whilst very useful occasionally, also is capable of deleting important system files. Use it for what you opened it for, then shut it again immediately. ;)

---

### Post by DaveMcC on 2012-04-30
Should have added that the Scandisk SD from Tesco is a fake, it showed up as a "Generic Storage Device",  and when I dropped in one of my Kingston Sd cards, it read it as a Kingston card, then I put one of my ScanDisk Cf cards in, guess what,,, it read it as Scandsk

I think that's proof enough it's a fake.

Now moving on to  "gksudo nautilus"  I guess that you open it in Terminal, which is what I done

Then what ?


Sorry but the padlock stayed on the folder

Dave

Had to get the right name for said fake

---

### Post by Cheesemill on 2012-04-30
When you have open nautilus as root using the above commands it will let you modify any file on the system.
Just browse to the location of the recup directory, select it and hit SHIFT+DEL.

Also the card may not be a fake, if it was you probably wouldn't have been able to recover the photos. There is testing software available here:
[http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)

---

### Post by DaveMcC on 2012-04-30
This is different

boss@Boss-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2140'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


```
(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2140): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```

Re tryed that again, it worked

I did close down when finished deleting 

Thankyou all once again

Dave

---

