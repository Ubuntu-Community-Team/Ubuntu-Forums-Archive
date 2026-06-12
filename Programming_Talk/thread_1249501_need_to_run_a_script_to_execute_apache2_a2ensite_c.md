---
title: "need to run a script to execute apache2 a2ensite command"
date: 2009-08-25
forum: Programming Talk
---

### Post by ac13 on 2009-08-25
Hi,

I'm on a php project where every registered user on the website get their own subdomain set up as a part of the registration.
I was planning to create a new virtual host config file in the sites-available with the appropriate vhost directives with the php fopen() function.

But I have two problems.

Firstly, php does not have permission to create a file in the *sites-available* folder.
Secondly, I need to write a script to run the a2ensite command to enable the site, how can I go about doing this?

Edit:
Folder *sites-available* permission is drwxr-xr-x, and as I understand the first three bits are Read Write and Execute for the Owner witch in this case is root.
So I changed the owner of the php file from my user to root, still it is not allowed to create the file(?).
Setting the write permission bit for Other of the *sites-available* folder (drwxr-xrwx) lets me create the file however.

Regarding security is it a good ide to let "Other" have write permission to this folder?

Cheers

---

