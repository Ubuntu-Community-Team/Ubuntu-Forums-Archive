---
title: "Monitor Switches off before Shutdown!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mrdosa on 2008-04-28
Hi! Now I have got a strange problem. I am using Ubuntu 7.10. Now as soon as I press the shut down button, the monitor switches off. And just when the system is about to shut down, the monitor switches back on before finally switching off!! I am really confused. Its been happening for as long as I remember, I just never cared to see!
Please let me know, whats wrong.
Thanks!

---

### Post by dokdoom on 2008-04-28
Well, lets start with your video driver. As far as you are aware, are you using the correct driver? Is rendering working? Also, lets say you shut down and experience the same issue, if you were to immediatley log back on is there anything showing in the logs?

You could try this, power off, go through the same problem Power on and immedieatley get on your command line.

run ls -ltr /var/log

This will show you your logs in order of time. Look for your Xorg.0.log, I can't imagine anything showing up in your other logs.

---

### Post by mrdosa on 2008-04-28
All right. I shall do that and report back. 
Just to let you know, everything works fine. I have no problem with my graphics card and all...
This happens only during shutdown. I dont see that Ubuntu logo and that closing sequence, coz the monitor already switches off.

---

### Post by mrdosa on 2008-04-28
Here I have attached the log of xorg.o.log

---

