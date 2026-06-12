---
title: "[SOLVED] Administration Login Fails"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by kevrust on 2008-05-28
I'm an absolute newbie to linux/Ubuntu, and I installed Hardy Heron (8.04) on my newly assembled system.I later added Mythbuntu on top. All was well for a few days, but suddenly,  can't open password based applications in the System/Administration menus, for example Synaptic, or Device Drivers. I tried accessing Synaptic using sudo, and this worked, but I haven't tried any other applications. What happens from the Gnome menu is that a panel opens at the bottom of the screen, reading "Staring Administrative Application", a second panel opens saying "Starting Synaptic" (or whatever), and the little wheel icon rotates for a minute or so. The wheel disappears, the panels close, and nothing happens.  Formerly, a full window would open asking for the password. It's like it wants a password, but can' figure out how to ask.

Your help is appreciated!

---

### Post by rockerphil on 2008-05-28
here's what i'd do. just open up your terminal and run chis code

sudo passwd

it'll then ask you for you sudo password, and when entered correctly it'll as you for a new UNIX password, after you set it you can log in as the user "root" which when you do administrative tasks it doesn't ask for your password. hope it hels

---

### Post by sayakb on 2008-05-28
Post the output of
```
cat /etc/pam.d/common-auth
```

---

### Post by kevrust on 2008-05-28
When I run the code, here's what I get:

auth	requisite	pam_unix.so nullok_secure
auth	optional	pam_smbpass.so migrate missingok


No idea what it means

K

---

### Post by lwclam on 2008-05-29
I have the same problem.
After the first installation, it OK.
But after a few reboot, these problem appears.:(

EDIT: after I edited the hosts file, all back to normal. Thank you

---

### Post by kevrust on 2008-05-29
Can you explain how you edited the hosts file?
Thanks

---

### Post by kevrust on 2008-05-29
Just to explain:  I can edit from the root directory, I just want to be able to use the gui.
Thanks

---

### Post by kevrust on 2008-06-11
Back from vacation and downloaded the latest set of upgrades.  All is well again!  Thanks to all for their help and interest
:guitar:

---

