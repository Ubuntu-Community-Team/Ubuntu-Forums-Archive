---
title: "change jdk and eclipse"
date: 2007-02-26
forum: Programming Talk
---

### Post by b4nsh33 on 2007-02-26
hi, i recently installed automatix2, and after i installed frpstware it installed jdk6 as a dependency, i had jdk5 before, so i ended with two jdk, so i uninstalled jdk5  but now elipse refuses to run with error no java virtual machine was found after searching /usr/lib/j2sdk1.4-sun/bin/java, thats the old location, now it is /usr/lib/jvm/java-6-sun-1.6.0.00/, where do i change that in elcipse config files, it doesnt run to use the wizard.

---

### Post by hod139 on 2007-02-27
I'm not sure how you installed eclipse, but if you used the repository version the config file is located at:
```

/etc/eclipse/java_home

```

---

### Post by b4nsh33 on 2007-02-27
Thanks, i used the reposutiries and editing that file did the trick,

---

