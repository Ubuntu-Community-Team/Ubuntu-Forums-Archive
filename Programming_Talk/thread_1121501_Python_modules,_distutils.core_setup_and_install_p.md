---
title: "Python modules, distutils.core setup and install paths"
date: 2009-04-10
forum: Programming Talk
---

### Post by deepspring on 2009-04-10
Hi Guys,

I've got a strange problem with Python 2.6 distutils.core.setup ignoring sys.prefix and sys.exec_prefix when installing applications.

Lets say I have application to setup, and the module includes extra files needed to be run. I create a setup.py file like so:
```

import sys, os
from distutils.core import setup

# define search paths to look for data files in constants.py
const_file = open(os.path.join('MyApp', "constants.py"), 'w')
const_file.write("MYAPP_UI = '%s/share/MyApp/'\n" % sys.prefix)
const_file.write("USER_DATA = '~/.MyApp/'\n")
const_file.close()

# Read in myapp.desktop.in template file
infile = open(os.path.join('data', 'MyApp', 'MyApp.desktop.in'))
# Replace all @PREFIX@ with prefix defined by sys.prefix
data = infile.read().replace('@PREFIX@', sys.prefix)
infile.close()

# Create the updated myapp.desktop file
outfile = open(os.path.join('data', 'MyApp', 'MyApp.desktop'), 'w')
outfile.write(data)
outfile.close()

setup(name = "MyApp",
    version = "0.0.1",
    description = "Ground breaking, earth shatteringly important application",
    author = "deepspring",
    author_email = "me@nospam.org",
    url = "http://somesite.com/MyApp",
    packages = ['MyApp'],
    scripts = ['myapp'],
    license = "GNU GPL Version 3",
    data_files=[('data/MyApp', ['share/MyApp/MyApp.glade']),
                ('data/MyApp', ['share/MyApp/icon.svg']),
                ('data/MyApp', ['share/applications/MyApp.desktop'])]
)

```Under Ubuntu 8.10 (w/ Python 2.5), distutils.core.setup obeys the prefixes set by sys.prefix (set to '/usr') and sys.exec_prefix (set to '/usr'), and the application would be installed like so:

[LIST]
[*]The script "myapp" gets installed to sys.prefix + "/bin/"
[*]The package "MyApp" (module) gets installed to sys.prefix + "/lib/python2.5/site-packages/"
[*]The data files "MyApp.glade" and "icon.svg" get installed to sys.prefix + "/share/MyApp/"
[*]The data file "MyApp.desktop" gets installed to sys.prefix + "/share/applications"
[/LIST]


The application works perfectly.

But, when I install the same application under Ubuntu 9.04 (w/ Python 2.6), sys.prefix (set to '/usr') and sys.exec_prefix(set to '/usr') are ignored and the application is setup with the prefix "/usr/local" like so:

[LIST]
[*]The script "myapp" gets installed to "/usr/local/bin/"
[*]The package "MyApp" (module) gets installed "/usr/local/lib/python2.6/dist-packages/"
[*]The data files "MyApp.glade" and "icon.svg" get installed to "/usr/local/share/MyApp/"
[*]The data file "MyApp.desktop" gets installed to "/usr/local/share/applications"
[/LIST]


The application breaks.

If I force a prefix of "/usr/local" in Python2.6, the package gets installed to "/usr/local/lib/python2.6/site-packages" which is ignored by Python.

Is there any sane way to correct this problem so the application remains backwards compatible? as not eveyone uses the latest version of Ubuntu.

**Edit:** here is the is the output of sys.path on Ubuntu 9.04 (Python 2.6):
```

['', '/usr/lib/python2.6', '/usr/lib/python2.6/plat-linux2', '/usr/lib/python2.6/lib-tk', '/usr/lib/python2.6/lib-old', '/usr/lib/python2.6/lib-dynload', '/usr/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages/PIL', '/usr/lib/python2.6/dist-packages/gst-0.10', '/var/lib/python-support/python2.6', '/usr/lib/python2.6/dist-packages/gtk-2.0', '/var/lib/python-support/python2.6/gtk-2.0', '/usr/local/lib/python2.6/dist-packages']

```

---

### Post by deepspring on 2009-04-10
Ok, I found a possible solution, but it means refactoring a lot of things, like where data files are located on a hard disk, and total rethink of the whole dynamically generated desktop file.

So I'm looking at using pkg_resources module.

---

### Post by deepspring on 2009-04-10
Ok so pkg_resources isn't what I'm looking for.

---

### Post by deepspring on 2009-04-10
After everything, I've settled on the following...

```

import sys, os, platform
from distutils.core import setup

# Get current Python version
python_version = platform.python_version_tuple()

# Setup the default install prefix
prefix = sys.prefix

# Check our python is version 2.6 or higher
if python_version[0] >= 2 and python_version[1] >= 6:
    ## Set file location prefix accordingly
    prefix = '/usr/local'

# Get the install prefix if one is specified from the command line
for arg in sys.argv:
    if arg.startswith('--prefix='):
        prefix = arg[9:]
        prefix = os.path.expandvars(prefix)

# define search paths to look for data files in constants.py
const_file = open(os.path.join('MyApp', "constants.py"), 'w')
const_file.write("MYAPP_UI = '%s/share/MyApp/'\n" % prefix)
const_file.write("USER_DATA = '~/.MyApp/'\n")
const_file.close()

# Read in myapp.desktop.in template file
infile = open(os.path.join('data', 'MyApp', 'MyApp.desktop.in'))
# Replace all @PREFIX@ with prefix defined by prefix
data = infile.read().replace('@PREFIX@', prefix)
infile.close()

# Create the updated myapp.desktop file
outfile = open(os.path.join('data', 'MyApp', 'MyApp.desktop'), 'w')
outfile.write(data)
outfile.close()

setup(name = "MyApp",
    version = "0.0.1",
    description = "Ground breaking, earth shatteringly important application",
    author = "deepspring",
    author_email = "me@nospam.org",
    url = "http://somesite.com/MyApp",
    packages = ['MyApp'],
    scripts = ['myapp'],
    license = "GNU GPL Version 3",
    data_files=[('data/MyApp', ['share/MyApp/MyApp.glade']),
                ('data/MyApp', ['share/MyApp/icon.svg']),
                ('data/MyApp', ['share/applications/MyApp.desktop'])]
)

```I hope this helps someone else.

---

### Post by Umang on 2009-12-06
Hi,
I'm having the same problem. However, I don't like this hacky way of dealing with the problem. Because if they do fix the problem (and I have no idea why they haven't), then the files will start going back to /usr/ but we'll be reading it from /usr/local/.

Also, if you read this( [http://docs.python.org/distutils/setupscript.html#installing-additional-files](http://docs.python.org/distutils/setupscript.html#installing-additional-files) ), it says that the files will be installed relative to sys.prefix. That is not happening now. So I'm hesitant to put /usr/local directly if Python > 2.6.

This method will also render distutils useless to install the package on a non Unix OS.

Any further ideas?

(Sorry for reviving this old thread)

---

### Post by deepspring on 2009-12-06
> **Umang said:**
> Hi,
I'm having the same problem. However, I don't like this hacky way of dealing with the problem. Because if they do fix the problem (and I have no idea why they haven't), then the files will start going back to /usr/ but we'll be reading it from /usr/local/.

Also, if you read this( [http://docs.python.org/distutils/setupscript.html#installing-additional-files](http://docs.python.org/distutils/setupscript.html#installing-additional-files) ), it says that the files will be installed relative to sys.prefix. That is not happening now. So I'm hesitant to put /usr/local directly if Python > 2.6.

This method will also render distutils useless to install the package on a non Unix OS.

Any further ideas?

(Sorry for reviving this old thread)

The way we got around it, we installed all the python module files to the default python module path, but moved all the extra files (bash scripts, glade files, icons, etc) to a specific folder in the "/usr/share" folder using static path declarations in the "setup.py" file and in the python module files that called those specific files.

For example, instead of this:
```

#!/usr/bin/env python
#########################################################################
## Import required modules
import os, sys, platform
from distutils.core import setup

## Get current Python version
python_version = platform.python_version_tuple()

## Setup the default install prefix
set_prefix = sys.prefix

## Check our python is version 2.6 or higher
if python_version[0] >= "2" and python_version[1] >= "6":
    ## Set file location prefix accordingly
    set_prefix = '/usr/local'

## Get the install prefix if one is specified from the command line
for arg in sys.argv:
    if arg.startswith('--prefix='):
	prefix = arg[9:]
	set_prefix = os.path.expandvars(prefix)

## Make sure people are using Python 2.5 or higher
if python_version[0] < "2" and python_version[1] < "5":
    print "The installed version of Python is to old."
    print "We require as a minimum Python 2.5.x."
    sys.exit(1)

## Create the contents of the KernelCheck/constants.py file
const_file = open(os.path.join('KernelCheck', 'constants.py'), 'w')
const_file.write("KCHECK_PREFIX = '%s/share/kernelcheck/'\n" % set_prefix)
const_file.write("KCHECK_UI = KCHECK_PREFIX\n")
const_file.write("KCHECK_PIXMAPS = '%s/share/kernelcheck/pixmaps/'\n" % set_prefix)
const_file.write("KCHECK_SCRIPTS = '%s/share/kernelcheck/scripts/'\n\n" % set_prefix)
const_file.close()

## Update applications/kernelcheck.desktop file with new prefix
in_file = open(os.path.join('share', 'applications', 'kernelcheck.desktop.in'))
data = in_file.read().replace('@PREFIX@', set_prefix)
in_file.close()

out_file = open(os.path.join('share', 'applications', 'kernelcheck.desktop'), 'w')
out_file.write(data)
out_file.close()

## Prepare setup() directive
setup(name = "kernelcheck",
    version = "1.2.5",
    description = "Build the latest kernel",
    author = "Master Kernel",
    author_email = "master.kernel.contact@gmail.com",
    url = "http://kcheck.sf.net",
    packages = ['KernelCheck'],
    scripts = ['kernelcheck'],
    license = "GNU GPLv3",
    data_files=[('share/kernelcheck/', ['share/kernelcheck/kernelcheck.glade']), 
                ('share/kernelcheck/', ['share/kernelcheck/terminal.glade']),
                ('share/kernelcheck/', ['share/kernelcheck/fixed.list']),
                ('share/kernelcheck/', ['share/kernelcheck/License.txt']),
                ('share/kernelcheck/scripts', ['share/kernelcheck/scripts/kscript.sh']), 
                ('share/kernelcheck/scripts', ['share/kernelcheck/scripts/build.py']),
                ('share/kernelcheck/scripts', ['share/kernelcheck/scripts/main.py']),
                ('/usr/share/pixmaps', ['share/kernelcheck/pixmaps/kernelcheck.png']),
                ('share/kernelcheck/pixmaps', ['share/kernelcheck/pixmaps/KernelCheckLogo.png']),
                ('share/kernelcheck/pixmaps', ['share/kernelcheck/pixmaps/kernelcheck.svg']),
                ('share/kernelcheck/pixmaps', ['share/kernelcheck/pixmaps/side.png']),
                ('/usr/share/applications', ['share/applications/kernelcheck.desktop'])]

)

```

We did this:
```

#!/usr/bin/env python
#########################################################################
## Import required modules
import os, sys, platform
from distutils.core import setup

## Get current Python version
python_version = platform.python_version_tuple()

## Make sure people are using Python 2.5 or higher
if python_version[0] < "2" and python_version[1] < "5":
    print "The installed version of Python is to old."
    print "We require as a minimum Python 2.5.x."
    sys.exit(1)

## Prepare setup() directive
setup(name = "kernelcheck",
    version = "1.2.5",
    description = "Build the latest kernel",
    author = "Master Kernel",
    author_email = "master.kernel.contact@gmail.com",
    url = "http://kcheck.sf.net",
    packages = ['KernelCheck'],
    scripts = ['kernelcheck'],
    license = "GNU GPLv3",
    data_files=[('/usr/share/kernelcheck/', ['share/kernelcheck/kernelcheck.glade']), 
                ('/usr/share/kernelcheck/', ['share/kernelcheck/terminal.glade']),
                ('/usr/share/kernelcheck/', ['share/kernelcheck/fixed.list']),
                ('/usr/share/kernelcheck/', ['share/kernelcheck/License.txt']),
                ('/usr/share/kernelcheck/scripts', ['share/kernelcheck/scripts/kscript.sh']), 
                ('/usr/share/kernelcheck/scripts', ['share/kernelcheck/scripts/build.py']),
                ('/usr/share/kernelcheck/scripts', ['share/kernelcheck/scripts/main.py']),
                ('/usr/share/pixmaps', ['share/kernelcheck/pixmaps/kernelcheck.png']),
                ('/usr/share/kernelcheck/pixmaps', ['share/kernelcheck/pixmaps/KernelCheckLogo.png']),
                ('/usr/share/kernelcheck/pixmaps', ['share/kernelcheck/pixmaps/kernelcheck.svg']),
                ('/usr/share/kernelcheck/pixmaps', ['share/kernelcheck/pixmaps/side.png']),
                ('/usr/share/applications', ['share/applications/kernelcheck.desktop'])]
)

```

Forcing a static path saved us a lot of effort.

---

### Post by Umang on 2009-12-06
I just had a discussion with someone on the distutils IRC. Turns out that if you do python2.5 it works perfect (even in Karmic). Python 2.6 is installing it in /usr/local.

While trying to debug, we found that the relavant file had been patched by Ubuntu. I'm going to contact the Ubuntu developer sometime this week or next week explaining everything (because I think we've almost pin-pointed the problem) and I'll let you know what I find out.

---

### Post by Umang on 2009-12-10
Hi!
It's an Ubuntu specific problem. It is actually intended: [https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027439.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-February/027439.html)

The solution is to install it as:
```
$sudo python setup.py install --install-layout=deb
```

I am still to try packaging it as a .deb, but as far as I understand, --install-layout=deb will automatically be added as an option when packaging.

---

### Post by Umang on 2009-12-14
Confirmed. If you package it as a .deb ([https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)), then --install-layout=deb is automatically passed. That means that you should write setup.py as you are supposed to (no hacking around) and package it using a .deb. 

On all other OSs setup.py will work as expected. 

If your users are using setup.py to install on Ubuntu, ask them to pass the --install-layout=deb at the end.

---

