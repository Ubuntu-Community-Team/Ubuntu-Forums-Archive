---
title: "Success on useradd...next question"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by campusgray on 2008-10-18
Hi all, trial and error. i re-installed ubuntu on vmware. i was able to add the users and create group. How do i let one of the users access a web server?....the instructions here confuse me..it says  /usr/bin/httpd  as root....

---

### Post by Little Girl on 2009-10-26
From your mention of **/usr/bin/httpd**, I'm assuming you're using Apache. If I'm wrong, ignore this post. ;)

[COLOR="red"]**_An insecure way of letting a user serve up a page on your server_**[/COLOR]
You can create a directory for the user inside the the web server's directory. The user will require access to your system files and password, so this is only for someone you really trust. Any changes he or she makes to his or her folder will immediately take effect on the web server.

For this example, let's say your web server is located at **/var/www** on the virtual machine, the user is **user01**, and the folder he or she will be serving up is located at **/var/www/user01** on the virtual machine.

[LIST=1]
[*]Load up the virtual machine.
[*]Open a terminal window.
[*]Create a directory in your web server for user01 by typing this:
```
mkdir /var/www/user01
```
[*]Ask user01 to put an index.html file in the /var/www/user01 directory, or put one in it for him or her.
[*]Test the setup by opening a browser on any machine and typing this into the address bar, replacing IP with your server's IP or domain name:
```
http://IP/user01/index.html
```
[/LIST]

[COLOR="red"]**_A secure way of letting a user serve up a page on your server_**[/COLOR]
You can create a symbolic link from a specific folder inside the user's home folder to the web server's folder. This way the user can have normal access to the contents of the folder without needing access to your system files or password. Any changes he or she makes to that folder will immediately and automatically take effect on the web server.

For this example, let's say your web server is located at **/var/www** on the virtual machine, the user is **user01**, and the the folder he or she will be serving up is located at **/home/user01/mywebpage** on the virtual machine.

[LIST=1]
[*]Ask user01 to create the /home/user01/mywebpage directory, or create it for him or her.
[*]Ask user01 to put an index.html file in the /home/user01/mywebpage directory, or put one in it for him or her.
[*]Load up the virtual machine.
[*]Open a terminal window.
[*]Create a directory in your web server for user01 by typing this:
```
mkdir /var/www/user01
```
[*]Create a symbolic link to user01's folder in your web server by typing this:
```
sudo ln -s /home/user01/mywebpage /var/www/user01
```
[*]Test the setup by opening a browser on any machine and typing this into the address bar, replacing IP with your server's IP or domain name:
```
http://IP/user01/index.html
```
[/LIST]

---

