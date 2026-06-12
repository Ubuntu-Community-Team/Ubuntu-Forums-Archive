---
title: "Ubuntu on Acer Aspire D250"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by n00bi on 2012-04-19
Hi Everyone 

I have just installed my 11.10 distro on my netbook the aspire one D250, and it was the most seamless and most amazing experience ever. 

BUT.....

The netbook keyboard is broken and i am using a USB external keyboard and i can not seam to adjust my screen brightness as it is set by default to the lowest setting.

I have tried looking up some terminal commands but at no avail. would anyone be able to help ?

---

### Post by kazztan0325 on 2012-04-19
Hi n00bi,

Have you tried this?

1. Open "System Settings" window.
2. Click on 'Screen' icon.
3. Adjust Brightness with slider.

Hope this helps.

---

### Post by flurospar on 2012-04-19
Press [Ctrl] + [Alt] + [F1]. You'll see a black screen with a username prompt at the end. Can you type your username, password, here and make a successful login with your netbook keyboard?

---

### Post by n00bi on 2012-04-19
Yeah, it's not responsive, it just moves right and left and nothing changes.

---

### Post by n00bi on 2012-04-19
I'm not facing a problem logging in, I am only facing a problem with my screen brightness

---

### Post by cogier on 2012-04-19
Have a look at the BIOS settings. There is sometimes a setting for the screen brightness there.

---

### Post by n00bi on 2012-04-19
I checked the bios, not even there. and i used some kind of code some soda crap, also couldnt get it to work.

All i want is to increase the brightness and make it default.

---

### Post by audiomick on 2012-04-19
What happened when you tried this?


> **kazztan0325 said:**
> Hi n00bi,

Have you tried this?

1. Open "System Settings" window.
2. Click on 'Screen' icon.
3. Adjust Brightness with slider.

Hope this helps.

That wont change the default brightness, but it should let you brighten the screen once you are booted and logged in.

I'm not sure where the default brightness is. Need to find out myself, actually. When I boot this machine on battery power in daylight, it is so dark I can hardly read it...

---

### Post by NikTh on 2012-04-19
> **n00bi said:**
> 

All i want is to increase the brightness and make it default.

For default i don't know , but try this for the brightness effect to work 
```
sudo gedit /etc/default/grub
```Find the line **GRUB_CMDLINE_LINUX=""** and make it like this **GRUB_CMDLINE_LINUX="acpi_osi=Linux"** . 
save the document and
```
sudo update-grub
```and reboot. 

i believe that you must be able then to adjust your brightness. Try and keyboard combination .. i think for acer are Fn + arrow keys . (left - right)

---

### Post by dzponce11 on 2012-04-19
> **NikTh said:**
> For default i don't know , but try this for the brightness effect to work 
```
sudo gedit /etc/default/grub
```Find the line **GRUB_CMDLINE_LINUX=""** and make it like this **GRUB_CMDLINE_LINUX="acpi_osi=Linux"** . 
save the document and
```
sudo update-grub
```and reboot. 

i believe that you must be able then to adjust your brightness. Try and keyboard keys.. i think for acer are Fn + arrow keys . (left - right)

That should do the trick.

---

### Post by n00bi on 2012-04-21
Hi Everyone i tired the above command

and i received this.

Cannot Open Display

Run gedit --help

The slider wont work and Fn plus arrows gives me an error sign "circle with a strike through"

---

