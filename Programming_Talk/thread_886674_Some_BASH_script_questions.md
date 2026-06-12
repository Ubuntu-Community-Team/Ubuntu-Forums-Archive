---
title: "Some BASH script questions"
date: 2008-08-11
forum: Programming Talk
---

### Post by Craigy90 on 2008-08-11
Hello,

Recently, I have been trying to write scripts to take care of tasks that I perform frequently. One of these tasks is updating all of the subversion repository checkouts that I watch. Here is an example of what I do:

```

echo BLENDER
cd ~/Blender/bf-blender/
svn up

```

which works in most cases.

However, I have run into a problem that I need to work around. In some repositories, I get the following error many times before the update works:

```

svn: Malformed network data


```

I looked around a bit, but did not find a solution to this besides updating repeatedly. So, what I thought I could/should do was to continually update until I no longer get the error message by watching for that string. Here is what it looks like now:

```

var=`svn up`
echo $var

while [ $var=="svn: Malformed network data" ]; do
        var=`svn up`
        echo $var
done

```

This seems to have the desired effect, but the command line output is ugly, to say the least:

```

svn: Malformed network data

svn: Malformed network data

svn: Malformed network data

svn: Malformed network data

svn: Malformed network data

svn: Malformed network data

svn: Malformed network data

U lib/exceptionhandler/exceptionhandler.c U lib/framework/wzglobal.h Updated to revision 5796.
./subversion.sh: line 58: [: too many arguments

```

What I want it to look like, (it would also be OK if the error lines were included without the newline after each one):

```

U lib/exceptionhandler/exceptionhandler.c
U lib/framework/wzglobal.h
Updated to revision 5796.

```

I want to fix this, but I also want to learn more about BASH and the CLI in the process. Also, if anyone knows about that subversion error, that would be helpful too. I would still want to know about handling text output from programs run from scripts like this.

Thanks in advance

---

### Post by caljohnsmith on 2008-08-11
Maybe I'm misunderstanding you, but if the CLI output is "ugly", why do you have the "echo $var" in the loop? Do you want it to output that error every time svn tries, or no? :) What exactly would you like it to do instead?

---

### Post by Craigy90 on 2008-08-11
Thanks for the response.

The reason I put echo $var in, is so that it will (hopefully) output the correct subversion. I store the output of `svn up` in a variable so that I can test to see if it is the error that I am trying to avoid.

What I would like it to do, is output each time it tries, and give the error if it occurs. Instead of including the extra line each time with the error message, I want one error per line.

Once it gets through and subversion is correctly updating, I want it to print the output as the program itself normally does. Also, I would like to not have the "too many arguments" error, which is most likely a result of my lack of knowledge of bash. :)

I know you can save error output and normal output to different files, but can you run a program and then determine if an output is one or the other and then take appropriate action?

I am very inexperienced with this sort of thing, but I would like to learn the correct way to approach this kind of problem.

---

### Post by unutbu on 2008-08-11
Try 
```

var=$(svn up)

while [[ "$var" == "svn: Malformed network data" ]] ; do
        var=$(svn up)
done
echo "$var"

```

The reason you are getting this error
> 
./subversion.sh: line 58: [: too many arguments


is because $var in
"[ $var=="svn: Malformed network data" ]"
is getting expanded into many arguments since $var contains a space. So the test has too many arguments and is not really testing what you want properly.

The double-bracket notation is a bashism -- make sure your script begins with 
#!/bin/bash, not #!/bin/sh, since by default Ubuntu links /bin/sh to /bin/dash, rather than /bin/bash.

[http://tldp.org/LDP/abs/html/testconstructs.html#DBLBRACKETS:](http://tldp.org/LDP/abs/html/testconstructs.html#DBLBRACKETS:)
> 
The [[ ]] construct is the more versatile Bash version of [ ]...
No filename expansion or word splitting takes place between [[ and ]], but there is parameter expansion and command substitution.


---

### Post by Craigy90 on 2008-08-11
Thank you very much unutbu, that is just what I wanted!

Now let me try to understand how the syntax changed:

[LIST]
[*]var=$(svn up) is a newer way to do `svn up`
[*]I do not want it to print the errors, so don't have an echo before or during the loop
[*]Using double brackets makes the condition be evaluated literally
[*]Putting quotes around $var retains the newlines properly
[/LIST]

Thanks again, you were quite helpful. :)

---

