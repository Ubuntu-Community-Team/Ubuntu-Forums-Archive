---
title: "i need help changing my shell =("
date: 2008-07-16
forum: New to Ubuntu
---

### Post by kulote on 2008-07-16
Hi... so i have been trying to install the program called Byond and i get to install it but in the process i need to type this code .../bin/byondsetup
and it says if i get a error i need to change my shell so dreamdeamon and the other programs work ...

The thing is that i dont know how to change my shell.

Please replay me with a solution..

this is what the makefile says: 

"If it generates errors, your shell is not compatible with 'sh', so you will"
	@echo "have to edit byondsetup and make it work with your shell.  If the script works, you should be able to run DreamDaemon."

and i dont have any idea of how to fix this =( 

TYVM and i hope u come up with a solution =D

---

### Post by mcduck on 2008-07-17
I doubt that the shell would be your problem. THe default shell in Ubuntu is definitely compatible with "sh".

Could you give more details of what you are exactly trying to do (the commands you run, and the error you get)?

---

### Post by nowshining on 2008-07-17
cd into the folder u untared

issue:
```

sh /bin/byondsetup

if u need root access to intall it

sudo sh /bin/byondsetup
```

---

### Post by scorp123 on 2008-07-17
> **mcduck said:**
> THe default shell in Ubuntu is definitely compatible with "sh". Not always. I have seen problems too and I personally prefer to get rid of "dash" (Ubuntu's default shell) and use the real "bash" even though it's a lot bigger and may consume more resources, but "bash" definitely works better than "dash".

How to get rid of "dash" without breaking anything? Please see my next posting to OP.

---

### Post by scorp123 on 2008-07-17
> **kulote said:**
> and it says if i get a error i need to change my shell so dreamdeamon and the other programs work ... The problem here is "dash", Ubuntu's default shell. I personally have had problems too and I prefer to use "bash" which should work way better.

So here is how to get rid of "dash", reinstate "bash" as default shell:

1. Open a terminal
2. type these commands:
```
sudo dpkg-reconfigure dash
``` ... if it asks for a password: That's your password. And the password input IS NOT echoed back, so there will be no stars, no question marks or anything, just empty black space. Just type in your password and hit the "ENTER" key.

3. A dialogue will show:
```
The default /bin/sh shell on Debian and Debian-based systems is bash.
However, since the default shell is required to be POSIX-compliant, any shell that
conforms to POSIX, such as dash, can serve as /bin/sh.
You may wish to do this because dash is faster and smaller than bash.

Install dash as /bin/sh?

<Yes>                                               <No> 
``` Highlight "No" with your cursor keys and hit the 'ENTER' key on your keyboard.

4. Voila, you're done.

I suggest you open now a new terminal and try to run your program from there again. Only newly started sessions will reflect the shell change. If you really really really want to be sure everything is changed you might also reboot ... but it's not really necessary but it can be done too if you want.

Hope this helped.

---

### Post by nowshining on 2008-07-17
once u do that - can u move dash without any side-effects?

---

### Post by mcduck on 2008-07-17
> **scorp123 said:**
> Not always. I have seen problems too and I personally prefer to get rid of "dash" (Ubuntu's default shell) and use the real "bash" even though it's a lot bigger and may consume more resources, but "bash" definitely works better than "dash".

How to get rid of "dash" without breaking anything? Please see my next posting to OP.

It's compatible with sh, although not fully compatible with bash.

The instructions required sh-compatible shell..

Anyway, the default login shell for users is still bash.

---

### Post by mcduck on 2008-07-17
> **nowshining said:**
> cd into the folder u untared

issue:
```

sh /bin/byondsetup

if u need root access to intall it

sudo sh /bin/byondsetup
```

Yes, those are the instructions. Could you please post the error you get when trying to do that?

Anyway, if the instrctions are wrong, and being compatible with sh is not enough and the program needs bash instead just run it with "./path/to/yourfile" or "bash /path/to/yourfile".

Replacing dash with bash will slow your system down for no reason at all. Like I already mentioned, the user shell is still Bash.

---

### Post by scorp123 on 2008-07-17
> **nowshining said:**
> once u do that - can u move dash without any side-effects? Nope. There are some hard-to-explain and IMHO stupid dependencies between "dash" and other packages. If you remove "dash" (e.g. 'sudo apt-get remove dash') then there is a chance that other packages might be accidentally removed as well. If I try that here I get this: ```
 > sudo apt-get remove dash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dash ubuntu-minimal
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  dash
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 262kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] no
Abort.
```

So instead of removing "dash" and risking unwanted side effects I prefer to just disable it and use "bash" as default shell.

---

### Post by scorp123 on 2008-07-17
> **mcduck said:**
> Anyway, the default login shell for users is still bash. Not true. Per default (e.g. after a Ubuntu installation) "dash" is the default shell. Even if **/etc/passwd** says that one's shell is **/bin/bash** it's "dash" that's being loaded because /bin/bash is just a symbolic link to "dash" ..... Unless you change it via '**sudo dpkg-reconfigure dash**' after which the symbolic link is permanently removed.

If you remove the link manually then everytime there is an update it will automagically be regenerated ... which is highly annoying (been there, done that). So to remove the link cleanly and keep it removed you have to use above command.

---

### Post by ibuclaw on 2008-07-17
> **scorp123 said:**
> Not true. Per default (e.g. after a Ubuntu installation) "dash" is the default shell. Even if **/etc/passwd** says that one's shell is **/bin/bash** it's "dash" that's being loaded because /bin/bash is just a symbolic link to "dash" ..... Unless you change it via '**sudo dpkg-reconfigure dash**' after which the symbolic link is permanently removed.

If you remove the link manually then everytime there is an update it will automagically be regenerated ... which is highly annoying (been there, done that). So to remove the link cleanly and keep it removed you have to use above command.

Where do you get your information from?

[PHP]
dpkg -l | grep bash
 ii  bash              3.2-0ubuntu18            The GNU Bourne Again SHell
 ii  bash-builtins     3.2-0ubuntu18            Bash loadable builtins - headers & examples
 ii  bash-completion   20060301-3ubuntu3        programmable completion for the bash shell

ls -l /bin/bash
 -rwxr-xr-x 1 root root 813912 2008-05-12 19:36 /bin/bash

env | grep SHELL
 SHELL=/bin/bash
[/PHP]
BASH is definately bash...

sh, on the other hand is most definately dash...

Regards
Iain

---

### Post by nowshining on 2008-07-17
> **scorp123 said:**
> Nope. There are some hard-to-explain and IMHO stupid dependencies between "dash" and other packages. If you remove "dash" (e.g. 'sudo apt-get remove dash') then there is a chance that other packages might be accidentally removed as well. If I try that here I get this: ```
 > sudo apt-get remove dash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dash ubuntu-minimal
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  dash
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 262kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] no
Abort.
```

So instead of removing "dash" and risking unwanted side effects I prefer to just disable it and use "bash" as default shell.

oh I removed ubuntu-minimal awhile back. :) - all is there apt-get, etc..
```

dash ubuntu-minimal
```

example:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  dash*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 213kB disk space will be freed.
Do you want to continue [Y/n]?
```


^ as for the ^, as you can see - it just shows dash compared to your ubuntu-minimal. :)... as long as it's not ubuntu-desktop or kubuntu-desktop - it should be fine then unless removing dash would break bash....hmmmmm

---

### Post by scorp123 on 2008-07-17
> **tinivole said:**
>  BASH is definately bash... sh, on the other hand is most definately dash...  I was under the impression that /bin/sh and /bin/bash both linked to /bin/dash ... Oh well. I make mistakes too. My apologies to everyone then. :)

---

### Post by madams11 on 2008-08-01
> **scorp123 said:**
> Not true. Per default (e.g. after a Ubuntu installation) "dash" is the default shell. Even if **/etc/passwd** says that one's shell is **/bin/bash** it's "dash" that's being loaded because /bin/bash is just a symbolic link to "dash" ..... Unless you change it via '**sudo dpkg-reconfigure dash**' after which the symbolic link is permanently removed.

If you remove the link manually then everytime there is an update it will automagically be regenerated ... which is highly annoying (been there, done that). So to remove the link cleanly and keep it removed you have to use above command.

I just tried the dpkg-reconfigure dash, answered "NO" to the prompt, and yet I still have bash pointing to dash.  If I try to apt-get install bash, it tells me I have the latest version.

How can I get bash back?

---

### Post by scorp123 on 2008-08-03
> **madams11 said:**
> I just tried the dpkg-reconfigure dash, answered "NO" to the prompt, and yet I still have bash pointing to dash.  If I try to apt-get install bash, it tells me I have the latest version.

How can I get bash back? You can apparently simply remove it, with no ill side-effects. See the posting from user "nowshining" above. Once "dash" is gone, the default should be "bash" again.

---

