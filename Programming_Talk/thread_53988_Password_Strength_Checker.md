---
title: "Password Strength Checker"
date: 2005-08-03
forum: Programming Talk
---

### Post by teardrop on 2005-08-03
I'm writing a bash shell script to manage ftp virtual users and i want to use the built-in password strength checking utility, but i'm having difficulty finding what that is precisely.  I would like to enforce that there be at the least lowercase, numbers, and special characters and that it be a minumum of 8 characters long.  While I could write the password checking into the script, why recreate the wheel?  I'm under ubuntu btw.  Thanks for any help you can provide.  And help with using it would be appreciated.

---

### Post by ubuntu_demon on 2005-08-03
maybe check out libpam-passwdqc or its source

---

### Post by teardrop on 2005-08-03
[QUOTE=ubuntu_demon]maybe check out libpam-passwdqc or its source[/QUOTE]

I can't figure out how to use this in the script, any help would be appreciated.  This seems to be a little beyond me, I don't know how to load or access these libraries.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=teardrop]I can't figure out how to use this in the script, any help would be appreciated.  This seems to be a little beyond me, I don't know how to load or access these libraries.[/QUOTE]
 I've never made a password strength checker or directly accessed libraries either :)

I'll look into it a bit this weekend. Let's see what I can dig up. Maybe I'll create a password strengh checker and learn python at the same time next week.

---

### Post by LordHunter317 on 2005-08-04
You wouldn't.

You'd add the pam module to the pam stack, and then call ueradd/delete and passwd normally.  PAM handles the rest for you.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=LordHunter317]You wouldn't.

You'd add the pam module to the pam stack, and then call ueradd/delete and passwd normally.  PAM handles the rest for you.[/QUOTE]
 please elaborate a bit

---

### Post by LordHunter317 on 2005-08-04
PAM is the authentication stack used by all supporting application (which is most of them, on Linux).

You change the contents of the stack and all applications using PAM are effected.  For example, if you start using LDAP, you change the approrpiate pam files, and all applications start using LDAP: no recompiles or updates necessary.

---

### Post by teardrop on 2005-08-04
Like I said, I want to use it from within a script to check the passwords of virtual users.  "You wouldn't."  Wouldn't I?  What PAM module are you referring to?  Is there one for adding and deleting virtual FTP users from a text file?  Do I need to write my own PAM module now?  Or is there a simple program for password strength checking out there?  Please elaborate.

(I stress VIRTUAL, meaning they are not found in the passwd file, they are just names in a text file that are loaded in a berkeley db for use by PAM when authenticating in vsftpd.  I'm trying to manage them using this program and manipulating the contents of a textfile containing users/passwords before they are loaded into the db)

---

