---
title: "ksh vs bash: setting variable in piped loops are lost"
date: 2006-12-03
forum: Programming Talk
---

### Post by Georges on 2006-12-03
I'm a long time unix (not linux) programmer, mainly shell scripts.
Unix does not know about bash, but rather ksh or sh.

So I often build stuff like this:
```

n=0
du | sort -n | while read size dir
do
  if [ "$size" -gt 100000 ]
  then
    n=$((n+1))
  fi
done
echo "Found $n too big files"

```
the question is **not** how to reformulate this differently using awk or perl.
The question is:

in ksh this script returns the correct value
in bash it always returns 0

This is because in ksh the last command in the pipe runs in the current process, whereas in bash the first command runs in the current proces. Result: the modified variables are lost.

I'm still puzzled that his is the case and that nobody really cares about.
Maybe I'm missing the point and there is some simple environment variable or other setting to change to enable ksh compatible behaviour.

Georges

---

### Post by mssever on 2006-12-03
> **Georges said:**
> I'm a long time unix (not linux) programmer, mainly shell scripts.
Unix does not know about bash, but rather ksh or sh.

So I often build stuff like this:
```

n=0
du | sort -n | while read size dir
do
  if [ "$size" -gt 100000 ]
  then
    n=$((n+1))
  fi
done
echo "Found $n too big files"

```the question is **not** how to reformulate this differently using awk or perl.
The question is:

in ksh this script returns the correct value
in bash it always returns 0

This is because in ksh the last command in the pipe runs in the current process, whereas in bash the first command runs in the current proces. Result: the modified variables are lost.

I'm still puzzled that his is the case and that nobody really cares about.
Maybe I'm missing the point and there is some simple environment variable or other setting to change to enable ksh compatible behaviour.

Georges

I guess that's something I've never really tried before--maybe because I've always used bash. I don't think that the bash devs care a whole lot about ksh, but I understand that zsh is nearly 100% compatible with ksh--plus a bunch of added features. You might be interested in it. It's available from the main repo. I haven't used it much, but then, bash does everything I need...

I suppose a bash kludge could be to use tmp files rather than a pipeline, but that isn't very elegant.

---

### Post by Georges on 2006-12-04
yes, "apt-get install ksh" is a solution too.

So you never use longer pipe constructs with loops etc?
That's the real power of shell programming, else one could as well use perl.

zsh also behaves correctly.

Only bash is different. The developers probably think they can reinvent the wheel in square form. Do you think there is any chance that a bug report will help?

---

### Post by Arndt on 2006-12-04
> **Georges said:**
> yes, "apt-get install ksh" is a solution too.

So you never use longer pipe constructs with loops etc?
That's the real power of shell programming, else one could as well use perl.

zsh also behaves correctly.

Only bash is different. The developers probably think they can reinvent the wheel in square form. Do you think there is any chance that a bug report will help?

Googling for "bash pipe subprocesses order" shows that the question has been asked before, but I couldn't find what the bash developers' official stand is.

---

### Post by malagant on 2008-10-13
I know this is a dead thread but I wanted to add something in case someone comes looking at this for a solution.  My thanks as always to the mksh team.  The solution involves (m)ksh co-processes.  Sounds like you may be able to do something similar with bash using named pipe pairs (one for read, one for write) if you do a little research in that area.

This works in mksh 35b:

```
n=0
du | sort -n |& 
while read -p size dir
 
do
  if [ "$size" -gt 1000 ]
  then
    n=$((n+1))
  fi
done
echo "Found $n too big files"

```

Basically this is straight from the mksh man page.  mksh is the successor to pdksh and several times smaller and faster than bash or zsh.  Think of it as a step up from dash at almost 100% POSIX compliance.  If you come from a Solaris, HP-UX or AIX shop and are used to ksh but miss the nice touches of the newer shells then you should give mksh a try.  As a bonus it is UTF aware (zsh isn't nor is bash without add-ons, I believe) and is also actively being developed.

---

### Post by Georges on 2008-10-13
that's like a kludge with temporary files we mentioned earlier.
And there are no co-processes in bash either.
How can this be the default shell in linux. It lacks several great inventions which make unix stand out.

Thanks for the hint on mksh, I will give it a try (setting it as default shell).

Georges

---

### Post by mirabilos on 2008-11-12
> **malagant said:**
> My thanks as always to the mksh team.

That would be me ;) thanks.

> **malagant said:**
> ```
du | sort -n |&
```

Basically this is straight from the mksh man page.

Actually, in your case, this would be better:

```
(du | sort -n) |&
```

I seem to recall, though, that these parenthes&#275;s are implicit in recent versions of mksh. (These also build on a fair larger number of platforms &#8211; ULTRIX, OSF/1, QNX, &#8230; &#8211; and with much more compilers than just gcc.)

---

### Post by eightmillion on 2008-11-12
I just spent 15 minutes trying to do this in pure bash before realizing that this thread is nearly 2 years old.:lolflag: Anyway, here's what I came up with. It's not pretty, but it works.

```

#!/bin/bash
n=0;a=0;x=0
for line in `du | sort -n`;do
if [ $line -eq $line 2> /dev/null ];then
 size[$n]=$line
 n=$(($n+1))
fi
done
while [ $x -lt ${#size[*]} ];do
  if [ ${size[$x]} -gt 100000 ];then
    a=$(($a+1))
  fi
  x=$(($x+1))
done
echo "Found $a too big files"
exit

```

---

### Post by Cracauer on 2008-11-13
Unfortunately bash is plain and simply correct when it comes to bourne shell script according to POSIX. You got the pipe, you are in a child process and nothing you do influences the parent process.

This is really annoying since it pretty much disables all sane ways to deal with filenames that contain any number of wired characters, sequences of multiple spaces one after another etc.

You never can use
find . ... | while read foo ; echo $foo ; do

Nor can you use 
find . -print0 | xargs -0 ...
invoking anything under the script's control that would allow you to count.

The only way to make use of this in the loop solution is to return everything you want for status by echoing them and putting the whole loop into $(...). If you need stdout for other purposes inside the loop you gotta start placing a bunch of bloddy `1>&3) | ... 3>&1 | grep`.

---

### Post by geirha on 2008-11-13
I guess the prettiest way to handle it in bash would be something like this:
```

#!/bin/bash
exec 3< <(du | sort -n)  

n=0
while read size dir; do
  [ $size -gt 1000 ] && ((n++))
done <&3
exec 3<&-

echo "Found $n too big files"

```

---

### Post by mirabilos on 2008-12-15
Heh, these GNU bash examples are probably one more
reason to use mksh. Here&#8217;s how a native Korn shell
programmer would do it:

```

(du | sort -nr) |&
n=0
while read -p size dir; do
        # we sort so that the largest numbers are up front
        (( size > 1000 )) || break
        let n++
done
print Found $n too big files

```

If you don&#8217;t want the optimisation, but something
closer to the original code:

```

(du | sort -n) |&
n=0
while read -p size dir; do
        (( size > 1000 )) && let n++
done
print Found $n too big files

```

This would also work (C like):

```

(du | sort -n) |&
n=0
while read -p size dir; do
        (( n += size > 1000 ? 1 : 0 ))
done
print Found $n too big files

```

---

### Post by Georges on 2008-12-15
lol, you replied with a complicated ksh script to implement a simple ksh script I mentioned in the original post.

Which shows that a really well programmed shells should run the last process of a pipe in the current process and not the first.

Will ubuntu be the first linux to dump bash for zsh?
Where can we go vote for that?

---

### Post by mssever on 2008-12-15
> **Georges said:**
> Will ubuntu be the first linux to dump bash for zsh?
Where can we go vote for that?
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Cracauer on 2008-12-15
zsh as default shell? You gotta be kidding me?

I agree that the "full pipe no shared memory" behavior is annoying, but it is correct according to Posix. The only problem I can see with bash is that it doesn't even attempt to have a mode that is restricted to Posix /bin/sh capabilities. But what it does it does very well.

---

### Post by Ajaxelitus on 2009-01-02
A somewhat cleaner way to preserve bash environment variables
is to use process substitution in lieu of pipes:

   name=FAILED
   while read new; do
      name=$new
   done < <(/bin/echo OK)

See the 'Process Substitution' section of bash(1).

---

### Post by mirabilos on 2009-03-26
> **Georges said:**
> lol, you replied with a complicated ksh script to implement a simple ksh script I mentioned in the original post.

I don&#8217;t think it&#8217;s too complicated, but I showed several
ways of optimising them and using a style of coding more
native to the Korn shell.

> **Georges said:**
> Will ubuntu be the first linux to dump bash for zsh?
Where can we go vote for that?

They use dash, not GNU bash. Forgotten already?
If you want zsh&#8230; grml exists.

---

### Post by mssever on 2009-03-28
> **mirabilos said:**
> They use dash, not GNU bash. Forgotten already?
Actually, the default Ubuntu shell *is* Bash. Ubuntu uses Dash for /bin/sh, since Bash doesn't behave properly when it's invoked as /bin/sh, but that means nothing as far as the default shell goes.

---

### Post by marco.caminati on 2009-11-10
Nice to renew this yearly thread tradition :)
The issue is faced in Advanced Bash-Scripting Guide, a must reference for bash:
> 
More generally spoken
(
: | x=x
# seems to start a subshell like
: | ( x=x )
# while
x=x < <(:)
# does not
)

So, the solution proposed by geirha would be the most natural one, given the will to stay in bash and the original example. I add to this that you don't need file descriptors (as hinted above by Ajaxelitus), and I don't see any reason to call sort, so this is my one-liner version:

```
n=0 ; while read size dir; do [ $size -gt 100000 ] && (( n++ )) ; done < <( du ); echo $n
```

But I don't like much this implementation, firstly because it sounds like undocumented ("seems to start..." is vague).

Secondly, to me shell scripting implies a different style than real coding. 
This could be seen as a matter of elegance, but to me it hides  the essence of shell scripting, which has that nice feeling of finding tasty, less natural, alternative implementation, possibly compact and unoptimized. Tipically, this implies avoiding loops in favour of piping, redirections, etc..., which are the inherent tools of shell scripting.

So, here's a totally different approach:
 ```
n=$(( $((du ; echo 100000)| sort -n |sed -n -e "/^100000$/,$ p" | wc -l) - 1 ))
```

I think this approach shall mitigate the issue of giving bash a ksh-like behaviour, in favor of sticking with posix specifications.
Cheers,
Marco.

---

### Post by dearvoid on 2011-11-03
A few more years later, bash-4.2 added a new shopt option 'lastpipe' which runs the last command of a pipeline in the current shell context. But the lastpipe option has no effect if job control is enabled, which is usually true for an interactive shell.

---

### Post by defdefred on 2012-06-01
You need to add parenthesis to make it works.

```
du | [SIZE=4]**(**[/SIZE] while read size dir
do
    if [ "$size" -gt 10000 ]
    then
        n=$((n+1))
    fi
done
echo "Found $n too big files" [SIZE=4]**)**[/SIZE]

```

But I agree, that it is a pain that bash is forking a subshell...

---

### Post by defdefred on 2012-06-01
Newer bash 4 have a new shopt option :

**lastpipe**

   	 		Option:  lastpipe  Since:  4.2-alpha   	 	 		Shell mode:  all  Default: off   	 
   If set, **and job control is not active**, the shell runs the last command of a pipeline not executed in the background in the current shell environment.

---

### Post by Arndt on 2012-06-01
> **defdefred said:**
> Newer bash 4 have a new shopt option :

**lastpipe**

   	 		Option:  lastpipe  Since:  4.2-alpha   	 	 		Shell mode:  all  Default: off   	 
   If set, **and job control is not active**, the shell runs the last command of a pipeline not executed in the background in the current shell environment.

Someone said that seven months ago.

---

