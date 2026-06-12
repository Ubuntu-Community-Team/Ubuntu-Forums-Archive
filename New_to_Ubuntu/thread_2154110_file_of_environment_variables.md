---
title: "file of environment variables"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by mprat on 2013-06-13
Where is the file that stores environment variables? My PATH variable was changed a while ago and I can't seem to find the file that stores that information, since I want to change it back to the standard.

---

### Post by sandyd on 2013-06-13
/etc/environment stores the default, which may be overrided in many places including ~/.bashrc, /etc/profile, .etc .etc

How did you change the PATH variable?

---

### Post by Lars Noodén on 2013-06-13
Usually your path for your account is set in ~/.profile

---

### Post by slickymaster on 2013-06-13
There is a very good explanation of all that at [Environment Variable]("https://help.ubuntu.com/community/EnvironmentVariables").

---

