---
title: "kivy/buildozer on Ubuntu 15.04"
date: 2015-06-24
forum: Programming Talk
---

### Post by promet on 2015-06-24
Hi,

I'm on Ubuntu 15.04 and have been having a devil of a time getting  kivy/buildozer to work, and just wanted to share what has seemed to get  me "up and running". It seems like some version confusion with the  Android Build Tools, was at the root of my problems. This howto is  actually for OSX, but the "ABT cleanup" described here: [http://stackoverflow.com/questions/26277154/android-compile-error-using-buildozer]("http://Hi,%20I%27m%20on%20Ubuntu%2015.04%20and%20have%20been%20having%20a%20devil%20of%20a%20time%20getting%20kivy/buildozer%20to%20work,%20and%20just%20wanted%20to%20share%20what%20has%20seemed%20to%20get%20me%20&quot;up%20and%20running&quot;.%20It%20seems%20like%20some%20version%20confusion%20with%20the%20Android%20Build%20Tools,%20was%20at%20the%20root%20of%20my%20problems.%20This%20howto%20is%20actually%20for%20OSX,%20but%20the%20&quot;ABT&quot;%20cleanup%20described%20here:%20http://stackoverflow.com/questions/26277154/android-compile-error-using-buildozerworked%20for%20me;%20for%20what%20it%27s%20worth...")  worked for mein ubuntu 15.04 as well; for what it's worth... 

I'd tried various kivy install methods, repos, pip, etc. and toyed with  various android ndk and sdk versions. After, literally days, of  different combinations it seemed like the above got me going. I thought  I'd post it just in case anyone who is trying to learn android  development via the python route might find it useful. As these are,  largely, alpha dev projects, there is a lot of hit and miss with getting  a build environment set up. I hope someone can find this to their  benefit also at some point. It's the clearest path I've found to  resolving, what seem like a lot of complications with getting  kivy/buildozer to work. As I said, there are lots of confusing details,  to me at least, in the process but, hopefully this will be of some use  to someone, at some point.

Best,

---

