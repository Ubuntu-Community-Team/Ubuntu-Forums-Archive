---
title: "New To Linux, Disabled Password Login SSH"
date: 2021-07-20
forum: New to Ubuntu
---

### Post by seandavidson on 2021-07-20
So it appears I have made a mistake. I thought I backed up my SSH key and ended up reloading my workstation and put what I thought was my backed up SSH key on my machine. I guess this is not the correct key because I can't login to SSH now. I disabled Password login so it appears I am locked out, does anyone know a way into the machine? It is a VM on Proxmox so I can't plug in a monitor on the machine and when I login via the Console NoVNC it loads a desktop but I don't see a terminal in the list of applications. Completely lost as I did not think I installed a Desktop though I had installed on the server version of Ubuntu.

---

### Post by seandavidson on 2021-07-20
I was able to fix my issue, I had Filezilla installed on the server and was able to open that and edit the authorized_keys file with the new SSH key I had on my workstation.

---

### Post by TheFu on 2021-07-20
Please mark this thread a SOLVED to help the community.  
Thread Tools button --> Mark SOLVED.

---

### Post by ActionParsnip on 2021-07-20
You could have also booted to live CD, mounted the internal disk and grabbed the key pair

---

