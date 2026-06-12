---
title: "[SOLVED] Mother Board Model Number"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by s.fox on 2008-07-24
Hi,

Is their a way in ubuntu to find out what my mother board model number is?

Thanks for any help

---

### Post by Vivaldi Gloria on 2008-07-24
Try

```
sudo lshw -C system
```

---

### Post by ibuclaw on 2008-07-24
```
sudo lshw -html > ~/Desktop/hardwareinfo.html
```

It'll be at the top of the form under "**id: core**" :)

Regards
Iain

---

### Post by s.fox on 2008-07-24
Thanks for the quick replies.  I got the following output:

```
ashley@ashley-desktop:~$ 
ashley@ashley-desktop:~$ sudo lshw -C system
ashley-desktop            
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=80776E6E-781E-D911-9F04-00112FAEF9E8
ashley@ashley-desktop:~$ sudo lshw -html > ~/Desktop/hardwareinfo.html
ashley@ashley-desktop:~$ sudo lshw -html > ~/Desktop/hardwareinfo.html
PCI (sysfs)
```


Um.  Am i doing something wrong?
Thanks for the help :)

---

### Post by Vivaldi Gloria on 2008-07-24
Try

```
sudo dmidecode -t system -t baseboard
```

---

### Post by halitech on 2008-07-24
> **Ash R said:**
> Thanks for the quick replies.  I got the following output:

```
ashley@ashley-desktop:~$ 

ashley@ashley-desktop:~$ sudo lshw -html > ~/Desktop/hardwareinfo.html
ashley@ashley-desktop:~$ sudo lshw -html > ~/Desktop/hardwareinfo.html
PCI (sysfs)
```


Um.  Am i doing something wrong?
Thanks for the help :)

You should now have a file on your desktop called hardwareinfo.html, just open that with firefox and you will see the info

---

### Post by Elfy on 2008-07-24
> Am i doing something wrong?have you opened the file that's on your desktop? It works for me, as does Vivaldi's.

One new thing learnt :)

---

### Post by ARhere on 2008-07-24
Maybe a dumb comment, but have you looked on the motherboard?  You can also look in your BIOS when the PC boots up.

I have a sneaking suspicion that your PC is not built by you, but a generic PC like E-Machine or something similar.  In that case, those PC's motherboards are not 3rd party but build for that particular model of computer, like a lot of other PC makers.  So finding a motherboard model number will be pointless in that case.

Tell us what you are trying to do with this information, maybe we can help.

-AR

---

### Post by ibuclaw on 2008-07-24
> **Ash R said:**
> Thanks for the quick replies.  I got the following output:

```

ashley@ashley-desktop:~$ sudo lshw -html > ~/Desktop/hardwareinfo.html
ashley@ashley-desktop:~$ sudo lshw -html > ~/Desktop/hardwareinfo.html
PCI (sysfs)
```


Um.  Am i doing something wrong?
Thanks for the help :)

Check your desktop.
My command creates a html file readable by firefox

It's good for easy reading too :)

Regards
Iain

---

### Post by s.fox on 2008-07-24
Nice it worked.  i didn't realize it created a file on my dektop :lolflag:

i have got a friend in Texas that is helping me upgrade this current rig and will ship the cheep parts to Europe for me.  Graphics card was released in 2002!  lmao.  definitely time for an upgrade :)

thanks everybody :)

---

### Post by halitech on 2008-07-24
don't feel bad, my newest part is my dvd burner from 2006, everything else is pre 2002 ~L~

---

### Post by ARhere on 2008-07-25
> **Ash R said:**
> ...thanks everybody :)

Glad you where helped, please post as [SOLVED]

I have a zillion (*ok, maybe 12..sheesh!*) threads now that I check now and again because there are not marked and I don't want to leave anyone hanging.

-AR

---

