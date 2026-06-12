---
title: "shell script: &quot;#!/bin/bash&quot; has no effect!"
date: 2011-08-25
forum: Programming Talk
---

### Post by CryptKeeper777 on 2011-08-25
I've just started writing a shell script. That's what I have so far:

```

#!/bin/bash

cd Music

find . -maxdepth 1 -not -name ".*" -type d -print0 | \
while read -d $'\0' artist
do
    echo "$artist"
done

```The subfolders of Music have spaces in their names, that's why I can't simply use this command instead of the huge find command:
```
 for artist in *; do echo "$artist"; done 
```Unfortunately, running the script gives me the following error message:
```
 read: 9: Illegal option -d 
```If I run the exact same find command directly in the bash terminal, it works without any problems.

With google I found out that the problem is that the option -d of the read command is only available in bash, but not in sh. To solve this, the first line of the script must be #!/bin/bash. But that's the case here!

Why has this first line no effect???

---

### Post by fdrake on 2011-08-25
> **CryptKeeper777 said:**
> I've just started writing a shell script. That's what I have so far:

```

#!/bin/bash

cd Music

find . -maxdepth 1 -not -name ".*" -type d -print0 | \
while read -d $'\0' artist
do
    echo "$artist"
done

```The subfolders of Music have spaces in their names, that's why I can't simply use this command instead of the huge find command:
```
 for artist in *; do echo "$artist"; done 
```Unfortunately, running the script gives me the following error message:
```
 read: 9: Illegal option -d 
```If I run the exact same find command directly in the bash terminal, it works without any problems.

With google I found out that the problem is that the option -d of the read command is only available in bash, but not in sh. To solve this, the first line of the script must be #!/bin/bash. But that's the case here!

Why has this first line no effect???
try to change the first line into:

#!/bin/dash

and see if that works!

---

### Post by CryptKeeper777 on 2011-08-25
> **fdrake said:**
> try to change the first line into:

#!/bin/dash

and see if that works!
No, that doesn't have any effect...

---

### Post by sisco311 on 2011-08-25
> **CryptKeeper777 said:**
> 
Why has this first line no effect???

Most likely you run it in dash (sh), like:
```
sh myscript
```

Don't do that, you have  to run it in bash:
```
bash myscript
```

Or make it executable:
```
chmod +x myscript
```

and simply, run:
```
./myscript
```

---

### Post by sisco311 on 2011-08-25
BTW, the for loop should do the trick.  BASH does know that it's dealing with filenames, and it does know what the filenames are, and as such it can split them up nicely.

---

### Post by CryptKeeper777 on 2011-08-25
> **sisco311 said:**
> Most likely you run it in dash (sh), like:
```
sh myscript
```Don't do that, you have  to run it in bash:
```
bash myscript
``` 
Cool, using bash script.sh instead of sh script.sh works perfectly! That the solution would be that easy...

But I've done quite a lot of shell scripting in the last half year, first on OS X and then on Fedora (until I decided Xubuntu's the best distro for me), and I always ran the scripts with sh and I had never any problems with script using this exact command. 

Why doesn't it work on Ubuntu?

---

### Post by CryptKeeper777 on 2011-08-25
> **sisco311 said:**
> BTW, the for loop should do the trick.  BASH does know that it's dealing with filenames, and it does know what the filenames are, and as such it can split them up nicely.
Hmm, yes I've just tried it out and it seems to work despite the filenames containing spaces. Back on Fedora that never worked, the filenames were split into pieces at the space characters, that's why I had to use this find construction...

---

### Post by Bachstelze on 2011-08-25
> **CryptKeeper777 said:**
> Cool, using bash script.sh instead of sh script.sh works perfectly! That the solution would be that easy...

But I've done quite a lot of shell scripting in the last half year, first on OS X and then on Fedora (until I decided Xubuntu's the best distro for me), and I always ran the scripts with sh and I had never any problems with script using this exact command. 

Why doesn't it work on Ubuntu?

Because in Ubuntu, sh is dash, which is a lighter shell that conforms strictly to the POSIX standard and does not support things that work in Bash but are not part of the standard.  If your script uses Bash-only constructs (sometimes called "bashisms"), you should run it with bash, not sh.  On a lot of other systems, sh is Bash, and that's why a script with bashisms will work when run with sh, but you should avoid it because as you see, it does not work on all systems.

---

### Post by sisco311 on 2011-08-25
> **CryptKeeper777 said:**
> Cool, using bash script.sh instead of sh script.sh works perfectly! That the solution would be that easy...

But I've done quite a lot of shell scripting in the last half year, first on OS X and then on Fedora (until I decided Xubuntu's the best distro for me), and I always ran the scripts with sh and I had never any problems with script using this exact command. 

Why doesn't it work on Ubuntu?

In order to speed up the boot process Ubuntu uses dash as the default system shell, hence sh is a symlink to dash. See: [uwiki]DashAsBinSh[/uwiki]

Bash is still the default login shell. 

> **CryptKeeper777 said:**
> Hmm, yes I've just tried it out and it seems to work despite the filenames containing spaces. Back on Fedora that never worked, the filenames were split into pieces at the space characters, that's why I had to use this find construction...

Just a guess, but one of the most common mistakes BASH programmers make is to write a loop like this:

```
for i in $(ls *.txt) #WRONG
do
   something
done
```

For more, see:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by CryptKeeper777 on 2011-08-27
> **sisco311 said:**
> In order to speed up the boot process Ubuntu uses dash as the default system shell, hence sh is a symlink to dash. See: [uwiki]DashAsBinSh[/uwiki]

Bash is still the default login shell. 



Just a guess, but one of the most common mistakes BASH programmers make is to write a loop like this:

```
for i in $(ls *.txt) #WRONG
do
   something
done
```For more, see:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
No I didn't do it like that but simply "for i in *; do..." but it split up the filenames anyway.

Thanks for die useful link, I'll go through it!

---

### Post by CryptKeeper777 on 2011-08-27
When I do "for i in *; do echo "$i"; done" it splits up all the filenames at the space characters! Strange, because I'm sure it worked when I tried it out after it was mentioned in this thread...

Whatever, I'll just return to the find construct since that one works.

**Edit**: Turns out it work after all, I accidently created folders on the basis of the split-up names of the existing folders, that's why it seemed as if "for i in *; do echo "$i"; done" split up the names... Mea culpa.

---

### Post by AlphaLexman on 2011-08-27
Another thing BTW, if you happen to have some stray songs/files in the Music directory, the for loop would pick those up also. To avoid this add a slash like this...
```
for i in *[COLOR="Red"]/[/COLOR]; do echo "$i"; done
```

---

### Post by CryptKeeper777 on 2011-08-28
> **AlphaLexman said:**
> Another thing BTW, if you happen to have some stray songs/files in the Music directory, the for loop would pick those up also. To avoid this add a slash like this...
```
for i in *[COLOR=Red]/[/COLOR]; do echo "$i"; done
```
Nice, I didn't know that I can only loop through folders this way, thanks! I don't need it for my purpose, though, there are no stray song files in my Music folder...

---

### Post by ziekfiguur on 2011-08-28
The "#!/bin/bash" line only has an effect if you make your script executable and call it like ```
./myscript
``` When you do that the kernel doesn't know how to run the script and look at the first line to determine the correct interpreter. If you run `bash myscript' or `sh myscript' you allready are just running the interpreter with your scriptname as an argument. The argument tells the interpreter which file to run. The first line starts with a # so it's comment and ignored.

---

### Post by CryptKeeper777 on 2011-08-28
> **ziekfiguur said:**
> The "#!/bin/bash" line only has an effect if you make your script executable and call it like ```
./myscript
``` When you do that the kernel doesn't know how to run the script and look at the first line to determine the correct interpreter. If you run `bash myscript' or `sh myscript' you allready are just running the interpreter with your scriptname as an argument. The argument tells the interpreter which file to run. The first line starts with a # so it's comment and ignored.
Alright, thanks for clearing that up!

---

