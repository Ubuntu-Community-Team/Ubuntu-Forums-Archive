---
title: "is their a way i can see all my installed programs but not librarys and other files?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-06-25
i wanted to know if i could just see my installed programs listed.

i want to do this because i am afraid i've installed stuff and forgotten about it.

i don't want to view librarys and codecs and docs and all the other extras though.

is their a way?

thanks in advance

---

### Post by cpetercarter on 2008-06-25
[http://ubuntuforums.org/showthread.php?p=1990911]("http://ubuntuforums.org/showthread.php?p=1990911")

---

### Post by Elfy on 2008-06-25
That includes all packages.

The only way I've managed to work it out was checking through the bash history file by finding apt-get install, this works because I tend to use that to do so.

pretty unelegant but it got the job done for me

Edit - in fact this gives me a list of the packages I installed through terminal

```
cat .bash_history |grep -a "sudo apt-get install*" >installbyapt.txt
```

---

### Post by Cypher on 2008-06-25
The package manager doesn't differentiate between application packages, library packages, doc packages and any other style of package. That sort of granularity is overkill for most package managers.

So if you query DPKG/SYNAPTIC for packages it will list everything. You will, however, find that the maintaners will preceed library packages with the words "lib" to make them stand out a little. Additionally, you might find packages with "-doc" and "-dev" which indicate what they are, so you could get a full list of all the packages and use GREP to ignore these kinds of packages..something like
```

dpkg -l | grep -ve '-dev' | grep -ve '-dbg' | grep -ve '<any other pattern>'

```
You can put in well known names in the <any other pattern> and keep repeating that over and over again to remove anything you don't want to see..

---

### Post by pluckypigeon on 2008-06-25
thanks to both for your replies. I will have to work with both of your ideas I guess. Unless someone does actually know a definite way, which I doubt

---

### Post by pluckypigeon on 2008-06-25
ok, what I have done so far is

 dpkg -l | grep -ve '-dev' | grep -ve '-dbg' >installed.txt

which gave me a list of details. preferably I would have liked it to have been without details but I'll have to work around that

---

### Post by Elfy on 2008-06-25
TBH I looked last year before I installed Gutsy and couldn't find anything that suited then, neither when I went to Hardy.

@cypher - can I assume you could put as many of those | grep -ve '-dbg' in as you wanted to

---

### Post by pluckypigeon on 2008-06-25
The reason why I asked this question is because I don't like the idea of installing something and it getting lost only for me to forget about it.

Is their a way to update alacarte with installed programs even if they need a terminal or something else to run?

I already know about the debian menu and this is not what I am looking for

---

### Post by cariboo on 2008-06-25
Have tried in a terminal:

```
cd /usr/bin
ls -l
```

This will list all the files in the /usr/bin directory which is where most of the programs are located, on my installation it lists over 1500 programs. If you have no idea what a program is, in a terminal type:

```
man <programname>
```

Jim

---

### Post by Elfy on 2008-06-25
> Is their a way to update alacarte with installed programs even if they need a terminal or something else to run?

I don't think there is without physically doing it yourself, if there is no instruction in the code to make a menu entry it won't happen is my understanding.

There is a history available in synaptic so if you knew when you installed something you could find it, eg if there was a bunch of stuff you alweays installed on a reinstallation you could easily check that. 

It is quite a hard thing to find out it has seemed to me before.

---

### Post by Cypher on 2008-06-25
> **pluckypigeon said:**
> ok, what I have done so far is

 dpkg -l | grep -ve '-dev' | grep -ve '-dbg' >installed.txt

which gave me a list of details. preferably I would have liked it to have been without details but I'll have to work around that
You can do some more "invert" greps to get rid of various cruft, use AWK and just get the package names and then exlcude the "-dev" and "-dbg" files..something like this:
```

dpkg -l | grep -v "^|" | grep -v "^Desired" | grep -v "^+++" | awk '{print $2}' | grep -ve '-dev' | grep -ve '-dbg' > installed.txt

```
The above code will give you just the package names.

---

### Post by Cypher on 2008-06-25
> **forestpixie2 said:**
> @cypher - can I assume you could put as many of those | grep -ve '-dbg' in as you wanted to
Yup..the PIPE (|) command will allow you batch together many commands, in this case multiple GREPs..you could throw in a few AWK's and SED's in there too..:)

---

### Post by Elfy on 2008-06-25
> **Cypher said:**
> Yup..the PIPE (|) command will allow you batch together many commands, in this case multiple GREPs..you could throw in a few AWK's and SED's in there too..:)

It's taken me a year to get my head round grep - I thought AWK was something a teengaer was half of :)

---

### Post by Ptero-4 on 2008-06-25
If you're on KDE you can use the applications:/ uri in konqueror to see your installed apps.

---

### Post by pluckypigeon on 2008-06-25
> **Cypher said:**
> 
```

dpkg -l | grep -v "^|" | grep -v "^Desired" | grep -v "^+++" | awk '{print $2}' | grep -ve '-dev' | grep -ve '-dbg' > installed.txt

```
The above code will give you just the package names.

This looks like exactly what I want.:)

Is that really all the programs though? 

Is their a way I could transfer that in to alacarte?

---

### Post by Elfy on 2008-06-25
> **Ptero-4 said:**
> If you're on KDE you can use the applications:/ uri in konqueror to see your installed apps.

Would that show up programs that don't have a menu item though

---

### Post by ibuclaw on 2008-06-25
> **pluckypigeon said:**
> This looks like exactly what I want.:)

Is that really all the programs though? 

Is their a way I could transfer that in to alacarte?

You can cut a load more off that list though.
There are still the odd apps that you don't need to see (such as system-required and library packages) and other socal stuff that you can't run directly.

```
dpkg -l | grep -v "^|" | grep -v "^Desired" | grep -v "^+++" | awk '{print $2}' | grep -ve '-dev' | grep -ve '-dbg' **| grep -ve "lib" | grep -ve 'python-' | grep -ve "xserver"** > installed.txt
```
The above cut down the size of my file from **1728** lines to **934** (using the command "wc -l installed.txt").

Regards
Iain

---

### Post by Martje_001 on 2008-06-25
Look at **Applications --> Add/Remove** and select '**Installed**'.

---

### Post by pluckypigeon on 2008-06-25
> **Martje_001 said:**
> Look at **Applications --> Add/Remove** and select '**Installed**'.

doesn't that leave stuff out though?

---

### Post by ibuclaw on 2008-06-25
Yes, it does.

OK, here is my attempt at a solution.
I'm just testing it right now. I will post a fix if I find a problem with it.

Save this inside a text file and set the permissions of it to be executable (**chmod +x FILENAME**)
Then run it using **./FILENAME**
Replace "FILENAME" with a suitable name for the file.
```

#!/bin/bash

dirs=( `echo $PATH | sed 's/:/\n/g'` )
count=${#dirs[@]}
i=0

# Checks for existance of tmp files for the script
test -e /tmp/.tmppath && rm /tmp/.tmppath
test -e /tmp/.tmpinst && rm /tmp/.tmpinst

# Find all executables in the $PATH directories.
while [ $i -lt $count ]
do find ${dirs[$i]} -type f -print >> /tmp/.tmppath
   let "i++"
done

# Find them in the repository (takes a long time to process).
while read line
do dpkg -S "$line" | awk '{print $1}' | sed s/:// >> /tmp/.tmpinst
done < /tmp/.tmppath

# Sort the installed packages alphabetically and remove double lines.
sort -u /tmp/.tmpinst >~/installed.txt
rm /tmp/.tmppath /tmp/.tmpinst

```
Also, a list of executable files that have not been installed with apt will be shown in the terminal stderr output.
ie:
```
dpkg: /usr/local/bin/phun not found.
```
It should not be too much to worry about, unless you have never used anything but apt to install software.

Also note, that it will take a while to process everything, dpkg -S is a rather slow command that searches the entire repository to find a match on the file paths.

[EDIT]
It works :D
I have 639 installed apps that are runnable from my $PATH path.
There are a few "-dev" packages in there. But I think it is a much better output.

[EDIT2]
Oh, and if you just so happen to get
```
dpkg: /usr/bin/[ not found.
```
Just so you know, it **IS** supposed to be there (It's an alternative to the "test" command).
Just incase you get confused by it ;)
ie (a test of it in action):
```
**[** -d /usr/bin ] && echo "EXISTS"
test -d /usr/bin && echo "EXISTS"
```
Both do the exact same job.

Regards
Iain

---

### Post by Martje_001 on 2008-06-25
> **pluckypigeon said:**
> doesn't that leave stuff out though?
Some yes. But the TS said he/she didn't want 'advanced' stuff.

---

### Post by pluckypigeon on 2008-06-25
> **Martje_001 said:**
> Some yes. But the TS said he/she didn't want 'advanced' stuff.

i meant leave programs out not other stuff

---

### Post by Martje_001 on 2008-06-25
Yes, it leaves some programs out. ;)

---

### Post by pluckypigeon on 2008-06-25
> **tinivole said:**
> Yes, it does.


```

#!/bin/bash

dirs=( `echo $PATH | sed 's/:/\n/g'` )
count=${#dirs[@]}
i=0

# Checks for existance of tmp files for the script
test -e /tmp/.tmppath && rm /tmp/.tmppath
test -e /tmp/.tmpinst && rm /tmp/.tmpinst

# Find all executables in the $PATH directories.
while [ $i -lt $count ]
do find ${dirs[$i]} -type f -print >> /tmp/.tmppath
   let "i++"
done

# Find them in the repository (takes a long time to process).
while read line
do dpkg -S "$line" | awk '{print $1}' | sed s/:// >> /tmp/.tmpinst
done < /tmp/.tmppath

# Sort the installed packages alphabetically and remove double lines.
sort -u /tmp/.tmpinst >~/installed.txt
rm /tmp/.tmppath /tmp/.tmpinst

```


i didn't get any form of list anywhere. where is the list?

---

### Post by ibuclaw on 2008-06-26
> sort -u /tmp/.tmpinst >**~/installed.txt**

It will be in your **/home/name/** directory. Under the filename "**installed.txt**"

Regards
Iain

---

### Post by ConMan318 on 2008-06-26
How about Applications > Add/Remove and by "show" go to "installed applications only"?

---

