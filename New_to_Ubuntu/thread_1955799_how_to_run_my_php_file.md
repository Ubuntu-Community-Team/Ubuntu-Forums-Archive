---
title: "how to run my php file"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by jimeast on 2012-04-10
[SIZE=2]I installed lampp, I started apache, I found the htdocs folder, I created a simple php file but I don't know how to run it.

this is what I tried:
dad@dad-OEM:~$  /opt/lampp/htdocs/info.php
/opt/lampp/htdocs/info.php: line 1: ?php: No such file or directory
/opt/lampp/htdocs/info.php: line 2: syntax error near unexpected token `;'
/opt/lampp/htdocs/info.php: line 2: ` phpinfo(); '
dad@dad-OEM:~$ 

The code looks like this:
```
<?php
 phpinfo(); 
?>
```I know this looks like a php question and this is a ubuntu forum but this would work in Windows, I don't think it's a php syntax error so I'm confused.  I guess a matter of not knowing how to execute code from a terminal.[/SIZE]

---

### Post by GWBouge on 2012-04-10
Make sure you have the command-line interpreter installed:

```
sudo apt-get install php5-cli
```

And call it with php5:

```
php5 /opt/lampp/htdocs/info.php
```

If you're just using the interpreter for testing and such, you don't need apache running, or even installed (I don't have it installed on my machine).  Apache is just the web host.

---

### Post by jimeast on 2012-04-10
[SIZE=3]Thanks!! 
Now I can use umbuntu to help me in my php and mySql studies.
info.php ran though the function phpinfo() only gave me licensing info instead of the long list of php configuration info I was expecting but that's a question for the xampp forum.[/SIZE]

---

### Post by SeijiSensei on 2012-04-10
> **jimeast said:**
> [SIZE=3]Thanks!! 
Now I can use umbuntu to help me in my php and mySql studies.
info.php ran though the function phpinfo() only gave me licensing info instead of the long list of php configuration info I was expecting but that's a question for the xampp forum.[/SIZE]

That's not true for me.  I just ran

```
echo '<? phpinfo() ?>' | php
```

and got back the usual extensive report about the various installed modules.  There won't be any web server information, of course, like _SERVER['REMOTE_HOST'], but you should see things like _SERVER['HOSTNAME'].

This is on a server running CentOS 6, not Ubuntu.  I wouldn't think they'd be all that different, but you never know.

---

### Post by CharlesA on 2012-04-10
Seiji, that worked for me on 10.04

---

### Post by jimeast on 2012-04-11
[SIZE=2]It turns I actually did get the full listing but my terminal window was small and it loaded so fast I didn't notice I was just looking at the last few lines of it.  SeijiSensei thanks I didn't know you could just run php commands directly from the command line like that.[/SIZE]

---

