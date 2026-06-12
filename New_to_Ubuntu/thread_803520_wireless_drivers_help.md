---
title: "wireless drivers help ?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by harnick3 on 2008-05-22
I need help... I have recently ordered a live cd and I am getting the right drivers for my hardware and software I only need drivers or software for my belkin wireless card...

Company: Belkin
Wireless Type: G+ MIMO
Uses: usb
Model: F5D9050
version: 40001uk

Please help me this is the only thing that needs driver/software (apart from the eyetoy) that I still need to trackdown before the big switch over in a week or 2 time. I cannot return this wireless card and my mum is not prepared to buy me a new one.

Is there any software or drivers I could use?

Thanks in advance.

---

### Post by dstew on 2008-05-22
From postings on the forums, it seems that in the past devices like this that use RT73 needed a lot of help to get working. Hardy is supposed to support it now out of the box, but I couldn't find any confirmation of this.

---

### Post by eldragon on 2008-05-22
> **dstew said:**
> From postings on the forums, it seems that in the past devices like this that use RT73 needed a lot of help to get working. Hardy is supposed to support it now out of the box, but I couldn't find any confirmation of this.

if its a rt73 chipset, follow this link where i explain how to get it working (on gutsy, but hardy works too).....

[http://ubuntuforums.org/showthread.php?t=704260](http://ubuntuforums.org/showthread.php?t=704260)

---

### Post by sam_delta on 2008-05-22
make sure what chipset you use by typing ```
lspci
``` into the terminal or ```
lsusb
``` if its a usb adapter

sam

---

### Post by guildofghostwriters on 2008-05-22
I just did a quick google and as far as I can tell, this wireless adapter uses the ralink rt73 chipset. If this is the case, it SHOULD work out of the box in Hardy. However, I use a (different) rt73 wireless usb dongle and I had trouble with it which was solved by installing the serialmonkey drivers. Follow this post - [http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2](http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2)

It works perfectly. The only slight problem with it is that I can't get rutilt to remember save/load profiles unless I launch it from the terminal thus:
sudo su
sudo rutilt

However, as rutilt is a lot more reliable for me than network-manager then it's a very minor hardship.

EDIT: the above post wasn't there when I started typing this so apologies for that

---

### Post by harnick3 on 2008-05-22
Thankyou for quickly replying and i will use all of the suggested methords.

---

### Post by eldragon on 2008-05-22
> **guildofghostwriters said:**
> I just did a quick google and as far as I can tell, this wireless adapter uses the ralink rt73 chipset. If this is the case, it SHOULD work out of the box in Hardy. However, I use a (different) rt73 wireless usb dongle and I had trouble with it which was solved by installing the serialmonkey drivers. Follow this post - [http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2](http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2)

It works perfectly. The only slight problem with it is that I can't get rutilt to remember save/load profiles unless I launch it from the terminal thus:
sudo su
sudo rutilt

However, as rutilt is a lot more reliable for me than network-manager then it's a very minor hardship.

EDIT: the above post wasn't there when I started typing this so apologies for that

i resorted to the following to get rutilt to store changes (for all users, may i add).

first i ran rutilt with sudo from the terminal, created a profile.

exited and saved successfully.

then i moved the folder ~/.config/rutilt to /root/.config/rutilt

i chowned root:root and chmoded it to 777 (to be in the safe side)

i then did a hardlink to the moved folder
```

$ ln ~/.config/rutilt /root/.config/rutilt

```

this had to be done, because, when running rutilt without sudo, and then making it take privileges makes it point to the root profile. its quite odd.

now, if you wish for every new user to have this same config (Something desirable). then you should create the same link in /etc/skel/.config

next step is to have rutilt to run when you log into your desktop.
for this, create a file at ~/.config/autostart/ called rutilt.desktop
and add the following in the file:
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=No Name
Name[en_US]=rutilit
Comment[en_US]=wireless manager
Comment=wireless manager
Exec=rutilt -t
X-GNOME-Autostart-enabled=true

```

next, chmod it for execution.

```

chmod a+x ~/.config/autostart/rutilt.desktop

```
you could place this file in /etc/skel/.config/autostart too.

remember that everything in the skel dir is root owned.

now, rutilt wont be able to modify wireless properties, but it will save profiles even if it says it couldnt. just remember to pick a profile with rutlit, and enter your password (there must be a way to put it into sudoers so that you dont need to enter a password, but i couldnt yet).

hope im clear enough :D

---

### Post by guildofghostwriters on 2008-06-04
> **eldragon said:**
> i resorted to the following to get rutilt to store changes (for all users, may i add)....

I didn't see this until just now - I moved this week and haven't had any time for online stuff - so apologies for appearing ignorant. I'll try this in a while when synaptic has finished installing some stuff and let you know how I get on. In the meantime, do you have to reinstall the rt73 drivers every time there's a kernel update? It's happened a few times to me - after the restart, the rt73 driver disappears from 'hardware drivers' and I have to follow your guide again. It's not the end of the world but I wondered if there was a way of avoiding it.

---

### Post by guildofghostwriters on 2008-06-04
Okay - I followed this and it's improved things but I'm not sure that I followed everything correctly. I'm little more than a month into my linux/ubuntu learning curve and that's mostly been a month of cocking things up!

Anyway, I wasn't entirely sure what you meant by the chown and chmodded instruction but assumed you meant the new rutilt folder under root so I did 

```
chown root:root /root/.config/rutilt
chmod 777 /root/.config/rutilt
```

and this didn't seem to produce any errors so I assumed I'd got it right. Then when it came to the hardlink instruction, it said that I couldn't hard link to a directory so I did it for the two files in the directory and that also seemed to work. Finally, after doing everything, I restarted but when rutilt launched automatically, it didn't have any saved profiles. After some fiddling around I discovered that it if I rebooted, created a profile then quit rutilt, it saved the profile and that profile is available when I reboot. I just have to select it and enter my password. So thanks for the guide - I'd been looking/posting for help about this for the last month so it's good to have made some progress on it at last!

---

