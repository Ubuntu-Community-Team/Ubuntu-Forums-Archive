---
title: "Version for Dell inspiron 1525 core 2 duo T5550"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by afrocod on 2013-06-19
This will be my first time installing Linux and I'm completely getting rid of Vista. What I want to know is which is the latest version of ubuntu or xubuntu that has a tried and true method with the Dell Inspiron 1525 with the same specs as mine. All possible problems with the install have been well and truly worked out. I hear the Wifi and sound can be big problems, so if anyone has all ready done this and achieved success please let me know.

Specs:

Intel Core 2 Duo T5550 1.8Ghz

2GB RAM

Graphics:  Mobile Intel(R) 965 Express Chipset 358MB

Sound: Intel HD Audio HDMI and SigmaTel HD Audio Codec (I don't really understand which or if either of these are relevant)

Wifi:  Dell wireless 1490 Dual Band WLAN Mini-Card

There is probably some model numbers that I'm leaving out but I don't know the terminal command to get a hold of them.

Thanks in advance,

Cillian.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by user_of_gnomes on 2013-06-19
Did you make Vista recovery DVD's before you decided to go on this bold excursion? I'd heartily recommend that because you might end up destroying the recovery partition.

You should double the amount of RAM for Ubuntu 13.04. It nearly uses 2GB just doing regular tasks for me.
Or use Lubuntu.

---

### Post by afrocod on 2013-06-19
Great thanks. If I were to install the LTS Xubuntu instead will the same fixes work or will I have more trouble?

Oh I haven't wiped Vista yet, so that's a good idea, some recovery discs... I hadn't thought of that.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by afrocod on 2013-06-19
@ahallubuntu  All right I'm feeling better about this now. I'm actually doing this for my mothers old laptop too, that's why I'm so reluctant to go ahead and just jump in. One last question can I install from a usb drive instead of a disc?

EDIT: Nevermind I have the disc now.

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by oldfred on 2013-06-19
I only use my laptop when we travel, but I install the same 64 bit Ubuntu 12.04 as my Desktop just so they are the same. I also use gnome-panel or fallback not Unity as that seems to work a bit better, plus I have been used to the old layout.

My laptop is a 6 year old Toshiba with almost the same Intel chip - T5500 and 1.5GB of RAM. It runs the 64 bit version well, but I try not to load too may apps at once. Occasionally it does turn grey for a second or two and I know it then is using swap as swap is slow compared to RAM and I know I have opened too many apps at once. I typically have Firefox, Zim (for text files) and also maybe gedit all open at once without issue.

---

### Post by ahallubuntu on 2013-06-19
> **oldfred said:**
> I only use my laptop when we travel, but I install the same 64 bit Ubuntu 12.04 as my Desktop just so they are the same. I also use gnome-panel or fallback not Unity as that seems to work a bit better, plus I have been used to the old layout.

To clarify a little and avoid some confusion: Ubuntu calls gnome-fallback "Gnome Classic" on their session menu when you login. Oldfred and I are talking about the same thing.

---

### Post by afrocod on 2013-06-20
All right so I boot from the xubuntu cd I see the nice graphics, it ask's me to run from cd or install. I choose install, select the language. The next screen has the checks for 4.4GB hard drive space and is plugged into a power source and i'm not connected to the internet because I'm probably having that trouble with the wifi card. I hit continue and then this static screen comes up and the loading wheel just goes around and around but you can hear that the cd has stopped spinning and nothing is happening...

[[IMG]http://farm3.staticflickr.com/2873/9090098257_bd52050196_z.jpg[/IMG]]("http://www.flickr.com/photos/cillianpatrick/9090098257/")
[Untitled]("http://www.flickr.com/photos/cillianpatrick/9090098257/") by [C.P. O'Donnell]("http://www.flickr.com/people/cillianpatrick/"), on Flickr

[[img]http://farm6.staticflickr.com/5531/9092316708_cf08221a1d_z.jpg[/img]](http://www.flickr.com/photos/cillianpatrick/9092316708/)
[Untitled](http://www.flickr.com/photos/cillianpatrick/9092316708/) by [C.P. O'Donnell](http://www.flickr.com/people/cillianpatrick/), on Flickr


[[img]http://farm4.staticflickr.com/3760/9090097023_7fdfd78fed_z.jpg[/img]](http://www.flickr.com/photos/cillianpatrick/9090097023/)
[Untitled](http://www.flickr.com/photos/cillianpatrick/9090097023/) by [C.P. O'Donnell](http://www.flickr.com/people/cillianpatrick/), on Flickr


[[img]http://farm4.staticflickr.com/3689/9092315536_aa6690bd9a_z.jpg[/img]](http://www.flickr.com/photos/cillianpatrick/9092315536/)
[Untitled](http://www.flickr.com/photos/cillianpatrick/9092315536/) by [C.P. O'Donnell](http://www.flickr.com/people/cillianpatrick/), on Flickr

---

### Post by afrocod on 2013-06-20
I tested the memory and it's fine and I checked the disk for defects and it's also fine. So i'm not really sure what else it could be...

EDIT: I selected not to install third party software and that solved the problem, now i'm dealing with the wifi problem...

---

### Post by afrocod on 2013-06-20
Right so I was able to get the drivers installed with terminal commands and I've restarted but now but the wifi card is no longer detected now so i found 2 solutions 1. turn the wifi switch on and off on laptop (didn't work) and 2. use command "rfkill unblock all" (I tried this but I get "Can't open RFKILL control device: Permission denied) Am I missing something from the command that would give me permission, it didn't ask for a password or anything..

---

### Post by 3rdalbum on 2013-06-20
You need to put the word 'sudo' in front of that command.

---

### Post by Oscar_Mendizabal on 2013-09-04
Had the same issue, needed to install pulse audio volume control

code:
sudo apt-get install pavucontrol

---

### Post by Oscar_Mendizabal on 2013-09-04
then launch

code:
pavucontrol

and select hdmi output, that&#347; it!

---

