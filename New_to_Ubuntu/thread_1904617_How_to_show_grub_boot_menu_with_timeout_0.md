---
title: "How to show grub boot menu with timeout 0?"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Chiel92 on 2012-01-05
Hi,

I wonder if it is possible to pause at de grub menu (by pressing a key, or something) while having the timeout set to 0.
I it possible?

Regards

---

### Post by mcduck on 2012-01-05
Holding down Shift while booting should do the trick.

---

### Post by Chiel92 on 2012-01-05
Thanks for your reply!

> **mcduck said:**
> Holding down Shift while booting should do the trick.

That doesn't seem to work for me, for some reason.:confused:
Nothing happens, it justs continues booting the first OS in the menu.

I use ubuntu 10.04.
The grub version is:
grub-setup (GRUB) 1.98-1ubuntu12

I have a few other distro's and windows installed beside Ubuntu 10.04.

---

### Post by mcduck on 2012-01-05
It can be a bit tricky about the correct timing, but that really is the correct key. You might have to try a couple of times to find out what works for you. (holding down the shift before pushing power button, holding it down immediately after POST, pushing the button repeatedly etc.)

Anyway, if you don't want to show the menu by default, then setting it as hidden instead of setting the timeout to 0 might be a better approach. (it could even be that the Shift key only works for hidden Grub menu, and not for 0 timeout. I've never tried (and old Grub didn't actually even allow timeout of 0, if you tried to set that it used a 1-second timeout instead)

---

### Post by Chiel92 on 2012-01-05
> **mcduck said:**
> It can be a bit tricky about the correct timing, but that really is the correct key. You might have to try a couple of times to find out what works for you. (holding down the shift before pushing power button, holding it down immediately after POST, pushing the button repeatedly etc.)

Anyway, if you don't want to show the menu by default, then setting it as hidden instead of setting the timeout to 0 might be a better approach. (it could even be that the Shift key only works for hidden Grub menu, and not for 0 timeout. I've never tried (and old Grub didn't actually even allow timeout of 0, if you tried to set that it used a 1-second timeout instead)

Okay, I will play a bit around with those things. 
I initially had the timeout set to 2 seconds. 
I wanted to speed up my boot time, and also get a more comfortable way to choose another OS.  
EDIT: I just read in documentation: 
Holding down the "SHIFT" key will not display the menu if "GRUB_TIMEOUT=" is set to "0"

---

### Post by Chiel92 on 2012-01-05
I tried a little bit around with the configuration in /etc/default/grub, but without success. 
So I thought modding /etc/grub.d/30_os-prober would be a good idea. 
After backing up the file, I changed  
```

adjust_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
    cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}



```into

```
adjust_timeout () {
        cat <<EOF
        if keystatus --shift; then
          set timeout=-1
        else
          set timeout=0
        fi
EOF
}
```
That works fine. 
Every time I boot, I have to press shift (after pressing the power button), and then the boot menu pops up, without timeout.
If I do not press shift, grub immediately boots to the first OS.

---

### Post by amites on 2012-07-21
Thank you for the snippet -- I pasted a copy to github at
[https://gist.github.com/3158259](https://gist.github.com/3158259)

makes sense as a template setup option since it's what I end up wanting most of the time and likely others

---

### Post by NikTh on 2012-07-22
Hi , 
yes i can confirm  , this hack , works at 12.04 as well .. 

For me was a little bit different to change the file.
_ 30_os-prober was not exist_ , so i mattered an other file /etc/grub.d/proxifiedScripts/**os-prober** .

Similar codes are in this file but not exactly the same , and i had to delete some code to fix this. 

Original code in that file was 
```
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

. "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

[B]make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

[/B] [B]       if [ "x${1}" = "x0" ] ; then
    cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
    cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {[/B] [B]
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}[/B]

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
    found_other_os=1
        cat << EOF
menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" --class osx --class darwin --class os {
EOF
    save_default_entry | sed -e "s/^/\t/"
    prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
    cat << EOF
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume = 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

wubi=

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  echo "Found ${LONGNAME} on ${DEVICE}" >&2

  case ${BOOT} in
    chain)

      case ${LONGNAME} in
    Windows*)
      if [ -z "$wubi" ]; then
        if [ -x /usr/share/lupin-support/grub-mkimage ] && \
           /usr/share/lupin-support/grub-mkimage --test; then
          wubi=yes
        else
          wubi=no
        fi
      fi
      if [ "$wubi" = yes ]; then
        echo "Skipping ${LONGNAME} on Wubi system" >&2
        continue
      fi
      ;;
      esac

      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class windows --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
    Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
    ;;
    *)
      cat << EOF
    drivemap -s (hd0) \${root}
EOF
    ;;
      esac

      cat <<EOF
    chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

    if [ "${LROOT}" != "${LBOOT}" ]; then
      LKERNEL="${LKERNEL#/boot}"
      LINITRD="${LINITRD#/boot}"
    fi

    if [ -z "${prepare_boot_cache}" ]; then
      prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
      [ "${prepare_boot_cache}" ] || continue
    fi
    found_other_os=1
        cat << EOF
menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
EOF
    save_default_entry | sed -e "s/^/\t/"
    printf '%s\n' "${prepare_boot_cache}"
    cat <<  EOF
    linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
          cat << EOF
    initrd ${LINITRD}
EOF
        fi
        cat << EOF
}
EOF
      done
    ;;
    macosx)
      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      found_other_os=1
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" --class hurd --class gnu --class os {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | sed -e 's/(\(hd.*\),msdos\(.*\))/\1s\2/'`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
    *fs)    hurd_fs="${grub_fs}" ;;
    *)    hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
    multiboot /boot/gnumach.gz root=device:${mach_device}
    module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
            --multiboot-command-line='\${kernel-command-line}' \\
            --host-priv-port='\${host-port}' \\
            --device-master-port='\${device-port}' \\
            --exec-server-task='\${exec-task}' -T typed '\${root}' \\
            '\$(task-create)' '\$(task-resume)'
    module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
    ;;
  esac
done

adjust_timeout
```i deleted all the bolded and replaced them with @Chiel92's ```
adjust_timeout () {
        cat <<EOF
        if keystatus --shift; then
          set timeout=-1
        else
          set timeout=0
        fi
EOF
}
```It works like should be.. 
No timeout , and when "Shift" remains pressed,  grub loading the menu.

**Ps: **do not forget a backup of the original file (os-prober) , and also to update-grub after you save the new modified file. 


Thanks

---

### Post by Chiel92 on 2012-07-22
Great that the workaround also works in 12.04.
Recently a grub update caused my grub configuration to be messed up.
I thought the problem was in /etc/default/grub and I posted a question on the forum.
However the problem turned out to be in /etc/grub.d/30_os-prober. In other words, the changes I made, presented above, were reset by the update. 
The thread got solved by an alternative to the above method. 
[http://ubuntuforums.org/showthread.php?t=1987907](http://ubuntuforums.org/showthread.php?t=1987907)
One could consider that one to be a bit more neat, since only one line is replaced.

Of course performing the above again also would have fixed my grub configuration.

---

