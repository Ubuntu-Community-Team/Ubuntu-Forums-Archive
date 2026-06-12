---
title: "grub2 multiboot hide menu"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by zardoz1971 on 2013-03-25
Hello. I was searching for few days the way to hide grub2 menu unless I hold shift key. It's a multiboot system (linux + windows 8) so it was a bit harder to find the solution. But I'm almost there. Have two more problems. But first here's my current status. I only needed to change contents of 30_os-prober in /etc/grub.d/. I changed the following code:


```
make_timeout () {  if [ "x${found_other_os}" = "x" ] ; then    if [ "x${1}" != "x" ] ; then      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then    verbose=      else    verbose=" --verbose"      fi      if [ "x${1}" = "x0" ] ; then    cat <<EOFif [ "x\${timeout}" != "x-1" ]; then  if keystatus; then    if keystatus --shift; then      set timeout=-1    else      set timeout=0    fi  else    if sleep$verbose --interruptible 3 ; then      set timeout=0    fi  fifiEOF      else    cat << EOFif [ "x\${timeout}" != "x-1" ]; then  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then    set timeout=0  fifiEOF      fi    fi  fi}adjust_timeout () {  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then    cat <<EOFif cmostest $GRUB_BUTTON_CMOS_ADDRESS ; thenEOF    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"    echo else    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"    echo fi  else    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"  fi}
```
to:


```
adjust_timeout () {        cat <<EOF        if keystatus --shift; then          set timeout=-1        else          set timeout=0        fiEOF}
```

But now I have a problem. When I run sudo update-grub it doubles the Windows 8 recognition so I get:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
Found Windows 8 (loader) on /dev/sda1
done

Could anyone see where is the error. Here's complete code of changed 30_os-prober:



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


export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"


. "${datarootdir}/grub/grub-mkconfig_lib"


found_other_os=


adjust_timeout () {
        cat <<EOF
        if keystatus --shift; then
          set timeout=-1
        else
          set timeout=0
        fi
EOF
}


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
    if [ x$2 = x32 ]; then
        # TRANSLATORS: it refers to kernel architecture (32-bit)
    bitstr="$(gettext "(32-bit)")"
    else
        # TRANSLATORS: it refers to kernel architecture (64-bit)
    bitstr="$(gettext "(64-bit)")"
    fi
    # TRANSLATORS: it refers on the OS residing on device %s
    onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
        cat << EOF
menuentry '$(echo "${LONGNAME} $bitstr $onstr" | grub_quote)' --class osx --class darwin --class os \$menuentry_id_option 'osprober-xnu-$2-$(grub_get_device_id "${DEVICE}")'  {
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
           if [ /kernelcache -nt /System/Library/Extensions ]; then
              $1 /kernelcache boot-uuid=\${uuid} rd=*uuid
           else
              $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
              if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
                xnu_mkext /System/Library/Extensions.mkext
              else
                xnu_kextdir /System/Library/Extensions
              fi
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


used_osprober_linux_ids=


wubi=


for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"


  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi


  gettext_printf "Found %s on %s\n" "${LONGNAME}" "${DEVICE}" >&2


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
      onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
      cat << EOF
menuentry '$(echo "${LONGNAME} $onstr" | grub_quote)' --class windows --class os \$menuentry_id_option 'osprober-chain-$(grub_get_device_id "${DEVICE}")' {
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
      boot_device_id=
      is_first_entry=true
      title_correction_code=
      OS="${LONGNAME}"


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
    onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
    recovery_params="$(echo "${LPARAMS}" | grep 'single\|recovery')" || true
    counter=1
    while echo "$used_osprober_linux_ids" | grep 'osprober-gnulinux-$LKERNEL-${recovery_params}-$counter-$boot_device_id' > /dev/null; do
        counter=$((counter+1));
    done
    if [ -z "$boot_device_id" ]; then
        boot_device_id="$(grub_get_device_id "${DEVICE}")"
    fi
    used_osprober_linux_ids="$used_osprober_linux_ids 'osprober-gnulinux-$LKERNEL-${recovery_params}-$counter-$boot_device_id'"


    if [ "x$is_first_entry" = xtrue ]; then
            cat << EOF
menuentry '$(echo "$OS" | grub_quote)' --class gnu-linux --class gnu --class os \$menuentry_id_option 'osprober-gnulinux-simple-$boot_device_id' {
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
        echo "submenu '$(gettext_printf "Advanced options for %s" "${OS}" | grub_quote)' \$menuentry_id_option 'osprober-gnulinux-advanced-$boot_device_id' {"
        is_first_entry=false
    fi
    title="${LLABEL} $onstr"
        cat << EOF
    menuentry '$(echo "$title" | grub_quote)' --class gnu-linux --class gnu --class os \$menuentry_id_option 'osprober-gnulinux-$LKERNEL-${recovery_params}-$boot_device_id' {
EOF
    save_default_entry | sed -e "s/^/\t\t/"
    printf '%s\n' "${prepare_boot_cache}" | sed -e "s/^/\t/"
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
    if [ x"$title" = x"$GRUB_ACTUAL_DEFAULT" ] || [ x"Previous Linux versions>$title" = x"$GRUB_ACTUAL_DEFAULT" ]; then
        replacement_title="$(echo "Advanced options for ${OS}" | sed 's,>,>>,g')>$(echo "$title" | sed 's,>,>>,g')"
        quoted="$(echo "$GRUB_ACTUAL_DEFAULT" | grub_quote)"
        title_correction_code="${title_correction_code}if [ \"x\$default\" = '$quoted' ]; then default='$(echo "$replacement_title" | grub_quote)'; fi;"
        grub_warn "$(gettext_printf "Please don't use old title \`%s' for GRUB_DEFAULT, use \`%s' (for versions before 2.00) or \`%s' (for 2.00 or later)" "$GRUB_ACTUAL_DEFAULT" "$replacement_title" "gnulinux-advanced-$boot_device_id>gnulinux-$version-$type-$boot_device_id")"
    fi
      done
      if [ x"$is_first_entry" != xtrue ]; then
      echo '}'
      fi
      echo "$title_correction_code"
    ;;
    macosx)
      OSXUUID="`${grub_probe} --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      found_other_os=1
      onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
      cat << EOF
menuentry '$(echo "${LONGNAME} $onstr" | grub_quote)' --class hurd --class gnu --class os \$menuentry_id_option 'osprober-gnuhurd-/boot/gnumach.gz-false-$(grub_get_device_id "${DEVICE}")' {
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
      echo -n "  "
      # TRANSLATORS: %s is replaced by OS name.
      gettext_printf "%s is not yet supported by grub-mkconfig.\n" "${LONGNAME}" >&2
    ;;
  esac
done
```


adjust_timeout

So, that's the problem.

TIA

---

### Post by oldfred on 2013-03-25
Added code tags using # from advanced edit menu. Please use code tags for long posting of code or data.

Did you make a backup of 30_custom? All executeable files in grub folder are run, so it may also run backup?

I do not edit scripts as you can get into the issues you have. I have not used grub customizer but it does everything you want.
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

 The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

But I do not use Grub Customizer. I just copy entries into 40_custom and edit at will. And if I want to change timeout, I would just directly edit /etc/default/grub file. But I started with drs305's instructions long before Grub Customizer.

 gedit /boot/grub/grub.cfg
Copy Windows entry to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Then I turn os-prober off.
      In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by zardoz1971 on 2013-03-25
> **oldfred said:**
> Added code tags using # from advanced edit menu. Please use code tags for long posting of code or data.

Yea. Sorry. Noticed when I posted already.

> **oldfred said:**
> Did you make a backup of 30_custom? All executeable files in grub folder are run, so it may also run backup?

That's it. Thank you for this. I backed up original and left it in the same folder. After removing it it was O.K.

> **oldfred said:**
> I do not edit scripts as you can get into the issues you have. I have not used grub customizer but it does everything you want.

It was my first choice but couldn't do what I wanted. Also I found in this forum somewhere that it works  only for single boot systems. With multiboot only editing scripts helps.
       New Grub Customizer works with 12.10

Thank you very much for your help. I guess I can mark this as SOLVED.

---

