---
title: "ZRAM not starting at boot on Lubuntu 12.10"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by Treeant34 on 2013-05-30
Morning:

I recently upgraded from 12.04 to 12.10 in Lubuntu and everything went smoothly except ZRAM no longer initializes at boot. "sudo start zramswap" in a terminal will get it going but who wants to do that every time you boot up. I went into Synaptic and selected zram-config and zramswap-enabler to reinstall figuring something got borked during the upgrade.

I received this warning window: E: zram-config: subprocess installed post-installation script returned error exit status 1

The Synaptic log showed this:

Selecting previously unselected package zramswap-enabler.
(Reading database ... 113959 files and directories currently installed.)
Unpacking zramswap-enabler (from .../zramswap-enabler_0.2.1-0~25~precise1_all.deb) ...
Selecting previously unselected package zram-config.
Unpacking zram-config (from .../zram-config_0.1_all.deb) ...
Processing triggers for ureadahead ...
Setting up zramswap-enabler (0.2.1-0~25~precise1) ...
zramswap start/running
Setting up zram-config (0.1) ...
start: Job failed to start
invoke-rc.d: initscript zram-config, action "start" failed.
dpkg: error processing zram-config (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zram-config
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up zram-config (0.1) ...
zram-config start/running

zram was working until reboot and then back to the "won't initialize during boot thing"

Anyone have any thoughts on this?

If I purge zram-config and zramswap-enabler, is there anything else left behind that I will need to manually remove before trying a re-install and how would I go about finding said lingering zram crap?

I actually sent an email to Sergey but he said it wasn't his script...

Thanks in advance

T

PS 

After purging zram-config and zramswap-enabler, I ran a search via terminal and was given this (thanks to Mariane for the search syntax):

********@*************:~$ cd /
********@*************:/$ sudo find ./ -name *zram*
[sudo] password for ********: 
./etc/rc5.d/S20zramswap
./etc/rc0.d/K20zramswap
./etc/apt/sources.list.d/shnatsel-zram-precise.list.save
./etc/apt/sources.list.d/shnatsel-zram-precise.list
./etc/rc2.d/S20zramswap
./etc/rc1.d/K20zramswap
./etc/rc4.d/S20zramswap
./etc/rc6.d/K20zramswap
./etc/rc3.d/S20zramswap
./var/log/upstart/zram-config.log
./var/log/upstart/zram-config.log.1.gz
./var/log/upstart/zramswap.log.1.gz
./var/log/upstart/zramswap.log
./var/crash/zram-config.0.crash
./var/lib/apt/lists/ppa.launchpad.net_shnatsel_zram_ubuntu_dists_precise_Release
./var/lib/apt/lists/ppa.launchpad.net_shnatsel_zram_ubuntu_dists_precise_Release.gpg
./var/lib/apt/lists/ppa.launchpad.net_shnatsel_zram_ubuntu_dists_precise_main_binary-i386_Packages
./var/lib/update-rc.d/zramswap
./var/cache/apt/archives/zramswap-enabler_0.2.1-0~25~precise1_all.deb
./var/cache/apt/archives/zram-config_0.1_all.deb
./usr/src/linux-headers-3.2.0-44-generic/include/config/zram.h
./usr/src/linux-headers-3.2.0-44/drivers/staging/zram
./lib/modules/3.2.0-44-generic/kernel/drivers/staging/zram
./lib/modules/3.2.0-44-generic/kernel/drivers/staging/zram/zram.ko
********@*************:/$ 

Is there anything in that list that someone thinks needs to be removed prior to trying to reinstall zram again?

Cheers

---

### Post by gordintoronto on 2013-05-31
Do you have a ppa for zram? According to everything I can find, beginning with Ubuntu 12.04, the only thing you need is zram-config. I would boot without zram, completely remove everything to do with zram, remove any extraneous ppa, and install zram-config.

---

