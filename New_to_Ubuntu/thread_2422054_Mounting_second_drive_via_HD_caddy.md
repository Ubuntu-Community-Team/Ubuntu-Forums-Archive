---
title: "Mounting second drive via HD caddy"
date: 2019-07-01
forum: New to Ubuntu
---

### Post by nazih2 on 2019-07-01
I want to add 2nd hdd via CD/DVD caddy..
but I can't mount my hdd on ubuntu 18.04 
any suggestions?!

---

### Post by #&amp;thj^% on 2019-07-01
It could be some sort of weird incompatibility issue. What is the caddy used? Make/Model
 Do you have the option to try the caddy and the HDD with a different computer, even a desktop one, just to see if you still have the same issue.

---

### Post by nazih2 on 2019-07-01
Caddy Model: Serial ATA
when i connect the caddy it turns the blue light that it is connected...but it doesn't mount on gParted..

---

### Post by #&amp;thj^% on 2019-07-01
Caddy Model: Serial ATA is not what I asked for. Make/Model=Brand Name && Model.
Some of the CD/DVD Caddy's out there won't work with a Hard Drive over 500 Gigs, A 500GB drive could consume more power than a 1TB drive and vice versa. 
And an Import question>>Is the HardDrive formatted? (Just a question to answer and not take action on)
EDIT Maybe we can see with:
```
[COLOR="#FF0000"]inxi -d[/COLOR]
Drives:
  Local Storage: total: 465.76 GiB used: 25.21 GiB (5.4%) 
  ID-1: /dev/sda vendor: Toshiba model: MK5065GSX size: 465.76 GiB 
  [B]Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GT80N dev-links: cdrom 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram [/B]

```

---

### Post by nazih2 on 2019-07-01
[TISHRIC 2018 Hot Sale For Notebook ODD 2.5"SSD Optibay Aluminum Universal 2nd HDD DVDCaddy 9.5mm SATA 3.0 Case Enclosure Optibay]("https://www.aliexpress.com/item/TISHRIC-2018-Hot-Sale-For-Notebook-ODD-2-5-SSD-Optibay-Aluminum-Universal-2nd-HDD-DVDCaddy/32868199381.html?spm=a2g0s.9042311.0.0.6b9c33edJwzERy")

the hdd is 500 GB 5v 700mA
the disk is formatted with ext4

---

### Post by #&amp;thj^% on 2019-07-01
There you go, it shows on that link that there is a couple of switch settings to try if the laptop is not seeing the Hard Drive: IE "A" "B" and "C", and once its working don't move it any more.

---

### Post by nazih2 on 2019-07-01
there is only two options with the switch!
both give blue light in the caddy.. both make the hdd a little bit hot like it is working.. both can't be seen in gParted!

---

### Post by nazih2 on 2019-07-06
any other suggestions?!

---

