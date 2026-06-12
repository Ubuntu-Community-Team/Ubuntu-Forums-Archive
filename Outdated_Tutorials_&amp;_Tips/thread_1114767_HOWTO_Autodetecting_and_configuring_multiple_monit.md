---
title: "HOWTO: Autodetecting and configuring multiple monitors"
date: 2009-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by mikko.ohtamaa on 2009-04-03
A common problem for laptop users is that they use various display configurations. When traveling they use only the internal LCD panel, but in the office they use internal LCD panel + external display. It is pain to configure external display manually each time you plug it in. 

This HOW TO will give you instructions to create a shell script which will configure displays and Gnome panels according to the plugged in displays.

1. Install magnificent disper tool [https://launchpad.net/~wvengen/+archive/ppa](https://launchpad.net/~wvengen/+archive/ppa) by Willem van Engen. Currently disper supports nVidia only, but the author claims ATI support is possible to add by contributions.

2. Command 

```

  disper --displays=auto -e

```

will autodetect displays and set the extended desktop.

3. Dispering displays is not enough. You probably want to move Gnome panels to your primary (external) display when it is plugged in. 

Gnome architects have been clever. Gnome panel stores its settings in gconf registry. gconf registry is not just dummy storage backend; changing these values immediately reflect changes in applications using the registry. One of these applications is gnome-panel. This means that we can move the panels by editing its registry setting related to the monitor configuration.

Using gconf-editor command the critical settings can be found under:

```

/apps/panel/toplevels/bottom_panel_screen0/monitor
/apps/panel/toplevels/top_panel_screen0/monitor

```

Value = 0 -> panels on internal LCD
Value = 1 -> panels on External display

4. Let's make a little command line script which will 

  a) Detect and configure monitors

  b) Move gnome-panels according to the connected display count

See shell script [ATTACH]108498[/ATTACH]

5. Add monitor.sh  to your Startup Programs in System > Services menu, so it  will be run each time you login to Gnome.

Other pointers:

switchconf is a tool to switch between /etc configuration files and choosing the configuration from the b/apps/panel/toplevels/top_panel_screen0/monitoroot menu when starting the computer.

[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

nVidia settings low level poking:

[http://www.nvnews.net/vbulletin/showthread.php?p=1972884](http://www.nvnews.net/vbulletin/showthread.php?p=1972884)

nvidia-settings man page:

[http://linux.die.net/man/1/nvidia-settings](http://linux.die.net/man/1/nvidia-settings)

---

### Post by M4NIC on 2009-04-03
Awesome. Will this work with Intel graphic cards though?

---

### Post by binbash on 2009-04-03
Yes, same question, does this work on intel cards?

---

### Post by Geling on 2009-05-21
Works flawlessly on Lenovo Thinkpad T61 (Nvidia Quadro NVS 140M).

---

### Post by klemi on 2009-07-07
Hallo mikko.ohtamaa,

I have some question to your configuration:

With enter by:
```
klemens@klemens-laptop:~$ disper -l
display DFP-0: LPL
 resolutions: 320x240, 400x300, 512x384, 576x432, 680x384, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 960x600, 1024x768, 1152x864, 1360x768, 1440x900
display DFP-2: HP LP2475w
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 720x480, 700x525, 800x512, 720x576, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1280x720, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1600x1000, 1600x1024, 1680x1050, 1600x1200, 1920x1080, 1920x1200

```

Have I insert in Gnome panel the value DFP-0 and DFP-2 in this case?

Have you practice the nvidia-tool nvidia-settings to configure the xorg.conf?
Can you post your xorg.conf, please?

Can I do my autodedecting and configuration multiple monitors with single display configuration with laptop-display?

Thanks very much

Klemi

---

### Post by Thantos3000 on 2009-07-07
Great howto! Just wondering, is there a way to toggle between Laptop, extended, clone, and external?

---

### Post by Jenkins1 on 2009-10-07
This is a very good script and juet what I am after so thank you very much 

> **klemi said:**
> Hallo mikko.ohtamaa,

I have some question to your configuration:

With enter by:
```
klemens@klemens-laptop:~$ disper -l
display DFP-0: LPL
 resolutions: 320x240, 400x300, 512x384, 576x432, 680x384, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 960x600, 1024x768, 1152x864, 1360x768, 1440x900
display DFP-2: HP LP2475w
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 720x480, 700x525, 800x512, 720x576, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1280x720, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1600x1000, 1600x1024, 1680x1050, 1600x1200, 1920x1080, 1920x1200

```

Have I insert in Gnome panel the value DFP-0 and DFP-2 in this case?

Have you practice the nvidia-tool nvidia-settings to configure the xorg.conf?
Can you post your xorg.conf, please?

Can I do my autodedecting and configuration multiple monitors with single display configuration with laptop-display?

Thanks very much 

Klemi
I haven't adjusted the script in any way and my xorg.confirst as I login so I can avoid the flickerf is just set up for my laptop screen and no other screens. My xorg.conf is attached.
Is there anyway in which to make sure the script runs first as I login so that I can avoid the flicker?

---

