---
title: "Equivalent of Win32 LogonUser() to impersonate another user?"
date: 2008-08-11
forum: Programming Talk
---

### Post by scooter77 on 2008-08-11
Hi,

I'm a Windows programmer who's fairly new to Linux. I was wondering if there's an equivalent of the Windows LogonUser API in Linux? Something that allows a program to impersonate another user, given that user's username and password. I'm aware of the setuid() function, but as I understand the program needs to run as root to use that. What if it's not running as root, but essentially just wants to do "su someuser", but in code? Is there a way to do this or is it intentionally not supported in Linux?

Thanks in advance for any help!

---

### Post by Titan8990 on 2008-08-11
I believe this is intentionally not supported to force programs that do things that require root privileges to be ran as root or sudoed.

---

### Post by HermanAB on 2008-08-11
Have a look at 'kdesu' and 'gtksu'.

Cheers,

Herman

---

### Post by Mister.Vash on 2008-08-11
Might I query on what you are trying to do?  Depending on what it is, you might be able to setup something based on a newly created group or something of that sort so that it doesn't have to be programmed in.  And if does turn out to be something that has to be programmed in, you could check over in the Programming Talk section for help [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Joeb454 on 2008-08-12
Moved to Programming Talk

---

### Post by scooter77 on 2008-08-12
I've had a look at kdesudo (couldn't find the source for kdesu), but that doesn't really help. I'd like to have my program impersonate another user account without any user interaction and without having to be run setuid root. Basically, exactly what LogonUser accomplishes in Windows.

Yes, there are probably other ways around it, but I'd still like to know if this particular scenario is possible in Linux.

---

### Post by cszikszoy on 2008-08-12
What you want is

```

sudo -u <some_user> <program>

```

That will allow you to run the program as "some_user".

---

### Post by scooter77 on 2008-08-13
Thanks, cziksoy, but as far as I can see sudo like su won't allow stdin to be redirected, so it would require user interaction to enter the password.

---

### Post by Tuna-Fish on 2008-08-13
[quote= man sudo]
       -S  The -S (stdin) option causes sudo to read the password from the
           standard input instead of the terminal device.
[/quote] 
-tuna

---

### Post by cszikszoy on 2008-08-13
> **scooter77 said:**
> Thanks, cziksoy, but as far as I can see sudo like su won't allow stdin to be redirected, so it would require user interaction to enter the password.

Technically, yes.  But there are ways to get around that.  You can edit the sudoers file to determine which users require passwords (and what commands they can run) with sudo.

For example, editing the /etc/sudoers file, and adding this line for a given user
  ```
user ALL=(root) NOPASSWD: ALL
```


will allow them to run all commands using sudo without issuing a password.


I don't really suggest THAT approach, but what you can do, is create command aliases in your sudoers file.


For example, lets say the program you want to run, as another user without a password is /path/to/bin


In your sudoers file, put these lines:
```
Cmnd_Alias     CMD = /path/to/bin
<user>         ALL = NOPASSWD: CMD
``` This will allow <user> to only run the command in the cmnd_alias with sudo without a password.

For more information check the manpages for sudoers.

---

### Post by happysmileman on 2008-08-13
To the OP, I'd advise you to think about whether this is actually needed. There's a good chance you could achieve this better and with less hassle using groups instead of switching users.

---

### Post by scooter77 on 2008-08-14
> **Tuna-Fish said:**
> -tuna

Oops! How did I miss that? Thanks!

I wonder, though, why sudo can read the password from stdin, but su refuses to? With sudo you still have to modify the sudoers file, whereas with su you just need to know the password, which 
would be perfect if it allowed input to be redirected. Oh well.

Thanks to everyone who replied!

---

### Post by JAMJR on 2008-08-22
The call to setuid(*uid*) can be used in code without having to require that the user be root so long as the executable is owned by root and has the user s-bit is set.

As yourself (not root, but a normal user!!!) create the following main.c:

*----- code start for main.c*
[B]#include <unistd.h>
#include <errno.h>
#include <stdio.h>

int main()
{
[INDENT]int i = setuid(502);[/INDENT]
[INDENT]    /*
       assumes you have a user with uid = 502. 
       for this example – change to meet your need.
       this is not your uid, it should be the
       uid of someone else.
     */[/INDENT]
[INDENT]    if( i != 0)
    {
        [INDENT]int err = errno;
        fprintf(stderr, "setuid returned %d  on errno %d\n", i, err);[/INDENT]
    } else
    {
       [INDENT] /*
          anything you do from this point will be
          done as user with uid 502.
         */
        /*
           We can show results of setuid() by
           making a system call to run the command /usr/bin/id
        */
        system("/usr/bin/id");
        /*
           You don't need to call system, it can be whatever
           code you want.  The system call is only made to
           illustrate the results.
         */[/INDENT]
        }[/INDENT]
}[/B]
*---- code end*

Now compile 

**% cc main.c**
This will produce a.out

become root with su or sudo:
**% su**

The order of the next commands is critical:
[INDENT]*make the exe owned by root*[/INDENT]
**# chown root a.out **
[INDENT]*make permissions 755, so only root can modify.*[/INDENT]
**# chmod 755 a.out**          
[INDENT]*set the user s-bit on the exe*[/INDENT]
**# chmod u+s a.out **            
[INDENT]*quit the su so you become a normal user again*[/INDENT]
**# exit**                                  

Show a long list to see the results of the above command:
**% ls -l**
[B]-rw[COLOR="Blue"]s[/COLOR]r-xr-x 1 [COLOR="Blue"]root[/COLOR] users 5177 Aug 20 20:08 a.out
[/B]
Now run the command “id” , it should be in your path, Linux has it at /usr/bin/id:

**% id**

Examine the output to see your uid.

**% ./a.out**

Examine the output and it should show the changed uid assuming the setuid call did not error.

If you run the id command again, it should show your uid.

**% id**

---

