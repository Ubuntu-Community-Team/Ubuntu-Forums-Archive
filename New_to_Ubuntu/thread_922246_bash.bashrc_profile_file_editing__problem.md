---
title: "bash.bashrc profile file editing  problem"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by mam2008 on 2008-09-17
Hello all,
Iam suing ubuntu 7.04 desktop on my laptop.I was installing the perl program then decided to set the path by editing the bash.bashrc profile file.After setting the path,then I got the following message when i started the terminal commmand:
bash: lesspipe: command not found
bash: The: command not found
bash: sudo: command not found
bash: dircolors: command not found
bash: The: command not found
bash: sudo: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: currently: no completion specification
bash: complete: not: no completion specification
bash: complete: installed.: no completion specification
bash: complete: You: no completion specification
bash: complete: can: no completion specification
bash: complete: install: no completion specification
bash: complete: it: no completion specification
bash: complete: by: no completion specification
bash: complete: typing:: no completion specification
bash: complete: apt-get: no completion specification
bash: complete: install: no completion specification
bash: complete: sed: no completion specification

I'm  not in the root account,so I cannt edit it.How can I edit it again or   delete the added lines in bash.bashrc file?.
Thank you in advance for your help.
mam

---

### Post by tangibleorange on 2008-09-17
> **mam2008 said:**
> Hello all,
Iam suing ubuntu 7.04 desktop on my laptop.I was installing the perl program then decided to set the path by editing the bash.bashrc profile file.After setting the path,then I got the following message when i started the terminal commmand:
bash: lesspipe: command not found
bash: The: command not found
bash: sudo: command not found
bash: dircolors: command not found
bash: The: command not found
bash: sudo: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: currently: no completion specification
bash: complete: not: no completion specification
bash: complete: installed.: no completion specification
bash: complete: You: no completion specification
bash: complete: can: no completion specification
bash: complete: install: no completion specification
bash: complete: it: no completion specification
bash: complete: by: no completion specification
bash: complete: typing:: no completion specification
bash: complete: apt-get: no completion specification
bash: complete: install: no completion specification
bash: complete: sed: no completion specification

I'm  not in the root account,so I cannt edit it.How can I edit it again or   delete the added lines in bash.bashrc file?.
Thank you in advance for your help.
mam

well i don't know what you've done to your bashrc file but to edit it with root rights you can run this command:

```
sudo nano ~/.bashrc
```

if however bash is so borked on your profile that you can't run the command without loads of errors you will need to boot into recovery mode (an option after pressing ESC when your computer is loading GRUB at startup). then run the above command.

---

### Post by mam2008 on 2008-09-17
tangibleorange,
Thank you for your help,but it still giving error that it cannot find sudo command even in the recovery mode.,changed the session but still getting the same error.How can I enable the root account? Iam confused I dont know what to do,please any idea,appreciated

---

### Post by MegaJim on 2008-09-17
Most likely your path variables have been messed up, you can try asking your terminal

```
echo $PATH
```

if it doesnt look like this:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
```

you will need to replace them using
```
export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"
```

FYI to the poster above, i think the op is talking about the bash.bashrc file in /etc/ which requires root permissions to edit, not the user ~.bashrc file, either way he wouldn't need root permissions to edit it.

However, none of that will work as your paths are broken :S ->

If you just want to edit your bash.bashrc (as you are already logged in as root) you can use

```
nano /etc/bash.bashrc
```

---

### Post by jemate18 on 2008-09-17
> **mam2008 said:**
> Hello all,
Iam suing ubuntu 7.04 desktop on my laptop.I was installing the perl program then decided to set the path by editing the bash.bashrc profile file.After setting the path,then I got the following message when i started the terminal commmand:
bash: lesspipe: command not found
bash: The: command not found
bash: sudo: command not found
bash: dircolors: command not found
bash: The: command not found
bash: sudo: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: currently: no completion specification
bash: complete: not: no completion specification
bash: complete: installed.: no completion specification
bash: complete: You: no completion specification
bash: complete: can: no completion specification
bash: complete: install: no completion specification
bash: complete: it: no completion specification
bash: complete: by: no completion specification
bash: complete: typing:: no completion specification
bash: complete: apt-get: no completion specification
bash: complete: install: no completion specification
bash: complete: sed: no completion specification

I'm  not in the root account,so I cannt edit it.How can I edit it again or   delete the added lines in bash.bashrc file?.
Thank you in advance for your help.
mam

It happened to me 3 times.

Here is what I did to fix it.

Boot from live CD, mount the hardisk volume and 
Then edit your bash.bashrc file
save it. then boot from my hard disk
then GOOD! It is fixed.. Easy as that.....

---

### Post by jemate18 on 2008-09-17
next time, before editing an important file have a backup first

cp importantfile importantfile-backup

so that when things go wrong, you can easily fix it.

---

### Post by mam2008 on 2008-09-17
Megajim and jemate18
Thank you very much for your help! I have used megajim solution and it works.
thank you again
mam

---

### Post by jemate18 on 2008-09-17
> **mam2008 said:**
> Megajim and jemate18
Thank you very much for your help! I have used megajim solution and it works.
thank you again
mam

Please mark this thread as SOLVED and click the medal icon at the lower right part of megajim's post to THANK him and so that his reply will be marked as the USEFUL post, so that when others have the same problem, they will immediately find the solution to their answer.

---

