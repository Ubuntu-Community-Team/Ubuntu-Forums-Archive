---
title: "an easy way to make your remote control work in Ubuntu/Debian (pseudo keyboard)"
date: 2010-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by I'mGeorge on 2010-12-04
First of all you have to get your remote control specific codes (scancodes) from here [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/) . Edit the file and delete everything except the codes situated between **begin codes** and **end codes**. Let's say the file I've downloaded, containing the proper codes, it's called rem_codes. Copy the file with root privileges in /lib/udev/keymaps

```

sudo cp rem_codes /lib/udev/keymaps

```   

Now you have to determine which is your IR event. You can do this reading the /proc/bus/input/devices file 
```

gedit /proc/bus/input/devices

```
In my case the section that counts it's this

```

I: Bus=0001 Vendor=107d Product=6618 Version=0001
N: Name="cx88 IR (Leadtek TV2000 XP Glob"
P: Phys=pci-0000:03:06.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:14.4/0000:03:06.0/rc/rc0/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=100003
B: KEY=102fc336 235084800000000 0 400018001 180c0004801 1e000000004400 10000010000ffe

```

Here I can see that my Leadtek TV tuner uses event5 as a handler for infra red.

This being said you have to run the following command
```

/lib/udev/keymap input/event5 /lib/udev/keymaps/rem_codes

```
at startup, using the sessions manager from Gnome for example System–>Preferences–>Sessions, but this varies according to what desktop/wm everybody uses. For the moment just type it in your terminal.

After that playing along with xev and/or showkey terminal apps will help you get your remote control keycodes. I would recommend xev as for me was far more accurate. You can use your keycodes as regular shortcut keys, to open any kind of applications, execute commands and pretty much everything your heart desires. This can be done depending again on what desktop/wm everybody uses. In fluxbox for example  adding a line something like this

```

122 :Exec amixer set Master 2- & amixer set PCM 16- & tvtime-command MIXER_DOWN 7

```

in ~/.fluxbox/keys will make the alsa and tvtime volume decrease at approximative rates, when the RC's volume down button it's pressed, which has the 122 keycode. Another old fashioned way would be to make a ./xmodmap file, and for this are numerous tutorials just google search about it.

By the way this tutorial implies that your IR sensor it's recognised by your kernel.

Cheers

---

