---
title: "Is this script harmless?"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by tessawong on 2014-01-05
I am new to Linux.

Someone suggested that I install the individual sgfxi script first so that I can install NVIDIA-Linux-x86_64-331.20.run on Ubuntu 12.04.3 (x64). The URL to the aforementioned script is [http://smxi.org/site/install.htm](http://smxi.org/site/install.htm)

Could someone here tell me whether it is harmless or malicious?

---

### Post by monkeybrain20122 on 2014-01-05
It is much simpler to install Nvidia 331.20 with a ppa.
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=precise](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=precise)

Install ppa-purge as well in case something goes wrong.

**Edited:** Ok hold it. Since 12.04.3 has upgraded its graphic stack to raring's there may be problems using the ppa. Better wait for more expert opionions.

---

### Post by oldfred on 2014-01-06
If you are new to Linux, generally better to just install the nVidia drivers from the repository or that system settings, additional drivers offer.

Installing the nVidia driver directly can create issues and may only be required if you have so new of a nVidia card that the slightly older version from Ubuntu does not support it.

---

