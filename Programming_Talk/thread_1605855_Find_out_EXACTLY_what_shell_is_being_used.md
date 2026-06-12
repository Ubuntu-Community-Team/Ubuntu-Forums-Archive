---
title: "Find out EXACTLY what shell is being used"
date: 2010-10-25
forum: Programming Talk
---

### Post by for.i.am.root on 2010-10-25
Hi All:

So I was browsing the web today and came across a post where an individual was interested in finding out what shell they are using. There were several responses: echo $0, ps -p $$, echo $SHELL, however, none of them hit the mark (IMHO). If you were, for example, using Ubuntu 9.04 /bin/sh is a symlink to /bin/dash. If you ran echo $0 or ps -p $$ while using /bin/sh (/bin/dash) they would both report /bin/sh as the shell, not /bin/dash (the real interpretor). Furthermore if you ran echo $SHELL while using /bin/sh it would report /bin/bash (the login shell).

I wrote a little snippet of code to try to figure out what shell is actually being used, however, have hit a little bit of a thunker.

CODE:
var=`ps -p $$ | sed 's/[0-9]*//g' | sed -re 's/^.+\///g' | sed -re 's/://g' | sed -re 's/[A-Z]*//g' | sed -re 's/ //g'`
echo $var | grep "/" > /dev/null
if ! [ $? -eq 0 ]; then fullvar=`echo "/bin/"$var | sed -re 's/ //g'`; fi
readlink $fullvar > /dev/null
if ! [ $? -eq 0 ]
then echo $fullvar" is not a link. It must be the REAL shell interpretor."
else
fullvar=`readlink -f $fullvar` > /dev/null
var=`echo $var | sed -re 's/ //g'`
echo $fullvar" is the REAL shell interpretor, not /bin/"$var
fi

Obviously the first thing that stands out is how sloppy it is.
The second thing that stands out is that if the interpretor is outside of /bin the output would be wrong.
The third is using multiple symlinks to "fool" the script.

Any ideas on how to "fix" it?

Or better yet is there a one liner to figure out the current shell interpretor?

Thanks!

---

### Post by ArgusVision on 2010-10-25
Nothing against Mr "root",but since we're in the "Absolute Beginner Talk" Forum. I'd like to reiterate the warning not to run code/scripts unless you know what it does.

Again, let me say this is just a generic warning, not any implication against root.

EDIT: @ **for.i.am.root**, If I can make a suggestion, you might get better answers in the "Programming Talk" forum. (I think they cover scripting as well...) 
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by for.i.am.root on 2010-10-25
Hi Vision:

Based on the grammar and punctuation used, your post seems more like a rebuke than a suggestion.

For those that are interested:

ps - report a snapshot of the current process
sed - stream editor for filtering and transforming text
readlink - display value of a symbolic link

The rest is (hopefully) self explanatory.

If a mod finds that this post is better suited in the "Programming Talk" forum, I would have no objections to it being moved.

Thanks!

---

### Post by uRock on 2010-10-25
> **for.i.am.root said:**
> If a mod finds that this post is better suited in the "Programming Talk" forum, I would have no objections to it being moved.

Thanks!
Done!

---

### Post by ArgusVision on 2010-10-25
Please accept my apologies. It's dificult to express tone in type.
I simply think that you'll find more people with scripting and programming experience viewing your post there than in here.
 The use of quotes is to indicate that it is an exact name being used for that forum.

---

### Post by for.i.am.root on 2010-10-25
Hi uRock:

You Rock! Thanks!

Hi Vision:

Thanks for the suggestion!

---

### Post by cyberslayer on 2010-10-26
You might want to check out pwd -P.

---

### Post by saulgoode on 2010-10-26
> **for.i.am.root said:**
> Or better yet is there a one liner to figure out the current shell interpretor?
The following will print the full path wrapped in quotes.

```
stat -c%N $(which `ps -o comm= $$`)|awk -F' ' '{print $NF}'
```

Note that the $(command) construct is not available in the original Bourne shell (sh) -- if it is not supported in your shell(s) then you will have to separate things out a bit more (backticks can't be nested).

Additionally, 'stat' appears to only perform one level of dereferencing of symbolic links.

---

### Post by for.i.am.root on 2010-10-26
Hi saulgoode:

stat -c%N $(which `ps -o comm= $$`)|awk -F' ' '{print $NF}'

Thanks!

That worked really well.

jay@DARKSTAREEE:~$ stat -c%N $(which `ps -o comm= $$`)|awk -F' ' '{print $NF}'
`/bin/bash'
jay@DARKSTAREEE:~$ /bin/dash
$ stat -c%N $(which `ps -o comm= $$`)|awk -F' ' '{print $NF}'
`/bin/dash'
$ /bin/sh
sh-3.2$ stat -c%N $(which `ps -o comm= $$`)|awk -F' ' '{print $NF}'
`bash'
sh-3.2$ exit
exit
$ exit
exit
jay@DARKSTAREEE:~$ 

For those that are interested:

stat - display file or file system status
     -c  --format=FORMAT
use  the  specified FORMAT instead of the default; output a new&#8208;line after each use of FORMAT
     %N
Quoted file name with dereference if symbolic link

---

### Post by spjackson on 2010-10-26
> **for.i.am.root said:**
> Hi saulgoode:

stat -c%N $(which `ps -o comm= $$`)|awk -F' ' '{print $NF}'

Thanks!

That worked really well.

We have a bit of chicken and egg situation here. The syntax works for those shells for which it works, and doesn't work for other shells where this is the wrong syntax, csh for instance.

Also, what if /bin/sh was a hard link to dash? It isn't, but what if it was? ( /bin/uncompress and /bin/gunzip are hard links to the same file for example, so it's conceivable that shells could do this in a future release.)

Why doesn't using shebang solve the problem and tell you everything you need to know?

---

### Post by for.i.am.root on 2010-10-27
Hi spjackson:

Are you referencing THE shebang or an app called shebang? The only reason I ask is because specifying the shell interpretor would change the end result. If I specify /bin/bash the script would return /bin/bash every time. Even if the user is running /bin/sh, /bin/nash, /bin/dash, etc.

Unless you are suggesting a script to search for running interpretors and then eliminate the interpretor specified by shebang if it's not the only one running.

Maybe an easier method would be modifying the one liner by saul into a script also including readlink to dereference links to their destination.

Although you rose an interesting point. Hard links can't be followed by readlink. We do have one option though. If you cat a REAL shell interpretor you get unreadable output, but if you cat a hardlink you get text.

jay@DARKSTAREEE:~$ cat /bin/uncompress
#!/bin/bash
PATH=${GZIP_BINDIR-'/bin'}:$PATH
exec gzip -d "$@"
jay@DARKSTAREEE:~$ cat /bin/bash
^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@&#65533;&#65533;^E^H4^@^@^@p^[^K^@^@^@^@^@4^@ ^@$
^@&#65533;&#723;
^@^E^@^@^@^@^P^@^@^A^@^@^@&#65533;&#932;
^@&#65533;^^O^H&#65533;^^O^H&#65533;K^@^@&#65533;&#65533;^@^@^F^@^@^@^@^P^@^@^B^@^@^@^P&#979;

The above will continue on for a while, however, I am sure everybody gets what I mean.

---

### Post by CharlesA on 2010-10-27
They are refering to the #!/path/to/interpreter shebang.

A hardlink is just a link that points to that file.

Also, you shouldn't cat binary files.

---

### Post by for.i.am.root on 2010-10-27
Hi Charles:

I assumed he meant THE shebang, however, how would that help me to determine the CURRENT interpretor rather than the interpretor that I specify.

> 
Are you referencing THE shebang or an app called shebang? The only reason I ask is because specifying the shell interpretor would change the end result. If I specify /bin/bash the script would return /bin/bash every time. Even if the user is running /bin/sh, /bin/nash, /bin/dash, etc.

Unless you are suggesting a script to search for running interpretors and then eliminate the interpretor specified by shebang if it's not the only one running.


I know I "shouldn't" cat binary files, however, it's a very simple test to determine if a file is binary or not.

---

### Post by CharlesA on 2010-10-27
> **for.i.am.root said:**
> Hi Charles:

I assumed he meant THE shebang, however, how would that help me to determine the CURRENT interpretor rather than the interpretor that I specify.


Yep. That wouldn't tell you what shell you are currently using.


> I know I "shouldn't" cat binary files, however, it's a very simple test to determine if a file is binary or not.

True. Aren't there better way to tell if something is executable, like looking at permissions?

---

### Post by for.i.am.root on 2010-10-27
Hi Charles:

Quote:

> 
True. Aren't there better way to tell if something is executable, like looking at permissions? 


Wouldn't work. If the link weren't executable you wouldn't be able to use it.

i.e.

jay@DARKSTAREEE:~$ ls -l /bin | grep "uncompress" # /bin/uncompress is a hard link
-rwxr-xr-x 2 root root      63 2010-01-19 16:47 uncompress
jay@DARKSTAREEE:~$ ls -l /bin | grep "sh" # /bin/sh is a symlink to /bin/bash
-rwxr-xr-x 1 root root  729040 2009-03-02 09:22 bash
-rwxr-xr-x 1 root root   87924 2008-11-05 02:51 dash
lrwxrwxrwx 1 root root       4 2010-04-13 21:37 rbash -> bash
lrwxrwxrwx 1 root root       4 2010-10-25 14:43 sh -> bash
jay@DARKSTAREEE:~$ 

As you can see both symlinks and hard links are executable. I know there is a tool to find out wether or not a file is binary but I don't remember it or it's syntax. The only difference being symlinks are denoted by an l (ell)

jay@DARKSTAREEE:~$ ls -la /bin/ | grep ^l
lrwxrwxrwx  1 root root       6 2010-10-22 20:39 bzcmp -> bzdiff
lrwxrwxrwx  1 root root       6 2010-10-22 20:39 bzegrep -> bzgrep
lrwxrwxrwx  1 root root       6 2010-10-22 20:39 bzfgrep -> bzgrep
lrwxrwxrwx  1 root root       6 2010-10-22 20:39 bzless -> bzmore
lrwxrwxrwx  1 root root      20 2010-04-13 21:37 mt -> /etc/alternatives/mt
lrwxrwxrwx  1 root root      20 2010-04-13 21:37 nc -> /etc/alternatives/nc
lrwxrwxrwx  1 root root      24 2010-04-13 21:37 netcat -> /etc/alternatives/netcat
lrwxrwxrwx  1 root root       6 2010-04-13 21:37 open -> openvt
lrwxrwxrwx  1 root root      16 2010-04-13 21:37 pidof -> ../sbin/killall5
lrwxrwxrwx  1 root root       4 2010-04-13 21:37 rbash -> bash
lrwxrwxrwx  1 root root       4 2010-04-13 21:37 rnano -> nano
lrwxrwxrwx  1 root root       4 2010-10-25 14:43 sh -> bash
jay@DARKSTAREEE:~$ 

Thanks!

---

### Post by CharlesA on 2010-10-27
Interesting.

Thanks. :)

---

### Post by spjackson on 2010-10-27
> **for.i.am.root said:**
> 
I assumed he meant THE shebang, however, how would that help me to determine the CURRENT interpretor rather than the interpretor that I specify.

Yes I meant the shebang: the first line beginning with #!

If you simply run the script with ./myscript or similar, then that is the shell that you will get. From your other follow-up posts, I think that you are thinking of situations where the user does something like:
```

cat myscript.sh | /bin/some-random-shell
/bin/some-random-shell myscript

```I hadn't thought of that. Still, I think you are stuck because IF the user is going to do that, then they might choose /bin/csh as their random shell, or it might not even be a shell at all, they might try to shove it through an interpreter such as python.

For a subset of shells, i.e. those that support at least Posix sh syntax, then your suggestion might work, with some caveats. What are you trying to do with the information? Is it to quit with an error if the user has chosen the wrong shell?

How would you handle the situation where some user does:
```

cp /bin/bash $HOME/bin/dash
$HOME/bin/dash myscript

```Now the exe is called dash but it is really bash. I don't think that a bullet-proof solution is possible.

> 
I know I "shouldn't" cat binary files, however, it's a very simple test to determine if a file is binary or not.One way to do this is by inspecting the output of "file". A hard-link can be made to any sort of file, binary or text; it's coincidence that you've picked one that is text.

---

### Post by for.i.am.root on 2010-10-27
Hi spjackson:

Quote:
> 
One way to do this is by inspecting the output of "file". A hard-link can be made to any sort of file, binary or text; it's coincidence that you've picked one that is text.


I realized that after I posted that and did some more testing but I was hoping nobody would catch it. :)

file was what I was thinking of earlier (I just realized I misspelled whether earlier :/):

> 
I know there is a tool to find out wether or not a file is binary but I don't remember it or it's syntax.


I have used it before in a similar script, however, that was years ago.

One obvious (based on this thread) foreseeable need for such a script would be for determining syntax in a script. Although an easier method would be shebang bash.

I have no real use for such a "script" (at the moment) nor am I really planning on writing one (unless I figure out this quandary). Just had my interest piqued by a blog post I read pertaining to this topic and couldn't find a reliable solution through my own knowledge or google so I figured I would ask the experts (The cumulative knowledge of this board FAR surpasses that of ANY individual person.)

You do raise a very valid point with the renaming and moving of a shell. I haven't yet considered that possibility.

How is it there is no built in reliable identifier string? This is pretty wild to me. Until this point I assumed I was an idiot and missed something, however, it is looking like I may not be as naive as I initially suspected.

Thanks!

---

### Post by ArgusVision on 2010-10-27
Looks like a case of to many variables in the day to day usage.

---

### Post by for.i.am.root on 2010-10-27
Hi Argus:

I have to agree with you. The (potential) variables are endless when it comes to user(s) and individual systems.

On the other hand it (you would assume) *should* be a simple task to find out what (shell) interpretor is (currently) being used and which is the default.

There is also the point raised by spjackson, what if a user tries to shove it through a different (non shell) interpretor (/usr/bin/python for example)?

The phrase coined by Rich Cook comes to mind.....

Thanks!

---

### Post by ArgusVision on 2010-10-27
Which phrase would that be? (Or is it postable...) :)

---

### Post by for.i.am.root on 2010-10-27
Hi Argus:

This is my signature on another programming board I frequent:

"Programming today is a race between software engineers striving to build bigger and better idiot-proof programs, and the Universe trying to produce bigger and better idiots. So far, the Universe is winning."

Kind of sarcastic and demeaning, however, also true (to an extent). Some people do some VERY stupid stuff.

In one instance I had a signature that read:

"If you have tried EVERYTHING else and there is NO possible solution try (as a LAST resort) this: cd / && for file in `ls`; do sudo rm -fr $file; done"

Needless to say some noob got upset...

Thanks!

---

