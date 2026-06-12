---
title: "Really cool! Kinetic pointer movement for Synaptics touchpad driver"
date: 2008-12-12
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2008-12-12
I came to the realization recently that my Synaptics touchpad is an unintuitive input device. Now, the hardware itself is fine; it has a nice feel, it supports multi-finger clicking and it is reasonably big.

My problem is entirely with software! The way I must laboriously push my finger around this thing seems unnatural. Being a touch interface, it would make way more sense if I was in more direct contact with the pointer. The tap to click is on the right track, but what about moving the pointer?

So I set out to do just that. I downloaded the touchpad driver source (via apt-get source; don't shoot me please), let out a few agonized screams about how it is indented, then set to work.
It's actually a really simple hack, too. There is some tweaking to be done, but the concept is there.
If you haven't guessed it, the pointer with this modified driver now behaves a lot like that fancy kinetic scrolling stuff, except even better! Normal pointer movement still works fine since people generally stop at the end of a movement while still touching the pad, and if not are likely to click it again in a moment. However, if the finger is lifted *while moving* (a flicking motion), the pointer keeps sliding for a little while :)
In the future, I'll hopefully have a smarter friction calculation that works with finger pressure to determine how much drag to create, and the ability to configure friction coefficient. (For now, I have forgotten my physics lessons so have a really cheesey, hacked together and ugly algorithm).

Here is the source code!
[https://code.edge.launchpad.net/~dylanmccall/+junk/synaptics-kinetic-pointer](https://code.edge.launchpad.net/~dylanmccall/+junk/synaptics-kinetic-pointer)

Should be possible to download that, then run dpkg-buildpackage and install the resulting package. If not, I guess I'll stop being lazy and merge my changes with an actual real git checkout from upstream.
(Note that this has the same package version as that of Intrepid Ibex, so you won't forget to replace it with the official one when finished).

Have a spare mouse on the ready and be aware of how to disable the touchpad. It could very well crash xorg.

There are a few things I would love to know:

* Is there a standard kinetic scrolling algorithm for GNOME, for example, that I could adapt to this? I am not completely satisfied with how this feels.

* Is it possible for a higher level application outside of the driver to do stuff like this? The really important information is finger data; whether the finger is touching the pad, for example, and how heavily. (Naturally, this would be a mess if it started influencing the pointer as controlled by a computer mouse, since mice can't tell when they are being touched).

* How do you like it? For me, it is sometimes a tad erratic; sometimes the pointer flies to the top left of the screen without reason when it is gliding. I'm wondering if that is a quirk with my touchpad (maybe it's sending really huge numbers at some point that other functions are smart enough to ignore), or (more likely) a bug in my code.

---

### Post by mssever on 2008-12-12
Interesting concept. I'd try it, except my toughpad is so small that I've configured the entire thing to simply scroll vertically. (I've got a ThinkPad, so I use the TrakPoint for pointer movement.)

---

### Post by Mr. Picklesworth on 2008-12-14
Yippee! It is now vastly improved. Friction is calculated better, it is based on a speed and angle instead of seperate X and Y components, and it is configurable!

[Same place]("https://code.edge.launchpad.net/~dylanmccall/+junk/synaptics-kinetic-pointer") as before. Runtime configuration via synclient does not seem to work yet, but via xorg works fine. Here is an example configuration that feels right on my touchpad:
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "PointerGlide" "1"
    Option         "PointerGlideMaxSpeed" "1"
    Option         "PointerGlideFriction" "0.0035"
    Option         "SHMConfig" "1"
EndSection
```

Max speed is in pixels / millisecond; my setting lets the pointer glide at a maximum of 1000 pixels in a second. Friction is such a tiny number because the pointer is essentially weightless.

Now all I have to do is find out how the heck they are setting the version number for this package and make a PPA.

---

### Post by andrek on 2010-09-08
Hey Dylan, sorry for bumping a 2-year old thread but I'm really excited to see this. Is this still working? I'd love to try it out on my Maverick installation (I'm using a synaptic touchpad of course).

I got the source from bzr and ran dpkg-buildpackage. During the "make" stage, I'm getting:
```
cd obj-x86_64-linux-gnu && /usr/bin/make
make[1]: Entering directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu'
/usr/bin/make  all-recursive
make[2]: Entering directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu'
Making all in include
make[3]: Entering directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu/include'
Making all in src
make[3]: Entering directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src -I.. -I../../include/    -Wall -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../../src -MT synaptics.lo -MD -MP -MF .deps/synaptics.Tpo -c -o synaptics.lo ../../src/synaptics.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../../src -I.. -I../../include/ -Wall -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1 -I../../src -MT synaptics.lo -MD -MP -MF .deps/synaptics.Tpo -c ../../src/synaptics.c  -fPIC -DPIC -o .libs/synaptics.o
../../src/synaptics.c: In function &#8216;DeviceInit&#8217;:
../../src/synaptics.c:716: warning: passing argument 4 of &#8216;InitPointerDeviceStruct&#8217; from incompatible pointer type
/usr/include/xorg/input.h:368: note: expected &#8216;Atom *&#8217; but argument is of type &#8216;void (*)(struct _DeviceIntRec *, struct PtrCtrl *)&#8217;
../../src/synaptics.c:716: warning: passing argument 5 of &#8216;InitPointerDeviceStruct&#8217; makes pointer from integer without a cast
/usr/include/xorg/input.h:368: note: expected &#8216;PtrCtrlProcPtr&#8217; but argument is of type &#8216;int&#8217;
../../src/synaptics.c:716: error: too few arguments to function &#8216;InitPointerDeviceStruct&#8217;
../../src/synaptics.c:718: error: too few arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
../../src/synaptics.c:721: error: too few arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
../../src/synaptics.c:731: warning: passing argument 2 of &#8216;XIRegisterPropertyHandler&#8217; from incompatible pointer type
/usr/include/xorg/exevents.h:87: note: expected &#8216;int (*)(struct _DeviceIntRec *, Atom,  struct XIPropertyValueRec *, BOOL)&#8217; but argument is of type &#8216;int (*)(struct _DeviceIntRec *, Atom,  struct XIPropertyValueRec *)&#8217;
../../src/synaptics.c: In function &#8216;SynapticsGetHwState&#8217;:
../../src/synaptics.c:889: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
make[3]: *** [synaptics.lo] Error 1
make[3]: Leaving directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/andrzej/synaptics-kinetic-pointer/obj-x86_64-linux-gnu'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

---

### Post by Mr. Picklesworth on 2010-09-08
Hi! Hate to say it, but the branch is just very outdated. Since then, X has moved to xinput2 and the previous Synaptic driver has (as I understand it) seen a lot of revision. It may be possible to get the diff with my changes and apply it to the new code (bzr rebase with a recent branch will do it), but I'm not very optimistic there. Good luck, though, if you try it :)

---

### Post by andrek on 2010-09-08
Thanks for your reply. It sounds pretty tough from what you're saying, so I'm probably giving it up. It's beyond my capability :)

---

