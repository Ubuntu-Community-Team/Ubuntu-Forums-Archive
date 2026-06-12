---
title: "Need help optimizing subversion"
date: 2007-08-08
forum: Programming Talk
---

### Post by mssever on 2007-08-08
I'm using Subversion for the first time (I've never used any other version control system before). I'm currently importing a source tree into svn for a project that I just created on SourceForge. So far, the import has been going for nearly 24 hours with no end in sight.

Here are the details: My project includes among other things 20,000 small PNG images (average 394 bytes each). The entire source tree is 84 MB.

I'm connected to the Internet via satellite. Due to the laws of physics, there is a 0.5 second round trip satellite latency, in addition to any other network latency that might exist. In other words, a ping time of less than 0.5 seconds is impossible.

SVN has been uploading my files one at a time, with several round trips involved. That means that each of those 20,000 files takes about 4 seconds to upload. Clearly, the bottleneck is my network latency, not bandwidth.

Is there any way to make svn either use multiple simultaneous connections or temporarily tar up files for transport? Once this upload completes, I'll still have to download a working copy. If that takes me another 24 hours, I won't be happy.

---

### Post by bbzbryce on 2007-08-08
> **mssever said:**
> Is there any way to make svn either use multiple simultaneous connections or temporarily tar up files for transport? Once this upload completes, I'll still have to download a working copy. If that takes me another 24 hours, I won't be happy.

Do you have shell access to your svn location? If so upload a tarball of your source on to the server and then do an import into the repository from there. As far as I know there is no supported way through SVN to do what you ask.

---

### Post by mssever on 2007-08-08
> **bbzbryce said:**
> Do you have shell access to your svn location? If so upload a tarball of your source on to the server and then do an import into the repository from there. As far as I know there is no supported way through SVN to do what you ask.

Thanks for your reply. The import is finished, now. I tried to do a checkout from my sourceforge.net shell account, but got errors. So, I decided to try a local checkout. SVN appears to be doing the checkout operation in parallel as it should.

---

