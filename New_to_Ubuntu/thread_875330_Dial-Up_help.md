---
title: "Dial-Up help"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by napsta on 2008-07-30
I just got ubuntu onto my computer and was wondering how I connect to the internet using Dial-Up (yes it's sad I know) and was wondering if there is a way to connect (I'm completely lost on this)

---

### Post by rraj.be on 2008-07-30
Run this command in terminal
```

wvdialconf
```

This will search for  modems attached.

The it will store its configuration in file called as ```
/etc/wvdial.conf.

```
Edit thtat file with your details.

To edit type this command 
```

sudo gedit /etc/wvdial.conf
```

Save and close it.

Type this command in terminal to dial your connection.
```

wvdial
```

Thats it.

---

### Post by tuxxy on 2008-07-30
Dial up damn I thought they stopped that :lolflag:

---

### Post by nitehawk777 on 2008-07-30
Hello!
I'm new to Ubuntu also,...and I just now got it installed on my computer.  I also have a little dial-up service (yes,..there still are those of us)!  Do you have an external modem,..or an internal "winmodem"?   External modems work (but most internal winmodems don't).  
Dial-up can work on Ubuntu,..believe me,..(I'm using mine right now).  Someone with more experience may have to talk you through the steps,....(I'm not too sure as to how to explain it).
But be encouraged,...it CAN be done!:)

---

### Post by napsta on 2008-07-30
I wish let me try it on ubuntu

---

### Post by Shazaam on 2008-07-30
Look here.....
[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

---

### Post by Mike_cog on 2008-07-30
I have been using dial up on Ubuntu for about 2 years without a problem. Have just upgraded to heron 8.04 and dial up still working but when i disconect to do other stuff then try to redial i cant get back on the internet i have to reboot the computer to get back on the internet.
Have u used the network tool. Go to System > Administration and click on Network then see a tab that says unlock, click on this and enter your password then set up your modem. Can anyone help me not being able to reconnect?
Ta

---

### Post by ModelM on 2008-07-30
For Mike_cog:

The next time this happens, before you reboot type into a terminal:

ls -l /var/lock/

and let us see the results. I think I might know what's happening.

---

### Post by Mike_cog on 2008-08-20
> **ModelM said:**
> For Mike_cog:

The next time this happens, before you reboot type into a terminal:

ls -l /var/lock/

and let us see the results. I think I might know what's happening.

Problem is now solved. The modem seems to be "ALWAYS ON" so you just disconnect the power to the modem to switch off and connect power back to the modem to redial back onto the internet. Thanks

---

### Post by malspa on 2008-08-20
Some links to pages that might be helpful for those wanting to use dial-up with Ubuntu:

[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef6)

For those using dial-up with Linux, an external serial modem (instead of trying to use an internal winmodem) will save you a lot of time and hassle, and they can be found used for less than $15.  Most winmodems are not going to work with Linux, and the external serial modems I've used didn't require any additional drivers or anything like.

Re: the above links, when using GNOME I prefer to use gnome-ppp for my connections but Ubuntu doesn't come with gnome-ppp installed by default,so I use the "Network" or NetworkAdmin" approach to connect at first.  Then I typically download gnome-ppp from the repos and and use that for my connections from there on.

For KDE distros, kppp is usually included by default.

---

