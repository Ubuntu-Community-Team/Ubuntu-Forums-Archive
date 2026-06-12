---
title: "Resolution stuck at 1024x768 for VA1616w"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by fr34k on 2008-12-01
On Hardy , i got 1280x768 resolution, without any xorg editing . On Intrepid , resolution is stuck at 1024x768 . Is this what we call improvement ?:(

( Monitors native resolution is 1366x768 . But present graphic hardware wont support that extent. All i want is 1280x768 )

---

### Post by fr34k on 2008-12-02
I tried 
```

sudo dpkg-reconfigure -phigh xserver.xorg

```

But it gives the same xorg.conf file as of before.

If Hardy can give 1280x768 option in Screen Resolution menu, why cant Intrepid .
There ought to be a way to fix this.

---

### Post by m_l17 on 2008-12-02
Give this a try:

Make a backup of your xorg.conf:

```
$ cd /etc/X11/

$ sudo cp xorg.conf xorg.conf.orig
```

You can name the backup whatever you like I just like to use .orig for original.

Add these lines to your xorg.conf, in the Section Monitor below Identifier:
        HorizSync       30-81
        VertRefresh     60

Very important make sure you use your monitor's specs only


Add theses lines to your xorg.conf, in the Section Screen below  DefaultDepth :

        SubSection      "Display"
        Depth           24
        Modes           "1920x1200_60"
        EndSubSection

Modes = resolution-you-would-like-to-use_refresh-rate-you would-like-to-use

example:
```
Section "Monitor"
	 Identifier	"Configured Monitor"
        [COLOR="Red"]HorizSync       30-81 <----- change for your monitors specs
        VertRefresh     60    <----- change for your monitors specs[/COLOR]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
       [COLOR="Red"]SubSection      "Display"
       Depth           24
       Modes           "1280x1024_85" <--- change to desired resolution and refresh rate
       EndSubSection[/COLOR]
EndSection
```

logout then log back in or reboot

If the above does not work for you you change everything back by:

```
$ cd /etc/X11/

$ sudo cp xorg.conf.orig xorg.conf
```

---

### Post by fr34k on 2008-12-06
I changed my xorg.conf from

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

to

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       24-82
        VertRefresh     50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
        Depth           24
        Modes           "1280x768_60"
        EndSubSection
EndSection

```

But it displayed "Out of Range" 
So i reverted to the old xorg.conf.:(

---

### Post by mapes12 on 2008-12-06
In Terminal  ```
gksudo displayconfig-gtk
``` when the GUI pops up select your hardware and required screen res. It worked for me in 8.04. Don't know about 8.10 though.

---

### Post by fr34k on 2008-12-08
> **mapes12 said:**
> In Terminal  ```
gksudo displayconfig-gtk
``` when the GUI pops up select your hardware and required screen res. It worked for me in 8.04. Don't know about 8.10 though.

On my 8.10 terminal , no GUI is poping up after this command.
It just drops to the successive prompt.

---

### Post by mapes12 on 2008-12-08
OK. Try this.

Right click "Applications" then "Edit Menus".

In the left hand column select "Other" then in the R/H column check "Screens & Graphics"

Close the window then Applications>Other>Screens & Graphics then select your hardware and required res from there.

If the Screen & Graphics option is not listed under Other after doing the above then restart your machine. It should then show up.

Like I said, this works for 8.04. Not sure on 8.10.

---

### Post by fr34k on 2008-12-08
oops , no "Screens and Graphics" option available in 8.10, as far as i can see.
Fear,i may have to wait till Jaundy for a fix or either revert to hardy.

---

### Post by mapes12 on 2008-12-09
Looks like you haven't got the packages installed.

Go to the following 2 links. At the bottom of each page is a link to allow the package to be downloaded. Make sure that, for guidance-backends you select the correct architecture for your computer. For displayconfig-gtk there is only one possible download for all architectures. 

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

[http://packages.ubuntu.com/hardy/admin/displayconfig-gtk](http://packages.ubuntu.com/hardy/admin/displayconfig-gtk)

Once downloaded, click on the guidance-backends first, and you should be presented with the option 'Open with GDebi' or something similar. This installs the package on your system. Do the same for displayconfig-gtk package.

Then open a terminal and type:

```
gksudo displayconfig-gtk
```

The GUI should open for you to edit your settings.

---

### Post by fr34k on 2008-12-11
I am using intrepid and i regularly update with update manager.
So these packages should be available in the intrepid repositories via synaptic, but they aren't . So i suppose they are not intended for intrepid.

I think i may get into problems by directly installing hardy packages onto an intrepid. 

I missing my 1280X768 on Ubuntu desktop
Only solace is that i dual boot with Windows XP and i can see 1280X768 atleast in there..

---

### Post by fr34k on 2009-09-02
Solved . By setting virtual size in xorg.conf

---

