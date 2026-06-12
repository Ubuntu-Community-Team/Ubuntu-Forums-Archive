---
title: "Tried to instal google earth and broke Synaptic package manager"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by kanati on 2008-05-20
Hey,
   Not sure how I managed this but...
I tried to install google earth on 8.04 using the instructions found here: [http://www.ubuntu-unleashed.com/2008/05/howto-install-google-earth-easiest-way.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-google-earth-easiest-way.html).
It all went well until I was asked to accept the EULA.  The EULA was just text in the terminal with no 'accept' button, so I couldn't figure out how to accept it.  The only thing I could do was close the terminal.  Google earth now shows up in the applications menu but when I click it I get "Failed to execute child process "googleearth" (No such file or directory)".  So I went into synaptic to try and remove it but now when I try and launch the Synaptic package manager I get this warning:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What just happened?  Any idea how to fix synaptic?  Also, does anyone know how to either uninstall the now broken install of google earth?  How was I supposed to accept that EULA?

---

### Post by philinux on 2008-05-20
Run 

sudo dpkg --configure -a

google earth is in synaptic too.

---

### Post by kanati on 2008-05-20
Thanks, synaptic is working again.  What exactly happened there?  And what did that command do to fix it?

---

### Post by philinux on 2008-05-20
It fixed the broken install. Maybe you had an internet glitch or something that prevented the install going smoothly.

---

### Post by barnex on 2008-05-20
To easily install google software, I recommend using the google repositories. ad [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) to your software sources, you can then painlessly install google earth with ```
sudo apt-get install google-earth
``` This also works for picasa.

---

### Post by Donalb on 2008-05-23
Hey,
 Here's what I got after instally the google repositories

"Package google-earth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package google-earth has no installation candidate"

---

### Post by Maestro23 on 2008-05-23
> **Donalb said:**
> Hey,
 Here's what I got after instally the google repositories

"Package google-earth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package google-earth has no installation candidate"

Need to add the Medibuntu Repository.

[https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu)

---

