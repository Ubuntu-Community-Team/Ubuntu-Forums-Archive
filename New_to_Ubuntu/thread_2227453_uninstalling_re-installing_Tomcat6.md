---
title: "uninstalling/ re-installing Tomcat6"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by Danny_R on 2014-06-02
after an "issue" with tomcat6 i have uninstalled it (using apt-get remove tomcat6)

rebooted an then reinstalled it (using apt-get install tomcat6)

where is the default location for installed apps? im looking for the "webapps" folder

the original install of tomcat i manually installed it into /usr/src/ an i can still see the folder (apache-tomcat-7.0.53) even though i uninstalled it!? (did i perform the uninstall correctly?)

many thanks

---

### Post by Danger_Monkey on 2014-06-02
You might try:

```

apt-get purge <package_name>

```

Purge removes the config files, et al.  "Remove" leaves file and configs.  Why it would show a version 7 (apache-tomcat-7.0.53) when you installed a 6, I don't know.  I install that, manually from a tarball, since it is java, and easy to remove and move as I please.

---

