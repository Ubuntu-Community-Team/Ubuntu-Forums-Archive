---
title: "Having problems with 3d graphics"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by oDEIMOSo on 2008-08-03
I`m having problems with my graphics all of a sudden , only simple programs are working and compiz fusion just dosn`t work at all now !!!! Can someone help me ???????

---

### Post by northern lights on 2008-08-03
Can you please post the output of ```
sudo lshw -C display
```Thank you.

---

### Post by oDEIMOSo on 2008-08-03
This is what i got when i put in the code .
PCI (sysfs)  
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV31 [GeForce FX 5600]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5

---

### Post by northern lights on 2008-08-03
Run ```
sudo apt-get update
sudo apt-get install nvidia-xconfig nvidia-settings
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```

The last line might be superfluous.

---

### Post by oDEIMOSo on 2008-08-03
ok my games and other things are working again , but my compiz fusion is not , and when i try to play some shooter games my monitor says out of range .

---

### Post by northern lights on 2008-08-03
Can you repost 'lshw -C display'? Since now you should be fine. Can you also post the output of ```
cat /etc/X11/xorg.conf
```

---

