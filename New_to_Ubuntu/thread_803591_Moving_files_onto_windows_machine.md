---
title: "Moving files onto windows machine"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Tinystickfigure on 2008-05-22
Hello. I am brand brand new to ubuntu. I recently installed ubuntu on my HP Pavilion zx5000. In my house we have 3 computers, my computer, my brothers computer and our server where we have all of our media. typically, one of us will download something then throw it on the server for the other to use if needed. anywhoo, since i upgraded to ubuntu, every time i try to move something onto the media server throught places>>network>>...etc..etc.. it begins to move it over, but after a while it just times out. is there any way to fix this?

pretty much if i could fix this and figure out how to remote desktop into my machine, i would never have to use windows again haha.


Thanks for any help, 
Tinystickfigure

---

### Post by Inxsible on 2008-05-22
What OS is the server running? If its windows based, have you correctly installed Samba? You can always RDP into your server to get a X session.

---

### Post by Tinystickfigure on 2008-05-22
It is running windows media center. I have not installed samba, i am not even sure what that is :). i am also not sure what rdp or x session is either.

---

### Post by nowshining on 2008-05-22
x session is the GUI part u see. Samba lets one network. Look in the repos for Samba and install it.. Enable all repos first in the software Sources found in the menus.

---

### Post by Tinystickfigure on 2008-05-22
How do i get samba?

---

### Post by Inxsible on 2008-05-22
> **Tinystickfigure said:**
> It is running windows media center. I have not installed samba, i am not even sure what that is :). i am also not sure what rdp or x session is either.
Once you install samba, you can map your server onto your Ubuntu machine, and simply drag and drop files like you would in your regular partitions/drives.

RDP - Remote Desktop Protocol - you can connect to your server using this protocol and actually control your server thru your Ubuntu machine. X session is just another word for getting a GUI interface for doing RDP.

---

### Post by Inxsible on 2008-05-22
> **Tinystickfigure said:**
> How do i get samba?Open a terminal and run this command```
sudo apt-get install samba
```

---

### Post by Tinystickfigure on 2008-05-22
ok, i did that, but how do i run it?

---

### Post by ivze on 2008-05-22
Samba is that what makes sending files via Microsoft "file and prinetr sharing protocol" possible. Samba is definitely installed on your Ubuntu machine. The fact, that it hangs is, however, very strange. 
What about remote logins -- this is solvable, hovever, needs diging.

---

### Post by ivze on 2008-05-22
To arrange remote-login from a windows machine, make the following:
On Ubuntu:
Install openssh-server on Ubuntubox (via Synaptic).
On windows:
See xming project on sourceforge. 
Download and install "Xming" and "portable putty".
Run Xlaunch.
There will be a configuration dialog, make sure to choose portable putty as your remote connector and "gnome-session" as a programm you are going to launch.

If all goes well, you will see your desktop with programms, running remotely.

---

### Post by Iowan on 2008-05-22
> **Tinystickfigure said:**
> ok, i did that, but how do i run it? There is a certain amount of setup required for Samba.  Most of it centers around a configuration file /etc/samba/smb.conf. [Here ]("http://ubuntuforums.org/showthread.php?t=202605")is a good How-To and [this]("https://help.ubuntu.com/community/SettingUpSamba") is another good article.

---

