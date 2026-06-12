---
title: "Eclipse fails to launch and debug code"
date: 2005-06-22
forum: Programming Talk
---

### Post by Nicolinux on 2005-06-22
Hi,

I have Eclipse 3.0.2 installed. However every time I want to launch a project (C++, Java, doesen't matter). I get an error like this:
```

Launch failed

Reason:
Failed to set program arguments, environment or working directory

Unable to set working directory: mi_cmd_env_cd: Usage DIRECTORY

```

Anyone can help me with this?

Thanks.

Stefan

---

### Post by jmpep on 2006-01-11
Hi! I bet that by this time you don't need the answer, but anyway:

Has your project name or maybe the path to the folder which contains it any spaces? I tell you that because that was the reason why I had the same problem that you address.

---

### Post by morton2002 on 2007-02-24
That worked for me too, thanks for the tip!
-Robert

---

### Post by dunkirk on 2008-05-07
Hey, Gentoo user here, but thanks for the tip. Found it by Googling, and it fixed my problem as well.

---

### Post by mikej_96 on 2008-10-04
Gentoo user here as well. I also had this problem and hit this post. Saved me a big headache. I wouldn't have thought a space in the path would cause the problem.

---

### Post by huysamdua on 2008-10-13
That worked for me...three, thanks so much! :)

Huy

---

### Post by NWcustomcode on 2009-02-01
Hey great advice!! I am running Vista with a full cygwin install and removing spaces in my directory names fixed the problems!!!


Thanks

---

### Post by hoangdang on 2010-08-17
> **jmpep said:**
> Hi! I bet that by this time you don't need the answer, but anyway:

Has your project name or maybe the path to the folder which contains it any spaces? I tell you that because that was the reason why I had the same problem that you address.


This answer has saved my life ! Thank you so much!

---

### Post by moh.elsaka on 2011-12-20
> **jmpep said:**
> Hi! I bet that by this time you don't need the answer, but anyway:

Has your project name or maybe the path to the folder which contains it any spaces? I tell you that because that was the reason why I had the same problem that you address.
Thanks a lot
it worked for me too :D

---

### Post by epowerpii on 2012-01-29
Hi, looks like this is still a problem 6 and a half years after the original post I'd like to add...

If there are no spaces in your path and you're still getting this problem then it could be because the directory has been symlinked and although the link has no spaces in the path, the target of the link does.

Good luck!

---

### Post by epowerpii on 2012-01-29
For reference, it looks like this is the bug on the Eclipse Bugzilla:

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=191332](https://bugs.eclipse.org/bugs/show_bug.cgi?id=191332)

Apparently somebody has the coding working as of 8th Dec 2011 so hopefully the problem won't be in the next release of Eclipse / Ubuntu.

---

