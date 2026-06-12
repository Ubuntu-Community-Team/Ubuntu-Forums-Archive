---
title: "unable to install gstreamer-sdk-dev (Ubuntu 16.04)"
date: 2016-04-30
forum: Packaging and Compiling Programs
---

### Post by asif-bahrainwala on 2016-04-30
I am unable to install this on Ubuntu 16.04, although on Ubuntu 14.04.2 , it just worked.
I have followed all the steps as mentioned:- [http://docs.gstreamer.com/display/GstSDK/Installing+on+Linux](http://docs.gstreamer.com/display/GstSDK/Installing+on+Linux)

**sudo apt-get update**
output:-
W: [http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64/./Release.gpg:](http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64/./Release.gpg:) Signature by key E12966CEA64EF95EAF47A94CD7FD268A1900C4BE uses weak digest algorithm (SHA1)
E: Failed to fetch [http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64/./Release](http://www.freedesktop.org/software/gstreamer-sdk/data/packages/ubuntu/raring/amd64/./Release)  No Hash entry in Release file /var/lib/apt/lists/partial/www.freedesktop.org_software_gstreamer-sdk_data_packages_ubuntu_raring_amd64_._Release which is considered strong enough for security purposes
_E: Some index files failed to download. They have been ignored, or old ones used instead._

obviously  **sudo apt-get install gstreamer-sdk-dev** gives me:-

I get the following error
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gstreamer-sdk-dev

---

### Post by asif-bahrainwala on 2016-04-30
Its probably got to do with the new **apt** that doesn't recognize SHA1 anymore

---

### Post by asif-bahrainwala on 2016-05-01
I did mange to solve this by using dbkg (all the gstreamer packages) scripts saved me ,but I still prefer to use APT , any idea how we can side step this SHA2 enforcement

---

### Post by Bucky Ball on 2016-05-01
> **asif-bahrainwala said:**
> I did mange to solve this by using dbkg (all the gstreamer packages) scripts saved me ,but I still prefer to use APT , any idea how we can side step this SHA2 enforcement

You may have more success getting an answer by marking this thread as solved and asking this in a new one. Include a link to this thread in the new one as an example of what led you to your question. 

Thanks for sharing the fix. As the original issue is solved, best to mark it that way to help others in any case. This will not close the thread to further discussion. Good luck.

---

