---
title: "Prevent overwriting symlink by update-alternatives"
date: 2010-11-19
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-11-19
Dear Ubuntu packagers,

For a while I am now providing Ubuntu packages for a robot simulator. The community is itself eager to provide its own replacements for the plugins that come with the simulator.

Until now I recommended them to use update-alternatives to provide the simulator with their own shared libraries.

However, with every upgrade of the simulator, which happens often because I am actively developing and using the daily build on Launchpad, the alternative is overwritten.

They need to rerun e.g.: ```
sudo update-alternatives --config srInterface
``` which after hitting "Enter" indeed tells: oh ***, it was indeed broken:
```
update-alternatives: warning: forcing reinstallation of alternative
 /blah/blah/srInterface/libsrInterface.so.0 
 because link group srInterface is broken.
```

Is there some simple option to detect if there is a symlink created? (To check that, I don't want to include update-alternatives as a dependency for my package of course.)

Or, do you recommend me to use dpkg-divert, or is there something very simple which I overlook?

Thanks!


=== 

My current debian/rules file is simply:

```

%:
	dh  $@

```

Do I need to use update-alternatives as a post-installation target here?

---

### Post by MrQuincle on 2010-11-23
For the people waiting for an answer...

Nothing needs to be done in debian/rules.

However, I need to add to scripts to my package, in my case: debian/robot3d.postinst 
```

#!/bin/sh

set -e

if [ "$1" = "configure" ] || [ "$1" = "abort-upgrade" ] ; then
    update-alternatives --install /usr/lib/robot3d/components/libsrInterface.so \
        srInterface /usr/lib/robot3d/components/libsrInterface.so.0 0
fi

```

And debian/robot3d.prerm:

```

#!/bin/sh

set -e

if [ "$1" = "remove" ] || [ "$1" = "deconfigure" ] ; then
    update-alternatives --remove srInterface /usr/lib/robot3d/components/libsrInterface.so.0
fi

```

In the hope this saves someones day some time. :popcorn:

---

