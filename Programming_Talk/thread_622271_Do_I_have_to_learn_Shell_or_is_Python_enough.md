---
title: "Do I have to learn Shell or is Python enough?"
date: 2007-11-24
forum: Programming Talk
---

### Post by Majorix on 2007-11-24
I am a Linux (mainly Ubuntu) user trying to remember his knowledge of Python.

I have heard it being said that Python is an eye-candy Shell.

Is this really true? Can I do everything the Shell can do with Python? Or do I also have to learn the Shell?

If your answer to the second question above is yes, then do you have a link to a programmer's guide to shell scripting? I am currently reading Dive Into Python, which is mainly a programmer's guide to Python, and I like the way the author teaches the language to older programmers.

Thanks.

---

### Post by LaRoza on 2007-11-24
For me, Python replaces the shell.

Python can be used to make large applications, and can be used for short scripts. It versitility and power are amazing.

I have found no reason to learn more than the basics of the shell.

For more Python resources (in case you only have DiP), my wiki might help, it has information on GUI libraries among others. For shell, [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

### Post by Sayers on 2007-11-24
With .sh files, you will sub-learn them over your linux journeys. The more you learn about linux commands the better shell files become.

---

### Post by Majorix on 2007-11-24
@LaRoza
So you feel no need for the Shell? Not even for scheduling tasks, upgrades etc?

I don't know even the basics of the Shell. Do I have to learn some?

The guide you linked me to is a "beginner's" guide, which tend to be boring for those who know programming terms and maybe other programming languages.

---

### Post by geirha on 2007-11-24
They can basicly do the same things, but they do it in different ways. Sometimes 10 lines of python can be done with one line of bash and vice versa. Learn both.

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> @LaRoza
So you feel no need for the Shell? Not even for scheduling tasks, upgrades etc?

I don't know even the basics of the Shell. Do I have to learn some?

The guide you linked me to is a "beginner's" guide, which tend to be boring for those who know programming terms and maybe other programming languages.

I use the shell, but do not use shell scripts.

You can get a manual for the commands with 'man <commandName>"

Actually, go here: [http://www.ss64.com/bash/](http://www.ss64.com/bash/) 

I don't use the shell for programming, just for simple tasks. 

I usually do the following through the command line:

* Install programs
* Compile Programs and run them
* Search for things
* Editing (Vim ftw)
* List directories and files
* Delete things in bulk (rm *.jpg)
* and a few other things

---

### Post by LaRoza on 2007-11-24
This may help, rather than the long list:

[http://oat.tao.ca/book/view/185](http://oat.tao.ca/book/view/185)

---

### Post by smartbei on 2007-11-24
I second LaRoza with my reply; I have never really learned shell scripting, since I learned Python instead and it filled the same hole. There are some short scripts that are easier to do in the Shell, but in my experience the gained convenience is not worth the time spent learning a new language.

@Majorix - I am not sure what you mean by "scheduling tasks" or "upgrading". I think you misunderstood what LaRoza was saying - he does use the shell as a tool, but for scripting purposes chooses Python. That is, he still uses [for example] "sudo aptitude install <program>" from the terminal.

EDIT: LaRoza beat me by several seconds :p.

---

### Post by Majorix on 2007-11-24
I was asking about if he used scheduled upgrading through a script, and if he did, what language he used. There is a thread in this section of the forums regarding that subject, and the OP there used shell to do it. I was wondering if that could be done with Python too. For your information, the thread lies here:
[http://ubuntuforums.org/showthread.php?t=622166](http://ubuntuforums.org/showthread.php?t=622166)

LaRoza, I do pretty much the same things you do on the terminal.

I think I explained myself in a wrong way. When I say Shell, I mean shell scripting. Sorry about the confusion.

---

### Post by CptPicard on 2007-11-24
It's very much a moot point for someone who is serious about computing. It is a bit like these n00b threads where they are all concerned about learning the "wrong" language as their first programming language, while the right answer is that you'll end up learning many during your education, be it formal or informal.

You can't really avoid learning bash as you go, it's just way too convenient to know, and the very basics such as pipes are enormously powerful... but whenever you start to doing "proper" programming, you need to move up, and that's where Python comes in.

My suggestion would be that you shouldn't sit down and explicitly "learn" bash, but just pick it up as you go and read scripts. It's relatively quick to hack up the little bash scripts you need on demand by reading a bash guide, and the big ones you're probably better of writing in Python.

EDIT: You should do your scheduled updates using cron and a small bash script to include the commands you run periodically...

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> 
LaRoza, I do pretty much the same things you do on the terminal.

I think I explained myself in a wrong way. When I say Shell, I mean shell scripting. Sorry about the confusion.

I use no shell scripts at the moment.

Python has modules for doing things that one could use shell commands. The os module has all of that ([http://docs.python.org/lib/os-file-dir.html](http://docs.python.org/lib/os-file-dir.html)). You can use os.system("SHELLCOMMAND") to execute the command if one wanted to do that.

So, you could use 
```

os.system("gcc main.c modules.c -llinkablelibrary -o program")

```

Instead of having the same command in a shell script.

I would use shell scripts, and can write them, if the need arose. Learning it (shell scripting) is just as easy as learning a simple programming language plus you have the power of the shell (pipes and such).

---

### Post by Majorix on 2007-11-24
Thanks for the input guys, you made me save time. I won't try to learn Shell, I will only follow/debug .sh files I get as installation scripts etc, and hopefully that will be enough knowledge about the Shell.

LaRoza, I knew about the os module, but couldn't think of it in this situation. I should hit my head against the wall for not doing so :D

Thanks again.

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> Thanks for the input guys, you made me save time. I won't try to learn Shell, I will only follow/debug .sh files I get as installation scripts etc, and hopefully that will be enough knowledge about the Shell.

LaRoza, I knew about the os module, but couldn't think of it in this situation. I should hit my head against the wall for not doing so :D

Thanks again.

Python seems to have modules for everything, and it is easy to forget about them.

---

### Post by Smygis on 2007-11-24
Python also have the commands module (*nix only). A nice wrapper around os.popen.

Works almost like os.system but returns output and exitstatus to python for futher processing.

---

### Post by LaRoza on 2007-11-24
> **Smygis said:**
> Python also have the commands module (*nix only). A nice wrapper around os.popen.


Python has modules for specific OS's, including Windows (COM and such). 

Don't use them for cross platform programming (scripting) obviously.

---

### Post by ghostdog74 on 2007-11-24
> **Majorix said:**
> Or do I also have to learn the Shell?

yes you do. The shell is the most basic tool you need to "talk" to your computers. Also if you are working in an environment where Python or any other higher languages are not available or cannot be installed and you have only the shell to work with, what are you going to do ?

---

### Post by LaRoza on 2007-11-24
> **ghostdog74 said:**
> yes you do. The shell is the most basic tool you need to "talk" to your computers. Also if you are working in an environment where Python or any other higher languages are not available or cannot be installed and you have only the shell to work with, what are you going to do ?

We found out the OP was refering to shell scripting, not the use of the shell commands, which the OP already uses.

---

### Post by Majorix on 2007-11-24
LaRoza is right, sorry again for the confusion.

But a UNIX-like system without python is not realistic. They all have it pre-installed.

---

### Post by slavik on 2007-11-24
> **LaRoza said:**
> For me, Python replaces the shell.

Python can be used to make large applications, and can be used for short scripts. It versitility and power are amazing.

I have found no reason to learn more than the basics of the shell.

For more Python resources (in case you only have DiP), my wiki might help, it has information on GUI libraries among others. For shell, [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

I feel the same way about Perl. Perl can replace the shell, but something are easier done with straight shell code.

Shell scripting is about linking up the tools in a right way. Perl/Python involve writing some features of the small tools.

Perl/Python - sledgehammer
SHELL scripting - hammer

would you use a sledgehammer to hammer in a nail? would you use it to break a concrete block?

simple example:
locate files that match a certain criteria and remove them.

Programming approach:
1. Get list of files
2. Get files from list that match the criteria
3. remove the files in the resulting list

SHELL code:
1. run find and make it print files that match the criteria, pipe into xargs 'rm'

---

### Post by ghostdog74 on 2007-11-24
> **Majorix said:**
> 
But a UNIX-like system without python is not realistic. They all have it pre-installed.
Where did you hear this from?

---

### Post by slavik on 2007-11-24
> **ghostdog74 said:**
> Where did you hear this from?

I think he meant Perl ;)

---

### Post by LaRoza on 2007-11-24
> **Majorix said:**
> LaRoza is right, sorry again for the confusion.

But a UNIX-like system without python is not realistic. They all have it pre-installed.

Some don't, but that is rather rare, if Python doesn't cut it, Perl will do it (it is slightly more widespread I imagine)

---

### Post by LaRoza on 2007-11-24
> **slavik said:**
> I think he meant Perl ;)

Python is mostly installed, but I would think Perl is slightly more widespread.

---

### Post by Anzan on 2007-11-25
Thanks, folks. I've found this all very useful.

---

