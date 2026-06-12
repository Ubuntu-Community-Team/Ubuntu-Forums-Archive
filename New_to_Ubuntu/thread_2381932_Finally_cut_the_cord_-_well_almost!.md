---
title: "Finally cut the cord - well almost!"
date: 2018-01-06
forum: New to Ubuntu
---

### Post by jayram on 2018-01-06
I started tinkering around with linux 3 or 4 years ago having used Windows for 20 years.
Having seen Ubuntu 17.10 and tested it out in a VM, it was finally enough to persuade me that it's time to switch to Ubuntu as my main desktop. 
Unfortunately, when trying to install 17.10 on a second hard drive so that I could dual boot, every time I tried to install, two very strange things happened.

1) the n key would not work - every time, just that one key,
2) the password I entered at set up was never recognised. 

Eventually gave up, but did manage to set up dual boot for 16.04. 

Couldn't really find much on the two errors that solved my problem - I really do want 17.10, but might have to wait until it's LTS.. unless someone knows how to fix those two issues :)

Regardless - enjoying 16.04.

---

### Post by Xian on 2018-01-06
Regarding the keyboard:

1. If [COLOR=#000000]numlock is turned on -- turn it off and see if you can use the 'n' key.
2. Issue this command in a terminal and be sure you have selected the correct keyboard:

[/COLOR]```
[FONT=arial][COLOR=#242729]sudo dpkg-reconfigure keyboard-configuration[/COLOR][/FONT]
```

---

### Post by HermanAB on 2018-01-07
About once in ten years, my keyboard setup goes wonky and one or two keys disappear.  I don't know whether this is just a very rare bug in X, or a cosmic ray, or simply because a black cat crossed the road under a full moon...

When all else fails, you can pop up an on-screen keyboard to get the n key:
[https://help.gnome.org/users/gnome-help/stable/keyboard-osk.html.en](https://help.gnome.org/users/gnome-help/stable/keyboard-osk.html.en)

Then, you can use xev to find the key code for the n key and reset it to itself with xmodmap.

---

### Post by jayram on 2018-01-07
> **Xian said:**
> Regarding the keyboard:

1. If [COLOR=#000000]numlock is turned on -- turn it off and see if you can use the 'n' key.
2. Issue this command in a terminal and be sure you have selected the correct keyboard:

[/COLOR]```
[FONT=arial][COLOR=#242729]sudo dpkg-reconfigure keyboard-configuration[/COLOR][/FONT]
```

Thanks - I was going to reply saying that I could not log in to get to the terminal (point 2) then realised you can do this from the grub... is there a way of using the on screen keyboard from the grub as without the 'n' key I can type the command.  I might try a different computer to see if I can get 17.10 working, but actually 16.04 is working so well in dual boot right now that I am going to keep it as my main system until 17.10 becomes LTS (or whatever the next LTS version is).

cheers!

John

---

### Post by HermanAB on 2018-01-07
If sshd is running, then you can log in from another machine to fix it.

Wait - think!  If it is already screwed up in grub, then the problem has nothing to do with Linux, since Linux isn't booted yet.

---

### Post by jayram on 2018-01-07
> **HermanAB said:**
> If sshd is running, then you can log in from another machine to fix it.

Wait - think!  If it is already screwed up in grub, then the problem has nothing to do with Linux, since Linux isn't booted yet.

Hi,

The first problems only start once the 17.10 install starts.  I can't even use the n key to enter my name in the setup, so I just used a username without an 'n' in it.
The second problem then occurs on the login screen once installed.

---

### Post by Impavidus on 2018-01-07
> **jayram said:**
> ... but actually 16.04 is working so well in dual boot right now that I am going to keep it as my main system until 17.10 becomes LTS (or whatever the next LTS version is).

17.10 is not an LTS release and will never be. The next LTS release will be 18.04 and will be released in April. Ubuntu version numbers are just year and month of release. An upgrade from 16.04 to 18.04 should be offered around July, but some prefer clean installs over upgrades.

---

### Post by jayram on 2018-01-07
> **Impavidus said:**
> 17.10 is not an LTS release and will never be. The next LTS release will be 18.04 and will be released in April. Ubuntu version numbers are just year and month of release. An upgrade from 16.04 to 18.04 should be offered around July, but some prefer clean installs over upgrades.

Thanks - I'll be sticking to 16.04 until April and then installing 18.04 fresh. Nearly all my data is in the cloud and it's easy enough to reinstall any application I need.
I must say, enjoying the switch to Ubuntu.  Far more applications available than I expected.  Determined not to use wine and just keep a dual boot of windows for Star Citizen :)

---

### Post by mikewhatever on 2018-01-07
What does it mean "cut the cord - well almost"? It can't be both cut and uncut at the same time, and almost cut is definitely not cut.
Make up your mind. :)

PS: Either way, welcome to the club.

---

