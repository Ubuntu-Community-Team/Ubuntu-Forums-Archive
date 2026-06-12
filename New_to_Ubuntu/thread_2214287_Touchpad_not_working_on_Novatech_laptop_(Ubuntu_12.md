---
title: "Touchpad not working on Novatech laptop (Ubuntu 12.04 LTS)"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by AnomalyXB on 2014-03-31
I recently got a Novatech nSpire N1581 ([http://www.novatech.co.uk/laptop/range/novatechnspiren1581.html](http://www.novatech.co.uk/laptop/range/novatechnspiren1581.html)) with no OS installed.  I decided I wanted to try Ubuntu for the first time.  I noticed when I was doing the pre-installation setup that I couldn't move the pointer with the touchpad.  I could use the keyboard and used a wireless mouse to navigate through the process.  I thought that once the OS was installed that the touchpad would start working.  However, this didn't happen.

I've been doing some searching about it and I know there have been issues with the touchpad and Ubuntu, but as a complete newbie, I'm wary of trying any suggested solutions without a proper understanding of the problem, specifically to the make of my laptop.

I opened the terminal and inputted xinput list. These are the results:

```
emma@rootNSPIRE:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=13    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v8.0    id=12    [slave  keyboard (3)]
```

The Microsoft transciever must be the wireless mouse I am currently using.  Is the touchpad the "Virtual core XTEST pointer"? 

I would really appreciate any help to solve this.

---

### Post by pawel6 on 2014-04-01
I'm also struggling to get my pointer working on Mint. Logging the issue now.

---

### Post by BennyHill on 2014-04-25
If your still having problems.

Open up the terminal and insert:-

sudo gedit /etc/default/grub

and on the line GRUB_CMDLINE_LINUX="" 

change it to:-

GRUB_CMDLINE_LINUX="i8042.noloop" 

close and save and run in the terminal:-

sudo update-grub reboot

reboot and you should fingers crossed be good, I would be keen to hear how you get on.

---

### Post by Y^2om&amp;#7sgP on 2014-05-10
Hi BennyHill
I have the same issue on my Novatech N1577, tried their 'support' line and got the answer which boils down to "tough luck"
I found this thread and tried the suggestion you made, but it resulted in an un-bootable system....completely.
Ubuntu gave a kernel panic, windows refused to boot and only gave a corrupt screen :(
currently re-building the laptop from scratch ](*,)
Thanks for trying anyway

---

### Post by benf96 on 2014-05-22
hi, having the same issue on a n1581. i tried changing the /etc/default/grub file and it does still boot, but still no joy regarding the trackpad. hattpa- possibly it was your dual boot setup? i'm currently running standalone fedora. i called tech support and couldnt get any info on the part number or anything of the trackpad, does anyone have access to this information?

---

### Post by benf96 on 2014-05-22
sorry fro the double post, using my keyboard to navigate and is a bit tiresome, but another thing i would like to add is that mousekeys also appears not to work, this could be fedora specific and i am sorry im posting in the ubuntu forum, but i think this is a linux problem, not an ubuntu one. Try mousekeys in ubuntu and get back to me, if it works i will probably dual boot gnome ubuntu.

---

### Post by Y^2om&amp;#7sgP on 2014-05-22
I suspect that the version of the Synaptic touchpad may just be too new for Linux.  I've tried a few distros, including upgrading the kernel to the latest version, all to no avail.
Looks like I'm stuck with a laptop which will only run Windows.....for now :(

---

### Post by benf96 on 2014-05-22
hopefully they will update the synaptics driver soon enough, if you get any furthur with it, don't hesitate to email me on <snip>

---

### Post by TWhyman on 2014-07-16
Just for the record, the problem with the touchpad is still there with Linux Mint 17/Ubuntu 14.4. However, this fix seems to work fine and once added the laptop works with all hardware functioning including wifi and webcam. Looks like an upstream driver fix is needed.

> **BennyHill said:**
> If your still having problems.

Open up the terminal and insert:-

sudo gedit /etc/default/grub

and on the line GRUB_CMDLINE_LINUX="" 

change it to:-

GRUB_CMDLINE_LINUX="i8042.noloop" 

close and save and run in the terminal:-

sudo update-grub reboot

reboot and you should fingers crossed be good, I would be keen to hear how you get on.

---

### Post by benf96 on 2014-08-05
> **TWhyman said:**
> Just for the record, the problem with the touchpad is still there with Linux Mint 17/Ubuntu 14.4. However, this fix seems to work fine and once added the laptop works with all hardware functioning including wifi and webcam. Looks like an upstream driver fix is needed.

+1, fixed the problem.

---

### Post by Y^2om&amp;#7sgP on 2014-08-05
@benf96  was this on 14.04?

---

### Post by Y^2om&amp;#7sgP on 2014-08-06
Well.  I've just installed Xubuntu 14.04 (using a USB mouse)

added the line into grub, rebooted and........

IT WORKS :D

Thanks for the suggestion, you're a total star.  No more Windows on the laptop

Very happy about that :D

---

### Post by potatochip on 2014-08-14
> **BennyHill said:**
> If your still having problems.

Open up the terminal and insert:-

sudo gedit /etc/default/grub

and on the line GRUB_CMDLINE_LINUX="" 

change it to:-

GRUB_CMDLINE_LINUX="i8042.noloop" 

close and save and run in the terminal:-

sudo update-grub reboot

reboot and you should fingers crossed be good, I would be keen to hear how you get on.

Worked perfectly on my brand new nspire. Cheers!

---

### Post by Y^2om&amp;#7sgP on 2014-08-18
OK next daft question.....touchpad now works, but I can't get any audio output when connected to HDMI, even if I then connect headphones/speakers etc to the audio jack, sound just comes through the internal speakers.  I have checked that the ausio selection is for HSMI...

Help?

Thanks all

---

