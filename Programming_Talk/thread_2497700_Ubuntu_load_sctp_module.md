---
title: "Ubuntu load sctp module"
date: 2024-05-15
forum: Programming Talk
---

### Post by lthrl on 2024-05-15
[COLOR=#333F48][FONT=Arial]Hello,[/FONT][/COLOR]
[COLOR=#333F48][FONT=Arial]I have the same problem with the **SCTP protocol** on an LX2160 board.
Does anyone know how to install and activate the SCTP protocol?

**Here are the errors:**
[SCTP] Socket creation failed: Protocol not supported
[SCTP] could not open socket, no SCTP connection established
[SCTP] Socket creation failed: Protocol not supported
[SCTP] could not open server socket, no SCTP listener active
[SCTP] Failed to create new SCTP listener

**Here is more information:**[/FONT][/COLOR]
[COLOR=#333F48][FONT=Arial]$ checksctp
checksctp: Protocol not supported[/FONT][/COLOR]
[COLOR=#333F48][FONT=Arial]$ lsmod | grep sctp
(nothing)[/FONT][/COLOR]
[COLOR=#333F48][FONT=Arial]$ zcat /proc/config.gz | grep SCTP
CONFIG_NF_CT_PROTO_SCTP=y
# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
# CONFIG_IP_VS_PROTO_SCTP is not set
# CONFIG_IP_SCTP is not set

I tried to retrieve a sctp.ko file and then load it into the linux kernel with the command: sudo insmod -f ./sctp.ko
When I loaded it, the board rebooted with no new features.
The kernel version for which this module was compiled is 5.10.35-00078-g4c69857cb565 while the one I'm on is 5.10.35-00067-g241f7241ce2.

$ sudo modprobe sctp.ko
modprobe: FATAL: Module sctp.ko not found in directory /lib/modules/5.10.35-00067-g241f7241ce2

$ sudo modprobe sctp
(nothing, but nothing has changed)

$ ls /lib/modules/5.10.35-00067-g241f7241ce2
build
modules.alias                    modules.builtin
modules.builtin.bin             modules.dep
modules.devname             modules.softdep
modules.symbols.bin         kernel
modules.alias.bin              modules.builtin.alias.bin
modules.builtin.modinfo    modules.dep.bin modules.order modules.symbols sctp.ko source

Thanks in advance for your help ![/FONT][/COLOR]

---

### Post by Crafty Kisses on 2024-05-22
So first this should go without saying, ensure that your kernel is configured to support SCTP. Based on your provided configuration, it seems that the ```
CONFIG_IP_SCTP
``` Option is not set. This option is crucial for SCTP support. You'll need to install some necessary packages:

```
sudo apt-get update
sudo apt-get install build-essential libncurses-dev bison flex libssl-dev libelf-dev

```

Download the appropriate kernel source for your version. Replace 5.10.35 with your exact version if necessary:

```
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.10.35.tar.xz
tar -xf linux-5.10.35.tar.xz
cd linux-5.10.35

```

Copy your current kernel configuration and open the configuration menu:

```
cp /boot/config-$(uname -r) .config
make menuconfig

```

Navigate to Networking support -> Networking options -> The SCTP protocol and enable it ```
(CONFIG_IP_SCTP=y)
``` Next you need to compile and install the kernel:

```

make -j$(nproc)
sudo make modules_install
sudo make install

```

Would also be a good idea to update GRUB, the bootloader. So next pdate your bootloader to use the new kernel. This step may vary depending on your bootloader (e.g., GRUB):

```
sudo update-grub
```

Then reboot, and see if the SCTP module works.

---

