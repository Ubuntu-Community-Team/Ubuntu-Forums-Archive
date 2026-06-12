---
title: "USB instalation problem"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-10-03
All I get is a beep when pushing install ubuntu on a hard disk... any suggestions?

---

### Post by glyphted on 2011-10-03
I had a similar problem. In your BIOS/boot settings, there should be a "save and exit" tab... at the bottom there is a Boot Override option, select the USB and the menu will reappear, Install / Try / Check Disk. Select Install, and it should work. 

Also, is your system ready for it? Such as space/ physical capacity? Hope this works!

---

### Post by ajsoulmate on 2011-10-04
> **jiggajoe506 said:**
> All I get is a beep when pushing install ubuntu on a hard disk... any suggestions?

Yes. Even thought you didn't provide more info.

1- Use UNetbootin to create a Live USB.
2- Insert your USB, turn your Computer ON and enter BIOS.
3- Make sure you change your settings - you need to set BIOS to boot first from USB.
4- Done.

---

### Post by seawolf167 on 2011-10-04
Follow ajsoulmate's post - but on #3, as long as you have booting from USB *enabled *in BIOS, you can simply enter your boot menu during POST by hitting your BIOS specific function key (usually something like [F12]), then select which media to boot from.

---

