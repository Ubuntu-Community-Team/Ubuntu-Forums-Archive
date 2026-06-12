---
title: "Cannot find known_hosts in /etc/ssh on Ubuntu Server"
date: 2021-02-26
forum: New to Ubuntu
---

### Post by remag03 on 2021-02-26
Hi, I checked my ssh_config file and used nano to make hashknownhosts from yes to no so I could read it, but I do not know what file lists the keys so I can delete old keys or at least delete the file so it can be remade. What file in /etc/ssh has the keys to be deleted?

Also hello I am new to Linux and Ubuntu but I feel its a step up from Windows and I like it very much.

---

### Post by TheFu on 2021-02-26
What is "my ssh_config file"?  Be exact. Use the full path.  There are multiple files which can fit that purpose and users shouldn't really be touching it outside their HOME directories.

The easy answer is to purge the ssh package, then reinstall.  "purge" removes the system settings, not your ~/.ssh/, so your keys won't be impacted, just the system identification keys.  Then as other systems complain, you'll be told exactly which lines to remove.

nano - eeeeew.  I'm so sorry.

---

### Post by remag03 on 2021-02-26
So ssh_config is @ /etc/ssh/ssh_config, also what is wrong with nano compared to vi? What file in /etc/ssh actually holds the keys that can be deleted with a editor?

---

### Post by TheFu on 2021-02-26
> **remag03 said:**
> So ssh_config is @ /etc/ssh/ssh_config, also what is wrong with nano compared to vi? What file in /etc/ssh actually holds the keys that can be deleted with a editor?

In 25+ yrs as a Unix admin, I've never touched the /etc/ssh/ssh_config.  All personal changes are in ~/.ssh/config.
The sshd_config file is the ssh-server config which gets modified on every system I manage to improve security, limit access, allow only sftp access and password access only from trusted LAN systems. All other connections must use keys.

My /etc/ssh/ssh_config doesn't have any keys inside it.

The manpages for both the ssh_config and sshd_config are extensive.

ssh keys are stored in ~/.ssh/ for each user.

---

### Post by remag03 on 2021-02-26
Thank you I understand a bit more about the keys now, I purged the package as you suggested and reinstalled it then removed the key from /home/user/.ssh and I was able to safely log in again, thank you again

---

