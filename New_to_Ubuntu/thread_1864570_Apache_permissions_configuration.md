---
title: "Apache permissions configuration"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by Psyrus on 2011-10-19
Hi,

I have a small issue regarding my Apache setup. I have installed Apache, MySql, PHP. Apache is running and I have configured the virtual directory to be in my home directory (/home/mpt/dev_websites). This works. I have recently downloaded a site template, which includes some .js files. The template is not rendered correctly. For one, all the images are missing. My Firebug add-on tells me that all the .js files have 403 errors: (13) Access Denied. I have already set permissions for the directory to 777. What else could be the cause?

In the past I used XAMPP in Windows, which worked very well for needs. I have tried XAMPP for Linux, which installs correctly, but I have the same issue with this template under XAMPP.

---

### Post by mcduck on 2011-10-19
Check the permissions of the files themselves. And in case the server doesn't have access to any files, then your home directory as well. Keep in mind that Apache by default will run as it's own user account so it's not a question if *you* have the permissions or not.

---

### Post by Psyrus on 2011-10-19
Ah...thank you. That was it. The files containing the .js & images were set to only allow me access. Setting access for other users sorted it out.

---

