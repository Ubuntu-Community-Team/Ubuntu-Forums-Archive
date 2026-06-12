---
title: "Sudo"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Xafinia on 2008-10-09
Hi, 

I am just starting to use ubuntu and I am having some problems downloading stuff (like java, jmol...), as I keep coming across commands that I can't execute because I am not the root. I don't have the root password, is it possible to find out what this is? 

I was looking for ways around this and came across 'sudo', but if I try typing 'sudo *username*' it asks for my password and then tells me: '*username* is not in the sudoers file.  This incident will be reported.' How do I add my username to the suoders file? 

Thanks a lot for your help!!

---

### Post by nothingspecial on 2008-10-09
Log into to the account you created when you installed Ubuntu. If any process requires you to become root prefix the command with sudo. eg
```

sudo apt-get install name-of-app
```

Before ubuntu carries out that command it will ask for your password (the one you used to log in) As you type it you won`t see it then hit enter

---

### Post by jken146 on 2008-10-09
Check out Add/Remove and/or Synaptic before going hunting on the the web when you want to install something.

---

### Post by az on 2008-10-09
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bölvaður on 2008-10-09
Did anyone acually read the question?!? People READ THE QUESTIONS!

> **Xafinia said:**
> Hi, 

I am just starting to use ubuntu and I am having some problems downloading stuff (like java, jmol...), as I keep coming across commands that I can't execute because I am not the root. I don't have the root password, is it possible to find out what this is?

No unfortunetly there isn't a good way to do this. But there is a way to change the root password.

Boot into rescue mode (begins with R atleast) which is a command line only interface. I will update this if I remember how exactly how to do it but this is what I remember:

type passwd
pick new password, then you are asked to repeat it, wholla.

---

### Post by rick08 on 2008-10-09
Here is an awesome cheat sheet for learning how to work around in the terminal. [http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/]("http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/")  This guide helped me remember basic terminal commands and got me started with mastering terminal commands.

---

### Post by aysiu on 2008-10-09
Yes, everyone read the question. The OP thinks setting a root password is necessary. It is not, and that's why Ubuntu does not have the root account enabled for log in by default.

We're trying to show the OP the proper way to install software or accomplish root tasks.

Here's a screenshot-laden guide to installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And instructions specific for Java:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

---

