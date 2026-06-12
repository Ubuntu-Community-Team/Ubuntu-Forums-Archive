---
title: "Create user profile without admin/root privilege, but still enable Software Updater?"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by viktor-brech on 2013-09-30
Hello,

I am running Xubuntu 12.04 64bit, and would like to create a new user account. That user should not be allowed to install new software, but I still want to make it possible that security updates and other updates are regularly installed without requiring an admin password each time.

The goal is to keep security patches etc. up-to-date, even if this non-privileged user is the only person using the computer for a long time.

For any pointer I would be very grateful.

VB

---

### Post by whitesmith on 2013-09-30
Welcome! By design, Linux requires root privileges or equivalent (sudo) to install software with the exception of stuff installed in $HOME. Of course, you could play a game by installing the patches yourself on an account with the requisite permissions. Use```
sudo -l
```to make sure you're good to go.

[edit]Second thought: it might be possible to create a privileged-mode script to download and apply these patches, but your work is cut out for you. Maybe you could find something like this with Google. GitHub has a lot of stuff like this. Check it out.

---

### Post by Impavidus on 2013-09-30
You can set Ubuntu to automatically download and install all security updates. Go to software sources (a menu in update-manager, synaptic and software centre), click on the updates tab and select the right settings. It should be clear when you get there.

---

### Post by whitesmith on 2013-09-30
> **Impavidus said:**
> You can set Ubuntu to automatically download and install all security updates. Go to software sources (a menu in update-manager, synaptic and software centre), click on the updates tab and select the right settings. It should be clear when you get there.Are you sure of this? Presumably the OP wants his user to be an ordinary user. Would this not exclude downloading and installing anything by playing with a checkbox? If that can be done it represents a pretty big security hole.

---

### Post by DuckHook on 2013-09-30
*Impavidus* is correct, I believe. Ubuntu is designed to install *security* updates without having to invoke sudo. All other types and especially kernel updates require sudo. I believe that the system was built this way so that kiosks, remote computers,  etc could have potential security holes filled without requiring some administrator to intervene. The setting is in: Software Sources>Updates>"When there are security updates:". Just set this option to: Download *and install* automatically.

---

### Post by whitesmith on 2013-09-30
Not to beat a dead horse, but I was going by the OP's stated intention of allowing his user to handle "security updates and other updates." If only security updates were the issue I could understand Canonical's policy. It's that "other updates" part that gives me pause -- and on which my answer was based. I should have been more detailed.

---

