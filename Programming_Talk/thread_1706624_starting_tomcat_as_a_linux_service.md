---
title: "starting tomcat as a linux service"
date: 2011-03-14
forum: Programming Talk
---

### Post by ensienne on 2011-03-14
hello,

I have a problem with the launching of tomcat as linux service.
I use ubuntu 10.10 and tomcat6.
The steps that I have followed are:
1. Install tomcat.
2. create /etc/ini.d/tomcat file
3. change the access to this file
4. chkconfig --add tomcat
insserv: warning: script 'K01tomcat' missing LSB tags and overrides
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'tomcat' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-splash'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-splash'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `gdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `gdm'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-mixer-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-mixer-save'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-stop'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-stop'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-log'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-log'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: fopen(.depend.stop): Permission denied
tomcat                    0:off  1:off  2
:confused: please how can resolve that

---

### Post by Steve White on 2011-05-17
This is annoying me too.

I also spent a fair amount of time trying to discover how to do the simplest thing with upstart, only to find that a lot of other people are asking the same questions, and also getting no useful answer.

Come on guys!  The simplest thing:

For a given service, how does an admin
* start it
* stop it
* restart it
* control whether it starts at boot or not

In the case of tomcat6, the process is running, but
   initctl list 
shows nothing of the kind... and nothing I recognize.

What is the proper upstart way to stop this upstart-ized tomcat6?

Could we get some informed input here?

---

