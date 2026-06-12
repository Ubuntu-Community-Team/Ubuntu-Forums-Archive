---
title: "unable to save NVIDIA settings"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by SandyM on 2008-07-19
HI! I was a windows patriot and has only recently installed ubuntu on my brothers recoomendation. Therefore I am new to linux. 
I am facing a problem while saving my nvidia settings. I use command
'gksudo nvidia-settings' to configure nvidia settings.
Although settings seem to have saved but whenever I restart my computer they revert to default. PLEASE HELP!!!!!!!!!!!!!

---

### Post by silkstone on 2008-07-19
System > Preferences > Sessions > Startup Programs

Click on Add

In the Command line, type **nvidia-settings -l**  (That's a lower case letter L)

(Put anything you like in the name and comment lines!)

That will load the settings you've chosen on startup. (The -l switch tells it to load the settings, rather than launch the whole application.)

---

### Post by PmDematagoda on 2008-07-19
Also did you instruct nvidia-settings to save the changes to the xorg configuration file? Perhaps that is what you need.

---

### Post by neurostu on 2008-07-19
To save the xorg.conf file you must run the nvidia-settings as root, the only way I've been able to do it is to run nvidia settings with the following command:
```

gksudo nvidia-settings

```

---

### Post by daimaru on 2008-07-19
he used gksudo so I think [[COLOR=#d40000]**PmDematagoda**[/COLOR]]("http://ubuntuforums.org/member.php?u=361835") answer seems right you have to checkmark the part where it says to save to xorg.conf.

if that does not work. just edit your xorg.conf file manually. that always works. add your preferred resolution to the resolution list and restart xserver.
Oh and you can just use gksu (less typing :) )

---

