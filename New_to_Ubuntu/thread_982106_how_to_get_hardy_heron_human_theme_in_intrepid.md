---
title: "how to get hardy heron human theme in intrepid ?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-11-14
hi,

now, i have intrepid ibex in my desktop. i dont like the new human theme dont know why...... i want to use hardy heron's human theme.. where can i get that theme (hardy heron human theme) ?

please help

---

### Post by phidia on 2008-11-14
Have you looked in themes (System > Preferences > Appearance)
If it's not there you could pull it off of a heron cd if you have one-I'm sure you can still download it from places like linux tracker if you don't.

Also you can search through [gnome-look themes]("http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=27bec388a659ca5cb3a697dfe2bebae6")

---

### Post by tjwoosta on 2008-11-14
just curious, whats the difference between 8.04's human theme and 8.10's human theme?

---

### Post by phidia on 2008-11-14
> **tjwoosta said:**
> just curious, whats the difference between 8.04's human theme and 8.10's human theme?


I thought the "new human" was darker in tone-but I'm not sure.

---

### Post by LowSky on 2008-11-14
It look very much the same to me... Did I miss something?

---

### Post by OrangeCrate on 2008-11-14
> **tjwoosta said:**
> just curious, whats the difference between 8.04's human theme and 8.10's human theme?

I believe the new default Human theme in Intrepid, is the Human Murrine theme from Hardy. So, there would be differences.

---

### Post by LowSky on 2008-11-14
Well that might explain it, but then again I use the same Glossy P theme since Fiesty.

---

### Post by Keen101 on 2008-11-14
I'm not sure about differences in the human theme itself, but i have noticed some differences in the human-icon-theme. For example the shutdown button is grey, it is just defaulting to the gnome shutdown icon. Very annoying for me. I might rip the hardy theme from a cd too.

The icon theme(s) can be found in /usr/share/icons

---

### Post by niccholaspage on 2008-11-14
I know how. Open up a terminal and type this:
```

wget http://lug.mtu.edu/ubuntu/pool/main/h/human-theme/human-theme_0.18_all.deb
wget http://lug.mtu.edu/ubuntu/pool/main/h/human-icon-theme/human-icon-theme_0.28_all.deb
sudo apt-get install gtk2-engines-ubuntulooks
sudo dpkg -i human*.deb

```Don't upgrade human-icon-theme and human-theme.
Apply the Human theme and it should use the 8.04 theme. 

If you don't like it, then run the following commands:
```

sudo apt-get purge human-theme human-icon-theme
sudo apt-get install human-theme human-icon-theme ubuntu-artwork

```Apply Human back again and you will be using 8.10.

---

### Post by tjwoosta on 2008-11-14
> For example the shutdown button is grey, it is just defaulting to the gnome shutdown icon.

my ubuntu 8.10 shutdown icon is still red 

this is the default human theme, the only difference is that i changed the selected items color to grey

---

### Post by Keen101 on 2008-11-17
> **tjwoosta said:**
> my ubuntu 8.10 shutdown icon is still red

umm... no.   If you notice under >System >Shutdown.... the icon is grey. Your logout icon is the one which is red. You can clearly see it in your own screenshot.

---

### Post by tjwoosta on 2008-11-17
o..

ok, i thought you were talking about the shutdown icon on the right side of the top gnome panel

---

