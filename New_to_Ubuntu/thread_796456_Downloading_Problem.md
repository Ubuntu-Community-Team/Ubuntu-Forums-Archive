---
title: "Downloading Problem"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Tex786 on 2008-05-16
Hi Everyone.

I am in the process of downloading xubuntu alternate ISO and I have a problem.

xubuntu is 558 MB and my xubuntu when done downloading says its 557 MB. When I try to install as i have doen today with a CD that i made witht he missing MB it would not install. It said that the Linux Generic Kernal would not install or that it had some sort of error.

Would this downloading problem be due to my connection or would it be my internet provicer?

I don't know what to think at this momment, so i thought i would post here.

---

### Post by shifty_powers on 2008-05-16
two options.

1). use a torrent download, as it has error correction/checking and it will validate the download.

2). you can get a free cd shipped to yyou from canonical, but it might take a week or tow ;)

(oh and by the way use something like imgburn to burn the cd, so that you can check the md5 checksum;))

---

### Post by Tex786 on 2008-05-16
I just tryed downloading it again and in the K3B CDburning program it says the file size is 557.7!

Help :(

---

### Post by Tex786 on 2008-05-16
> **shifty_powers said:**
> two options.

 use a torrent download, as it has error correction/checking and it will validate the download.



Whats that?

I am really new.

---

### Post by shifty_powers on 2008-05-16
ok go to [http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/xubuntu-8.04-alternate-i386.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/xubuntu-8.04-alternate-i386.iso.torrent)

clikc on it and download the torrent to your desktop.

go and get utorrent, (google it).

install it and double click on the torrent file you downloaded ;)

---

### Post by Tex786 on 2008-05-16
> **shifty_powers said:**
> ok go to [http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/xubuntu-8.04-alternate-i386.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/xubuntu-8.04-alternate-i386.iso.torrent)

clikc on it and download the torrent to your desktop.

go and get utorrent, (google it).

install it and double click on the torrent file you downloaded ;)

How do i use torrent??

i'am still wet behind my ubuntu ears.

---

### Post by shifty_powers on 2008-05-16
heh ok, first thing first, i was assuming you were still in windows, yes?

---

### Post by linux phreak on 2008-05-16
Did you burn the file as an image?.Burn it at a slow speed as well like 10x.After that boot from the cd and then check for errors which is a feature included in the xubuntu CD.It comes up in the first menu after you boot from the cd.

---

### Post by Tex786 on 2008-05-16
> **shifty_powers said:**
> heh ok, first thing first, i was assuming you were still in windows, yes?

I am on my laptop witch has Ubuntu 8.04.

I am installing xubuntu on my wife's computer.

---

### Post by linux phreak on 2008-05-16
Right click on the .torrent file you downloaded and select open with, then choose transmission.The download will start soon.

---

### Post by shifty_powers on 2008-05-16
there we go ;)

---

### Post by Wraith Hunter X on 2008-05-16
I would request a free cd...if you have the time to...

---

### Post by aimpau on 2008-05-16
I think the free CD only applies to Ubuntu and Kubuntu, not Xubuntu.

---

### Post by dizee on 2008-05-16
Check the md5sum before you burn the disc, this will tell you if it downloaded ok. ```
md5sum xubuntu-8.04-alternate-i386.iso
```
It should give you
```
4f398cd35eaf297347f18634a5be5d77
```
If it does, the download was successful (if you're using K3B I think it does this anyway). Burn it at a slow speed (I'd recommend no more than 4x) and verify it for errors when you boot up with it.

As far as I know Shipit will provide Ubuntu, Kubuntu, Edubuntu and Ubuntu Server but not Xubuntu.

---

### Post by IcedDante on 2008-05-16
Tex- let me just say that before you go downloading it again, verify that your download was unsuccessful with Dizee's instructions, as a corrupted download is a more unlikely scenario.

---

