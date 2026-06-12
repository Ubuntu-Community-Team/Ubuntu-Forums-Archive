---
title: "Fans and Temps"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by capleton on 2008-04-24
I was surprised not to see any temp monitor or fan controller built into ubuntu.

I tried "compiling" (not sure if that's the right word) gkrellm and gkrellm-i8k from Synaptic Package manager, but I'm not quite sure how to use them.  I also tried following the [How to]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29"), but the command sudo apt-get install lm-sensors brings back ```
:~$ sudo apt-get install lm-sensors
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

``` I don't know what other process might be using it, or even how to check and see for that matter.

I used i8kfan in Windows (its an Inspiron e1505), and what I was hoping for was something like that (or like Speedfan)  possibly with a GUI.  But the main thing is just that I've had some fan/temp issues in the past, and I would like to be able to monitor them.

-->  **How could I monitor fans/temps in Ubuntu Gibbon?**

---

### Post by dmub82 on 2008-04-24
```
sudo apt-get install mbmon
```

```
sudo mbmon
```

That's text-only but it'll tell you your temps and fan speeds (unless you've got some weird mobo that doesn't report them right, I guess, but that's beyond my knowledge).

---

### Post by sukamusiru on 2008-04-24
I believe Conky does this as well.

---

### Post by elmer_42 on 2008-04-24
Conky relies on Terminal commands as far as I know, so it would really just be an extension of the Terminal that is embedded into the desktop.

---

### Post by tamoneya on 2008-04-24
as long as you are positive that no other processes are using synaptic```
sudo rm /var/lib/dpkg/lock
``` Then try to perform the install.

---

### Post by Paqman on 2008-04-24
There's also [sensors-applet](apt:sensors-applet), that you can add to a panel to display all sorts of stuff.

If you want more info than you could shake a stick at, you can always start messing around with Conky.

---

### Post by niteshifter on 2008-04-24
Hi,

> I don't know what other process might be using it, or even how to check and see for that matter.

Let's try this. In a terminal type:
```
ps -A | grep "synaptic"
```

If you get a return, synaptic is in use.

You can "inventory" the running process with just
```
ps -A > processlist.txt
```

which will create a file "processlist.txt" which you can examine with a text editor like gedit.

Another handy tool is
```
pstree
```

...and you can redirect it's output as well:
```
pstree > ptree.txt
```

pstree shows the relationship among processes, i.e, who called what.

Look thru the ps / pstree outputs for items containing these words: synaptic, apt, dpkg. 

You don't see anything - and you haven't started apt-get (or similar) or synaptic, then do as tamoneya suggests and delete the lock file.

---

### Post by capleton on 2008-04-24
Here are the results from pstree (great command btw)```
:~$ pstree
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9472;&#9472;3*[{NetworkManager}]
     &#9500;&#9472;NetworkManagerD
     &#9500;&#9472;acpid
     &#9500;&#9472;apturl&#9472;&#9516;&#9472;gksu&#9472;&#9472;&#9472;synaptic&#9472;&#9472;&#9472;gnome-pty-helpe
     &#9474;        &#9492;&#9472;{apturl}
     &#9500;&#9472;atd
     &#9500;&#9472;atieventsd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;61*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dd
     &#9500;&#9472;dhcdbd&#9472;&#9472;&#9472;dhclient
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data-}]
     &#9500;&#9472;evolution-excha&#9472;&#9472;&#9472;{evolution-excha}
     &#9500;&#9472;fast-user-switc
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;5*[{firefox}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg&#9472;&#9472;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;bluetooth-apple
     &#9474;                             &#9500;&#9472;compiz&#9472;&#9472;&#9472;compiz.real&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;compiz-decorato&#9472;&#9472;&#9472;gtk-w+
     &#9474;                             &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;{evolution-alarm}
     &#9474;                             &#9500;&#9472;gnome-panel&#9472;&#9472;&#9472;{gnome-panel}
     &#9474;                             &#9500;&#9472;gnome-settings-&#9472;&#9516;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;                             &#9474;                 &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9474;                             &#9474;                 &#9492;&#9472;{gnome-settings-}
     &#9474;                             &#9500;&#9472;nautilus
     &#9474;                             &#9500;&#9472;nm-applet
     &#9474;                             &#9500;&#9472;python
     &#9474;                             &#9500;&#9472;seahorse-agent
     &#9474;                             &#9500;&#9472;tracker-applet
     &#9474;                             &#9500;&#9472;trackerd&#9472;&#9472;&#9472;2*[{trackerd}]
     &#9474;                             &#9500;&#9472;update-notifier
     &#9474;                             &#9492;&#9472;{x-session-manag}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyboard-
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daemo}]
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;gweather-applet
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-cpuf
     &#9474;                    &#9500;&#9472;hald-addon-dell
     &#9474;                    &#9500;&#9472;hald-addon-inpu
     &#9474;                    &#9492;&#9472;hald-addon-stor
     &#9500;&#9472;hcid&#9472;&#9472;&#9472;2*[bluetoothd-serv]
     &#9500;&#9472;klogd
     &#9500;&#9472;mixer_applet2&#9472;&#9472;&#9472;{mixer_applet2}
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd
     &#9492;&#9472;wpa_supplicant

```  
And there is synaptic under "apturl" I quit out of it in System Monitor, and now pstree leaves this entry "     &#9500;&#9472;synaptic&#9472;&#9472;&#9472;gnome-pty-helpe
" i And that one does not come up in System Monitor, so I'm not quite sure how to quit out of it.

dmub82, I get an error when i do that command, maybe b/c of the process above?

and tamoneya, "sudo rm /var/lib/dpkg/lock" does not work either

Should I look into abandoning this and installing Conky?  what are the differences?

Where do i do from here?

---

### Post by Paqman on 2008-04-24
> **capleton said:**
> 
Should I look into abandoning this and installing Conky?  what are the differences?

Where do i do from here?

Conky is pretty complicated for what you want. Did you try sensors-applet?

---

### Post by capleton on 2008-04-24
> **Paqman said:**
> Conky is pretty complicated for what you want. Did you try sensors-applet?

Paqman, sorry I meant to include this in my last post.  I installed sensors-applet, and I've been searching the google and ubuntu forums to figure out how to configure/use it.  I followed [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29") guide, and it seems to be working, I get 40.0C for my cpu.  No GPU or HD though, any ideas?  

also the guide goes on to talk about fan adjustment, I didn't want to continue with that untill I asked if I should uninstal all the other stuff I have now like gkrellm and gkrellm-i8k?  Also, I dont really know what these last two things actually do?

---

### Post by capleton on 2008-04-25
UPDATE:

I've almost got gkrellm working!  Just trying to configure it--I've been going through some guides.  Something called THM pops up next to the cpu temps, is that motherboard or gpu?  And does anybody know of a good resource for a complete newb like me on GKrellM?

---

### Post by niteshifter on 2008-04-25
Hi capleton,

apturl provides a way for a browser to get and install software from the repos. It functions like a link (it is a link) in a web page (or HTML file being shown).

What's curious to me is why it's showing in your process list. Have any web pages open? Note that this does not have to be an http:// URL, file:// pages can invoke this as well.

You could try:
```
ps -A | grep "apturl"
```

This should return something like this:
```
DDDD ? 00:00:00 apturl
```
Those first digits (DDDD in the example) are important for the next step, where we'll kill off apturl:
```
kill DDDD
```

Now, you should be able to delete the lock file (should it still exist) and use apt-get successfully.

---

### Post by Paqman on 2008-04-25
> **capleton said:**
> Paqman, sorry I meant to include this in my last post.  I installed sensors-applet, and I've been searching the google and ubuntu forums to figure out how to configure/use it.  I followed [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29") guide, and it seems to be working, I get 40.0C for my cpu.  No GPU or HD though, any ideas?  


Er, i've never had to do any hackage to configure it. Just right-click and use [the GUI](http://sensors-applet.sourceforge.net/index.php?content=screenshots).

---

### Post by capleton on 2008-04-25
Awesome!  Thanks for all the help everybody!

Niteshifter, that worked money

Paqman, I finally got "Hardware Sensors Monitor" set up on a panel--I hadn't seen it under "add to penel.  But the only sensors that I can seem to bring up are core0 core1 and cpu,  no GPU or fan monitor, any ideas?

GKrellM is working too, and I enabled the Dell I8K plugin within it and checked "display fan speeds" in the Configuration tab; also no GPU info.  I checked in /usr/bin/, and there is i8kfan (it's a shortcut to i8kctl) but when I put /usr/bin/i8kfan into the terminal, it brings up "no such file or directory"

So where do I go from here?

Thanks for all the help!

---

### Post by capleton on 2008-04-25
UPDATE:

I've almost got it...

I have "Sensors Applet" running in a panel with a launcher for GKrellM right next to it if I need to actually change the fanspeeds.  (Plus I enabled "remember window position" in gkrll, so it pops up just beneath all the icons in on the panel 8) )  
But I'm still *loosing it* trying to figure out these last two things:

[COLOR="DarkRed"]-->  1. In the "properties" of the GKrellm app launcher; there is a space for "command" which is currently set to "gkrellm".  **I was wondering if there is a way to change that command so that when I click the icon once, gkrellm will open, but if I click it again, it will close (or hide) gkrellm?**[/COLOR] 

EDIT:  Figured this out!  Check it out [here.]("http://ubuntuforums.org/showthread.php?t=767987")

-->  2. **Still can't read GPU temperature.**  I've searched everywhere.  There were guides for Nvidia cards, but nothing for my ATI x1400.  **How could I get this to work? ** (new driver maybe?)

-->  3.  **Should I be posting in a different forum?**

Thanks in advance

---

### Post by capleton on 2008-04-26
Getting there...  (see above)

---

### Post by Nameless_one on 2008-05-13
I am also looking for a way to monitor my ATI card's temperature. I think the first step is to ensure that your motherboard has some kind of support for GPU temperature reading. 

I am trying to figue out wether mine does, can anyone help? 

I have installed lm-sensors, and have run sensors-detect, and the only temperature monitoring modules the program found are:
-w83627ehf
-k8temp

I googled it and saw that these have to do with CPU temperature and fan speeds and such. So lm-sensors cannot read my GPU's temperature. I also read that there is also ACPI, would that be able to read my card's temp? 

I am quite sure that my card has a temperature reading chip, it's fairly recent (an X1650PRO).

---

### Post by psyke777 on 2008-05-26
sudo modprobe i8k

Install sensors-applet then add to your panel "Hardware Sensors Monitor" applet. If it is on your panel already, remove it and re-add it. Change its properties to monitor the i8k fans and the CPU.

Your CPU may be able to handle very high temperatures. My Latitude c610 has a 100 _Celcius_ limit. So don't be suprised if it takes a lot to start the fans. My fans used to kick in in the high 40s but now they start in the mid 60s and turn off again in mid 40s.

gkrellm & gkrellm-i8k packages will also control your Dell fans and it will turn them on at lower temperatures which can be easily configured in gkrellm.

You can also manually control the fans with [i8kfan]("http://www.digipedia.pl/man/i8kfan.1.html") which is part of i8kutils package.

---

