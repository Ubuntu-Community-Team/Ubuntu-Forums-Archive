---
title: "Building NUX from Source (to Build Unity from Source)"
date: 2013-01-07
forum: Packaging and Compiling Programs
---

### Post by davidkrauser on 2013-01-07
In attempts to build Unity on 12.04 as described here ([ http://unity.ubuntu.com/getinvolved/development/unity/]("http://unity.ubuntu.com/getinvolved/development/unity/") ), I've run into a few issues.

Namely, when building NUX from source with the supplied instructions, I get the following error:

```

./GraphicsDisplayX11.h:88:5: error: 'shared_ptr' in namespace 'std' does not name a type

```It seems that the compiler is not recognizing the shared_ptr type. After a quick glance through the NUX makefile, I found this line:

```

GCC_FLAGS = -g -O0 -Wall -Wextra -Wno-unused-parameter -std=c++0x

```So, theoretically, with the -std=c++0x flag set properly, everything should be working fine. I'm completely baffled.

Has anyone else seen this and found a fix?

---

### Post by mc4man on 2013-01-08
> **davidkrauser said:**
> In attempts to build Unity on 12.04
..... found a fix?
if your aim is unity trunk then do on a 12.10 or even better a 13.04 dev install
(newer req.  compiz(dev), bamf, libX11*, ect.

---

### Post by davidkrauser on 2013-01-08
I may give that a try. The instructions specify Precise Pangolin, but they may just be out of date.

---

### Post by davidkrauser on 2013-01-12
I upgraded to the 13.04 daily build, and was able to get NUX compilation working.

Still no luck building Unity, though. I'm still following the official instructions here: [http://unity.ubuntu.com/getinvolved/development/unity/](http://unity.ubuntu.com/getinvolved/development/unity/)

It seems odd to me to pull both the trunk for both Unity and NUX as instructed. Right now the unity build fails because the NUX api is different than expected:

```

/home/davidkrauser/Workspace/unity/trunk/dash/DashController.cpp: In constructor ‘unity::dash::Controller::Controller(const WindowCreator&)’:
/home/davidkrauser/Workspace/unity/trunk/dash/DashController.cpp:71:26: error: no matching function for call to ‘nux::animation::AnimateValue<double>::AnimateValue(int)’
/home/davidkrauser/Workspace/unity/trunk/dash/DashController.cpp:71:26: note: candidates are:
In file included from /usr/include/Nux-4.0/NuxCore/Animation.h:114:0,
                 from /home/davidkrauser/Workspace/unity/trunk/dash/DashController.h:27,
                 from /home/davidkrauser/Workspace/unity/trunk/dash/DashController.cpp:20:
/usr/include/Nux-4.0/NuxCore/Animation-inl.h:41:1: note: nux::animation::AnimateValue<VALUE_TYPE>::AnimateValue(const VALUE_TYPE&, const VALUE_TYPE&, int) [with VALUE_TYPE = double]
/usr/include/Nux-4.0/NuxCore/Animation-inl.h:41:1: note:   candidate expects 3 arguments, 1 provided
/usr/include/Nux-4.0/NuxCore/Animation-inl.h:31:1: note: nux::animation::AnimateValue<VALUE_TYPE>::AnimateValue() [with VALUE_TYPE = double]
/usr/include/Nux-4.0/NuxCore/Animation-inl.h:31:1: note:   candidate expects 0 arguments, 1 provided
make[2]: *** [dash/CMakeFiles/dash-lib.dir/DashController.cpp.o] Error 1
make[1]: *** [dash/CMakeFiles/dash-lib.dir/all] Error 2
make: *** [all] Error 2

```

Anyone know of a workaround for this?

---

### Post by mc4man on 2013-01-14
> **davidkrauser said:**
> 
It seems odd to me to pull both the trunk for both Unity and NUX as instructed. Right now the unity build fails because the NUX api is different than expected:


Anyone know of a workaround for this?

You were maybe 1/2 a day off or so. Nux comes first, sometimes Unity has to catch up.
Atm tonight  both bzr are at current releases,  4.0.0daily13.01.11 & 6.12.0daily13.01.11.2,  so they'd certainly work together
(- really what you'd now have in an updated 13.04 install with proposed repo so you could just apt-get or bzr the unity source & do whatever you had in mind.

Actually just re-built unity here tonight, wanted to change up ExpoLaunchericon.cpp to suit a 1X4 workspace setup.

---

