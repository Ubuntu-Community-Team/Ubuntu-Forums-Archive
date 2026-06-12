---
title: "How I can compile and install mozilla NSS in ubuntu?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by legolas_w on 2008-05-24
Hi
Thank you for reading my post.
can some one please let me know how I can compile and install Mozilla NSS into ubuntu?

Mozilla NSS is available at [http://www.mozilla.org/projects/security/pki/nss/](http://www.mozilla.org/projects/security/pki/nss/)
and the source code can be downloaded from 
[ftp://ftp.mozilla.org/pub/mozilla.org/security/nss/releases/NSS_3_11_9_RTM/src/nss-3.11.9-with-nspr-4.7.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/security/nss/releases/NSS_3_11_9_RTM/src/nss-3.11.9-with-nspr-4.7.tar.gz)

Thanks

---

### Post by meborc on 2008-05-24
there should be a README file in the tar pack that explains the compiling bit, but maybe you do not need it... there are some libnss packages in the synaptic... don't these help? (libnss3-tools for example)

---

### Post by fetuspuppet on 2010-06-30
Hey I'm trying the same thing - it doesn't look like they included a README in the source. I will post back when I get it working.

---

### Post by fetuspuppet on 2010-06-30
[https://developer.mozilla.org/NSS_3.12.4_release_notes](https://developer.mozilla.org/NSS_3.12.4_release_notes)

They say you need to also have nspr as well to build NSS.

Also if you untar the archive there are a few docs in there. Still humming along haven't gotten too far yet.

---

### Post by fetuspuppet on 2010-06-30
gmake is required to build it from source.

here are some old instructions, they're probably close to the current version as well.

[http://www.mozilla.org/projects/security/pki/nss/buildnss_31.html#unix](http://www.mozilla.org/projects/security/pki/nss/buildnss_31.html#unix)

---

