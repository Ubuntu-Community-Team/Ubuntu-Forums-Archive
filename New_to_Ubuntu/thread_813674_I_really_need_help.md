---
title: "I really need help"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-31
Im trying to fix my compiz fusion since it decided to die today ive reinstalled everything and have not made any progress all im getting is that desktop effects cannot be enabled. help anyone

---

### Post by iaculallad on 2008-05-31
Had you tried visiting this [page]("http://ubuntuforums.org/showthread.php?t=612576")? I think you got similar problem.

---

### Post by PatrickMoore on 2008-05-31
i think that my circumstance is  a little different. it was working great until i installed koolapps now its gone 

i typed compiz into my terminal i got

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0244 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0 
```

---

### Post by iaculallad on 2008-05-31
What's the result when you input this on your terminal?

```
compiz --replace
```

---

### Post by PatrickMoore on 2008-05-31
for kicks i typed in composite manager i got

```
 composite manager
Version: ImageMagick 6.3.7 02/18/08 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2008 ImageMagick Studio LLC

Usage: composite [options ...] image [options ...] composite
  [ [options ...] mask ] [options ...] composite

Image Settings:
  -affine matrix       affine transform matrix
  -alpha option        activate, deactivate, reset, or set the alpha channel
  -authenticate value  decrypt image with this password
  -blue-primary point  chromaticity blue primary point
  -channel type        apply option to select image channels
  -colorspace type     alternate image colorspace
  -comment string      annotate image with comment
  -compose operator    composite operator
  -compress type       type of pixel compression when writing the image
  -define format:option
                       define one or more image format options
  -depth value         image depth
  -density geometry    horizontal and vertical density of the image
  -display server      get image or font from this X server
  -dispose method      layer disposal method
  -dither              apply Floyd/Steinberg error diffusion to image
  -encoding type       text encoding type
  -endian type         endianness (MSB or LSB) of the image
  -filter type         use this filter when resizing an image
  -font name           render text with this font
  -format "string"     output formatted image characteristics
  -gravity type        which direction to gravitate towards
  -green-primary point chromaticity green primary point
  -interlace type      type of image interlacing scheme
  -interpolate method  pixel color interpolation method
  -label string        assign a label to an image
  -limit type value    pixel cache resource limit
  -monitor             monitor progress
  -page geometry       size and location of an image canvas (setting)
  -quality value       JPEG/MIFF/PNG compression level
  -quiet               suppress all warning messages
  -red-primary point   chromaticity red primary point
  -regard-warnings     pay attention to warning messages
  -sampling-factor geometry
                       horizontal and vertical sampling factor
  -scene value         image scene number
  -seed value          seed a new sequence of pseudo-random numbers
  -size geometry       width and height of image
  -transparent-color color
                       transparent color
  -treedepth value     color tree depth
  -tile                repeat composite operation across and down image
  -units type          the units of image resolution
  -verbose             print detailed information about the image
  -virtual-pixel method
                       virtual pixel access method
  -white-point point   chromaticity white point

Image Operators:
  -blend geometry      blend images
  -colors value        preferred number of colors in the image
  -displace geometry   shift image pixels defined by a displacement map
  -dissolve value      dissolve the two images a given percent
  -extract geometry    extract area from image
  -geometry geometry   location of the composite image
  -identify            identify the format and characteristics of the image
  -monochrome          transform image to black and white
  -negate              replace every pixel with its complementary color 
  -profile filename    add ICM or IPTC information profile to image
  -quantize colorspace reduce colors in this colorspace
  -repage geometry     size and location of an image canvas (operator)
  -rotate degrees      apply Paeth rotation to the image
  -resize geometry     resize the image
  -sharpen geometry    sharpen the image
  -stegano offset      hide watermark within an image
  -stereo              combine two image to create a stereo anaglyph
  -strip               strip image of all profiles and comments
  -thumbnail geometry  create a thumbnail of the image
  -transform           affine transform image
  -type type           image type
  -unsharp geometry    sharpen the image
  -watermark geometry  percent brightness and saturation of a watermark
  -write filename      write images to this file

Miscellaneous Options:
  -debug events        display copious debugging information
  -help                print program options
  -list type           print a list of supported option arguments
  -log format          format of debugging information
  -version             print version information

By default, the image format of `file' is determined by its magic
number.  To specify a particular image format, precede the filename
with an image format name and a colon (i.e. ps:image) or specify the
image type as the filename suffix (i.e. image.ps).  Specify 'file' as
'-' for standard input or output.

```

what the hell is image magick?

---

### Post by PatrickMoore on 2008-05-31
```
patrick@patrick-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0244 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

---

### Post by iaculallad on 2008-05-31
For the last of it, because you mentioned that compiz just freezed working and that you did reinstallation.

What about (Or did we use the same command)?

```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
``` :)

ImageMagick:

is a software suite to create, edit, and compose bitmap images. It can read, convert and write images in a variety of formats.

---

### Post by PatrickMoore on 2008-05-31
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
compiz is already the newest version.
compiz-core is already the newest version.
compiz-core set to manually installed.
compiz-fusion-plugins-main is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
compiz-gnome is already the newest version.
compiz-plugins is already the newest version.
compiz-plugins set to manually installed.
Package libcompizconfig-backend-gconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcompizconfig-backend-gconf has no installation candidate

```

---

### Post by iaculallad on 2008-05-31
Try this if it will solve libcompizconfig-backend-gconf problem.

```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

---

### Post by PatrickMoore on 2008-05-31
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz-gnome is already the newest version.
compizconfig-settings-manager is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
Package libcompizconfig-backend-gconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcompizconfig-backend-gconf has no installation candidate

```

looks like same issue

---

### Post by PatrickMoore on 2008-05-31
if i go into synaptec im showing that compiz backend gconf is already installed

---

### Post by PatrickMoore on 2008-05-31
i tried seeing if reinstalling that package would work but alas no

---

### Post by PatrickMoore on 2008-05-31
has anyone else had this problem before?

---

### Post by quinnten83 on 2008-05-31
Maybe we could try looking in a different direction.
Could you copy the contents of your xorg.conf for us?
```
sudo gedit /etc/X11/xorg.conf
```

or if you are willing to take a risk, reconfigure your video settings:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I think it is more of a problem of XGL not being recognized than anything else. Compiz itself might not be broken. Have you tried reinstalling the Nvidia drivers?

---

### Post by PatrickMoore on 2008-05-31
> **quinnten83 said:**
> Maybe we could try looking in a different direction.
Could you copy the contents of your xorg.conf for us?
```
sudo gedit /etc/X11/xorg.conf
```


```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

or if you are willing to take a risk, reconfigure your video settings:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

i could try that but i want to see the outcome of the former

I think it is more of a problem of XGL not being recognized than anything else. Compiz itself might not be broken. Have you tried reinstalling the Nvidia drivers?

I'll try that too

---

### Post by PatrickMoore on 2008-05-31
i tried reinstalling my nvidia drivers but nothing has changed anything else i could try

---

### Post by mcgyverbob on 2009-07-22
Sorry to revive this old thread but I thought I'd help. 
This has happened to me three times now over a long period of time and I never noted as to how I fixed it the first time, and I had forgotten how I had done it. 
There are many threads about this issue out there and not one has come to a solid conclusion or has mentioned what got this issue fixed for me. 

The problem on all three of my Compiz installs that caused the 'no window borders issue' and the "another composite manager is already running" message was that xcompmgr was installed. Simply uninstalling it via the packag manager immediately fixed this issue. 

Hope this helps someone out there.

Cheers
\\:D/

---

