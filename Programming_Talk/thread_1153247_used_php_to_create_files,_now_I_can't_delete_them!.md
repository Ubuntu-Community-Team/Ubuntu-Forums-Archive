---
title: "used php to create files, now I can't delete them!"
date: 2009-05-08
forum: Programming Talk
---

### Post by machine_VS_johnHenry on 2009-05-08
I wrote a php script that creates .txt files, but the .txt permissions are under apache, and I can't delete the files now. The files are on my webserver, and I don't have root access, so I can't delete them that way.... Will I have to write a script to delete these files:guitar:?

---

### Post by AlexDudko on 2009-05-08
Yes, you'll have to.

---

### Post by machine_VS_johnHenry on 2009-05-11
Rats!

---

### Post by whansen02 on 2009-05-11
You could also write a script to quickly chown those files (if the apache user is authorized to use chown on files owned by itself) to your user name.  Beware - it might not be able to chown them back if you do something wrong if this is a shared hosting setup.

Then also update your original script that creates the files to chown the files after it creates them.

---

### Post by stroyan on 2009-05-11
Many operating systems won't let a non-root user chown a file.
They won't even let a user give away a file that they can remove.

If you need a php script to get the right user id, then you could consider using a php script that acts like a shell.  Have a look at [http://phpshell.sourceforge.net/](http://phpshell.sourceforge.net/) .  Note that the php must not be running in 'safe mode' for the phpshell to work.  And do be cautious about security.  If someone else gets access to a php shell it is just about as much trouble as them having access to your normal shell account as your normal user id.

---

### Post by whansen02 on 2009-05-11
> Many operating systems won't let a non-root user chown a file.

Ah, you're right.  Something tells me I've been logging in as root too much if I'm passing along these sorts of suggestions :(

> And do be cautious about security. If someone else gets access to a php shell it is just about as much trouble as them having access to your normal shell account as your normal user id.

I think I used to use one called PHP Commander, there's many out there.  And yes - if you use a php shell lock it down good.  It should not be accessible without at least htaccess password protection and you should restrict access to specific single ip addresses (IMO)  This is not being paranoid considering what someone can do with one of these.

---

