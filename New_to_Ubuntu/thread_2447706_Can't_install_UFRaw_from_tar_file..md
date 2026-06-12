---
title: "Can't install UFRaw from tar file."
date: 2020-07-24
forum: New to Ubuntu
---

### Post by Brian_G_M on 2020-07-24
Hi,
I very recently installed UBUNTU (20.04 )- tried it several times in the past, but have been absent for a number of years.
Trying to install UFRaw (from a tar file) to work with GIMP, but i get this error when I try to run ./configure:

[I]No package 'gtkimageview' found
[/I]
[I]Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/I]

I do not know what this means. Can I install my software in a standard prefix - what does that mean? I am very ignorant here and I need some help to get over this bump. Many thanks, Brian

---

### Post by monkeybrain20122 on 2020-07-24
That means you are missing the dependency gtkimageview. The package is not in 20.04 apparently because it is dead upstream and doesn't build with gtk3 [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=944995](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=944995). I think ufraw itself is also dead, it has not seen any update since 2015 and apparently works only with gimp <= 2.6, and it recommends 2.4 on its website.
Now to open raw files in gimp install darktable.

---

### Post by Brian_G_M on 2020-07-26
> **monkeybrain20122 said:**
> That means you are missing the dependency gtkimageview. The package is not in 20.04 apparently because it is dead upstream and doesn't build with gtk3 [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=944995](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=944995). I think ufraw itself is also dead, it has not seen any update since 2015 and apparently works only with gimp <= 2.6, and it recommends 2.4 on its website.
Now to open raw files in gimp install darktable.

Thanks for this.

I installed rawtherapee(appimage) but I couldn’t get GIMP to work with that. When I tried to open a raw file in GIMP I got error messages:
“Calling error for procedure 'gimp-file-load':
Error opening file /tmp/gimp/2.10/gimp-temp-33081.tif: No such file or directory” 
and:
“Opening '/home/brian/Pictures/2020/SSCC_BinalongBooroowa_16July20-58.rw2' failed:

Raw Panasonic plug-in could not open image”

I decided also that DarkTable is a better editor than rawtherapee, so decided to go with that.

I tried to get rid of rawtherapee, by deleting all the files I could find – there is apparently (?) no uninstall process for appimages.

I have GIMP and DarkTable each working OK independantly, but GIMP keeps trying to use rawtherapee as its raw image importer plug-in. I change the raw image importer under preferences, but when I close and open GIMP it is back to wanting to use rawtherapee. I keep getting the same error messages when I try to open a raw file in GIMP.

I assume there is still part of rawtherapee in my system that I haven’t found and deleted. But I don’t know why I can’t change the preferred plug-in in GIMP.

Any ideas? Many thanks for your help.

---

### Post by monkeybrain20122 on 2020-07-26
> **Brian_G_M said:**
> 

I assume there is still part of rawtherapee in my system that I haven&#8217;t found and deleted. But I don&#8217;t know why I can&#8217;t change the preferred plug-in in GIMP.

Any ideas? Many thanks for your help.

How did you install darktable? If it is an appimage or a snap it won't work. It may be a snap if you grab it just off the software store. gimp doesn't work with external programs called by wrapper scripts,  installed as flatpak or snap, or appimages. See the last four posts [here]("https://gitlab.gnome.org/GNOME/gimp/-/issues/2985").  So darktable has to be installed in the "normal" way for gimp to find it, i.e either from the repo or a[ ppa]("https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/darktable") (installed through apt or synaptic, or the non snap package in the software store) Gimp installed as snap or flatpak also won't work, but gimp appimage + darktable "normal" works.

If you install darktable and gimp "normally" and it still doesn't work, you can "factory reset" gimp by deleting it configuration folder. Open the file manager, press ctrl+h to show hidden files, find the .config folder (note the "." in front) open it, find the GIMP folder inside and delete it and anything that has to do with rawtherapee. But be warned that this way you'll lose all customizations for gimp.

---

### Post by Brian_G_M on 2020-07-27
> **monkeybrain20122 said:**
> How did you install darktable? If it is an appimage or a snap it won't work. It may be a snap if you grab it just off the software store. gimp doesn't work with external programs called by wrapper scripts,  installed as flatpak or snap, or appimages. See the last four posts [here]("https://gitlab.gnome.org/GNOME/gimp/-/issues/2985").  So darktable has to be installed in the "normal" way for gimp to find it, i.e either from the repo or a[ ppa]("https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/darktable") (installed through apt or synaptic, or the non snap package in the software store) Gimp installed as snap or flatpak also won't work, but gimp appimage + darktable "normal" works.

If you install darktable and gimp "normally" and it still doesn't work, you can "factory reset" gimp by deleting it configuration folder. Open the file manager, press ctrl+h to show hidden files, find the .config folder (note the "." in front) open it, find the GIMP folder inside and delete it and anything that has to do with rawtherapee. But be warned that this way you'll lose all customizations for gimp.

Thanks for your help with this, but I have got nowhere.
I have installed Darktable “normally” using apt. But I can only get GIMP through Snap. 
There is s ppa source for gimp quoted widely, 
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
But this is apparently not being maintained and the system is broken:
“404  Not Found [IP: 91.189.95.83 80]”
I tried to download a tar file and build from that, but I was overwhelmed by broken dependencies. I sorted out a few of them, many I cannot sort out (Python seems to be a problem), and many have broken dependencies of their own.
Darktable and GIMP are set up to work together, but it seems impossible to install them in such a way that they do work together! I can get around this by manually saving files from Darktable and then opening them in Gimp. 
Thanks again.

---

### Post by monkeybrain20122 on 2020-07-27
No, gimp installed with snap can't use darktable or any external plugin (e.g gmic) since it is sandboxed, see this [thread]("https://discourse.ubuntu.com/t/gimp-woes-in-20-04/15828/7"). But gimp installed from Ubuntu's repo would work normally. The ppa hasn't been updated for months  and is probably broken. So just 
```
sudo apt update
sudo apt install gimp
```

This is a slightly older version [2.10.18 instead of 2.10.20] but it works.
 

If you must have 2.10.20, the gimp [appimage]("https://appimage.github.io/GIMP/") also works, I tested it.

I think they should really remove the snaps that don't work properly from the app store or at least put some big warnings about their limitations for new users.Otherwise it conveys the bad impression that Ubuntu is broken and hurts its reputation for new users.

I suggest you install synaptic to manage your software, it really makes life a lot easier. As a new user I had a lot of problems with these sudo apt install x commands from online tutorials because the name of x might have changed and how would I know the proper name of x in the first place? But synaptic has good search function so you don't need to remember those mysterious names.  It provides much more fine grain control and complete listing as the software store (the software store only shows end user software, not libs and components)

There is also no snap in synaptic, all the packages are deb, so there is no gotcha like installing from the software store (which does label which package is snap but it is not prominently displayed, you have to go to the description and check the provider, i f it says snapcraft then it is a snap)
```

sudo apt install synpatic
```

P.S. The tar file is source code, it is quite daunting to compile gimp from source since all the dependencies issues. I have gimp 2.10.20 on Ubuntu 16.04 compiled from source but it took a bit of work to install all the dependencies locally (so they don't interferer with the system's version) and then invoke gimp with a wrapper script to load the proper environmental variables so it uses libs I installed locally rather than system's. The idea is simple but involves a bit of work. I won't recommend it for new users.

---

### Post by Brian_G_M on 2020-07-28
> **monkeybrain20122 said:**
> No, gimp installed with snap can't use darktable or any external plugin (e.g gmic) since it is sandboxed, see this [thread]("https://discourse.ubuntu.com/t/gimp-woes-in-20-04/15828/7"). But gimp installed from Ubuntu's repo would work normally. The ppa hasn't been updated for months  and is probably broken. So just 
```
sudo apt update
sudo apt install gimp
```

This is a slightly older version [2.10.18 instead of 2.10.20] but it works.
 

If you must have 2.10.20, the gimp [appimage]("https://appimage.github.io/GIMP/") also works, I tested it.

I think they should really remove the snaps that don't work properly from the app store or at least put some big warnings about their limitations for new users.Otherwise it conveys the bad impression that Ubuntu is broken and hurts its reputation for new users.

I suggest you install synaptic to manage your software, it really makes life a lot easier. As a new user I had a lot of problems with these sudo apt install x commands from online tutorials because the name of x might have changed and how would I know the proper name of x in the first place? But synaptic has good search function so you don't need to remember those mysterious names.  It provides much more fine grain control and complete listing as the software store (the software store only shows end user software, not libs and components)

There is also no snap in synaptic, all the packages are deb, so there is no gotcha like installing from the software store (which does label which package is snap but it is not prominently displayed, you have to go to the description and check the provider, i f it says snapcraft then it is a snap)
```

sudo apt install synpatic
```

P.S. The tar file is source code, it is quite daunting to compile gimp from source since all the dependencies issues. I have gimp 2.10.20 on Ubuntu 16.04 compiled from source but it took a bit of work to install all the dependencies locally (so they don't interferer with the system's version) and then invoke gimp with a wrapper script to load the proper environmental variables so it uses libs I installed locally rather than system's. The idea is simple but involves a bit of work. I won't recommend it for new users.

Fantastic, thanks. I used the code you gave me above, and it worked! I have GIMP installed and  working with DarkTable. All good. Thanks again, Brian

---

### Post by william-6 on 2021-02-07
I have the same problem - 100k raw files that I've processed using ufraw and I do not want to give it (or all the settings that I've saved for each image) up.  It's really annoying because the loss of this application seems to be due to a -Werror compile flag in gtkimageview... and nobody has bothered to change that.

I have tried using darktable but the image quality is execrable.

Things are so dire that at this point I am running ufraw in a windows VM using cygwin because at least there is a binary available, though it is mighty mighty crashy.

---

