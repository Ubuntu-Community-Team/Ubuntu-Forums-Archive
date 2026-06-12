---
title: "font problems"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-10-05
since the last updates when i open the terminal have trouble reading the font also all  when i open the ubuntu software all the main headings are un-readable.

---

### Post by rburkartjo on 2011-10-11
font in ubuntu software center is still messed up and unreadable

---

### Post by effenberg0x0 on 2011-10-11
Hey,

You mean the Terminal Window inside a GUI session or the Virtual Terminals (VT) (accessible using Ctrl+Alt+F1 to F6)?

If you mean the first case (Terminal Window inside GUI session), on Unity select the Terminal Window, go to the Panel, click Edit / Profile Preferences / General Tab, and tell us what it looks like there. Do you have the "System Fixed Width Font" selected? If not, which font is selected there?

If you mean the second case (VTs), then we have to adjust grub options. (VT resolution, framebuffer, etc)

Regards,
Effenberg

---

### Post by rburkartjo on 2011-10-11
eff the windows terminal and i have it set to system width font. it has improved lately but after i type somethneg  like and then enter

sudo aptitude update && sudo aptitude safe-upgrade
 terminal goes blurrey.
also on ubuntu software center only problem is with the start page-
our star apps etc. everything is blurred and the categories listed on the left hand side are not readable. have had these problems for over a week and my updates are current.

---

### Post by effenberg0x0 on 2011-10-11
Well I'm missing the good-old Font Config Window, in which we could select the font face and size for applications, select Rendering Details (DPI, hinting, etc). I don't think Oneiric has it, as it seems.

I went to /etc/fonts/fonts.conf to do things manually, but now we have a big warning telling us to not mess with that file while they're finishing fontconfig.

So, only way I can think off is to set some hinting in your Home Directory ~/.fonts.conf file.

Backup the file first, so we can easily revert later, if needed:

```
sudo mv ~/.fonts.conf ~/.fonts.conf.backup
sudo gedit ~/.fonts.conf
```Add the BOLD lines to your file. It will look like this:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!--
    This file is maintained by Font Manager.

    If you wish to make any changes it is suggested you do so using

        /home/al/.config/font-manager/local.conf

    Any changes made to this file will be automatically relocated there
    at startup and any settings already in that file will be overwritten.
-->

    <include ignore_missing="yes">/home/al/.config/font-manager/conf.d</include>
    <include ignore_missing="yes">/home/al/.config/font-manager/directories.conf</include>
    <include ignore_missing="yes">/home/al/.config/font-manager/local.conf</include>
    <include ignore_missing="yes">/home/al/.config/font-manager/select.conf</include>
[B]  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>[/B]
</fontconfig>

```Save your work, reset fontconfig, and then restart the GUI session:
```

sudo dpkg-reconfigure fontconfig
sudo service lightdm restart

```And lets hope it helps you. Otherwise we'll have to look at other settings.

Regards,
Effenberg


[B]EDIT
[/B]- There's a bug report, with an attached screenshot. You should have a look to see if that's what you are seeing there too and, if so, "me too" on that bug report. The URL is [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/864855](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/864855)

- I forgot to ask you to change your font in the Terminal (uncheck system default monospace) and select other font (such as Ubuntu Mono Size 9, for example), run a command and see if you still get this blurry behavior you reported.

---

### Post by rburkartjo on 2011-10-11
eff tks for your help. problem still persists with ubuntu software center. not a big deal usually use spm. just aggravating.

---

### Post by cariboo on 2011-10-11
I used gnome-tweak-tool to set system wide fonts, I have Ubuntu-mono, set for mono space font, and in my opinion the terminal font looks pretty good.

---

