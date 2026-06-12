---
title: "Set Shotwell Viewer as Default"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-10-19
im trying to set 'Shotwell Viewer' as my default to open images, but the option to set it as default is missing. im only allowed to 'open with' shotwell viewer.

---

### Post by rihikz on 2013-10-19
Right click a file you want to open with shotwell by default, and open the properties menu. In the Open With tab you can change the default applications for the file extension.

---

### Post by Danny_Michel on 2013-10-19
> **rihikz said:**
> Right click a file you want to open with shotwell by default, and open the properties menu. In the Open With tab you can change the default applications for the file extension.
Everything else but shotwell viewer is listed.

---

### Post by Danny_Michel on 2013-10-19
I dont understand what this guy is saying in the first comment. [http://redmine.yorba.org/issues/7292](http://redmine.yorba.org/issues/7292) what file do i need to change the NoDisplay=True in?

---

### Post by mc4man on 2013-10-19
> **Danny_Michel said:**
> I dont understand what this guy is saying in the first comment. [http://redmine.yorba.org/issues/7292](http://redmine.yorba.org/issues/7292) what file do i need to change the NoDisplay=True in?
That would be /usr/share/applications/shotwell-viewer.desktop
though don't see this as an issue in 13.04 & 13.10 ubuntu session(unity
What release of Ubuntu are you using & what session?

---

### Post by Danny_Michel on 2013-10-19
thanks. that worked. 13.10 ubuntu
shotwell was seen but not shotwell viewer.
changed it and it worked.

---

