---
title: "Sharing issue"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by Sagimore on 2012-02-23
Hello,

Having a problem with network. My Ubunto machine can see my windows 7, Home, windows 7 pro.

But my Windows machines cant see the Ubunto shares. I set up SAMBA, also updated and installed some add-ons I read I needed- Glade phython-glade...Windows machines only see each other. 

Any ideas? I'm on 11.10

Thanks

---

### Post by Morbius1 on 2012-02-23
* Make sure the server samba daemons are running on your Linux box:
```
sudo service smbd status
sudo service nmbd status
```If they aren't running start them:
```
sudo service smbd start
sudo service nmbd start
```* See if the Samba client on your box can see the Samba server on your box:
```
smbtree
```[COLOR=Blue]*It should list your Linux box and any shares you created. If it does not or gives you errors post the entire output here so people can see them. *[/COLOR]

* Run the following command:
```
hostname
```And count the number of characters. If it's 15 or less then you're good to go. If it's 16 characters or more then you need to fix it. You can do that in a samba config file that you will need to edit as root:
```
gksu gedit /etc/samba/smb.conf
```In the [global] section - right under the workgroup line - add the following line:
```
netbios name = something
```[COLOR=Blue]*"something" has to be 15 character or less in length.*[/COLOR] [COLOR=Blue]*This is the name that you lan will see when they browse the network*[/COLOR]

Then restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Note: every time you restart samba the network has a fit so wait a few minutes, run smbtree again to see if you can see the server without errors, and then try  to connect to it from Win7.

---

### Post by Sagimore on 2012-02-23
Thanks will try tonight.

---

### Post by Sagimore on 2012-02-23
It was 16 characters, and im good to go now. Thank You, very helpful

---

