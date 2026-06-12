---
title: "Prompting for sudo password in graphical python app"
date: 2009-07-08
forum: Programming Talk
---

### Post by brydonhunter on 2009-07-08
I'm teaching myself python and in the middle of creating a graphical python app and I need to prompt the user to enter their sudo password.

- I want this to be graphical similar to Ubuntu's prompt when the sudo password is required. wxPython, PyGTK, glade, doesn't matter which one.

- I do not want to run the complete script as sudo, not great for security.

Can someone point me in the right direction please.

TX

---

### Post by brydonhunter on 2009-07-09
Found the answer in the source of update-manager package

<code>

cmd = ["/usr/bin/gksu", 
           "--desktop", "/usr/share/applications/update-manager.desktop", 
           "--", "/usr/sbin/synaptic", "--hide-main-window",  
           "--non-interactive", "--parent-window-id", "%s" % (id) ]

</code>

This did the job.

---

