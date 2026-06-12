---
title: "Linux Shell Script to authenticate usb drive deny others"
date: 2013-03-23
forum: Programming Talk
---

### Post by Cyrebo on 2013-03-23
Hi, I am currently hardening my Kubuntu 12.10 OS and I want to run a shell script that automatically runs when my usb is plugged in. It should ask for authentication/authorization for my usb when its plugged in and deny ANY other device. So basically what I want is a lockdown of all external media except those which I have specified to be authenticated when they're plugged in. I've seen an example of running a script when a usb device is plugged in but I'm not sure how to incorporate a messagebox style prompt asking the user for a password and lockdown other devices. To me this is very challenging as I'm still relatively new to Linux and I probably wouldn't know how to do it on an OS I am familiar with.

Thanks in advance.

---

### Post by r-senior on 2013-03-23
You should look into [Zenity]("https://en.wikipedia.org/wiki/Zenity").

EDIT: Manual page available here, with examples: [http://www.linuxmanpages.com/man1/zenity.1.php](http://www.linuxmanpages.com/man1/zenity.1.php)

Try this ...

```
zenity --entry --text="Password" --title="USB Device" --hide-text
```

---

### Post by ofnuts on 2013-03-23
> **Cyrebo said:**
> Hi, I am currently hardening my Kubuntu 12.10 OS and I want to run a shell script that automatically runs when my usb is plugged in. It should ask for authentication/authorization for my usb when its plugged in and deny ANY other device. So basically what I want is a lockdown of all external media except those which I have specified to be authenticated when they're plugged in. I've seen an example of running a script when a usb device is plugged in but I'm not sure how to incorporate a messagebox style prompt asking the user for a password and lockdown other devices. To me this is very challenging as I'm still relatively new to Linux and I probably wouldn't know how to do it on an OS I am familiar with.

Thanks in advance.

I'm wondering what you are trying to achieve... is there any USB device that can take control of your computer by merely being plugged in? Furthermore plugging things in requires physical access to the computer so other attacks would be more efficient (like stealing the hard disk...).

---

### Post by Cyrebo on 2013-03-26
Well, I simply want a shell script to run when my specific usb device is plugged in. The pass word is just an integrity check for both parties so it can only be me accessing the computer with that device. I then want to block other external media. This part can be done without plugging any device into the system. I've seen a thread on here where somebody runs a synchronisation script with a usb on plug in and i wanted to implement something similar buth for mutual authentication of device with computer.

---

### Post by schragge on 2013-03-26
[size=-1]*double post deleted*[/size]

---

### Post by schragge on 2013-03-26
You probably need a custom udev rule
[http://unix.stackexchange.com/questions/28548/how-to-run-custom-scripts-upon-usb-device-plug-in](http://unix.stackexchange.com/questions/28548/how-to-run-custom-scripts-upon-usb-device-plug-in)

---

### Post by ofnuts on 2013-03-26
That doesn't really answer my question about the assumed dangerousness  of plugged-in USB devices... 

OK, assume you can ask a password when one connects a USB device, so what? If there is an answer to the password prompt then that means the desktop is unlocked (if the desktop is locked this prompt is going to wait). Either it's you (or someone who has got your password...), or it's someone using your unlocked PC when you are not in sight. But since the desktop is unlocked, how do you prevent that person from killing the process that runs the script that asks for a password? And what happens while the script waits for the password? Is the device still usable?

Using udev with a specific configuration file could help achieve what you want to do, but no password would be necessary...

---

### Post by Cyrebo on 2013-03-26
> **ofnuts said:**
> That doesn't really answer my question about the assumed dangerousness  of plugged-in USB devices... 

OK, assume you can ask a password when one connects a USB device, so what? If there is an answer to the password prompt then that means the desktop is unlocked (if the desktop is locked this prompt is going to wait). Either it's you (or someone who has got your password...), or it's someone using your unlocked PC when you are not in sight. But since the desktop is unlocked, how do you prevent that person from killing the process that runs the script that asks for a password? And what happens while the script waits for the password? Is the device still usable?

Using udev with a specific configuration file could help achieve what you want to do, but no password would be necessary...

I understand where your coming from but my emphasis wouldn't really be on the desktop itself its the copying of data onto the desktop. Of course anybody can sneak in somehow and do whatever they want with a machine so that's probably not even up to the security I wanna implement. I want it to be in such a way that files don't get copied to or from the system without a password. So its OS hardening but not the actual OS the files on the OS if you get what I mean? I can deal with the actual OS later, just need to get this down first. I'm pretty sure someone out there has done something like this before, I just need to find out how if anyone can tell me.

---

### Post by Vaphell on 2013-03-26
> I want it to be in such a way that files don't get copied to or from the system without a password.
the point is when the disk is mounted with your permissions or even in readonly mode, the data can be copied. In such a scenario slapping a password on top is like putting a note saying 'please don't steal it' next to a $100 bill and expecting it to work. You can completely ignore it, navigate to the source via file browser or terminal and copy.

options i see:
#1 encrypt your usb device and ask for password to decrypt it
#2 make your system mount the device with permissions set to require admin credentials (so you have to go through sudo to get to the data), custom user account made only for that purpose would work too
#3 make your system mount the device with you as an owner and do not give access to your account to others (all people using the computer should have their own account either way)

only #1 truly protects the data from unwanted access (authorization is attached to the device not the machine), #2 and #3 can be easily circumvented by plugging in to another computer or whatever because the data on the device is there in plain view and you can obfuscate it a bit at best.

---

### Post by ofnuts on 2013-03-27
> I want it to be in such a way that files don't get copied to or from the system without a password.

Then make mounting disks require root privileges.... and look at your mail client, instant messaging client, ftp client, source control system, and web browser(s)...

---

### Post by Cyrebo on 2013-03-27
> **ofnuts said:**
> Then make mounting disks require root privileges

Could you please elaborate on this or point in the right direction? Perhaps where and how its done on a typical Linux file system?

---

### Post by Cyrebo on 2013-03-27
> **Vaphell said:**
> the point is when the disk is mounted with your permissions or even in readonly mode, the data can be copied. In such a scenario slapping a password on top is like putting a note saying 'please don't steal it' next to a $100 bill and expecting it to work. You can completely ignore it, navigate to the source via file browser or terminal and copy.

options i see:
#1 encrypt your usb device and ask for password to decrypt it
#2 make your system mount the device with permissions set to require admin credentials (so you have to go through sudo to get to the data), custom user account made only for that purpose would work too
#3 make your system mount the device with you as an owner and do not give access to your account to others (all people using the computer should have their own account either way)

only #1 truly protects the data from unwanted access (authorization is attached to the device not the machine), #2 and #3 can be easily circumvented by plugging in to another computer or whatever because the data on the device is there in plain view and you can obfuscate it a bit at best.

Can you be as kind enough to show me an example of how to do number 1 manually, e.g. a c/c++program of some sort perhaps? I've heard about software like TrueCrypt that does something similar  but it doesn't really do it the way I want because it is just an application.

---

