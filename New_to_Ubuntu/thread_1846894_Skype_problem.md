---
title: "Skype problem"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by jockyburns on 2011-09-19
I received a skype video call from my dad tonight and on the interface where it says, Start my video,,,, no amount of clicking would start my usb webcam. I eventually started it using Cheese webcam booth and sharing my screen on skype, but surely this can't be right,,, can it?

Thanks in advance 

JB

---

### Post by TeoBigusGeekus on 2011-09-20
Start skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
or
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

---

### Post by madjr on 2011-09-20
> **TeoBigusGeekus said:**
> Start skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
or
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

i wonder why the skype devs keep shipping this bug, isnt there any bug reports about this?... or why the ubuntu devs dont ship the workaround in the .desktop file/shortcut....

---

### Post by TeoBigusGeekus on 2011-09-20
I think the skype devs don't care much about the linux version - look at the percentage of linux users and then look at the percentage of them using skype.
And now that microsoft purchased skype...

---

### Post by madjr on 2011-09-20
> **TeoBigusGeekus said:**
> I think the skype devs don't care much about the linux version - look at the percentage of linux users and then look at the percentage of them using skype.
And now that microsoft purchased skype...

yes, but this fix seems simple enough for ubuntu devs to include it.

maybe ubuntu devs dont care about ubuntu either (Kidding :p)

---

### Post by TeoBigusGeekus on 2011-09-20
> **madjr said:**
> maybe ubuntu devs dont care about ubuntu either (Kidding :p)

That's a thought... If you take unity into account... (not kidding :p)

---

### Post by xx58 on 2011-09-20
:rolleyes: When I share My full screen, then other side see me, but if he shares his screen , then I see only like 1/3 screen. Any advice?

---

### Post by koftis on 2011-10-09
ubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:1869): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:1869): Gtk-WARNING **: Loading IM context type 'ibus' failed





Any suggestions?

i've also tried this

go to terminal and type:
[INDENT] *echo -e "\n# libv4l PPA\ndeb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) `lsb_release -c | awk '{print $2}'` main" | sudo tee -a /etc/apt/sources.list*[/INDENT][INDENT] *sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C3FFB4AA*[/INDENT][INDENT] *sudo apt-get update*[/INDENT][INDENT] *sudo apt-get install libv4l-0*[/INDENT]Now if you want to start Skype just run this in terminal:[INDENT] [I]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

i got an error in the end...

cheese is working ok..


[COLOR=Red]**LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype**[/COLOR]
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2001): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2001): Gtk-WARNING **: Loading IM context type 'ibus' failed
libv4l2: error allocating conversion buffer
libv4l2: error allocating conversion buffer


and it works!

thx ubuntu forum, you guys rock!
[/I][/INDENT]

---

