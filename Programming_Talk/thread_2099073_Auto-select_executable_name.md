---
title: "Auto-select executable name"
date: 2012-12-28
forum: Programming Talk
---

### Post by Myoldmopar on 2012-12-28
Greetings, I'll keep it brief:

1. I build a program from source routinely as it is updated.  The result of the build is a file that is named 
   <program>_<version or build number>.jar
2. I have a python app that calls this program

The python app shouldn't rely on a specific executable name since it changes with each version/build (roughly daily).  Right now, what I have is a bash script in my PATH that does this:

    #!/bin/bash
    cd <bin directory>
    for file in *.jar; do
        java -jar $file
    done

This works fine for me, since I know there will be one and only one jar file there, but I am curious if there is an obvious and more robust solution.

I do realize there are two options that relate to modifying the build:

1. Modify the build scripts to not put the version number, or
2. After the build, create a link that is always named the same thing

These are good solutions, but this question has less to do with my example, and more to do with the problem in general.

Thanks!!

---

### Post by TheFu on 2012-12-28
I think your solutions are reasonable for the problem. If the builds happen daily, you could modify the build-number into a calendar date (yyyy.mm.dd) and use that to call the exact file (.jar) as you like.

Still, your current solution might work better if it created a list of .jar files and only ran the one with the largest build-number inside. that way you could have multiple .jar files in the same directory.

---

### Post by Myoldmopar on 2012-12-28
@TheFu:

Thanks for the reply!  I think I might have been a little unclear in trying to be extra-brief.

What I am really curious about is whether there is a simpler way to call the unknown-named executable.  I'll try to one-liner it:

[INDENT]If I have a directory with a single executable file, but I don't know the name of it, is there a better way than the for loop I listed in the original post?[/INDENT]

It's definitely not a big deal, especially for my specific example, but I just get the feeling maybe there's something I can learn here.

Thanks!

---

### Post by TheFu on 2012-12-28
Finding if a file is executable isn't hard ... I'd use perl and the stat() function, but if you already **know** there is only 1 .jar file, I wouldn't bother.  Using the loop, like you do, is fine and plenty efficient.  Perhaps bash has a built-in function for file stat()?  The "Advanced Bash Scripting Guide" might help.

---

### Post by Myoldmopar on 2012-12-28
Thanks, I think it's a moot point by now.  I can use the -x argument in an 'if' structure in bash to check for executable, but I'm just calling java with a jar file anyway.  I'll go ahead and mark it solved since I think the for loop may be as robust as possible for this situation.

---

### Post by TheFu on 2012-12-28
> **Myoldmopar said:**
> Thanks, I think it's a moot point by now.  I can use the -x argument in an 'if' structure in bash to check for executable, but I'm just calling java with a jar file anyway.  I'll go ahead and mark it solved since I think the for loop may be as robust as possible for this situation.

I feel dumb.  I know about the -x, but** didn't think of it.**  I'm always using -z or -f when working with data files.  Also, the .jar file doesn't NEED to be marked executable for it to run. It is really just data input into the `java` program after all.

---

