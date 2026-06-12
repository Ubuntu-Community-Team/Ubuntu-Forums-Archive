---
title: "Dell Monitor Brightness and File Permissions on Startup"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by card_ace on 2014-01-30
This will be a bit long, but I'll try to give as many details as I can.

I have a Dell Inspiron N7010 with 12.04 LTS 64 bit running on it.  I've been having trouble with the brightness buttons (namely them not working) and finally got around to trying to fix it.  I looked around and tried a lot of other solutions found online, but none of them worked.  Finally I just decided to write my own program to do it.  The brightness file is located at /sys/class/backlight/intel_backlight/brightness.
I used nautilus and changed the permissions of the file so I could edit it without being root.  From this point it was a simple matter of pulling the value and changing it.  This is the code I wrote to do it (in C language).  This is obviously the brightness up one.  It's saved in my home directory.

```
#include<stdio.h>

#define INCREMENT_SIZE 478
int main()
{
  FILE *fp;
  int brightness;
  int new_brightness;

  fp = fopen("//sys//class//backlight//intel_backlight//brightness", "w+");

  fscanf(fp, "%d", &brightness);

  new_brightness = brightness + INCREMENT_SIZE;

  fprintf(fp, "%d", new_brightness);
  fclose(fp);

  return(0);
}
```

I know it's probably not the cleanest code, but it's functional.  Now with the file permissions set so I can access them, the program works flawlessly.  I mapped the program to use Alt+Brightness Keys.  Works perfectly.  So I restart and realize that the permissions didn't stay set.  To remedy this, I added a line into /etc/rc.local that read

```
chmod 777 /sys/class/backlight/intel_backlight/brightness/
```

However, when I restart the permissions are still set to "root."  I tried using 666 as well, and still no luck.  So I went through nautilus and changed them to myself again, only to find out that my keyboard shortcuts are not functioning properly.  Even with the permissions set to my user account, the keyboard shortcuts weren't functioning.  So I went back into the keyboard shortcuts menu and reset them to different keys (Alt-Up/Down) and they functioned perfectly again.  After changing them back to Alt-BrightnessKeys they still work.  So even though it appears the mapping is still set, it's not actually working unless I reset them.

So really there's 2 problems in one here.
1: Either setting the permissions on the brightness file to allow editing or run my program as root
2: Strange keyboard mapping behavior

---

### Post by Impavidus on 2014-01-31
/sys is a virtual file system. It's not located on your disk and recreated on every boot. /sys is meant to have a convenient way to access various system parameters via the file system. As it's not on disk, changed permissions don't survive a reboot.

To give the program the right access to the pseudo-file in /sys, you can execute it with root permissions. First make sure the program is absolutely safe to execute with root permission. This short program looks OK, except that you should
- check that the file has been opened succesfully. When you change your hardware it may no longer work, giving unexpected results. Make sure the return value of fopen() is not NULL.
- make sure the old brightness has been read correctly. The return value of fscanf should be 1 and brightness should be some sensible value. It should be fine, but better to double-check.
- make sure the brightness is not increased over a certain limit, the maximum brightness that can be set. If it grows too large, set it to the maximum. Otherwise you may get unexpected results (although most likely it's just capped to the maximum).
- make sure it doesn't overflow the maximum number that can be stored in an int, which would result in negative brightness, which is an undefined result too (unlikely to happen before the previous limit is reached).

To prevent you from having to type your password everytime, you can make the program setUID root. To do so, use```
sudo chown root:root progname
sudo chmod 4755 progname
```

On my system I can find the actual brightness and the maximum brightness in /sys/class/backlight/intel_backlight/{actual_brightness,max_brightness} respectively. Alternatively, I can use /sys/class/backlight/acpi_video0/{actual_brightness,brightness,max_brightness}, which uses a scale from 0 to 20. Every press on the brightness keys changes this value by 1 and it is mapped non-linearly to the values in intel_backlight/. This may be a cleaner way to set the brightness. Note that the details are hardware-dependent.

---

### Post by card_ace on 2014-01-31
Thanks for the explanation.  That solution worked perfectly.  I'm going to run edit my program to include your suggestions as well.
The only problem now is the keyboard mapping not working.  As I stated above, as soon as I change the keys it works fine, just not directly after a reboot.

edit: Also, it seems that on most Dells, judging from other forum posts I've found, there isn't a "acpi_video" folder, it's "dell_backlight" or "intel_backlight" as the options.

---

### Post by card_ace on 2014-02-06
I found a solution.  The built in keyboard shortcuts weren't working, but when I used the commands section in Compiz, it works on a reboot every time.  Just in case anybody else has this problem

---

