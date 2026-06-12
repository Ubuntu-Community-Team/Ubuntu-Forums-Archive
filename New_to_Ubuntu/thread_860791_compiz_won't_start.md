---
title: "compiz won't start"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by erans on 2008-07-15
Can't seem to get compiz or the "Normal" setting for Visual Effects to work. It worked before, but then I formatted and reinstalled Ubuntu and now it's a no-go. 

Here's the output of starting compiz from console: 

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5964 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

---

### Post by jbrown96 on 2008-07-17
Did you install the proprietary graphics driver if you are using an Nvidia or ATI graphics card? System-->Administration-->Hardware Drivers

---

