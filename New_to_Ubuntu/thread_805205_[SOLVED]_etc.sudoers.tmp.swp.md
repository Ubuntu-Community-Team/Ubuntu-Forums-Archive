---
title: "[SOLVED] /etc/.sudoers.tmp.swp"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Bruce M. on 2008-05-23
Hi Folks

A while ago (using Ubuntu 7.10) I was looking to "kill" the 15 minute grace period for my password when using "sudo" and I posted:

[Use "sudo" password every time!]("http://ubuntuforums.org/showthread.php?t=739243") that lead to:

[lengthen sudo keyring session timeout]("http://ubuntuforums.org/showthread.php?t=179048")

It worked **BUT** I'm now using Xubuntu 8.04 and I tried the command:
```
sudo visudo
```
... so I could add the line:
```
Defaults:bruloo timestamp_timeout=0
```
However I couldn't edit the file and Ctrl-X didn't get me out, now I'm getting an error message:
```
E325: ATTENTION
Found a swap file by the name "/etc/.sudoers.tmp.swp"
          owned by: root   dated: Fri May 23 19:34:22 2008
         file name: /etc/sudoers.tmp
          modified: YES
         user name: root   host name: bruloo
        process ID: 11229
While opening file "/etc/sudoers.tmp"
             dated: Thu May 15 20:02:36 2008

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/sudoers.tmp"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.sudoers.tmp.swp"
    to avoid this message.
"/etc/sudoers.tmp" 23 lines, 470 characters
Press ENTER or type command to continue
```
So I used:
```
vim -r /etc/sudoers.tmp
```
and get:
```
Swap files found:
   Using specified name:
1.    .sudoers.tmp.swn
          owned by: root   dated: Fri May 23 19:43:52 2008
         [cannot be opened]
2.    .sudoers.tmp.swo
          owned by: root   dated: Fri May 23 19:40:27 2008
         [cannot be opened]
3.    .sudoers.tmp.swp
          owned by: root   dated: Fri May 23 19:34:22 2008
         [cannot be opened]
   In directory ~/tmp:
      -- none --
   In directory /var/tmp:
      -- none --
   In directory /tmp:
      -- none --

Enter number of swap file to use (0 to quit): 
```
At which point I hit "0" to quit.
I am at a **[COLOR="Red"]total loss[/COLOR]** here as to what to do.

Can someone please help me.
Have a nice day.
Bruce

---

### Post by bodhi.zazen on 2008-05-23
first, make sure /etc/sudoers exists :

```
cat /etc/sudoers
```

Assuming the file is not empty :

```
sudo rm -f /etc/.sudoers.tmp.swp
```

---

### Post by Bruce M. on 2008-05-24
> **bodhi.zazen said:**
> first, make sure /etc/sudoers exists :

```
cat /etc/sudoers
```

```
bruloo@bruloo:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
bruloo@bruloo:~$
``` 
Contents grabbed with:
```
gksudo mousepad
```
Opened, copied the contents, and closed mousepad. I know it needs to be edited with "visudo"
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```


> **bodhi.zazen said:**
> Assuming the file is not empty :

```
sudo rm -f /etc/.sudoers.tmp.swp
```

OK...
```
bruloo@bruloo:~$ sudo rm -f /etc/.sudoers.tmp.swp
[sudo] password for bruloo: 
bruloo@bruloo:~$ 

```
Done. Now what?
I tried:
```
vim -r /etc/sudoers.tmp
```
again and get only two left:
```
Swap files found:
   Using specified name:
1.    .sudoers.tmp.swn
          owned by: root   dated: Fri May 23 19:43:52 2008
         [cannot be opened]
2.    .sudoers.tmp.swo
          owned by: root   dated: Fri May 23 19:40:27 2008
         [cannot be opened]
   In directory ~/tmp:
      -- none --
   In directory /var/tmp:
      -- none --
   In directory /tmp:
      -- none --

Enter number of swap file to use (0 to quit): 
```
Do I:
```
sudo rm -f /etc/.sudoers.tmp.swn
sudo rm -f /etc/.sudoers.tmp.swo
```
as well? I'm guessing yes, but don't want to go charging in until it's not a guess but a fact.

Thanks for your response.
Looking forward to hearing from you.
Bruce

---

### Post by bodhi.zazen on 2008-05-24
Yes, locate and remove all those files.

---

### Post by sisco311 on 2008-05-24
If you want to edit the sudoers file with nano(like in Gusty):
```
export EDITOR=nano
sudo -E visudo
```To make it permanent, add this lines to the ~/.bashrc:
```
nano ~/.bashrc
```> 
export EDITOR=nano
alias visudo='-E visudo'
~from the bug report:[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369)

---

### Post by drs305 on 2008-05-24
Edited.

You can briefly read about the risks/benefits when editing the sudoers file here:
```
man visudo
```

---

### Post by Bruce M. on 2008-05-24
> **bodhi.zazen said:**
> Yes, locate and remove all those files.

Thank you
Have a nice day.
Bruce

---

### Post by sisco311 on 2008-05-24
> **drs305 said:**
> It should be noted that using export=EDITOR does expose the user to certain risks not encountered when opening with the standard command 'sudo visudo'. Using the latter will open the sudoers file in vi and will not allow saving of the file if errors have been made during editing. This is not the case if the sudoers file is edited via other apps. I initially used the export=Editor command to edit sudoers only when I was making very simple changes to the file that I was sure were correct.

I am the first to admit using vi with no knowledge of the program can be a frustrating experience. Here is one link to using vi: 
[http://staff.washington.edu/rells/R110/](http://staff.washington.edu/rells/R110/)

You can briefly read about the risks/benefits when editing the sudoers file here:
```
man visudo
```

Tested visudo with nano
1.) syntax error:
> [acme] ~$ sudo visudo 
>>> sudoers file: syntax error, line 7 <<<
What now? 
Options are:
  (e)dit sudoers file again
  e(x)it without saving changes to sudoers file
  (Q)uit and save changes to sudoers file (DANGER!)
2.) running multiple instances:
> visudo: /etc/sudoers busy, try again later

---

### Post by drs305 on 2008-05-24
sisco311,

thanks for pointing out that it is nano prevents saving sudoers with errors.

still trying to think of a 11-digit prime number ... ;-)

---

### Post by Bruce M. on 2008-05-24
I've cleaned up my files, and because of a very interesting conversation going on here about this I've changed the Status: Solved back to unsolved, as I still have to make my changes.

Watching with great interest.

Thanks to all concerned.
Bruce

---

### Post by drs305 on 2008-05-24
Further: in ubuntu, sudoers is edited with nano (and invoked with the 'sudo visudo' command), not as it is in some other distributions, with vi. So nano via visudo is the method which will protect the integrity of the sudoers file.  I have gone back and edited my previous posts in this thread so as not to confuse anyone. Thanks.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by bodhi.zazen on 2008-05-24
Just to be clear, it is the command visudo, and not the editor, that gives the "protection" when editing /etc/sudoers

You may use any editor, vi , vim, nano, gedit, kate , emacs with visudo

You may directly edit /etc/sudoers (with any editor), however, if you do not use visudo you do not get the protection of syntax checking and locking the file (to prevent multipe edits).

If you break sudo, you will have to fix it from the recovery mode. 

Before you edit system files, never a bad idea to back them up :

```
sudo cp /etc/sudoers /etc/sudoers.bak
```

---

### Post by Bruce M. on 2008-05-25
> **bodhi.zazen said:**
> Just to be clear, it is the command visudo, and not the editor, that gives the "protection" when editing /etc/sudoers

You may use any editor, vi , vim, nano, gedit, kate , emacs with visudo

You may directly edit /etc/sudoers (with any editor), however, if you do not use visudo you do not get the protection of syntax checking and locking the file (to prevent multipe edits).

If you break sudo, you will have to fix it from the recovery mode. 

Before you edit system files, never a bad idea to back them up :

```
sudo cp /etc/sudoers /etc/sudoers.bak
```

Agreed, a backup is a good idea, and always done here.

So if I read what you wrote correctly, I can use:
```
sudo cp /etc/sudoers /etc/sudoers.orig && gksudo gedit visudo
```
to edit the file. I prefer .orig to .bak, for the first edit, subsequent edits of a file get bak1, bak2 etc. to give a history of the files.

Have a nice day.
Bruce

---

### Post by bodhi.zazen on 2008-05-25
Almost, you need to set the editor by adding the appropriate lines to ~/.bashrc. For gedit add :

```

export EDITOR=nano
```

Then you can "```
gksu -E visudo
```

visudo is a command , not a file

---

### Post by Bruce M. on 2008-05-25
Hi bodhi.zazen,

Like my sig says: *Until I know what I'm doing, I'll ask questions.*, sorry if its a pain but it's the only way I know of learning this stuff. :)

> **bodhi.zazen said:**
> Almost, you need to set the editor by adding the appropriate lines to ~/.bashrc. For gedit add :

```
export EDITOR=nano
```

Do you mean:
```
export EDITOR=gedit
```
by chance?

> **bodhi.zazen said:**
> Then you can "```
gksu -E visudo
```

visudo is a command , not a file

Yea read that earlier about visudo, which beings my next question.

Why gksu and not gksudo?

To date I have never used "su" I know what it is and to be honest, I'm still green enough behind the ears to be a bit timid of that command. Even though I check **man pages** constantly.

---

### Post by sisco311 on 2008-05-25
> **Bruce M. said:**
> Hi bodhi.zazen,

Like my sig says: *Until I know what I'm doing, I'll ask questions.*, sorry if its a pain but it's the only way I know of learning this stuff. :)



Do you mean:
```
export EDITOR=gedit
```by chance?



Yea read that earlier about visudo, which beings my next question.

Why gksu and not gksudo?

To date I have never used "su" I know what it is and to be honest, I'm still green enough behind the ears to be a bit timid of that command. Even though I check **man pages** constantly.

gksudo is a symbolic link to gksu
And don't use GUI editors with visudo. When you try to save the file with syntax error the (e)dit option opens an empty file. nano and vi are more secure.

---

### Post by Bruce M. on 2008-05-25
> **sisco311 said:**
> gksudo is a symbolic link to gksu
And don't use GUI editors with visudo. When you try to save the file with syntax error the (e)dit option opens an empty file. nano and vi are more secure.

RE: Symbolic link, thanks, I didn't know that. {some of the green got lighter} :)

See, now that I didn't know, ok, I'll set it up as nano then, I'm more comfortable with that than vi.

Thanks for you help everyone.
Time to mark this Solved again

Have a GREAT Day!
Bruce

---

### Post by Brannon May on 2010-08-19
Hello all. I have gotten myself into trouble with my Mac and I am looking for some help. Googled a line out of term and found this site. I going through a tutorial on Rixstep and got into a situation that is not addressed on the site. 

It was a step by step process and I still managed to screw it up. It concerns "sudo visudo". Below is the instructions:

You have to run visudo. From a command line. You must do this from an administrator account.

Go to a command prompt (Terminal.app) and type in 'sudo visudo'. You'll be prompted for your passphrase. Give it.

Use arrow down to get to the line that says '# Defaults specification'. Hit 'o' on your keyboard.

Type in 'Defaults tty_tickets'. Hit Enter. Type in 'Defaults:ALL timestamp_timeout=0'. Hit <Esc>.

[COLOR="Blue"]You should now have this.
# Defaults specification
Defaults tty_tickets
Defaults:ALL timestamp_timeout=0
Type ':q!' if you make a mistake and want to exit without saving changes.
Type ':w' followed by Enter then ':q' followed by Enter to save your changes.[/COLOR]

I managed to screw that up on step 3 and tried to back out of this using abort. So now when I go back to this this is what I get. 

[COLOR="Blue"]E325: ATTENTION
Found a swap file by the name "/etc/.sudoers.tmp.swp"
          owned by: root   dated: Fri Aug 13 19:21:39 2010
         file name: /private/etc/sudoers.tmp
          modified: YES
         user name: root   host name: brannon-mays-macbook-pro.local
        process ID: 345
While opening file "/etc/sudoers.tmp"
             dated: Fri Aug 13 19:15:31 2010

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/sudoers.tmp"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.sudoers.tmp.swp"
    to avoid this message.

Swap file "/etc/.sudoers.tmp.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort: 
-- More --[/COLOR]

I dont want to choose any of these options until I can get someone that understands what is going on here to help me out. 

I am using a Macbook Pro V. 10.6.4. 

Any help would be much appreciated.

---

### Post by bodhi.zazen on 2010-08-19
You probably want to edit anyways.

---

