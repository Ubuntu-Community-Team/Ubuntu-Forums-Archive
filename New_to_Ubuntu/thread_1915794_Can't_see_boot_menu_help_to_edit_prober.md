---
title: "Can't see boot menu: help to edit prober"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by seeker.k3 on 2012-01-26
Hi Folks.
I'm running win7 (64) and have installed 11.10 (32) alongside it on a Compaq Presario desktop. When I start the computer it boots 11.10 without displaying the boot menu, so I can't access win7. The shift key doesn't help. (All of this happened to me before, and ended in disaster. I've now re-installed every thing, and I'm at the same impasse, again.)

I'm inserting part of 30_os-prober because it looks like the timer might be set to 0, and that the boot menu is hidden, but I don't know how to read the file, or how to make adjustments. Can someone please tell me how to adjust this so that I can see the boot menu so that I can get back into win.

I'd be grateful for any help.

make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
    verbose=
      else
    verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
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

adjust_timeout () {
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

---

### Post by carl4926 on 2012-01-26
When you run
```
sudo update-grub
```
Does os-prober even see windows?

[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

---

### Post by seeker.k3 on 2012-01-27
Ok. That's helpful, thank you. Here's the answer to your question.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3
done

The link was helpful, but I still can't see the boot menu. I'll post the settings here. As you can see, I've made the timeout very long. The blank screen seems to hang there for a very long time, but I still can't see it.
Thanks again. Here are the settings.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by carl4926 on 2012-01-27
I'm not 100% sure

Maybe this line
GRUB_HIDDEN_TIMEOUT=

should be

GRUB_HIDDEN_TIMEOUT=0

> If the value is set to **0**, a *keystatus* check is performed to determine if the *SHIFT* key is depressed. If GRUB 2 determines the *SHIFT*  key is depressed during the boot process, the menu will be displayed.  This gives the user a method of interrupting an automatic boot which  would normally not display the menu. 

---

### Post by seeker.k3 on 2012-01-27
Hi, yeah, I would have thought so, but it doesn't seem to work. Here's where I'm at. The link you provided helped me sort a few things out. I can't see the menu, but I now know that Ubuntu is 0, and windows is 4. That's great because I can now get back into win7, which solves the main problem. I'll keep experimenting with it to see if I can get the menu to show. I wonder if it's something to do with the motherboard.
Thanks for your help.

---

### Post by carl4926 on 2012-01-27
I never yet had a problem with Grub2
Yet I keep reading about such..

Strange :o

---

### Post by varunendra on 2012-01-27
In order to make the menu visible, make sure the following two lines in **/etc/default/grub** file are same as put here:

> #GRUB_HIDDEN_TIMEOUT=0
(where # disables the effect of this line)
and
> GRUB_TIMEOUT=10
(where 10 is the timeout in seconds before grub proceeds to boot the default choice. You can change it as you wish)
Afterwards, run the command:
```
sudo update-grub
```

By the way, when you previously ran update-grub,  it should have automatically put that **#** before the 'GRUB_HIDDEN_TIMEOUT' line, as soon as it discovered Win7. So I'm wondering if you manually removed it from there.

A typical set of those lines in a etc/default/grub file in 11.10 (with multiple OSes installed and the menu is visible):

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Hope it helps.

---

### Post by seeker.k3 on 2012-01-27
Thank you both. The Grub file was exactly as you have it, and yes, I removed the #, but only after trying, and trying, and trying to get it to work. I have an Acer monitor, and I really think there's a problem there. When xp (on Acer box) or win7 (Compaq box) is in sleep mode, I get an ugly little message drifting around the screen saying 'Input not supported', or 'Cable not connected'. I wonder if there's a graphics problem. In every other respect, the Grub seems to be working fine.
 
I'm very happy with the progress we've made here. It all works. (I'll restore the Grub file to it's correct configuration.) I'll leave this thread open a little longer just to see if someone has a further comment. Maybe someone knows about monitors.

---

### Post by carl4926 on 2012-01-28
I can tell you, I always disable all screensavering and power saving, so my screen never turns off. I just physically press the screen off button if I leave the desk for any time.

I use the same policy with my Laptops/Netbooks. When I'm not using those I just suspend them

---

### Post by seeker.k3 on 2012-02-04
Thanks for the advice. Unfortunately it hasn't actually changed my situation here. 

BTW
Do you suspend desktop computers, or just let them run while you eat your dinner? Also, I wonder why you have adopted that policy: Do those power options cause problems? Finally, I wonder if you have any comment to make about BIOS settings. Could BIOS settings cause a problem (because the problem arises prior to booting)? 

My problem seems unlikely given that it's an Acer monitor and Compaq computer. Pretty common I think.

Thanks again for your help.

---

