---
title: "2 questions, dual booting and resolution"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by ktulu19 on 2008-07-19
hi everyone, as hinted at in the title, i have 2 questions.

1. does anyone know of a good guide to dual booting XP where i can share files between the OS's.

2. i'm not able to set up ubuntu to use a 1280 1024 screen resolution, i'm stuck at 1024 768, i'm using a nvidia card, could that be the culprit?

thanks!
:guitar:

---

### Post by niyonk on 2008-07-19
Welcome :)

Have you tried system->administration->hardware drivers?? EDIT: this will check if the nvidia driver is enabled in the first place

And try [this]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") for dual-booting ;)

Anything else, don't hesitate to ask

Cheers! :biggrin:

P.S: we are all n00bs

---

### Post by overdrank on 2008-07-19
> **ktulu19 said:**
> hi everyone, as hinted at in the title, i have 2 questions.

1. does anyone know of a good guide to dual booting XP where i can share files between the OS's.

2. i'm not able to set up ubuntu to use a 1280 1024 screen resolution, i'm stuck at 1024 768, i'm using a nvidia card, could that be the culprit?

thanks!
:guitar:

Hi and welcome, you should be able to read and write to windows data with ubuntu but this link may help
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
Also if you are using nvidia graphics then you can use the nvidia settings to help with the resolution. Use synaptic manager located under system, administration. Search for nvidia settings and install. Then you can use the command ```
gksu nvidia-settings
```  to help with the resolution.

---

### Post by ktulu19 on 2008-07-19
i have enabled the nivida driver, when i finished installation it notified me of it, and i then enabled it...
i've seen somewhere that there is a file that must be edited to allow the higher resolution, is that anything?

---

### Post by overdrank on 2008-07-19
> **ktulu19 said:**
> i have enabled the nivida driver, when i finished installation it notified me of it, and i then enabled it...
i've seen somewhere that there is a file that must be edited to allow the higher resolution, is that anything?

As I stated in my previous post that the nvidia setting well help to do this. The xorg is not like it has been in the past. You may also try the command ```
gksu displaycofig-gtk
``` but beware that you can really mess up the GUI (desktop) and if so you can use the xfix option by booting to recovery mode from the grub.

Edit also you can use the command ```
lspci
``` in the terminal and this will identify your hardware. Look for VGA and that is the model of the graphics card then you may search the forums.

---

