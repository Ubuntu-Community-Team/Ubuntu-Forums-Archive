---
title: "HOWTO: Random Wallpapers on Different Monitors with Different Resolutions"
date: 2009-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by KennethGodwin on 2009-07-02
**To Setup**

Assumptions: This only works in GNOME. You have one or two monitors. I don't have more so it isn't tested with more. I think it may work...not sure on that point. :P

_Script Setup_

1) Download the attachment wallpaper.sh (It is really a perl file however .pl is blocked but it works fine with either extension.)

2) sudo apt-get install perlmagick (This installs perlmagick which does the splicing of images and outputing them.)

3) Open Terminal

4) mkdir ~/.wallpaper (Or wherever you want to put your wallpaper images.)

5) Place the wallpapers in ~/.wallpaper (Or wherever you made the folder). The wallpapers must be the **exact** resolution of the monitor or it won't be picked.

6) Open gedit (Applications -> Accessories -> Text Editor or Open Terminal -> gedit)

7) Open wallpaper.sh with gedit

The config is pretty self explanatory but let us do an example config.

Let us say, for the sake of argument, that your monitors are 1920x1200 and 1440x900. They are right next to each other, horizontally. (Bigger monitor on the right, smaller on the left.) You will need to modify the numbers used according to your setup.

8) Find the @outputScreen line. You add the widths and use the largest height. If we were doing vertical, that would be the opposite.

```

my @outputScreen = ('3360','1200'); 

```

9) Find the @screens line. The first monitor is the one furthest on the right. So here you just put in the monitor resolutions. This is already correct for our example config. 

```

my @screens = (
  ['1920', '1200'], 
  ['1440', '900'], 
);

```

10) Find the $orientation line. Since our monitors are horizontally aligned, this is already correct. If we had one on top of the other, we'd need to change this to vertical.

```

my $orientation = "horizontal";

```

11) Find the @wallpaper_dirs line. Change it so it looks like this. Replace [username] with your username if you used the default wallpaper directory location. 

```

my @wallpaper_dirs = (
  '/home/[username]/.wallpaper/',
);

```

12) Find the $output_file line. Change it so it looks like this. Replace [username] with your username if you used the default wallpaper directory location. If you want your desktop image somewhere else, adjust accordingly.

```

my $output_file = "/home/[username]/.wallpaper/output.jpg";

```

13) Open a terminal 

14) /path/to/wallpaper/wallpaper.sh

15) If your wallpaper shows up in the wrong place, or something else goes wrong, fix your config accordingly.

_Cron Job_
(If you want it to run every X length of time, if you are just lazy and want it to stitch the wallpaper for you instead of GIMP, just run it normally.)

1) Open Terminal

2) crontab -e

3) Choose your prefered editor (I'd go with nano if you don't know what this means.)

4) Insert the following line at the end of the file. The suggested length is 30 minutes. In other words, every 30 minutes the wallpapers will try to switch. They may not if you have a small # of wallpapers for a given resolution. If you want this to be faster / longer just modify the number 30. (e.g. 1 is every minute. 59 is every 59 minutes.) Remove the >/dev/null 2>&1 if you want to receive 'mail' (via the mail command) about your cron job. :P

```
*/30 * * * * /path/to/wallpaper.sh >/dev/null 2>&1
```


**To Revert Changes**
1) Just delete the relevant file (wallpaper.sh) from where it was placed.

2) crontab -e 

3) Delete the crontab line you added.

---

### Post by jpeddicord on 2009-07-07
Approved, and thank you for contributing to Tutorials & Tips!

---

### Post by KennethGodwin on 2009-07-07
Awesome. :guitar:

I just hope it helps somebody until Gnome finally adds the feature!

---

### Post by kellyhardinguk on 2009-07-07
I can confirm this works a treat :)

---

