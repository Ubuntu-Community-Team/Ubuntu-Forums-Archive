---
title: "How to remove hydra in ubuntu?"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by Calvert on 2014-02-13
Hi, 

I installed hydra by copying command from a blog but I don't know how to remove it and where are the files being saved.


Please advice me how to remove it. Thanks in advance.

---

### Post by Bashing-om on 2014-02-13
Calvert; Hi ! Welcome to the forum .


How to (un)install a "program" is dependent on how it was installed. Maybe the author of the "program" included a removal routine in the package ?
As I know nothing of "hydra", please:
Provide us the link you used when you installed the "program" and we can see what action to take to remove it from your system.


[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by Calvert on 2014-02-14
Hi there,

[http://itswapshop.com/content/how-crack-ssh-ftp-or-telnet-server-using-hydra-ubuntu](http://itswapshop.com/content/how-crack-ssh-ftp-or-telnet-server-using-hydra-ubuntu)

I followed this to install hydra.

Please advice. Thanks

---

### Post by Bashing-om on 2014-02-14
Calvert; Umph ,

Not very informative there in the link to (un-)install hydra.
OK, is there anything in the tar file that you uncompressed ?
cd to the directory where you extracted the files:
```

ls -la

```
Is there a read me file ? Or, maybe a uninstall.sh file ?
Hopefully the author has made a provision to do the removal in an easy manner.

[INDENT][INDENT]directions are nice to have
[/INDENT][/INDENT]

---

### Post by Calvert on 2014-02-15
Well I am new to ubuntu and I couldn't get the way to find it out.

---

### Post by Vladlenin5000 on 2014-02-15
> **Calvert said:**
> Well I am new to ubuntu and I couldn't get the way to find it out.

Bashing-om asked you to check whether or not there was a READ ME file or an 'uninstaller' in the package you downloaded... There is but I couldn't attach it due to invalid file error ?!?

---

### Post by Bashing-om on 2014-02-15
Calvert; Hey,

Let's see if we can flounder our way through this.

OK, you downloaded the tar file somewhere onto your system, most likely ~/Downloads. And extracted the files in the tar.
We need to look at the files that were extracted and see if there are instructions to remove the application.
As an example, say you did download to the ~/Downloads directory, to see what the directory contains; terminal code:
```

ls -la ~/Downloads

```

And see what we can find for the author's instructions.

[INDENT][INDENT][INDENT]we be look'n
[/INDENT][/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2014-02-15
There's only a readme file and the reason I couldn't attach it before was due to a missing file extension. However there's only instructions on how to compile.
[ATTACH]250359[/ATTACH]

---

### Post by Bashing-om on 2014-02-15
@ Vladlenin5000 Hey, Thanks !

That may not directly help but at least it does make us look else where.
Will take a bit of thinking as to how best to proceed.

[INDENT][INDENT]study twice 
[INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-15
Calvert; Welp;

That avenue proves non-productive.
Let's do a bit of sleuthing, see if the author worked with the package manager.
What returns from terminal commands:
```

ls -la /var/lib/dpkg/info/hydra.list
cat /var/lib/dpkg/status | grep "hyrdra*"

```
Did the author leave a means to update his application ?
Post back these outputs
```

cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

Then next is to use "find" and see what is installed.

[INDENT]Got to be a way,
[INDENT][INDENT]and we want to do it cleanly
[/INDENT][/INDENT][/INDENT]

---

### Post by wiremoons on 2014-02-16
Hi

You can try the command in your terminal:   [FONT=Courier New]**which hydra**[/FONT]
This should tell you where the application is located on your computer, and therefore confirm it is is installed?

Bit of help on how to install, search for, and then remove applications using the Terminal are below - which might be useful for the future:

There is an application in the Ubuntu software repositories call 'hydra'.  You can find any application (installed or not) by searching for it in a Terminal window (or 'Ubuntu Software Center' of course). 

To find a packages using the Terminal window, one command you can use is:

[FONT=Courier New]**sudo apt-cache search <application-name>**[/FONT]

so to look for the application called 'hydra' enter:

[FONT=Courier New]**sudo apt-cache search hydra**[/FONT]

This returns a list of applications that match the name given, and the first in the list on my computer is: "***hydra - very fast network logon cracker***"

If you want more information about that particular application, you can then enter the command:

[FONT=Courier New]**sudo apt-cache show hydra**[/FONT]

This will tell the package maintainer details, the version, a brief description, etc.  If you want to see if it is installed, you can enter:

[FONT=Courier New]**dpkg --get-selections hydra**[/FONT]

And finally if you want to remove an application from your computer in the Terminal, you can use the command:

sudo apt-get remove <package-name>    so to remove the package called 'hydra' if it is installed, enter:  [FONT=Courier New]**sudo apt-get remove hydra**[/FONT]

However - if you followed the instructions on the page you linked to in the post above, you downloaded the source code directly from the site (ie the wget command on that page) and then compiled and installed it manually on your computer yourself. This approach therefore bypassed the package management commands shown in my post above. Sometimes you do need to do this, if you need a version newer than the one in the Ubuntu software repositories for example. However, it does mean you need to also manually remove the application yourself too.

You will need to locate where on your computer it installed the program, the man pages and maybe some configuration files. The location of these files can vary. You can search your computer for any files that begin with the name 'hydra' with the find command as below:

[FONT=Courier New]**sudo find / -name 'hydra*' -print 2> /dev/null**[/FONT]

This command starts the search in the root directory (so will search your whole computers file system), looks for any file starting with the name hyrda, print the results to the screen, and throws away any errors it encounters while it searches.

Just be careful the files you find are actually part of the application, and not part of something else !   Another approach is to rerun the step in the instruction you followed on the web page, and when you run the command: [FONT=Courier New] sudo make install[/FONT], this is the command that installs the program - so if you look at where is copies the files too, you can locate and removed them that way. The instructions is follows to copy these files will be in the 'Makefile' under the section called 'install'.

Apologies for the long post - hope it is useful to you though :)

---

