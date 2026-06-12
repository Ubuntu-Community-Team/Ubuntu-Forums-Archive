---
title: "Laptop automatically reboots after shutdown"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by petefic on 2014-01-19
I recently bought a Thinkpad S431and installed 13.10 onto it dual booting with Windows 7. When I'm in Ubuntu I cannot shut down the laptop. When I shutdown the computer stays off for about 2 seconds before automatically booting itself up again. It does not do this if I shutdown in windows.  
I made sure I have all the latest updates from the software updater. I tried shutting down by using the commands sudo halt and sudo shutdown -h but there was no difference. I also tried disabling wake from lan in my bios as per recommendation of a forum post I found on google with a similar problem, but that did not work either. It is a pain to have to reboot into windows in order to shutdown the laptop.

Here are the specs of the laptop if that matters

CPU: Intel Core i5 3427U @1.80GHz Ivy Bridge 22nm
RAM: 4.00GB Single-Channel DDR3 @ 798MHz
Motherboard: LENOVO 20AXCTO1WW (CPU Socket - U3E1)
Graphics: Intel HD Graphics 4000
Storage: 119GB SAMSUNG MZ7TD128HAFV-000 (SSD)
Audio: Realtek High Definition Audio

---

### Post by egeezer on 2014-01-19
You might try
```
sudo shutdown -h -P
```

That adds the power off (-P) to it.

---

### Post by petefic on 2014-01-19
Tried that, same effect.

---

### Post by petefic on 2014-01-19
I seemed to have fixed it. Using the steps on this page. [http://linuxg.net/computer-reboots-instead-of-shutdown-on-ubuntu-12-04/](http://linuxg.net/computer-reboots-instead-of-shutdown-on-ubuntu-12-04/)

It appears to be working after using the command
[COLOR=#555555][FONT=consolas]$ sudo apt-get install laptop-mode-tools.[/FONT][/COLOR]

---

