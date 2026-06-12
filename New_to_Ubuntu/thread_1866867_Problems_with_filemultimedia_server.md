---
title: "Problems with file/multimedia server"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by Stevek33 on 2011-10-22
Hello everyone! Brand new to the forum lost like most other noobs. :D
 
I was hoping this would go a little more smoothly. I decided to try and create my own file/multimedia server with an old machine.
 
Ubuntu install went smooth. Install and configuring some basics ok. 
 
I guess my noobness came shining through when I was able to set up the sharing of a folder on the server side but none of my windows machines can see the server. After hours of reading I still cannot sift/wade through the tons of information.
 
I just cannot grasp the terminal/file system on linux yet. I love the look and feel and I can't really see what it can do. I just am to new to do anything. I think I am going to seek out some local classes becase I would like to become proficient with ubuntu/linux.
 
So.... can someone PLEASE help me with. 
1st. Getting my server shared to my windows home network.
2nd. Samba. i cannot pull this up and have yet to find anything on the internet to help me. I installed it but I cannot locate it. :(
3rd. Speak as plainly as possible regarding the terminal. Also on some samba sights I followed their commands only to get errors.
 
Thank you thank you in advance! 
 
Steve

---

### Post by garvinrick4 on 2011-10-22
> 1st. Getting my server shared to my windows home network.
You installed Ubuntu server edition or Desktop edition using it as a server?

---

### Post by mörgæs on 2011-10-22
Changed the title to a more descriptive one.

---

### Post by Stevek33 on 2011-10-22
> **garvinrick4 said:**
> You installed Ubuntu server edition or Desktop edition using it as a server?
 
Unsure.  I followed the main download from the Ubuntu website.
 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by garvinrick4 on 2011-10-22
> 1st. Getting my server shared to my windows home network.```
sudo apt-get install sytem-config-samba
```Now open and make your samba shares by path.
(example)
/home/rick/Music

Or Make your own Directory:
```
sudo mkdir /home/rick/Shared
```now share at path.
Make sure you hit permissions tab, only 2 tabs, pretty self explanatory.

 Samba will work in Windows workgroup out of box just need the shares.

Shares will be in samba config file at this path. Can see how application makes shares at bottom of config file.
/etc/samba/smb.conf

---

### Post by masgeeks on 2011-10-22
BTW - system-config-samba doesn't work as gui in gnome shell (at least it didn't for me) needs some other packages installed.  If you try to run system-config-samba from command line, it will give you the verbose, complaining abut what it doesn't like or doesn't have.  I think it wanted glade and some other stuff, don't recall now.

---

### Post by Stevek33 on 2011-10-22
> **garvinrick4 said:**
> ```
sudo apt-get sytem-config-samba
```Now open and make your samba shares by path.
(example)
/home/rick/Music
 
Or Make your own Directory:
```
sudo mkdir /home/rick/Shared
```now share at path.
Make sure you hit permissions tab, only 2 tabs, pretty self explanatory.
 
Samba will work in Windows workgroup out of box just need the shares.
 
Shares will be in samba config file at this path. Can see how application makes shares at bottom of config file.
/etc/samba/smb.cfg
 
 
sudo apt-get system-config-samba 
 
enter returns E: invalid operation system-config-samba

---

### Post by garvinrick4 on 2011-10-22
I am sorry
```
sudo apt-get install system-config-samba
```
Will repair the install code of previous post to include install.

---

### Post by Stevek33 on 2011-10-24
> **garvinrick4 said:**
> I am sorry
```
sudo apt-get install system-config-samba
```
Will repair the install code of previous post to include install.
 
 
"system-config-samba is already the newest version."
 
0 upgraded.

---

### Post by Stevek33 on 2011-10-24
I am making progress. I can now see the shared folder. But when I click on it through my windows machine it is asking for "Enter Network Password"
 
Username
Password
 
So Im locked out until I figure out what info it's looking for. Is there a way to disable the password keyring?
 
Looking at my smb.conf file it seems ok.  I'm not sure how to completely open up sharing so my win7 machines don't require a password.

---

