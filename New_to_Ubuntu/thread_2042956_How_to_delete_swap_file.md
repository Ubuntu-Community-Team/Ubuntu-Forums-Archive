---
title: "How to delete swap file???"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by MrPez on 2012-08-15
Hi guys, first I'll point out that I am a [I]complete newbie...

[/I]I've got a revo r3700 with 12.04 that I run xbmc on and I'm trying to fix the IP address on it so that I don't have to keep reconfiguring the remote.

I found some instructions and tried to follow them:

```
sudo vi /etc/network/interfaces
```I then added this to the file:
```
iface eth0 inet static
        address 192.168.2.102
        netmask 255.255.255.0
        gateway 192.168.2.1
```Somehow I then managed to close the file without saving and when I went in to check it made a swap file, whatever that is.

I then did it again and typed :wq to save it which seemed to work.  Problem is when I try to go into the file I get a warning that a swap file with the name /etc/network/interfaces.swp has been detected.

The proper file is there and is right, but I can't seem to delete the swap.  I've tried

```
rm -f ./etc/network/interfaces.swp
```as well as 
```
rm ./etc/network/interfaces.swp
```and have tried both without the . in front of the filename.  I don't get any warnings saying it hasn't worked, but I can still browse and see that the swap file hasn't been deleted.  There are also 4 other files named interfaces with various extensions that I guess I have inadvertently created...  

Please can someone tell me how to delete these extra files that I've created?  With it the way it is when I switch it on I don't have any network connection at all!

---

### Post by spjackson on 2012-08-15
> **MrPez said:**
> The proper file is there and is right, but I can't seem to delete the swap.  I've tried

```
rm -f ./etc/network/interfaces.swp
```as well as 
```
rm ./etc/network/interfaces.swp
```and have tried both without the . in front of the filename.  I don't get any warnings saying it hasn't worked, but I can still browse and see that the swap file hasn't been deleted.  There are also 4 other files named interfaces with various extensions that I guess I have inadvertently created...  

Please can someone tell me how to delete these extra files that I've created?  With it the way it is when I switch it on I don't have any network connection at all!
```

sudo rm /etc/network/.interfaces.swp

```As for the other files, it depends what their names are. I'm guessing that 
```

sudo rm /etc/network/interfaces.swp~

```might deal with one of them. (This is a backup file created by vi). Generally, you should **not** remove files from /etc unless you know what they are.

---

### Post by MrPez on 2012-08-16
Thanks SPJackson, that worked for the swap file
The other files in question have extensions swk, swl, swm, swn, swo  Sounds awfully like a sequence of my errors to me!  Are they ok to delete?

---

### Post by spjackson on 2012-08-16
> **MrPez said:**
> Thanks SPJackson, that worked for the swap file
The other files in question have extensions swk, swl, swm, swn, swo  Sounds awfully like a sequence of my errors to me!  Are they ok to delete?
I didn't know this before, but those files are created if you edit again and again while the swap file exists. [See here]("http://vimdoc.sourceforge.net/htmldoc/recover.html"). So yes, these are safe to be removed in the same way.

---

### Post by MrPez on 2012-08-16
Thanks for all the help, all sorted now

---

