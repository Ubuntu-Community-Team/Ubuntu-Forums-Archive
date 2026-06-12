---
title: "cant install/remove flash"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by lion2 on 2014-04-30
hello ,
i am new to ubuntu and dont know many things yet .. i first thing i would like to do after installing ubuntu is flash since its very importent .i wanted to install it through dowload center , so i gone there and clicked install and it download but keeps on saying " Applying changes for 30-40 mins . after restart its saying its installed but its not as i checked , i want to remove it but now its saying " Removing " not even moving a bit .

please help !!

solved . please close the thread !!

no its not true , please help flash not working ...

---

### Post by Elfy on 2014-04-30
stop bumping this thread with pointless posts - people will just look elsewhere - edit your first post - your image gives me a 403 forbidden

---

### Post by LastDino on 2014-04-30
Is it happening with just flash or other things as well? 
Try changing preferred server/mirror settings in 
>settings>software and update>Ubuntu software>download from>other>best server>select best server 
Give your password when asked
while saving it will ask for updating software list, click ok/yes.

This will look for best server in your location and update the available software list.

I've noticed this problem when packages are not downloaded correctly due to slow download or broken downloads. I also suggest trying ''Synaptic package manager'' 
Try to install Flash from there if this problem is limited to Flash only.

---

### Post by pfeiffep on 2014-04-30
> **lion2 said:**
> hello ,
i am new to ubuntu and dont know many things yet .. i first thing i would like to do after installing ubuntu is flash since its very importent .i wanted to install it through dowload center , so i gone there and clicked install and it download but keeps on saying " Applying changes for 30-40 mins . after restart its saying its installed but its not as i checked , i want to remove it but now its saying " Removing " not even moving a bit .

please help !!

solved . please close the thread !!

no its not true , please help flash not working ...

If you are using Chromium read [this]("http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html")

If not post some particulars about your system ... OS, browser, hardware

This forum has loads of folks who can help, but you must help us to help you!

---

### Post by Elfy on 2014-04-30
Make sure that the ubuntu software centre is closed. IF it is doing something else - do not just close it - wait.

Open a terminal, Super(windows key) + T 

Copy and paste this command in 

```
sudo apt-get install flashplugin-installer
```

Press enter - when prompted - put in your password and then enter again, let it do what it needs to.

If there is an issue - copy and paste the WHOLE terminal output to a new post here.

When you enter your password you WILL not see it - this is normal.

---

