---
title: "Belkin 300 wireless router"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by johnmoran on 2014-08-30
Hi 
I am new to ubuntu and having problems setting up my wireless router.
it has identified my router, but it will not connect. It seems to be connected for about 20secs then asks for the pass word again. The router is a Belkin 300 which works fine with windows but not ubuntu. 
I have set it up inside windows via wubi. Everything works fine except the wireless connection.
I forgot to mention my machine is a Lenovo  T60

John

---

### Post by 3rdalbum on 2014-08-30
The router doesn't matter - it's most likely your wireless card in your computer that is causing the problem.

Can you please run this command in the terminal and give us the details?

```
lshw -C network
```

Also, what version of Ubuntu are you using? If you are new, you should be using 14.04 as it's both the latest version, and the latest long-term support version.

---

### Post by johnmoran on 2014-08-30
Thank you for your quick reply, I am using ubuntu 12.04 lts fully updated. I have tried to follow your instructions.
I am using a ralink pci wireless as my internal unit cracked up, it works fine with windows and can't understand what the problem is with ubuntu. I have followed your instructions as best as I can and I am attaching the read out that it produced.
I am most gratefull for any assistance you can give me.

John

```
State:             disconnected
  Default:           no
  HW Address:        7C:DD:90:15:14:7F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    belkin.864:      Infra, B4:75:0E:6B:28:64, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:16:41:E6:B2:41

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off
```

---

### Post by wildmanne39 on 2014-08-31
When you have output from the terminal and post the output here please do so by clicking on new reply and click # then paste the information between the brackets.
Thanks

---

### Post by johnmoran on 2014-08-31
Hi Wildman
I don't quiet understand what you need. I thought everyone could read my reply to 3rdalbum, if this is not the caseI attaching report again.

John

#
Code:

State:             disconnected
  Default:           no
  HW Address:        7C:DD:90:15:14:7F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    belkin.864:      Infra, B4:75:0E:6B:28:64, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:16:41:E6:B2:41

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

---

### Post by wildmanne39 on 2014-08-31
The output from the terminal goes between the code tags ```
Here
```you can add them by clickng on the # at the top of the reply window or manually add them useing your keyboard.
Thanks

---

