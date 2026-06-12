---
title: "Inconsistently  High  CPU  Usage"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by faron45 on 2008-10-10
I've done alot of research regarding this & I'm just really tired.This has taken up way too many hours of my time & I'm just not sure what to do.Plus,being [slightly] a beginning comp. user,I'm also [ a little ] scared to try certain things that could possibly end up [really] screwing up my pc.So,I have finally decided to ask for help/opinions.
 Using Google,I found this thread in the forums:"Change size of swap with xubuntu already setup and running".[http://ubuntuforums.org/showthread.php?t=489032]("http://ubuntuforums.org/showthread.php?t=489032") And,larytet's reply sounds very intriguing.
 Essentially,what my problem is,high cpu usage.This is not a constant problem but,it is fairly consistent.And,sometimes,when it happens,it [really] slows things down.As,the internet [Firefox] is what I use mostly,I have found that this is where the problem originates.I'm just wondering what I can do [if anything] to improve performance & stop the pc from [basically] locking up on me when the cpu gets maxed out.I have done the  "check the swappiness value" with "cat /proc/sys/vm/swappiness" in the terminal & found it to be set at 60.So,I'm just wondering if I were to change this if this might solve my problem.Any help/opinions GREATLY [needed and] appreciated.
 And,sorry for the length of the post...just wanted to provide as much info as possible for all of you.
                       Everybody's pal...faron45

---

### Post by jamesrl on 2008-10-10
You could use top (or better htop though you'd have to install it via 'sudo apt-get install htop').  Go to a terminal and type top (or htop if you installed it), and you can see what the top CPU consuming processes are.  

What is your pc cpu speed 'cat /proc/cpuinfo'
and how much memory do you have ('free -m')? 

Have you tried running a lighter web browser, such as epiphany or konqueror?

---

### Post by kerry_s on 2008-10-10
first what are your specs?

try disabling aiglx and composite.
gksudo gedit /etc/X11/xorg.conf:
```
Section "ServerFlags"
Option  "AIGLX" "off"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

```

once you use top to see what's running try to trim the ones you don't need.

i'm using gnome on 450mhz 256mb ram, it's a vaio pcg-f430 laptop from the 90's, so if you got equal or better specs, you just need to find whats causing the problem.

---

### Post by faron45 on 2008-10-10
Sorry for the length of time it took for reply.Hope you're still here.
jamesrl-No,haven't tried any other browsers.

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 8
model name	: Celeron (Coppermine)
stepping	: 3
cpu MHz		: 567.690
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips	: 1136.81
clflush size	: 32

         total       used       free     shared    buffers     cached
Mem:           248        243          5          0          1         34
-/+ buffers/cache:        206         41
Swap:          721        280        441

---

### Post by kerry_s on 2008-10-10
okay, so your running on 256mb ram.

turn on reduced resources for metacity in the configuration editor, swap gedit for leafpad, use abiword instead of open office writer, etc...

---

### Post by faron45 on 2008-10-10
Kerry-can you please explain to me how to go about doing some of this ? Remember,I am [slightly] a begining comp user.Like where is the config edotor ? And,gedit,is that like notepad ? Notepad is what I run.Abi,is what I use.I do not use officewriter
 Thank you.

---

### Post by taqkavar on 2008-10-10
I recommend that you use another distro which has its design centered around older hardware. 

Here is a list of different distros based on their popularity: [http://distrowatch.com/](http://distrowatch.com/)

From top of my head, I have head about Arch Linux, Puppy Linux and Damn Small Linux to be fast. I have personally tried Puppy Linux and would recommend it.

[http://www.puppylinux.org/](http://www.puppylinux.org/) for main site

---

### Post by kerry_s on 2008-10-10
> **faron45 said:**
> Kerry-can you please explain to me how to go about doing some of this ? Remember,I am [slightly] a begining comp user.Like where is the config edotor ? And,gedit,is that like notepad ? Notepad is what I run.Abi,is what I use.I do not use officewriter
 Thank you.

okay, the configuration editor is, applications> system tools> configuration editor
once its open press ctrl+f, type> reduced , select both boxes
it will take you right to it, then just check it.

yes, gedit is the default editor, it's slow. the editor is up to you, what ever works fast enough. :lolflag:

make sure you disable that aiglx & composite, just paste those 2 sections to the bottom of xorg.conf, log out and press ctrl+alt+backspace to restart x.

yeah, if you don't want to use a lighter desktop, just try your best to reduce the resource use, like not using a background.

also, see if your suspend & hibernate work, that will cut boot times out. i use hibernate when i go to bed and suspend through out the day, never need to do a slow full boot.

ubuntu is not really built to be light, using a different distro can help. i use debian etch, it's fast and reliable, also the programs aren't all tied together so it's easy for me to uninstall what ever i don't plan on using. 
i hear arch is also great, but i'm debian all the way. :)

---

### Post by faron45 on 2008-10-10
Kerry-what os are you using ? I am using Xubuntu & there is no config editor under sys tools

---

### Post by faron45 on 2008-10-10
Kerr...Unfortunately,my suspend option does not work [I wish to God,it did].Hibe,does work though.So,generally,I just leave the pc turned on 24/7.
taqkavar-thanks.I have indeed looked at others.Dsl sounds great but,I need a burner,damnit !

---

### Post by kerry_s on 2008-10-10
> **faron45 said:**
> Kerry-what os are you using ? I am using Xubuntu & there is no config editor under sys tools

oh, my bag i thought you was using gnome.
i'm using debian etch gnome:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)


xubuntu is 1 of the slowest xfce4 distro's i've seen, you should try a different xfce4 distro instead, for example debian xfce4:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso)

xfce4 is pretty fast as is, not really much you can tweak on that.

---

### Post by jamesrl on 2008-10-11
you can get to the gnome-configuration editor by typing Alt-F2 and typing in  'gconf-editor' (no quotes).

---

