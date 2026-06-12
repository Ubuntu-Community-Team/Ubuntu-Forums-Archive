---
title: "Can't write to /usr/lib"
date: 2010-06-15
forum: Programming Talk
---

### Post by Vistz on 2010-06-15
I ran a .exe file through Wine. It asked me where to install some files and I chose /usr/lib/eclipse because that's where my application is located. I got the error message saying I didn't have sufficient privileges. Is there a way around this?

---

### Post by schauerlich on 2010-06-15
1) man sudo
2) what are you installing? /usr/lib is for, surprisingly, library files.

---

### Post by simeon87 on 2010-06-16
Given that it's a Wine application, you could install the files in your C:/ drive that you've been given by Wine. It's a Windows program so it'll probably work when you store the files to some place on the C:/ drive.

---

### Post by denver on 2010-06-16
All wine applications should be installed in your home folder. DO NOT under any circumstances use wine under the root user.

Any application installed in /usr/lib is a native Linux app. Installing a windows app in the same folder will NOT get you the desired result. You cannot combine native apps with windows apps and expect them to work together.

If you absolutely need to use a specific windows app with eclipse, install the windows version of eclipse using wine and then install that app the same way.

Good luck!

---

