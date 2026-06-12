---
title: "connecting to windows share"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Doormat on 2008-05-01
How can I connect to a windows share in ubuntu 8.04?

---

### Post by damis648 on 2008-05-01
Click "Places" in the panel then click "Network". Click "Windows Network" and then select the workgroup and computer. To save this connection, click "Places" again and then click "connect to server". Then choose the "windows share " option and fill in the fields.

---

### Post by Doormat on 2008-05-01
I have the folder shared on my windows machine but I can't see it under windows network? Is there any way to manually connect ( I know the ip, username, password)

---

### Post by Monicker on 2008-05-01
> **Doormat said:**
> I have the folder shared on my windows machine but I can't see it under windows network? Is there any way to manually connect ( I know the ip, username, password)

Places -> Connect to Server

Select Windows Share for the Service Type

---

### Post by bilal.17 on 2008-05-01
install samba and then go to system->administration and click samba to configure your network to connect to , then go to places->network

---

### Post by Monicker on 2008-05-01
> **bilal.17 said:**
> install samba and then go to system->administration and click samba to configure your network to connect to , then go to places->network

You don't need to install Samba to access a Windows share from Ubuntu.  Samba  is only necessary if he wants to share files from his Ubuntu machine to a Windows machine.

---

### Post by bcre8iv on 2008-05-01
I need help with this too.
I have a Ubuntu desktop connected by wire to my router.

My Vista laptop connects wirelessly to the network.

Samba is installed on my ubuntu machine, but there is no option for it under system > administration.

I tried to create a shared folder on my ubuntu desktop but it says I don't have permission to change it to shared.

I've searched and read many posts, none seem to be specific to Ubuntu 8.04.

Please help, I'm a complete nube.

When I go into my network places on ubuntu I can see my laptop with the shared drive, but when I click on them nothing shows up.
I did share them on my vista machine.

My Vista machine can't even see my ubuntu.

---

### Post by Monicker on 2008-05-01
> **bcre8iv said:**
> I need help with this too.
I have a Ubuntu desktop connected by wire to my router.

My Vista laptop connects wirelessly to the network.

Samba is installed on my ubuntu machine, but there is no option for it under system > administration.

I tried to create a shared folder on my ubuntu desktop but it says I don't have permission to change it to shared.

I've searched and read many posts, none seem to be specific to Ubuntu 8.04.

Please help, I'm a complete nube.

When I go into my network places on ubuntu I can see my laptop with the shared drive, but when I click on them nothing shows up.
I did share them on my vista machine.

My Vista machine can't even see my ubuntu.

Was it a "create usershares" error when you tried to share from Ubuntu?  If so, look at the Samba Shares section here:  [http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

You should be able to connect to Vista by going to Places -> Connect to Server, as mentioned previously in this thread.

---

### Post by bcre8iv on 2008-05-02
Ok, after reboot I was able to create the share, but I still can't read my windows shares with gnome desktop.

However, I downloaded the KDE desktop and for whatever reason, everything works fine there.

So I guess I'm real close.... 

Either way, I don't mind using KDE. I think I like KDE better.

---

### Post by bradandersen on 2008-05-26
> **damis648 said:**
> Click "Places" in the panel then click "Network". Click "Windows Network" and then select the workgroup and computer. To save this connection, click "Places" again and then click "connect to server". Then choose the "windows share " option and fill in the fields.
Okay,
  I've installed Mythbuntu and there is no "Places" tab.  How can I get this "Places" tab added to Mythbuntu.  I want to be able to browse the "Network".
Thanks,
Brad

---

### Post by bradandersen on 2008-05-26
> **bradandersen said:**
> Okay,
  I've installed Mythbuntu and there is no "Places" tab.  How can I get this "Places" tab added to Mythbuntu.  I want to be able to browse the "Network".
Thanks,
Brad
P.S. I've checked the "Ubuntu Desktop" option in MythTV Control Center, but it didn't install a "Places" tab.  It also doesn't appear to use Nautilus as it's file browser.  I will try to install Nautilus.

Brad

---

### Post by bradandersen on 2008-05-26
> **bradandersen said:**
> P.S. I've checked the "Ubuntu Desktop" option in MythTV Control Center, but it didn't install a "Places" tab.  It also doesn't appear to use Nautilus as it's file browser.  I will try to install Nautilus.

Brad
Mythbuntu used the file browser "Thunar", but Nautilus is installed.  How do I make Nautilus the default file browser?  With Nautilus I'm able to browse the Windows network running "sudo nautilus" from a terminal.

Brad

---

### Post by bradandersen on 2008-05-26
> **bradandersen said:**
> P.S. I've checked the "Ubuntu Desktop" option in MythTV Control Center, but it didn't install a "Places" tab.  It also doesn't appear to use Nautilus as it's file browser.  I will try to install Nautilus.

Brad
Mythbuntu used the file browser "Thunar", but Nautilus is installed.  How do I make Nautilus the default file browser?  With Nautilus I'm able to browse the Windows network running "sudo nautilus" from a terminal.  You can also use "ALT+TAB" to switch application under Nautilus - great when you are ripping and want to use your computer.

Brad

---

