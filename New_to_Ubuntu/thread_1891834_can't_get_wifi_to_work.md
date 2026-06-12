---
title: "can't get wifi to work"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by topguns on 2011-12-06
I have a HP Pavilion G7-1167dx laptop 

dual boot. with ubuntu 11.10 and windows 7 

64 bit machine
4gb RAM
500gb HHD
1.8 GHz quad core ( amd phenom II quad core) 

the problem is that I can get the wifi card to work just fine with windows 7. but when i boot into ubuntu I noticed that i can't enable the wifi card. the light should be white but instead it;s orange which means that the wifi card is not enable. i tried activating the card by pushing the button but nothing happens. I installed the additional drivers and rebooted the machine but still it did nothing. the only way for me to get Internet is to plug it into a Ethernet cord. so i need some one's help.... to help me get my wifi card working again. so i can be able to use ubuntu again.

---

### Post by BC59 on 2011-12-06
Go here and follow the instructions:
[http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](http://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/)

---

### Post by pierreyy on 2011-12-06
hey this is what ur lookin for:

**cp**: The **cp** command will make a copy of a file for you.  Example:  **"cp file foo"**  will make an exact copy of "file" and name it "foo", but the file  "file" will still be there. If you are copying a directory, you must use  **"cp -r directory foo"** (copy recursively). (To  understand what "recursively" means, think of it this way: to copy the  directory and all its files and subdirectories and all their files and  subdirectories of the subdirectories and all their files, and on and on,  "recursively")

the link is:
```
https://help.ubuntu.com/community/UsingTheTerminal
```check it out.

ps this is done using  the terminal.

---

### Post by BC59 on 2011-12-06
> **pierreyy said:**
> hey this is what ur lookin for:

**cp**: The **cp** command will make a copy of a file for you.  Example:  **"cp file foo"**  will make an exact copy of "file" and name it "foo", but the file  "file" will still be there. If you are copying a directory, you must use  **"cp -r directory foo"** (copy recursively). (To  understand what "recursively" means, think of it this way: to copy the  directory and all its files and subdirectories and all their files and  subdirectories of the subdirectories and all their files, and on and on,  "recursively")

the link is:
```
https://help.ubuntu.com/community/UsingTheTerminal
```check it out.

ps this is done using  the terminal.

Wrong thread!

---

### Post by pierreyy on 2011-12-06
sry wrong thread :P *walks away slowly as if nothing has happened*

---

### Post by Martyn Thompson on 2011-12-06
I don't know a lot about Ubuntu but do use it. 

If Ubuntu doesn't have the appropriate drivers then the card will not work.  This is probably a relatively easy 'fix' (if it works) and avoids using the command line. 

Try going to System > Administration > Additional Drivers and see if you can download/install any proprietary drivers for the WiFi card. 

It might be the only option open to you at the moment.  You would need to be connected through your LAN cable until it was installed (obviously!). 

Hope this helps.  Sorry I cannot be of further help.

---

### Post by BC59 on 2011-12-06
> **Martyn Thompson said:**
> I don't know a lot about Ubuntu but do use it. 

If Ubuntu doesn't have the appropriate drivers then the card will not work.  This is probably a relatively easy 'fix' (if it works) and avoids using the command line. 

Try going to System > Administration > Additional Drivers and see if you can download/install any proprietary drivers for the WiFi card. 

It might be the only option open to you at the moment.  You would need to be connected through your LAN cable until it was installed (obviously!). 

Hope this helps.  Sorry I cannot be of further help.

He said that installed the proprietary drivers. In his case these drivers are not working and he needs some extra. It's unusual but happens.

---

### Post by Martyn Thompson on 2011-12-06
> **BC59 said:**
> He said that installed the proprietary drivers. In his case these drivers are not working and he needs some extra. It's unusual but happens.

Ooops - yes - sorry about that. 

After I upgraded to latest 11.10 the settings were changed from managed network to unmanaged.  


Might be worth checking this isn't the case with your setup.  If you are new you might prefer to avoid the command line so try: 

ALT + F2 then type into the box:

```
gksu gedit /etc/NetworkManager/NetworkMangager.conf
```

After asking for your password a new window will appear with the file already loaded into it.  Look for an entry that says:

managed = false 

and change it to

managed = true

Log out/in (or reboot) and see if that helps.

---

### Post by bkratz on 2011-12-06
I would think a good place to start would be to find out what the cards involved are:

If you post the output of 

lspci -nnk | grep -iA2 net

It will show both the wired and wireless devices involved

---

