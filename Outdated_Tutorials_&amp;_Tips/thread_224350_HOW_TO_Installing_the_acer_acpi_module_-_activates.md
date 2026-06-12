---
title: "HOW TO: Installing the acer_acpi module - activates wireless on Acer laptops"
date: 2006-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ovimunt on 2006-07-27
***Last updated on 29/07/2006 21:03 GMT.***

**ATTENTION: This HOW TO covers ONLY the installation of the *acer_acpi* module and NOT of the wireless adapter drivers.**

Before you can go ahead and install the ***acer_acpi*** module you need to make sure you have some other tools installed.
```

sudo aptitude update
sudo aptitude install build-essential

```

***UPDATED:***
You'll also need the linux headers:
```

sudo aptitude install linux-headers-$(uname -r)

```
***END OF UPDATE***

Once this is done you can go ahead and install the ***acer_acpi***.
First you should create a folder to keep all your downloads in one place.
```

mkdir /home/USER_NAME/download

```
Where USER_NAME is your actual user name.

Now go to the new folder
```

cd /home/USER_NAME/download

```

and download and install the package:
```

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install
cd ../..

```

Load the acer_acpi into memory and activate the wireless:
```

su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit

```

And check if it worked:
```

dmesg | grep acer_acpi

```

You should get some output like this:
```

[17179594.992000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17179595.000000] acer_acpi: Wireless value 1

```

Right, this might have worked for now but you need to load and activate ***acer_acpi*** every time your computer starts. 
For this you can write a little start up script so you don't have to do it manually each and every time.

[b]ATTENTION!
For Gnome type:[/b]
```

sudo gedit /etc/init.d/acer_acpi_wireless_enable

```
**Or if you're running KDE type:**
```

sudo kate /etc/init.d/acer_acpi_wireless_enable

```

Paste the following code and save:
```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo "enabled: 1" >/proc/acpi/acer/wireless

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Make the file executable and add it to the appropiate linux run levels.
**ATTENTION! Don't miss ANY of the characters in the following lines, especialy the dots in the third line!**
```

su
chmod 755 /etc/init.d/acer_acpi_wireless_enable
update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
exit

```

Now check if it worked:

```

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

```

If you get any ***No such file or directory*** messages then something must have gone wrong during the last couple of steps but your ***acer_acpi*** is still installed and can be started manually if needed.

If you didn't get any error messages everything should be up and running. You can now restart the computer and, if you have already installed the wireless drivers, your wireless adapter should work fine and be ready to configure.

---

### Post by jngtt on 2006-09-17
for the last 3 lines of codes i replace the dash with underscores
and it worked for me
thanks ovimunt

```

ls /etc/rcS.d/S39acer_acpi_wireless_enable
ls /etc/rc0.d/S34acer_acpi_wireless_enable
ls /etc/rc6.d/S34acer_acpi_wireless_enable

```

---

### Post by WalterIM on 2006-10-08
Hi, 
I'm using an Acer Aspire 5043. The wireless and mailled are working fine but the bluetooth isn't. Any hints ?

Thanks,

Walter.

---

### Post by karhulitos on 2006-10-15
Thanks ovimunt!

I had exactly one week own time to play with new laptop and get Ubuntu to run on it. I've been struggling to get wlan to work all this time.
It is now day 6 and I found your thread. 15 minutes wlan light is lit.

(Acer Aspire 5044 WLMi)

Thank you very much!

---

### Post by joellord on 2006-11-12
The link to the acer_acpi download doesn't seem to work.  Anyone knows an alternate download site ?

---

### Post by joellord on 2006-11-13
The link to acer_acpi seems to work again...  never mind that last message.
 
About acer_acpi, I just tried a fresh install and followed everything here (until modprobe) but I still get the message:

```
root@joel-laptop:~# modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko): No such device

```

What is it that I'm doing wrong ???

Thanks,
Joel

---

### Post by mig10k on 2006-12-20
i have an acer 2413WLMi(CeleronM, Atheros wifi - using madwifi) and my wireless connection needs to be restarted from time to time. it works for some minutes, sometimes some hours, and sometimes for 2-3 minutes and then it just hangs out.

can i fix somehow that the connection will be stable?

---

### Post by bloodniece on 2006-12-22
You magnificent SOB!  I read your thread and got my TravelMate 4400 w/ BCM4318 card to work. You rock!


:p :p :p :p :p :p :p :p

---

### Post by HyperFlexed on 2006-12-24
> **joellord said:**
> The link to acer_acpi seems to work again...  never mind that last message.
 
About acer_acpi, I just tried a fresh install and followed everything here (until modprobe) but I still get the message:

```
root@joel-laptop:~# modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko): No such device

```

What is it that I'm doing wrong ???

Thanks,
Joel

I get a similar if not the same message

```

root@Johnny-Laptop:/home/johnny# modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

```

And I am wondering why my error says nothing about AMD64, because I do have an AMD 64

---

### Post by mmendez on 2006-12-28
Alright so Im on a Ferrari 4000 and I had to update my kernel to 2.6.19.1 for ndiswrapper to work with edgy and now when I go to do ¨make¨ i get (prepare)

manny@mannymovil:~/Downloads/acer_acpi-0.3$ make
awk: cannot open /lib/modules/2.6.19.1/build/include/linux/version.h (No such file or directory)
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
acer_acpi.c:41:26: error: linux/module.h: No such file or directory
acer_acpi.c:42:24: error: linux/init.h: No such file or directory
acer_acpi.c:44:27: error: linux/proc_fs.h: No such file or directory
acer_acpi.c:45:25: error: linux/delay.h: No such file or directory
acer_acpi.c:46:27: error: linux/suspend.h: No such file or directory
acer_acpi.c:47:25: error: asm/uaccess.h: No such file or directory
acer_acpi.c:49:31: error: acpi/acpi_drivers.h: No such file or directory
acer_acpi.c:51: error: expected declaration specifiers or &#8216;...&#8217; before string constant
acer_acpi.c:51: warning: data definition has no type or storage class
acer_acpi.c:51: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;MODULE_AUTHOR&#8217;
acer_acpi.c:51: warning: function declaration isn&#8217;t a prototype
acer_acpi.c:52: error: expected declaration specifiers or &#8216;...&#8217; before string constant
acer_acpi.c:52: warning: data definition has no type or storage class
acer_acpi.c:52: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;MODULE_DESCRIPTION&#8217;
acer_acpi.c:52: warning: function declaration isn&#8217;t a prototype
acer_acpi.c:53: error: expected declaration specifiers or &#8216;...&#8217; before string constant
acer_acpi.c:53: warning: data definition has no type or storage class
acer_acpi.c:53: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;MODULE_LICENSE&#8217;
acer_acpi.c:53: warning: function declaration isn&#8217;t a prototype
acer_acpi.c:76: error: expected specifier-qualifier-list before &#8216;u32&#8217;
acer_acpi.c:91: error: expected specifier-qualifier-list before &#8216;acpi_handle&#8217;
acer_acpi.c: In function &#8216;is_valid_acpi_path&#8217;:
acer_acpi.c:99: error: &#8216;acpi_handle&#8217; undeclared (first use in this function)
acer_acpi.c:99: error: (Each undeclared identifier is reported only once
acer_acpi.c:99: error: for each function it appears in.)
acer_acpi.c:99: error: expected &#8216;;&#8217; before &#8216;handle&#8217;
acer_acpi.c:100: error: &#8216;acpi_status&#8217; undeclared (first use in this function)
acer_acpi.c:100: error: expected &#8216;;&#8217; before &#8216;status&#8217;
acer_acpi.c:102: error: &#8216;status&#8217; undeclared (first use in this function)
acer_acpi.c:102: warning: implicit declaration of function &#8216;acpi_get_handle&#8217;
acer_acpi.c:102: error: &#8216;handle&#8217; undeclared (first use in this function)
acer_acpi.c:103: warning: implicit declaration of function &#8216;ACPI_FAILURE&#8217;
acer_acpi.c: At top level:
acer_acpi.c:107: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;WMAB_execute&#8217;
acer_acpi.c:158: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
acer_acpi.c: In function &#8216;read_mled&#8217;:
acer_acpi.c:185: warning: implicit declaration of function &#8216;sprintf&#8217;
acer_acpi.c:185: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
acer_acpi.c: In function &#8216;write_mled&#8217;:
acer_acpi.c:195: warning: implicit declaration of function &#8216;sscanf&#8217;
acer_acpi.c:195: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
acer_acpi.c:197: warning: implicit declaration of function &#8216;memset&#8217;
acer_acpi.c:197: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
acer_acpi.c:198: error: &#8216;WMAB_args&#8217; has no member named &#8216;eax&#8217;
acer_acpi.c:199: error: &#8216;WMAB_args&#8217; has no member named &#8216;ebx&#8217;
acer_acpi.c:200: warning: implicit declaration of function &#8216;WMAB_execute&#8217;
acer_acpi.c:202: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
acer_acpi.c: In function &#8216;read_bt&#8217;:
acer_acpi.c:213: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
acer_acpi.c: In function &#8216;write_bt&#8217;:
acer_acpi.c:223: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
acer_acpi.c:225: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
acer_acpi.c:226: error: &#8216;WMAB_args&#8217; has no member named &#8216;eax&#8217;
acer_acpi.c:227: error: &#8216;WMAB_args&#8217; has no member named &#8216;ebx&#8217;
acer_acpi.c:230: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
acer_acpi.c: In function &#8216;read_wlan&#8217;:
acer_acpi.c:241: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
acer_acpi.c: In function &#8216;write_wlan&#8217;:
acer_acpi.c:251: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
acer_acpi.c:253: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
acer_acpi.c:254: error: &#8216;WMAB_args&#8217; has no member named &#8216;eax&#8217;
acer_acpi.c:255: error: &#8216;WMAB_args&#8217; has no member named &#8216;ebx&#8217;
acer_acpi.c:257: warning: implicit declaration of function &#8216;printk&#8217;
acer_acpi.c:257: error: &#8216;KERN_INFO&#8217; undeclared (first use in this function)
acer_acpi.c:257: error: expected &#8216;)&#8217; before string constant
acer_acpi.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
acer_acpi.c: In function &#8216;read_version&#8217;:
acer_acpi.c:267: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
acer_acpi.c: At top level:
acer_acpi.c:280: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;__init&#8217;
acer_acpi.c:300: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;__exit&#8217;
acer_acpi.c:314: error: expected &#8216;)&#8217; before &#8216;handle&#8217;
acer_acpi.c: In function &#8216;acpi_acerkeys_add&#8217;:
acer_acpi.c:329: error: &#8216;acpi_status&#8217; undeclared (first use in this function)
acer_acpi.c:329: error: expected &#8216;;&#8217; before &#8216;status&#8217;
acer_acpi.c:332: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
acer_acpi.c:334: warning: implicit declaration of function &#8216;kmalloc&#8217;
acer_acpi.c:334: error: &#8216;GFP_KERNEL&#8217; undeclared (first use in this function)
acer_acpi.c:334: warning: cast to pointer from integer of different size
acer_acpi.c:336: error: &#8216;ENOMEM&#8217; undeclared (first use in this function)
acer_acpi.c:337: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
acer_acpi.c:338: error: &#8216;struct acer_hotk&#8217; has no member named &#8216;handle&#8217;
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:339: warning: implicit declaration of function &#8216;strcpy&#8217;
acer_acpi.c:339: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
acer_acpi.c:339: warning: implicit declaration of function &#8216;acpi_device_name&#8217;
acer_acpi.c:339: warning: passing argument 1 of &#8216;strcpy&#8217; makes pointer from integer without a cast
acer_acpi.c:340: warning: implicit declaration of function &#8216;acpi_device_class&#8217;
acer_acpi.c:340: warning: passing argument 1 of &#8216;strcpy&#8217; makes pointer from integer without a cast
acer_acpi.c:341: warning: implicit declaration of function &#8216;acpi_driver_data&#8217;
acer_acpi.c:341: error: invalid lvalue in assignment
acer_acpi.c:344: error: &#8216;status&#8217; undeclared (first use in this function)
acer_acpi.c:344: warning: implicit declaration of function &#8216;acpi_install_notify_handler&#8217;
acer_acpi.c:344: error: &#8216;struct acer_hotk&#8217; has no member named &#8216;handle&#8217;
acer_acpi.c:344: error: &#8216;ACPI_SYSTEM_NOTIFY&#8217; undeclared (first use in this function)
acer_acpi.c:345: error: &#8216;acer_acerkeys_notify&#8217; undeclared (first use in this function)
acer_acpi.c:347: error: &#8216;KERN_ERR&#8217; undeclared (first use in this function)
acer_acpi.c:347: error: expected &#8216;)&#8217; before string constant
acer_acpi.c: In function &#8216;acpi_acerkeys_remove&#8217;:
acer_acpi.c:354: error: &#8216;acpi_status&#8217; undeclared (first use in this function)
acer_acpi.c:354: error: expected &#8216;;&#8217; before &#8216;status&#8217;
acer_acpi.c:358: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
acer_acpi.c:359: warning: cast to pointer from integer of different size
acer_acpi.c:361: error: &#8216;status&#8217; undeclared (first use in this function)
acer_acpi.c:361: warning: implicit declaration of function &#8216;acpi_remove_notify_handler&#8217;
acer_acpi.c:361: error: &#8216;struct acer_hotk&#8217; has no member named &#8216;handle&#8217;
acer_acpi.c:361: error: &#8216;ACPI_SYSTEM_NOTIFY&#8217; undeclared (first use in this function)
acer_acpi.c:362: error: &#8216;acer_acerkeys_notify&#8217; undeclared (first use in this function)
acer_acpi.c:364: error: &#8216;KERN_ERR&#8217; undeclared (first use in this function)
acer_acpi.c:364: error: expected &#8216;)&#8217; before string constant
acer_acpi.c:365: warning: implicit declaration of function &#8216;kfree&#8217;
acer_acpi.c: At top level:
acer_acpi.c:370: error: variable &#8216;acpi_acerkeys&#8217; has initializer but incomplete type
acer_acpi.c:371: error: unknown field &#8216;name&#8217; specified in initializer
acer_acpi.c:371: warning: excess elements in struct initializer
acer_acpi.c:371: warning: (near initialization for &#8216;acpi_acerkeys&#8217;)
acer_acpi.c:372: error: unknown field &#8216;class&#8217; specified in initializer
acer_acpi.c:372: warning: excess elements in struct initializer
acer_acpi.c:372: warning: (near initialization for &#8216;acpi_acerkeys&#8217;)
acer_acpi.c:373: error: unknown field &#8216;ids&#8217; specified in initializer
acer_acpi.c:373: warning: excess elements in struct initializer
acer_acpi.c:373: warning: (near initialization for &#8216;acpi_acerkeys&#8217;)
acer_acpi.c:374: error: unknown field &#8216;ops&#8217; specified in initializer
acer_acpi.c:374: error: extra brace group at end of initializer
acer_acpi.c:374: error: (near initialization for &#8216;acpi_acerkeys&#8217;)
acer_acpi.c:377: warning: excess elements in struct initializer
acer_acpi.c:377: warning: (near initialization for &#8216;acpi_acerkeys&#8217;)
acer_acpi.c:381: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;acer_acpi_init&#8217;
acer_acpi.c:430: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;acer_acpi_exit&#8217;
acer_acpi.c:441: warning: data definition has no type or storage class
acer_acpi.c:441: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;module_init&#8217;
acer_acpi.c:441: warning: parameter names (without types) in function declaration
acer_acpi.c:442: warning: data definition has no type or storage class
acer_acpi.c:442: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;module_exit&#8217;
acer_acpi.c:442: warning: parameter names (without types) in function declaration
make: *** [acer_acpi.o] Error 1

which is right (the no such file or directory ALL THE WAY AT THE TOP) and unfortunately when i try to update the kernel headers before this I get 

manny@mannymovil:~$ sudo aptitude install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Any Ideas????????:confused: 

MAAAAAAAAANNNNNNNNNNNNNNNNNYYYYYYYYYYY THANKS

---

### Post by Scaryclouds on 2007-01-03
> **joellord said:**
> The link to acer_acpi seems to work again...  never mind that last message.
 
About acer_acpi, I just tried a fresh install and followed everything here (until modprobe) but I still get the message:

```
root@joel-laptop:~# modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-26-amd64-generic/extra/acer_acpi.ko): No such device

```

What is it that I'm doing wrong ???

Thanks,
Joel

I get the exact same message as well. Anybody else got some ideas on what to next?

---

### Post by Apples on 2007-01-07
I got that very same message! Has anyone gotten this and resolved it?

---

### Post by bartoknagyjanos on 2007-01-14
> **Apples said:**
> I got that very same message! Has anyone gotten this and resolved it?

The same problem (Acer Travelmate 2492nWLMi, BCM4318 )

heeeeeelp...

---

### Post by Matt J Thomas on 2007-01-15
Same problem as them - if it helps make someone solve problem

---

### Post by KarasuTengu on 2007-01-20
When I type:  sudo modprobe acer_acpi

I get the following"

```

FATAL: Module acer_acpi not found.

```


Anyone know what is going on with this? I followed the directions exactly....

---

### Post by -X- on 2007-01-23
Looks like I'm getting the same problem as everyone else - running Feisty Herd 2. I had to read through the "INSTALL" file to get it to compile without a bucketload of errors.

> FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-5-generic/kernel/drivers/acpi/acer_acpi.ko): No such device

---

### Post by Joe Kehr on 2007-01-24
I have the same problem as mmendez.

When I type the make command, it seems that there is a lot of problems.
```

zero@Zero:~/download/acer_acpi-0.3$ make
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /lib/modules/2.6.19.2/build/include/asm/timex.h:14,
                 from /lib/modules/2.6.19.2/build/include/linux/timex.h:187,
                 from /lib/modules/2.6.19.2/build/include/linux/sched.h:50,
                 from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/asm/processor.h:77: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.19.2/build/include/asm/processor.h:77: error: requested alignment is not a constant
/lib/modules/2.6.19.2/build/include/asm/processor.h:233: error: requested alignment is not a constant
In file included from /lib/modules/2.6.19.2/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.19.2/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:332: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:371: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.19.2/build/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/lib/modules/2.6.19.2/build/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /lib/modules/2.6.19.2/build/include/asm/semaphore.h:43,
                 from /lib/modules/2.6.19.2/build/include/linux/sched.h:59,
                 from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/linux/rwsem.h:24:65: error: asm/rwsem.h: Aucun fichier ou répertoire de ce type
In file included from /lib/modules/2.6.19.2/build/include/linux/memory_hotplug.h:7,
                 from /lib/modules/2.6.19.2/build/include/linux/mmzone.h:368,
                 from /lib/modules/2.6.19.2/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.19.2/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.19.2/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.19.2/build/include/linux/rcupdate.h:41,
                 from /lib/modules/2.6.19.2/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.19.2/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/linux/notifier.h: At top level:
/lib/modules/2.6.19.2/build/include/linux/notifier.h:62: error: field ‘rwsem’ has incomplete type
In file included from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/linux/sched.h:316: error: field ‘mmap_sem’ has incomplete type
/lib/modules/2.6.19.2/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/lib/modules/2.6.19.2/build/include/linux/sched.h:1268: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.19.2/build/include/linux/sched.h:1270: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.19.2/build/include/linux/sysdev.h:24,
                 from /lib/modules/2.6.19.2/build/include/linux/sched.h:1606,
                 from /lib/modules/2.6.19.2/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.19.2/build/include/linux/kobject.h: At top level:
/lib/modules/2.6.19.2/build/include/linux/kobject.h:172: error: field ‘rwsem’ has incomplete type
In file included from /lib/modules/2.6.19.2/build/include/linux/fs.h:356,
                 from /lib/modules/2.6.19.2/build/include/linux/proc_fs.h:5,
                 from acer_acpi.c:44:
/lib/modules/2.6.19.2/build/include/linux/quota.h:290: error: field ‘dqptr_sem’ has incomplete type
In file included from /lib/modules/2.6.19.2/build/include/linux/proc_fs.h:5,
                 from acer_acpi.c:44:
/lib/modules/2.6.19.2/build/include/linux/fs.h:561: error: field ‘i_alloc_sem’ has incomplete type
In file included from /lib/modules/2.6.19.2/build/include/linux/proc_fs.h:5,
                 from acer_acpi.c:44:
/lib/modules/2.6.19.2/build/include/linux/fs.h:927: error: field ‘s_umount’ has incomplete type
In file included from /lib/modules/2.6.19.2/build/include/acpi/platform/acenv.h:140,
                 from /lib/modules/2.6.19.2/build/include/acpi/acpi.h:54,
                 from /lib/modules/2.6.19.2/build/include/acpi/acpi_bus.h:31,
                 from /lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h:30,
                 from acer_acpi.c:49:
/lib/modules/2.6.19.2/build/include/acpi/platform/aclinux.h: In function ‘acpi_os_allocate’:
/lib/modules/2.6.19.2/build/include/acpi/platform/aclinux.h:116: warning: implicit declaration of function ‘irqs_disabled’
In file included from acer_acpi.c:49:
/lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h: At top level:
/lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h:69: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h:69: warning: its scope is only this definition or declaration, which is probably not what you want
/lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h:70: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h:72: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.19.2/build/include/acpi/acpi_drivers.h:77: warning: ‘struct acpi_device’ declared inside parameter list
acer_acpi.c: In function ‘acpi_acerkeys_add’:
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:339: warning: implicit declaration of function ‘acpi_device_name’
acer_acpi.c:339: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:340: warning: implicit declaration of function ‘acpi_device_class’
acer_acpi.c:340: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:341: warning: implicit declaration of function ‘acpi_driver_data’
acer_acpi.c:341: error: invalid lvalue in assignment
acer_acpi.c: In function ‘acpi_acerkeys_remove’:
acer_acpi.c:359: warning: cast to pointer from integer of different size
acer_acpi.c: At top level:
acer_acpi.c:370: error: variable ‘acpi_acerkeys’ has initializer but incomplete type
acer_acpi.c:371: error: unknown field ‘name’ specified in initializer
acer_acpi.c:371: warning: excess elements in struct initializer
acer_acpi.c:371: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:372: error: unknown field ‘class’ specified in initializer
acer_acpi.c:372: warning: excess elements in struct initializer
acer_acpi.c:372: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:373: error: unknown field ‘ids’ specified in initializer
acer_acpi.c:373: warning: excess elements in struct initializer
acer_acpi.c:373: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:374: error: unknown field ‘ops’ specified in initializer
acer_acpi.c:374: error: extra brace group at end of initializer
acer_acpi.c:374: error: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:377: warning: excess elements in struct initializer
acer_acpi.c:377: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c: In function ‘acer_acpi_init’:
acer_acpi.c:405: error: ‘acpi_root_dir’ undeclared (first use in this function)
acer_acpi.c:416: warning: implicit declaration of function ‘acpi_bus_register_driver’
acer_acpi.c: In function ‘acer_acpi_exit’:
acer_acpi.c:432: warning: implicit declaration of function ‘acpi_bus_unregister_driver’
make: *** [acer_acpi.o] Erreur 1

```

I suppose that if this doesn't work, that's not useful to continue.
So, tell me what to do to make this thing working.

I'm on an Acer 5014WLMi, with an AMD 64.

I hope you'll be able to help me...

Joe Kehr

---

### Post by -X- on 2007-01-25
Some usefull info from the install file:

> 4. Do:
	make
to compile the driver. If you run into problems because of the makefile not
recognizing your kernel version correctly, try this:
	make acer_acpi.o	- kernel version 2.4
	make acer_acpi.ko	- kernel version 2.6

5. Do:
	make install
to install the kernel module.  If that step fails, try:

Copy the created file "acer_acpi.o" ("acer_acpi.ko" with version 2.6) to your
kernel modules path. In Debian this could be
"/lib/modules/<kernelversion>/kernel/drivers/char/".
Update module dependencies: depmod -a

6. Try loading the module with:
	insmod/modprobe acer_acpi

So, try...

```
make acer_acpi.ko
make install
```

For me it compiles fine that way but I still get the "No such device" error.

---

### Post by Johnny_Too_Bad on 2007-01-30
OK, so I'm brand new to Linux/Ubuntu and while I do love it, I cannot stand not having wireless.  I'm running Dapper on an Acer Aspire 3620, and have followed all the steps in the Broadcom forum which re-directed me here.

Everything works out great until I get to the following:

```
su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit
```

When I type "su" I get asked for my Password, but when I type it in, I am met with the following message:

```
su: Authentication failure
Sorry.
```

I don't get it.  What am I supposed to do?  I read someplace else that I should instead type "sudo", but then when I put in "modprobe acer_acpi", this appears:

```
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-27-386/extra/acer_acpi.ko): Operation not permitted

```

I am so completely lost in all of this.  All I want is to use the internet on my laptop.  Why does it have to be such a painfully arduous process?

In short, PLEASE HELP!

---

### Post by Perfecto on 2007-01-30
su: Authentication failure

You can try with this:

sudo su
[LEFT]You will become root after introducing the correct password

FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-27-386/extra/acer_acpi.ko): Operation not permitted
Try first deleting the file and later installing:

sudo su
rm /lib/modules/2.6.15-27-386/extra/acer_acpi.ko
make clean
make acer_acpi.ko
cp -v acer_acpi.ko /lib/modules/2.6.15-27-386/extra/
depmod -a
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless

I couldn't use "make install", it didn't worked correctly in my case, I think that it is because it can't find the correct kernel.

Be sure that the kernel you are running is the correct, in your case if you execute:

uname -r

you will have:

2.6.15-27-386

Thanks for everybody because this is the first time I make my BCM4318 on an Aspire 5021 to work. :D

[/LEFT]

---

### Post by Johnny_Too_Bad on 2007-01-30
OK, so I did the little "sudo su" trick and found, much to my delight, that it worked.  So, I proceeded with the guide and, according to it, everything works fine.  In reality, it does not.  The light is on, but no one's home, as it were.

I can manage to "see" networks around me, and activating the wireless card and all that works fine, but whenever I switch from wired to wireless, it says I have absolutely no signal strength.  As I am typing this, I am sitting in the very room where my router is located.  Why am I getting no signal?  I followed both this guide and the "HOWTO: Broadcom..." guide to the letter, and still nothing.

Why must these things be so difficult?

---

### Post by mmendez on 2007-01-31
This has also happened to me before on every machine I've installed Dapper with. I think it might have something to do with the alternate install version. Anyway this is what I always do to:
Turn on/Restart
when grub is loading press "Esc"
select latest kernel in safe/recovery mode
if this is your first time going into safe mode you should be automatically logged in as root
enter ```
passwd
```
and then just enter the password
then enter ```
exit
```
and then X should start and you can try again it again with this password
if you get it working please post because the same has happened to me and I am no go

---

### Post by Johnny_Too_Bad on 2007-01-31
> **mmendez said:**
> This has also happened to me before on every machine I've installed Dapper with. I think it might have something to do with the alternate install version. Anyway this is what I always do to:
Turn on/Restart
when grub is loading press "Esc"
select latest kernel in safe/recovery mode
if this is your first time going into safe mode you should be automatically logged in as root
enter ```
passwd
```
and then just enter the password
then enter ```
exit
```
and then X should start and you can try again it again with this password
if you get it working please post because the same has happened to me and I am no go

While I'm not entirely sure what this was supposed to accomplish...:confused: 

Either way, I created a new password, but it didn't work for anything.  And I'm still not getting a signal.  :(

---

### Post by neocon on 2007-02-01
Well guys, I've tried everything but it still doesn't work, I get the same message as everyone
```

FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-27-386/extra/acer_acpi.ko) : No such device
```

I still can't get passed this error, and I've tried all the aforementioned. Please help

thanks in advance

---

### Post by KarasuTengu on 2007-02-02
```

FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-6-generic/extra/acer_acpi.ko): No such device

```

Still doesn't work.

---

### Post by disabled_20220313 on 2007-02-02
Hi, 

I also get,

```
FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-386/extra/acer_acpi.ko): No such device

```

I think a lot of people here are experiencing problems with your guide. Has anyone suss'd it out yet? I'd be willing to post up outputs of commands, as long as you ask which commands.

---

### Post by diatribe on 2007-02-03
I have a aspire 3004 that I have gotten wireless working on.  I followed the instructions at :

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

The wireless light does not come on at boot, but will light up when in use.  Try using these instructions and let me know what happens.

Edit:  I had also tried following these directions and they did not work; I recieved the same error messages as the rest of you.

---

### Post by -X- on 2007-02-04
I got my wireless to work by installing linux-restricted-modules (Atheros chip). I would still like to get the switches and bluetooth working, however.

---

### Post by mmendez on 2007-02-05
> **diatribe said:**
> I have a aspire 3004 that I have gotten wireless working on.  I followed the instructions at :

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

The wireless light does not come on at boot, but will light up when in use.  Try using these instructions and let me know what happens.

Edit:  I had also tried following these directions and they did not work; I recieved the same error messages as the rest of you.
diatribe where did you get the acerhk driver from? or did it work as soon as you finished installing it?

---

### Post by spacetree on 2007-02-14
If you check the official site for acer_acpi, it clearly says FERRARI 4000 not supported. Sorry

But in my case, i also get a similar output with:

FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-11-generic/extra/acer_acpi.ko): No such device

saul@saul-laptop:/proc/acpi$ dmesg | grep acer_acpi
[  114.519283] acer_acpi: Acer Laptop ACPI Extras version 0.3
[  114.519295] acer_acpi: No WMI interface, unable to load.


I must say i have an acer aspire 5101 . turion x2, and atheros wiresslan chipset

---

### Post by kosson on 2007-02-24
I tried installing acer_acpi on a Faisty Fawn Hurd 4 and I encountered a beautifull line:

FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-8-generic/kernel/drivers/char/acer-acpi.ko): Invalid module format


I mention that making acer_acpi didn't work so I copied the .ko in its rightful place I depmod-ed but nothing

moddprobe acer_acpi throwed the beutifull line right on my nose !

HELP !

---

### Post by mmendez on 2007-02-24
Ok so guess what everybody? I have my wireless working!!! I sure wish I would have looked [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") before doing all this stuff being that this wont work for the Ferrari's. Anyway I tried the firmware cutter and it worked like a charm. I do have a wireless connection and can even surf on my default network. I am having a problem with compwiz's "wicd" and connecting to other networks but I think thats another matter. I will once again confirm that this worked for me and you might want to try this out.

---

### Post by HailandKill on 2007-03-02
> **kosson said:**
> I tried installing acer_acpi on a Faisty Fawn Hurd 4 and I encountered a beautifull line:

FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-8-generic/kernel/drivers/char/acer-acpi.ko): Invalid module format


I mention that making acer_acpi didn't work so I copied the .ko in its rightful place I depmod-ed but nothing

moddprobe acer_acpi throwed the beutifull line right on my nose !

HELP !

Exactly the same problem I'm getting. What Acer model have you got? Mines the aspire 5050

---

### Post by kosson on 2007-03-03
I have Aspire 5101 ANWLMi 
There is not a resolution yet on this matter ! I only hope that stable version of Feisty will solve this matter !

Diggin' the WiFi support with a WinWiFi design is a pain in the proverbial... trust me !

I succeeded in workin out the wifi but I got really tired with errors and overal instability. So, i hope for the best and I'm eager to discover a distro that supports this card (bcm 4318).
There's only one month left.
We shall live and see...

---

### Post by HailandKill on 2007-03-04
After typing

> # sudo modprobe acer_acpi

and getting the "Invalid" error, dmesg is reporting:

```
acer_acpi: version magic '2.6.15-27-amd64-generic SMP preempt gcc-3.4' should be '2.6.15-27-amd64-generic SMP preempt gcc-4.0'
```

I'm not really sure what this means. But sure looks like a clue! Anyone?

---

### Post by HailandKill on 2007-03-04
EDIT :: Wrong thread.. oddly. :?

---

### Post by HailandKill on 2007-03-06
Been doing a little research..

For those of you getting the error "Invalid module format" try adding the flag --force-vermagic, so as root:

```
# modprobe acer_acpi --force-vermagic
```

With that I got a step further and got the more common error "No such device", result!

```
dmesg | grep acer
```

The above shows the "No WMI Interface" error. A known problem:

> 5. dmesg tells me "No WMI Interface: unable to load"

Your laptop does not have the ACPI BIOS interface I use to control the hardware. There may be an equivalent function with a different name - in order to find it, you'll need to do some disassembly of your ACPI DSDT, or send me the contents of the DSDT and once I have enough pieces I'll be able to put the picture together!

I've been looking at my DSDT, but it would help immensely if I had a few other DSDT from other broken acers and working ones. 

If there was anyone out there willing to lend a hand in trying to sort this could please post a reply attaching a copy of your DSDT. It would be further helpful if you could mention what model of acer you're using, and obviously whether it works or not!

To make a copy of your DSDT:

```
cat /proc/acpi/dsdt > ~/dsdt.dat
```

Attach the dsdt.dat (now in your home folder) with your post.

Thanks in advance for anyone willing to help.

---

### Post by MJewkes on 2007-03-08
Hey Everyone,
Installing the acer_acpi module, in combination with getting a proper ndiswrapper driver for my broadcom airforce one card has worked on my dapper xubuntu travelmate 4400.

However, could someone tell me how to set the acer_acpi to automatically load on boot-up in xubuntu dapper xfce?

thanks,
Matthew

---

### Post by HailandKill on 2007-03-09
> **MJewkes said:**
> Hey Everyone,
Installing the acer_acpi module, in combination with getting a proper ndiswrapper driver for my broadcom airforce one card has worked on my dapper xubuntu travelmate 4400.

However, could someone tell me how to set the acer_acpi to automatically load on boot-up in xubuntu dapper xfce?

thanks,
Matthew

try 

> # update-rc.d acer_acpi defaults

Since it's otherwise working on your machine, can I enlist you to make a copy of you DSDT and post it? (Instructions in my previous post)

---

### Post by xemoka on 2007-03-13
I am having the same problems. I have an Acer 5000 and here is my dsdt.dat
Thank you for everything you've done. I hope this i the lynch pin that is stopping me from using wireless with this laptop.

---

### Post by kosson on 2007-03-13
Aspire 5101 ANWLMi
AMD Turion 64 Mobile Technology MK36

dmesg:

[SIZE="2"]
[   41.209415] NET: Registered protocol family 10
[   41.209569] lo: Disabled Privacy Extensions
[   41.604918] ACPI: AC Adapter [ACAD] (on-line)
[   41.719464] input: Power Button (FF) as /class/input/input4
[   41.735309] ACPI: Power Button (FF) [PWRF]
[   41.771635] input: Lid Switch as /class/input/input5
[   41.787416] ACPI: Lid Switch [LID]
[   41.823725] input: Power Button (CM) as /class/input/input6
[   41.839575] ACPI: Power Button (CM) [PWRB]
[   41.875700] input: Sleep Button (CM) as /class/input/input7
[   41.891498] ACPI: Sleep Button (CM) [SLPB]
[   41.904140] No dock devices found.
[   41.996967] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   41.997291] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.128991] ACPI: Battery Slot [BAT1] (battery present)
[   42.144337] ibm_acpi: ec object not found
[   42.171879] Using specific hotkey driver
[   42.356119] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[   42.356163] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[   42.356166] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[   42.356168] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x12
[   42.356171] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   46.241012] eth0: link down
[   46.241234] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.435710] ppdev: user-space parallel port driver
[   52.562259] Bluetooth: Core ver 2.11
[   52.562313] NET: Registered protocol family 31
[   52.562315] Bluetooth: HCI device and connection manager initialized
[   52.562319] Bluetooth: HCI socket layer initialized
[   52.613507] Bluetooth: L2CAP ver 2.8
[   52.613511] Bluetooth: L2CAP socket layer initialized
[   52.700784] Bluetooth: RFCOMM socket layer initialized
[   52.700799] Bluetooth: RFCOMM TTY layer initialized
[   52.700801] Bluetooth: RFCOMM ver 1.8
[   71.515466] hda_codec: num_steps = 0 for NID=0xd
[   71.766754] hda-intel: Invalid position buffer, using LPIB read method instead.
[   72.194601] hda_codec: num_steps = 0 for NID=0xd
[   90.611106] hda_codec: num_steps = 0 for NID=0xd
[  114.308469] wlan0: no IPv6 routers present
[  125.527175] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
[  125.527180] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[  125.545104] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
[  125.545109] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.[/SIZE]

hope it helps

---

### Post by rohandhruva on 2007-03-17
I get the WMI error too, while loading the module. The laptop is Acer TravelMate 3260.

Attaching my dsdt - hope it helps ! :)

---

### Post by donnellymp on 2007-03-19
Hi. I've been through these forums looking for answers on how to get my wired *and* wireless Internet working on my Acer 3680 laptop. Tried Madwifi and Ndiswrapper tutorial found elsewhere. Googled a lot too. I have a fresh install of Ubuntu Edgy with the 2.6.17-10 generic kernel. I can't upgrade or load anything suggested in other tutorials because my Ethernet (wired) connect also doesn't work. What's weird is that a few times I got KNetwork manager in Sabayon and openSuse 10.2 to see my wireless connection, but it wouldn't connect to it successfully. Suspect something with the Acer acpi: tried *that* tutorial too, to no avail.

Without repeating the other tutorials, or linking me to them, what else can be done? Why can I see my wireless card but not connect to it? Please help!!

---

### Post by HailandKill on 2007-03-20
If it's an acer laptop, you'll certainly need [acer acpi](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html) or [acerhk](http://www.cakey.de/acerhk/). You can see it, but your software cannot cummunicate with it without one of these.

If you need a 64 bit port, your only hope is getting acer acpi to work.

I haven't used acerhk, but I can try and give you as much help with that as I can. On the other hand, I've got a lot more experience with the acer acpi and should hopefully be out with a fix soonish.

Where did you get stuck with the tutorial?

---

### Post by imda2001 on 2007-03-21
I'm still getting the same error:

bob@computer:~/download/acer_acpi-0.3$ sudo modprobe acer_acpi 
FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-11-generic/extra/acer_acpi.ko): No such device


Acer 5100, Ubuntu 6.10.  Any fixes for this, yet?

Thanks!

---

### Post by Hunter4242 on 2007-03-22
> **xemoka said:**
> I am having the same problems. I have an Acer 5000 and here is my dsdt.dat
Thank you for everything you've done. I hope this i the lynch pin that is stopping me from using wireless with this laptop.

I've also got an Aspire 5000, with the same issues. However when I try to get my dsdt file there's nothing in it. I may have missed a step somewhere, but if you find a solutiont hat works for the other Aspire 5000, it ought to work for me.

---

### Post by briansalo on 2007-03-22
This guide has worked up till the point that I enter the 'su' command and get an authentication failure when I enter in my password... Is there something I'm doing wrong or is there some sort of super secret password I need to know? lol

---

### Post by FNGtyler on 2007-03-23
help same damn problem acer aspire 5000 fresh install of ubuntu

root@laptop:/home/tyler# modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.17-10-generic/extra/acer_acpi.ko): No such device

I do have a blinking light now though. not sure why

---

### Post by -X- on 2007-04-01
There is a new version out (0.4) which should work on the newer kernels!

[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

---

### Post by benikaj on 2007-04-04
I have an Acer Aspire 5002 WLMi
I tried to insert acer_acpi using modprobe...
> 
sudo modprobe acer_acpi

...and got the same error.
> 
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-28-amd64-generic/extra/acer-acpi.ko): No such device

I then checked my kernel messages
> 
dmesg

dmesg reveales the following...
> 
[ 1489.657561] acer_acpi: Acer Laptop ACPI Extras version 0.3
[ 1489.657572] acer_acpi: No WMI interface, unable to load.

I traced the code and acer_acpi crapped out in acer_acpi.c in function acer_acpi_init(void).  When it tries the following...
> 
is_valid_acpi_path(WMI_METHOD)

I can only assume our models of acer laptops require a different WMI_METHOD value that the one acer_acpi is currently work with...
> 
#define WMI_METHOD              "\\_SB_.AMW0.WMAB"

Here is my DSDT file, hope it helps...

---

### Post by notsteve on 2007-04-05
hey i can't download aceracpi i think the site has changed for that site can do you have a newer link?

---

### Post by homiq78 on 2007-04-07
> **-X- said:**
> There is a new version out (0.4) which should work on the newer kernels!

[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

Right, I have downloaded it and I did everything according to the INSTALL file. Everything worked until I was told
> Copy the created file "acer_acpi.o" ("acer_acpi.ko" with version 2.6) to your
kernel modules path. In Debian this could be
"/lib/modules/<kernelversion>/kernel/drivers/char/".

I tried to do it using Nautilus, but I got the "You do not have permissions to write to this folder" dialog. I guess I have to do it as "root", but can anyone tell me how to do it?

Thanks a lot

By the way, when trying to install the old version (0.3) I get the usual "no such device" error.

---

### Post by homiq78 on 2007-04-07
> **notsteve said:**
> hey i can't download aceracpi i think the site has changed for that site can do you have a newer link?

The new link is [http://aceracpi.googlecode.com/files/acer_acpi-0.3.tar.gz](http://aceracpi.googlecode.com/files/acer_acpi-0.3.tar.gz) - it worked with me. There is also a newer version at [http://aceracpi.googlecode.com/files/acer_acpi-0.4.tar.gz]("http://aceracpi.googlecode.com/files/acer_acpi-0.4.tar.gz")

---

### Post by sarahg on 2007-04-10
[FONT="Arial Black"]Hi,

Does anyone know a alternative link for the:

wget [http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz](http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz) 

part of the installation? ?:confused: [/FONT]

---

### Post by notsteve on 2007-04-10
> **homiq78 said:**
> The new link is [http://aceracpi.googlecode.com/files/acer_acpi-0.3.tar.gz](http://aceracpi.googlecode.com/files/acer_acpi-0.3.tar.gz) - it worked with me. There is also a newer version at [http://aceracpi.googlecode.com/files/acer_acpi-0.4.tar.gz]("http://aceracpi.googlecode.com/files/acer_acpi-0.4.tar.gz")

that site didn't work, it does not find the file

---

### Post by archernar on 2007-04-14
The homepage is [http://code.google.com/p/aceracpi/]("http://code.google.com/p/aceracpi/"), just download the latest version from the download links on the right hand side.

---

### Post by H2OGuitarist on 2007-04-18
I can't even make the module. I read the INSTALL file and I don't know how to change KERNELSRC. Im a complete noob to this so could you please help me? I have an ACer Ferrari 4006 and running Dapper

---

### Post by archernar on 2007-04-20
Hi, you shouldn't need to change KERNELSRC at all, although with Dapper you might have more luck with version 0.3 rather than 0.4 (the only real change between versions is the build process for later kernels such as the one used in Feisty).
I don't know if acer_acpi works at all on the Ferrari 4006, but if you try a make, capture the output, and PM me including the output and I'll see if I can spot the problem.  I know 0.3 worked on Dapper, 'cos I used it myself :-)
The most important common trick (sorry if you've already done this) is to ```
sudo apt-get install build-essential
```

---

### Post by mansie on 2007-04-21
Just upgraded to feisty which broke my previous acer_acpi setup coz of the kernel update...

...but all I had to do, to fix it, was to run:

```

sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx
```

And if the above worked: Make it "stick" by editing your /etc/modules and replace acer_acpi with bcm43xx.

Thanks to mmendez who posted the url <3, found again as reference > [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") <

Is there any drawback to using this method instead of acer_acpi?

// mansie

---

### Post by KoldKay on 2007-04-22
Hi,

I have an Acer Aspire 5051AWXMi.  It's got the Broadcom BCM4318 802.11 b/g.  If I'm right, I take it I have to install this AFTER I've installed fwcutter or something else such as Ndiswrapper to get the Broadcom wireless card working, right?

I'm pretty confused about all this, so if someone could clarify this for me, that'd be much appreciated.

---

### Post by OG_LOC_08 on 2007-05-04
win i put  this in i got 

ace2k7@johnny-laptop:~/download$ tar zxvf acer_acpi-0.3.tar.gz
tar: acer_acpi-0.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ace2k7@johnny-laptop:~/download$ cd acer_acpi-0.3
bash: cd: acer_acpi-0.3: No such file or directory
ace2k7@johnny-laptop:~/download$ make
make: *** No targets specified and no makefile found.  Stop.
ace2k7@johnny-laptop:~/download$ sudo make install
ace2k7@johnny-laptop:~/download$ cd ../..
ace2k7@johnny-laptop:/home$ su
Password: 
su: Authentication failure

WTF dose this mean

---

### Post by aaronmontana on 2007-05-05
While reinstalling my wifi card on the ol'TravelMate 4400 after the feisty update - I noticed the acer_acpi download has been moved here:   [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)        Worked for me.

---

### Post by lxop on 2007-05-10
Like everyone, I'm getting the 'No Such Device' error. I'm on an Aspire 5001WLMi, standard 4318 chipset. Would love a solution.

 OG_LOC_08: You are trying to unzip the wrong file. Go to your download folder and right click on the file that starts with acer_acpi, then click 'extract here'. That does the first line of your problem. You probably have the newer version than when the instructions were written, so the filenames are incorrect. Carry on from the 'cd' command, but put the name of the folder that appeared when you unzipped the file in instead of 'acer_acpi-0.3'. That should get you a little further through.

---

### Post by kosson on 2007-05-11
same here !
I hate Winstrons....

---

### Post by cjbrooker on 2007-05-14
I'm also getting the 'No Such Device' error. I'm on an Aspire 3004WLMi. Would also love to have a solution to this.

---

### Post by Zdravko on 2007-05-14
I have an Acer laptop and my wireless worked *almost* out of the box. This howto is useless to me.

---

### Post by mumbly58 on 2007-05-17
Just wanted to inform you that i've just made a feisty .deb package for acer_acpi-0.5.
It should be fine for edgy too ...
This is a "beta release" and need feedback ... But it seems to work fine...
You will find it there : [http://repository.mumblyworld.info/](http://repository.mumblyworld.info/)  (look in feisty directory)
More info about acer aspire 5024 wlmi on my blog (in french !) : [http://www.mumblyworld.info](http://www.mumblyworld.info)

---

### Post by andreyvul on 2007-05-22
OG_LOC_08:
It means there was a snowball reaction because wget couldn't find the file because of a bad link. And because newline (or semicolon) was used instead of &&, the cascade is inevitable.

Works for me:
```

wget http://aceracpi.googlecode.com/files/acer_acpi-0.5.tar.bz2
tar xvf acer_acpi-*.tar.gz
cd acer_acpi*
make
sudo make install
cd ../..

```

---

### Post by Sonny Boy on 2007-05-22
the link....doesn't work for me either

Not found - 404

URL requested (/acer_acpi/acer_acpi-0.3.tar.gz) not found

---

### Post by Sir_Yaro on 2007-05-22
use The Brain Luke...
One post above there is proper link...

[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

---

### Post by tbalci on 2007-05-27
Hello,

Everything seems to work fine until I issue "modprobe acer_acpi" command.

I do not know the reason but it spits out:

modprobe acer_acpi:
```

FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-15-generic/extra/acer_acpi.ko): No such device

```

insmod acer_acpi:
```

insmod: can't read 'acer_acpi': No such file or directory

```

lsmod | grep acpi:
```

acpi_cpufreq           10056  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
processor              31048  2 acpi_cpufreq,thermal

```

I have both compiled acer_acpi v0.5 from source and by synaptic from 
[http://repository.mumblyworld.info/dists/feisty-i386/drivers/](http://repository.mumblyworld.info/dists/feisty-i386/drivers/), but to no avail.

When I check /lib/modules/2.6.20-15-generic/extra, the acer_acpi.ko is there, but it does not accept modprobe. 

What is the problem ?!?!

---

### Post by purpzey on 2007-05-31
I've got the same exact symptoms as the posts above me. Specifically I have run all of the command described in the post directly above me. 

There seems to be a bug here, or at least a problem that is not, "just working."

Although I suspect, there are other people in the thread who know more than I perhaps they don't know how to fix this properly so the modprobe will go through. I just, can't help but think there that is a "broken pipe" or "missing link" somewhere, that a few lines of code wouldn't fix. ](*,)
[I]
Has anyone considering hitting up launchpad on this issue?[/I]

Of course, if anyone did get it working please post and let everyone know so we can all share the goodness.

Thanks all.

Acer 3050, w/ 4318(rev. 2)

---

### Post by project4 on 2007-07-01
Hi, thanks for the post... I got stuck at the step "make"... this is what I get:
Please help me... thanks!
================
13:05:16 (39.01 KB/s) - `acer_acpi-0.3.tar.gz.1' saved [16083/16083]

portos@portos:~/download$ tar zxvf acer_acpi-0.3.tar.gz
acer_acpi-0.3/
acer_acpi-0.3/NEWS
acer_acpi-0.3/Makefile
acer_acpi-0.3/README
acer_acpi-0.3/AUTHORS
acer_acpi-0.3/INSTALL
acer_acpi-0.3/acer_acpi.c
acer_acpi-0.3/COPYING
portos@portos:~/download$ cd acer_acpi-0.3
portos@portos:~/download/acer_acpi-0.3$ make
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/lib/modules/2.6.20-16-generic/build/include/linux/sched.h:1309: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.20-16-generic/build/include/linux/sched.h:1311: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:21,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /lib/modules/2.6.20-16-generic/build/include/acpi/platform/acenv.h:140,
                 from /lib/modules/2.6.20-16-generic/build/include/acpi/acpi.h:54,
                 from /lib/modules/2.6.20-16-generic/build/include/acpi/acpi_bus.h:31,
                 from /lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:30,
                 from acer_acpi.c:49:
/lib/modules/2.6.20-16-generic/build/include/acpi/platform/aclinux.h: In function ‘acpi_os_allocate’:
/lib/modules/2.6.20-16-generic/build/include/acpi/platform/aclinux.h:116: warning: implicit declaration of function ‘irqs_disabled’
In file included from acer_acpi.c:49:
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h: At top level:
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:69: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:69: warning: its scope is only this definition or declaration, which is probably not what you want
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:70: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:72: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:77: warning: ‘struct acpi_device’ declared inside parameter list
acer_acpi.c: In function ‘acpi_acerkeys_add’:
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:339: warning: implicit declaration of function ‘acpi_device_name’
acer_acpi.c:339: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:340: warning: implicit declaration of function ‘acpi_device_class’
acer_acpi.c:340: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:341: warning: implicit declaration of function ‘acpi_driver_data’
acer_acpi.c:341: error: invalid lvalue in assignment
acer_acpi.c: At top level:
acer_acpi.c:370: error: variable ‘acpi_acerkeys’ has initializer but incomplete type
acer_acpi.c:371: error: unknown field ‘name’ specified in initializer
acer_acpi.c:371: warning: excess elements in struct initializer
acer_acpi.c:371: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:372: error: unknown field ‘class’ specified in initializer
acer_acpi.c:372: warning: excess elements in struct initializer
acer_acpi.c:372: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:373: error: unknown field ‘ids’ specified in initializer
acer_acpi.c:373: warning: excess elements in struct initializer
acer_acpi.c:373: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:374: error: unknown field ‘ops’ specified in initializer
acer_acpi.c:374: error: extra brace group at end of initializer
acer_acpi.c:374: error: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:377: warning: excess elements in struct initializer
acer_acpi.c:377: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c: In function ‘acer_acpi_init’:
acer_acpi.c:387: error: ‘acpi_disabled’ undeclared (first use in this function)
acer_acpi.c:405: error: ‘acpi_root_dir’ undeclared (first use in this function)
acer_acpi.c:416: warning: implicit declaration of function ‘acpi_bus_register_driver’
acer_acpi.c: In function ‘acer_acpi_exit’:
acer_acpi.c:432: warning: implicit declaration of function ‘acpi_bus_unregister_driver’
make: *** [acer_acpi.o] Error 1
portos@portos:~/download/acer_acpi-0.3$ sudo make install
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:9,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/lib/modules/2.6.20-16-generic/build/include/linux/sched.h:1309: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.20-16-generic/build/include/linux/sched.h:1311: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:21,
                 from acer_acpi.c:41:
/lib/modules/2.6.20-16-generic/build/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /lib/modules/2.6.20-16-generic/build/include/acpi/platform/acenv.h:140,
                 from /lib/modules/2.6.20-16-generic/build/include/acpi/acpi.h:54,
                 from /lib/modules/2.6.20-16-generic/build/include/acpi/acpi_bus.h:31,
                 from /lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:30,
                 from acer_acpi.c:49:
/lib/modules/2.6.20-16-generic/build/include/acpi/platform/aclinux.h: In function ‘acpi_os_allocate’:
/lib/modules/2.6.20-16-generic/build/include/acpi/platform/aclinux.h:116: warning: implicit declaration of function ‘irqs_disabled’
In file included from acer_acpi.c:49:
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h: At top level:
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:69: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:69: warning: its scope is only this definition or declaration, which is probably not what you want
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:70: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:72: warning: ‘struct acpi_device’ declared inside parameter list
/lib/modules/2.6.20-16-generic/build/include/acpi/acpi_drivers.h:77: warning: ‘struct acpi_device’ declared inside parameter list
acer_acpi.c: In function ‘acpi_acerkeys_add’:
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:339: warning: implicit declaration of function ‘acpi_device_name’
acer_acpi.c:339: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:340: warning: implicit declaration of function ‘acpi_device_class’
acer_acpi.c:340: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:341: warning: implicit declaration of function ‘acpi_driver_data’
acer_acpi.c:341: error: invalid lvalue in assignment
acer_acpi.c: At top level:
acer_acpi.c:370: error: variable ‘acpi_acerkeys’ has initializer but incomplete type
acer_acpi.c:371: error: unknown field ‘name’ specified in initializer
acer_acpi.c:371: warning: excess elements in struct initializer
acer_acpi.c:371: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:372: error: unknown field ‘class’ specified in initializer
acer_acpi.c:372: warning: excess elements in struct initializer
acer_acpi.c:372: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:373: error: unknown field ‘ids’ specified in initializer
acer_acpi.c:373: warning: excess elements in struct initializer
acer_acpi.c:373: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:374: error: unknown field ‘ops’ specified in initializer
acer_acpi.c:374: error: extra brace group at end of initializer
acer_acpi.c:374: error: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:377: warning: excess elements in struct initializer
acer_acpi.c:377: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c: In function ‘acer_acpi_init’:
acer_acpi.c:387: error: ‘acpi_disabled’ undeclared (first use in this function)
acer_acpi.c:405: error: ‘acpi_root_dir’ undeclared (first use in this function)
acer_acpi.c:416: warning: implicit declaration of function ‘acpi_bus_register_driver’
acer_acpi.c: In function ‘acer_acpi_exit’:
acer_acpi.c:432: warning: implicit declaration of function ‘acpi_bus_unregister_driver’
make: *** [acer_acpi.o] Error 1
portos@portos:~/download/acer_acpi-0.3$ cd ../..
=================================

---

### Post by forsberg on 2007-07-09
I found this thread from here: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

...I have an Acer Aspire 3610.  Do I need to do steps #1 - #7 from the thread above BEFORE I do the steps in this thread?

---

### Post by forsberg on 2007-07-09
OK - i have gone ahead with the steps.  But when I do the modprobe acer_acpi I get the error

FATAL: Module acer_acpi not found

please help!

---

### Post by hardhu on 2007-07-26
On Gutsy Gibbon amd64 acer_acpi doesn't work; here's a copy of the report I made on the developer page
([http://code.google.com/p/aceracpi/issues/detail?id=7](http://code.google.com/p/aceracpi/issues/detail?id=7))

Hello,
I have been using acer_acpi on an Acer Aspire 5024 for two years without
problems on Debian and Ubuntu. Recently I moved to the development version
of Kubuntu (Gutsy Gibbon) whose latest kernel is 2.6.22-8-generic. Since
then I have this problem (both  with 0.3 and 0.6 releases of acer_acpi):
when I enable wireless (echo 1 > /proc/acpi/acer/wireless) cpu usage goes
to 100% (as reported by gkrellm) and notebook becomes almost totally
irresponsive; I have to wait several minutes to write on a terminal the
command to disable wireless (echo 0 > /proc/acpi/acer/wireless), but after
disabling it everything works properly and cpu consumption is at a normal
level.

Here's what dmesg says to me (with debug=2):

[ 2085.084977] acer_acpi: Acer Laptop ACPI Extras version 0.6
[ 2085.084986] acer_acpi: Detected ACER AMW0 interface
[ 2085.084989] acer_acpi: Doing \_SB_.AMW0.WMAB( 1, 1, [16-byte buffer] )
[ 2085.085279] acer_acpi:   Execution status: 0
[ 2085.085281] acer_acpi:   Result: 0 bytes
[ 2085.085284] acer_acpi:   Args: 0x00009610 0x00000000 0x00000000 0x00000000
[ 2085.086193] acer_acpi: Commandline args: mailled(0) wireless(0)
bluetooth(0) brightness(-1)
[ 2085.086198] acer_acpi: Doing \_SB_.AMW0.WMAB( 1, 1, [16-byte buffer] )
[ 2085.087853] acer_acpi:   Execution status: 0
[ 2085.087855] acer_acpi:   Result: 0 bytes
[ 2085.087858] acer_acpi:   Args: 0x00009610 0x00000031 0x8039192d 0xffffffff
[ 2085.087861] acer_acpi: Doing \_SB_.AMW0.WMAB( 1, 1, [16-byte buffer] )
[ 2085.091227] acer_acpi:   Execution status: 0
[ 2085.091229] acer_acpi:   Result: 0 bytes
[ 2085.091232] acer_acpi:   Args: 0x00009610 0x00000035 0x8039192d 0xffffffff
[ 2085.091235] acer_acpi: Doing \_SB_.AMW0.WMAB( 1, 1, [16-byte buffer] )
[ 2085.094546] acer_acpi:   Execution status: 0
[ 2085.094548] acer_acpi:   Result: 0 bytes
[ 2085.094551] acer_acpi:   Args: 0x00009610 0x00000034 0x8039192d 0xffffffff
[ 2095.477589] acer_acpi: Doing \_SB_.AMW0.WMAB( 1, 1, [16-byte buffer] )
[ 2095.480731] acer_acpi:   Execution status: 0
[ 2095.480733] acer_acpi:   Result: 0 bytes
[ 2095.480736] acer_acpi:   Args: 0x00009610 0x00000135 0x8029a4d5 0xffffffff
[ 2174.107592] acer_acpi: Doing \_SB_.AMW0.WMAB( 1, 1, [16-byte buffer] )
[ 2174.111052] acer_acpi:   Execution status: 0
[ 2174.111054] acer_acpi:   Result: 0 bytes
[ 2174.111058] acer_acpi:   Args: 0x00009610 0x00000035 0x8029a4d5 0xffffffff

---

### Post by hardhu on 2007-07-27
> **hardhu said:**
> On Gutsy Gibbon amd64 acer_acpi doesn't work; here's a copy of the report I made on the developer page
([http://code.google.com/p/aceracpi/issues/detail?id=7](http://code.google.com/p/aceracpi/issues/detail?id=7))



Update: after further investigation, I discovered that the problem is not acer_acpi related, but it depends on the version of ndiswrapper on Gutsy; in fact I have built frmo source ndiswrapper-1.47 and the problem has disappeared.

---

### Post by rohandhruva on 2007-08-15
I tried the new 0.7 release .. and it works ABSOLUTELY WONDERFUL on my Acer TravelMate 3260 .. Finally I got software brightness control for my laptop ! The bluetooth and wireless LEDs too are controllable from software now .. Hats off to the new acer_acpi developer ! He :guitar:

---

### Post by rickc on 2007-10-10
Sweet. Nice to see the light on...

Does this work with the 64 bit OS or just the 32?

(NOTE: just because you have a 32 bit cpu, doesn't mean you have a 32 bit OS, nor do you have to run one.) I would like to use a 64 bit OS, but still searchin for all the drivers 1st. (sound and wireless)

---

### Post by cathectic on 2007-10-16
[quote=rickc]Does this work with the 64 bit OS or just the 32?[/quote]Both. acer_acpi was actually started because the older acerhk couldn't be ported to 64 bit systems.

Since I develop acer_acpi  on a 64 bit system, I can guarantee you that:

A) It supports 64 bit
B) It will _always_ support 64 bit

---

### Post by mrukus on 2007-10-28
allright, i downloaded and extracted acer_acpi0.6 from another link on the forum, but people seemed to be having alot of luck with this. i download and extract the package fine, but when i enter make i get this response

mrukus@mrukus-laptop:~/download/acer_acpi-0.6$ make
No support for 2.4 series kernels

what do i do. i grabbed the .6 because the link on this post for the .3 isn't working

---

### Post by cathectic on 2007-10-31
> **mrukus said:**
> mrukus@mrukus-laptop:~/download/acer_acpi-0.6$ make
No support for 2.4 series kernels

acer_acpi 0.6 is ancient as well - please use the latest stable release (0.9.1). The problem you have is because of an incompatibility with older acer_acpi Makefile's and the version of Bash that *buntu uses - this was fixed back in acer_acpi 0.8.2.

---

### Post by mrukus on 2007-10-31
when i go to install and enter t emake command.....nothing happens. anybody know why?

---

### Post by mrukus on 2007-10-31
allright, i downloaded and installed teh up to date module, now when i go to enable it with teh echo comman i get these two results

```
mrukus@mrukus-laptop:~$ sudo echo "enabled: 1">/proc/acpi/acer/wireless
echo: write error: Invalid argument
```

and

```
mrukus@mrukus-laptop:~$ echo "enabled: 1">/proc/acpi/acer/wireless
bash: echo: write error: Invalid argument
enabled: 1
```

---

### Post by mrukus on 2007-10-31
anybody know what to do

---

### Post by harleyquine on 2007-11-01
I installed Ubuntu about three months ago and got the wireless working on that after a couple of hours. Now I've installed the same version of Ubuntu and I've been trying all day to get wireless to work.. no luck. My card doesn't appear in the networking box yet the OS knows it's there. I have all the drivers and things installed but the bloody thing just will not appear. I must have tried at least 10 guides and not one of them could solve the problem. The later versions of acer-acpi don't want to work on dapper (the deb files) when I try compiling them the make program just freezes or comes up with compiling errors. I've tried a four versions of acer-acpi 3, 6, 9 and 10 and not one of them gets past modprobe. I know i'm not a linux whizkid but I get by so why the hell is this so difficult?? I guess this'll teach me not to ever delete Ubuntu again. Anyhoo being without wireless isn't really an option for me cos we've got a few laptops here so if I can't get this working then I'll have to go back to stinky windows and I really.. really.. don't want to do that. Good luck everyone else and if anyone finds a way of doing it without throwing their laptops out the window and buying a desktop, don't hesitate to hit the reply button :confused:

---

### Post by nomarko on 2007-12-05
Go to this site on Google Code 
[http://code.google.com/p/acer-acpi-deb/]("http://code.google.com/p/acer-acpi-deb/")   and download the debian packages for the acer_acpi. On gutsy you need the acer-acpi_0.9.1+2.6.22-14.46-mumbly5_i386.deb. Install the package.

After that, you have to download the windows driver on the Acer website and install them with ndiswrapper. I installed version 1.9 from the repositories (both ndiswrapper-common and utils.

---

### Post by scoober on 2008-02-05
Hey all

Is there any progress on this.  I am also getting the message:

FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-15-generic/extra/acer_acpi.ko): No such device

Seems common to quite a few people.

NB - Unless I am missing something, there is no Deb package released at the site listed above

---

### Post by nomarko on 2008-02-13
It looks like you can put a line in your sources.list and install directly with apt-get. At least that is what I makeof the lines on the bottom...

---

### Post by rohandhruva on 2008-02-13
Note that acer-acpi has been integrated into the upstream linux kernel - [http://groups.google.com/group/aceracpi-announce/browse_thread/thread/76f2cb0e08c01c42](http://groups.google.com/group/aceracpi-announce/browse_thread/thread/76f2cb0e08c01c42)

Sadly it will be available from kernel 2.6.25 onwards, whereas Hardy will include 2.6.24. Hence I have filed this bug -- [https://bugs.launchpad.net/bugs/190677](https://bugs.launchpad.net/bugs/190677)

Please add your comments to the bug if you support it :)

---

### Post by Shadowfire on 2008-03-07
This is an update with acer_acpi-0.7 update.

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install build-essential
mkdir Acer
cd Acer
wget [http://aceracpi.googlecode.com/files/acer_acpi-0.7.tar.bz2](http://aceracpi.googlecode.com/files/acer_acpi-0.7.tar.bz2)
tar -xjf acer_acpi-0.7.tar.bz2
cd acer_acpi-0.7
make
sudo make install
sudo -s
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit 

Hope this helps...

---

### Post by sm4xas on 2008-03-24
Hi!

I had thesame problem as the people earlier written about, the key is to change on of the lines in the earlier post, instead of:

*echo "enabled: 1">/proc/acpi/acer/wireless*

it should be:

**echo "1">/proc/acpi/acer/wireless**

Works fine for me!

---

### Post by apolloxi on 2008-04-01
Can somebody please help me with a problem I'm having?

Every time I run the "sudo apt-get install linux-headers-`uname -r'", the command always encounters errors with "bcm43xx-cutter". Can someone tell me why this is, and how I can fix it? I am desperate to get wireless working on my Ubuntu. Any help would be appreciated.

---

### Post by apolloxi on 2008-04-04
Anyone, please?

---

### Post by ZinkAlkon on 2008-05-25
Hi there guys, first post ever, as noob as someone can be
This will be my second time trying to get this to work.

Acer Aspire 5043 WLMi with the Atheros Card

I did check every single post on this thread, and tried each one that applies to the issues that I've been having. Also installed (I guess) Mad wifi
Bad News, no Wifi, and I'm still stuck.
So far, I'm stuck in here:

> **ovimunt said:**
> 
Load the acer_acpi into memory and activate the wireless:
Code:

su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit




and here's what I get:

root@Zink-Book:/# cd /home/zink/download/acer_acpi-0.11.2root@Zink-Book:/home/zink/download/acer_acpi-0.11.2# make
make: Nothing to be done for `all'.
root@Zink-Book:/home/zink/download/acer_acpi-0.11.2# sudo make install
mkdir -p /lib/modules/2.6.20-16-generic/extra
cp -v wmi-acer.ko acer_acpi.ko /lib/modules/2.6.20-16-generic/extra/
`wmi-acer.ko' -> `/lib/modules/2.6.20-16-generic/extra/wmi-acer.ko'
`acer_acpi.ko' -> `/lib/modules/2.6.20-16-generic/extra/acer_acpi.ko'
depmod 2.6.20-16-generic -a
root@Zink-Book:/home/zink/download/acer_acpi-0.11.2# modprobe acer_acpi
root@Zink-Book:/home/zink/download/acer_acpi-0.11.2# modprobe acer_acpi.ko
FATAL: Module acer_acpi.ko not found.
root@Zink-Book:/home/zink/download/acer_acpi-0.11.2# cd ../..
root@Zink-Book:/home/zink# modprobe acer_acpi.ko
FATAL: Module acer_acpi.ko not found.
root@Zink-Book:/home/zink# modprobe acer_acpi

-------------
As you can see, due to the fact that the prev version of the acer acpi link was not working, I download it from the googledev link, and extract it there. After that, I'm pretty much lost


(warning, historic purposes only, maybe it will help)

I've previously installed Ubuntu 8.04 (64 bits v), dual boot with XP, got stuck in the same place (never asked for help, somehow my sudo pass got changed, and then while formatting again the ubuntu partition, the MBR got screwed up, long story short, almost ruined me.

Now, same laptop, (again, Acer Aspire 5043WLMi) but got the Ubuntu 7.04 Original CD from a pal. It did install smoothly, updated (208 updates downloaded). I was trying to figure out which version I have installed now (32 or 64 bits) already tried 
root@Zink-Book:/home/zink# cat /etc/issue
Ubuntu 7.04 \n \l

dunno if that could help
BTW, no XP now on my PC, all formatted into 3 partitions: 7 gb for the root, 2 for swap, rest /home

THXS in advance!

---

### Post by rohandhruva on 2008-05-25
From 8.04 onwards, acer-acpi is already integrated into the distribution itself - [https://bugs.launchpad.net/bugs/190677](https://bugs.launchpad.net/bugs/190677)

First, check whether you laptop is supported - [http://code.google.com/p/aceracpi/wiki/SupportedHardware](http://code.google.com/p/aceracpi/wiki/SupportedHardware)
The procedure to enable or disable wireless, bluetooth, etc has changed.
To read the status of a device (0=off, 1=on):
cat /proc/acpi/acer/{device}
or
cat /sys/devices/platform/acer_acpi/{device}

To enable a feature:
echo 1 > /proc/acpi/acer/{feature}
or
echo 1 > /sys/devices/platform/acer_acpi/{device}

To disable a feature:
echo 0 > /proc/acpi/acer/{feature}
echo 0 > /sys/devices/platform/acer_acpi/{device}

HTH :)

Rohan.

---

### Post by ZinkAlkon on 2008-05-25
Thanks for the quick response, I am now going trought the updating process, first to 7.10 (100/1043 and still downloading) and after that, I'll go to the 8.04 v or until I get the latest one.

Seems to be that it will help me at least getting the little orange light to light up as it is listed as "supported" under 5040 (b,d,3)

If you or anyone, by any chance, can give me a heads up on how to get my atheros wifi card to work after that, I'll be very grateful.

---

### Post by rohandhruva on 2008-05-25
Right, because it's listed as [c,d,3], means you can control the brightness, bluetooth etc from software side.

However, keep in mind that you will still require the proper drivers for your card - [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

To enable or disable the card, if you don't have a hardware switch, do 

echo 1 > /proc/acpi/acer/wireless

NetworkManager should take care of the rest.

---

### Post by ZinkAlkon on 2008-05-25
My girlfriend states "que buena onda!" (she's been by my side all the way, and seeing how easy it was... she started giving me "the look".)

 Regardless the anecdotic time, thanks again, I'm reading the docs about MadWIFI and hopefully will run smoothly, definitly will ask for help if I need to.

---

### Post by ZinkAlkon on 2008-05-26
MmmmI do have a hardware enabler button at the front of my laptop, thought is not coming on.

Tried what you suggested me to do... here's what I got

zink@Zink-Book:~$ echo 1 > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied
zink@Zink-Book:~$ sudo echo 1 > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied
zink@Zink-Book:~$ cat /proc/acpi/acer/wireless
0
zink@Zink-Book:~$ echo 1 > /proc/acpi/acer/wifi
bash: /proc/acpi/acer/wifi: No such file or directory
zink@Zink-Book:~$ echo 1 > /proc/acpi/acer/wireless
bash: /proc/acpi/acer/wireless: Permission denied
zink@Zink-Book:~$ 

mmm HELP! plz? :D

---

### Post by rohandhruva on 2008-05-27
Two options:

1) Type 'sudo -i' to become root first, and then type that command - echo 1 > /proc/acpi/acer/wireless

2) As normal user, type 'echo 1 | sudo tee /proc/acpi/acer/wireless'

Both methods should work equally fine, but in the first one remember to logout and give up root after executing the command.

---

### Post by ZinkAlkon on 2008-05-27
Whooooa! orange light up and running, tried both options, first the second one, did nothing. first option worked perfectly fine, and I did exit root mode.

  Now I guess everything is up to the Madwifi driver... wish me luck!

Thxs again for the tips!

---

### Post by mtantawy on 2008-05-28
So, everything worked fine with me and the lamp is ON but i still see no wireless access points??

also, how can i reach the window through which i can navigate through available connections??and ofcourse adjust settings?

that little icon in the panel is called wired connections, so where is the wireless one??

Thanks in advance

Mahmoud Tantawy

---

### Post by kioftes on 2008-07-27
Hi!! No bluetooth here...here's the output of dmesg | grep Bluetooth:

[   48.290295] Bluetooth: Core ver 2.11
[   48.290638] Bluetooth: HCI device and connection manager initialized
[   48.290642] Bluetooth: HCI socket layer initialized
[   48.326540] Bluetooth: L2CAP ver 2.9
[   48.326751] Bluetooth: L2CAP socket layer initialized
[   48.405715] Bluetooth: RFCOMM socket layer initialized
[   48.405733] Bluetooth: RFCOMM TTY layer initialized
[   48.405736] Bluetooth: RFCOMM ver 1.8


However no bluetooth device shown at /sys/devices/platform/acer_acpi/devices and bluetooth led is always off...never managed to make it work on neither version of ubuntu from edgy up to hardy...wireless howevere worked out of the box with fw-cutter

---

### Post by MiguelCosta on 2008-08-27
My driver is working...but only when I reb00t the computer..when I turn it on the first time the led turns on but no wireless!

---

### Post by dtk1985 on 2008-11-22
Hi

I'm running Ubuntu 8.04 on an Acer Travelmate 4401LMi laptop. Acer_acpi comes with the default kernel, i've loaded it already with "modprobe acer_acpi" and when i want to activate the wireless with the following command i get this error:```
dtk@qqriq:~$ sudo echo "enabled: 1">/proc/acpi/acer/wireless
[sudo] password for dtk: 
echo: write error: Invalid argument
dtk@qqriq:~$ 

```The file exists, i can open it with a text editor (but i can't modify it!), rights are 777. I tried the same by logging in as root ("sudo -i") but it didn't work.

Edit: Problem solved, i've updated to 8.10 and i'm using acer-wmi module now.

---

### Post by stephen_b on 2010-04-17
no wireless

I installed Ubuntu 9.10 on acer aspire 3680 with broadcom 4311 card which is reported as being supported. the driver is installed, but wireless does not work.

pls help:

truncated from lshw -C network

product: BCM4311 802.11b/g WLAN
configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
logical name: eth2

I can see the device in Network tools where it says state Active. the IPv6 address is sth in hex and the IPv4 is 0.0.0.0 (so it does not have it). I am using Bell wireless with DHCP.

Thank you
Stephen

---

