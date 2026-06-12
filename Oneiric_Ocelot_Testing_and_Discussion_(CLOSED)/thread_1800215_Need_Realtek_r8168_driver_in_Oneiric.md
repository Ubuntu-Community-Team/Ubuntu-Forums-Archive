---
title: "Need Realtek r8168 driver in Oneiric"
date: 2011-07-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-07-08
Ok, I know how to solve my problem, but I cannot get it to work. Natty and Oneiric load the wrong driver (r8169) for my Realtek NIC. The solution in Maverick is to download the correct r8168 driver from Realtek Taiwan, build the module, and install it into the kernel.

However, the driver states that it is for kernels 2.4 or 2.6. Of course, Oneiric has moved along to the 3.0 kernel. I cannot get the supplied Makefile to install the module in Oneiric. I tried to modify the Makefile to do so, but I got the same error as I did without the modification.

Here is the supplied Makefile:

```

# FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
# more details.
# 
# You should have received a copy of the GNU General Public License along with
# this program; if not, see <http://www.gnu.org/licenses/>.
# 
# Author:
# Realtek NIC software team <nicfae@realtek.com>
# No. 2, Innovation Road II, Hsinchu Science Park, Hsinchu 300, Taiwan
# 
################################################################################

################################################################################
# This product is covered by one or more of the following patents:
# US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
################################################################################

KVER        := $(shell uname -r)
KDIR        := /lib/modules/$(KVER)/build
KMISC        := /lib/modules/$(KVER)/kernel/drivers/net/
KEXT        := $(shell echo $(KVER) | sed -ne 's/^2\.[567]\..*/k/p')o
KFLAG        := 2$(shell echo $(KVER) | sed -ne 's/^2\.[4]\..*/4/p')x

EXTRA_CFLAGS += -DCONFIG_R8168_NAPI
EXTRA_CFLAGS += -DCONFIG_R8168_VLAN

modules:
ifeq ($(KFLAG),24x)
    $(MAKE) -f Makefile_linux24x
else
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD)/src modules
    strip --strip-debug r8168.$(KEXT)
endif

clean:
    rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order


install:
    install -m 744 -c r8168.$(KEXT) $(KMISC)

ifneq ($(KFLAG),24x)
obj-m += r8168.o
r8168-objs :=  r8168_n.o r8168_asf.o rtl_eeprom.o rtltool.o
endif#($(KFLAG),24x)

```

I attempted to modify it to allow kernel 3.0 by changing line # 36 to:

```

KEXT            := $(shell echo $(KVER) | sed -ne 's/^3\.[0567]\..*/k/p')o

```

As I said, it made no difference.

Can anyone help me with this?

Thanks,
Tim

---

### Post by Harry33 on 2011-07-08
> **ratcheer said:**
> Ok, I know how to solve my problem, but I cannot get it to work. Natty and Oneiric load the wrong driver (r8169) for my Realtek NIC. The solution in Maverick is to download the correct r8168 driver from Realtek Taiwan, build the module, and install it into the kernel.

However, the driver states that it is for kernels 2.4 or 2.6. Of course, Oneiric has moved along to the 3.0 kernel. I cannot get the supplied Makefile to install the module in Oneiric. I tried to modify the Makefile to do so, but I got the same error as I did without the modification.
...
As I said, it made no difference.
Can anyone help me with this?

Thanks,
Tim

I have a Gigabyte Mobo (GA-MA790XT-UD4P) with Realtek 8111DL Gigabit Ethernet.
It works well with the 8169 driver.
Occasionally the net card gets stucked (not resetting correctly).
A complete power off helps.

---

### Post by ratcheer on 2011-07-08
Thanks. However, neither Natty nor Oneiric work with the r8169 driver on my system. It does not get stuck occasionally, it just does not work. I had to install Ubuntu without a network connection.

Tim

---

### Post by lucazade on 2011-07-08
is there any evidence of the issue using 8169, like malformed packets or CRC errors that fill the buffer? (i.e looking at dmesg and ifconfig)
ethtool is good for net driver diagnostic, in case you might need... anyway i'll give a look at makefile to see if i can help.

---

### Post by ronacc on 2011-07-08
I think whats causing the problem is that the makefile don't like the symlinks in  /usr/src/3.0-3-generic and /lib/modules/3.0-3-generic/build , it seems not to be finding the files , its looking in the right place .

---

### Post by ratcheer on 2011-07-08
Here is the output from the make script:

```

Check old driver and unload it.
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
FATAL: Module r8168 not found.
Completed.

```However, module r8168.ko is created in the ./src directory. I tried manually copying it to /lib/modules/3.0-3-generic/kernel/drivers/net and running modprobe, but that didn't work, either.

Tim

---

### Post by ratcheer on 2011-07-19
> **Harry33 said:**
> I have a Gigabyte Mobo (GA-MA790XT-UD4P) with Realtek 8111DL Gigabit Ethernet.
It works well with the 8169 driver.
Occasionally the net card gets stucked (not resetting correctly).
A complete power off helps.

I apologize, Harry33. After researching for days on the issue of r8169 vs r8168 drivers, I saw enough posts with the same recommendation that I decided to try it. It worked, so I am now successfully using Oneiric with the r8169 driver and a seemingly good ethernet connection.

This means completely unplugging the PC from AC power for several minutes.

Tim

---

### Post by Harry33 on 2011-07-19
> **ratcheer said:**
> I apologize, Harry33. After researching for days on the issue of r8169 vs r8168 drivers, I saw enough posts with the same recommendation that I decided to try it. It worked, so I am now successfully using Oneiric with the r8169 driver and a seemingly good ethernet connection.

This means completely unplugging the PC from AC power for several minutes.

Tim

Well Tim, no need to apologize.
Good that the ethernet is working OK now with your Realtek NIC.

---

### Post by ratcheer on 2011-07-20
Well, not so fast. After a single reboot, the ethernet connection was unusable, again. I certainly don't want to have to unplug and replug the machine every time I reboot it.

Tim

---

### Post by devil103 on 2011-07-25
Any solutions? I'm facing thrbe same problem with kernel 3.0. same makefile error.

---

### Post by ratcheer on 2011-07-25
> **devil103 said:**
> Any solutions? I'm facing thrbe same problem with kernel 3.0. same makefile error.

I haven't seen anything yet. When I run Oneiric, I have to go strictly with wireless.

Tim

---

### Post by AndresChort on 2011-08-28
GOT IT !!
The problem was indeed the makefile. Here is what i changed:

(I'm using the latest version r8168-8.025.00)

./src/Makefile

Line 36: So the script creates the file with the correct extension
```
KEXT        := $(shell echo $(KVER) | sed -ne 's/^3\.[0567]\..*/k/p')o
```Line 47: Added "src" to the path. For some reason strip couldn't find the file.
```
strip --strip-debug src/r8168.$(KEXT)
```I didn't use the autorun.sh script

Run this as root (sudo su) (working directory = folder containing autorun.sh, src folder, etc):
```

make -f src/Makefile
install -m 744 -c src/r8168.ko /lib/modules/3.0.0-7-generic/kernel/drivers/net/
cd src
depmod -a
modprobe r8168
reboot

```And now all works fine. I'm posting this from my Oneiric box :D

I tryed to attach the makefile but the uploading tool said "Invalid File"

Hope it helps!

---

### Post by ratcheer on 2011-08-28
Thanks, AndresChort. I will try that as soon as I get a chance.

Tim

---

### Post by ratcheer on 2011-08-30
AndresChort, I finally tried your instructions and they did not work for me:

```
sudo make -f src/Makefile
make -C /lib/modules/3.0.0-9-generic/build SUBDIRS=/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-9-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[2]: *** No rule to make target `/src/Makefile'.  Stop.
make[1]: *** [_module_/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-9-generic'
make: *** [modules] Error 2
```It seems to be putting a "/" before src. I put it exactly the way you did in Makefile, with no leading "/"

Tim

---

### Post by AndresChort on 2011-08-31
mmm weird
did you tried adding a full path instead of just "src"? (with or without a leading "/")

Later I realized that on reboot Ubuntu kept loading the r8169 module instead of the r8168

I had to run this command:
```
sudo update-initramfs -u
```

Now it load both modules, I added this to /etc/modprobe.d/blacklist.conf
```
blacklist r8169
```

But Ubuntu keeps loading that module on boot.

Andres.

---

### Post by ratcheer on 2011-08-31
Now this is just crazy. I tried it with the full path to src, but that failed, too. So, for no good reason, I restored the original src/Makefile and ran autorun.sh. It worked! It has failed a hundred times before, but this time it worked. I have no idea how this happened.

```
    Kernel driver in use: r8168
    Kernel modules: r8168

```

Tim

---

### Post by ratcheer on 2011-09-01
> **ratcheer said:**
>  I have no idea how this happened.
 
 
Maybe it has something to do with all the updates to Ubuntu over the past few weeks.
 
Tim

---

### Post by pt123 on 2011-09-01
> **AndresChort said:**
> GOT IT !!
The problem was indeed the makefile. Here is what i changed:

```
KEXT        := $(shell echo $(KVER) | sed -ne 's/^3\.[0567]\..*/k/p')o
```Line 47: Added "src" to the path. For some reason strip couldn't find the file.


Thanks a lot AndresChort my network connection works fine now. 

I have added it as issue 
[http://code.google.com/p/r8168/issues/detail?id=5](http://code.google.com/p/r8168/issues/detail?id=5)

Is there a reason why the problem with the r8169 drivers has not been fixed, the bug appears as early as 2009.

---

### Post by ratcheer on 2011-09-02
> **pt123 said:**
>  
Is there a reason why the problem with the r8169 drivers has not been fixed, the bug appears as early as 2009.
 
Someone pointed me to a document that said it would be fixed in kernel 3.1. I hope they are right.
 
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=70090424e59652c4b2e777b533cc23134b176b83](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=70090424e59652c4b2e777b533cc23134b176b83)
 
Tim

---

### Post by AndresChort on 2011-09-02
> **pt123 said:**
> 
I have added it as issue 
[http://code.google.com/p/r8168/issues/detail?id=5](http://code.google.com/p/r8168/issues/detail?id=5)


> **ratcheer said:**
> Someone pointed me to a document that said it would be fixed in kernel 3.1. I hope they are right.


Great! let's wait and see if it gets fixed.

There's something I don't understand. Which is the right module? According to Realtek it's r8168 but linux uses r8169, which doesn't work (it's a bug?)

Now my box loads both modules and after some minutes I have to remove both of them and add r8168 back to get it working. I have to do this on every reboot. Anybody knows how to blacklist r8169 and prevent it from loading? I've already added it to /etc/modprobe.d/blacklist.conf with no results.

Or maybe I'll just wait for 3.1

---

### Post by ratcheer on 2011-09-02
Here is how I did it and I have only r8168 loaded:

1) Besides having "blacklist r8169" in blacklist.conf, I also have "r8168" in /etc/initramfs-tools/modules.

2) sudo depmod -a

3) sudo update-initramfs -v -u -k `uname -r`

4) Reboot

Of course, every time a new kernel is released, all this stuff has to be redone. I hope this helps.

Tim

PS - Note that in the step 3 command, those are not single quote marks, they are grave accents. That is usually the key to the left of the 1 (one) key.

---

### Post by AndresChort on 2011-09-03
> **ratcheer said:**
> Here is how I did it and I have only r8168 loaded:

1) Besides having "blacklist r8169" in blacklist.conf, I also have "r8168" in /etc/initramfs-tools/modules.

2) sudo depmod -a

3) sudo update-initramfs -v -u -k `uname -r`

4) Reboot


Thanks Tim, that did the trick! :)

---

### Post by stombi on 2011-10-03
Actually you just have to replace the KEXT line like this for example :  

> -KEXT        := $(shell echo $(KVER) | sed -ne 's/^2\.[567]\..*/k/p')o 
+KEXT        := $(shell echo $(KVER) | sed -ne 's/^[23]\.[01567]\..*/k/p')o  

there is nothing wrong with the src path as long as you run ./autorun.sh

I also added the comment here [http://code.google.com/p/r8168/issues/detail?id=5](http://code.google.com/p/r8168/issues/detail?id=5)

---

