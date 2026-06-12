---
title: "HOWTO: Setup your Logitech MX510 for fancy use in Breezy and Dapper"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by [D-Tail] on 2006-06-13
Following the HOWTO guides [here (5.10)](http://www.ubuntuforums.org/showthread.php?t=65471) and [Here (6.06)](http://www.ubuntuforums.org/showthread.php?t=188302), I got some fancy stuff working for the extra mouse buttons for those mice. Assuming you've managed to set up your mouse correctly, according to the two previously mentioned threads, I'll show you now how to add neat functionality to it all.

First off, if you have a cool 3D accelerated card and you're eager to use it, try downloading 3ddesktop from the Universe repository, by doing:```
sudo apt-get install 3ddesktop
```It comes with a standard conf file, located in /etc/3ddesktop/3ddesktop.conf, but here's mine for your convenience:```
autoacquire 0
texturesize 1024
wm gnome2

#
# Example views (use by doing: '3ddesk --view=<viewname>')
#

view			default    ## this is the default if no --view specified
zoom			on
mode			cylinder
changespeed		64
show_digit		on
digit_size		100
digit_color		green
reverse_mousewheel	true
alt_mousebuttons	true
use_breathing		true

view         goright
zoom         off
mode         cylinder
gotoright    on


view         goleft
zoom         off
mode         cylinder
gotoleft     on


view         slide
zoom         off
mode         linear
digit_size   100
digit_color  gray
linear_spacing 0.0


view         nozoom
zoom         off
mode         viewmaster
digit_size   100
digit_color  gray


view         linear
mode         linear
digit_color  yellow
linear_spacing 0.0


view         linearzip
mode         linear
linear_spacing 19.0
depth        5
digit_size   200
digit_color  blue


view         bigmoney
mode         priceisright
depth        10
digit_color  purple
digit_size   150
```Well now. Now that's setup easily, you can experiment a bit with 3ddesktop, by opening a terminal and saying:```
3ddesk --view==<viewname>
```Back to the Logitech thing now. I myself have an MX510 optical USB mouse, so I'll take that as a reference point. Usually the top button is identified by 'mouse button 8'. The two cruise buttons take numbers 9 (up) and 10 (down) respectively, but they're rather useless as you've got that nice 'n' shiny mousewheel. So, let's remap those three buttons.

From Windows experiences, the top button was normally used as a task switcher. So what would we make out of this? Yes, you've got it right: a desktop switcher! Fire up your favourite text editor and paste the following:```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"/usr/bin/3ddesk"
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Prior]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Next]""
  m:0x0 + b:10
```Save this text file as ~/.xbindkeysrc and type the following from your terminal:```
:~$ xbindkeys
```This will bring the keybindings, just made in ~/.xbindkeysrc in effect. What do we see in the .xbindkeysrc file:[list][*]Button 6 is mapped to the left alt and cursor left key. This makes Firefox and Nautilus go back one page in history[*]Button 7 is mapped to th left alt and cursor right key. This makes Firefox and Nautilus go forward one page in history (this one and the previous were already in this file, if you followed the two tutorials I mentioned before)[*]Now, the new stuff: button 8 is mapped to the Prior key. Notice that you should write this as BRACKET_OPEN Prior BRACKET_CLOSE and a backslash before this. In other words, Prior should start with a capital P. In reality, this is the page up key from your keyboard. It will make Firefox, Nautilus and all those other programs go up one page[*]Button 9 is mapped to the [Next] key, this is the opposite of the [Prior] key: page down. Note that Next should also be written with a capital N, be in brackets and have a preceding slash[*]Button 10 will be mapped to /usr/bin/3ddeskd, which fires up the default view. Using my conf file and your scroll wheel, this is pretty nifty desktop switching -- have fun showing to your friends![/list]Well, so far this first tutorial of mine, thanks all for reading and I'm awaiting your comments and criticism! :D

---

### Post by Cyraxzz on 2006-06-25
Would this work for my MX518 mouse?

---

### Post by [D-Tail] on 2006-07-24
> **Cyraxzz said:**
> Would this work for my MX518 mouse?Hey man, sorry for the late reply. But let's head on to the important stuff: I think you'd have to change some things in for example the xorg.conf file, in order to get your mouse working and correctly recognised (also, to make all buttons work uniquely). When you've done that, it's just a matter of assigning in a same way as I described in my earlier message. I reckon it'd work right away, though, since the mice are intrinsically the same - safe that the 518 is a gamer's edition, which would differ a bit with the 510 in programs like WinXP. Good luck though - and let me please know if you managed to get it all up and running :)

---

