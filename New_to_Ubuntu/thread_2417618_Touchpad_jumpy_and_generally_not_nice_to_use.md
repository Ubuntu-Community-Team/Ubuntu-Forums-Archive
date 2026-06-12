---
title: "Touchpad jumpy and generally not nice to use"
date: 2019-04-25
forum: New to Ubuntu
---

### Post by bobbaker1970 on 2019-04-25
Hello, and forgive me if I ask stupid questions, I am a linux newbie.

I have:
Dell E7250
Lubuntu 18.04 (previously tried Ubuntu 18.04 and had exactly the same problems)
the touchpad is an Alps

Basically, the touchpad is over sensitive. Also it doesn't have palm rejection so the cursor keeps jumping back to previous words when I am typing (happened 3 times in writing this sentence).
FYI it works perfectly in Windows 10.

Some info:
xinput --list-props <id> > ~/xinput
 

 

 I: Bus=0011 Vendor=0002 Product=0008 Version=0310
 N: Name="AlpsPS/2 ALPS GlidePoint"
 P: Phys=isa0060/serio1/input0
 S: Sysfs=/devices/platform/i8042/serio1/input/input6
 U: Uniq=
 H: Handlers=mouse0 event6 
 B: PROP=9
 B: EV=b
 B: KEY=e420 70000 0 0 0 0
 B: ABS=260800001000003
 

 

 a@a-pc:~$ xinput --list-props <id> > ~/xinput
 bash: syntax error near unexpected token `>'
 a@a-pc:~$ xinput --list
 &#9121; Virtual core pointer                          id=2    [master pointer  (3)]
 &#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
 &#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                  id=13   [slave  pointer  (2)]
 &#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
     &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
     &#8627; Power Button                              id=6    [slave  keyboard (3)]
     &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
     &#8627; Power Button                              id=8    [slave  keyboard (3)]
     &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
     &#8627; Laptop_Integrated_Webcam_HD: In           id=10   [slave  keyboard (3)]
     &#8627; Dell WMI hotkeys                          id=11   [slave  keyboard (3)]
     &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
 a@a-pc:~$ 

Thanks for any help resolving this. Currently the touchpad is almost unusable.

---

### Post by cruzer001 on 2019-04-25
I had a Dell (m6600} with the Alps touchpad and it was painful getting it set up.

The Dell site has a Alps/Linux fix that helped, but still needed to be tweaked.

I also switched from libinput to the synaptics touchpad driver which had just as many problems.

Ubuntu Mate had the best out-of-the-box touchpad results and was usable, but still needed some tweaking.

In the end (gnome desktop) I used the libinput driver.  Touchpad sensitivity/pressure and gesture settings made a big improvement and I don't remember what else.  Sorry

---

### Post by Rex Bouwense on 2019-04-25
Check the answer given here.  [https://askubuntu.com/questions/886092/how-do-i-disable-the-touchpad-while-typing#886098](https://askubuntu.com/questions/886092/how-do-i-disable-the-touchpad-while-typing#886098)

---

### Post by Holger_Gehrke on 2019-04-25
A small detail which might be helpful; the placeholder '<id> in 'xinput -list-props <id>' needs to be replaced with an actual id or name for the device, so to see the properties for your touchpad you'd need to enter
```

xinput -list-props "AlpsPS/2 ALPS GlidePoint"

```
(using the name is usually better since the numerical id is subject to change without notice from one session to the next ...)

Holger

---

