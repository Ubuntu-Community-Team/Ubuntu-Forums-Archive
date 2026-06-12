---
title: "Ubuntu at linode.com"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by Ron_Watkins on 2015-02-28
I am trying Ubuntu at linode.com for the first time. I was able to get it running with xrdp.
My goal is to run the blender rendering in the cloud, however, when I try to run it, I get the errors, which I don't know how to resolve.
A screenshot of the errors is here: [http://i.imgur.com/3g7PJWZ.png](http://i.imgur.com/3g7PJWZ.png)
Looking for any suggestions on how to proceed. Thanks

---

### Post by tgalati4 on 2015-02-28
Since you are running in a virtualized environment and your display is set to 10, there may be an issue with X-Windows environment variables.  Look through:

```
env
```

Compare it with a localized machine running Blender performing the same rendering.  It's possible that Blender sets some environment variables that need changing to work properly in a vm.

The other issue is *swrast*, which I presume means software raster is not loading because it can't find a resources file (/root/.drirc).  So make a file called .drirc and put stuff in it.

---

