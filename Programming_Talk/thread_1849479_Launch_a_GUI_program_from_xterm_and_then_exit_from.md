---
title: "Launch a GUI program from xterm and then exit from it (from the terminal)"
date: 2011-09-24
forum: Programming Talk
---

### Post by insecure hyena on 2011-09-24
Hi guys here's my problem.
I need to open a terminal (xterm), execute an initial command (source "/path/...") and then launch a GUI application.
After that I want the terminal to close it self leaving only the GUI application open.
I presume that all this stuff could be done easily with a bash script but sincerely I don't want to create such a script. Indeed my objective is to create a sequence (it's essentially a sequence of command) of commands that can be called by a link in a menu.
Until now the principal problem is that the terminal don't want to close after launching the GUI app with nohup.
All the help is appreciated :).

---

### Post by papibe on 2011-09-24
If it all happens in the same machine, just adding an ampersand and the end of the command will do the trick. For example, in a terminal you could do:
```
$ nautilus &
```
(The $ represents the command prompt).
And then close the terminal. The file manager Nautilus will keep running.

Now, if you are trying to launch a GUI application, why not make the link to open it directly instead of running a terminal that calls the app?

Just some thoughts,
Regards.

---

### Post by ajgreeny on 2011-09-24
And to save the extra step, or sort of save, at least ```
nautilus & exit
``` will close the terminal without you doing it.

Not necessary, I agree, but it is useful to know and understand such things.

---

### Post by lykwydchykyn on 2011-09-24
You might need to launch the command like this:
```

command &disown

```

The ampersand launches it in the background like others have said, but adding the "disown" completely detaches it from the launching session.

---

### Post by insecure hyena on 2011-09-25
Thanks guys for all your responses!
However I should say that I've tried all your suggestions but none of them helped me getting what I want.
Here I'll explain it in a clearer way.
I have a GUI program that normally must be started from the terminal (in a specified path every time different on the base of the situation) after running the command *source "/path/to/a/file"*. After running this command the GUI program can be called. Now what I want is to automate this procedure and make a link to start this dammed GUI program.
After I think about it I'm now convinced that it's better to create a bash script and so I put it down the first lines but here the first problem:
after I ask to specify the path from where to run the GUI app I need to run the *source* command and the result is:
source: not found
Besides this problem I also don't know how to evaluate the correctness of the path (i.e. the path really exists).

P.S: sorry if I've somehow changed the topic of the thread but I realized that's a better way to put it down a script rather to append all the stuff I need to do on a line only a few hour ago.

---

### Post by ajgreeny on 2011-09-25
I'm still not sure I understand;  do you mean the path to the gui executable changes each time it is run?

If so it may be possible to use a script which starts by using the **find** command and then runs whatever executable is found.

Or maybe I've still got it all wrong.

---

### Post by insecure hyena on 2011-09-25
Sorry it's my fault...as all you could note my English is quite poor and besides that I'm not the kind of person who can express what he had in his mind in a clear way.
However you get it wrong...the path I'm talking about in my previous post is not the one referred to the GUI application but the path FROM which the GUI application must be called. As mentioned in my previous post this damned GUI application must be started from the command line (from a terminal)...and in particular from a path that could be every time different. But that's not the problem...what I can't do is to execute the command *source "/a/fixed/path/not/the/one/that/change/from/situation/to/situation"* from my little bash script.

P.S: let me apologize for my lack of clarity and let me say thank you for your interest.

---

### Post by ajgreeny on 2011-09-25
You now say > "what I can't do is to execute the command *source "/a/fixed/path/not/the/one/that/change/from/situation/to/situation"* from my little bash script." Originally you said you did not want to use a script, but I assume you now have written one, so can we please see it if full as that may make the problem clearer.

---

### Post by insecure hyena on 2011-09-25
Ok here's the script:

```

#!/bin/bash

echo Specify the root path of the project you want to analyze:
read PATH
echo $PATH
#Here's the problem
source /opt/program-tools/program-kshrc
#Before this cd I would to check if the path exists...however I #don't know how to do it...
cd $PATH
#Execute the damned GUI Program
GUI Program


```

Hoping it's more clear now

---

### Post by lykwydchykyn on 2011-09-25
Not sure why source wouldn't work; is the argument a file or directory?  

to check if the path exists, you can do:
```


if [ -d $PATH ]; then
cd $PATH
fi


```

---

### Post by insecure hyena on 2011-09-26
The PATH is a directory...however I'm now facing another problem...we can say more GUI based XD.
However thank you very much for the intervention, I'll try what you suggested as soon as possible ;).

---

### Post by lykwydchykyn on 2011-09-26
> **insecure hyena said:**
> The PATH is a directory...however I'm now facing another problem...we can say more GUI based XD.
However thank you very much for the intervention, I'll try what you suggested as soon as possible ;).

I'm pretty sure "source" only works on files.  What exactly is sourcing the directory supposed to accomplish?

---

### Post by insecure hyena on 2011-09-26
Yes of course "source" works on files. Indeed the PATH I'm talking about is not the one pointing to the file "program-kshrc" but the PATH from which the GUI Program should be launched. Again this damned GUI Program should be launched from the terminal and so obviously from a path...this path is different each time and should be specified by the user...this path is the one represented by the variable PATH.

---

### Post by lykwydchykyn on 2011-09-26
> **insecure hyena said:**
> Yes of course "source" works on files. Indeed the PATH I'm talking about is not the one pointing to the file "program-kshrc" but the PATH from which the GUI Program should be launched. Again this damned GUI Program should be launched from the terminal and so obviously from a path...this path is different each time and should be specified by the user...this path is the one represented by the variable PATH.

Ok earlier you said this was the problem:
```

source /opt/program-tools/program-kshrc

```

I was asking if program-kshrc was a file or directory, so you're saying it's a file.  

Does that line run from the terminal just fine?

---

### Post by insecure hyena on 2011-09-26
Ok the PATH thing comes out from your suggestion:

```

if [ -d $PATH ]; then cd $PATH fi
```

Besides that, the principal problem is that the "source" command runs fine from the terminal but not from the script.

---

### Post by jwbrase on 2011-09-27
I think your problem is that PATH is a variable name already used by the shell. It contains a list of directories that the shell looks through when you execute a command that isn't built into the shell. So you're replacing this list with your project directory. When the script then sources the file you're trying to source, if it runs into any commands in that file that aren't shell-builtins, it tries to find the executables for those commands in your project directory (rather than in the normal system search path), doesn't find them there, and dies.

The solution is to use some other name than "PATH" for your project directory, such as "PROJPATH".

---

