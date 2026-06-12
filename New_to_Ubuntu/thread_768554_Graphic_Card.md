---
title: "Graphic Card"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by mecanologo on 2008-04-26
Hey all!
I'm completely new at linux, yet, not at computers.
I've been able to install every single driver I needed except two:
[LIST]
[*]Ir Port
[*]Video Card (Nvidia Geforce4 go 440)  [32 mb]
[/LIST]
so, I want your help to fix the problem of the Nvidia by now.
I found some forums where users did solved their problems, yet they use some terms I can't understand or execute.
thanks!!

---

### Post by Qwerty_ on 2008-04-26
Ok to install your graphics you are going to have to install the restricted drivers.

you can do this quite easily but firstly you have to make sure you have all your software sources selected.

Go to System>Administration>Software Sources 

and make sure they are all ticked bar the source code one.

Then you need to go to

System>Administration>Hardware Devices

from in there you are able to enable your nvidia card and install nividias drivers.

Hope that helps I am not sure what to do with the ir port though.

---

### Post by mecanologo on 2008-04-26
And with such driver will I be able to run the Desktop Effects??

---

### Post by mecanologo on 2008-04-26
Surprise!!!
Whitescreen!

---

### Post by Joeb454 on 2008-04-26
I think this is an issue with Compiz rather than Ubuntu. It could also be the graphics driver.

What effects are you trying to run? Some will need higher than a 32Mb card, though most should be ok.

---

### Post by Michael.Godawski on 2008-04-26
Try to boot into the recovery mode and run this:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by mecanologo on 2008-04-26
> **Joeb454 said:**
> I think this is an issue with Compiz rather than Ubuntu. It could also be the graphics driver.

What effects are you trying to run? Some will need higher than a 32Mb card, though most should be ok.

I'm not enabling it by now. First I want to enable it successfully. Thanks

> **Michael.Godawski said:**
> Try to boot into the recovery mode and run this:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

How should I use the recovery?
Resume, Boot or xFix?
Thanks

---

### Post by mecanologo on 2008-04-26
Sudo: unable to resolve host Jose-Linux

---

### Post by mecanologo on 2008-04-26
Fine, thanks
Now I may boot, but my drivers are not yet the right ones...
What may I do?

---

### Post by vidus on 2008-04-26
go to synaptic, press search and search for "envy" mark for installation the core and the gtk. apply.

once installed it will be in applications > system tools.

run the program, select nvidia and apply. 

this will install your drivers. reboot and you should be good to go.

---

### Post by mecanologo on 2008-04-26
Seems to be going!
By now it's installing, yet, it correctly detected all of its settings.
Now it's downloading some things, I hope it works...
Finished dlling and its unpacking things and setting it up!
"Setting up Nvida-settings"
"Operation complete"
"Restart? Y"
Nice!
Works now, thanks
Buuuut, my screen resolution is limited to 1024*768
Is there a way to make it higher?
it must be 1405*? fogot
LOL

---

### Post by vidus on 2008-04-26
not sure why you are limited... that is strange. im sorry i cant answer that!

---

### Post by mecanologo on 2008-04-26
thank you very much!
I;ll continue researching.

---

### Post by Fury5000 on 2008-04-26
> **vidus said:**
> go to synaptic, press search and search for "envy" mark for installation the core and the gtk. apply.

once installed it will be in applications > system tools.

run the program, select nvidia and apply. 

this will install your drivers. reboot and you should be good to go.

WOW!!! thanks so much for posting this!!!... this is the first time in 3 version of Ubuntu I have EVER had GL working on this old Toshiba Satellite with the Geforce 440 Go chip....  I followed your instructions but the auto didnt work and had to go manual and select 96.43.05 version...rebooted and saw the nVidia logo for the first time...  just tested google earth and runs flawlessly.  THANK YOU!!!

Follow-up:.. just tried compiz and its blisteringly fast..full cube with all settings at max running 1280x1024 on this 440 go with 64meg ram and it runs just as fast as the 8800GT 512 runs it... truly amazing.

---

