---
title: "MATE and Ubuntu 12.04"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by suomalainen on 2013-03-25
I installed MATE into 12.04 so I have a better feeling desktop environment.

Now I have one problem:

I got a few folders on my desktop. No matter which one I open if I choose to view a file inside a folder it takes AGES to open...

How can I fix this?

Other than that everything looks fine and works well. No latency issues to report.

Thank you.

---

### Post by tgalati4 on 2013-03-25
Open a terminal, post the output of:

```
free
```

Now open a file and while the file is taking time to open:

```
dmesg | tail -40
```

Also try opening another file and look at IOWaits in* top*:  (Look for "wa" and Control-C to quit)

```
top
```

---

### Post by suomalainen on 2013-03-25
Thank you for the advice. Strangely, everything seems to be working now? I have no explanation to offer. But thanks for your willingness to help out!

---

### Post by tgalati4 on 2013-03-25
You may have had a background process running, like updating the software repositories, and that can cause slowness.  But feel free to use the above commands if it happens again.  That will give more information as to what is happening.

---

### Post by suomalainen on 2013-03-25
I appreiate that! Thanks

---

