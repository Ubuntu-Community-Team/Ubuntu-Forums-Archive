---
title: "Shell script on startup"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by linuxforrealpeople on 2008-05-19
I have created a simple data backup shell script. It runs fine and I want it to run on startup. I set this up in system/preferences/sesions but it does not run. Any help would be appreciated. Thanks.

---

### Post by tamoneya on 2008-05-19
that is how it should work.  Are you getting any error messages?  Can you put some logging into the shell script so that we can figure out if it is actually doing anything.

---

### Post by Oak37 on 2008-05-19
Try wrapping the command in double quotes like so, "home/user/Documents/Script.sh"

---

