---
title: "Touchpad not detected in Asus K55N"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by Eeba on 2013-10-20
I had really bad experience upgrading to Ubuntu 13.10 from Ubuntu 13.04. I was very satisfied with Ubuntu 13.04. After upgrading, I found that the internet connection was too slow and the system did not detect touchpad at all.

Then I downloaded the 64 bit iso file on yesterday Oct. 19 2013. and installed Ubuntu 13.04 from a bootable disk. Everything was working fine including the touchpad. The system automatically updated different softwares. Then after I restarted the computer, I had the strange problem with my touchpad. Ubuntu did not detect my touchpad at all.  Even in the mouse and touchpad system setting, it doesn't have any touchpad tab. 

Here's my xinput list:
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                          id=11    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard   

Any help or suggestion is greatly appreciated.

---

### Post by varunendra on 2013-10-23
Please also post the output of -
```
lsmod
```

And try these -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```
It will remove-reload the psmouse driver which controls the touchpad in asus laptops.

If that does not help, try -
```
echo "blacklist asus_nb_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and see if it helps.

The "asus_nb_wmi" driver mainly controls the wifi and bluetooth switch, but in combination of some other drivers, it also controls some other Fn+ hotkeys, including enable/disable touchpad.

Disabling it will also disable some Fn+ key combinations, so this is just for a test. To remove it from blacklist to make it work again -
```
sudo sed -i "/asus_nb_wmi/ d" /etc/modprobe.d/blacklist.conf
```

Although since your touchpad is entirely disappeared, I doubt if any of these trivial workarounds are going to fix it, but testing won't hurt. Maybe another update would fix it automatically. Else of course it is a good idea to just stick with 13.04 for now, and give 13.10 some more time until these bugs are fixed.

---

