---
title: "Bash Question - passing input to command line"
date: 2009-10-23
forum: Programming Talk
---

### Post by akvino on 2009-10-23
Hello all!

I am just interested on what would be a good way in bash shell to pass password to ssh command once the password is prompted.


I am trying to make this on the fly, so I would prompt the user for the password, store it in the variable, and then use it to connect to a server via ssh username@servername. 

Once the password prompt comes on - how do you echo it to the stdin?

---

### Post by diesch on 2009-10-23
You can use expect (not installed by default). Usually the better way is to use key authentication with ssh-agent (see man ssh-keygen and man ssh-agent) instead of password authentication.

---

### Post by thantos on 2009-10-23
Maybe writing the info to a temporary identity file?

You prompt the user for their info, write it to an identity file,
use the -i option with ssh and the identity file, and then delete the file.

I don't think this is a very secure method

---

### Post by scorp123 on 2009-10-23
> **akvino said:**
>  I am just interested on what would be a good way in bash shell to pass password to ssh command once the password is prompted. 

This is extremely unsafe and not recommended. It would be better to SSH key-based authentication

"Password-less logins with OpenSSH"
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

With SSH keys configured correctly a user would not even see the password prompt .. and yet this method would be safe and can be used in scripts.

---

### Post by akvino on 2009-10-23
> **scorp123 said:**
> This is extremely unsafe and not recommended. It would be better to SSH key-based authentication

"Password-less logins with OpenSSH"
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

With SSH keys configured correctly a user would not even see the password prompt .. and yet this method would be safe and can be used in scripts.

I am already using ssh-keygen and authorized_keys. This is a bit different as I found usage for the install script when I am deploying new server. In essence - password is not stored anywhere but in the variable, and it is for personal/ internal usage.

My main problem is passing, echoing, redirecting password to the password prompt once ssh [email]username@servername.com[/email] is executed.

---

### Post by diesch on 2009-10-23
Then expect should be the right tool:

Description: A program that can automate interactiveapplications
 Expect is a tool for automating interactive applications
 according to a script Following the script, Expect knows what
 can be expected from a program and what the correct response
 should be. Expect is also useful for testing these same
 applications. And by adding Tk, you can also wrap interactive
 applications in X11 GUIs. An interpreted language provides
 branching and high-level control structures to direct
 the dialogue. In addition, the user can take control and
 interact directly when desired, afterward returning control
 to the script

---

