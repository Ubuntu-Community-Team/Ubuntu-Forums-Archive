---
title: "Python to download and install .debs"
date: 2006-01-25
forum: Programming Talk
---

### Post by wolphin on 2006-01-25
Hi,

I'm learning Python and was wondering what I would need to type to make the script download a .deb using wget and then install it with dpkg, and let the user know what it is doing by printing something like "Downloading *package*" or "Installing *package*". Could someone please get me started by writing a quick example with just one .deb being downloaded and installed?

Thanks in advance,

Wolphin

---

### Post by ubuntumaneh on 2006-01-25
Basically what you are going to use is the module os, with the function system for the command wget and dpkg. Something like:

import os

print "doonloading"
os.system('wget [options] URL_name_of_deb')
print "installing"
os.system('sudo dpkg -i address_and_name_of_deb')

This is the core, I think.

---

### Post by gord on 2006-01-25
you might be better going with the newer SubProcess package for running other files, i also think there might be python modules you can use, i know there is an Apt python module

---

### Post by ubuntumaneh on 2006-01-25
Gord, thanks a lot for the tip. I was not aware of this new module.
 
[http://python.org/doc/current/lib/module-subprocess.html](http://python.org/doc/current/lib/module-subprocess.html) 

I haven't found any apt module in the site above, though.

---

### Post by ow50 on 2006-01-25
[QUOTE=ubuntumaneh]I haven't found any apt module in the site above, though.[/QUOTE]
Install package "python-apt". There's some examples included in the package, installed to usr/share/doc/python-apt/examples/. I haven't found any proper documentation for the apt module.

---

### Post by wolphin on 2006-01-25
Thanks for the help guys! I'll read up on SubProcess and python-apt. :D

Cheers,

-Wolphin

---

