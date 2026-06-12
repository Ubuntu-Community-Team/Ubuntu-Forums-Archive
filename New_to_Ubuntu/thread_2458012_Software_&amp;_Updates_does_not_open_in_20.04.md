---
title: "Software &amp; Updates does not open in 20.04"
date: 2021-02-14
forum: New to Ubuntu
---

### Post by wmrp on 2021-02-14
In order to get my 20.04 to open and play certain mp4 files and DVDs, I am supposed to give a check mark to "Software restricted by copyright or legal issue", and "Community maintained free and open source software" to access more packages. 
Now it is possible that I have already done that in the past, but since "Software & Updates" does not open and only returns an error message I am unable to find out...
Any suggestions? Thanks!

I cannot open Additional Drivers either. I have no idea what is going on.

---

### Post by grahammechanical on 2021-02-14
I am just checking as part of a process of elimination.

Someone recently asked on this forum about removing Update Manager and Update Notifier. He did not want a GUI utility as he used the command line. Have you removed anything by any chance?

What exactly is the error message that appears when you try to open Software & Updates?

If you go to /etc/apt and open sources.list you will see a list of all the repositories (sources) enabled on your system. Lines that begin with a # are comment lines and are not acted upon. Look for multiverse and restricted.

It is possible to use the command line to install some of these codecs

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://askubuntu.com/questions/56446/how-do-i-install-the-ubuntu-restricted-extras-package](https://askubuntu.com/questions/56446/how-do-i-install-the-ubuntu-restricted-extras-package)

Regards

---

### Post by wmrp on 2021-02-14
> **grahammechanical said:**
> I am just checking as part of a process of elimination.

Someone recently asked on this forum about removing Update Manager and Update Notifier. He did not want a GUI utility as he used the command line. Have you removed anything by any chance?

What exactly is the error message that appears when you try to open Software & Updates?

If you go to /etc/apt and open sources.list you will see a list of all the repositories (sources) enabled on your system. Lines that begin with a # are comment lines and are not acted upon. Look for multiverse and restricted.

It is possible to use the command line to install some of these codecs

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://askubuntu.com/questions/56446/how-do-i-install-the-ubuntu-restricted-extras-package](https://askubuntu.com/questions/56446/how-do-i-install-the-ubuntu-restricted-extras-package)

Regards

Thank you for your reply.  I did not remove anything by my knowledge. I did run the following commands earlier: 
sudo apt install ubuntu-restricted-extras
sudo apt install libdvdnav4 libdvd-pkg gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly 

When running the following, it could not find ffmpeg: 

$ ffmpeg -encoders
$ ffmpeg -decoders
$ ffmpeg -codecs

When starting Software & Updates, it says that Ubuntu experienced an internal error. There is a lot more under "details" but it won't allow copy and paste. It does mention "crash" multiple times. 

"If you go to /etc/apt and open sources.list..." Where do I find this?

---

### Post by deadflowr on 2021-02-14
> "If you go to /etc/apt and open sources.list..." Where do I find this?
In the Files program go down in the left pane to Other Locations.
In Other Locations click on Computer (it'll be at the top of the listings.
This will open the system's directory where etc is located.
click on that and then locate the apt directory.
sources.list is a file in this directory.


As far as crashes are concerned, they might be in the crash report folder.
That folder is located in the var directory.
Follow the same way to go to the etc in Files, look for the var entry in the Computer location.
There is a directory in there called crash.
Any crashes should be located in here.
(Clicking on a crash report should open them in the crash report utilty,
the crash report utility should allow you to at least read about the crash)

---

### Post by Impavidus on 2021-02-14
Or you can edit your software sources directly from command line:```
sudoedit /etc/apt/sources.list
```If you only wish to see if the right sources have been enabled, you can read the file without root permissions.

The misbehaving tool "Software & Updates" is known internally as software-properties-gtk and is a python script stored in /usr/bin/. It is contained in the package software-properties-gtk (how original...). Reinstalling that package may help, but the problem may also be caused by a related package (like software-properties-common), one of the dependencies of that package or by some configuration file with an unexpected error, causing the tool to crash.

I hope you haven't tried replacing Ubuntu's default Python. Some people try that and it leads to this kind of problems.

---

### Post by Frogs Hair on 2021-02-14
Try the following command and report the errors if any.

```
software-properties-gtk
```

---

### Post by wmrp on 2021-02-17
> **Frogs Hair said:**
> Try the following command and report the errors if any.

```
software-properties-gtk
```

$ software-properties-gtk
ERROR:dbus.proxies:Introspect error on :1.206:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 211, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 141, in __call__
    return self._connection.call_blocking(self._named_service,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.206 was not provided by any .service files

---

### Post by wmrp on 2021-02-17
> **Impavidus said:**
> Or you can edit your software sources directly from command line:```
sudoedit /etc/apt/sources.list
```If you only wish to see if the right sources have been enabled, you can read the file without root permissions.

The misbehaving tool "Software & Updates" is known internally as software-properties-gtk and is a python script stored in /usr/bin/. It is contained in the package software-properties-gtk (how original...). Reinstalling that package may help, but the problem may also be caused by a related package (like software-properties-common), one of the dependencies of that package or by some configuration file with an unexpected error, causing the tool to crash.

I hope you haven't tried replacing Ubuntu's default Python. Some people try that and it leads to this kind of problems.

I did not try to replace Python.

---

### Post by CelticWarrior on 2021-02-18
If you din't then before anything else make sure your system is fully updated:
```
sudo apt update
sudo apt full-upgrade
```
Please report back the error messages in full, if any.

---

