---
title: "Windows share mount_[Errno 1] Operation not permitted:"
date: 2017-04-27
forum: New to Ubuntu
---

### Post by rajavinoth on 2017-04-27
Hi,

  I mount windows share by added this line on fstap //192.168.3.23/Data/tactic/assets /media/windowsshare  cifs  domain=rajvino.com,username=uname,password=pwd,file_mode=0777,dir_mode=0777,gid=1000,iocharset=utf8,sec=ntlm  0  0

  I did configure a web server on ubuntu 14.04 LTS using apache and postgresql. When i try to upload a file to that windows share got error given below.but the file is uploaded and the process stuck there after error.

 Error :  [COLOR=#000000][FONT=sans-serif]Check-in failed: [Errno 1] Operation not permitted: '/media/windowsshare/feb/shot/fly/PRE/ge-ct-scan-machine-500x500_PRE_v001.jpg'

  I think it is happened  beacuse of some missing permission. Please tell me the solution for this issue.
[/FONT][/COLOR]

---

### Post by lammert-nijhof on 2017-04-28
Apache is not for windows sharing, it is a web server. You have to install samba to share files on your network. In Ubuntu you can simply right click the folder you want to share and select "local network share" from the menu. It will install the relevant parts of samba for you. Most file managers (nautilus, nemo a.o) will also allow you to connect permanently to such a windows share without using fstab, fstab is the more nerdy way. You also might have to add your user-id to the samba file server by the smbpasswd command, I don't remember whether also that is done by the file manager nowadays.

---

