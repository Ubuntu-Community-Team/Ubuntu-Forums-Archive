---
title: "MSI Z370 gaming plus mobo resolution issue with Ubuntu 16.04.3"
date: 2018-01-29
forum: New to Ubuntu
---

### Post by jans99 on 2018-01-29
Hello,

Good Evening.
I had very recently installed Ubuntu 16.04.3 on a desktop which has MSI Z370 gaming plus mobo with i3-8100. Everything is working fine. 
When i connect my monitor i get a resolution of 1024 x 768 and there is no other option. I don't have an external graphics card.

I wish to attach 4 monitors (off course i will buy card for that), but with current single monitor is there any way in Ubuntu to get a better resolution?

Any pointers would be very helpful.

Thanks and Regards
Anish


[h=2][/h]

---

### Post by onesixtyfourth on 2018-01-29
I have just installed an MSI motherboard (MSI Z270) but also MSI NVIDIA GeForce GT 1030 and had a similar problem. all I had to do was open the software loader (repositories etc listed) and go to the additional software tab. When I cliked search for additional drivers the NVidia driver was found and I installed it. This gave me better resolution for this card and two monitors.

---

### Post by Autodave on 2018-01-29
+1 with onesixtyfourth.  Go to Settings -> Additional Drivers. Let it search and install the recommended one (if it finds any). Report back.

---

### Post by oldfred on 2018-01-29
If no nVidia or AMD video card, your setting should be in System Settings, Displays. Run detect displays.
Or is your monitor not a standard one that it can detect?

---

### Post by jans99 on 2018-01-29
Hello 

Thank you for the inputs.
I tried the suggested options.

Under additional drivers tab - i can see "this device is using an alternative driver" with 2 radio buttons "using processor microcode firmware for Intel CPUs from intel-microcode (open source) and "do not use the device" only.

I had also tried the Display -> Detect Display button, but there is no change over there also.

My monitor is bit old, think around 5/6 - Model is ProLite E2208HDD (IIyama)

Thanks and Regards
Anish

---

### Post by oldfred on 2018-01-29
You may need to install this app.
sudo apt install read-edid
sudo get-edid | parse-edid

If monitor real old, it may not have edid, but my 10 year old monitor does.

---

### Post by jans99 on 2018-01-29
Hello,
Did edit as you had mentioned and below is the output

Section "Monitor"
    Identifier "DP2VGA V226"
    ModelName "DP2VGA V226"
    VendorName "ITE"
    # Monitor Manufactured week 3 of 2015
    # EDID version 1.4
    # Analog Display
    DisplaySize 600 340
    Gamma 2.20
    Option "DPMS" "false"
    #Not giving standard mode: 1280x720, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1600x1200, 60Hz
    #Not giving standard mode: 1920x1080, 60Hz
    #Not giving standard mode: 1680x1050, 60Hz
    #Not giving standard mode: 1400x1050, 60Hz
    #Not giving standard mode: 1440x900, 60Hz
    #Not giving standard mode: 1600x900, 60Hz
    Modeline     "Mode 0" 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync 
    Modeline     "Mode 1" 85.50 1366 1436 1579 1792 768 771 774 798 +hsync +vsync 
    Modeline     "Mode 2" 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync

---

### Post by oldfred on 2018-01-29
Is that just an adapter converting your output to the old VGA standard.
And if monitor really only VGA that may be the issue.

---

### Post by jans99 on 2018-01-30
Few mins back just got a msi GT 710 graphics card, going to setup tonight, as far as I read 16.04 supports that card. Hopefully everything will be OK. :{-)

---

