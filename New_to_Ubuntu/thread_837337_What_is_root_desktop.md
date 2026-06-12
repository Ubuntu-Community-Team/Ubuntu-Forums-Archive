---
title: "What is /root desktop?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by sofasurfer on 2008-06-22
I just realized that there are 2 differant desktop folders. There is the one in my /home directory and one in the /root directory. The one in /root does not contain anything that is in the one in my /home directory. What is /root/desktop?

---

### Post by hyper_ch on 2008-06-22
/root is the home folder of the root-account.

---

### Post by sofasurfer on 2008-06-22
But what is its purpose? When I do 'sudo' to become root, are there reasons why I would need to save stuff to /root/desktop instead of /home/daryl/desktop? Is it just a matter of personal preference or is there a good reason for it?

---

### Post by hyper_ch on 2008-06-22
with sudo you don't become root... you temporarily are granted root rights.

But why you have a "desktop" folder in /root is strange... it would be created if you try to start a gui environment while you are really logged in as root.

---

### Post by Paqman on 2008-06-22
> **sofasurfer said:**
> But what is its purpose?

Not a lot. It's kind of a vestigal organ, like our tailbone or a whale's pelvis.

Traditionally, Linux systems have a separate user account called root, as well as the actual users. Ubuntu does away with this and handles the need to take on admin rights with the "sudo" command. The directory structure for the root user is just a leftover.

---

### Post by sofasurfer on 2008-06-22
Ok. When I use nautilus as sudo for instance, I see this /root/desktop in the list of 'places' on the left side of the nautilus window. It is confusing. So, if you guys don't stop me, I am going to delete the /root/desktop directory. Ok?

---

