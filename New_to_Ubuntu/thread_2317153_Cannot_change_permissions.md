---
title: "Cannot change permissions"
date: 2016-03-14
forum: New to Ubuntu
---

### Post by sarah_2 on 2016-03-14
Hi all,

I've only been running ubuntu for the last few weeks or so. But I have this really annoying issue. I am unable to run one of my programs via Terminal, because it keeps saying permission denied.

I have tried chmod, etc. I have tried doing it by right clicking on the actual file. But nothing works.

Also, when I try and move another program/file into /usr/bin, it won't let me either, again saying I don't have permission. I've done heaps of googling and trying various things, and I just can't seem to fix this. I am the only user for my computer - I should have full permissions.

If anyone could help, I would be so grateful.

Thanks. :confused:

---

### Post by kevdog on 2016-03-14
I'm not an expert with the GUI stuff but I can do it in a terminal.  
If you were to list permissions in the terminal or in the gui, you would see something like this:

(Using the ls -l command within the appropriate directory):
-rw-r--r--    1 root    wheel    656 Jan 14  2015 org.macports.logrotate.plist

This line shows a few things
-rw-r--r--   I want you to think of this line in a series of triplets (forget the first dash, it specifies a directory of not). The first triplet rw- is the owner permissions, the second triplet r-- is the group permissions, and the third r-- is everybody else.
root is the owner of this file, and the group is wheel.  

The dashes symbolize space holders.  Within a triplet, the first dash is either r or - (meaning read or not read), the second dash is either w or - (meaning write or not write), and the third - is either x or - (meaning executable or not).

In this particular example,
Root has read and write privileges but not executable privileges
Wheel group has read privileges but not write or executable privileges
and everyone else has read but not write or executable priviledges

rwx -- can be represented by a binary number. Probably a better explanation to this but each place holder is represented by a binary number: 
rwx -- r=2^2, w=2^1, x= 2^0.  So if read privileges are present, its represented as a 4, if write privileges are present its represented by a 2 and if executable privileges are present its represented by a 1.  (You'll see where I'm going in a second). 

So in the example above
rw-r--r--
Owner = r+w = 4+2=6
Group = r = 4
Other = r = 4
So in essence putting this together the file listed above has permissions 644.  

If you need to change permissions to a particular file, you either need to change the ownership of the file to you, or change the group ownership or put yourself in the group owning the file, or change the properties of the file so you can either read it, write to it, or execute it.  chown can change the owner, chmod can change the file properties.

/usr/bin is usually owned by root:root (Owner root, group root) and files usually have 755 permissions (rwx,r-x,r-x) meaning anyone can execute or read the files within /usr/bin, but only root or sudo can write to the file.  

Can you post maybe a little bit more info about the file you're trying to run?

---

### Post by yetimon_64 on 2016-03-14
> **sarah_2 said:**
> Hi all,

I've only been running ubuntu for the last few weeks or so. But I have this really annoying issue. I am unable to run one of my programs via Terminal, because it keeps saying permission denied.

What is the program name please and does it need to be run as root ?  You may need to check the permissions on the executable or if it requires root privileges to run you must preface the command with the "sudo" command eg...
```
sudo <your-program-name>
``` 
...then input your user password to raise privileges for the program. You won't see any indication of your password being entered in terminal, an extra security measure; just enter it as you normally would and press the enter button. If you put the password in right it should work ok.

> **sarah_2 said:**
> Hi all,Also, when I try and move another program/file into /usr/bin, it won't let me either, again saying I don't have permission. I've done heaps of googling and trying various things, and I just can't seem to fix this. I am the only user for my computer - **I should have full permissions.**

No, not in linux, you need to authenticate any root level programs or actions to do with the root filesystem otherwise malware/user mistakes can do serious damage to your install. It may seem a nuisance for someone coming from another closed source OS but it is also _*one*_ of the main reasons linux is so secure from malware etc. 

In this case the sudo command is used in terminal with the mv or cp commands or else you will have to use a root nautilus window (**dangerous for beginners**, too darn easy to destroy an installation) to move files to a root owned location. When opening nautilus as root you can do so from a terminal with the command ...

```
sudo -H nautilus
```Edit: or as Bucky Ball notes in the next post, an even better command ...
```
gksudo nautilus
```  
 **WARNING: you can destroy your installation from this window if you make a mistake here**. Use only for as long as absolutely needed then shut the window and terminal down.

Most applications installed from the software center or terminal will be put into such a location. You can run programs of your own from your home folder if they do not need root privileges, a much better idea. Also users should not add programs to /usr/bin, if you have a custom program needing root access /usr/local/bin is a better location; if the program doesn't need to run as root, run it from your home folder which you own and have full rights to; that will save the permissions headaches you are currently experiencing. 

Some reading for you about using sudo for root level access : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Some more information about the program you are trying to run and move etc would be a great help.

---

### Post by Bucky Ball on 2016-03-14
It helps when you tell us what it is you're trying to launch from a terminal (and perhaps why from a terminal).

You want:

> gksudo <your_program_ name>

Insert your program name after gksudo, obviously enough. Hit enter. You'll be asked for your password. It will be invisible. That is normal.

---

### Post by QIII on 2016-03-14
> I am the only user for my computer - I should have full permissions.

Not quite correct, and no you shouldn't.  Besides yourself, there is at least "root".  Some permissions are reserved for root only.

However, you can temporarily raise you permissions to do nearly everything root can do by prefixing commands with "sudo".

Rather than rooting around in your file permissions and making random changes that my render your machine inoperable and unrecoverable, try your terminal command with "sudo" as in 

```
sudo somecommand
```

You will be asked for your password.  That is the password you use to log in with.

gksudo (or kdesudo for KDE) should be used with graphical applications.

Don't start messing around with file permissions anywhere outside of your /home directory unless you know *exactly what you are doing*.  Your system is designed and installed with certain permissions set on many files and changing those permissions will likely cause you now end of problems and leave you with no option but to reinstall.

---

### Post by sarah_2 on 2016-03-18
Thanks, everyone, for your really really informative and helpful  answers. I tried the sudo command in front, as suggested, and that has  worked for some things -- but still not for others.

I am trying  to run John the Ripper - for application security testing, not for any  malicious intent. I believe this does need to be run from root...correct  me if I'm wrong. Currently, when I'm trying the command: sudo unshadow  /etc/passwd /etc/shadow > /root/examples_passwd (to create one file  with username and password details), I get the following response: bash:  /root/examples_passwd permission denied. 

I hope that sheds some  clarity on what I am trying to do, and thanks once again for all your  help. I may not have fully solved my issue yet, but I learnt a bit and  it did help some.

It is just trying to do stuff around this application that I have encountered the permission issues.

---

### Post by howefield on 2016-03-18
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

Thread closed.

---

