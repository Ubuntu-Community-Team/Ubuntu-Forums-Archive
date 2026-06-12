---
title: "Apache /var/www permissions"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by deputypresident on 2013-12-30
Hello,

   Ignore my username... don't understand how it doesn't allows me to choose my username. I'm new to ubuntu and apache. I manage to install the LAMP setup, however, I can't seem to be able to upload my drupal onto the /var/www. What should I do to allow uploading of the installation files? Also, what should I do to be able to have apache have a folder for subdomains?

Thanks

---

### Post by 3rdalbum on 2013-12-30
> **deputypresident said:**
> I can't seem to be able to upload my drupal onto the /var/www. What should I do to allow uploading of the installation files?

/var/www is only writable by root, as it's a system location. However you are installing Drupal, or however you are moving files into /var/www, you need to do it as root. Usually that involves putting the 'sudo' command in front of the command ("sudo cp file.txt /var/www/file.txt" for instance) or opening a file browser as root using "gksudo nautilus".

---

### Post by Rockiger on 2013-12-30
Do you use apache on a server or just on you local machine?

---

### Post by deputypresident on 2013-12-31
> **3rdalbum said:**
> /var/www is only writable by root, as it's a system location. However you are installing Drupal, or however you are moving files into /var/www, you need to do it as root. Usually that involves putting the 'sudo' command in front of the command ("sudo cp file.txt /var/www/file.txt" for instance) or opening a file browser as root using "gksudo nautilus".

That's the problem, its kinda troublesome. Is there any other way?

---

### Post by deputypresident on 2013-12-31
> **Rockiger said:**
> Do you use apache on a server or just on you local machine?

I'm running on a VPS. Is there any way I can create another home directory instead of /var/www with my non-root account so I don't have to meddle with the root account? Also, please advise how can I create a subdomain folder?

Thanks

---

### Post by deputypresident on 2014-01-02
Anyone?

---

### Post by 3rdalbum on 2014-01-02
I don't understand what is troublesome about it. Whatever commands you are using, just put 'sudo' in front of them.

---

### Post by cessanfrancisco on 2014-01-02
Just open a terminal and type the command:  

```
sudo nautilus
```

then type your password.

Now you can do all the stuff you'd normally with nautilus with the exception that you can do it as root.  You can upload, download, copy, delete, move...

---

### Post by bertan2 on 2014-01-03
> **deputypresident said:**
> That's the problem, its kinda troublesome. Is there any other way?

Usually, for my own website, I create a new directory under /home, for example, /home/yourname/public_html. Then you will be the owner of public_html and you can put your site in there without having to do sudo all the time.

---

### Post by deputypresident on 2014-01-04
So how do I do that?

---

### Post by bertan2 on 2014-01-09
Sorry, I've been away for a few days. 


See the section beginning at "Virtual Hosts" in this tutorial:


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by deputypresident on 2014-01-11
> **bertan2 said:**
> Sorry, I've been away for a few days. 


See the section beginning at "Virtual Hosts" in this tutorial:


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Alright, Thank You!

---

