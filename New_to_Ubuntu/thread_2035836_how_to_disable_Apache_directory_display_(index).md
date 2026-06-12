---
title: "how to disable Apache directory display (index)?"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by stupidquestion on 2012-07-31
I have a directory that contains some user files, but no HTML or php files. If that directory is accessed, the server returns an index of all the files in that folder. How do I change this behavior so that such a list is not automatically viewable?

I've read that you can add the line "Options -Indexes" to http.conf to do this. But in Ubuntu my http.conf is empty, and adding it there doesn't work for me.


Then I tried adding it to /etc/apache2/apache2.conf, still doesn't work for me.


I've restarted apache2 service each time.


Ideas?

---

### Post by nbetham on 2012-07-31
I would try adding a <Directory> stanza for the specific directory and adding the Options -Indexes there. You could also add and empty index.html file so that the server doesn't default to indexing the directory. The other thing I would check for is in apache2.conf see if the indexes option is already defined and set that to -. It could be that the directive has already been defined and the server is using that instead of the one you are adding.

Regards,
Neil

---

### Post by stupidquestion on 2012-07-31
It apparently had to do with my VirtualHost statement. 
I had to edit the file: /etc/apache2/sites-enabled/000-default

After that it worked, now it returns "Forbidden" when the directory is accessed.

By the way, at the bottom of the Forbidden message is text describing my Apache version, my IP and port. Does anyone know if I can disable this too?

---

### Post by nbetham on 2012-07-31
Check out: [http://httpd.apache.org/docs/2.2/mod/core.html#servertokens](http://httpd.apache.org/docs/2.2/mod/core.html#servertokens) it hast a listing of the different server tokens that apache will send in it's responses. Also look at the ServerSignature directive right above ServerTokens on that link.

---

