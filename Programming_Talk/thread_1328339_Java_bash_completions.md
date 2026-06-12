---
title: "Java bash completions"
date: 2009-11-16
forum: Programming Talk
---

### Post by glitch83 on 2009-11-16
Well I'm pretty sure this was working in 9.04 and is now broken but I may be hallucinating. Anybody know how to install/restore the ability to do java bash completions in ubuntu?

I used to be able to do this: 
java com.ub<tab>
java com.ubuntu.<tab>

<options>

I'm like 99% sure that this was working in 9.04 when I was using openjdk. Can anybody help me restore this functionality? I tried to apt-get install bash-completion and it didn't work. On a little more investigation - it seems like there used to be a /etc/bash_completion.d/java file that doesn't exist or maybe it was all sourced into /etc/bash-completion now. I don't know, help?

~Nick

---

### Post by 0cton on 2009-11-16
AFAIK this is IDE dependent.
what IDE do you use?
or editor?

---

### Post by glitch83 on 2009-11-16
Hm. I had this working in bash (gnome-terminal).

And it usually bash-completed it by using the .class files and using a . separator instead of the / separator.

---

### Post by glitch83 on 2009-11-18
Still looking for an answer here - anybody know how to do this?

---

### Post by falconindy on 2009-11-18
/etc/bash_completion

have fun!

---

### Post by glitch83 on 2009-11-18
> **falconindy said:**
> /etc/bash_completion

have fun!

So does this mean I must write it? I was under the impression that Ubuntu had this built in and that perhaps my bash_completion file was overwritten? Maybe I just need to apt-get a special package that would modify my bash_completion file? 

Or has nobody had this work yet and I'm just hallucinating?

---

### Post by glitch83 on 2009-12-05
Well I finally got a chance to figure this out. In your /etc/bash_completions file, it looks like the FIND command changed a little bit in the new distribution and is throwing errors on mis ordered params. Since this error eats up the result, nothing comes out and the error is piped to /dev/null so it feels like nothing is installed since there is no output. This is a super hacky fix but it works: 

/etc/bash_completion::_java_classes()
```

		elif [ -d $i ]; then
			i=${i%/}
			# See bug #496828
			COMPREPLY=( "${COMPREPLY[@]}" $( find "$i"  -type f\
			-maxdepth 1 -path "$i/$cur*.class" 2> /dev/null | \
			grep -v "\\$" | sed -e "s|^$i/||" ) )
			# FIXME: if we have foo.class and foo/, the completion
			# returns "foo/"... how to give precedence to files
			# over directories?
		fi

```
should be: 
```

		elif [ -d $i ]; then
			i=${i%/}
			# See bug #496828
			COMPREPLY=( "${COMPREPLY[@]}" $( find "$i"  -type f\
			-path "$i/$cur*.class" 2> /dev/null | \
			grep -v "\\$" | sed -e "s|^$i/||" ) )
			# FIXME: if we have foo.class and foo/, the completion
			# returns "foo/"... how to give precedence to files
			# over directories?
		fi

```


Basically remove the -maxdepth 1 line in the find... 

So now it does a completion multiple levels down which I'm not too broken up with but I'd like the canonical fix at some point. I'll see if I can report this bug..

---

### Post by glitch83 on 2009-12-05
Furthur detail: when I looked up this bug, I came across this fix: 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=496828](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=496828)

Which seems to indicate the maxdepth is a bugfix and is new which validates my original hypothesis that its new

EDIT: Even better, there is an ubuntu bug related to this as well: [https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/492611](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/492611)

---

### Post by inzpektor on 2010-03-12
> **glitch83 said:**
> 
```

			# FIXME: if we have foo.class and foo/, the completion
			# returns "foo/"... how to give precedence to files
			# over directories?

```


To address this issue (which may be a little off-topic), how about if the name starts with a lower-case letter, assume that it's the directory, otherwise use the class-file.

---

