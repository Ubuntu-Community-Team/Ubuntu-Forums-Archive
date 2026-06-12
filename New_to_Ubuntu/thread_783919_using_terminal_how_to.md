---
title: "using terminal how to?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by creekchub on 2008-05-06
i am the only user on this pc.  i was trying to use the terminal function last eve. but when i typed in a code it stated i do not have administrative privileges so now how or what do you do to get
logged into that function?

---

### Post by rahulsharma on 2008-05-06
what kind of function are you using like to install any software you need to type sudo before that to get super user privileges could you post what exactly you were trying to do

---

### Post by subzero316 on 2008-05-06
type
```
sudo <command>
```

you will be prompted for a password enter your pwd

If you need this privilges for all the later commands

```
sudo passwd

```
here enter your password you ll become root.


or
```
su passwd
```

From next time just enter
```
su
```

then your commands

---

### Post by subzero316 on 2008-05-06
Also check the community Docs on Sudo youll understand.

[<<----Sudo Docs---->>]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29")

---

### Post by creekchub on 2008-05-06
the reason i am trying to use this function is my monitor resoulution cannot be adjusted.  the best it will do is 800x600 i posted another thread and it was suggested i get into sudo but when i typed the command it stated i did not have root adm. priveleges. also make note that i am into my 3rd day of using this distro or any type of linux program.  swithching from windows. so i can use all the help and support i can get!!

---

### Post by mlentink on 2008-05-06
Could you please post what happens when you open up a terminal (Applications > Accessories> Terminal) and type:
```
sudo su
```

---

### Post by Joeb454 on 2008-05-06
Hmm..sounds odd, almost like something messed up on the install...

What is the exact error you get when you try to do a command as sudo?

---

### Post by creekchub on 2008-05-06
here is exactly what i tried last eve.  

sudo dpkg-reconfigure xserv-xorg

nothing happene.  so i started playing around i forgot what i typed in but when i entered it stated that i need root priveleges so i was wondering how you login in 
as adnin. while in terminal

---

### Post by jtrindle on 2008-05-06
The proper command is:
sudo dpkg-reconfigure xserver-xorg

and then you type in the password you use to log in when prompted.

However, you *should* be able to do this more easily through the desktop:
System->Administration->Screen & Graphics->Graphics Card

Click on the driver (which is probably SVGA now) and choose by manufacturer and model.  What kind of video card is it?

---

### Post by creekchub on 2008-05-06
it is an onboard video card.  nVIDIA 6100 chipset

---

### Post by NightwishFan on 2008-05-06
I have a Nvidia 6150 SE, and with the restricted nvidia drivers it runs perfectly on my 1440x900 lcd.

---

### Post by creekchub on 2008-05-07
where do i get the driver?  and exactly how do i go about installing it on this distro.  i have tried enabling the nVida accelerated graphics driver.  this appears in the task bar when i first install.. now when i enable the driver and reboot i get an error message and black screen.  so what driver and where and how do i install

---

### Post by NightwishFan on 2008-05-07
Perhaps try envy, I think it is in the repos.

---

