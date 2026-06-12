---
title: "apache intranet"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ja660k on 2008-08-12
hey guys, i have apache installed...
and i can hit the index from the other computers...

but i just needa know what directory is it in so i can make my proper intranet?

---

### Post by iaculallad on 2008-08-12
> **ja660k said:**
> hey guys, i have apache installed...
and i can hit the index from the other computers...

but i just needa know what directory is it in so i can make my proper intranet?

On your terminal, use the command below to traverse to your apache (pages) directory:

```
cd /var/www
```

---

### Post by ja660k on 2008-08-12
thanks alot =)

but i have another problem, i want to put some pdf's in there
but when i drag n drop it says permission denied

---

### Post by Dill on 2008-08-12
Try this-- open a Terminal and navigate to the directory where you have your pdfs saved. Then, enter this code:

```
sudo cp your_pdf.pdf /var/www
```

And enter the root password, assuming you know it.

You have to execute the command as root because the root user owns the directory. No one except root has write permissions on the directory (try going into /var, typing ls -l and looking at the permissions), and you should probably keep it that way. So every time you need to move something into the directory, you'll need to execute the command as the root user using sudo.

---

### Post by ja660k on 2008-08-12
simple, thanks alot =D

---

### Post by rabatitat on 2008-08-12
you could also just put the pdf files into your /home directory and include that folder in your httpd.conf file.

It'd save you from the hassle of doing multiple sudos

---

### Post by rhodry on 2008-08-12
The easiest way for you to control your site without having to use sudo/root permissions is to create a Virtual Server in your /home directory.

There are very clear instructions given for how to do this in the 'Install a LAMP server for local web development' section at [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy).

Under /home/"myusername"/www/ I have a seperate folder for each person on my Intranet that holds all the relevant files for their respective web pages. That way I control all file access easily (no forgetting to be sudo) and if I want to publish the site to the wider Internet, I just ftp the relevant folder contents straight to the hosting site.

Very straight forward.

Cheers,
rhodry.

---

### Post by Joeb454 on 2008-08-12
> **rabatitat said:**
> you could also just put the pdf files into your /home directory and include that folder in your httpd.conf file.

It'd save you from the hassle of doing multiple sudos

I wouldn't recommend including your home folder as a webroot, all your files would then be accessible (or at least visible) from all networked machines (unless I'm very much mistaken).

Making a symlink to ~/www (/home/user/www) isn't a bad idea, as you wouldn't need sudo priveleges (except to set up the link), and only files in the www folder would be visible :)

---

