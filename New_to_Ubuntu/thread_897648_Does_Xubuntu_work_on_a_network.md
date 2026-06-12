---
title: "Does Xubuntu work on a network??"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by mark.tj on 2008-08-22
Its probably a silly question but I just installed Xubuntu on an old laptop that used to struggle with XP (runs fantastic by the way I would recommend it to anyone) trouble is I cannot see any way that I could connect to other computers on the network. Although the wireless connection is OK and it has Internet.

I have a LAN storage device and a server, its not that it is unable to see them its just that I can see no way of making it see them.

How do you do this? Or could this be a limitation for Xubuntu, shame if it is because it will do everything else I want it to although not even tried to get the Vodafone 3g working yet!!!!!

---

### Post by tangibleorange on 2008-08-22
what happens if you type the address of your server in thunar's (file manager) address bar. if the bar is not there by default, it is probably in one the drop-down menus. i'm afraid i don't use thunar so i don't know.

---

### Post by mark.tj on 2008-08-22
Thanks, just tried that, you have to enable it within the View menu, basically nothing happens.

The address of my server on all the other computers here (Windows XP, Vista and Ubuntu) is //hal6/ (I have tried both left and right leaning slashes but neither seem to work). 

Its as though it is only designed to see itself

---

### Post by tangibleorange on 2008-08-22
when you say server, what kind of server is it. A samba server (windows file sharing), a LAMP server?

---

### Post by mark.tj on 2008-08-22
Server is a bit grand its being used like a spare hard drive at the moment. Just another computer that happens to be an IBM server but is running desktop Ubuntu without any keyboard, screen etc. 2 drives but RAID switched off. All the other computers can see it no problem.

---

### Post by xouns on 2008-08-22
\\bar\ is a windows network name, isn't it? Try the ip-adress in the adressbar.

I'm wondering to, would networking work with ubuntu, and if yes, how?

---

### Post by xouns on 2008-08-22
nvm, misread the post...

---

### Post by OffAxis on 2008-08-22
xubuntu doesn't come with a native network browsing gui (you can still use the command line, though)

```
man smbclient
```
if you want to read up on it.

Otherwise, a lot of people use pyneighborhood.

```
sudo apt-get install pyneighborhood
```

---

### Post by mark.tj on 2008-08-22
pyneighborhood seems to work although everything fails to mount for some reason at the moment.
I will read up on this later this evening thank you for pointing me in the right direction it is much appreciated.

---

### Post by Gannon8 on 2008-08-22
Does xubuntu even come with samba pre-installed? On Ubuntu I needed to install samba before doing anything. Try:
```
sudo apt-get install samba
```
Though dependencies may have forced you to install it anyway.

If that does not work try the other GUI.

---

### Post by tangibleorange on 2008-08-22
> **Gannon8 said:**
> Does xubuntu even come with samba pre-installed? On Ubuntu I needed to install samba before doing anything. Try:
```
sudo apt-get install samba
```
Though dependencies may have forced you to install it anyway.

If that does not work try the other GUI.

you only need the samba package if you plan on sharing files to other PCs from the xubuntu box - not accessing shared files.

to access you server from the CLI, you need the following command:

```
smbclient //hal6/
```

---

### Post by OffAxis on 2008-08-22
Here's the 'definitive' thread on the forum:
[http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba](http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba)

It's targeted at Edgy, but still has application.

And here's the FAQ section on xfce's site. The question answering 'Why is there no native network browsing?' is the very last one.

[http://thunar.xfce.org/pwiki/documentation/faq](http://thunar.xfce.org/pwiki/documentation/faq)

---

### Post by mark.tj on 2008-08-22
Looks like the answer to me I will swot up on it later it seems just about anything is possible with Ubuntu it just takes a while to delve in and discover it all. Trouble is I do it all, get it working then forget how I did it!!

This functionality however should be there as standard in Xubuntu, I can't think of any computer especially a laptop that does not need to connect to other computers at some point, or maybe thats just me. 

Anyway thanks to everyone for taking the time to help.

---

