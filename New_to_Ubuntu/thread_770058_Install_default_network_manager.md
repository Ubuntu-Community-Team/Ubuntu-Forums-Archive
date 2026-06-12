---
title: "Install default network manager"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by riptreeper on 2008-04-27
I need help installing the default network manager. 

Thanks

---

### Post by Michael.Godawski on 2008-04-27
hi,
may I ask why the network manager is not there ?:)

If you have the Installation CD somewhere put it in, select in Software Sources the CD as an additional source and run this in terminal:
```
sudo apt-get install network-manager
```

If you have a running internet connection just enter the code into the terminal.

---

### Post by riptreeper on 2008-04-27
I installed a different network manager and It doesn't handle the network setup the way that I want. I am having trouble with my wireless network setup. 

Thanks for your help.

---

### Post by riptreeper on 2008-04-27
That didn't work. Is there anything else that I can try?

---

### Post by riptreeper on 2008-04-27
I am hitting the hay for tonight 

If anyone happens upon this and can help me get back the default network manager that runs from the top panel that would be greatly appreciated. 

Thanks.

---

### Post by .nedberg on 2008-04-27
You install it with
```
sudo apt-get install network-manager
```
or
```
sudo apt-get install network-manager-gnome
```
run it with
```
nm-applet
```

If you never uninstalled it then you do not need to reinstall it.

---

### Post by mrsteveman1 on 2008-04-27
I think it was WiCD that required the user to remove networkmanager to install it, i have seen it happen before.

---

### Post by riptreeper on 2008-04-27
Thanks a bunch. Got it back the way that I wanted it.

---

### Post by thatDougore on 2009-06-16
> **mrsteveman1 said:**
> I think it was WiCD that required the user to remove networkmanager to install it, i have seen it happen before.

I can confirm - this _just_ happened to me and before I hit "y" realized my terminal said something about removing...something. Anyway, I was able to re-install using the code listed above after opening my newly installed "WiCD" and connecting to my SSID. Or you can always plug the Ethernet in ;-)

---

