---
title: "Not listing the installed packages"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by karthik24 on 2015-07-25
Hi,

When I tried to install some programs, I got the dependency is not satisfiable error. So , I installed libicu42 pakage, after the installation it showed like installation completed. But after those packages installation, when looking in Ubuntu software center it is not showing libicu42 package. I enabled to show all technical items too, under the libicu42 it is not listing. Is that needed to do any activations or enable? Please explain. Thank you.

---

### Post by sandyd on 2015-07-25
What's the output of
```

dpkg -l | grep libicu
```

---

