---
title: "Is There a BIOS Utility?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by wagb278 on 2008-05-11
1.  Is there a Ubuntu command or utility that allows saving current BIOS settings? 

I would like to record BIOS settings using something like:
 ```
dumpbios > ./bios.txt
```

I just want a record in case I need it later.  I could spend a few hours going thru the BIOS pages and manually recording the settings, which I will do if necessary.



2.  Is there a tool within Ubuntu that allows monitoring the Temperatures that are available in BIOS?


All I know of is to enter BIOS to view current temperatures, but that is not stressing the system.

---

### Post by Steveway on 2008-05-11
If you want to view the temperatures then you can ask acpi.
Just type acpi -t in a terminal and it will tell you the temperatures it knows of.
Since Linux doesn't really interact or uses the BIOS I doubt that you can reach it somehow.

---

### Post by y-lee on 2008-05-11
Something like the below might do

```
sudo dmidecode > ./bios.txt
```


See [Reading BIOS Information]("http://wiki.xdroop.com/space/Linux/Reading+BIOS+Information"). :)

---

### Post by kansasnoob on 2008-05-11
I don't know about saving BIOS settings, but I always add computertemp from synaptic. Then I right click on any open area of either panel and select "add to panel". The computertemp applet will now be in the list and you can drag-n-drop it into either panel. By right clicking the applet you can change settings.

---

### Post by wagb278 on 2008-05-11
Thanks for the reply - 

acpi -t returns "No support for device: Thermal"

I looked at acpi --help too.  I guess the information I want is not passed by my motherboard; which is an Intel DP35DP.  I am running HH 8.04 64-bit.

---

### Post by wagb278 on 2008-05-11
Thanks kansasnoob

I installed that but it acts like the "acpi -t" giving a tool-tip saying "No Thermal support".

So, I am thinking my Intel DP35DP motherboard does not make this info available outside the BIOS.

Y-lee:  Thanks for the "dmidecode" clue.

---

