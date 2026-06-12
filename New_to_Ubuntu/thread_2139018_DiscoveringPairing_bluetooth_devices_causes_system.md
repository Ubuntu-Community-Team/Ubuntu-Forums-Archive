---
title: "Discovering/Pairing bluetooth devices causes system to crash"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by stevesy on 2013-04-25
Looking for some pointers here if possible.  I've been having difficulty getting bluetooth going on my Dell Mini/Lubuntu 12.04 via a Dynamode v2.0 dongle. I've tried discovering/pairing bluetooth devices using blueman bluetooth manager and also gnome-bluetooth. In a lot of cases I can detect the particular bluetooth device but then when I attemp to pair with it, my system crashes and I need to power cycle the pc. In some cases though, even the detection process e.g. of my K810 Logitech Keyboard, causes the system to crash. I've googled and searched the forums for answers. Nothing has explained my situation but some of the more useful info I've found has been

[http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html](http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html)
[http://ubuntuforums.org/showthread.php?t=2101785&highlight=k810+bluetooth](http://ubuntuforums.org/showthread.php?t=2101785&highlight=k810+bluetooth)

Again, using terminal commands e.g. hcitool scan causes my system to crash.

---

### Post by stevesy on 2013-04-27
Finally got bluetooth working!  I decided to return my Dynamode dongle   and swapped it for a slightly less cheapo dongle, a Hantol v2.0 which is   around &#8364;10/$13. This solved the system hang problem.  So, if you're   experiencing crashing like I was then from my experience it's most   likely the dongle you're using.  Maybe consider upgrading it.  

I  used blueman bluetooth manager 1.23 that ships with Lubuntu 12.04 to   pair/connect my bluetooth devices.  I'll tell you the process I went   through to get my K810 keyboard working..

Open a terminal (ctrl & alt & T) and enter in *blueman-manager* to open up the bluetooth manager.

Click "enable bluetooth" on the gui that pops up.

Make  sure your K810 keyboard is discoverable and then click on the  "search"  button.  When the keyboard is detected it'll appear on the  devices  list.  Once it does, highlight it and click on "setup" to  access the  setup assistant and get pairing set up

Click on custom  pin/passkey code and enter whatever you like (e.g.0000 )  then quickly  enter this same code into the K810 keyboard (and hit  enter).  You may  need to try this a few times before it works, I got  "pairing failed"  quite a bit before succeeding.  Power cycling the  keyboard and pc may  also be worth a go if you're having no luck  pairing.  Once paired and  the device added click on "input service" and  you're good to go.  If you  trust the device which I assume you will as  it's your keyboard, click  on the yellow star to add it as such. Done.   

If none of that works try another app e.g. gnome bluetooth and/or command-line workarounds like [http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html](http://devasive.blogspot.ie/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html)

Just to mention, PC-Smartphone bluetooth works fine for me.
Still looking into Keyboard-Smartphone, devices pair but won't connect.

Hope this is of some help to those suffering from the same headache as i was.

---

