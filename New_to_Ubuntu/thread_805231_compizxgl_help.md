---
title: "compiz/xgl help"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by hardy_hardy on 2008-05-23
I get this in the terminal:

lg@lg-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

lg@lg-laptop:~$ 


I don't know what to do about the last part?

Any help would be appreciated!

---

### Post by cubeist on 2008-05-23
Have you installed the restricted nvidia drivers yet?

type this in terminal and post the results

```
glxinfo | grep direct
```

---

### Post by hardy_hardy on 2008-05-23
here is the results

lg@lg-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

### Post by cubeist on 2008-05-23
You need to install the nvidia restricted driver.  You will find it in System/Admin/Hardware Drivers

---

### Post by hardy_hardy on 2008-05-23
It says it has been enabled and in use

---

### Post by hardy_hardy on 2008-05-23
what kind of default effects would I see if compiz was actually working?

When I move a window it gets distorted and rubbery looking...

If it is working why does the terminal say that? 

Thanks

---

