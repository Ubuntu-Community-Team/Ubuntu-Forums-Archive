---
title: "HOWTO: Laptop profile management like SCPM"
date: 2006-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by mrjyg on 2006-11-10
One thing I liked a lot about SuSE Linux is its SCPM configuration profile management component.  As soon as I switched to Ubuntu Edgy on my Dell Inspiron 700m laptop, I looked for something similar.  I didn't expect to find anything as good as SCPM, but I was not expecting nil either :(

Instead of spending the time to port the basic SCPM components over, I just implemented something simple.

My goals:
- Control office / home network profile switching.
- Control multihead / single display xorg.conf switching.
- Do this with a grub boot menu, but allow fast network profile switching w/o a reboot (so that I can 'dock' my laptop to an ethernet cable when needed).

Basic approach:
- Add kernel boot command line args which will be present in /proc/cmdline, for the profile switcher script to read at init time.
- Create multiple copies of slightly different configuration files, with extensions denoting the profile it's for.
- Have the profile switcher copy the right set of configuration files into place during init time.
- Allow the profile switcher to be run w/ additional arguments to override  /proc/cmdline (runtime switch of profile).

Issues addressed:
1. The pathname of the new init script, /etc/init.d/profile-switcher (source code below), must be added to /etc/readahead/boot file.

2. When switching between wired and wireless NICs, Ubuntu Edgy seems to "remember" the old interface used before the reboot.  Need to quell this memory effect, by resetting the configuration files before shutdown.  This resets the configuration files, and prevents udev / hardware probe startups (which happens very early in the game) from activating network configuration w/ the old configuration setting (e.g. the /etc/udev/rules.d/85-ifupdown.rules).  Specifically, the /etc/network/interfaces file must be restored at shutdown time to just include the lo interface.
   Configuration files used for the reset operation should be created, with the .DEFAULT suffix per my profile-switcher script.

Installation:
- Select a directory path where you store profile configuration files.  In my example, I used /data/system/profile.d ... you can use other directory pathnames (but make sure the script's _PROFILE_DIR is adjusted accordinly).  I just used this pathname because of my habit to keep all system modification data under /data/system/...

- Create /etc/init.d/profile-switcher script, and make sure it's executable etc., e.g.
  chmod 755 /etc/init.d/profile-switcher
  chown root:root /etc/init.d/profile-switcher
  echo "/etc/init.d/profile-switcher" >> /etc/readahead/boot

- Link it up to rcS.d, rc0.d, rc6.d:
  ln -s ../init.d/profile-switcher /etc/rcS.d/S38profile-switcher
  ln -s ../init.d/profile-switcher /etc/rc0.d/S38profile-switcher
  ln -s ../init.d/profile-switcher /etc/rc6.d/S38profile-switcher

  S38 in rcS.d places this script startup right before network startup.
  S38 in rc0.d / rc6.d places this script stop right before filesystems are to be un-mounted.

- Edit /boot/grub/menu.lst to include the custom boot args:
  + PROFILE=<profile>
    The value of this defines the location and network type.
    For location, just decide on the ones appropriate to you, e.g. I used Home and Work.
    For network type, the script hardcodes it to Eth for ethernet, and Wlan for wireless network.  This is because the script tries to cut apart the PROFILE= value into location and network type fields, to help reduce the number of profiles you'd need to create.  For example, given Home vs. Work and Eth vs. Wlan:
    I can create these files:
      <_PROFILE_DIR>/etc/resolv.conf.DEFAULT
      <_PROFILE_DIR>/etc/resolv.conf.Home
      <_PROFILE_DIR>/etc/resolv.conf.Work
      <_PROFILE_DIR>/etc/network/interfaces.DEFAULT
      <_PROFILE_DIR>/etc/network/interfaces.HomeEth
      <_PROFILE_DIR>/etc/network/interfaces.HomeWlan
      <_PROFILE_DIR>/etc/network/interfaces.Work
    When a HomeEth PROFILE is given, .../resolv.conf.Home would match this profile, instead of having to create two identical files resolv.conf.HomeEth and resolv.conf.HomeWlan ...
  + VIDEO=
    The value here determines whether it's single LCD display or external display + LCD display, e.g. I used CRTLFP and LFP (following the pipe names supported by the i810 driver).
    I used the following set of xorg.conf profile files:
    <_PROFILE_DIR>/etc/xorg.conf.DEFAULT
    <_PROFILE_DIR>/etc/xorg.conf.LFP
    <_PROFILE_DIR>/etc/xorg.conf.HomeCRTLFP
    <_PROFILE_DIR>/etc/xorg.conf.WorkCRTLFP
    Again, because of the split of location and network type, reduction of number of files like the above is possible.  Take a look at the script where the fallback suffix search is implemented:
   <loc><net><vid> <loc><net> <loc><vid> <loc> <net> <vid> DEFAULT
  + Here is what I did to /boot/grub/menu.lst:
    * Change default boot option from 0 to 1, so that we don't step onto Ubuntu controlled entry:
default                1
    * Set timeout to be really large (instead of 3 seconds), so that you get a chance to select the profile to boot into:
timeout                99999
    * Do not hide grub menu, comment out the hiddenmenu line:
#hiddenmenu
    * Add additional alternative boot entries in front of the recovery mode entry, by inserting '# altoptoins=' lines in front of the '# altoptions=(recovery mode) single' line, e.g. I use the following:
# altoptions=(Work LFP) quiet splash PROFILE=WorkEth VIDEO=LFP
# altoptions=(Home Ethernet CRT+LFP) quiet splash PROFILE=HomeEth VIDEO=CRTLFP
# altoptions=(Home Ethernet LFP) quiet splash PROFILE=HomeEth VIDEO=LFP
# altoptions=(Home Wifi CRT+LFP) quiet splash PROFILE=HomeWlan VIDEO=CRTLFP

+# altoptions=(Home Wifi LFP) lapic pci=assign-busses quiet splash PROFILE=HomeW
lan VIDEO=LFP

- Effect the grub boot menu change:
  + update-grub
  You will see that additional boot entries are created out of the above commented out altoptions entries.

- Reboot and enjoy :)

The profile configurations I use:
# tree /data/system/profile.d/
/data/system/profile.d/
`-- etc
    |-- X11
    |   |-- xorg.conf.DEFAULT
    |   |-- xorg.conf.HomeCRTLFP
    |   |-- xorg.conf.LFP
    |   `-- xorg.conf.WorkCRTLFP
    |-- default
    |   |-- ntpdate.DEFAULT
    |   |-- ntpdate.Home
    |   `-- ntpdate.Work
    |-- network
    |   |-- interfaces.DEFAULT
    |   |-- interfaces.HomeEth
    |   |-- interfaces.HomeWlan
    |   `-- interfaces.WorkEth
    |-- resolv.conf.DEFAULT
    |-- resolv.conf.Home
    `-- resolv.conf.Work

4 directories, 14 files

The /etc/init.d/profile-switcher script:
#!/bin/sh

### BEGIN INIT INFO
# Provides:             profile-switcher
# Default-Start:        S
# Default-Stop:         0 6
# Short-Description:    Instantiate/reset network and X-window configurations
# Description:          Uses kernel boot command line or script
#                       command line PROFILE / VIDEO mnemonics, and
#                       copies profile-specific configuration settings
#                       upon start, or resets these profiles upon stop.
### END INIT INFO

PATH=/bin:/usr/bin:/sbin:/usr/sbin

. /lib/lsb/init-functions

_PROFILE_DIR=/data/system/profile.d
[ ! -d ${_PROFILE_DIR} ] && exit 0

start_stop_profile_switcher () {
    _PROFILE_SIGS=$1

    _dstpnames=DUMMY
    _files=`find ${_PROFILE_DIR} -type f`
    for _sig in ${_PROFILE_SIGS}; do
        for _srcpname in ${_files}; do
            _dstpname=${_srcpname%.${_sig}}
            if [ "${_dstpname}" != "${_srcpname}" ]; then
                for _seenfile in ${_dstpnames}; do
                    if [ "${_dstpname}" = "${_seenfile}" ]; then
                        _dstpname=
                        break
                    fi
                done
                if [ -n "${_dstpname}" ]; then
                    mkdir -p `dirname ${_dstpname#${_PROFILE_DIR}}`
                    cp -fp ${_srcpname} ${_dstpname#${_PROFILE_DIR}}
                    _dstpnames="${_dstpnames} ${_dstpname}"
                fi
            fi
        done
    done
}

case "$1" in
start|restart|force-reload)
    # Accept optional [PROFILE [VIDEO]] mnemonics from command line.
    #
    [ $# -ge 2 ] && _prof=$2
    [ $# -ge 3 ] && _vid=$3     

    # Get boot-time PROFILE / VIDEO mnemonics.
    #
    read _cmdline < /proc/cmdline 2>/dev/null
    for _token in ${_cmdline}; do
        case ${_token} in
        PROFILE=*)
            eval ${_token}
            [ -z "${_prof}" ] && _prof=${PROFILE}
            ;;
        VIDEO=*)
            eval ${_token}
            [ -z "${_vid}" ] && _vid=${VIDEO}
            ;;
        esac
    done

    log_action_begin_msg "Activating profile ${_prof} ${_vid}"

    _ploc=
    _pnet=
    if [ -n "${_prof}" ]; then
        for _net in Eth Wlan; do
            case "${_prof}" in
            *${_net})
                _ploc=${_prof%${_net}}
                _pnet=${_net}
                ;;
            esac
            [ -n "${_pnet}" ] && break
        done
        [ -z "${_ploc}" ] && _ploc=${_prof}
    fi
    start_stop_profile_switcher "${_ploc}${_pnet}${_vid} ${_ploc}${_pnet} ${_ploc}${_vid} ${_ploc} ${_vid} DEFAULT"

    log_action_end_msg $?
    ;;
stop)
    start_stop_profile_switcher "DEFAULT"
    ;;
*)
    echo "Usage: $0 {start|stop|restart|force-reload}" >&2
    exit 3
    ;;
esac

exit 0

---

### Post by evs on 2006-11-10
Wow, I had never heard of SCPM before, but it sounds really useful.  I'll give your profile manager a try this weekend.  This could make things a little bit easier!

---

### Post by Enki on 2006-11-25
This looks useful, thanks.

Another solution i found (while researching how to run an existing OS install in vmware) is here: [http://forums.gentoo.org/viewtopic.php?t=46180]("http://forums.gentoo.org/viewtopic.php?t=46180").  The beauty here is that you can have the system autodetect which profile to use based on available hardware. It was made for Gentoo, but should work for Ubuntu as well.

---

