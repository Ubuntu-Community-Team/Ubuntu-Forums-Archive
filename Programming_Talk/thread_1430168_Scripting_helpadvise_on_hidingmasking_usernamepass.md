---
title: "Scripting help/advise on hiding/masking username/password"
date: 2010-03-15
forum: Programming Talk
---

### Post by newbie01.linux on 2010-03-15
Hi,

I currently have a UNIX script with a function that uses a username and password to connect to the database, retrieve some information and then exit.

At the moment, am getting the username and password from a hidden plain text file and permission set to -r--------, i.e. read only to who own the file.

The owner of the file is the same owner of the script. At the moment, am not too overly concern as the script works as it is but I want to know if anyone have a suggestion if there is any better way of achieving the same thing with some "form" of security, i.e., for example, masking the username/password.

Basically, I want to be able to mask or hide the username or password in some way. I've thought about encryting the password file, which is in plain text, using simple crypt command from which I retrieve the username and password but I need to decrypt it as well which is sort of similar to how it will be as it is now once it is decrypted.

Is there anyway that I can get a username and password in some gibberish format and then translating them into something usable which can be passed on the next command that requires the username/password.

Any advise or suggestion will be very much appreciated. Some kind of starting point to test with I supposed ...

Thanks in advance.

---

