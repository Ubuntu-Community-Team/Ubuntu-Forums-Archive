---
title: "Ubuntu 20.04 auto-login stopped working after backing up Proxmox VM"
date: 2024-09-22
forum: New to Ubuntu
---

### Post by ianmanning on 2024-09-22
I have a Lubuntu 20.04 LTS VM running on my Proxmox 8.2.5 server. It was configured to auto-login at boot, as it is running on a headless server. Today I stopped the VM to do a snapshot backup from the Proxmox console (to a local SATA SSD). When I restarted the VM it did not auto-login - it prompted me for a user id and password. My user name and password were rejected, however - when I enter them I get bounced back to the login box. I am only able to login as root.


If I do "cat /etc/passwd" I can see my user in the list. If I try to open "Users and Groups" from the UI the application hangs.


Any idea why this has happened, and how I can restore my login access and auto-login?

---

### Post by ianmanning on 2024-09-22
[COLOR=#141618][FONT=&quot]I figured it out - I was low on disk space (6GB remaining). Freeing up a little space resolved the problem[/FONT][/COLOR]

---

### Post by ActionParsnip on 2024-09-23
Please mark as solved if there is no more issue :)

---

