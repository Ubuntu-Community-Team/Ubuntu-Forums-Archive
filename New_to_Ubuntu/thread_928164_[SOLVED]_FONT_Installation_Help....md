---
title: "[SOLVED] FONT Installation Help..."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Bee Wildered on 2008-09-23
Please would some kind soul tell me how to install .ttf font files into the Open Office word processor in Hardy Heron?

1.) The open office help pages state the following but the commands do not seem to work when I put them into my terminal window:

"Under UNIX based platforms, the printer administration program spadmin is provided to help you set up printers, faxes and fonts for use with the OpenOffice.org software.
Call the printer administration program spadmin as follows:
Change to the {install_path}/program directory.
Enter: ./spadmin
After it starts, the window of the printer administration program spadmin appears.
Following a server installation, the system administrator first logs on as with root privileges, and starts the printer administration program spadmin. The administrator then creates a general printer configuration file called {install_path}/share/psprint/psprint.conf for all users. All changes are immediately available to all users.
The system administrator can also add fonts for all users in the server installation. However, these fonts are available only after restarting the OpenOffice.org software."

2.) I've tried google for advice and came upon a solution which says to use Nautilus bit I'm not sure what this is/how to use it: Is this the same thing as the 'Nautilus Actions Configuration' programme?

My standard ubuntu open office does not seem to have the following fonts (but I do now have the .ttf/.TTF files for them):Times New Roman; Arial; Calibri.

Many thanks.

B.

---

### Post by benerivo on 2008-09-23
Have you tried opening synaptic package manager and installing the msttcorefonts package? If you do, then log out and back in again for the fonts to appear in openoffice.

---

### Post by Bee Wildered on 2008-09-23
Many thanks indeed,

the msttcorefonts package installation worked, however...

it did not install CALIBRI and one or two other fonts I want: any clues as to how to add them.

Cheers,

B.

---

### Post by benerivo on 2008-09-23
If you have them as .ttf files, then you'll need to find the system location that .ttf fonts are stored in. From memory it is something like /etc/X11/fonts/truetype. Once you have found the folder, then open a terminal and type ```
gksudo nautilus
```You will now have the power to delete system files so be careful. However, it is safe for you to just copy and paste your files in to the folder. Once you have done so, then you can type```
sudo dpkg-reconfigure fontconfig
```which will run a short process. Then log out and back in again.

---

### Post by Bee Wildered on 2008-09-23
Thanks again,

I found the /etc/X11/fonts folders but there is no folder within this named Truetype. There are four other folders in the Fonts folder and are named: 75dpi; 100dpi; misc; Type1. None of them appear to contain any .ttf files.

Any further clues?

Much obliged.

B.

---

### Post by benerivo on 2008-09-23
I think the location might be /usr/share/fonts/truetype/msttcorefonts/

---

### Post by Bee Wildered on 2008-09-23
Thank you,

I've found the folder and am all set to go but when I type <gksudo nautilus>

I get the following error message:

<Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
** (nautilus:5275): WARNING **: Unable to add monitor: Not supported>

Any idea on how to remedy this?

Thank you for your patuence and persistence.

B.

---

### Post by benerivo on 2008-09-23
> **Bee Wildered said:**
> Any idea on how to remedy this?No, but it looks like it is something to do with file sharing, and perhaps file permissions (see [here]("http://www.google.co.uk/search?hl=en&q=gksudo+nautilus+Nautilus-Share-Message+Called+net+usershare+info+but+it+failed&btnG=Search&meta=")). If you can't find a solution to this error, then post a new thread as it is definitely something separate to the font problem, and although not serious, it is something i would look to get fixed.

As far as just solving the font problem, the solution i outlined may be done by loading ubuntu live cd and copying and pasting the files from there - in to your ubuntu partition. Sorry i can't be of much more help for the moment (i've got to go to bed!).

---

### Post by Bee Wildered on 2008-09-23
Thanks for all of your help: much appreciated.
B.

---

