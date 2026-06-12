---
title: "how can I send a plotfile to plotter through the USB port?"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by s1baker on 2013-04-29
hi,
On my old computer, I could send a plotfile to my big HP plotter, through
the parallel port, using this command:

```
cat  plotfile  >  /dev/lp0
```

My new computer does not have a parallel port so my plotter is 
attached to the USB port, there is not a "/dev/lp0".

What command can I use to send the plotfile to the plotter through the USB port?

I can set my plotter as the "default" printer, and then use this command:
```
lpr plotfile
``` 
It prints ok, but I get this error message in the terminal:
```
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-oldaOi/pkcs11: No such file or directory
```

I would rather just send the plotfile through the USB port using "cat".

Thanks

---

### Post by s1baker on 2013-05-01
bump 

I found that I do have a /dev/usb/lp0
but when I try a 
```
cat  plotfile  >  /dev/usb/lp0 
```

I get a 
```
bash: /dev/usb/lp0: Permission denied
```

---

