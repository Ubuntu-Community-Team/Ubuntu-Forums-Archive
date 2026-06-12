---
title: "Trouble activating compiz"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by hannnndy on 2012-01-24
I have some how likely problem too

I have Dell N5110

I want to activate my compiz but it does not  any effects in my graphics, nothing changes
I have googled the problem and results leads me to compiz check
# compiz-check
result:
```
 More than one graphics chip detected -- sorry, the script can not handle that.
 Aborting.
```after that I checked my hardware:
# lspci | grep VGA
result:
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
```I tried to disable the intel one via my bios settings but there is not any option to do so
let me mention the last thing when I tried compiz

the Unity is not there.

and lshw returns the folloing result

# lshw -C video
result:
```
 *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:56 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
```

please help !

---

### Post by hannnndy on 2012-01-24
I have some how likely problem too

I have Dell N5110

I want to activate my compiz but it does not  any effects in my graphics, nothing changes
I have googled the problem and results leads me to compiz check
# compiz-check
result:
     ```
More than one graphics chip detected -- sorry, the script can not handle that.  Aborting. 
```after that I checked my hardware:

# lspci | grep VGA
result:
     ```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 

01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) 
```I tried to disable the intel one via my bios settings but there is not any option to do so
let me mention the last thing when I tried compiz

the Unity is not there.

and lshw returns the folloing result

# lshw -C video
result:
     ```

  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:56 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
 
```please help !

---

### Post by oldos2er on 2012-01-24
Post moved to its own thread.

---

### Post by grahammechanical on 2012-01-24
What do you mean by activate Compiz? Is Ubuntu working on your machine? Have you activated a proprietary driver using Additional Drivers? When you are at the log-in screen do you get an option to log in to Ubuntu and Ubuntu 2D or is it only Ubuntu 2D?

What is more, what version of Ubuntu are you using? 11.10 Oneiric Ocelot?

Regards.

---

### Post by hannnndy on 2012-01-24
@grahammechanical:
I mean I have compiz on my machine but it does not work I have gotten it from repository but my changes there does not save and no visual effect activated on my pc 

about ubuntu: yes I have 11.10 updated today morning

about ubuntu 2D: I do not know what you exactly mean but I do not have any problem logging in my ubuntu when the pc boots a login screen appears at the lft of the screen after auth. i just got log in and every thing works properly except this compiz and graphic extra performance

about additional drivers yes it is mentioned
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=211397&stc=1&d=1327435195[/IMG]

but it seems my problem is something else as i had said before it seems i have two active vga on my pc and this conflicts
intel & nvidia

---

### Post by hannnndy on 2012-01-24
this thread is followed at [http://ubuntuforums.org/showthread.php?p=11637373#post11637373](http://ubuntuforums.org/showthread.php?p=11637373#post11637373)  page

---

### Post by grahammechanical on 2012-01-24
Hi

There are two types of Ubuntu 11.10 desktop environment. One type is simply called Ubuntu at the log-in screen. It uses Compiz as the window manager. So, Compiz is already installed.

Some computer hardware cannot run the special effects so there is a version of Ubuntu for those machines. It is called Ubuntu 2D. That uses something called Metacity as the window manager. There are no special effects with Ubuntu 2D.

When we first install Ubuntu 11.10 it installs Ubuntu 2D. Then after installation we run Additional Drivers and activate the proprietary video driver as you have done. Now, we can log into the Ubuntu desktop (3D with special effects. But are you logging into Ubuntu or Ubuntu 2D?

At the log in-screen you should see a cog icon. You may need to click on your user name to see it. Click on the cog icon and you should see a list. You should see Ubuntu and Ubuntu 2D.

The system always loads the last desktop environment that you used. So, if you have been using Ubuntu 2D that will be the desktop environment that will load. If you click on Ubuntu it will load the 3D desktop environment and will always load Ubuntu 3D until you select Ubuntu 2D.

Ubuntu (3D) and Ubuntu 2D look almost the same. This is intentional. It is only when we use Compiz Configuration Settings Manager to make modifications that we notice a difference.

I think that you are in the Ubuntu 2D desktop and Compiz Configuration Settings Manager (CCSM) will not have any effect in Ubuntu 2D because Metacity city is the window manager.

Once you get into Ubuntu (3D) you will find that CCSM will work. It will make changes. Try clicking on Ubuntu Unity Plugin.

Regards.

---

### Post by overdrank on 2012-01-24
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by hannnndy on 2012-01-24
> **grahammechanical said:**
> Hi

There are two types of Ubuntu 11.10 desktop environment. One type is simply called Ubuntu at the log-in screen. It uses Compiz as the window manager. So, Compiz is already installed.

Some computer hardware cannot run the special effects so there is a version of Ubuntu for those machines. It is called Ubuntu 2D. That uses something called Metacity as the window manager. There are no special effects with Ubuntu 2D.

When we first install Ubuntu 11.10 it installs Ubuntu 2D. Then after installation we run Additional Drivers and activate the proprietary video driver as you have done. Now, we can log into the Ubuntu desktop (3D with special effects. But are you logging into Ubuntu or Ubuntu 2D?

At the log in-screen you should see a cog icon. You may need to click on your user name to see it. Click on the cog icon and you should see a list. You should see Ubuntu and Ubuntu 2D.

The system always loads the last desktop environment that you used. So, if you have been using Ubuntu 2D that will be the desktop environment that will load. If you click on Ubuntu it will load the 3D desktop environment and will always load Ubuntu 3D until you select Ubuntu 2D.

Ubuntu (3D) and Ubuntu 2D look almost the same. This is intentional. It is only when we use Compiz Configuration Settings Manager to make modifications that we notice a difference.

I think that you are in the Ubuntu 2D desktop and Compiz Configuration Settings Manager (CCSM) will not have any effect in Ubuntu 2D because Metacity city is the window manager.

Once you get into Ubuntu (3D) you will find that CCSM will work. It will make changes. Try clicking on Ubuntu Unity Plugin.

Regards.
hi,
I have checked i think you were right metacity is running in my pc I have used the following code

```
if [ $(pgrep -c metacity) -gt 0 ]; then   echo "metacity is running" elif [ $(pgrep -c compiz) -gt 0 ]; then   echo "compiz is running" fi
```
the result is metacity it means that i am using ubuntu 2D how should i activate ubuntu 3D and compiz?

---

### Post by hannnndy on 2012-01-24
@grahammechanical:

hi,
I have checked i think you were right metacity is running in my pc I have used the following code

```

if [ $(pgrep -c metacity) -gt 0 ]; then   
       echo "metacity is running" 
elif [ $(pgrep -c compiz) -gt 0 ]; then   
       echo "compiz is running" 
fi

```

the result is metacity it means that i am using ubuntu 2D how should i activate ubuntu 3D and compiz?

---

### Post by hannnndy on 2012-01-25
I have tried :

```

# compiz --replace

```

out put:
```

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
mohammad@itrc-rafiee:~$ 
(metacity:3731): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3731): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3731): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3731): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

---

### Post by hannnndy on 2012-01-26
To so called admins.

It is to be regretted to ubuntu I have asked you a question about 48 hours ago and still there is no answer.

it seems ubuntu is just a name and no real support is available around.

---

