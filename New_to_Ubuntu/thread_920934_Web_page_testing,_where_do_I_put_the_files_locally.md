---
title: "Web page testing, where do I put the files locally  so that  Apache can see them?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by artgeek on 2008-09-15
Maybe I'm just not writing the right search term but I couldn't find this in the help or here in the forums.

*Problem*
- Want to test web pages locally using the built in Apache server.

*Hurdles*
- Mac background, know where to put my files in my user folder to have them show up though the local server in OS X.5, but a bit stymied by the Ubuntu system. :confused:

- Trying to test install of either Wordpress or Movable Type. Wordpress preferred.

If this has come up before links would be greatly appreciated, thanks.

---

### Post by jken146 on 2008-09-15
If you've already installed Apache, put them in /var/www and point your browser to [http://localhost](http://localhost)

---

### Post by artgeek on 2008-09-16
I tried to do that, and it says that the folder is locked and I don't have the privilages for it. Am I doing something wrong?

I am hoping to find a way to get it to see a folder in my home directory so I don't need to be constantly using SUDO to move files around.

---

### Post by bodhi.zazen on 2008-09-16
sudo chown -R user.www-data ~user/web_directory
sudo chmod 770 ~user/web_directory

You may need to set permissions of the files in the directory as well, depends on what you are doing exactly.

You may also wish to read on linux permissions.

[uhelp]community/FilePermissions[/uhelp]

---

### Post by halitech on 2008-09-16
there is more information here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

look for the section on Editing Apache Configuration

---

### Post by jerome1232 on 2008-09-16
meh, I've always liked this guide [http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

It tells you how to tell apache to search for the site in a folder of your choosing.

After all normal webpage editing shouldn't be done as root.

---

### Post by artgeek on 2008-09-16
bodhai.zazen, hailtech, and jerome1232

Thank you all for the links I will be looking into those. You all rock!:guitar:

---

