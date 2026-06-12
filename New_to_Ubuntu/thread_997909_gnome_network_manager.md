---
title: "gnome network manager"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by simsek49 on 2008-11-30
Looks like this

[IMG]http://tips.webdesign10.com/files/connection-properties.png[/IMG]

As im sure you all know but i dont have gnome network manager i dont know what i have. I am currently connected with a ethernet cable but i cant get it to connect wirelessly, if i had gnome network manager im sure i could do this easly so im wondering how do i get it?

---

### Post by quazi on 2008-11-30
Try running the command
```

sudo apt-get install network-manager-gnome
```

---

### Post by simsek49 on 2008-11-30
> **quazi said:**
> Try running the command
```

sudo apt-get install network-manager-gnome
```

Done says i already have latest installed, it says wireless disabled. After doing a bit of research maybe my wireless card needs the drivers downloading?

Anyone know how i can find out what my wireless card is called?

---

### Post by simsek49 on 2008-11-30
eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Do i need drivers?

---

### Post by FreewheelinFrank on 2008-11-30
The screenshot is gnome-network-monitor.

Do you dual boot? If you have Windows, boot into Windows, enable wireless and boot back into Ubuntu. (Wireless was greyed out on my laptop till I did this.)

---

