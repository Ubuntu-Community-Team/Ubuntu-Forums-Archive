---
title: "can't get download to run"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by vegas89 on 2013-06-05
*I am running ubuntu *12.04 and have downloaded hplip-3.13.5 run. What must I do to get this download to run  ](*,)

---

### Post by snowpine on 2013-06-05
You can install hplip with one mouse click in the Ubuntu Software Center.

If you have a specific reason for downloading it from the HP site (for example, you have a newer model printer that isn't supported by the version of hplip Ubuntu provides) then you may find these instructions helpful: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by vegas89 on 2013-06-05
Thanks, I did that and when I try to run I get this window ( see screenshot ). I have the printer installed on the laptop ( see screenshot ) Can't get around this.  :confused:

---

### Post by snowpine on 2013-06-05
Maybe I'm confused, but it appears your printer is successfully installed? Can you take a step back and tell us what the actual problem is?

---

### Post by vegas89 on 2013-06-05
When I hit the hp icon the window comes up as no devices found, but as you can see I do have the printer installed. When I try to print something the computer says the job is processing but the printer never responds.

---

### Post by vegas89 on 2013-06-07
Problem solved, I typed the following terminal script comand cd ~/Downloads
chmod +x hplip-3.13.5.run
sudo sh hplip-3.13.5.run    hplip is now running fine.

---

