---
title: "Unity 3D and Asus EAH3650 SILENT/HTDI/512M"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by JdeP on 2012-05-04
My (very) old graphics card won't run Unity in 3D mode.

I have been offered an Asus EAH3650 SILENT/HTDI/512M very cheap (by a reliable friend): it's much more recent than my previous graphics card, and quieter.

If I run ```
/usr/lib/nux/unity_support_test -p
``` in a terminal I get this output:

```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

My question is: is it just a matter of time waiting for someone to write a suitable driver to enable this card to run Unity 3D, or will it never be supported? (Is there any way to know if anyone is already working in this?)
 
Thanks in advance.

---

### Post by NikTh on 2012-05-04
Hi , 
give the output of this command also ```
lspci -nnk | grep -iA2 vga
``` 
Thanks

---

### Post by JdeP on 2012-05-04
> **NikTh said:**
> Hi , 
give the output of this command also ```
lspci -nnk | grep -iA2 vga
``` 
Thanks

Thanks for responding. The output is this:

```
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 3600 Series] [1002:9598]
	Subsystem: ASUSTeK Computer Inc. Device [1043:01e4]
	Kernel driver in use: radeon

```

---

### Post by NikTh on 2012-05-04
> **JdeP said:**
> Thanks for responding. The output is this:

```
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 3600 Series] [1002:9598]
    Subsystem: ASUSTeK Computer Inc. Device [1043:01e4]
    Kernel driver in use: radeon

```
Hi,
Do you want to test the proprietary AMD driver ? 
I see that you have the open source now. Open source is more stable but it has not so good 3D support. 
Run this command from terminal (ctrl +alt+t)
```
jockey-gtk
``` 
see the window and activate the additional driver .. i prefer the one without (post-release). 
Reboot for driver take effects. 
Thanks

---

### Post by JdeP on 2012-05-04
Many thanks, NikTh. I'm willing to try ... but before I do, can you please tell me how to revert to my present driver if the change is not good?!

Thanks again.

---

### Post by JdeP on 2012-05-04
> **JdeP said:**
> Many thanks, NikTh. I'm willing to try ... but before I do, can you please tell me how to revert to my present driver if the change is not good?!

Thanks again.

Actually, I went ahead and this is what happened: [I have truncated the beginning]
```
  File "/usr/lib/python2.7/os.py", line 294, in walk
    for x in walk(new_path, topdown, onerror, followlinks):
  File "/usr/lib/python2.7/os.py", line 294, in walk
    for x in walk(new_path, topdown, onerror, followlinks):
  File "/usr/lib/python2.7/os.py", line 284, in walk
    if isdir(join(top, name)):
  File "/usr/lib/python2.7/genericpath.py", line 44, in isdir
    return stat.S_ISDIR(st.st_mode)
  File "/usr/lib/python2.7/stat.py", line 41, in S_ISDIR
    return S_IFMT(mode) == S_IFDIR
RuntimeError: maximum recursion depth exceeded


Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 274, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 819, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 212, in available
    return self.handlers.keys()
AttributeError: 'Backend' object has no attribute 'handlers'
```

---

### Post by NikTh on 2012-05-04
> **JdeP said:**
> Many thanks, NikTh. I'm willing to try ... but before I do, can you please tell me how to revert to my present driver if the change is not good?!

Thanks again.
Hi,
If you want to revert then you must deactivate the driver from additional drivers window.. 
or
from terminal 
```
sudo apt-get remove fglrx
```and reboot

Now 
run these commands to your terminal 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get autoclean 
sudo apt-get update 
``` Copy-paste them from here one by one if you want for more accuracy . 

Then give the result of this command 
```
apt-cache policy fglrx
```Thanks

---

### Post by JdeP on 2012-05-04
Thanks again.

I ran the three sudo commands, one after another, and then the ```
apt-cache policy fglrx
```
one. The output is:
```
fglrx:
  Installed: (none)
  Candidate: 2:8.960-0ubuntu1
  Version table:
     2:8.960-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages

```

I hope this helps!

---

### Post by NikTh on 2012-05-04
> **JdeP said:**
> Thanks again.

I ran the three sudo commands, one after another, and then the ```
apt-cache policy fglrx
```one. The output is:
```
fglrx:
  Installed: (none)
  Candidate: 2:8.960-0ubuntu1
  Version table:
     2:8.960-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages

```I hope this helps!
Hi , 
Ok , as you can see you have not installed fglrx (proprietary AMD) driver. You are now at the begin again. 
Now try to install it again.. from terminal 
```
sudo apt-get install fglrx
``` if all goes well then reboot for driver to take effect , if something wrong post the output of errors. 

Thanks

---

### Post by JdeP on 2012-05-04
I ran sudo apt-get install fglrx which seemed to go fine (no error messages) and returned me to my normal $ prompt.

I rebooted and it seemed to boot OK, and I entered my password at the usual login screen. This took me to my desktop, with a launcher at the left, but no top panel, and although the mouse is active, I cannot launch any of the programs on the launcher, and CTRL+ALT+T does not bring up a terminal. I re-started the machine manually (no other obvious way to shut it down) and the same thing happens.

I tried again and selected Unity 2D at the login screen, and I got back to a fully-functioning desktop.

Do you think there is an easy way to solve this, or would it be more sensible to conclude that the alternate driver does not work with my setup, and revert to the Open Source one?

Thanks again for all your help and advice!

---

### Post by JdeP on 2012-05-04
Actually I spoke too soon: now my dual monitors only work in 'mirror' mode. 

If I go into 'Displays' and uncheck 'Mirror displays' and click the 'Apply' button I get a dialog that says 
'The selected configuration for displays could not be applied: required virtual size does not fit available size [... etc.]'

I think it would be best to roll back to my original Open Source driver, if you can tell me how to do that!

Thanks again

---

### Post by JdeP on 2012-05-04
> **JdeP said:**
> I think it would be best to roll back to my original Open Source driver, if you can tell me how to do that!

I have now managed to do this by myself, but thanks for all previous help.

---

### Post by NikTh on 2012-05-05
> **JdeP said:**
> I have now managed to do this by myself, but thanks for all previous help.

Hi , 
and sorry for delay 
If you want to go back to pre-installed open source driver then 
```
sudo apt-get remove fglrx
``` this command will remove the proprietary driver and activate the pre-installed open source. 
Reboot. 
Thanks.

---

