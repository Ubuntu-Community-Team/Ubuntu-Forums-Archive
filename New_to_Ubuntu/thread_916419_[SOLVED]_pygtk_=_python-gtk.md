---
title: "[SOLVED] pygtk = python-gtk?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-09-10
I downloaded and installed Comix through Synaptic. I'm using Ubuntu 8.04.

But whenever I try to load it, I get this:

```
PyGTK version 2.8.0 or higher is required to run Comix.
No version of PyGTK was found on your system.
```

Doesn't Synaptic resolve dependencies errors like this? I searched Synaptic for 'pygtk' and I have python-gtk 2.12,1 or something installed... I googled 'pygtk' and 'python-gtk' and I got the same website, so they're apparently the same package.

Can anyone help? :(

---

### Post by OutOfReach on 2008-09-10
The version in the repositories seems to be 2.12.1, and Comix needs at least 2.8.0. 
So you would need to get a newer version of pygtk. But unfortunately I do not know where you can obtain this.

---

### Post by Rolcol on 2008-09-10
> **outofreach said:**
> the version in the repositories seems to be 2.12.1, and comix needs at least 2.8.0. 
So you would need to get a newer version of pygtk. But unfortunately i do not know where you can obtain this.
2.12.1 > 2.8.0

maybe you can try: ```
sudo apt-get build-dep comix
```

Edit: looking at its dependencies, it's "python-gtk2"

[center][img]http://ubuntuforums.org/attachment.php?attachmentid=84877&d=1221100545[/img][/center]

---

### Post by akiratheoni on 2008-09-10
Don't version numbers work differently than decimals? So therefore 2.12 > 2.8?

[http://www.pygtk.org/downloads.html](http://www.pygtk.org/downloads.html)

> The latest release of PyGTK for GTK+ 2.12 is available from the following website

Thanks for the help though.

@Rolcol: It installed several other packages but I still get the same error... :(

---

### Post by Rolcol on 2008-09-10
I updated my post.  You may want to try and install "python-gtk2" on its own.

---

### Post by akiratheoni on 2008-09-10
```
abong@zantherus:~$ sudo apt-get install python-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
abong@zantherus:~$ comix
PyGTK version 2.8.0 or higher is required to run Comix.
No version of PyGTK was found on your system.
abong@zantherus:~$ 
```

=/ This is really making me mad... I thought Synaptic's purpose was to get rid of this dependency hell.

---

### Post by unutbu on 2008-09-10
What happens if you 
```

sudo apt-get remove python-gtk2
sudo apt-get install python-gtk2
```

---

### Post by akiratheoni on 2008-09-10
> **unutbu said:**
> What happens if you 
```

sudo apt-get remove python-gtk2
sudo apt-get install python-gtk2
```

During the remove command, I get this. And it looks scary. I don't want to remove deluge or anything that it says:

```
abong@zantherus:~$ sudo apt-get remove python-gtk2
[sudo] password for abong: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu dia-libs libatk1.0-dev libgda3-common libpango1.0-dev python-dbg
  python-pyogg libgdl-gnome-1-0 libboost-thread1.34.1 python2.5-dbg
  libboost-date-time1.34.1 deluge-torrent-common python-cairo-dbg
  python-pyvorbis x11proto-composite-dev python-openssl x11proto-damage-dev
  libgtk2.0-dev python-pyopenssl libxdamage-dev python-numeric-dbg libffi4-dev
  libxcomposite-dev libgda3-3 libboost-filesystem1.34.1 libgdl-1-0
  python-gobject-dbg python-gobject-dev libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte apport-gtk aptoncd apturl awn-manager-trunk comix
  compizconfig-settings-manager deluge-torrent deskbar-applet dia dia-common
  displayconfig-gtk exaile fast-user-switch-applet gdebi gedit gimp-python
  glipper gnome-app-install gnome-applets gnome-control-center gnome-games
  gnome-menus gnome-orca gnome-panel gnome-terminal hwtest-gtk jockey-gtk
  language-selector libdeskbar-tracker nautilus nautilus-cd-burner
  nautilus-image-converter nautilus-sendto nautilus-share onboard
  python-glade2 python-gmenu python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gtk2 python-gtk2-dbg python-gtk2-dev
  python-gtkhtml2 python-notify python-pyatspi python-sexy python-vte
  rhythmbox software-properties-gtk soundconverter startupmanager
  system-config-printer-gnome ubufox update-manager update-notifier
0 upgraded, 0 newly installed, 57 to remove and 6 not upgraded.
After this operation, 124MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by unutbu on 2008-09-11
Please post the output:
```

apt-cache policy python-gtk2
apt-cache policy comix
```

---

### Post by akiratheoni on 2008-09-11
> **unutbu said:**
> Please post the output:
```

apt-cache policy python-gtk2
apt-cache policy comix
```

Here it is:
```
akiratheoni@zantherus:~$ apt-cache policy python-gtk2
python-gtk2:
  Installed: 2.12.1-0ubuntu1
  Candidate: 2.12.1-0ubuntu1
  Version table:
 *** 2.12.1-0ubuntu1 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
akiratheoni@zantherus:~$ apt-cache policy comix
comix:
  Installed: 3.6.4-1.1
  Candidate: 3.6.4-1.1
  Version table:
 *** 3.6.4-1.1 0
        500 http://us.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
akiratheoni@zantherus:~$ 
```

Thanks for the help.

---

### Post by unutbu on 2008-09-12
If you open /usr/bin/comix with a text editor, you'll find that it is a python script.

Around line 47 you'll find something like this:

```
try:
    import pygtk
    pygtk.require('2.0')
    import gtk
    assert gtk.gtk_version >= (2, 8, 0)
    assert gtk.pygtk_version >= (2, 8, 0)
    import pango
    import gobject
except AssertionError:
    print ('You do not have the required versions of GTK+ and/or PyGTK ' +
    'installed.\n\n' +
    'Installed GTK+ version is ' + 
    '.'.join([str(n) for n in gtk.gtk_version]) + '\n' +
    'Required GTK+ version is 2.8.0 or higher\n\n'
    'Installed PyGTK version is ' + 
    '.'.join([str(n) for n in gtk.pygtk_version]) + '\n' +
    'Required PyGTK version is 2.8.0 or higher')
    sys.exit(1)
except:
    print 'PyGTK version 2.8.0 or higher is required to run Comix.'
    print 'No version of PyGTK was found on your system.'
    sys.exit(1)
```

One of the statements in the "try:" section is failing. Let's find out which one.

Save the following in a file named test.py:
```

#!/usr/bin/env python
print "1",
import pygtk
print "2",
pygtk.require('2.0')
print "3",
import gtk
print "4",
assert gtk.gtk_version >= (2, 8, 0)
print "5",
assert gtk.pygtk_version >= (2, 8, 0)
print "6",
import pango
print "7",
import gobject
print "8",

```

Make it executable:
```

chown 755 test.py
```

Run it:
```

./test.py
```

Please post the output.

---

### Post by akiratheoni on 2008-09-12
Here's the output:

```
akiratheoni@zantherus:~$ ./test.py
1
Traceback (most recent call last):
  File "./test.py", line 3, in <module>
    import pygtk
ImportError: No module named pygtk
akiratheoni@zantherus:~$ 
```

Is that what you're looking for?

---

### Post by unutbu on 2008-09-12
Okay, try installing python-gobject.
Then try running comix. 
If it doesn't work, please run the test.py script again and post the output.

Also please post```


ls -l /usr/share/python-support/python-gobject/pygtk.py
ls -l /var/lib/python-support/python2.5/pygtk.py
```

---

### Post by akiratheoni on 2008-09-12
python-gobject is already installed according to synaptic.

the output of test.py is:

```
akiratheoni@zantherus:~$ ./test.py 
1
Traceback (most recent call last):
  File "./test.py", line 3, in <module>
    import pygtk
ImportError: No module named pygtk
akiratheoni@zantherus:~$ 
```

Running the commands you gave me gives me this:

```
akiratheoni@zantherus:~$ ls -l /usr/share/python-support/python-gobject/pygtk.py
-rw-r--r-- 1 root root 2946 2008-07-09 08:18 /usr/share/python-support/python-gobject/pygtk.py
akiratheoni@zantherus:~$ ls -l /var/lib/python-support/python2.5/pygtk.py
lrwxrwxrwx 1 root root 49 2008-08-31 12:52 /var/lib/python-support/python2.5/pygtk.py -> /usr/share/python-support/python-gobject/pygtk.py
akiratheoni@zantherus:~$ 
```

---

### Post by unutbu on 2008-09-12
Please run
```

ls -l /usr/lib/python2.5/site-packages/python-support.pth

```
You should see 
```

  lrwxrwxrwx  1 root root     39 2008-01-15 05:15 python-support.pth -> /var/lib/python-support/python2.5/.path

```
If you do not see this link, then create it with
```

sudo ln -s /var/lib/python-support/python2.5/.path /usr/lib/python2.5/site-packages/python-support.pth

```
Try comix again. If still doesn't work, check the contents of the .pth file:
```

cat /usr/lib/python2.5/site-packages/python-support.pth

```
It should look like this:```


/var/lib/python-support/python2.5
gtk-2.0
/var/lib/python-support/python2.5/gtk-2.0

```
If yours looks different, use
```

gksu gedit /usr/lib/python2.5/site-packages/python-support.pth

```
to add any lines that are missing.

Try comix again. If it still does not work, 

Run this little script 
```

#!/usr/bin/env python
import sys
print "\n".join(sys.path)
```

and post the output.

Note: even if this works, it still leaves open the question why your system was not naturally set up this way. It should not take this kind of manual tinkering to get python modules linked up properly. Unfortunately, I don't know of a cleaner way to check and/or fix if your python installation has any more of these missing links. Of course, I might be getting ahead of myself. Let's see how this goes.

---

### Post by akiratheoni on 2008-09-12
The commands that you told me to run gave the same output as you told me it should. 

I still get this error when I run comix:

```
akiratheoni@zantherus:~$ comix
Traceback (most recent call last):
  File "/usr/local/bin/comix", line 44, in <module>
    import pygtk
ImportError: No module named pygtk

```

---

### Post by unutbu on 2008-09-13
What is the output of 
```

#!/usr/bin/env python
import sys
print "\n".join(sys.path)
```

---

### Post by akiratheoni on 2008-09-13
> **unutbu said:**
> What is the output of 
```

#!/usr/bin/env python
import sys
print "\n".join(sys.path)
```

The output is:

```
akiratheoni@zantherus:~$ ./python-test 
/home/akiratheoni
/usr/local/lib/python25.zip
/usr/local/lib/python2.5
/usr/local/lib/python2.5/plat-linux2
/usr/local/lib/python2.5/lib-tk
/usr/local/lib/python2.5/lib-dynload
/usr/local/lib/python2.5/site-packages
/usr/local/lib/python2.5/site-packages/PIL
akiratheoni@zantherus:~$ 

```

---

### Post by unutbu on 2008-09-13
akiratheoni, okay think I see the problem. But before I claim something that isn't true, please post

```
which python
ls -l /usr/local/bin/python*
ls -l /usr/bin/python*
locate python | grep bin/
echo $PYTHONPATH
dpkg -S /usr/bin/python
dpkg -S /usr/local/bin/python
```

Is there anything unusual you did regarding installing or compiling python?
A normal Hardy installation has a sys.path that looks like this:

```
/home/user/bin
/usr/lib/python25.zip
/usr/lib/python2.5
/usr/lib/python2.5/plat-linux2
/usr/lib/python2.5/lib-tk
/usr/lib/python2.5/lib-dynload
/usr/local/lib/python2.5/site-packages
/usr/lib/python2.5/site-packages
/usr/lib/python2.5/site-packages/Numeric
/usr/lib/python2.5/site-packages/PIL
/usr/lib/python2.5/site-packages/gst-0.10
/var/lib/python-support/python2.5
/usr/lib/python2.5/site-packages/gtk-2.0
/var/lib/python-support/python2.5/gtk-2.0
```

---

### Post by akiratheoni on 2008-09-13
It's been awhile since I installed python... I don't think I've ever compiled it so I must have gotten it through the repository.

Here are the commands:

```
akiratheoni@zantherus:~$ which python
/usr/local/bin/python
```
```
akiratheoni@zantherus:~$ ls -l /usr/local/bin/python*
-rwxr-xr-x 2 root root 3665775 2008-05-23 21:06 /usr/local/bin/python
-rwxr-xr-x 2 root root 3665775 2008-05-23 21:06 /usr/local/bin/python2.5
-rwxr-xr-x 1 root root    1281 2008-05-23 21:06 /usr/local/bin/python2.5-config
lrwxrwxrwx 1 root root      16 2008-05-23 21:06 /usr/local/bin/python-config -> python2.5-config
```
```
akiratheoni@zantherus:~$ ls -l /usr/bin/python*
lrwxrwxrwx 1 root root       9 2008-04-24 15:02 /usr/bin/python -> python2.5
-rwxr-xr-x 1 root root 1030732 2008-07-31 11:52 /usr/bin/python2.4
-rwxr-xr-x 1 root root 1163668 2008-07-31 11:42 /usr/bin/python2.5
-rwxr-xr-x 1 root root    1419 2008-07-31 11:41 /usr/bin/python2.5-config
-rwxr-xr-x 1 root root 3094873 2008-07-31 10:28 /usr/bin/python2.5-dbg
-rwxr-xr-x 1 root root    1423 2008-07-31 11:41 /usr/bin/python2.5-dbg-config
lrwxrwxrwx 1 root root      16 2008-04-25 22:15 /usr/bin/python-config -> python2.5-config
lrwxrwxrwx 1 root root      13 2008-09-10 19:46 /usr/bin/python-dbg -> python2.5-dbg
lrwxrwxrwx 1 root root      20 2008-09-10 19:46 /usr/bin/python-dbg-config -> python2.5-dbg-config
```
```
akiratheoni@zantherus:~$ locate python | grep bin/
/home/akiratheoni/Other/new/Flash Drive/PortableApps/ClamWinPortable/App/clamwin/bin/python23.dll
/usr/bin/dh_python
/usr/bin/python
/usr/bin/python-config
/usr/bin/python-dbg
/usr/bin/python-dbg-config
/usr/bin/python2.4
/usr/bin/python2.5
/usr/bin/python2.5-config
/usr/bin/python2.5-dbg
/usr/bin/python2.5-dbg-config
/usr/lib/debug/usr/bin/python2.5
/usr/local/bin/python
/usr/local/bin/python-config
/usr/local/bin/python2.5
/usr/local/bin/python2.5-config
/usr/sbin/update-python-modules
```
```
akiratheoni@zantherus:~$ echo $PYTHONPATH


```

^^^ that command right there gave a blank output.

```
akiratheoni@zantherus:~$ dpkg -S /usr/bin/python
python-minimal: /usr/bin/python
akiratheoni@zantherus:~$ dpkg -S /usr/local/bin/python
dpkg: /usr/local/bin/python not found.
```

---

### Post by unutbu on 2008-09-13
akiratheoni, you have two python executables on your system: /usr/bin/python and /usr/local/bin/python. /usr/local/bin/python is an incomplete installation. The problem is that 
/usr/local/bin/python is your default python, so when comix calls python, it is getting /usrl/local/bin/python which does not include pygtk.

Let's try renaming /usr/local/bin/python. This will make /usr/bin/python the default python and then comix should work. Let me know if anything else breaks... reverting is easy, or we might be able to fix it by adding the necessary modules to the /usr/bin (default Hardy) python installation.

```

cd /usr/local/bin
sudo mv python python-broken
```

That's it. Now see if comix works.

If after this change, you find that everything else continues to work, then you might want to think about deleting /usr/local/bin/python and the rest of the incomplete installation. Knowing how it was installed would be helpful at that stage, because whatever installed it might come with an uninstall script.

---

### Post by akiratheoni on 2008-09-13
THANK YOU! It works!!

I'm gonna go and thank all of your posts, you've been a great help.

I don't think I'll delete the incomplete installation though. Intrepid is right around the corner so I'll be doing a fresh install when it's released and the problem will be gone. Thank you soooo much though. Saves me a lot of time because I had to boot up a Windows XP virtual machine for another comic reader to use.

---

### Post by barx on 2009-08-26
THANKS!

Worked for me exaile and tucan were not opening. I tryed to update to 2.6, but it never works.

I'm glad that those programs back to work

---

### Post by vega113 on 2010-11-24
Thanks. It solved my problem too.

---

### Post by r_raol on 2011-06-11
Hi,

After I renamed broken python folder, I was able to resolve a similar problem. Thank you very much...

---

