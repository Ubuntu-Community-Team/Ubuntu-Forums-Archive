---
title: "bash scripting"
date: 2010-06-03
forum: Programming Talk
---

### Post by Drenriza on 2010-06-03
Is it possible with bash scripting to make a list of installed packages with ```
dpkg -l |grep (package name)
```

or with some other (better) command.

and then compare it to a list, that i have defined.

The purpose of this would be to see if a system has the right packages installed, by comparing it to a list i have defined. That would be the "correct package list".

So i quickly can see if an external system has all the correct packages or correct package versions, or if it needs an upgrade.

Does this make any sence?

Also i'am reading some guides and tutorials. And their keeps being examples of the $...... what does this do in bash? Does this still means it a variable?

Thanks on advance.

---

### Post by leg on 2010-06-03
You can do it with dpkg or apt but I am not sure of the arguments required.

---

### Post by Drenriza on 2010-06-03
Maybe its just me.

But when i try to do the following

```
#!/bin/bash

$ echo "I am $logname"

$ echo "My computer is $(hostname)"
```

i make the script executable. Run it, and then it says that neither of the commands are found......... why... since logname and hostname are commands i can run in the terminal.

---

### Post by leg on 2010-06-03
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

Have a look through those they are very good resources.

---

### Post by rnerwein on 2010-06-03
hi
try this as a script:
#!/bin/bash
 dpkg --get-selections | grep -v deinstall > allepakete.`date +%y.%m.%d.%H.%M`
exit $?

and to get all the packets ( from a spezial date ) back:
dpkg --set-selections < allepakete.yy.mm.dd.hh.mm

( answer with: i )
ciao

---

### Post by geirha on 2010-06-03
> **leg said:**
> [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

Have a look through those they are very good resources.

They are not, at least not for beginners. They don't teach you good practice and in some cases they're just plain wrong. I recommend [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

@Drenriza

The $ just represents the bash prompt that you see in an interactive bash shell. The default prompt in ubuntu looks something like:

```
username@hostname:/current/dir$ 
```
The prompt can be customized quite extensively, so guides commonly just use a $ to represent it. You do not actually type in that $ at the start of a line, neither in an interactive shell nor a script.

What is the format of the file you have? Is it just package names, one package per line, or is it dpkg -l output?

---

### Post by Drenriza on 2010-06-03
> The $ just represents the bash prompt that you see in an interactive bash shell

Hehe, ive spent hours thinking about this while i also did other stuff. About why it didnt work. And no guides have "told" that the $ is not actually to be typed. Ty

```
cristian@cristian-laptop:~/Dokumenter/scripts$ ./script\ 1.0 
I am 
My computer is cristian-laptop
cristian@cristian-laptop:~/Dokumenter/scripts$ 

```

And now its working. THANKS alot mate. This actually made my day. From being a :mad::mad::mad::mad: day to be a :D:D:D:D day


> What is the format of the file you have? Is it just package names, one package per line, or is it dpkg -l output?

I'm not quite sure what you mean.

I would like to make a static list of packages that should be installed on a system. I would then like to compare external systems to this static list. To make sure that all necessary packages are installed. Or if the system needs to be upgraded.

For me to take a decision on weather the system needs an upgrade or not, i need the script to tell me if their a packages that are on the static list that arnt on the external system. And then tell me what packages that are missing.

Hope it makes sence.

---

### Post by P.ap G on 2010-06-03
If you go to  /var/cache/apt/archives ,unless you have deleted it ,you will find a list all installed package  files there .

If you use vim you could go into the file and do       :w  filename_you_like ; This will  copy all this into a new
 file  for you , if the file already exists  use  : w >>  filename    to append  an   to existing file .

---

### Post by geirha on 2010-06-04
```
aptitude -F "%?p" search "~i"
``` will list all installed packages. Unfortunately aptitude appends a lot of spaces after each packagename to make each line of equal length. There might be a way to tell aptitude not to do that, but at the present I don't feel like sifting through the documentation (it's quite large), so instead we'll just pipe it through tr to remove all the spaces.

Now, let's say you want vim, hello and coreutils to be installed, then put those in a file, one package per line. E.g. packagelist.txt:
```

vim
hello
coreutils

```

The following grep command will output all lines in packagelist.txt that did not appear in installed_packages.txt
```

aptitude -F "%?p" search "~i" | tr -d ' ' > installed_packages.txt
grep -Fxv -f installed_packages.txt packagelist.txt
```

You can also use comm, but it only operates on sorted files, so
```
comm -13 <(sort installed_packages.txt) <(sort packagelist.txt)
```

See [http://mywiki.wooledge.org/BashFAQ/036](http://mywiki.wooledge.org/BashFAQ/036)

---

### Post by Penguin Guy on 2010-06-04
**The answer is quite complicated:**


**List packages:**
To get the lists of packages use this command:
```
dpkg -l | grep ^ii | awk '{print $2}' > list-of-packages
```
```
**dpkg -l** - list package info
**grep ^ii** - ignore lines that don't have packages on
**awk '{print $2}'** - get the second column (the package name)
**> list-of-packages** - output file (can be anything/anywhere you want)
```


**Compare packages:**
Once you have your two package lists you can compare them using this command:
```
diff correct-packages my-packages | grep -E '^>|^<'
```
```
**diff** - find the difference between the files
**correct-packages** - list of packages you want
**my-packages** - list of packages you actually have
**grep -E '^>|^<'** - list only the changed packages
```

The output:
```
**>** - extra package
**<** - missing package
```


**Note:**
A lot of system packages change from version to version, so this might prove troublesome. I would just make a list of your favorite packages and then write a script to automatically install them for you.
I would also recommend [http://www.linuxcommand.org/](http://www.linuxcommand.org/) - I learnt bash from that site and it explains both the interactive terminal and scripts.

---

### Post by oldfred on 2010-06-04
I am in process of creating my own reinstall script just to make it easier to update my system from version to version. I do not really know bash.

Someone suggested this but I have not tried it.

#If you have your own list:
#while read package; do
#    apt-get install $package
#done < pkglist.txt

This works from a dpkg list.
apt-get update
apt-get dist-upgrade
# Finally, install all the packages from previous install
# must have saved ubuntu-files from previous install to this directory
dpkg --set-selections < ubuntu-files
dselect
apt-get -y update
apt-get dselect-upgrade

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)


More complete lists (not for reinstall above)
List with explanations of programs
dpkg -l > ~/Desktop/installed_programs.txt

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

### Post by Drenriza on 2010-06-09
> **Penguin Guy said:**
> **The answer is quite complicated:**


**List packages:**
To get the lists of packages use this command:
```
dpkg -l | grep ^ii | awk '{print $2}' > list-of-packages
```
```
**dpkg -l** - list package info
**grep ^ii** - ignore lines that don't have packages on
**awk '{print $2}'** - get the second column (the package name)
**> list-of-packages** - output file (can be anything/anywhere you want)
```


**Compare packages:**
Once you have your two package lists you can compare them using this command:
```
diff correct-packages my-packages | grep -E '^>|^<'
```
```
**diff** - find the difference between the files
**correct-packages** - list of packages you want
**my-packages** - list of packages you actually have
**grep -E '^>|^<'** - list only the changed packages
```

The output:
```
**>** - extra package
**<** - missing package
```


**Note:**
A lot of system packages change from version to version, so this might prove troublesome. I would just make a list of your favorite packages and then write a script to automatically install them for you.
I would also recommend [http://www.linuxcommand.org/](http://www.linuxcommand.org/) - I learnt bash from that site and it explains both the interactive terminal and scripts.

Penguin Guy.

Can you explane
dpkg -l - list package info
grep ^ii - ignore lines that don't have packages on
awk '{print $2}' - get the second column (the package name)
> list-of-packages - output file (can be anything/anywhere you want)

and
diff - find the difference between the files
correct-packages - list of packages you want
my-packages - list of packages you actually have
grep -E '^>|^<' - list only the changed packages

abit. Prehaps giving an example with the 2 commands. I can see it makes sence. But im not a 100% how to run it

---

### Post by Drenriza on 2010-06-09
what i dont quite get is that, after i have created my list of installed packages

```
> list-of-packages
```

how do i then with
```
correct-packages - list of packages you want
my-packages - list of packages you actually have
```

compare the lists.

does my "correct package list" need to be a .txt file? where i have
added all the package names in? 1 package per line. i don't quite get it, can you please explane.

---

### Post by Penguin Guy on 2010-06-09
Install the packages you want, then run this command:
```
dpkg -l | grep ^ii | awk '{print $2}' > list-of-packages
```
You should now have a list of the packages you want (I will call this list [FONT="Courier New"]correct-packages[/FONT]).

When you want to fix the packages on a new system you'll need to run the same command as above to list the packages on the new system. You should now have two lists (I will call them [FONT="Courier New"]correct-packages[/FONT] and [FONT="Courier New"]my-packages[/FONT]).

Now you need to find the difference between the two, which we will do using [FONT="Courier New"]diff[/FONT]:
```
diff correct-packages my-packages | grep -E '^>|^<'
```

I hope that makes sense.

---

### Post by oldfred on 2010-06-09
If you have a list of packages you want you do not have to compare with what is already installed. The installer will just ignore any that are already installed and not reinstall.

---

### Post by Drenriza on 2010-06-10
I tryed the commands. Making the 2 lists and then comparing them. But when i did so nothing happened.

```
cristian@cristian-laptop:~/Dokumenter/scripts$ diff correct-packages my-packages | grep -E '^>|^<'
cristian@cristian-laptop:~/Dokumenter/scripts$ 
```

The 2 lists are in the same folder, and iam in the terminal standing in the path to that folder.

---

### Post by Drenriza on 2010-06-10
Is it me who have made a mistake?

Just so you dont believe i ran it and matched the same packages on my system then i made the first text file
with my packages, waited for updates and then i made the second file to compare.

So i cant see why it shouldn't work, for that reason.

---

### Post by Drenriza on 2010-06-10
Working, solved.

Its a nice command

---

### Post by Penguin Guy on 2010-06-10
> **Drenriza said:**
> Working, solved.
I'm glad you got it sorted, but it would help others find what they're looking for, and reduce clutter, if you could [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") through [COLOR="Green"]Thread Tools -> Mark this thread as solved[/COLOR]. Thanks :).

---

### Post by Drenriza on 2010-06-11
I will resolve it :p but haven't had the chance to do it before now.

:p anyways thanks for the help Penguin.

---

