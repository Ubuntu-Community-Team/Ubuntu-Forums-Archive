---
title: "password protect certain commands in my bashrc"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by whitethorn on 2008-09-08
I need to connect to a couple different computers using Remote Desktop, that works. Since there are something like 5 computers and I need to do certain things on each computer.  I didn't feel like typing up rdesktop ip each time, so I added a couple aliases in my .bashrc which automated this process.  I also added my user name and password to the file, I don't exactly feel all the safe having some administration passwords lying around in plain text in my bashrc.  I want someway to get these seperated from my normal .bashrc and so I can use them only when I need them, and if possible have the file with the passwords protected/hidden?

---

### Post by unutbu on 2008-09-08
I agree with you that leaving passwords as plain text in any file is a bad security risk.
You could chmod'd it so only you have permission to read .bashrc, but there are a number of ways an attacker could get around this. You could encrypt the admin password, but then you would need to type in a password to unencrypt the admin password. That won't save you much typing would it? :)

So I think you are caught between the proverbial rock and hard place. You can either continue typing in the password(s) and maintain security, or you can throw up a lame defense which probably would not thwart a knowledgable attacker.

---

