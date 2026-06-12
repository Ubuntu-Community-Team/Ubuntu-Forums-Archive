---
title: "how to install logisim"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by david107 on 2013-09-28
Hi,
I can't install logisim 2.7.1, which I need to use for a computer architecture class I am taking. I looked in the software center and tried the apt-get thing but might not have used it correctly. I am new to ubuntu but I did install updates and a c++ compiler through apt-get. I am using Ubuntu 12.04 LTS on a laptop that was installed using a windows installer. Can someone tell me step by step how to install this program called Logisim?

Thanks
David

---

### Post by kostkon on 2013-09-28
In 12.04 logisim is in the backports and not in the main repositories. What you need to do is open the Software Centre, select Edit -> Software Sources from the menu and then when the window opens, click on the Updates tab and enable the Unsupported Updates (precise-backports) option; press Close and then search for it and install it.

---

### Post by sandyd on 2013-09-28
> **david107 said:**
> Hi,
I can't install logisim 2.7.1, which I need to use for a computer architecture class I am taking. I looked in the software center and tried the apt-get thing but might not have used it correctly. I am new to ubuntu but I did install updates and a c++ compiler through apt-get. I am using Ubuntu 12.04 LTS on a laptop that was installed using a windows installer. Can someone tell me step by step how to install this program called Logisim?

Thanks
David

Logisim can be installed through software center/apt-get if you have backports enabled - Can you see it in the menu right now?

Does it show up if you run
```

/usr/bin/logisim
```
in the terminal?

Thanks.

---

### Post by david107 on 2013-09-28
I have enabled the backports, but I still can't find it.

---

### Post by david107 on 2013-09-28
Ok I finally got it. I did [FONT=lucida console]sudo apt-get upgrade [/FONT] and then opened the software center again and found logisim. It installed and works. Thank you both for helping.

---

### Post by poppys-boat on 2013-09-28
how do i open edit? i cannot see it in the ubuntu software centre?

found it, i expected it to be in the same window not in the top bar.

---

