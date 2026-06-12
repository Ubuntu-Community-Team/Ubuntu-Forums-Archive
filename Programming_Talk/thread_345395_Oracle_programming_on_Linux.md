---
title: "Oracle programming on Linux"
date: 2007-01-24
forum: Programming Talk
---

### Post by Hendrixski on 2007-01-24
Which IDE would you recommend for PL/SQL programming in LINUX?  I've mostly used TOAD on Windows before, and I heard that TOra is kind of similar.  Has anyone used it, would you recommend it?  How about JDeveloper?  Any hints?

---

### Post by marianom on 2007-01-24
I'm using Oracle Sql Developer and sqlplus. 
You have TOra en the repos but they have support just for postgre. If you want support for Oracle you need to compile it from source. In my case and after several tries, I got stuck in a little error and couldn't continue.

---

### Post by Hendrixski on 2007-01-24
Yeah, seems like I ran into similar problems with TOra.  It's really crappy that the Ubuntu repo's only have a PostGreSQL version of Tora.   I installed the .deb from their site on sourceforge and haven't been able to get it to connect.  I just switched back to Windows for now to program from TOAD for now.

SQL Developer looks like an interesting alternative.  I just googled it and saw the description on Oracle's website, Linux friendly is always a plus.  I'll give that a try tonight after work.  For now I just want to have something to show for the hours that I'm billing the customer.

Can I get SQL Developer to read a TNS names file correctly or will I have to enter everything by hand?

---

### Post by marianom on 2007-01-24
You have a TNS option when creating connections and you just fill in with the name of the desired db.

I must say it has some problems and it's a little frustrating sometimes. I personally just use it for  large selects. I develop my packages and types with vim and compile them in sqlplus. 
Hope it fits your needs.

---

### Post by KeighleHawk on 2007-03-20
So do you have any configuration suggestions for Oracle SQL Developer?  I am having trouble getting SQL*Plus to start from with in the IDE.  I have a kludged script now, but it still seems hackish.  I just installed it a week or two ago so am still digging through the documentation.  I also saw reference to plugins for SQL Developer but have not yet found said plugi-ins...

Otherwise, I am currently toying with:

Oracle SQL Developer
TOra
SQuirreL SQL Client

Just trying to see what does the best with the least pain...

---

### Post by marianom on 2007-03-20
To set sql*plus from sql developer:
1- go to Tools->Preferences and select SQL*Plus. 
2- fill the input box with the information regarding your sqlplus executable. For example mine is:
*/usr/bin/xterm -e* _/opt/oracle/product/10.2.0/client_1/bin_
In italic what it's a must, in bold the route to my sqlplus executable.
3- In your connection properties, click in "Save Password" (risky, I don't like it) and be sure the connection type is "Basic".
4- With your application focused on the left panel, select the Tools-> Sql plus and it should launch without problems.
More [here]("http://forums.oracle.com/forums/thread.jspa?messageID=1249286&#1249286").
If you ask me, I don't like how you invoke it so I use it directly form my terminal.

As you saw in the other thread I too have tora running now so I'm using it: I guess I'm leaving sql developer as a second option in case of need.

---

### Post by KeighleHawk on 2007-03-20
okay, now that is just weird.  It is working whether or not I have the password saved or not.  Also, either way, it makes me enter my password at the SQL*Plus login (seems inconsistent).  

I know now why it did not work when I first tried it because I had it set to use TNS instead of Basic.  As it turns out, I must have redone it using Basic without realizing it, but by then,  I was "troubleshooting" it and didn't realize it was working.

As another aside, I'm not sure if it matters, I added my Oracle Environment Variables to my .bash_profile.  Originally, I had them set only in my .bashrc.  Apparently, I don't actually understand the distcintion between the two because they may not be acting the way I thought they should...

---

