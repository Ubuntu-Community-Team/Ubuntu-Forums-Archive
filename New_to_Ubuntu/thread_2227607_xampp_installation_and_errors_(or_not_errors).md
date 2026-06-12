---
title: "xampp installation and errors (or not errors)"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by swipisnt on 2014-06-03
Hello my friends i have a problem. i trying to install xampp, so my first step is
```

chmod 755 xampp-...-installer.run
sudo ./xampp-...-installer.run

```
after i hit enter i get message:
```

sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set

```

and i stuck on this one because it wont let me run installer. need help please :)

Thank you

---

### Post by jdeca57 on 2014-06-03
That's not a problem of xampp but one with sudo. See: [http://askubuntu.com/questions/452860/usr-bin-sudo-must-be-owned-by-uid-0-and-have-the-setuid-bit-set](http://askubuntu.com/questions/452860/usr-bin-sudo-must-be-owned-by-uid-0-and-have-the-setuid-bit-set) I don't know how you managed to do that, but since root access seems impossible...

Edit: look at the third solution, the link to SO might work.

---

### Post by AskTell on 2014-06-03
First off you should probably reinstall your OS since your permissions have been messed up... 

If you want to continue using this installation of what I'm assuming is an Ubuntu desktop distro go ahead and restart the machine and press shift at boot menu. This should  bring up GNU GRUB (ie recovery mode) menu.
  
[LIST]
[*]If this doesn't work, just restart mid boot and choose recovery mode when prompted on next launch.
[/LIST]
  Select the line which starts with Advanced options
  Select the topmost version of the OS ending with ("recovery mode")
  Press enter
  In the following menu, go down to "Drop to root shell prompt"
  Type the following:

  mount -o remount,rw /

mount --all

chown root:root /usr/bin/sudo

chmod 4755 /usr/bin/sudo

restart
  This should restore sudo privellages.

As for installing xamp I found this nifty little video tutorial on youtube [http://www.youtube.com/watch?v=9oK4DsfVBmE](http://www.youtube.com/watch?v=9oK4DsfVBmE)

---

### Post by swipisnt on 2014-06-03
looks like i need reinstall OS because i did what you told me but after restart no changes... ahhh well... how ppl said "shits happens" :) thank you guys!

---

### Post by Lars Noodén on 2014-06-03
If you are going to re-install anyway you might try using the package manager this time around instead of xampp.  

```

sudo apt-get update
sudo apt-get install lamp-server^

```

(Note the caret ^ there)

Some of the advantages include automatic updates and security updates and having everything (programs, logs, data) in the normal location for Linux.

---

