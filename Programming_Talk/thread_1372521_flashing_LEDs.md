---
title: "flashing LEDs"
date: 2010-01-04
forum: Programming Talk
---

### Post by akashiraffee on 2010-01-04
Anyone ever found anything to flash the keyboard leds?  I've done a bit of googling and found a bunch of stuff that seems out-dated, eg kernel modules that reference non-existent includes, and "ledcontrol" which appears to do nothing on my system.

**[XChangeKeyboardControl()]("http://tronche.com/gui/x/xlib/input/XChangeKeyboardControl.html")** can apparently do this "if possible", but in fact it will not change anything including the bell:
```

       Display *XDisplay = XOpenDisplay(NULL);
       KCntl.bell_percent = 50;
        KCntl.bell_duration = 150;
        XChangeKeyboardControl(XDisplay,KBBellPercent | KBBellDuration,&KCntl);
        printf("%%: %d pitch: %u dur: %u\n",KState.bell_percent,KState.bell_pitch,KState.bell_duration); 

```None of the values are changed, and the same is true for the LEDS.  The most I seem to be able to do with Xlib is get information.

(which occasionally my bell does ring, god knows how...)

---

### Post by akashiraffee on 2010-01-05
Wow, I just learned all about **ioctl** and spend some time paging thru the kernel source and c include headers.  Now that's *nix programming.

Anyhow, there's some old stuff out there on the web that may not work, so for posterity:
```

#include <stdio.h>
#include <unistd.h>        /* close */
#include <fcntl.h>        /* open */
#include <errno.h>        /* perror */
#include <linux/kd.h>        /* Keyboard macros */
#include <sys/ioctl.h>        /* ioctl */

int main() {
    int tty = open("/dev/console", 0), led;
    unsigned long int arg;

    if (tty<3) {
        perror("open: ");
        return -1;
    }
    if (ioctl(tty,KDGKBTYPE, &arg) > 0) perror("ioctl: ");
    if (arg == KB_101) puts("You have a 101 key keyboard.");

    for (led=1; led<9; led++) {
        if (ioctl(tty,KDSETLED, led) > 0) perror("ioctl led on: ");
        printf("LED %d on...hit enter", led);
        getchar();
        if (ioctl(tty,KDSETLED, led+0xff) > 0) perror("ioctl led off: ");
        printf("off (hit enter)\n");
        getchar();
    }

    close(tty);

    return 0;
}

```Most people have a 101 key keyboard, so the first ioctl is just a check.  The LED numbers are bitmasks; on my keyboard there are three: 1,2, and 4 -- 3, 5, 6, and 7 set patterns of multiple lights.  8 doesn't do anything, but I suppose it will if you have a forth LED.  This doesn't actually set the CAPLOCK or anything, it just flashes the lights.

This is pretty handy if you need to be alerted but have problems with the linux soundsystem, such that you can't play a wav while watching youtube ;)

If I keep digging maybe I'll find the bell :D

---

### Post by Sockerdrickan on 2010-01-05
Cool, now create a little game with these!

---

