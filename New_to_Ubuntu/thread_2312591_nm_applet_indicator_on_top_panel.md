---
title: "nm_applet indicator on top panel"
date: 2016-02-05
forum: New to Ubuntu
---

### Post by bekirs on 2016-02-05
Hi,

I don't have **nm_applet** indicator on top panel of my desktop. It is also not in the list when I right click on top panel and choose [B]Add New Items...

[/B]Could you please help me to solve this issue?

Please see [http://ubuntuforums.org/showthread.php?t=2311841](http://ubuntuforums.org/showthread.php?t=2311841) for some background information about it.

Thanks in advance,

---

### Post by ajgreeny on 2016-02-05
Make sure you have the indicator-plugin in the panel; that is where the network icon sits.

---

### Post by bekirs on 2016-02-05
How can I check whether I have this?

---

### Post by Dennis N on 2016-02-05
> **bekirs said:**
> How can I check whether I have this?

Run this command (shown with my output). This comes with the Xubuntu installation as a default package, so it should be present.

```
dmn@Sydney:~$ apt-cache policy xfce4-indicator-plugin
xfce4-indicator-plugin:
  Installed: 2.3.3-0ubuntu2
  Candidate: 2.3.3-0ubuntu2
  Version table:
 *** 2.3.3-0ubuntu2 0
        500 http://mirrors.us.kernel.org/ubuntu/ vivid/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by bekirs on 2016-02-06
```
:~$ apt-cache policy xfce4-indicator-pluginxfce4-indicator-plugin:
  Installed: 2.3.2-0ubuntu2
  Candidate: 2.3.2-0ubuntu2
  Version table:
 *** 2.3.2-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ajgreeny on 2016-02-06
So you have it installed, but is it actually in your panel?

Right click in the panel and go to Panel -> Panel Preferences -> Items tab to see if it is listed.  If not add it by using the + button on the right hand side.

---

### Post by bekirs on 2016-02-06
after following the solution of ajgreeny, the problem is solved.

Thank you all.

---

