---
title: "Still trying to play DVDs"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by richg on 2008-09-16
I have been trying for some months to view commercial videos with my Ubuntu 8.04 desktop. The DVD icon shows on the desktop and when I try to open with Totem Movie Player, the only option, I get an error message. I hopefully have attached the scree shot.

After searching the messages, I downloaded VLC using Synaptic package manager along with other files that Synaptic suggested. VLC does not see the DVD.

Is there the equivalent of a plug and play application for viewing commercial DVDs? Thanks.

This issue and webcam use are the last two items, using Linux. to get running since I left Windows a few years ago.

Rich

---

### Post by danbuter on 2008-09-16
You need libdvdcss2, look it up in google along with the word ubuntu.

---

### Post by richg on 2008-09-16
Thanks but I would like to do this from the Ubuntu repositories or Synaptic.
The results of a Google search always leaves more questions. I know this from experience. Maybe someone else might have a more direct answer. I am not a software type.
Cheers

Rich

---

### Post by jken146 on 2008-09-16
libdvdcss2 is available from Medibuntu.  [Add the repository]("https://help.ubuntu.com/community/Medibuntu#Adding the Repositories") and install it as you would any other package.

---

### Post by richg on 2008-09-16
> **jken146 said:**
> libdvdcss2 is available from Medibuntu.  [Add the repository]("https://help.ubuntu.com/community/Medibuntu#Adding the Repositories") and install it as you would any other package.

Thanks for the answer.
Still confusing. Do you mean install Medibuntu and then install libdvdcss2?

I clicked on the link and Medibuntu does not seem to be straight forward. Techiesh language is used. I would rather not have to mess up my PC.

By the way, I still do not know how to use the thank you option. I did it twice but that was pure luck.

Rich

---

### Post by richg on 2008-09-16
The more I think about it, the more I realize I am trying to run an operating system. I want to only run applications. Maybe Ubuntu will eventually get to the point of including a DVD player application without having to through a bunch of mumbo jumbo. Ubuntu is supposed to be trying to reach the masses according to all the Hype I read on the 'Net.
I can live with it. I can slip in the Linspire 5.1.427 hard drive which has a good DVD player. A little inconvenient thats all.

Cheers

---

### Post by crjackson on 2008-09-16
If your running 32-bit Hardy, open up a terminal and past in the following code:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by jken146 on 2008-09-16
Yes, I do mean add the Mudibuntu repository (don't worry, this is perfectly safe!) and then install libdvdcss2.  That's the package that allows you to decrypt commercial DVDs so that they can be played by Totem, VLC etc.

Following the instructions that I linked to, first you open a terminal (Applications -> Accessories -> Terminal) and then copy and paste these 3 commands:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```

---

### Post by Tatty on 2008-09-16
> **richg said:**
> Maybe Ubuntu will eventually get to the point of including a DVD player application without having to through a bunch of mumbo jumbo. Ubuntu is supposed to be trying to reach the masses according to all the Hype I read on the 'Net.

No.  There is a legal grey area surrounding DVD decryption which is why it is not included by default in a Ubuntu install.

It is very unlikely that Ubuntu would get sued for including it (and even less likely that any case would win), but it is still possible.  So Canonical are taking the sensible option of steering clear of any potential problem with this.

If this legal grey area did not exist then adding the dvd decryption support out of the box would be a very simple thing to do and would already happen.


All you have to do is

1. Add the medibuntu repo to your list of repos.
2. Install libdvdcss2 via the package manager

Just follow the guide posted above by jken146 - the medibuntu repo is a pretty standard repo that most ubuntu users add :)

---

### Post by pyromanic123boom on 2008-09-16
Yeah, you need sections of medibuntu to play dvds. I use LinDVD as my dvd program...totem is kinda like the equivalent of a blahish windows media player or something generic.

LinDVD is only available to manufacturers, though..so unless you bought a ubuntu computer you might have a hard time finding it. Oh0 found the t0rrent for the deb package. It was generated from the rpm.
Go to this google search [http://www.google.com/search?hl=en&q=lindvd+deb+torrent&btnG=Search](http://www.google.com/search?hl=en&q=lindvd+deb+torrent&btnG=Search) and it's the 3rd one from the top. Demonoid. Can't get in trouble for posting a google search result..

---

### Post by Tatty on 2008-09-16
> **pyromanic123boom said:**
> Yeah, you need sections of medibuntu to play dvds. I use LinDVD as my dvd program...totem is kinda like the equivalent of a blahish windows media player or something generic.

LinDVD is only available to manufacturers, though..so unless you bought a ubuntu computer you might have a hard time finding it. Oh0 found the t0rrent for the deb package. It was generated from the rpm.
Go to this google search [http://www.google.com/search?hl=en&q=lindvd+deb+torrent&btnG=Search](http://www.google.com/search?hl=en&q=lindvd+deb+torrent&btnG=Search) and it's the 3rd one from the top. Demonoid. Can't get in trouble for posting a google search result..

Alternatively use VLC :)

---

### Post by Jim_in_Omaha on 2008-09-23
This worked for me on 64-bit for playing DVD's. And I might say it plays them very well....


> **jken146 said:**
> Yes, I do mean add the Mudibuntu repository (don't worry, this is perfectly safe!) and then install libdvdcss2.  That's the package that allows you to decrypt commercial DVDs so that they can be played by Totem, VLC etc.

Following the instructions that I linked to, first you open a terminal (Applications -> Accessories -> Terminal) and then copy and paste these 3 commands:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```

---

