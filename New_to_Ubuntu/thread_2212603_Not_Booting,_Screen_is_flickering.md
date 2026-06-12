---
title: "Not Booting, Screen is flickering"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by Akhil_K_A on 2014-03-22
kubuntu 12.04 works fine in live mode (via usb), but after installing as dual boot with Windows 7, it doesn't boot.

When I select kubuntu from the boot menu, the screen keeps on flashing.  I waited for 5 minutes and same screen is flickering! All I can do is manually, switch-off the laptop. I have tried several time, but no use.

Then I tried to get into the recovery mode. From the recovery mode options, I'm able to get into the Kubuntu OS :confused:

What to do? Is this is a common issue of version 12.04? Using 13.10 will resolve this issue? Please help me.

Thanks.

Akhil

---

### Post by Bashing-om on 2014-03-22
Akhil_K_A; Hi !

Let's "surmise" from the indications that there is a graphics driver issue.
To test:
Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->ubuntu Software Center ->Additional Drivers [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

And maybe resolve the situation.

advise on results.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by Akhil_K_A on 2014-03-23
Hi Bashing-om.

Thank you for your reply. I'm an absolute beginner in ubuntu. Can you please elaborate your solution? I'm unable to understand your solution :( I have reported this thread to the moderators to move this thread to absolute beginners section.

Thanks.

---

### Post by deadflowr on 2014-03-23
Bashing-Om's first part is sensible.

When you first start the machine, do you get a screen with options to choose either Kubuntu or Windows7?

If so, this is what's known as the grub menu. It's Ubuntu's boot program.
As the advice said, when this screen appears, press the e key (E, the letter E)
This will allow you to edit the options.
It's useful because it allows you to change a setting quickly, such as the method described in the earlier post.

As stated, try adding nomodeset into the first Kubuntu(Ubuntu?) entry.
As stated put it after quiet splash.
The save and exit as stated.

Then choose the entry you added the nomodeset to.


As for the rest of the post, that seems to be geared toward unity, and not Kubuntu.

For Kubuntu try opening the menu in the bottom left side panel.
(I think it should be a kde icon)
Kubuntu has a quick search function so use it to find Additional Drivers.
(There should be a search bar in the top of the menu box(?) [I don't know what to call the menu, lol]
The additional drivers will list drivers for the graphics card that may or may not be better than the ones used by default.
(It might also not list any...)
I hope something here helps, somehow...

---

### Post by coffeecat on 2014-03-23
*Thread moved to **Absolute Beginners Section** at request of OP.*

---

### Post by Akhil_K_A on 2014-03-23
> **deadflowr said:**
> Bashing-Om's first part is sensible.

When you first start the machine, do you get a screen with options to choose either Kubuntu or Windows7?

If so, this is what's known as the grub menu. It's Ubuntu's boot program.
As the advice said, when this screen appears, press the e key (E, the letter E)
This will allow you to edit the options.
It's useful because it allows you to change a setting quickly, such as the method described in the earlier post.

As stated, try adding nomodeset into the first Kubuntu(Ubuntu?) entry.
As stated put it after quiet splash.
The save and exit as stated.

Then choose the entry you added the nomodeset to.


As for the rest of the post, that seems to be geared toward unity, and not Kubuntu.

For Kubuntu try opening the menu in the bottom left side panel.
(I think it should be a kde icon)
Kubuntu has a quick search function so use it to find Additional Drivers.
(There should be a search bar in the top of the menu box(?) [I don't know what to call the menu, lol]
The additional drivers will list drivers for the graphics card that may or may not be better than the ones used by default.
(It might also not list any...)
I hope something here helps, somehow...

Thank you sir. Let me try this. After that, I will update this thread.:KS

---

### Post by Akhil_K_A on 2014-03-23
> **coffeecat said:**
> *Thread moved to **Absolute Beginners Section** at request of OP.*

Thank you so much for considering my request.

---

### Post by Akhil_K_A on 2014-03-23
I'm able to boot into the os by using "nomodeset" in grub menu. To update the driver, Internet connection is needed. I'm only having "Reliance Net connect+" usb data modem. Unfortunately it is not detecting in Kubuntu.
So, i searched in google and found a solution. To detect the modem i need to install "wvdial". Then I downloaded the wvdial and installed it on kubuntu. Then I configured it by editing "usb_modeswitch.conf " and "wvdial.conf". Then I reeboted the system and connected the device and did these steps:

1. Opened terminal and typed "kdesudo wvdial netconnect"

but, I'm getting this error: "wvdial: error while loading shared libraries: libwvstreams.so.4.6: cannot open shared object file: no such file or directory"

2. Downloaded a package named "wvstreams-4.6.1-7-x86_64.pkg.tar", but, I don't know how to install this file.

Please help me to complete this step!

Thanks.

---

### Post by Rob Sayer on 2014-03-23
I just looked up wvdial in ...

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

... and I don't believe this is the correct way to go about this.  If the underlying system can't detect your network device it's not likely to work.

Post the output (use code tags) of:

```
sudo lshw -C network
```

Be careful what you search.  There's a lot of good info out there.  There's also a lot of bad info, and things that novices don't understand.

---

### Post by Akhil_K_A on 2014-03-23
Thanks Rob Sayer.

I have lost my 48hrs for installing and configuring kubuntu :( Now, I'm going to replace kubuntu with ubuntu. I will update this thread once I have complete the installation process.

Thanks

---

