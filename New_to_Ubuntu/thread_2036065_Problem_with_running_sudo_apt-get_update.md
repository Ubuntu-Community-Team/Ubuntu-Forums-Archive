---
title: "Problem with running sudo apt-get update"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by rufus muturi on 2012-08-01
Hello, guys. I am trying to update my system (Ubuntu 12.04) but after a certain point I get this message (I have partly edited it, but the meat is there, as it were):



W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A5D712AEE06E6293
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.


I am especially interested in finding out what that last statement means. Any help will be greatly appreciated

---

### Post by levlaz on 2012-08-01
It looks like you added a repo that needed a gpg key.

See [this article]("http:// http://www.webupd8.org/2010/05/automatically-import-all-missing.html") on how to fix it. 

The last line isn't too important ... basically since you don't have the key nothing else will happen. :)

---

### Post by rufus muturi on 2012-08-01
levlaz, thank you. I'm checking it out now

---

### Post by NikTh on 2012-08-01
Hi , 
please go to Update Manager > Settings > Ubuntu Software and Un-tick CdRom . 

OR an other way 


Open a terminal (Ctrl+alt+t ) 
and write ```
gksudo software-prorerties-gtk
``` 
and again , Unitck Cdrom . 

Thanks

---

### Post by Elfy on 2012-08-01
```
gpg --keyserver keyserver.ubuntu.com --recv  A5D712AEE06E6293
gpg --export --armor A5D712AEE06E6293 | sudo apt-key add -
```

Should deal with the signatures - likely that you added a PPA without adding the signatures as well.

---

### Post by rufus muturi on 2012-08-01
Hey, NikTh, thank you. I've done that. I'll now wait to see how it goes.

---

### Post by rufus muturi on 2012-08-01
Thank you, Elfy!

---

### Post by rufus muturi on 2012-08-01
Hey, still nothing. From Elfy's solution all I'm getting is:


gpg: no valid OpenPGP data found.

---

### Post by NikTh on 2012-08-01
Hi , 
please try these commands 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get autoclean 
sudo apt-get clean all
sudo apt-get update
```and post the results of 
```
sudo apt-get update 
cat /etc/apt/sources.list
```**Put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane.**

Thanks

---

### Post by blade4 on 2012-08-01
Here's a terminal free solution I use :

first take a look at the hash code of your gpg ( that long garble after NO_PUBKEY )

Now goto keys.indymedia.com  and in the bar that asks for key id , put in 

          0x(your hash code here)

in your case , this is  0xA5D712AEE06E6293 

you'll now be directed to a page that gives you the gpg key : click on the blue hyperlink after "pub" . Now copy the entire text and paste it in a blank file ( create new document ) on your desktop ( or anywhere you like , it doesn't matter ) . Now go to software sources  ( you can do this by clicking on the settings button in the ubuntu update dialog ) and goto the [B]authentication tab .

[/B]Here , click on import key file and import the document you just saved . 

AAand yu're done ! Its a bit lengthy , I know , but its terminal free :P 

Cheers

---

### Post by rufus muturi on 2012-08-02
Hey, NikTh. Nothing :-(

blade4, I'm trying it out now, I'll let you know how it goes. All you guys, thanks a bunch!

---

### Post by rufus muturi on 2012-08-02
blade4, did what you suggested, same problem.

This are the last few lines of the output.

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by NikTh on 2012-08-02
Hi , 
can you please post the output of 
```
cat /etc/apt/sources.list
```and the output of ```
sudo apt-get update
```by click on New Reply and click # and paste results between brackets. 

Thanks

---

### Post by blade4 on 2012-08-02
Refer this site : 

[http://askubuntu.com/questions/120621/w-duplicate-sources-list-entry-http-archive-ubuntu-com-ubuntu-precise-update](http://askubuntu.com/questions/120621/w-duplicate-sources-list-entry-http-archive-ubuntu-com-ubuntu-precise-update)

Hope this helps 

Cheers

---

