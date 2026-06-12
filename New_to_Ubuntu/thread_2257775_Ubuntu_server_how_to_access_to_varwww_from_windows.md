---
title: "Ubuntu server how to access to var/www/ from windows ?"
date: 2014-12-22
forum: New to Ubuntu
---

### Post by fatzombi on 2014-12-22
today i've installed ubuntu server on windows using Virtualbox i want ftp access to var/www/

---

### Post by nerdtron on 2014-12-22
Lazy way:
1. Install Filezilla on the windows machine. 
2. Open filezilla, on the Host put the IP address of server, your Username to login, Password, and port 22. Click connect.
3. Now upload your files to your home folder.
4. Login or SSH manually on the server and move your files to the /var/www folder. (you'll need to use sudo)
5. Change ownership of the files on /var/www folder to www-data. (you'll also need to use sudo)

---

### Post by Gone fishing on 2014-12-22
Do you need ftp access or just to upload files from windows? If so the ssh client Putty [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) should do the trick and here's a howto [https://www.hostknox.com/tutorials/ssh/putty/file-transfer](https://www.hostknox.com/tutorials/ssh/putty/file-transfer) or you could try [http://winscp.net/eng/docs/free_ssh_client_for_windows](http://winscp.net/eng/docs/free_ssh_client_for_windows)

---

### Post by lisati on 2014-12-22
Are you looking for easy ways of updating a server that displays web pages? If so, you'll need to keep in mind that recent versions of Ubuntu use /var/www/html for Apache's home folder instead of /var/www used by older versions.

---

