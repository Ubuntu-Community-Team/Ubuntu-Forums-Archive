---
title: "Sharing files"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by HaemoLacria on 2008-04-26
How can I share files? I mean with another computer in my house.
Thanks a bunch

---

### Post by Michael.Godawski on 2008-04-26
You probably need a samba share if you want to share files with a windows machine:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29)

For Linux<>Linux share use ssh:
[http://ubuntuforums.org/showthread.php?t=134439](http://ubuntuforums.org/showthread.php?t=134439)
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by swoll1980 on 2008-04-26
install samba,```
sudo apt-get install samba
``` create a samba password ```
sudo smbpasswd -a username
``` then enter your sudo password then the new samba pass word

---

