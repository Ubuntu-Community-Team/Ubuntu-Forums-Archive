---
title: "Fn keys Sony Vaio"
date: 2006-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Zhukov on 2006-11-29
From Thewall83
> 
Zhukov: you should edit your first post and specify that it works only on the FJ series of Sony VAIO's laptop.
On the FE under Feisty it doesn't work.

So, you're warned :D

**Gutsy instructions as well!! Read the post!**

Nice! :) Feisty instructions! ;)

```

sudo rmmod sony_acpi
```

```
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4 libxosd-dev checkinstall
```

```
wget http://download.berlios.de/fsfn/sony_acpi.tar.gz
wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt
wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt
```

**Forgot this deb... tsc tsc**
```

wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn_1.1-1_i386.deb
```

```

sudo dpkg -i fsfn_1.1-1_i386.deb
```

```
tar xvzf sony_acpi.tar.gz
cd sony_acpi
make
```

```

sudo cp sony_acpi.ko /lib/modules/2.6.20-15-generic/kernel/ubuntu/acpi/
```

```

sudo modprobe sony_acpi
```

```

sudo modprobe sony_acpi
```


Sexy! :)

Kudos mainly to [Schwieb]("http://ubuntuforums.org/member.php?u=233410") and also to [UbuntuFS]("http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/") for the sony_acpi link (new version I believe).

So now just continue from where you left with the old tutorial :) (marked with **bold**).




Ok, so this is what I did to get the FN keys to work on my Vaio:

	First let's install some packages:

	```
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4 libxosd-dev checkinstall
```
	
Then:

	```
wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn-1.1-take2.tar.gz
	wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt
	wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt
```

	Extract and compile:

	```
tar zxvf fsfn-1.1-take2.tar.gz
	cd fsfn-1.1
	./configure && make && sudo checkinstall
```

	Don't forget to get back to the initial directory:

	```
cd ..
```

	Then, just to be sure all modules are loaded:

	```
sudo rmmod sony_acpi
	sudo modprobe sony_acpi
	ls /proc/acpi/sony/
```

	And check for:
	
	```
brightness brightness_default fnkey
```

        **Feisty users continue here!**

	Then let's copy the configuration file:
	
	```
sudo cp fsfn.conf.txt /etc/fsfn.conf
```

	Then edit it as desired:

	```
sudo gedit /etc/fsfn.conf
```

	For example, I reduce the size of the fonts and use Headphone as the ALSA device.

	If you need to activate the FJS hack add this to the beggining of the file:

	```
BRT_SETDEFAULT=1
	BRT_HACK_FJS=1
```

	Now let's test it!

	```
sudo fsfn
```

	And:

	```
fsfn -o
```

	Now try the keys. If everything is ok let's just add it to the boot process:

	```
sudo chown root:root fsfn.txt && sudo chmod +x fsfn.txt && sudo mv fsfn.txt /etc/init.d/fsfn
```

	And:

	```
sudo update-rc.d fsfn defaults
```
	

!!! UPDATE FOR FRESH GUTSY INSTALLS :) !!! This comes from our friend [mjpoetic]("http://ubuntuforums.org/member.php?u=122735")

Kudos man! :D You saved my day!

[B]UPDATE:
[/B]I have been messing around with this and I managed to install it now. First I unloaded the other sony modules before installing things (i.e., sonypi and sony_laptop). Then when you are compiling the sony_acpi.ko file use:

Code:

```
make && sudo make install
```

Copy the sony_acpi.ko to it's appropriate place:

Code:

```
sudo cp sony_acpi.ko /lib/modules/`uname -r`/ubuntu/acpi/
```



Ill try to clean this post up soon


	And that's it! Hope it works for you!


	This is basically a summary of this I have NO CREDIT AT ALL!: [http://www.ubuntuforums.org/showthread.php?t=88611](http://www.ubuntuforums.org/showthread.php?t=88611)

	Kudos to the developers and original thread creators! :D

---

### Post by bricksun on 2006-12-02
This is my eagerest thread, thanks for your efforts. Although I followed everything you posted, my sony laptop's fn-keys still don't work. That's what happened:

```
sudo rmmod sony_acpi
ERROR: Module sony_acpi does not exist in /proc/modules
```

```
modprobe sony_acpi
FATAL: Error inserting sony_acpi (/lib/modules/2.6.17-10-generic/kernel/drivers/acpi/sony_acpi.ko): Operation not permitted
```
I have tried more than twice. :) 
Any help is appreciated.

---

### Post by Zhukov on 2006-12-02
The fact that the module isn't there when you want to remove it it's not a problem.
(That's what rmmod does anyway :D )

To solve your issue just do sudo modprobe sony_acpi instead of just modprobe sony_acpi.
That is the cause of the permission problem, you have to run the command as sudo.

Thanks for pointing it out, i've already fixed it.

---

### Post by bricksun on 2006-12-03
Thanks for your reply, it works fine.

---

### Post by mjpoetic on 2006-12-03
Worked here too!!  Nice Howto!! A must have for VAIO users

---

### Post by thewall83 on 2006-12-12
It doesn't work for me!
I've got a UBUNTU 6.10 on a Sony VAIO FE11H.
The kernel is 2.6.17-10-generic.

The howto goes well until I type:
```
ls /proc/acpi/sony/ 
```
This command responds to me:
```
brightness brightness_default
```
So, "fnkey" is not present!
In fact when, after ```
fsfn -o
```, I try to type Fn+F5 or Fn+F6 it doesn't happen anything!
I think that I should add some command near the lines F5 and F6 in the file "/etc/fsfn.conf", but Idon't know what kind of command will work!

The only command that work (by terminal) are:
```
smartdimmer -i (increase brightness)
smartdimmer -d (decrease      "    )
```
but in my case they don't work near lines F5 and F6.

How could I assign these commands to my Fn keys?

---

### Post by Zhukov on 2006-12-12
Ok, what's the output when you type

sudo modprobe sony_acpi

---

### Post by thewall83 on 2006-12-12
> **Zhukov said:**
> Ok, what's the output when you type

sudo modprobe sony_acpi

No output, it seems to apply the command and return the console:-k.

---

### Post by Zhukov on 2006-12-13
Are you sure you did everything ok?

If so, please go to berliOS and submit a bug within the fsfn project.
I had to do the same in order to get it to work with my laptop. The devs are really nice so you should get a reply, and hopefully a solution, in no time.

Regards!

---

### Post by thewall83 on 2006-12-13
> **Zhukov said:**
> Are you sure you did everything ok?

If so, please go to berliOS and submit a bug within the fsfn project.
I had to do the same in order to get it to work with my laptop. The devs are really nice so you should get a reply, and hopefully a solution, in no time.

Regards!

I did eerything ok, and I think that the software "fsfn" is only for FS series...Mine is a FE Vaio!
However, I'll try to contact the developers.Thanks;)

---

### Post by Zhukov on 2006-12-13
:) That was exactly why I told you to write them.

Mine is FJ, that's why I have the FJ_HACK ;)

Regards!

---

### Post by larytet on 2007-01-25
To thewall83:

try to check
```

cat /var/log/acpid

```
Is there any exceptions ?
Try to click Fn keys and check /var/log/acpid again

---

### Post by thewall83 on 2007-01-25
> **larytet said:**
> To thewall83:

try to check
```

cat /var/log/acpid

```
Is there any exceptions ?
Try to click Fn keys and check /var/log/acpid again

Any exceptions:( 
It's like I didin't click any key.
It's a known bug and (at the moment) it's unresolved because it needs the hard patching of the module sony_acpi.
[http://www.iwebyoumind.com/index.php?codice=1147477228&SID=guest](http://www.iwebyoumind.com/index.php?codice=1147477228&SID=guest)
Bye bye!

---

### Post by larytet on 2007-01-26
Looks like screendimmer works in 6.10 out of the box for VGN-S460
```

 sudo smartdimmer -i
 sudo smartdimmer -d

```

I slightly modified 
 /etc/acpi/sonybright.sh

```

#!/bin/bash

BRIGHTNESS=$(cat /proc/acpi/sony/brightness)


if [ "$BRIGHTNESS" -gt 8 ]; then
	BRIGHTNESS=8
fi

if [ "x$1" = "xdown" ]; then
   if [ "$BRIGHTNESS" -gt 1 ]; then
      BRIGHTNESS=$(( $BRIGHTNESS - 1 ))
      echo $BRIGHTNESS > /proc/acpi/sony/brightness
      echo "BRIGHTNESS=$BRIGHTNESS"
      [ -x /usr/bin/smartdimmer ] && smartdimmer -d 2>/dev/null
      [ -x /usr/bin/smartdimmer ] && smartdimmer -d 2>/dev/null
   fi

elif [ "x$1" = "xup" ]; then
   if [ "$BRIGHTNESS" -lt 8 ]; then
      BRIGHTNESS=$(( $BRIGHTNESS + 1 ))
      echo $BRIGHTNESS > /proc/acpi/sony/brightness
      echo "BRIGHTNESS=$BRIGHTNESS"
      [ -x /usr/bin/smartdimmer ] && smartdimmer -i 2>/dev/null
      [ -x /usr/bin/smartdimmer ] && smartdimmer -i 2>/dev/null
   fi

else
   echo >&2 Unknown argument $1
fi


```


make sure that you start from some reasonable number
for example:
 sudo echo 8 > /proc/acpi/sony/brightness
and call 
sudo smartdimmer -i
 
a couple of times


Interesting exercise with ACPI (this one throttles power for CPU0)
```

su
cd /proc/acpi/processor/CPU0/
echo 7:7 > limit

```

---

### Post by SanSe on 2007-02-25
Hi, 

I have Sony Vaio VGN FE28B. I tried to do the same and still not working.

When I do ```
ls /proc/acpi/sony/
``` I just see ```
brightness brightness_default
```

Im not really sure where is the problem, but my laptop is unable to use FN keys at the moment.

This is [my lshw]("http://ultra.eupmt.es/~santorja/lshw_vaio") FYI 


Thanks

---

### Post by Zhukov on 2007-02-25
Was the module successfully loaded?

---

### Post by SanSe on 2007-02-25
Yes, i haven't problems with modprobe. No messages are showed when i type```
# modprobe sony_acpi
```

---

### Post by thewall83 on 2007-02-25
> **SanSe said:**
> Yes, i haven't problems with modprobe. No messages are showed when i type```
# modprobe sony_acpi
```

Someone contacted an ex sony pi mantainer and this was the reply for FE keys on sony vaio:
```

Since the SNC ACPI extension isn't supported yet, neither webcam nor Fn keys can work. At this time, the linux kernel sony support seems to be Unmaintained.
```

:(

---

### Post by Zhukov on 2007-02-26
:S No solution then.

---

### Post by Migs on 2007-02-26
> **Zhukov said:**
> :S No solution then.

I have maybe some good news! Check out the changelog for latest kernel 2.6.21-rc1

[http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.21-rc1](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.21-rc1)

It realy sounds cool, gues we just have to wait :KS 

> 
   sony-laptop: add to MAINTAINERS
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit ab5bd20696485a3f8c2f27058ace1cc1d6b580b3
Author: Mattia Dongili <malattia@linux.it>
Date:   Thu Feb 8 20:16:41 2007 +0100

    sony-laptop: Update docs
    
    Update documentation to be consistent with current implementation
    (backlight subsys and platform_device).
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit a02d1c1d2aa8ad4b2ed8da25e234c8962973f1b8
Author: Len Brown <len.brown@intel.com>
Date:   Wed Feb 7 15:34:02 2007 -0500

    sony-laptop: Lindent
    
    Signed-off-by: Len Brown <len.brown@intel.com>

commit d78865cdb096781382074943c1b7781696b178a6
Author: Mattia Dongili <malattia@linux.it>
Date:   Wed Feb 7 20:01:56 2007 +0100

    sony-laptop: Group functions and structures to better draw subsytems usage
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 287ddfd522097257dadf37deb21969ad4dbc8148
Author: Mattia Dongili <malattia@linux.it>
Date:   Wed Feb 7 20:01:55 2007 +0100

    sony-laptop: Small update to the Kconfig help to make people believe this driver is useful.
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit ed3aa4b729478978f117269b5266a2d18948912c
Author: Mattia Dongili <malattia@linux.it>
Date:   Wed Feb 7 20:01:54 2007 +0100

    sony-laptop: Remove /proc/acpi/sony interface and implement platform_device.
    
    Rework method names list to allow an easier management of multiple
    values.
    Add myself as author/maintainer and bump the version number.
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 91fbc1d311c1b8b71203b96f1a0629da7360eb4c
Author: Mattia Dongili <malattia@linux.it>
Date:   Wed Feb 7 20:01:53 2007 +0100

    sony-laptop: create from sony_acpi
    
    Move drivers/acpi/sony_acpi.c to drivers/misc/sony-laptop.c with all the
    necessary configuration.
    The SONY_LAPTOP config option substitutes the old ACPI_SONY and is 'default n'
    now.
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 7df03b82ed081777d2393ff8a5fb9d4a3a560f26
Author: Mattia Dongili <malattia@linux.it>
Date:   Sat Jan 13 23:04:41 2007 +0100

    sony_acpi: Fix sony_acpi backlight registration and unregistration
    
    Initialize the current brightness if the driver registration
    was successful and unregister the driver in the error exit path.
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 57ede701af3bc0c153070133e7831332ffa1d761
Author: Mattia Dongili <malattia@linux.it>
Date:   Sat Jan 13 23:04:40 2007 +0100

    sony_acpi: Allow multiple sony_acpi_values for the same .name
    
    The acpi handles are kept _only_ if both the requested .acpiget and .acpiset
    are available in the DSDT.
    Currently only the SCDP/CDPW dualism is known.
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 4465857d5f99079bae00621626adf74ed8256296
Author: Mattia Dongili <malattia@linux.it>
Date:   Sat Jan 13 23:04:39 2007 +0100

    sony_acpi: Add lanpower and audiopower controls
    
    audiopower works well on my SZ72B so it's not marked has "debug" while lanpower
    has at least one report of not resuming power happily so morked as "debug"
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 05e2d8274ef4504db9941f7c515f340ab6c0b2e1
Author: Mattia Dongili <malattia@linux.it>
Date:   Sat Jan 13 23:04:38 2007 +0100

    sony_acpi: Allow easier debugging for the unknown SNC methods.
    
    Allow the existence of a setter method without a getter and viceversa,
    additionaly set /proc file permissions reflecting it.
    Fix also the error exit path.
    
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit c561162f10b9f35c9aa5c25eb8dbeb446f0c5201
Author: Stelian Pop <stelian@popies.net>
Date:   Sat Jan 13 23:04:37 2007 +0100

    sony_acpi: Add acpi_bus_generate event
    
    Added acpi_bus_generate event for forwarding Fn-keys pressed to acpi subsystem,
    and made correspondent necessary changes for this to work.
    
    Signed-off-by: Nilton Volpato <nilton.volpato@gmail.com>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 82c47731f77e7615f5a952c662d873b55e71f3b9
Author: Andrew Morton <akpm@osdl.org>
Date:   Sat Jan 13 23:04:36 2007 +0100

    sony_acpi: Video sysfs support take 2
    
    add dev argument for backlight_device_register
    
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 243e8b191df4e9c11e62ea11fa298351997e98c3
Author: Alessandro Guido <alessandro.guido@gmail.com>
Date:   Sat Jan 13 23:04:35 2007 +0100

    sony_acpi: Add backlight support to the sony_acpi v2
    
    Enable the sony_acpi driver to use the backlight subsysyem for adjusting
    the monitor brightness.  Old way of changing the brightness will be still
    available for compatibility with existing tools.
    
    Signed-off-by: Alessandro Guido <alessandro.guido@gmail.com>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 50f62afb114ffcf052cf07d4b49b2d148b749955
Author: Alessandro Guido <alessandro.guido@gmail.com>
Date:   Sat Jan 13 23:04:34 2007 +0100

    sony_acpi: Add backlight support to the sony_acpi
    
    Make the sony_acpi use the backlight subsystem to adjust brightness value
    instead of using the /proc/sony/brightness file.  (Other settings will
    still have a /proc/sony/...  entry)
    
    Signed-off-by: Alessandro Guido <alessandro.guido@gmail.com>
    Cc: Stelian Pop <stelian@popies.net>
    Cc: Richard Purdie <rpurdie@rpsys.net>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit fac3506100c19391bc5474084dd838f0fb87bf26
Author: Andrew Morton <akpm@osdl.org>
Date:   Sat Jan 13 23:04:33 2007 +0100

    sony_acpi: Fix sony_acpi_resume call
    
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 3f4f461fa816815b9338047a29cf2521f23f1783
Author: Andrew Morton <akpm@osdl.org>
Date:   Sat Jan 13 23:04:32 2007 +0100

    sony_acpi: Avoid dimness on resume.
    
    Doesn't work.
    
    Cc: Stelian Pop <stelian@popies.net>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>

commit 7f09c432bed80cecfba634933ddc06735e64da00
Author: Stelian Pop <stelian@popies.net>
Date:   Sat Jan 13 23:04:31 2007 +0100

    sony_acpi: SNC device support for Sony Vaios
    
    From: Bjorn Helgaas <bjorn.helgaas@hp.com>
    
      Even though the devices claimed by sony_acpi.c can not be hot-plugged, the
      driver registration infrastructure allows the .add() and .remove() methods
      to be called at any time while the driver is registered.  So remove __init
      and __exit from them.
    
    From: Matthew Garrett <mjg59@srcf.ucam.org>
    
    [UBUNTU:acpi/sony] Add FN hotkey support
    Source URL of Patch:
    [http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commitdiff;h=7a9b49cba4919e8506604629db03add8e0b85767](http://www.kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper.git;a=commitdiff;h=7a9b49cba4919e8506604629db03add8e0b85767)
    
    Signed-off-by: Ben Collins <bcollins@ubuntu.com>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Mattia Dongili <malattia@linux.it>
    Signed-off-by: Len Brown <len.brown@intel.com>


---

### Post by SanSe on 2007-02-26
Oh! That's cool! Thanks Migs :P\\:D/

---

### Post by Zhukov on 2007-02-26
Very nice in deed :)

---

### Post by newen on 2007-02-27
please, file a bug against this so that a patch is backported (I don't know if this is possible yet, though)

---

### Post by Migs on 2007-02-27
I am sorry to disappoint you but I will personally not file a bug. The reasons for it are very simple first of all: These patches are not yet declared stable and therefore not for daily usage. Looking at the kernel number 2.6.21-rc1 you could have known that it is a release candidate.

Second; I think developers should not waste their precious time on back porting these patches. There are far more important things that should have more priority. It's just like waiting for your birthday, just count the nights you have to sleep till it's there :) 

I know it’s frustrating that newer breed of Sony laptop’s don’t support all features in Linux. I’ve bought especially a Sony laptop because I have read that the support was okay using the modules SONYPI and SONY_ACPI, not knowing that those modules didn’t work on my VGN-FE11M :( 

From what I know all new laptops from Sony have this problem. For the following European Sony laptops I am 100% sure:
VGN-FE11x (where x is the specific type H, M or S)
VGN-FE21x 
VGN-FE31x
VGN-FE41x

---

### Post by newen on 2007-02-28
I understand your point.

I did believe the same. I thought Vaio support was ok, but it isn't for newer models. I own a FE31M, which is gorgeous, but acpi support really sucks. gnome-power-manager isn't even able to change the brightness.

By the way, I though gnome-power-manager had frequecy scaling support (so that we don't have to use the CPUfreq applet with SUID) as frecuency scaling is supported by HAL. Does Anyone know if this is working?

---

### Post by Zhukov on 2007-02-28
Just my opinion:
Vaios are sold like chocolate cakes. They look nice, the overall specs are quite nice, sturdy build and not (very) expensive.
In less than one year after I bought mine all the hardware was supported. Please, be patient, as you can see development is under way :)

Best Regards.

---

### Post by ARGONIQ on 2007-04-24
> **Zhukov said:**
> Ok, so this is what I did to get the FN keys to work on my Vaio:

	First let's install some packages:

	```
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4 libxosd-dev checkinstall
```
	
[INDENT][/INDENT]Then:

	```
wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn-1.1-take2.tar.gz
	wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt
	wget http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt
```

	Extract and compile:

	```
tar zxvf fsfn-1.1-take2.tar.gz
	cd fsfn-1.1
	./configure && make && sudo checkinstall
```

	Don't forget to get back to the initial directory:

	```
cd ..
```

	Then, just to be sure all modules are loaded:

	```
sudo rmmod sony_acpi
	sudo modprobe sony_acpi
	ls /proc/acpi/sony/
```

	And check for:
	
	```
brightness brightness_default fnkey
```

	Then let's copy the configuration file:
	
	```
sudo cp fsfn.conf.txt /etc/fsfn.conf
```

	Then edit it as desired:

	```
sudo gedit /etc/fsfn.conf
```

	For example, I reduce the size of the fonts and use Headphone as the ALSA device.

	If you need to activate the FJS hack add this to the beggining of the file:

	```
BRT_SETDEFAULT=1
	BRT_HACK_FJS=1
```

	Now let's test it!

	```
sudo fsfn
```

	And:

	```
fsfn -o
```

	Now try the keys. If everything is ok let's just add it to the boot process:

	```
sudo chown root:root fsfn.txt && sudo chmod +x fsfn.txt && sudo mv fsfn.txt /etc/init.d/fsfn
```

	And:

	```
sudo update-rc.d fsfn defaults
```
	
	And that's it! Hope it works for you!


	This is basically a summary of this I have NO CREDIT AT ALL!: [http://www.ubuntuforums.org/showthread.php?t=88611](http://www.ubuntuforums.org/showthread.php?t=88611)

	Kudos to the developers and original thread creators! :D

This worked for me in 6.10 release, but NOT in Feisy. What can i do?
Thx!!!!!

---

### Post by Zhukov on 2007-04-24
Well, I was considering migrating to Feisty somewhere tonight/tomorrow, so what I can do is (finally) make some scripts or debs for this under Feisty and post them here.

---

### Post by Zhukov on 2007-04-30
Ok guys, just to tell you that I´ve migrated today and I´ll start looking into the issue as soon as possible.

Regards!

---

### Post by Zhukov on 2007-05-02
New: A bug was submitted at BerliOS and I was informed that as soon as 2.6.21 gets out we wont need to do anything :)

But ok, I need brightness control under Feisty, so I did this ugly script:

Usage: **brightness [number]**

Just copy it to /usr/bin: **sudo cp brightness.sh /usr/bin/brightness**

Make it executable: **sudo chmod +x /usr/bin/brightness**

And then, voilá: **brightness 1**

---

### Post by mjpoetic on 2007-05-02
Man thanks for this hack....I have needed it for some time but couldn't figure out what to do.  Any idea on when 2.6.21 will be coming out?

---

### Post by Zhukov on 2007-05-02
No problem :)

I have no idea at all, but there was some talk going on last week about backporting it to feisty.

---

### Post by ARGONIQ on 2007-05-03
This hack works.

A few day ago I try and try and try several methods that I found in google (this included)  One morning I try FN key+F5 and the keys worked!!!! And the volume keys too. A Miracle!!!! I dont know what I did. I was very happy and my Lap works fine many days  

Sad Story: I tried to install  the fingerprint usplash And my new ubuntu (and fn keys) its gone...(Kernel Panic not syncing. No init found) I kill my system!

I'll try again, I'll Follow my own steps to recovery fn keys. If I can get my keys back, I try to resume step by step. 
But the fn keys works in festy. I swear.

pd Zhukov: Your hack works but is very ugly hehe... Im just kidding.

---

### Post by Zhukov on 2007-05-03
:P I know its ugly :D lol

Well, then I belive we can help each other. The issue is only loading the sony_acpi module, that should enable the fnkeys, so, when I do a **ls /proc/acpi/sony/** I would get **brightness  brightness_default fnkeys**, instead of just **brightness brightness_default**.

Maybe you found some "patched" code somewhere or did some thing regarding this module that enabled its loading.

Try to figure what you did :D

---

### Post by ARGONIQ on 2007-05-06
Hey!  I did it again. My FN key is  working again in feisty!!!


I worked in my lap for several hours, Im very tired now but at least it works
, I take notes for every step that I did, I install and uninstall fsfn, install vaio-stat, unninstall FN keys install again, and then fnkey appears in proc.
The keys works

A snapshot of fnkey in action: 

[[IMG]http://img245.imageshack.us/img245/4773/fnkeyhe7.th.png[/IMG]](http://img245.imageshack.us/my.php?image=fnkeyhe7.png)

I think i did an "homer".

If I can do it again from a fresh ubuntu, i try to write a mini-guide

---

### Post by ARGONIQ on 2007-05-08
Hey!

This is the Key for FN keys in Feisty. I try 3 times and it works on each one.

[http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/](http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/)

Regards!

---

### Post by schwieb on 2007-05-08
I echo the above link.  Trip and I got it working under feisty by manually copying the module.

Schwieb

---

### Post by Tripmonkey_uk on 2007-05-08
> **ARGONIQ said:**
> Hey!

This is the Key for FN keys in Feisty. I try 3 times and it works on each one.

[http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/](http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/)

Regards!

Glad to know you found it useful Argoniq. It must work ok if you've managed to do it 3 times lol.

Cheers once again for the fix schwieb. I've had that tutorial **almost** finished for over a month & it's a relief to be able to finally get it finished :D

---

### Post by mjpoetic on 2007-05-08
Man I have been trying to get this most recent tutorial to work for me with no success.  I get as far as the ```
**ls** **/proc/acpi/sony**
``` and no **fnkey** appears alongside [B]```
brightness  brightness_default
```

[COLOR=Red]EDIT:
Okay it worked out after all.  I had to undo some of the things I tried a while ago (e.g., had to remove the [/COLOR][/B][COLOR=Red][B]sony_acpi.ko that I had before the tutorial).
[/B][/COLOR]

---

### Post by xenoph0be on 2007-05-09
> **newen said:**
> I understand your point.

I did believe the same. I thought Vaio support was ok, but it isn't for newer models. I own a FE31M, which is gorgeous, but acpi support really sucks. gnome-power-manager isn't even able to change the brightness.

By the way, I though gnome-power-manager had frequecy scaling support (so that we don't have to use the CPUfreq applet with SUID) as frecuency scaling is supported by HAL. Does Anyone know if this is working?

This may be off topic or a late reply but here goes as a first post... 

To fix gnome-power-manager to change brightness you need to change the hal scripts:
hal-system-lcd-get-brightness
hal-system-lcd-set-brightness

They were located in the following locations on my fresh feisty install:
/usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux
/usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux
/usr/lib/hal/scripts/hal-system-lcd-get-brightness
/usr/lib/hal/scripts/hal-system-lcd-set-brightness

You can use 'locate' in a console to find where the files are located on your machine.

Change:
#!/bin/sh

to:
#!/bin/bash

Jacob

---

### Post by thewall83 on 2007-05-09
> **xenoph0be said:**
> This may be off topic or a late reply but here goes as a first post... 

To fix gnome-power-manager to change brightness you need to change the hal scripts:
hal-system-lcd-get-brightness
hal-system-lcd-set-brightness

They were located in the following locations on my fresh feisty install:
/usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux
/usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux
/usr/lib/hal/scripts/hal-system-lcd-get-brightness
/usr/lib/hal/scripts/hal-system-lcd-set-brightness

You can use 'locate' in a console to find where the files are located on your machine.

Change:
#!/bin/sh

to:
#!/bin/bash

Jacob

But.....do you have a Vaio FE serie and is this working?:confused:

---

### Post by xenoph0be on 2007-05-09
> **thewall83 said:**
> But.....do you have a Vaio FE serie and is this working?:confused:

Yes, I have a VGN-FE660G and it works properly.  It is a known and documented problem.  I had the same problem with Edgy and that was the fix prescribed for it as well.

---

### Post by thewall83 on 2007-05-12
Good work!
Another question: does your laptop have got Fn keys?
Do they work or not?

Thanks!

---

### Post by xenoph0be on 2007-05-12
> **thewall83 said:**
> Good work!
Another question: does your laptop have got Fn keys?
Do they work or not?

Thanks!

Yes, it has FN keys, but I have yet to get them to work.

---

### Post by Zhukov on 2007-05-15
I've edited the first post and added some instructions for Feisty :D

Nice :D

---

### Post by thewall83 on 2007-05-15
> **xenoph0be said:**
> Yes, it has FN keys, but I have yet to get them to work.
Ok, thank you for the tip!

Zhukov: you should edit your first post and specify that it works only on the FJ series of Sony VAIO's laptop.
On the FE under Feisty it doesn't work. Thank you.

---

### Post by Bluecircle on 2007-05-15
Anything for the TX series? The front volume buttons don't work.

---

### Post by Zhukov on 2007-05-16
Done Thewall83.

Anyway, did any of you guys managed to configure something with the S buttons?

---

### Post by xenoph0be on 2007-05-16
One other nifty/off topic thing I found in the panel applets...  Right click any gnome panel and select 'Add to Panel...'  then click/drag the brightness control from the window to gnome panel and you have yourself an easy way to change the screen brightness... I assume that this would require that you have already fixed the hal scripts in my previous post.

Jacob

---

### Post by Zhukov on 2007-05-17
Yes it requires :D

Anyway, just got this:

(From mk2lehe)

> 
Hi,

I saw your thread "Fn keys Sony Vaio", and this thread was my primary source for getting it to work on Feisty, 2.6.21.1 (customized) on a FS395VP machine.

I'm not able to post in forum, (don't know why - forum complains on activation blah blah) maybe you're interested in sharing the info in the thread. Let me also notify you I am not a very skilled programmer. I don't even know how to write patches.

In 2.6.21.1, fsfn is already included. No more use for patched sony_acpi.

what used to be /proc/acpi/sony/brightness is now found in /sys/class/backlight/sony/brightness
/proc/acpi/sony/fnkey replaced with /sys/devices/platform/sony-laptop/fnkey
/proc/acpi/sony/brightness_default replaced with /sys/devices/platform/sony-laptop/brightness_default
( at least for me, in my system. )
These changes needs to be done in generics.h and in acpihandler.c .

 I also fixed a bug in osd.c and fsfn.c regarding my laptop, which uses brightness levels 0 to 7 (and not 1-8). Not sure how to make a generic solution.

---

### Post by Max Luebbe on 2007-05-23
Worked perfect for my VGN-FS760.

I've put together a convenience script for the feisty version and made it available for download on my blog - [http://intentionallyobsolete.com/?p=23]("http://intentionallyobsolete.com/?p=23").

I want to put some development effort into a better solution - if you use this and it works, let me know so I can assemble a list of models this is known to work on!

Next steps are to make a real Ubuntu package in place of the script, and see if I can get it added to the repos. I'm also working on getting the 'S' buttons working.

Let me know if this makes anyone's life easier!

---

### Post by Zhukov on 2007-05-23
Nice! :D

I haven't checked the script (no real need for it now), but I'm volunteering to help :D

Anyway, I believe the sony_acpi will be available with the next kernel, right?

---

### Post by Migs on 2007-05-23
Does this script also provide a fix for the newer Sony Vaio models? We all know that the older models are supported somehow with the SonyPI module. All models released in january 2006 have a different FN key controller wich the SonyPI module doesn't recognize. 
Also the ACPI code isn't compatible with the linux kernel. My FE11M hasn't any ACPI support even with the Sony_ACPI module wich meanse no battery support, no FN key support, no S key support. I hope someone could solve this problem otherwise Vaio laptop have to be blacklisted for use with linux.

---

### Post by Max Luebbe on 2007-05-25
Doesn't sound like it does.

All my script does at this point is automate the directions found in this thread and eliminate the need for typing.

If SonyPI isn't working and you don't have acpi support, then I think you're out of luck until the kernel hackers get around to making some new modules or fixing the old one.

---

### Post by Depressed Man on 2007-05-30
> **Max Luebbe said:**
> Worked perfect for my VGN-FS760.

I've put together a convenience script for the feisty version and made it available for download on my blog - [http://intentionallyobsolete.com/?p=23]("http://intentionallyobsolete.com/?p=23").

I want to put some development effort into a better solution - if you use this and it works, let me know so I can assemble a list of models this is known to work on!

Next steps are to make a real Ubuntu package in place of the script, and see if I can get it added to the repos. I'm also working on getting the 'S' buttons working.

Let me know if this makes anyone's life easier!

Much thanks! I'm still a newbie at Linux so I couldn't figure out how to get bash to run the script so I just copied and pasted all the commands in... :) but now my FN key works! Well sortof..when I hold it I can get the p to do a * and some of the other symbols like +, -, etc.. though the brightness controls, and the numbers don't work. 

Though I think the brightness problem is a seperate thing since I can't seem to control the screen brightness at all with Gnome even given the slider. And hibernate, sleep doesn't work >.< But one less thing to work one! So thanks alot everyone! And thank you for the script! I can't wait till you get the "S" buttons working. :)

---

### Post by qstraza on 2007-06-01
hey... i have vaio vgn-c2z

anyways im using feisty fawn kubuntu 64bit and here is where my problem occurres.

I need function key to work on 64 bit. 

Any help on that?

thatnks in advance! ;>

glhf

---

### Post by IntuitiveNipple on 2007-06-06
As I've posted in other Vaio threads, there's an effort underway to finally solve all the Fn-key and other issues on Vaio portables via the sony-laptop kernel module.

If you have a Vaio portable check out the [Calling all Vaio Owners]("http://ubuntuforums.org/showthread.php?t=465491") thread and help us gather more data.

---

### Post by unsichtbarre on 2007-09-08
> Then edit it as desired:

sudo gedit /etc/fsfn.conf

I'm kinda new at this, but what do we put in fsfn.conf at the appropriate Fn lines to make brightness and volume work?

-John

---

### Post by mjpoetic on 2007-10-10
Anybody got this working on Gutsy Beta yet?

---

### Post by Miette-chan on 2007-10-18
I ran the script that Max Luebbe provided and the fn keys on my vgn-fs series vaio worked perfectly. However, once I updated to Gutsy these stoped working and running the script also ceased to work. I also get this:


```
cp: target `/lib/modules/2.6.22-14-generic/kernel/ubuntu/acpi/' is not a directory: No such file or directory
```

---

### Post by jtslau on 2007-10-20
I have been following this thread every since dapper/edgy, and is one of the most helpful thread I have visited.

Guess its time for me to contribute, if I can:

Alright, I got this to work for Ubuntu Gutsy Gibbon.
If the thread owner could test it out and add it to the top message.

The instructions below are almost identical to the parent message with all the instructions, however I will highlight the difference in bold.

And yes, this is my first post to Ubuntu Forums, so I don't know how to use the quotes that are usually used to wrap codes, but anyways, 

Here goes:

Step 1:
sudo rmmod sony_acpi

Step 2:
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4 libxosd-dev checkinstall


Step 3
wget [http://download.berlios.de/fsfn/sony_acpi.tar.gz](http://download.berlios.de/fsfn/sony_acpi.tar.gz)

Step 4
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt](http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt)

Step 5
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt](http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt)

Step 6
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn_1.1-1_i386.deb](http://student.dei.uc.pt/~jpoa/fsfn/fsfn_1.1-1_i386.deb)

Step 7
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn-1.1-take2.tar.gz](http://student.dei.uc.pt/~jpoa/fsfn/fsfn-1.1-take2.tar.gz)

Step 8
sudo dpkg -i fsfn_1.1-1_i386.deb

Step 9
tar xvzf sony_acpi.tar.gz

Step 10
cd sony_acpi

Step 11
make

[B]Step 12
sudo cp sony_acpi.ko /lib/modules/2.6.22-14-generic/ubuntu/acpi/[/B]

[B]Step 13 (Depreciated but I still did it anyways, don't think this is necessary)
sudo mkdir /lib/modules/2.6.22-14-generic/kernel/ubuntu/
sudo mkdir /lib/modules/2.6.22-14-generic/kernel/ubuntu/acpi/
sudo cp sony_acpi.ko /lib/modules/2.6.22-14-generic/kernel/ubuntu/acpi/[/B]

Step 14
cd ..

Step 15
sudo modprobe sony_acpi

Step 16
tar zxvf fsfn-1.1-take2.tar.gz

Step 16
cd fsfn-1.1

Step 17
./configure && make && sudo checkinstall

Step 18
cd ..

Step 19
sudo rmmod sony_acpi

Step 20
sudo modprobe sony_acpi

Step 21
ls /proc/acpi/sony/

Step 22
Check for this output from the last command
brightness brightness_default fnkey

if this shows, good, continue

Step 23
sudo cp fsfn.conf.txt /etc/fsfn.conf

Step 24
sudo fsfn

Alright done.  Now test the FN-key and see if they work.  I KNOW FOR SURE they work for me, Gutsy Gibbon.

Regards
Jerome

---

### Post by mjpoetic on 2007-10-20
> **jtslau said:**
> 
 Alright done.  Now test the FN-key and see if they work.  I KNOW FOR SURE they work for me, Gutsy Gibbon.

 Regards
 Jerome

Yea this worked for me too. Thanks! By the way, you don't need all the steps (like you said). AFAIK, you don't need Step 13 at all (I skipped it and it worked). Also, you don't need to download the "fsfn-1.1-take2.tar.gz" file at all as the fsfn deb package you install before that takes care of it. I would do a modified version of your HOWTO but I don't have anymore time with this right now.
 
THANKS again though...I couldn't figure out where the acpi module directory changed to but it was so simple!

p.s.
The code quoting things is easy...if you know anything about HTML it's similar....just wrap your text like this:

[IMG]http://i42.photobucket.com/albums/e320/mjpoetic/Screenshots/screenshot1.png[/IMG]
```
and it will look like this
```

---

### Post by Depressed Man on 2007-10-20
Interesting, I'll have to try it on my FE series sometime..

---

### Post by jtslau on 2007-10-20
Oh btw, the instructions I give was only tested on my FS, so I am not sure if this will work for other VAIO models, namely FJ/FE.

And mjpoetic, thanks for your comment.  I knew out of the hat it is related to HTML tagging, but was too lazy to preview and test.

I will end this with a note.  Whenever there is a Ubuntu version change or a kernel change, say from 2.6.15-20 to 2.6.22-14, you must move the sony_acpi.ko file to the new acpi directory.

Say for kernel 2.6.15-20 to 2.6.22-14 (using the acpi location for Gutsy, not for Feisty)

```

sudo cp /lib/modules/2.6.15-20-generic/ubuntu/acpi/sony_acpi.ko /lib/modules/2.6.22-14-generic/ubuntu/acpi/

```

and of course modprobe it as well.

---

### Post by mjpoetic on 2007-10-20
Actually I wrote my self a quick shell script that will allow you to just run the command "**fsfn-kernel-update**" to quickly get fsfn going on any kernel.  It wasn't working anymore until I read your post realizing the difference in the /lib/modules/...location (i.e., it used to be in /lib/modules/`uname -r`**/kernel/ubuntu/acpi/** but as of Gutsy now is just /lib/modules/`uname -r`**/ubuntu/acpi/**)

---

### Post by AlfyBoy on 2007-10-22
> **jtslau said:**
> 


Alright done.  Now test the FN-key and see if they work.  I KNOW FOR SURE they work for me, Gutsy Gibbon.

Regards
Jerome


Thanks Jerome, this should be on a HOW TO

THIS Works Great!!!!!!

---

### Post by Hoosier205 on 2007-10-22
Hmm...I wonder if this would work for me. I have a Sony Vaio PCG-K35 with Fn keys for volume (mute, up, down) and brightness. I guess I could give it a try.

---

### Post by Miette-chan on 2007-10-25
I have run into a problem when I try: ```
wget http://student.dei.uc.pt/~jpoa/fsfn/...1-take2.tar.gz
``` I end uo with a 404 error. I also get other errors relating to the lack of this package if I try to continue with the steps

---

### Post by rwind on 2007-10-26
When I get to "ls /proc/acpi/sony/" nothing shows up... everything else worked fine. 

I downloaded the "fsfn-1.1-take2.tar.gz" from "http://ubuntuforums.org/attachment.php?attachmentid=4704&d=1135058274"

---

### Post by mjpoetic on 2007-10-26
Funny thing about this is that I was able to get it to work without fail the first time I tried it.  I decided to do a clean install of the official Gutsy release and I haven't been able to get it to work anymore.  I get as far as modprobe-ing the sony_acpi module and it actually segfaults.  Weird.  After doing it, I can't even remove the module and it claims that it is still in use (that's scary because it reminds me of Windows).

---

### Post by rwind on 2007-10-26
> **rwind said:**
> When I get to "ls /proc/acpi/sony/" nothing shows up... everything else worked fine. 

I downloaded the "fsfn-1.1-take2.tar.gz" from "http://ubuntuforums.org/attachment.php?attachmentid=4704&d=1135058274"


EDIT:

Ok, so I rebooted and I tried ```
ls /proc/acpi/sony/
``` and the three showed up ```
brightness  brightness_default  fnkey
```

Now I do  ```
sudo cp fsfn.conf.txt /etc/fsfn.conf
``` and get the error:

```
cp: cannot stat `fsfn.conf.txt': No such file or directory
```

BUT I can use Fn + F5 and F6 to turn the brightness up and down. There isn't any graphical display for it though, is there a way to get it shown?

---

### Post by Depressed Man on 2007-10-27
"http://ubuntuforums.org/attachment.php?attachment id=4704&d=1135058274"

The link doesn't work for me, I'm trying to grab the file myself.

---

### Post by lordvanx on 2007-10-27
> **jtslau said:**
> I have been following this thread every since dapper/edgy, and is one of the most helpful thread I have visited.

Guess its time for me to contribute, if I can:

Alright, I got this to work for Ubuntu Gutsy Gibbon.
If the thread owner could test it out and add it to the top message.

The instructions below are almost identical to the parent message with all the instructions, however I will highlight the difference in bold.

And yes, this is my first post to Ubuntu Forums, so I don't know how to use the quotes that are usually used to wrap codes, but anyways, 

Here goes:

Step 1:
sudo rmmod sony_acpi

Step 2:
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4 libxosd-dev checkinstall


Step 3
wget [http://download.berlios.de/fsfn/sony_acpi.tar.gz](http://download.berlios.de/fsfn/sony_acpi.tar.gz)

Step 4
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt](http://student.dei.uc.pt/~jpoa/fsfn/fsfn.conf.txt)

Step 5
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt](http://student.dei.uc.pt/~jpoa/fsfn/fsfn.txt)

Step 6
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn_1.1-1_i386.deb](http://student.dei.uc.pt/~jpoa/fsfn/fsfn_1.1-1_i386.deb)

Step 7
wget [http://student.dei.uc.pt/~jpoa/fsfn/fsfn-1.1-take2.tar.gz](http://student.dei.uc.pt/~jpoa/fsfn/fsfn-1.1-take2.tar.gz)

Step 8
sudo dpkg -i fsfn_1.1-1_i386.deb

Step 9
tar xvzf sony_acpi.tar.gz

Step 10
cd sony_acpi

Step 11
make

[B]Step 12
sudo cp sony_acpi.ko /lib/modules/2.6.22-14-generic/ubuntu/acpi/[/B]

[B]Step 13 (Depreciated but I still did it anyways, don't think this is necessary)
sudo mkdir /lib/modules/2.6.22-14-generic/kernel/ubuntu/
sudo mkdir /lib/modules/2.6.22-14-generic/kernel/ubuntu/acpi/
sudo cp sony_acpi.ko /lib/modules/2.6.22-14-generic/kernel/ubuntu/acpi/[/B]

Step 14
cd ..

Step 15
sudo modprobe sony_acpi

Step 16
tar zxvf fsfn-1.1-take2.tar.gz

Step 16
cd fsfn-1.1

Step 17
./configure && make && sudo checkinstall

Step 18
cd ..

Step 19
sudo rmmod sony_acpi

Step 20
sudo modprobe sony_acpi

Step 21
ls /proc/acpi/sony/

Step 22
Check for this output from the last command
brightness brightness_default fnkey

if this shows, good, continue

Step 23
sudo cp fsfn.conf.txt /etc/fsfn.conf

Step 24
sudo fsfn

Alright done.  Now test the FN-key and see if they work.  I KNOW FOR SURE they work for me, Gutsy Gibbon.

Regards
Jerome

Hello:

I'm newbie, and I arriegue to use these steps to the FJ series, it no gave me result, only works brightness, and move one level, but I lose my control functions in gnome, the truth that I love, what they ask me to explain as to remove all these steps to stop my funtions of brightness as before, I very much appreciate the support given to me, in advance greetings and thank you very much! ! !

---

### Post by zamurai on 2007-10-27
Hi, I'm using fs25gp. When I ran the 1st command, it gave me this error. 

```
sudo rmmod sony_acpi
ERROR: Module sony_acpi does not exist in /proc/modules
```


:confused::confused:

---

### Post by Depressed Man on 2007-10-27
That means you never installed the module to begin  (that's fine, go to next step)

---

### Post by derick on 2007-10-27
Ok, gone through this on Gutsy.  Sony_acpi module built and running.  However, I only get the brightness and brightness_default files in /proc/acpi/sony, no fnkey.

Any clues as to why this would be?

---

### Post by ygxu on 2007-10-28
Help ~!!!

I have done  all the thing, but there are only two file in "/proc/acpi/sony/"--(brightness brightness_default ) no  "fnkey"

what is wrong with me? 

thanks~!

by the way 

It is necessory for me to mkdir "/lib/modules/2.6.22-14-generic/kernel/ubuntu/acpi" and copy sony_acpi.ko there. 
however this is not enough, brightness and brightness_default still cannot be seen, until restarting the laptop


my ubuntu version is "7.10 Gutsy Gibbon", and the linux core is  2.6.22-14-generic

---

### Post by zamurai on 2007-10-28
Step 3, The link is down. Can anyone fix it?

I also tried clicking as direct link, it doesn't work.

Thanx

---

### Post by mjpoetic on 2007-10-28
I have a copy...I really don't think you need it though.

I uploaded it to mediafire here's the link:
[http://www.mediafire.com/?8blfywowmd9](http://www.mediafire.com/?8blfywowmd9)

---

### Post by JpB&#1103; on 2007-10-29
Like zamurai said, it's actually the link for step 3 that isn't working, to get the sony_acpi module. Any thoughts? I want desperately to get this working! Thanks!!

---

### Post by JpB&#1103; on 2007-10-29
On whim, I tried ```
wget http://download2.berlios.de/fsfn/sony_acpi.tar.gz
``` for step 3, and it works. Hope that helps!

---

### Post by aeonwings on 2007-10-29
Ok, I'm super new to linux and commands, so I don't understand what I'm suppose to do with the links from step 3-7.  I'm using an FJ model laptop so what part do I step do I insert the FJ hack?

It is so annoying that when I unplugged the charger, the screen turns dark, and I can't do anything about it. Thanks

---

### Post by Miette-chan on 2007-10-30
After successfully getting to step 22 when I try 

```
ls /proc/acpi/sony
``` nothing showed up.

---

### Post by mjpoetic on 2007-10-31
> **Miette-chan said:**
> After successfully getting to step 22 when I try 

```
ls /proc/acpi/sony
``` nothing showed up.
I am experiencing that problem now after I had it working before.  Something changed between the release candidate of Gutsy and the official release, but I can't figure out what.

[COLOR=DarkRed]**UPDATE:**
I have been messing around with this and I managed to install it now.  First I unloaded the other sony modules before installing things (i.e., sonypi and sony_laptop).  Then when you are compiling the sony_acpi.ko file use:

```
make && sudo make install
```Copy the sony_acpi.ko to it's appropriate place:

```
sudo cp sony_acpi.ko /lib/modules/`uname -r`/ubuntu/acpi/
```I also copied it to the other directory just in case:
```
sudo cp sony_acpi.ko /lib/modules/`uname -r`/kernel/ubuntu/acpi/
```That was basically the only thing I did different from the instructions and now it works again.  Whew!  Hopefully this helps you out.[/COLOR]

---

### Post by makrook on 2007-11-02
hello,

I'm with a fresh installed gutsy on a vaio VGN-NR11S/S

I tried the entire thing two times, following the first step-by-step instructions and then unloading everything and redoing it with the modifications from mjpoetic.
but still, absolutely nothing shows up in /proc/acpi/sony

so, before I throw my notebook through the window (I begin to *seriously* think about that) can anyone help ?
or does anyone have any idea where and what to look for to try to identify the problem ?

why sony laptop keyboards are such a pain in the ... ????? (this as well I'd like to understand)

thanks,

Ugo

---

### Post by Zhukov on 2007-11-05
Mine worked fine when updating to gutsy :)

---

### Post by Zhukov on 2007-12-04
Man, thanks! Really :)

You saved my day with this! I added your instructions to the first post.

Ill try to get some time to clean it and add it to the wiki.

Cheers!

> **mjpoetic said:**
> I am experiencing that problem now after I had it working before.  Something changed between the release candidate of Gutsy and the official release, but I can't figure out what.

[COLOR=DarkRed]**UPDATE:**
I have been messing around with this and I managed to install it now.  First I unloaded the other sony modules before installing things (i.e., sonypi and sony_laptop).  Then when you are compiling the sony_acpi.ko file use:

```
make && sudo make install
```Copy the sony_acpi.ko to it's appropriate place:

```
sudo cp sony_acpi.ko /lib/modules/`uname -r`/ubuntu/acpi/
```I also copied it to the other directory just in case:
```
sudo cp sony_acpi.ko /lib/modules/`uname -r`/kernel/ubuntu/acpi/
```That was basically the only thing I did different from the instructions and now it works again.  Whew!  Hopefully this helps you out.[/COLOR]

---

### Post by bigbrovar on 2007-12-09
please non of these procedures worked for my sony vaio fz21e .volumes works but i cant get brightness to work.. also my mutimedia keys dont work.. is there anything i can do ... using ubuntu is beginging to frustrate me

---

### Post by AirLancer on 2007-12-19
Hi, I have a Vaio VGN-BX570B, I use Ubunto 7.10 (Gutsy)
when I get to the point
brightness brightness_default fnkey
i get
bash:brightness:command not found

can someome please help me?

---

### Post by tedmar on 2007-12-25
I followed the instructions on my VGN-FS570 and the Fn keys are operable. (Ubuntu 7.10)
I can use volume and brightness settings.
Following problems are encountered:
1.- When I use the Fn keys there are no message in screen
2.- When I boot up, there is no audio and also the Fn keys are not functioning. In order to recover audio and Fnkeys I must 'rmmod' sonypi and sony-laptop and 'modprobe' sony_acpi.
3.- If I try to hear an MP3 file, as soon as I try to touch volume with Fn keys, screen is blanked and computer is no more responsive, although I can hear the MP3 song.

---

### Post by Toufik on 2008-01-02
> **AirLancer said:**
> Hi, I have a Vaio VGN-BX570B, I use Ubunto 7.10 (Gutsy)
when I get to the point
brightness brightness_default fnkey
i get
bash:brightness:command not found

can someone please help me?

You don't have to execute "brightness etc", you should ** see** "brightness etc" when you type ls /proc/acpi/sony/

Remark to everybody seeing nothing at this stage, you may need to reboot before it works. If you still get issues, type
```
sudo lsmod | grep sony
```
you should see "sony_acpi", if not, add sony_acpi at the end of this file:
```
sudo gedit /etc/modules
```
then reboot and check again with lsmod

---

### Post by dontcopymusic on 2008-01-24
Thanks a lot! My FN keys work fine now! I have a FS315B.
Maybe you could add to the first post that it might be necessary to reboot before you can see "brightness" etc when doing "ls /proc/acpi/sony"...

Great tutorial! Thanks :)

---

### Post by matt_risi on 2008-03-07
Works awesome, now just have to figure out how to implement it on bootup. I'm on the laptop below. :)

---

### Post by danscali on 2008-03-17
Have anyone got this to work with VGN-FZ240E?

---

### Post by mjpoetic on 2008-03-27
I am using fsfn in Hardy Beta!

I don't if people know this one already or not, but in another [thread]("http://ubuntuforums.org/showthread.php?p=3873750#post3873750")...someone posted the attached version of fsfn that supports the newer **sony_laptop** module** (so, AFAIK, no need for sony_acpi anymore)**.  The instructions should be pretty much the same from Zhukov's on page 1.

[B]NOTE: The deb installs fsfn to [COLOR=Green]/usr/bin/fsfn[/COLOR] and [COLOR=DarkRed]not[/COLOR] [COLOR=DarkRed]/usr/local/bin/fsfn[/COLOR].  So I just changed that line in the other file for you (or you can just change it yourself).

Not that it's dangerous or anything, but permit me to also say...USE AT YOUR OWN RISK!
[/B]

---

### Post by mmk622 on 2008-06-20
Quite interesting thread :)


I have SONY VAIO VGN CR-320 Series. I dont want to experiment on it since it is brand new :guitar:

Will this procedure suggested works fine for SONY VAIO VGN CR320 ?

Also suggest me any other new packages for my sony vaio .

-Murali:)

---

### Post by ndmciq on 2008-06-24
Hi! I have 2 OSD screen. Where's the problem?

Ubuntu Hardy - Vaio VGN-FS415M

---

### Post by mmk622 on 2008-06-24
I am using sony vaio cr320 laptop.Volume keys provided by sony vaio on top of keyboard are not working. But when I press volume up an image of speaker is displayed and volume status bar moves froward and same with volume down also infact volume status bar decreases.

Can anybody help me out pls...:(

---

### Post by tellyons on 2008-08-23
Many thanks for this.
The bit for Feisty users onwards worked just fine on my
VGN-FS285H running Hardy 2.6.24-21

:guitar:

---

### Post by orengolan on 2008-10-18
my fnc+f7 (video out) is not working on vaio vgn txn27.
I have Hardy.

any idea if any of those instructions are relevant to me?

Thanks!

---

### Post by ARGONIQ on 2008-11-17
> **mjpoetic said:**
> I am using fsfn in Hardy Beta!

I don't if people know this one already or not, but in another [thread]("http://ubuntuforums.org/showthread.php?p=3873750#post3873750")...someone posted the attached version of fsfn that supports the newer **sony_laptop** module** (so, AFAIK, no need for sony_acpi anymore)**.  The instructions should be pretty much the same from Zhukov's on page 1.

[B]NOTE: The deb installs fsfn to [COLOR=Green]/usr/bin/fsfn[/COLOR] and [COLOR=DarkRed]not[/COLOR] [COLOR=DarkRed]/usr/local/bin/fsfn[/COLOR].  So I just changed that line in the other file for you (or you can just change it yourself).

Not that it's dangerous or anything, but permit me to also say...USE AT YOUR OWN RISK!
[/B]

This worked for me on ubuntu Hardy, but in intrepid ibex not. There's a way to FN keys work on intrepid?

Thx

---

### Post by mk2lehe on 2008-11-18
Maybe this gives the experts some fn-related clues about 8.10. 

To /etc/X11/xorg.conf, I added:

```
Section "InputDevice"
	Identifier "Vaio keys" 
	Driver "evdev" 
	Option "Name" "Sony Vaio Keys" 
EndSection 
```

This made Power Manager Brightness Applet 2.24.0 on my Gnome panel work.

I'm on a fresh ubuntu 8.10 install on Vaio FG-FS395VP, and 'lsmod | grep -i sony' says I've loaded
sony_acpi
sony_laptop

Still, the fn keys does not work.

/H

---

### Post by mjpoetic on 2009-02-28
fsfn works in Jaunty Alpha 5!!  See this thread for the deb you need to get it working out of the box:

[http://ubuntuforums.org/showthread.php?t=759150](http://ubuntuforums.org/showthread.php?t=759150)

---

### Post by trelirodia on 2009-03-28
Hi there

> **mjpoetic said:**
> fsfn works in Jaunty Alpha 5!!  See this thread for the deb you need to get it working out of the box:

[http://ubuntuforums.org/showthread.php?t=759150](http://ubuntuforums.org/showthread.php?t=759150)

I've installed the deb file and have managed to get the fnkeys to work in past versions of Ubuntu, but not for 8.10. I have a vaio vgn-fs195xp and both sony-laptop and sonypi are in the kernel. The fnkeys are also recognised when I use fnkey to see the number they are mapped on. All this is fine, but it seems like fsfn is not working and when I type fsfn -o it hangs. Any ideas? Have you or anyone else made it work for 8.10?

Many thanks in advance for the help,
T

---

### Post by ARGONIQ on 2009-05-06
> **mjpoetic said:**
> fsfn works in Jaunty Alpha 5!!  See this thread for the deb you need to get it working out of the box:

[http://ubuntuforums.org/showthread.php?t=759150](http://ubuntuforums.org/showthread.php?t=759150)

In Jaunty final this deb dont work.

Any other idea?

---

### Post by svaens on 2009-06-13
I had the brightness problem with my Sony Vaio VGN-FW35G, on Ubuntu 9.04 (jaunty)
I fixed it with a script. See what i used, and where I got it here:

[http://ubuntuforums.org/showthread.php?t=1185307](http://ubuntuforums.org/showthread.php?t=1185307)

However, as I say in my thread above, now i have troubles with the Fn volume keys. 

When i first installed I didn't have this problem.
However, I changed an option in the alsa-base.conf file (to try and get jack detection, which worked). And with that option, I have no volume control through the FN key. 

the options being:
options snd-hda-intel model=hippo

So I gained jack detection, and lost volume control. 

I assume then that the option I used wasn't completely correct. 

Anyone got any ideas? I've tried a few other options, but not found anything that works. 

regards, 

Sean

---

### Post by fernandoch on 2009-09-09
Does that work with ubuntu 9.04 on vaio vgn sr series?

---

### Post by svaens on 2009-09-09
Update:
I have a vaio vgn-fw35G, and am using ubunti 9.04.

I solved my volume control issue. 
I realised that the volume control keys on my laptop were controlling the mic recording volume. It was an easy case of changing the options in the System/Preferences/Sound dialog.

As of 9/9/09, the snd-hda-intel option doesn't seem to do much at all. My jack detection works fine whichever I choose, and the volume is nice and strong. Brightness still works fine thanks to that script I mentioned in the previous post. 

I also have a fn key that looks like a zoom in and zoom out (on the F9 and F10 keys). That doesn't seem to do anything, and I didn't have any other operating system on my machine long enough to test it there either..... Anyone else?

---

### Post by mojotexas on 2009-10-02
Has anyone had any luck geting Function Keys to work on Sony Vaio PCG series in Jaunty?

---

### Post by nomnex on 2009-10-23
> **mojotexas said:**
> Has anyone had any luck geting Function Keys to work on Sony Vaio PCG series in Jaunty?

 a. load the module related to your computer make.
b. module names: sony-laptop.ko
c. modules location: /lib/modules/2.6.xx-xx-generic/kernel/drivers/misc/sony-laptop.ko
c. command: sudo modprobe sony-laptop
d. edit the /etc/module: sony-laptop (one single line)
e. restart.

---

### Post by angelblack666 on 2010-06-30
tengo una sonyvaio pcg-grt360zg despues de hacer todo lo aqui escrito no se me solucionaba el problema espero les ayude esta solucion tienen que presionar las teclas ctrl-alt-numlk y se me acabo el problema de que me salian numeros en lugar de letras espero les sirva.

---

### Post by svaens on 2010-06-30
you might want to repeat that one, angelblack666, in English, for the members not quite so far in their Spanish learning ;)

---

