---
title: "Multi user LAMP setup"
date: 2011-05-28
forum: Programming Talk
---

### Post by darioshanghai on 2011-05-28
Hi,

I am trying to set up a web server with the following:
- SSH2 access for different users
- the ssh access is necessary for the users to upload files to a web server 
- the websites are dynamic (Drupal, WordPress).

The problems:

- WP automated updates are not working, I suspect because of permission issues
- Apache is set up as www-data user, so it can access files only if www-data is the owner, but the users too can only access the files if they are the owners.

How do I allow www-data to edit access regular users' files as the owner?

Do you have any decent example of LAMP setup where multiple users access and modify files via ssh (and each user can manage more than one website)?

Thank you.

---

