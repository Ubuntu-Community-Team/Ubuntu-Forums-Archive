---
title: "Xorg/mesa issue"
date: 2011-08-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2011-08-08
I installed the 11.7 ati drivers as per the fglrx thread and when i try to run any 3d application, i get this error:

```
evan@ubuntu-testing:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

Seems like a regression of [this bug]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012").

Anyone else having this issue? My computer's specs are in my sig. The install is completely up to date from the main server.

---

### Post by rbrick49 on 2011-08-09
> **linuxman94 said:**
> I installed the 11.7 ati drivers as per the fglrx thread and when i try to run any 3d application, i get this error:

```
evan@ubuntu-testing:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

Seems like a regression of [this bug]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012").

Anyone else having this issue? My computer's specs are in my sig. The install is completely up to date from the main server.
it should be this to test fglrx fgl_glxgears

---

### Post by dino99 on 2011-08-09
its ok on my side: nvidia 280.04 / 8500gt

oem@oem-desktop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.370 FPS
300 frames in 5.0 seconds = 59.929 FPS
300 frames in 5.0 seconds = 59.929 FPS
300 frames in 5.0 seconds = 59.929 FPS
300 frames in 5.0 seconds = 59.929 FPS

---

### Post by VinDSL on 2011-08-09
OK on my side too:  nVidia 280.13 / 7600GT

```

vindsl@Zuul:~$ glxgears
10459 frames in 5.0 seconds = 2091.313 FPS
11658 frames in 5.0 seconds = 2331.187 FPS
11652 frames in 5.0 seconds = 2326.691 FPS
12675 frames in 5.0 seconds = 2534.936 FPS
11795 frames in 5.0 seconds = 2358.873 FPS

```

---

### Post by linuxman94 on 2011-08-09
> **rbrick49 said:**
> it should be this to test fglrx fgl_glxgears

Nope, still says:
```
evan@ubuntu-testing:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

It does this with any 3D game/application.  For example, trying to launch warsow:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  31
  Current serial number in output stream:  31
```

I am using the catalyst 11.7 drivers installed from the debs that the installer built.

---

