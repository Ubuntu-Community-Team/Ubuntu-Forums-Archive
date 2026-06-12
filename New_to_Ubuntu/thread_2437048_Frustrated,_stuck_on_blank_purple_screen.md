---
title: "Frustrated, stuck on blank purple screen"
date: 2020-02-17
forum: New to Ubuntu
---

### Post by woomdawg on 2020-02-17
So I was dual booting win10 and ubuntu, I have run both 18.04 and 19.10 and had no troubles other than some sound issues. The sound issues were annoying but always got it fixed. Now I have run into a blank unresponsive purple screen after GRUB no matter what version I install. I reformat the drive with each new install and scrub the mbr in win10. I am running 2 ssd's, win on a 500gb and linux on a 250gb both samsung drives.my system is an I7 920 with an evga x58 classified motherboard, 12 or 16gb ram, evga gtx 780 GPU and a creative recon 3d PCIe sound card. I have tried the work arounds I can find on google but nothing has worked. What I find interesting is I am now running linux mint 19.3 and do not get hung up after GRUB like I do with ubuntu. I really do not want to run mint and would love to go back to ubuntu. I could really use some help.

---

### Post by Bashing-om on 2020-02-17
woomdawg; Hello -

As a test try booting with the nomodeset boot parameter:
 [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If this isolates to a graphic's driver issue - 
well we can try and clean things up, purge the present driver, and install the recommended driver for your card.

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by woomdawg on 2020-02-17
Ok I will do a fresh install  and  give it a try with 19.10.

---

### Post by Bashing-om on 2020-02-17
woomdawg; Hey !
Nomodeset with this install -

we try and get this install functional.
Was my thought.

[INDENT]together we can-
[/INDENT]

---

### Post by woomdawg on 2020-02-17
I had to do a fresh install I was running mint ugh and hated it. Just finishing the flash drive, windows has been cleaned and the linux drive refomated.

---

### Post by woomdawg on 2020-02-17
So I did a fresh install and of course  it booted to a blank purple screen. I went back to GRUB and added nomodeset and hit ctrl x and it showed a black screen then the ubuntu splash for a moment and right back to the blank purple screen.

---

### Post by Bashing-om on 2020-02-17
woomdawg; Hummm ...

does not seem a graphic's driver issue - "nomodeset" should take the driver out of the equation.

The install medium ?
what does booting the installer - check disk for defaults - reveal ? as soon as the bios screen clears hold a key to get the installer menu. -> [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

[INDENT]got to be a reason
[/INDENT]

---

### Post by woomdawg on 2020-02-17
I am using a flash drive. I tried bomodeset and it was the same results.

---

### Post by Bashing-om on 2020-02-18
woomdawg;
> 
I am using a flash drive. I tried bomodeset and it was the same results.

and that tells us it is not a graphic's driver at fault here, looking for info as to where the root of the issue is.

Just because it is a flash drive, the method to "check" the .iso copy to the install medium is still valid.

[INDENT][INDENT]looking
[INDENT][INDENT]for that reason
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wildmanne39 on 2020-02-18
To clarify it's:
```
nomodeset
```
Not:
```
bomodeset
```

---

### Post by woomdawg on 2020-02-18
Yes at the end of the line that starts with linux

---

### Post by alirezas on 2020-02-18
> **woomdawg said:**
> Yes at the end of the line that starts with linux

Ok did you turn off fast boot in bios and also if you using UEFI Boot and have dual boot, are you using both from Other OS instead of Windows OS.

---

### Post by woomdawg on 2020-02-18
I could really use so help here please.

---

### Post by Bashing-om on 2020-02-18
woomdawg; -

Trying to help - I am at the point of verifying what you are working with, i,e, "check disk for defects".
Though a USB devise - the check remains the same process.
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

If you are unable to verify here - we then drop back to verifying the .iso that you downloaded.

[INDENT]got to have a firm foundation to push from
[/INDENT]

---

### Post by woomdawg on 2020-02-18
I can not find anything in my bios for fast boot. This is an older evga x58 motherboard. I am not sure what UEFI Boot is.

---

### Post by woomdawg on 2020-02-18
Sorry I did not see your reply. I can not figure out how to verify a USB drive.

---

### Post by Bashing-om on 2020-02-18
woomdawg; Hey :)

As I have said - just boot the usb drive ( bios - disable secure boot ??), as soon as the bios screen clears hold any key -> boot menu .
Here select 'check disk for defects' and allow the test to complete.

[INDENT]easy when you have done it a time or three
[/INDENT]

---

### Post by woomdawg on 2020-02-18
> **Bashing-om said:**
> woomdawg; Hey :)

As I have said - just boot the usb drive ( bios - disable secure boot ??), as soon as the bios screen clears hold any key -> boot menu .
Here select 'check disk for defects' and allow the test to complete.

[INDENT]easy when you have done it a time or three
[/INDENT]

Ok checked USB drive for error and no errors were found. Not sure what secure boot is. Is it where you set a password in the bios?

---

### Post by Bashing-om on 2020-02-18
woomdawg; Well -

That is good news,

As to "secure boot" that only apples to UEFI systems.

We now know that the install medium is sound; so next is how far do you get in the boot process ?

When you boot the install, hold a shift key - do you get grub's boot menu ?

from grub we can make up some options to boot.

[INDENT][INDENT]there is a procedure for this
[/INDENT][/INDENT]

---

### Post by woomdawg on 2020-02-18
> **Bashing-om said:**
> woomdawg; Well -

That is good news,

As to "secure boot" that only apples to UEFI systems.

We now know that the install medium is sound; so next is how far do you get in the boot process ?

When you boot the install, hold a shift key - do you get grub's boot menu ?

from grub we can make up some options to boot.

[INDENT][INDENT]there is a procedure for this
[/INDENT][/INDENT]

GRUB loads up no problem. Once I choose Ubuntu I  get a black screen briefly  and then a blank purple screen.

---

### Post by Bashing-om on 2020-02-18
woomdawg; Good

OK, next to isolate to a GUI issue:
Let's boot to console rather than a GUI.

In grub add the boot parameter systemd.unit=multi-user.target - like you did with the nomodeset boot parameter.
Here I expect that you boot to a terminal, can you log into the system here ( username and password - no response when the password is entered)
Any errors reported here ?

restart from terminal:
systemctl reboot

shutdown:
systemctl poweroff

[INDENT]gots to be a reason
[/INDENT]

---

### Post by woomdawg on 2020-02-18
> **Bashing-om said:**
> woomdawg; Good

OK, next to isolate to a GUI issue:
Let's boot to console rather than a GUI.

In grub add the boot parameter systemd.unit=multi-user.target - like you did with the nomodeset boot parameter.
Here I expect that you boot to a terminal, can you log into the system here ( username and password - no response when the password is entered)
Any errors reported here ?

restart from terminal:
systemctl reboot

shutdown:
systemctl poweroff

[INDENT]gots to be a reason
[/INDENT]

At the end of the line that starts with linux correct?

---

### Post by woomdawg on 2020-02-18
Same result blank purple screen.

---

### Post by Bashing-om on 2020-02-18
woomdawg; Ouch !

Then we have a kernel issue -
Way above my skill level at this point. Others here will have to advise further.

[INDENT]A know-it-all I am not
[/INDENT]

---

### Post by woomdawg on 2020-02-18
I was able to get to the terminal and login using Ctrl+Alt+F1

---

### Post by woomdawg on 2020-02-18
Thank you for your help

---

### Post by Bashing-om on 2020-02-18
woomdawg; Well !

> 
I was able to get to the terminal and login using Ctrl+Alt+F1


Then we are back to a GUI issue :)

In this Ctrl+Alt+F1 terminal, what shows:
```

sudo lshw -C display

```

Maybe best to relay that to a pastebin site:
```

sudo lshw -C display | nc termbin.com 9999

```

[INDENT]let there be light
[/INDENT]

---

### Post by woomdawg on 2020-02-18
I have screenshots but I can not attach them

---

### Post by woomdawg on 2020-02-18
[https://drive.google.com/folderview?id=1DI6elYLbWmxKbSy7Vt4UGZGKfJVRwInu](https://drive.google.com/folderview?id=1DI6elYLbWmxKbSy7Vt4UGZGKfJVRwInu)

---

### Post by Bashing-om on 2020-02-19
woomdawg; Ouch !

ATA14: Hardware issue indicated here ? - nvidia driver is loaded - I pass this to those here with the greater experience.

But:
what results:
```

sudo apt update
sudo apt upgrade

```
as a test of the file system

[INDENT]sometimes I do wonder
[/INDENT]

---

### Post by woomdawg on 2020-02-21
I ended up sadly re-installing Mint.

---

### Post by Bashing-om on 2020-02-21
woomdawg; :(

Regrets that this one is above my skills set.

carry on, smartly

---

### Post by woomdawg on 2020-02-29
Bump

---

### Post by CelticWarrior on 2020-02-29
> **woomdawg said:**
> Yes at the end of the line that starts with linux

Not sure you did it right... End of the line is not always the best way. But this likely needs some boring explanation:

This is about the [KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") link you were given in a previous post.
In one of the screenshots please notice that the line "linux" actually ends with "$vt_handoff_" (initializes the desktop). Unfortunately the guide has a couple of problems and the first is not making it clear enough, IMO, that the added parameters are to written after "quiet splash" (or before or instead of) with a space, and not after "$vt_handoff_". Pleased note they do mention it like this:
> 
[LIST]
[*]Use the down arrow key to move the cursor to the line beginning with the word "linux", then press the **END** key to move the cursor to the end of that line.  Normally this will be just after the words "quiet splash". 


[*]Press **SPACE** to add a blank space (after "splash")  then carefully type in the kernel boot parameter that you need to add.   (If you need to add multiple parameters separate them with **SPACE** but do not add spaces before or after any = signs or punctuation in the parameters themselves). 

[/LIST]


So, if your edit didn't look like "quiet splash nomodeset" (actually a better idea is just "nomodeset" instead of "quiet splash" so you can see the boot messages, but I digress...) that explains why it didn't work as it should assuming we're back to very likely a graphics driver problem, the first hypotheses mentioned in this thread. A different kind of issues is also possible, of course, but I decided to post this to **confirm or not if you're sure you used "nomodeset" exactly as mentioned above**.

My hypotheses: 
[LIST=1]
[*]Knowing that 18.04 was fine either with the default open-source *nouveau* or a proper Nvidia driver that you installed (you tell us, please) and
[*]19.10 runs fine in a live session and installs successfully
[/LIST]

I think 19.10 could have somehow installed a wrong driver.

You may try reinstalling but this time do not select installation of third-party goodies to force it it to use the same driver as in the live session instead of the Nvidia one. Maybe that just works, If it does then we (optionally) troubleshoot the Nvidia driver. If nouveau fits your needs there's no reason not to keep it that way.

---

### Post by woomdawg on 2020-02-29
> **CelticWarrior said:**
> Not sure you did it right... End of the line is not always the best way. But this likely needs some boring explanation:

This is about the [KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") link you were given in a previous post.
In one of the screenshots please notice that the line "linux" actually ends with "$vt_handoff_" (initializes the desktop). Unfortunately the guide has a couple of problems and the first is not making it clear enough, IMO, that the added parameters are to written after "quiet splash" (or before or instead of) with a space, and not after "$vt_handoff_". Pleased note they do mention it like this:


So, if your edit didn't look like "quiet splash nomodeset" (actually a better idea is just "nomodeset" instead of "quiet splash" so you can see the boot messages, but I digress...) that explains why it didn't work as it should assuming we're back to very likely a graphics driver problem, the first hypotheses mentioned in this thread. A different kind of issues is also possible, of course, but I decided to post this to **confirm or not if you're sure you used "nomodeset" exactly as mentioned above**.

My hypotheses: 
[LIST=1]
[*]Knowing that 18.04 was fine either with the default open-source *nouveau* or a proper Nvidia driver that you installed (you tell us, please) and
[*]19.10 runs fine in a live session and installs successfully
[/LIST]

I think 19.10 could have somehow installed a wrong driver.

You may try reinstalling but this time do not select installation of third-party goodies to force it it to use the same driver as in the live session instead of the Nvidia one. Maybe that just works, If it does then we (optionally) troubleshoot the Nvidia driver. If nouveau fits your needs there's no reason not to keep it that way.

Yes you are correct I did enter nomodeset in the wrong place at the end of the linux line. I have both 18.04 and 19.10 working with the nvidia driver. I will reinstall with no goodies. One thing I thought of and  probably not the cause but this all started about the time I plugged my TV into my GPU with an HDMI cable as a second monitor, I will unplug that as well. Thanks

---

### Post by woomdawg on 2020-02-29
Installed and working and I did not have to use nomodeset. Oddly enough I think my TV plugged into the HDMI port on my GPU caused the issue. We will see as I update and install drivers.

---

