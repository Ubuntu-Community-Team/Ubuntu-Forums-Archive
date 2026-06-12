---
title: "intrepid hangs up at shutdown when there is no internet connection"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by thebestofall007 on 2008-12-01
hello, i was wondering what would cause intrepid to hang up on shutdown when there is no internet connection. i dont have this problem, however, when the system has an internet connection. what could i do to fix this?

---

### Post by kansasnoob on 2008-12-01
> **thebestofall007 said:**
> hello, i was wondering what would cause intrepid to hang up on shutdown when there is no internet connection. i dont have this problem, however, when the system has an internet connection. what could i do to fix this?

I had a problem with two Intrepid installs "hanging" on shutdown but it had nothing to do with the network manager. It was a bug in alsa-utils.

But while looking for answers I noticed some mention of related (or unrelated) issues in the bug report:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/alsa-utils/+bug/274995](https://bugs.launchpad.net/ubuntu/intrepid/+source/alsa-utils/+bug/274995)

This fixed my problem:

> 
 Martin Pitt wrote on 2008-11-26: (permalink)

Accepted into intrepid-proposed, please test and give feedback here. Please see [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to enable and use -proposed. Thank you in advance!


I skipped all the mumbo-jumbo and just enabled Intrepid Proposed, then de-selected all updates except alsa-utils (yeah, lot's of unticking), then after installing the new alsa-utils package I unticked Intrepid Proposed in Software Sources so I wouldn't goof and run a bunch of updates before their time!

Of course your problem may be entirely different.

---

### Post by thebestofall007 on 2009-01-10
yes youre right. i found out about this problem and went to where you went to fix this. worked like a charm.

---

