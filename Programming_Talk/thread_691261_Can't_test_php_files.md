---
title: "Can't test php files"
date: 2008-02-08
forum: Programming Talk
---

### Post by mike_g on 2008-02-08
I want to run some php code. I had it working on my old Ubuntu PC before it broke. I just installed wordpress on another computer and dumped my php files in /var/www.

Now when i go to local host it displays the files, and that I have apache and php installed. The problem is when I select a php file it wont run in FF. Instead i get a dialog asking if i want to open it with gedit. 

Is there something I missed here? Or anyone know what i could do to get php to work?

Cheers.

---

### Post by DrMega on 2008-02-08
Have you set the permissions on the directory to allow execute?

---

### Post by mike_g on 2008-02-08
Yeah I set: **a+rwx -R** on the directory. 

I just created an Index.html file from which i seem to be able to link to a php file, the only problem is that none of the script seems to execute, and I also cant seem to access pages in subdirectories.

Edit: it seems to have something to do with directory paths, as they dont seem to work the same as in windows

---

### Post by Majorix on 2008-02-08
It is probably a problem with FF.

Can you view .php with FF on that installation? I know for one that these forums work with PHP, so can you view them on your comp?

---

### Post by aks44 on 2008-02-08
To me, it rather looks like something went wrong with the LAMP install.

Check that LAMP is correctly installed:
```
sudo tasksel
```Then check LAMP (**DON'T** uncheck anything, it could screw your installation up).


AFAIK FF has nothing to do with it, it only handles the pages according to the information the Apache server sends.

---

### Post by eggdeng on 2008-02-08
Check that you have installed libapache2-mod-php5. If not, install it.Then run
```
sudo a2enmod php5
```
then ```
sudo /etc/init.d/apache2 restart
```

---

### Post by tosk on 2008-02-08
> **eggdeng said:**
> Check that you have installed libapache2-mod-php5. If not, install it.Then run
```
sudo a2enmod php5
```
then ```
sudo /etc/init.d/apache2 restart
```

eggdeng is correct. Apache has to be instructed to load the PHP module before it will source PHP scripts.

---

### Post by mike_g on 2008-02-09
Thnks for the input. I'll try out the suggestions when I'm on my Ubuntu machine :)

---

### Post by Hilko on 2008-02-09
> **mike_g said:**
> 
Now when i go to local host it displays the files, and that I have apache and php installed. The problem is when I select a php file it wont run in FF. Instead i get a dialog asking if i want to open it with gedit. 


Hi mike,

I just installed a LAMP server using tasksel in synaptic package manager. I tried to test my server and i had exactly the same problem.

I solved it by stopping and restarting apache:
```
$ sudo /usr/sbin/apache2ctl stop
$ sudo /usr/sbin/apache2ctl restart
```

Hope this works for you too.

---

