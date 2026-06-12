---
title: "error while launching the azureus using crontab"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by shashank.ks on 2008-07-06
i was trying launch azureus using crontab . 

the entry in the crontab -e is

15 02 * * * DISPLAY=:0 /usr/bin/azureus

and i get this following error message in my mail box

Invalid MIT-MAGIC-COOKIE-1 keyException in thread "main" org.eclipse.swt.SWTError: No more handles [gtk_init_check() failed]
        at org.eclipse.swt.SWT.error(SWT.java:3400)
        at org.eclipse.swt.widgets.Display.createDisplay(Display.java:793)
        at org.eclipse.swt.widgets.Display.create(Display.java:781)
        at org.eclipse.swt.graphics.Device.<init>(Device.java:145)
and azureus does not launch.

for the time being i am using the at command to launch the azureus . But the thing is i have to give this command every day . so any one got any solution ....?

---

### Post by roquefilipe on 2008-07-08
it might have something to do with different environment in the crontab. check this out [http://blog.spikesource.com/crontab.htm](http://blog.spikesource.com/crontab.htm)

---

