---
title: "Downloading repositories"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by kezron on 2008-09-04
Hi all, does anyone know how i can download the whole of the ubuntu repositories and put them onto DVD's? I am using my brothers internet connection at the moment as i don't have the internet myself. I have done a search but nothing suitable came up in the search. If anyone knows of a site that has instructions how to do it or knows how to do it themselves i would be grateful. I could just click on every box in the synaptic package manager but that would take far too much time to do. Any help or a point in the right direction would be very much appreciated.

Many thanks.

---

### Post by rraj.be on 2008-09-04
You dont want to download the whole repositaries.

just have a ubuntu install system where all required packages are installed.

then you can use a application known as APTonCD to copy all installed packages into a CD to make a local repsitary.

[https://wiki.ubuntu.com/APTonCD-try this link]("https://wiki.ubuntu.com/APTonCD")

---

### Post by alpage2 on 2008-09-04
The command line package manager is apt-get, and will probably do what you want. First check that you have all the necessary archives selected, then at the command line:

sudo apt-get -d *

will probably do it. The -d option means download only, so that packages are only retrieved, and not unpacked or installed.

The catch will be that the hard drive on the machine doing this will need enough disk space for them all, although I expect there will be a way to split things up with a regular expression. See man apt-get.

Alan

---

### Post by kezron on 2008-09-04
@rraj.be - yes i do want them all. I have just found a site [ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)
that has them all for hardy. There is about 8 dvd's or so i think and that's what i need. Many thanks for the suggestions, if these dvd's don't work or some other reason i will try both of your suggestions. Many thank to you both again.

---

### Post by Archmage on 2008-09-04
I think that is the stupids question of the day, but what is wrong with downloading the Ubuntu-DVD? There are all the programs that you need, beside the ones from a different desktop. But for this you could download the three of them, if you really need everything.

---

### Post by kezron on 2008-09-04
There is no need to be insulting. I have my reasons and if you you can't contribute to the thread without being insulting then don't respond at all.

---

### Post by Elfy on 2008-09-04
Maybe apt-mirror will help you, you get a copy of the packages on pc - once you have them there's no reason that you couldn't use them

[http://ubuntuforums.org/showthread.php?t=599479](http://ubuntuforums.org/showthread.php?t=599479)

I have seen other similar threads but not having a lot of luck finding them, but they are on the forum somewhere if I can find them I'll post them.

---

### Post by kezron on 2008-09-04
Thank you forestpixie, that was very helpful. I will give that a go as i have 120Gb of space which is more than enough. Thank you.

---

### Post by Cadmus on 2008-09-04
No-one is intending to be insulting, however downloading an entire repository is unusual. The reason we're interested in why you wish to do so in case there is a more elegant way you could achieve the same results.

---

### Post by hyper_ch on 2008-09-04
you know, the ubuntur repos are like 40gb? you still want to download it all?

---

### Post by Nythain on 2008-09-04
i used to keep the repos downloaded locally onto one of my hard drives...
but i thought that option went out the window with something they changed in gutsy...
would be interested to see how these techniques work out... the repos on hard drive makes that first upgrade after install so much easier :)

---

### Post by hyper_ch on 2008-09-04
Nythain: search for "mirror" on [http://www.howtoforge.com](http://www.howtoforge.com) --> there's a howto for apt-mirror

---

