---
title: "wifi &quot;device not ready&quot;"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by Someone uk on 2011-10-29
i keep getting this message about the wifi connection on 11.10

the wifi works out of the box on the live cd but the second i tried installing it it seems to give me this problem

---

### Post by Someone uk on 2011-10-29
what does "device not ready" actually mean?

---

### Post by roger_1960 on 2011-10-29
Hi

The device may be disabled by something.

Could you copy the following into terminal and post back the output

> rfkill list all

This should let us know if something has turned off your wifi

---

### Post by Someone uk on 2011-10-29
> **roger_1960 said:**
> Hi

The device may be disabled by something.

Could you copy the following into terminal and post back the output



This should let us know if something has turned off your wifi

softblock: no
hardblock: no

---

### Post by roger_1960 on 2011-10-29
That rules out quite a few possibilities.

You could try the suggestion is this article

[http://ubuntup.blogspot.com/2010/07/wireless-device-not-ready-problem.html](http://ubuntup.blogspot.com/2010/07/wireless-device-not-ready-problem.html)

If you have an Eeepc it could be a bug - see [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/587498](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/587498)

---

### Post by Someone uk on 2011-11-06
> **roger_1960 said:**
> That rules out quite a few possibilities.

You could try the suggestion is this article

[http://ubuntup.blogspot.com/2010/07/wireless-device-not-ready-problem.html](http://ubuntup.blogspot.com/2010/07/wireless-device-not-ready-problem.html)

If you have an Eeepc it could be a bug - see [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/587498](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/587498)
i don't have an eepc.....and no it's still "no ready"

i installed ubuntu on the alternative cd, and the it has worked out of the box on many live cds....any possible driver issue?

---

