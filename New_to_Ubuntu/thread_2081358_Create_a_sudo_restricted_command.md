---
title: "Create a sudo restricted command"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by acolyte_to_jippity on 2012-11-06
Hello,

I'm trying to create a command on my system (i'm running 12.10) that can be run straight from terminal (not requiring a pathname) BUT only when executed via sudo.

I tried to create a script file, and place it in \bin, (where it sits alongside commands like ls, cat, etc etc) but it won't run.  even when I am inside the directory, as root I cannot execute it.

Is there a way to define an alias somewhere such that it won't run without sudo?

---

### Post by cwsnyder on 2012-11-06
Did you do? ```
sudo chown root:root script.sh
sudo chmod +x script.sh
```This assumes your script name is script.sh .

---

### Post by ajgreeny on 2012-11-06
The first part of cwsnyder's answer is correct, ie it gives root ownership of the script, but the second part simply makes it executable; it does not say who can execute it..

The easiest way is to use ```
sudo chown root:root script.sh
sudo chmod +x script.sh
sudo chmod 744 script.sh
``` (or even 700).

So having given ownership to root, the +x makes it executable and the 744 gives root permission to read/write and execute, but all others can only read;  700 would mean root still has the same permission, but all others have none, ie can not read write or execute.

---

### Post by wojox on 2012-11-06
> **ajgreeny said:**
> 
So having given ownership to root, the +x makes it executable and the 744 gives root permission to read/write and execute, but all others can only read;  700 would mean root still has the same permission, but all others have none, ie can not read write or execute.

+1 
@OP you can also check in the script itself:
```
if [ `whoami` != root ]; then
    echo Please run this script as root or using sudo
    exit
fi

```

---

### Post by acolyte_to_jippity on 2012-11-06
Alright, I'll have to try some of these out tomorrow.  Thanks for the help.  Is it normal that it tells me no such command exists, if i didn't give it exec permissions?

---

### Post by taras.kuzyo on 2012-11-07
Yes it allright. It becomes executable when you add exec permission.

---

### Post by Impavidus on 2012-11-07
```

sudo chown root:root script.sh
sudo chmod 744 script.sh

```
should be enough. No need to make it executable twice.

---

### Post by newb85 on 2012-11-07
If you're going to follow hierarchy standards, /bin isn't the place for a script requiring sudo privileges.  /usr/sbin is probably more appropriate.

---

### Post by Lars Noodén on 2012-11-07
> **newb85 said:**
> If you're going to follow hierarchy standards, /bin isn't the place for a script requiring sudo privileges.  /usr/sbin is probably more appropriate.

Yes,  /sbin/ or even /usr/local/sbin/ would be the [right place to put the script](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html)

---

### Post by acolyte_to_jippity on 2012-11-07
> **Lars Noodén said:**
> Yes,  /sbin/ or even /usr/local/sbin/ would be the [right place to put the script](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html)

so, putting it in /sbin ir /usr/local/sbin will automatically cause it to require sudo o run?

---

### Post by cwsnyder on 2012-11-07
No. The required chown chmod shown in previous postings are still required, it is just that that is the POSIX (suggested) place for you to put your script.

---

### Post by Lars Noodén on 2012-11-07
/sbin/ or, more correctly, /usr/local/sbin/ is simply the right place in the system for you script.  You could also put it in ~/bin/ 

To make it require sudo to run, make it owned by root and give execute permission only to the owner*.

```

sudo chown root:root /usr/local/sbin/myscript
sudo chmod 750 /usr/local/sbin/myscript

```

/usr/local/sbin and co are in the search path so you can run programs in those directories just by typing their name.

* Technically sudo can be used to become any user, not just root.  So you could make up a user just for this script and require users **sudo -u** to that user while running that script.

---

### Post by acolyte_to_jippity on 2012-11-07
> **Lars Noodén said:**
> Yes,  /sbin/ or even /usr/local/sbin/ would be the [right place to put the script]("http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html")


sweet!  i put it in /usr/local/sbin and it worked.  now i just need to figure out how to have it reference a file in a different directory easily.  thanks for all the help guys!

edit: alright. where can i put a second file it needs to use?  should i try putting that file within the same folder (/usr/local/sbin/?)

edit again:  NEVER MIND!!  i figured it out.  thanks again for all the help.

---

