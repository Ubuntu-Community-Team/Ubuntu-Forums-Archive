---
title: "Hacking a digital camera"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rab4567 on 2008-07-13
I was wondering if its possible to hack into a samsung s730 point and shoot camera and make it a web cam. Can it be done?

---

### Post by rushikesh988 on 2008-07-13
most of Digital cameras have that facility 

my kodak DX cam also supoorts that

---

### Post by unutbu on 2008-07-13
There might be a better way, but you might find this interesting:

Try connecting your camera to the computer, turn it on and then run

```
gphoto2 --capture-image
```

Does it snap a picture?

---

### Post by BLTicklemonster on 2008-07-13
Bah

bill@bill-desktop:~$ gphoto2 --capture-image
                                                                               
*** Error ***              
This camera can not capture.
ERROR: Could not capture.
*** Error (-6: 'Unsupported operation') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --capture-image

Please make sure there is sufficient quoting around the arguments.


using a Sony Mavica mvc fd100. Figured it wouldn't work...

---

### Post by rab4567 on 2008-07-14
I got almost the same message

*** Error ***              
This camera can not capture.
ERROR: Could not capture.
*** Error (-6: 'Unsupported operation') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --capture-image

Please make sure there is sufficient quoting around the arguments.

I'm not sure what to do next is there a a protocol to access the camera?

---

### Post by t0p on 2008-07-14
> **rab4567 said:**
> 
I'm not sure what to do next

I'd suggest getting a different camera, as the one you've got clearly will not serve as a webcam.

---

