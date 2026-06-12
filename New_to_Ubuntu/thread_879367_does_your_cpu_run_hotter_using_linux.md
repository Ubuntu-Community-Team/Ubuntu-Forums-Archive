---
title: "does your cpu run hotter using linux"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-08-03
Seems mine does: I have dual boot and when I am in hardy I can hear my power supply fan going full tilt and I can feel the heat coming out.. thats just doing nothing.. then I reboot into windows xp and first thing is check cpu temp and it will be about 38c and falling  / just checked now and is down to 31c  
    I just wonder what that something is that chews power and cpu...

---

### Post by tuxxy on 2008-08-03
Are you running Hardy? 

Its a long shot bu maybe a zombie process running before you switched to win?

---

### Post by OutOfReach on 2008-08-03
Well not really, It's about the same for both Ubuntu and Win XP.

---

### Post by bpowell2005 on 2008-08-03
My Laptop is louder (more fan action) when running Ubuntu Hardy vs. Windows XP pro. I just figured Windows was better as power / CPU management. Ubuntu is much quieter than PC Linux OS 2007 though! I used to heat the house with my lappy running PCLOS!

---

### Post by MeTylerDurden on 2008-08-03
Hardy is my OS 8.04 hardy heron :)  anyway just wanted to get this off my mind..   I am really into saving energy (bless you al gore you little energy miser)  I don't know if it wears and tears the pc .. but what is a zombie process?? sounds alltogether frightening

---

### Post by CloudFX on 2008-08-03
Ubuntu actually uses a lot less power than Windows for me.  My laptop is always quieter, and the battery lasts a lot longer on maximum brightness.

---

### Post by tuxxy on 2008-08-03
I meant a process that may of failed like firefox and didnt get killed correctly, which has carried on using CPU constantly, I have had this issue with npwrapper

---

### Post by cariboo on 2008-08-04
My cpu runs hotter running Vista and it also uses more ram. I am currently running Intrepid alpha 3, and I've got 6 zombie processes running at the moment, all gnome related. :)

Jim

---

### Post by bpowell2005 on 2008-08-04
> **CloudFX said:**
> Ubuntu actually uses a lot less power than Windows for me.  My laptop is always quieter, and the battery lasts a lot longer on maximum brightness.

I've had the opposite experience...Less batter life in Linux...I'm sure if I compiled a custom kernel, and modified the "stock" installation, it might work better; but from a "stock" installation standpoint, Windows has been better for power on my Compaq 6510b.

---

### Post by mcduck on 2008-08-04
As far as I know Ati's and nVidia's Linux drivers have worse support for GPU power saving features (or no support at all) than the Windws driver has. This would be the most likely reason for shorter battery life on laptops with more powerful graphics chips, and also the most likely reason for original user's problems, as it's the PSU fan that's speeeding up, not the CPU fan (meaning that the systems power usage is higher, instead of CPU's power usage).

It's hard to know what the real situation is without knowing what hardware you have, and what drivers youa re using.

Anyway, it's also possible to change the CPU frequency scaling governor to prefer lower frequencies when running on battery power (depending on your CPU, of course). Of course thew effect you get this way is nothing compared to what the power hungry graphics chips use.. Also the display backlight is one of the most power hungry components on modern laptops, dropping the brightnsess by couple of steps can have a huge effwct on your battey life.

---

