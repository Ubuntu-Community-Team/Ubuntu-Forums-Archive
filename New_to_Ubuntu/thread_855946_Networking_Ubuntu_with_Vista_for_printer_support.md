---
title: "Networking Ubuntu with Vista for printer support?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by kingkoopa2000 on 2008-07-11
Hey guys i just installed Ubuntu on my work computer. One thing i need to do and i dont know how as i am very new to ubuntu, is i need to connect this ubuntu machine to the vista machine out the front as that is where the printer is connected to. So how to i connect to the vista computer out the front? Cheers

---

### Post by Dark_Stang on 2008-07-11
Okay, get ready because this one took me two weeks to figure out.

Step 1: On vista machine. Go to your network and sharing center. Turn on network sharing. You have the option to turn on password protection as well if you'd like.

Step 2: Open your registry on the vista machine. Go to
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Contro l
Now make the Value of LMCompatibility 1, instead of 3.
Reboot the machine.

Step 3: Now on the linux machine. Run...
```
sudo apt-get install smbfs
```
This will install tools to mount windows shares.

Step 4: Now go to the linux machine.
Manual Mount with Password:
sudo mount -t smbfs //IP-Addy-For-VISTA-PC/public /path/to/desired/folder -o username=user,password=pass,iocharset=utf8

Manual Mount without Password:
sudo mount -t smbfs //Ip-Addy-For-VISTA-PC/public /path/to/desired/folder -o iocharset=utf8

If you want you can make a script with just that command in it, and add a launcher to the desktop or panel so all you have to do is run that to connect. Then you'll be connected until you reboot.

Unfortunately you cannot mount Vista machines through a file browser yet, so you will have to run those commands.

Now to add the printer on the Vista machine go System > Administration > Printing. Click new printer, it will be a windows printer via SAMBA, then click the browse button to browse for the printer. Then click next and select what brand/type of printer it is.

Aaand you're done.

---

### Post by tgyorgyi on 2008-07-12
Hi, would you be so kind and share how to do the same if the PC with the printer runs XP?

---

### Post by avtolle on 2008-07-12
> **tgyorgyi said:**
> Hi, would you be so kind and share how to do the same if the PC with the printer runs XP?
Take a look at [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

