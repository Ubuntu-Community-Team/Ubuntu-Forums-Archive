---
title: "Touchpad More Sensitive Horizontally than Verticallly"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by BlindSoothsayer on 2013-03-06
I'm dual-booting Windows Vista and Ubuntu 12.10 on a Sony Vaio laptop.  This is a fairly minor annoyance, but while running Ubuntu, the touchpad is more sensitive in the left-right direction than in the up-down direction.  While running Vista on the same machine, this is not a problem.  The system settings only allow me to change the overall sensitivity and acceleration, rather than changing the sensitivity in each dimension independently.  Any help would be much appreciated!

---

### Post by UltimateCat on 2013-03-07
I have a Sony Vaio too and I noticed that with the up and down motion I have to be closer to the edge of the pad for it to be more effective to the touch.
My Vaio is only about 4 months old.  
If you have had your Vaio for a long time the touch pad could be getting wore out- 

You have to hold down and be farther away from the space bar when you hold down to right click.

Sometimes it scrolls easily when I don't want it to-

Very rarely do I use my touchpad because I use a wireless mouse with my Vaio:-

If you keep having this annoyance try getting a wireless mouse or call Sony they have always  given me great support.
I'm using a Logitech and it works well.

Here's a video on How To Troubleshoot the touchpad with your Vaio
[http://www.youtube.com/watch?v=TJ0B8sDr5XI](http://www.youtube.com/watch?v=TJ0B8sDr5XI)

Hope this helps

---

### Post by BlindSoothsayer on 2013-03-07
It's nothing like that.  I've had my Vaio for four years, and haven't noticed any touchpad wear while running Windows.  If I move my finger around in a circle on the touchpad while running Windows, the cursor moves in a circle.  If I move my finger around in a circle on the touchpad while running Ubuntu, the cursor consistently moves in an ellipse.  This continues to happen even after rebooting or shutting down and restarting.

---

### Post by UltimateCat on 2013-03-08
If your touchpad works just fine when your Vaio is booted in Windows but behaves differently with Ubuntu; I suspect that it could potentially be a bug.

If it were a hardware functionality issue it would most likely present it's self in Windows as well.

>  only allows me to change overall sensitivity and acceleration


I find this perplexing and worth re-search.  Maybe there is mention of this in the Hardware forum:-
If there is a way around it I'll post it-
I tend not to give up easily-

I'm far from the expert at this however Scott Mueller is a really intelligent guy.  I'm learning about 2nd and 3rd generation acceleration and how motherboards work from the books he writes.
[http://forum.scottmueller.com/](http://forum.scottmueller.com/)
[http://forum.scottmueller.com/viewtopic.php?f=2&t=796](http://forum.scottmueller.com/viewtopic.php?f=2&t=796)

---

### Post by UltimateCat on 2013-03-08
Found a few things:

Fix Touchpad Vaio on Ubuntu 11.10

[http://www.youtube.com/watch?v=DW4cF7uas5U](http://www.youtube.com/watch?v=DW4cF7uas5U)
[https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty](https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty)

Setup Your VAIO F Series Touchpad in 
[http://www.chrismaddalena.com/2010/10/how-to-setup-your-vaio-f-series.html](http://www.chrismaddalena.com/2010/10/how-to-setup-your-vaio-f-series.html)
[http://smashingweb.info/sony-vaio-touch-pad-in-linux-fedora-and-ubuntu/](http://smashingweb.info/sony-vaio-touch-pad-in-linux-fedora-and-ubuntu/)

---

### Post by BlindSoothsayer on 2013-03-08
Okay, I've learned a few things.  Using the following command:

```

xinput list

```

I learn that my pointing device is identified as:

```

SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]

```

Then I can list the properties for the device using the command:

```

xinput list-props 11

```

One of the properties is listed as:

```

Synaptics Pad Resolution (295):    106, 64

```

According to [the xorg archive]("http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html"),these two numbers (106 and 64) are used to compensate unequal vertical and horizontal sensitivity.  Unfortunately, this is one of the few read-only properties of the device.  I attempted to set the VertResolution and HorizResolution options (which are used to calculated the Pad Resolution) by creating the following 50-synaptics.conf file in my /etc/X11/xorg.conf.d directory:

```

Section "InputClass"
        Identifier      "Synaptics TouchPad"
        Driver          "synaptics"
        Option         "VertResolution" "44.89"
        Option         "HorizResolution" "44.89"
EndSection

```

This fixes the touchpad issue, but unfortunately it also disables my keyboard.

---

### Post by UltimateCat on 2013-03-09
> 
This fixes the touchpad issue, but unfortunately it also disables my keyboard.                 


Jeez; when it rains it pours doesn't it-
our Vaios might have a on screen keyboard.....don't know; I'll check -

Anyway by "disables your keyboard" do you mean that you can not even type one single character (or) as in 'Power Management" the keys (backlit/backlight) won't light ?

---

### Post by BlindSoothsayer on 2013-03-09
I mean I can't type a single character.  I can use the onscreen keyboard.  When the keyboard is functional, xinput lists the following:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (05ca:18b3)                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```

After correcting the touchpad, input id's 6-10 are missing.  I guess I will just tolerate the touchpad until I figure out how to configure everything properly with X11.

---

### Post by UltimateCat on 2013-03-10
>   I guess I will just tolerate the touchpad until I figure out how to configure everything properly with X11. 				


Yeah; I think so because I can't think of anything else to try.


Here's the Ubuntu Vaio Testing team. They might be helpful. Not sure but you might have to write to them.
[https://wiki.ubuntu.com/LaptopTestingTeam#Manufacturer%20Sub%20Pages](https://wiki.ubuntu.com/LaptopTestingTeam#Manufacturer%20Sub%20Pages)

And here's a Vaio Ubuntu blog if you wanna read thru that.

[http://vaioubuntu.wordpress.com/](http://vaioubuntu.wordpress.com/)
[http://myubuntublog.wordpress.com/tag/sony-vaio-vgn-ns11j/](http://myubuntublog.wordpress.com/tag/sony-vaio-vgn-ns11j/)

Not sure if these links will help but I tried-

---

