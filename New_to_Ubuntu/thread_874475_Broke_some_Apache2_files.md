---
title: "Broke some Apache2 files"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Rakathan on 2008-07-30
I was trying to get my Apache server set up, and I learned that the default directory for web files was set to /var/www.  As a non-root user, I quickly figured out that I can't access this when I tried to change the files.

To fix this, I decided to change the web file directory to something I can access with my home directory.  The file I needed to edit was /etc/apache2/sites-available/default.  And of course, as a non-root user I can't access this either!  So I went to the console to move it out temporarily for editing.  Here's the line that broke it:

... :/etc/apache2/sites-available$ sudo mv default /home$

Now the "default" file doesn't exist anywhere (used the windowed search for the whole file system) on the computer.


There are a few options I see from here:
1) Download Apache2, rip that file out of the package and replace it (after changing the web directory, of course)
2) Find the default file somehow (I couldn't have deleted it, right?)
3) Give up and cry about it

Any help is much appreciated! Also, if there are holes in my logic, please clarify them for me.  I'm trying to learn all of this at once, and the first way to improve how quickly I learn is probably to learn problem-solving techniques.

---

### Post by roquefilipe on 2008-07-30
the "mv" command can also be used to simple rename files, in addition to move them. 

I you really entered  "sudo mv default /home$" then your file was moved to the root directory "/" and renamed "home$". 

about your proposed options:
1) It should work, but I believe it requires root access. 
2) To search for a file I like to use "locate". It uses a database to search for your file. To manually update the database run "sudo updatedb". You can also try "find". Both are case sensitive I think.
3) never ;)

---

### Post by Rakathan on 2008-07-30
> **roquefilipe said:**
> the "mv" command can also be used to simple rename files, in addition to move them. 

I you really entered  "sudo mv default /home$" then your file was moved to the root directory "/" and renamed "home$". 

about your proposed options:
1) It should work, but I believe it requires root access. 
2) To search for a file I like to use "locate". It uses a database to search for your file. To manually update the database run "sudo updatedb". You can also try "find". Both are case sensitive I think.
3) never ;)

Yep, it was right there.  Thanks!

---

