---
title: "Build a script to ping server, email results"
date: 2010-08-12
forum: Programming Talk
---

### Post by CrusaderAD on 2010-08-12
Is there a way to build some kind of script that will ping a server and then e-mail the results?

---

### Post by Bachstelze on 2010-08-12
```
ping -c 4 server.foo.org | mail -s "Ping results" foo@bar.org
```

---

### Post by CrusaderAD on 2010-08-12
> **Bachstelze said:**
> ```
ping -c 4 server.foo.org | mail -s "Ping results" foo@bar.org
```

Thanks for the reply. Is there a way to set it so that it only e-mails if the ping is unresponsive?

---

### Post by Bodsda on 2010-08-12
> **raptormanad said:**
> Thanks for the reply. Is there a way to set it so that it only e-mails if the ping is unresponsive?
 
You would use conditionals based on the output of the program. This should be trivial for any programmer or beginner. I would suggest doing some research yourself. A python script for this would be about 10 lines, but I am sure Bachstelze could do it with a bash one liner :)
 
Bodsda

---

### Post by CrusaderAD on 2010-08-12
Nice. Any recommendations for a python "compiler"?

---

### Post by Bachstelze on 2010-08-12
> **raptormanad said:**
> Thanks for the reply. Is there a way to set it so that it only e-mails if the ping is unresponsive?

```
ping=`ping -c 4 server.foo.org 2>1`; [ $? = 0 ] || echo "$ping" | mail -s "Ping failed!" foo@bar.org
```

2>1 means we also catch stderr, probably useful to have that emailed too since it could give a first clue as to why the server is down.

---

### Post by CrusaderAD on 2010-08-12
> **Bachstelze said:**
> ```
ping=`ping -c 4 server.foo.org 2>1`; [ $? = 0 ] || echo "$ping" | mail -s "Ping failed!" foo@bar.org
```

2>1 means we also catch stderr, probably usefule to have that emailed too since it could give a first clue as to why the server is down.

That's awesome! How do I run it? Is this something that needs to be in a python script?

---

### Post by conundrumx on 2010-08-12
> **raptormanad said:**
> That's awesome! How do I run it? Is this something that needs to be in a python script?

That's all bash, actually.

---

### Post by Bachstelze on 2010-08-12
> **raptormanad said:**
> That's awesome! How do I run it? Is this something that needs to be in a python script?

On the command-line, in a shell script, in a cron job... Wherever you can input commands.

---

### Post by CrusaderAD on 2010-08-12
> **Bachstelze said:**
> On the command-line, in a shell script, in a cron job... Wherever you can input commands.

Very cool. It delivers the message, but I get this in the command line:

```
bash: ping=PING: No such file or directory
Null message body; hope that's ok
```

With nothing in the body of the message.

---

### Post by Bachstelze on 2010-08-12
> **raptormanad said:**
> Very cool. It delivers the message, but I get this in the command line:

```
bash: ping=PING: No such file or directory
Null message body; hope that's ok
```

With nothing in the body of the message.

You're doing it wrong. ;) you probably use ' instead of `.

---

### Post by CrusaderAD on 2010-08-12
Hm, this is what I used, looks like it's using `

```
user@user:~$ bash ping=`ping -c 4 user.com 2>1`; [ $? = 0 ] || echo "$ping" | mail -s "Ping failed" user@user.com
bash: ping=PING: No such file or directory
Null message body; hope that's ok
```

---

### Post by Bachstelze on 2010-08-12
You don't need to put bash before your command. You're running bash already. ;) As you did it, it tries to run a bash script whose flename is given by the second argument.

---

### Post by CrusaderAD on 2010-08-12
Thanks! That worked! What parameters would I have to pass in order to add something to the message of the e-mail on top of the ping results?

---

### Post by Bachstelze on 2010-08-12
You would need something like

```
ping=`ping -c 4 user.com 2>1`; [ $? = 0 ] || echo -e "Here are the ping results:\n\n$ping" | mail -s "Ping failed" user@user.com
```

But at that point, you would probably be better off writing a shell script for it than doing it all on the command line.

---

### Post by CrusaderAD on 2010-08-13
It runs great! Thanks! One thing tho... when I run this as another user:

```
ping=`ping -c 4 server.foo.org 2>1`; [ $? = 0 ] || echo "$ping" | mail -s "Ping failed!" foo@bar.org
```

I get this:

```
-bash: 1: Permission denied
```

If I take out the 2>1 it works fine. Any ideas why?

---

### Post by Bachstelze on 2010-08-13
Sorry, it's 2>&1. Forgot the amp

---

### Post by CrusaderAD on 2010-08-27
I've been using that script, and it works incredibly well. Thanks! Would you happen to know of a way to do something similar, only instead of emailing stuff, just have a script that opens the browser to a certain url?

---

### Post by Bachstelze on 2010-08-27
Replace the echo | mail combo with something like

```
x-www-browser 'http://foo.org'
```

---

### Post by CrusaderAD on 2010-08-27
Nice, it works great in the terminal. When I make a cron script with it, I get this:

```
(x-www-browser:13497): Gtk-WARNING **: cannot open display: 
```

---

### Post by CrusaderAD on 2010-08-27
Would wget be the same as executing the page in the browser?

---

### Post by Bachstelze on 2010-08-27
> **raptormanad said:**
> Would wget be the same as executing the page in the browser?

For some purposes yes, for others no.  What do you want to do?

---

### Post by CrusaderAD on 2010-08-27
I just have scripts on a page that I want to run. They need to be executed via the web server since the technology is web based. Simple stuff, like selecting and updating a database. If wget executed the page and ran these queries, I'd go with that.

---

### Post by Bachstelze on 2010-08-27
It they are PHP or something similar, then yes, wget'ing the page will execute them. If they are JAvaScript, probably not.

---

### Post by CrusaderAD on 2010-08-27
Hm, what do you think about other languages? .net, asp classic, etc.

---

### Post by Bachstelze on 2010-08-27
> **raptormanad said:**
> Hm, what do you think about other languages? .net, asp classic, etc.

I don't know much about them but IIRC they are server-side like PHP, so they should also work.

---

### Post by CrusaderAD on 2010-08-27
I just tested it with asp. Works great! I setup two shell scripts to run with cron. One to hit the page and generate the data. The other to e-mail me the log file afterwards. Good stuff. Thanks again!

---

