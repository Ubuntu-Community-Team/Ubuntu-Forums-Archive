---
title: "Skype Video (and) connection problem"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Formerly on 2012-03-08
I'm not all that new to Linux, but when it comes to Skype I just can't find the fix; even when using tutorials that helped others.

1 - I tested my webcam and it works in Cheese. Yet when I go into Skype and click "Start my video" the other person cannot see me nor can I see myself. I'm not sure exactly what information would be needed to help fix this, nor how to find such just yet. It seems the more I look, the more confusing this all gets.

2 - Every now and then after Skype has been running for a while, it just crashes. I can't exit Skype and none of my messages send to the other person, nor can I see any new messages from them. Looking up it seems to be a Pulse audio issue? I'm not 100% how to fix this, after deleting the .Pulse directory it came back.

Any help would be much appreciated.

---

### Post by TeoBigusGeekus on 2012-03-08
1. Try launching skype from a terminal with this command
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by Formerly on 2012-03-08
> **TeoBigusGeekus said:**
> 1. Try launching skype from a terminal with this command
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

I don't have a person to test with at the moment, but I think this fixed issue #2 considering I don't see "Pulse Audio" in Sound Devices. But when I "test" my webcam under Video Devices it's just pitch black, even though it recognises my webcam. 

Is this normal under Ubuntu, or should I also be able to see my video feed under the test?

> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(skype:17254): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:17254): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:17254): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:17254): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


---

### Post by TeoBigusGeekus on 2012-03-08
What about this?
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```

---

### Post by Formerly on 2012-03-08
Just tried it, same results. Same error messages, and still glad to see no more "pulse audio" under Sound Devices

---

### Post by TeoBigusGeekus on 2012-03-08
> **Formerly said:**
> ...and still glad to see no more "pulse audio" under Sound Devices
Completely coincidental... unfortunately...

Can you post the output of
```
ls /usr/lib/libv4l/
```

---

### Post by Formerly on 2012-03-08
> **TeoBigusGeekus said:**
> Completely coincidental... unfortunately...

Can you post the output of
```
ls /usr/lib/libv4l/
```
ls: cannot access /usr/lib/libv4l/: No such file or directory

---

### Post by TeoBigusGeekus on 2012-03-08
Open synaptic package manager and search for libv4l.
Install it and try again.

---

### Post by Formerly on 2012-03-08
> **TeoBigusGeekus said:**
> Open synaptic package manager and search for libv4l.
Install it and try again.
Well this is odd. It's stating that libv4l-0 is already installed, and so I tried to reinstall. But received the same error stating that I don't have it

Version 0.8.5-3ubuntu installed, the latest version.

---

### Post by TeoBigusGeekus on 2012-03-08
That's odd... Can you post the output of
```
find / -iname "*libv4l*" 2>/dev/null
```
?

---

### Post by Formerly on 2012-03-08
> **TeoBigusGeekus said:**
> That's odd... Can you post the output of
```
find / -iname "*libv4l*" 2>/dev/null
```?

```
/usr/share/doc/libv4l-0
/usr/share/lintian/overrides/libv4l-0
/usr/lib/i386-linux-gnu/libv4l1.so.0
/usr/lib/i386-linux-gnu/libv4l2.so.0
/usr/lib/i386-linux-gnu/libv4lconvert.so.0
/usr/lib/i386-linux-gnu/libv4l
/var/cache/apt/archives/libv4l-0_0.8.5-3ubuntu2_i386.deb
/var/lib/dpkg/info/libv4l-0:i386.md5sums
/var/lib/dpkg/info/libv4l-0:i386.symbols
/var/lib/dpkg/info/libv4l-0:i386.postinst
/var/lib/dpkg/info/libv4l-0:i386.list
/var/lib/dpkg/info/libv4l-0:i386.postrm
/var/lib/dpkg/info/libv4l-0:i386.shlibs

```

---

### Post by TeoBigusGeekus on 2012-03-08
Ok, now post the output of
```
ls /usr/lib/i386-linux-gnu/libv4l
```

---

### Post by Formerly on 2012-03-08
> **TeoBigusGeekus said:**
> Ok, now post the output of
```
ls /usr/lib/i386-linux-gnu/libv4l
```
```
ov511-decomp  ov518-decomp  v4l1compat.so  v4l2convert.so
```

[COLOR=YellowGreen]**ov511-decomp**[/COLOR] and [COLOR=YellowGreen]**ov518-decomp**[/COLOR] are both in bold green text

---

### Post by TeoBigusGeekus on 2012-03-08
Now give
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```
and test your camera.
If that doesn't work, try with
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by Formerly on 2012-03-08
> **TeoBigusGeekus said:**
> Now give
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```and test your camera.
If that doesn't work, try with
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```

Wow, you're amazing. It's all fixed, thanks!!

---

### Post by TeoBigusGeekus on 2012-03-08
You're welcome and don't forget to mark the thread as solved.

---

### Post by markbl on 2012-03-08
Both v4l1compat.so and v4l2convert.so seem to fix skype for me. Does anybody know which is best to use?

---

### Post by TeoBigusGeekus on 2012-03-08
> **markbl said:**
> Both v4l1compat.so and v4l2convert.so seem to fix skype for me. Does anybody know which is best to use?

v4l2convert.so
It allows skype to use the more recent v4l2 library.
But with the mess that skype is...

---

### Post by markbl on 2012-03-08
> **TeoBigusGeekus said:**
> v4l2convert.so
It allows skype to use the more recent v4l2 library.

Thanks. That is what I suspected. Perhaps you should edit your post above to try v4l2convert.so first and, if that does not work, then v4l1compat.so?

---

### Post by TeoBigusGeekus on 2012-03-08
> **markbl said:**
> Thanks. That is what I suspected. Perhaps you should edit your post above to try v4l2convert.so first and, if that does not work, then v4l1compat.so?
Will do so, but skype hasn't been updated for ages; I doubt if there's gonna be any real difference - especially now, that Microsoft owns it.

---

### Post by flacone on 2012-05-06
Hello, 
I recently installed Ubuntu 12.04 64bit and the cam does not work with skype.

$ LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so skype
gives the output 
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

What can i do to get it work?

the v4l1compat.so gives the same error:
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


Thanks for any help.

---

### Post by emsitripijo on 2012-05-06
Hi,
I got the same error as flacone using the 64bit version of Mint 12.

I also tried installing and preloading the 32bit versions of [COLOR=#000000][FONT=sans-serif][FONT=Cantarell]libv4l with the same result. Webcam (Logitech Quickcam e2500) is working fine with video4linux but not with Skype.

Thanks in advance
[/FONT][/FONT][/COLOR]

---

### Post by cerda on 2012-05-15
I also have the same problem. 

> **flacone said:**
> Hello, 
I recently installed Ubuntu 12.04 64bit and the cam does not work with skype.

$ LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so skype
gives the output 
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.

What can i do to get it work?

the v4l1compat.so gives the same error:
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


Thanks for any help.

---

### Post by eipic on 2012-06-18
This work for me:

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
[CENTER]Wireshark Cookie Dump:

OKCancel[/CENTER]

---

### Post by flacone on 2012-07-04
wow! that works for me as well. I waited 3 months for this little line ;). Thank you eipic

---

### Post by kjaspan on 2012-10-24
I have concluded all my frustration by buying a Logitech C310 webcam. The the video works OOB. Audio needs to be set up in the Ubuntu Pulse Audio Volume Control. The webcam needs to be set up in the Input devices tab and the Configuration tab. Then you're GTG (good to go).

Configuration: Ubuntu 12.04 64 bit. Hardware: HP Pavilion p7-1247c with AMD 64 bit processor.

---

### Post by cloutz on 2013-01-04
Same problem, solved here:
[http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530](http://forum.ubuntu-it.org/viewtopic.php?f=95&t=546530)

):P

---

