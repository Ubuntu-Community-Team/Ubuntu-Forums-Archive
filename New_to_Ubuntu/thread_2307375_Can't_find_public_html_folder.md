---
title: "Can't find public html folder"
date: 2015-12-24
forum: New to Ubuntu
---

### Post by Arshia_Aghaei on 2015-12-24
Hi all , i tried to solve my php problem i have like in [this thread]("http://ubuntuforums.org/showthread.php?t=1983120") .
I read user *Senior_Buckethead* solution , but i can't find the public html folder in home.
I've installed and tested apache2 and got the "**It works !**" page by typing *localhost* in my browser.

What is the problem ?

I'm using ubuntu 14.04 LTS.

---

### Post by brian-mccumber on 2015-12-24
When I installed a lamp I found the www folder in /var as in computer/var/www/html from the file browser. Since I wasn't using the lamp to serve online webpages, just for dev purposes, I took ownership of the folder so I could add/edit/delete files in it. There is a way to make virtual localhost/www directory in your home drive too but it requires editing apache conf files or you can just recreate the var/www/html directory on the home drive.

[http://askubuntu.com/questions/617190/how-to-setup-apache2-virtualhosts-on-your-home-directory-on-ubuntu-14-04-](http://askubuntu.com/questions/617190/how-to-setup-apache2-virtualhosts-on-your-home-directory-on-ubuntu-14-04-)

---

### Post by steeldriver on 2015-12-24
I don't think users' public_html folders are created by default, you would need to manually create one

```

mkdir ~/public_html

```

and then put whatever personal webpage content you want there

---

### Post by Arshia_Aghaei on 2015-12-24
> **steeldriver said:**
> I don't think users' public_html folders are created by default, you would need to manually create one

```

mkdir ~/public_html

```

and then put whatever personal webpage content you want there
No result for uisng the *mkdir ~/public_html code.*

---

### Post by steeldriver on 2015-12-24
What result are you expecting? All it does is create the directory

Did you also enable the userdir module and restart the apache2 service?

---

### Post by Arshia_Aghaei on 2015-12-24
> **brian-mccumber said:**
> When I installed a lamp I found the www folder in /var as in computer/var/www/html from the file browser. Since I wasn't using the lamp to serve online webpages, just for dev purposes, I took ownership of the folder so I could add/edit/delete files in it. There is a way to make virtual localhost/www directory in your home drive too but it requires editing apache conf files or you can just recreate the var/www/html directory on the home drive.

[http://askubuntu.com/questions/617190/how-to-setup-apache2-virtualhosts-on-your-home-directory-on-ubuntu-14-04-](http://askubuntu.com/questions/617190/how-to-setup-apache2-virtualhosts-on-your-home-directory-on-ubuntu-14-04-)

Do I need to create a virtual localhost/www folder for solving the php problem ?

> **steeldriver said:**
> What result are you expecting? Did you also enable the userdir module and restart the apache2 service?
There is no folder stiil on home directory called public html.

---

### Post by steeldriver on 2015-12-24
OK sorry in that case I have no idea what you are asking about

---

### Post by brian-mccumber on 2015-12-24
> **brian-mccumber said:**
> or you can just recreate the var/www/html directory on the home drive.

Goto Home then create a directory named var and inside var make a www folder and inside www make a html folder, then put your files inside of html. Apache should pick up the new directory.

The directory that was created when Apache was installed is /var/www/html starting in root drive or Computer if you're using your file browser but you always need elevated privileges to use the default folder. If you're serving webpages, you should create virtual drives in home directory, if you're just using localhost for dev then you can use the terminal to get permissions for the default www/html folder and put your files in there.

---

### Post by Arshia_Aghaei on 2015-12-24
> **brian-mccumber said:**
> Goto Home then create a directory named var and inside var make a www folder and inside www make a html folder, then put your files inside of html. Apache should pick up the new directory.

The directory that was created when Apache was installed is /var/www/html starting in root drive or Computer if you're using your file browser but you always need elevated privileges to use the default folder. If you're serving webpages, you should create virtual drives in home directory, if you're just using localhost for dev then you can use the terminal to get permissions for the default www/html folder and put your files in there.
You mean the public html folder is the same as */var/www/html* ?

---

### Post by Arshia_Aghaei on 2015-12-24
PHP problem solved. Thanks all.

I don't know how to remark the thread as solved...

---

### Post by Vladlenin5000 on 2015-12-24
You can use the thread tools in the first post to mark it as solved.

---

### Post by brian-mccumber on 2015-12-25
Just to clarify the last question op asked, yes, var/www/html is equivalent to public_html. On a paid web host it is public_html which you can recreate on your computer by creating a public_html folder then making a listing for it in the apache.conf file like the example from the first link I sent you, which is just what the web hosts do when they are sectioning up a drive for their clients' domains.

Here is a link to the official Apache wiki, there is alot of stuff to read there. - [http://wiki.apache.org/general/](http://wiki.apache.org/general/)

---

