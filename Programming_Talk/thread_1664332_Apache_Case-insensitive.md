---
title: "Apache Case-insensitive"
date: 2011-01-10
forum: Programming Talk
---

### Post by PJOS13 on 2011-01-10
Hi, recently I've been migrating my development environment to ubuntu (desktop edition, because this is not a server, is just my computer) and I've been having some problems with apache case-sensitive (I'm an absolute beginner with it).

I want to make apache case-insensitive, but I didn't find a complete and easy to follow solution online more than doing this:

[LIST=1]
[*]From the command line, type sudo su to get root privileges.
[*]nano /etc/apache2/mods-available/speling.conf
[*]Type CheckSpelling on and hit ctrl-x, y to exit and save the file.
[*]type a2enmod and then speling and hit enter.
[*]type /etc/init.d/apache2 reload to reload apache.
[*]Mistype a url to test it.
[/LIST]

I found that here: [http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/](http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/)

It worked for some things but I'm still having a lot of problems with capitalization. Any suggestions? :confused:

Please, help me! I don't wanna go back to windows an ISS. And fixing my file name by hand won't be a solution it will take to long. :(

BTW I'm using ubuntu 10.10 desktop edition 32-bits, and I've not moved any apache configuration more than that described above.

---

