---
title: "Taking command ... or trying to ..."
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Langstracht on 2008-09-18
I have been using cron to start kwordquiz.

I would now like to use it to start up various combinations of mode, session type and file names at various times.  However I cannot get anything to work.

Can someone suggest either why cron is not doing this or why a command such as:

kwordquiz -m 5 -g fc Francais.kvtml 

does not work.

Thanks in advance.

---

### Post by jbrown96 on 2008-09-18
I don't know much about cron, but I think the problem is with the file. You most likely need to have the entire file path. like /home/user/Documents/Francais.kvtml Also be aware that linux is case sensitive

---

### Post by KIAaze on 2008-09-18
cron always sends error messages to the "system mail".

Just look at your "system mail" using the following command:
```
mail
```
To read a message, just type it's number + enter.

If you don't have the mail program, you can install it via:
```
sudo apt-get install mailx
```

Also, does the command you gave work when you run it in a terminal?

It would also help if you posted the contents of your crontab file here:
```
crontab -l
```

---

### Post by Langstracht on 2008-09-18
It could well be the file name.  Sorry to say I don't know.  That said I have tried every path I can think of ... to no avail.

mail is apparently not installed, I'll see if I can do something about that.

No, I've discovered, the command doesn't work in terminal either.  Which I guess is not a surprise.

Finally the cron contains:

0 09 * * * export DISPLAY=:0 && kwordquiz -m 5 -g fc home/Directory/Francais.kvtml

Perhaps if someone could tell me how to find out what path cron needs.  I know where Francais.kvtml is but it's a bit of a mystery where cron is ... and how it would get to Francais.

---

### Post by KIAaze on 2008-09-18
> **Langstracht said:**
> It could well be the file name.  Sorry to say I don't know.  That said I have tried every path I can think of ... to no avail.

...

Perhaps if someone could tell me how to find out what path cron needs.  I know where Francais.kvtml is but it's a bit of a mystery where cron is ... and how it would get to Francais.

Mmh, why don't you use the absolute path, i.e. /home/.../Francais.kvtml?

cron always runs the jobs from the users home directory (/root if it's root's crontab).

It's also possible to define the PATH and HOME variables in the crontab file.

More details:
> cron invokes the command from the user's HOME directory with the shell, (/usr/bin/sh).
cron supplies a default environment for every shell, defining:
HOME=user's-home-directory
LOGNAME=user's-login-id
PATH=/usr/bin:/usr/sbin:.
SHELL=/usr/bin/sh

Users who desire to have their .profile executed must explicitly do so in the crontab entry or in a script called by the entry.
[http://www.adminschoice.com/docs/crontab.htm#Environment](http://www.adminschoice.com/docs/crontab.htm#Environment)

> In crontab there can be PATH definition. In Debian 1.3 there is the following default line in the beginning of /etc/crontab:

    PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

[http://tldp.org/HOWTO/Path-10.html](http://tldp.org/HOWTO/Path-10.html)

> Several environment variables are set up automatically by the cron(8) daemon. SHELL is set to /bin/sh, and LOGNAME and HOME are set from the /etc/passwd line of the crontab's owner. PATH is set to "/usr/bin:/bin". HOME, SHELL, and PATH may be overridden by settings in the crontab; LOGNAME may not.

(Another note: the LOGNAME variable is sometimes called USER on BSD systems... on these systems, USER will be set also.)

In addition to LOGNAME, HOME, and SHELL, cron(8) will look at MAILTO if it has any reason to send mail as a result of running commands in ``this'' crontab. If MAILTO is defined (and non-empty), mail is sent to the user so named. If MAILTO is defined but empty (MAILTO=""), no mail will be sent. Otherwise mail is sent to the owner of the crontab. 
[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/crontab.5.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/crontab.5.gz)

---

### Post by Langstracht on 2008-09-18
Sorry ... but isn't the quoted command

0 09 * * * export DISPLAY=:0 && kwordquiz -m 5 -g fc home/Directory/Francais.kvtml

not doing what you said? i.e. giving a path from the home directory?

Maybe, to be sure this is a problem particular to me, someone would be kind enough to check/confirm that kwordquiz will in fact react to the options I have been trying to use ...

---

### Post by KIAaze on 2008-09-18
> **Langstracht said:**
> 
0 09 * * * export DISPLAY=:0 && kwordquiz -m 5 -g fc **[SIZE="4"]/[/SIZE]**home/Directory/Francais.kvtml


You forgot a slash I believe. ;)

I also just made an interesting discovery: You can get cron errors mailed to any e-mail address by doing the following:

```
MAILTO=me@gmail.com
# m h  dom mon dow   command
* * * * * command

```
cf: [http://www.clickmojo.com/code/cron-tutorial.html](http://www.clickmojo.com/code/cron-tutorial.html)

Of course it's easier to get it mailed to your own PC (default MAILTO) and access it via "mail".

Maybe I'll have to install kwordquiz to see what your problem is...

---

### Post by jbrown96 on 2008-09-18
i think that you're passing invalid options to kwordquiz. You can check out the man page for more info with ```
man kwordquiz
```
The problem seems to be -g fc. There is no option listed as that. I think you want flash cards, so the proper flag would be -g flash. Here's the realvent info: >        Below are the  kwordquiz-specific  options.   For  a  full  summary  of
       options, run kwordquiz --help.

       -m, --mode number
              Specify  the  order  and direction in which questions are asked.
              The number argument must be 1, 2, 3, 4 or  5  (corresponding  to
              the five entries in the Mode menu).

       -g, --goto session
              Begin  a  quiz  immediately.   The session argument may be flash
              (for a flashcard quiz), mc (for a multiple choice  quiz)  or  qa
              (for a question and answer quiz).


---

### Post by KIAaze on 2008-09-18
jbrown is right. It should be "flash" instead of "fc".

However this worked for me:
```
[70][~]$  crontab -l
# m h  dom mon dow   command
* * * * * export DISPLAY=:0 && kwordquiz -m 5 -g fc /usr/share/kde4/apps/kwordquiz/examples/example.kvtml 
```
Since it doesn't understand "fc", it just opens it in editor mode.

But if you want flash cards, it must be:
```
[70][~]$  crontab -l
# m h  dom mon dow   command
* * * * * export DISPLAY=:0 && kwordquiz -m 5 -g flash /usr/share/kde4/apps/kwordquiz/examples/example.kvtml 
```

---

### Post by Langstracht on 2008-09-18
Between my apparent dyslexia and Torvald's insistence on syntactically demanding code ...

Thank you all so much.  The fc => flash ... AND the "/" did the trick.

Result, one very happy camper.  Thanks to all!

---

