---
title: "can not connent via sftp"
date: 2009-10-03
forum: Philippine Team
---

### Post by guitar_man on 2009-10-03
mga sir,

help nga po..

ayaw na mag-connect ng client sa server...fresh install lang yung server...
nung hindi pa ako nagre-install nagconnect pa siya...

nag-connect naman yung ssh...sftp lang talaga ayaw..sa terminal naman pwede yung sftp..help nga sir.

---

### Post by guitar_man on 2009-10-04
sino po ba may alam nito???naguguluhan na ako.

---

### Post by loell on 2009-10-04
snip--

ok, what port are you using?


from [http://www.openssh.com/faq.html#2.9]("http://www.openssh.com/faq.html#2.9")

2.9 - sftp/scp fails at connection, but ssh is OK.

sftp and/or scp may fail at connection time if you have shell initialization (.profile, .bashrc, .cshrc, etc) which produces output for non-interactive sessions. This output confuses the sftp/scp client. You can verify if your shell is doing this by executing:

ssh yourhost /usr/bin/true

---

### Post by guitar_man on 2009-10-04
port 22 lang sir..ayaw ko na baguhin..ok lang ba yun?secure ba ako kahi thindi ko baguhin..sabi kasi ng iba baguhion daw...

sir loell yung sftp ng terminal nakaka-connect naman..yung  nautilus lang talaga tsaka pag ginamit yung connect to server ng gnome....

---

### Post by guitar_man on 2009-10-04
port 22 lang sir..ayaw ko na baguhin..ok lang ba yun?secure ba ako kahi thindi ko baguhin..sabi kasi ng iba baguhion daw...

sir loell yung sftp ng terminal nakaka-connect naman..yung  nautilus lang talaga tsaka pag ginamit yung connect to server ng gnome....

---

### Post by loell on 2009-10-04
diba yung nautilus di pa daw maka-connect sa sftp? or baka outdated na info na ito, nakakaconnect ka ba before?

---

### Post by loell on 2009-10-04
tingnan mo daw yung file na,

**~/.ssh/known_hosts**

bak kasi na iba ang public key?

---

### Post by guitar_man on 2009-10-04
dati po nakakaconnect ako dati gamit nautilus...nag-fresh install lang po ako ulit ng crungbang sa host na comp tapos ayun ayaw na sa nautilus...

pinalitan ko na din yung sa ~/.ssh/known_hosts

---

