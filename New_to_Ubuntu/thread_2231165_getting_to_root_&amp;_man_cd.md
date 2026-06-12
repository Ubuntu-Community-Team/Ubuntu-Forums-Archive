---
title: "getting to root &amp; man cd"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by Johnny3 on 2014-06-23
johnny@johnny-desktop:~$ sudo cd /
[sudo] password for johnny: 
sudo: cd: command not found
johnny@johnny-desktop:~$ sudo cd/
sudo: cd/: command not found
johnny@johnny-desktop:~$ man cd
No manual entry for cd

I have been tying to get to use the terminal more. Most of the time it is copy and paste. I can't get to root google I find the commands but they don't work. Tried with a space between cd and / and no space. Also have tried the man for cd and CD but that is no help. For ls, pwd,etc man works. I am using Ubuntu 14.04 all updates and upgrades in SPM too. What am I doing wrong?
Thanks and God Bless Johnny333 67++

---

### Post by grahammechanical on 2014-06-23
Try

```
 help cd
```

This is what I got just now

> cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
    
    The variable CDPATH defines the search path for the directory containing
    DIR.  Alternative directory names in CDPATH are separated by a colon (:).
    A null directory name is the same as the current directory.  If DIR begins
    with a slash (/), then CDPATH is not used.
    
    If the directory is not found, and the shell option `cdable_vars' is set,
    the word is assumed to be  a variable name.  If that variable has a value,
    its value is used for DIR.
    
    Options:
        -L    force symbolic links to be followed: resolve symbolic links in
        DIR after processing instances of `..'
        -P    use the physical directory structure without following symbolic
        links: resolve symbolic links in DIR before processing instances
        of `..'
        -e    if the -P option is supplied, and the current working directory
        cannot be determined successfully, exit with a non-zero status
        -@  on systems that support it, present a file with extended attributes
            as a directory containing the file attributes
    
    The default is to follow symbolic links, as if `-L' were specified.
    `..' is processed by removing the immediately previous pathname component
    back to a slash or the beginning of DIR.
    
    Exit Status:
    Returns 0 if the directory is changed, and if $PWD is set successfully when
    -P is used; non-zero otherwise.


The second point you need to define a directory and/or the path to the directory. Try

```
cd Downloads
```

Also note that this will take you back up the directory structure to the directory you just came from.

```
cd ..
```

I do not think that we need to prepend sudo to the cd command. I don't and cd works just fine. This is what I get when I run

```
cd /
```

followed by 

```
ls
```

> graham@sdb8-Roll-Dev:~$ cd /
graham@sdb8-Roll-Dev:/$ ls
bin    dev   initrd.img      lib64       mnt   root  srv  usr      vmlinuz.old
boot   etc   initrd.img.old  lost+found  opt   run   sys  var
cdrom  home  lib             media       proc  sbin  tmp  vmlinuz


See, no sudo and it works. I am in root ( / ) this ~$ is changed to /$


Regards.

---

### Post by Johnny3 on 2014-06-23
I can move around in my home directory fine. But can't move up to my root directory. I think the $ means home directory and I want to get to the root  directory which is one up from home.
Thanks Johnny333 67+++

---

### Post by Iowan on 2014-06-23
~$ is home, /$ is root. **pwd** will show you where you are.
```

iowan@4500S:/$ cd
iowan@4500S:~$ pwd
/home/iowan
iowan@4500S:~$ cd /
iowan@4500S:/$ pwd
/
iowan@4500S:/$ sudo -i
[sudo] password for iowan: 
root@4500S:~# pwd
/root
root@4500S:~# cd /
root@4500S:/# pwd
/
root@4500S:/# exit
logout
iowan@4500S:~$ 

```
$ for users, # for root

---

### Post by coldcritter64 on 2014-06-23
The ~ symbol in your prompt indicates you are in the home folder not the $ symbol. 

If your prompt shows a $ sign you are operating the terminal as your user, if it shows as a # symbol it is running as root user; the ~ symbol is the working directory (in your home folder when it shows).

To cd to root try "cd /" without the quotes to change to the root directory and note the prompt will show a "/" instead of a "~" BUT the $ (indicating you as the user) will stay the same.

Edit: ninja'd, I just noted Iowan's reply says the same + "pwd" noted OP.

---

### Post by buzzingrobot on 2014-06-23
"cd" is built into the Bash shell, the program that parses the command line and launches the specified commands. There is no executable separate cd program.  That's why "sudo cd" returned "command not found".

---

### Post by Iowan on 2014-06-23
> **coldcritter64 said:**
> Edit: ninja'd, Doesn't happen often.
Glad you posted - it's valuable to have that RootSudo Documentation link in your sig available!

---

### Post by Johnny3 on 2014-06-23
> **buzzingrobot said:**
> "cd" is built into the Bash shell, the program that parses the command line and launches the specified commands. There is no executable separate cd program.  That's why "sudo cd" returned "command not found".
I had a / behind the cd command. Which this [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) under File & Directory Commands should take me to root but does not.
Thanks Johnny

---

### Post by buzzingrobot on 2014-06-23
> **Johnny3 said:**
> I had a / behind the cd command. Which this [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) under File & Directory Commands should take me to root but does not.
Thanks Johnny

"cd/" will return "bash: cd/: No such file or directory". because there's nothing in the filesystem called "cd/" for bash to find.

"cd /" -- with the space -- will change the current directory to the "/" directory. (BTW, that's a different directory than "/root" ) The "cd" command is built into bash, along with a number of others that also do not exist as  separate executables.

"sudo cd /" returns "sudo: cd: command not found" because sudo launches a process that looks for an executable called "cd" and doesn't find one because there isn't one.

Confusingly, "sudo pwd" (Print Working Directory), another Bash builtin, works as expected.

---

### Post by Impavidus on 2014-06-24
> **buzzingrobot said:**
> Confusingly, "sudo pwd" (Print Working Directory), another Bash builtin, works as expected.
But that's because pwd is also an executable in /bin. For efficiency reasons it's usually used as a shell build-in, but when used with sudo, /bin/pwd is used. Both function more or less identically. In case of cd this doesn't work, as cd is used to set a property of the running shell and therefore can only be a shell build-in.```
$ type cd
cd is a build-in shell function
$ type pwd
pwd is a build-in shell function
$ ls -l /bin/pwd
-rwxr-xr-x 1 root root 31392 mrt 24 08:35 /bin/pwd
$ type /bin/pwd
/bin/pwd is /bin/pwd
$ ls -l /bin/cd
ls: Cannot access /bin/cd: No such file or directory
```(I translated to english, so the exact wording may be off.)

---

### Post by buzzingrobot on 2014-06-24
Ah, thanks.  I did the "type pwd', but didn't go looking for it elsewhere.

---

### Post by Johnny3 on 2014-06-29
The easy way for me is just sudo nautilus most of the time.
Thanks and God Bles Johnny 68++ and still moving

---

