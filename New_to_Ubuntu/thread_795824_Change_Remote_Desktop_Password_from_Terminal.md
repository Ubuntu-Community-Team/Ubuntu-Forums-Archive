---
title: "Change Remote Desktop Password from Terminal"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Mazen on 2008-05-15
Hi All,
I configures VNC and logged in my ubuntu box remotly, i had an unsecure password and when i changed it to a secure one, which happens to be the same as my root password, VNC is failing to authenticate!
i tried vncpasswd and vnc4passwd in the terminal and changed them but still the same thing is happening and i need to reset my password from the "Remote Desktop" menu!
is there a way to do that through the terminal because i am logged on SSH and away from my laptop!
thanks!

---

### Post by hariprs on 2008-05-15
Try deleting the password file inside /home/<user>/.vnc folder.

---

### Post by Mazen on 2008-05-15
didn't work !!:(

---

### Post by jcr1 on 2008-07-08
Did you solve this? I'd like to know too.

---

### Post by traveler400 on 2008-10-07
I could use an answer to this as well...

---

### Post by traveler400 on 2008-10-08
This worked for me (on Ubuntu 8.04):

- gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
- go to [http://www.javazoom.net](http://www.javazoom.net) and encode the password you originally set in remote desktop preferences
- gconftool-2 -s -t string /desktop/gnome/remote_access/vnc_password <encode_pwd>

Here is the whole thread where I found the answer:

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/141032")

Hope this helps someone out.

---

### Post by sjaxso on 2008-12-03
Just confirming this worked for me also -
I didn't understand the line "- gconf-editor"
so I skipped it, it still worked.

---

