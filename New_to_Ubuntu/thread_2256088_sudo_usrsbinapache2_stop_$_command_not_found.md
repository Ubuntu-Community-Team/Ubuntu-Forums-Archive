---
title: "sudo /usr/sbin/apache2 stop $: command not found"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by gregory10 on 2014-12-09
Stopping starting apache2 is not working
the installation worked and get the test page when I put [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) in the brower
It is working OK. I want to be able to turn it off as I am working on setting it up for development work on my new kubuntu instalation which I use for other things as well.

thanks for any help I do apreciate it and only tend to come here and ask at the forums after exhausting my own research
tried using sudo and it doesn't seem to work and used what was on the ubuntu wiki page 
as well as what I could find on the README.Debian.gz and anything else I could find.
In the end found that they were only saying what path to use in the command not the whole command
this the result of using what is said on the ubunbtu wiki
[h=2]Run, Stop, Test, And Restart Apache[/h] Use the following command to run Apache :  
$ sudo /usr/sbin/apache2ctl stop
gregory@gregory-Satellite-L500:~$ sudo /usr/sbin/apache2ctl stop
[sudo] password for gregory: 
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. 
Set the 'ServerName' directive globally to suppress this message
gregory@gregory-Satellite-L500:~$ 

this is from the the startup page of the instalation
apache2 needs to be                            started/stopped with /etc/init.d/apache2 or apache2ctl.                            [B]
Calling /usr/bin/apache2 directly will not work[/B] with the                            default configuration.                         
So I did that and...
gregory@gregory-Satellite-L500:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server apache2                                                   * 
gregory@gregory-Satellite-L500:~$ 

the trouble is when I put this below into the browser the default page comes up indicating the apache2 is still running ????
[http://localhost/](http://localhost/) and hit enter and the default page shows in my browser

thanks again for any clarity you can give me on this
G

---

### Post by sandyd on 2014-12-10
Hi, can you run
```

ps aux | grep apache
```
after attempting to stop apache?

Thanks!

---

### Post by gregory10 on 2014-12-10
@sandyd
thanks for the reply

I tested that command and this is the result:
gregory@gregory-Satellite-L500:~$ ps aux | grep apache
root      XXXXXXXXXXXXXXXXXXXX?        Ss   18:42   0:00 /usr/sbin/apache2 -k start
www-data   XXXXXXXXXXXXXXXXXX?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
gregory   XXXXXXXXXXXXXXXXXX pts/1    S+   20:27   0:00 grep --color=auto apache
gregory@gregory-Satellite-L500:~$ 

I don't know what this means but that's what resulted in the terminal
can you tell me what this means:
```
ps aux | grep apache
```

Could you please tell me what the code means and also the result of the code read out in the terminal?
thanks
G

---

### Post by gregory10 on 2014-12-10
@sandyd

Ahhh sorry suddenly realized you wanted me to stop it first
so tried again and got the result below

gregory@gregory-Satellite-L500:~$ sudo /etc/init.d/apache2 stop
[sudo] password for gregory: 
 * Stopping web server apache2                                                    * 
gregory@gregory-Satellite-L500:~$ ps aux | grep apache
gregory   3052  0.0  0.0  11748   908 pts/1    S+   20:52   0:00 grep --color=auto apache
gregory@gregory-Satellite-L500:~$ 

so what does this mean?
thanks
G

---

### Post by Lars Noodén on 2014-12-10
> **gregory10 said:**
>  ps aux | grep apache

The program [ps](http://manpages.ubuntu.com/manpages/trusty/en/man1/ps.1posix.html) list the status of processes running on your system.  It takes two styles of parameters, with a dash and without.  Without a dash, the **a** shows processes from all users, not just your own, the **x** lists even processes that are not running in a terminal/pseudo terminal.  The **u** means a particular format for the output.  The output has the following columns: User ,  Process ID #, %CPU used, %Memory used,   virtual memory size, non-swapped physical memory, terminal or pseudoterminal, starting time, duration, and actual command running.  See use of the option **o** and the section "standard format specifiers" in the manual page for more ideas about how to format the output.

The pipe  |  sends the output of the one program into the next program as input.  You can chain as many programs together as you need, but in this case only ps and grep are being chained.  

Lastly, [grep](http://manpages.ubuntu.com/manpages/trusty/en/man1/grep.1.html) prints lines matching a pattern.  In this case selecting from the output provided by ps.  You could substitute other programs as well.  [sed](http://manpages.ubuntu.com/manpages/trusty/en/man1/sed.1posix.html) is another option which is fancier and can allow the first line to be printed as well, preserving the headings from ps:

```

ps aux | sed '1p;/apache/!d'

```

Mostly people remember that there are programs that can do such things and then look up how as needed.  Otherwise it would be too much to remember.

---

### Post by gregory10 on 2014-12-10
OK @Lars
am I to understand from the results one before turning apache2 off and the other after 

**before:**
gregory@gregory-Satellite-L500:~$ ps aux | grep apache
root      XXXXXXXXXXXXXXXXXXXX?        Ss   18:42   0:00 /usr/sbin/apache2 -k start
www-data   XXXXXXXXXXXXXXXXXX?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
www-data  XXXXXXXXXXXXXXXXXX ?        S    18:42   0:00 /usr/sbin/apache2 -k start
gregory   XXXXXXXXXXXXXXXXXX pts/1    S+   20:27   0:00 grep --color=auto apache
gregory@gregory-Satellite-L500:~$ 

**and after:**
gregory@gregory-Satellite-L500:~$ ps aux | grep apache
gregory   3052  0.0  0.0  11748   908 pts/1    S+   20:52   0:00 grep --color=auto apache
gregory@gregory-Satellite-L500:~$ 

**because the root and www-date are showing **
root      XXXXXXXXXXXXXXXXXXXX?        Ss   18:42   0:00 /usr/sbin/apache2 -k start
www-data   XXXXXXXXXXXXXXXXXX?        S    18:42   0:00 /usr/sbin/apache2 -k start
**as compared to the second time when only myself is showing:**
gregory@gregory-Satellite-L500:~$ ps aux | grep apache
gregory   3052  0.0  0.0  11748   908 pts/1    S+   20:52   0:00 grep --color=auto apache

this must mean that apache2 is in fact stopped. Then if that is true I am still wondering why I can 
get the index page of localhost to come into the browser? 
that is puzzling me. Why is that? Is it a default thing setup for when the apache2 server is switched off?

---

### Post by steeldriver on 2014-12-10
is your browser perhaps caching the page?

---

### Post by gregory10 on 2014-12-10
@steeldriver
Yes looks like it
this time since starting the laptop I am working on I have not called my browser to search for the site address: http"//localhost
I'm thinking that is the case and it caches the page content.
thanks for that all who helped looks like it solved. thanks you so much for this.

---

