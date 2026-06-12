---
title: "Toshiba Laptop 1800-S204 Video Resolution"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by jibaricua on 2008-08-10
I installed 8.04.1 and the video resolution  is not correct, it defaults to 800x600

when I go into system-preference-screen resolution

the only options available are 800x600, 640x480, 400x300 and 320x240

it should be 1024x768, which is not one of the available options

help me ! :(

---

### Post by SZ07 on 2008-08-10
It looks like you'll probably have to edit your xorg.conf file and manually include the resolution you want.

Here is a guide on editing xorg.conf: [http://www.linux.com/feature/118108](http://www.linux.com/feature/118108) Scroll down to the screen resolution section.

You could also post your current xorg.conf setup and someone could guide you if you are uncomfortable with making the changes.

---

### Post by tyroeternal on 2008-08-11
Here is the most likely method for a quick fix.  These steps are taken from this article in the Ubuntu Community Documentation: [Fix Video Resolution Howto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")
//There are other steps in this guide to this process to be taken if this quick fix does not work.


**Method A**: This is not a fix all, but should take care of your problem easily.  Steps to undo any action have also been noted.  These steps should be done from the command line, so open up a terminal and follow along :)

**Step 1**: Backup the file you will edit
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

**Step 2**: Open up an editor
```
sudo nano /etc/X11/xorg.conf
```

**Step 3**: If you have an issue where only 800x600 is available in the dropdown for screen resolution, then modifying the Modes line within the section in that file called Section "Monitor" and adding the required resolution could solve this.
> 
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

You then can add the resolutions you know your laptop supports directly into that line... for example mine is "1680x1050" "1024x768" "800x600" "640x480".

**Step 4**: Close the file with CTRL+X and answer yes to saving and hit enter to save the file.

**Step 5**: Restart X (restart the display) by pressing CTRL+ALT+Backspace

If everything worked you will have your new resolution and everything will be happy with the world.

If not to restore the xorg.conf file to what it was, get to a terminal and enter this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```


**Method B**: There is also the option of installing the restricted drivers for your card.  Go to **System** -> **Administration** -> **Hardware Drivers** -> and enable your video card drivers if they are present.  When your system restarts you should be sitting nicely on your best resolution.

---

