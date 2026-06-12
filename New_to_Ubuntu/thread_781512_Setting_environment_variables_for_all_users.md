---
title: "Setting environment variables for all users"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-04
What file do I edit to set the environment variables for all users?
Is there a GUI to set them?

variables for a single user can be set by adding an export statement to the file: /home/<user>/.bashrc

One solution could be to have a global script that each user's .bashrc file calls. But that would require each user to modify his .bashrc file.

Thanks,
Norm

---

### Post by mike2357 on 2008-05-04
Try modifying /etc/bash.bashrc

---

