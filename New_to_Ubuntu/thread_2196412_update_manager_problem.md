---
title: "update manager problem"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by parcdulas on 2013-12-29
Hi,
When I run update manager it tells me there are 107 updates but when I click " install" I get a message to the effect that this would require packages from untrusted sources. What is wrong, how do I run update and get my system up to date?

thanks

---

### Post by 3grciii on 2013-12-29
If you have added any PPA's to your software sources this can happen. You can remove the PPAs to eliminate the error or continue with the untrusted sources

---

### Post by parcdulas on 2013-12-29
> **3grciii said:**
> If you have added any PPA's to your software sources this can happen. You can remove the PPAs to eliminate the error or continue with the untrusted sources

Sorry, what are PPA's? Not sure if I might have added any. The update manager will not seem to continue with the apparently untrusted sources.

Thanks.

---

### Post by deadflowr on 2013-12-29
If you try running "check" let it reload the package list, and then select install is it the same?

---

### Post by ajgreeny on 2013-12-29
Can you show us the full error message that you see when trying to update; does it give you any numbers or code for the untrusted source, or for a gpg error?

---

### Post by parcdulas on 2013-12-29
Thanks deadflowr. Clicked on check and the cache was reloaded so that 277 updates to install totaling 420Mb! clicked install and away it went. Now fine. Thanks again.

While on this tack I have a system in the heart of rural Wales where the only internet I can get is poor GPRS mobile so update is VERY slow. (>24 hours!) Something always interupts the download around 02:00am either the mobile network or Ubuntu. The only way I can recover the connection is to reboot the system as without a reboot there is no mobile available. Is there any way I can either update to a CD for use on the system in Wales or updat in small chunks of say 10Mb at a time so less is lost when it breaks.

Thanks

---

### Post by deadflowr on 2013-12-29
yeah, I've found one of the more common issues people get with installing packages and updating is they don't refresh the package lists so they end up with out of date package lists, which cause normally quite easily fixable errors.
But then they run a slew of commands to try to fix the issues and end up with even more problems.
Which leads to ten page threads, where somewhere along the line they manually tried removing files, which leads to even more problems. Which then leads to an unnecessary reinstall. 
I tend to try the simplest things first, in this case a refresh.

Anyway, I don't know anything on the network issues you've got.

---

