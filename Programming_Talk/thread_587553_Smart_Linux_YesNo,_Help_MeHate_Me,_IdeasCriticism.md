---
title: "Smart Linux: Yes/No, Help Me/Hate Me, Ideas/Criticism"
date: 2007-10-22
forum: Programming Talk
---

### Post by 1337455 10534 on 2007-10-22
> Sorry for the screenshot; but it's finally DONE!
Major design changes happened, and modVedu is a standalone command-line app now, but here it is!!!

##########################
[COLOR="Red"]**Vedu-BETA (pre 2.0) is finally DONE!#**[/COLOR]
##########################

Hey, I'm writing a program in Python that aims to make Linux easier, and **cross all distribution boundaries**. I don't really care if Automatix or EasyUbutnu has already done this, or already done that, since I tried both, and both resulted in me needing clean installs of Ubuntu.

As the thread title implies, feel free to do w/e to me on this thread (laugh, boo, etc.) but really I started it to get some constructive feedback and help. I'm going to finish this project, so don't tell me to stop or "Why are you doing this at all?". Also, I respectfully ask you to keep "Automatix [or EasyUbuntu] rules!" or "Nobody need this!" type comments to a minimum. Thank you.

Seeing as this thread is so long, if you have a suggestion, please just email or PM me (vminch@gmail.com).

Supported Package Managers;
Apt; debian, ubuntu, mint, pclinuxos
portage; Gentoo, Sabayon
Netpkg; Zenwalk
(base) RPM; pretty much all linuxes
Zypper; SUSE
YUM; Fedoras
URPMI; Mandriva

want another one on this (short) list? Name it, and I'll look into it!!!


NOTICE: This file is now far behind the severely unstable version of my code. It is still pretty unstable. It is still in wx (bleeding is in GTK) and this one has bugs in over 60% of its features.
Um, you cant mess with the GUI code (well, go ahead, but im moving to GTK), but the module code is undergoing enough structural changes so feel free to mess with it.

---

### Post by LaRoza on 2007-10-22
I don't think it is wise to import in a loop, do it at the beginning. Also, don't use "input", use raw_input and then convert the result to an integer, and use Python's exception handling. It might be better to use a GUI, like wxPython.

---

### Post by 1337455 10534 on 2007-10-22
[B][COLOR="Blue"]Jan 27, 2008 UPDATE;
The code has made humongous leaps since I first made this thread, it is now ready for heavy use and testing.
v1.3 is out.[/COLOR][/B]

---

### Post by LaRoza on 2007-10-22
<posting problem>

---

### Post by LaRoza on 2007-10-22
[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)


[php]
a = raw_input("What is your choice?[0,1-5]: ")
try:
    if int(a) == 1:
        print "A is 1"
    elif int(a) == 2:
        print "A is 2"
    elif 
        #etc
except(StandardError):
    print "Input not valid"
[/php]
Another possibility is just comparing strings, because it doesn't look like you are perform math on the input. I think that would be better.

---

### Post by slavik on 2007-10-23
I suggest the criticism of automatix for things to NOT do. :)

---

### Post by 1337455 10534 on 2007-10-23
Jan 3, 2008 UPDATE;
The code has made humongous leaps since I first made this thread, it is now ready for heavy use and testing.
v1.0 is out.

---

### Post by 1337455 10534 on 2007-10-23
Nvm: hitting enter during an "input" only kills teh script becuse there is no "elif [enter_number]" arguements..
How do you check if the user entered: "Enter"??
```

a = input("BLAH!: ")
# The User accidentally hit enter!
# My script assigns the value X to a

```
Anybody feel like solving for X :lolflag:?

---

### Post by Wybiral on 2007-10-23
I'm a pretty big Python advocate, but with all these system calls, why not just use a BASH script?

---

### Post by Acglaphotis on 2007-10-23
I dont think there is anything wrong with system calls. BTW Try using:

```

print '''
stuff you want to print
'''

```

Instead of multiple print statements

EDIT: when you hit enter to raw_input it returns ''. I think GUI should be your TOP priorities (besides from getting it to work), without GUI it won't *do* for its intended userbase.

---

### Post by Wybiral on 2007-10-23
> **Acglaphotis said:**
> I dont think there is anything wrong with system calls.

I'm not saying there's anything wrong, just that it would actually be cleaner in BASH since all (he | she)'s using is system/print/conditions.

---

### Post by Acglaphotis on 2007-10-23
> **Wybiral said:**
> I'm not saying there's anything wrong, just that it would actually be cleaner in BASH since all (he | she)'s using is system/print/conditions.

He said he is planning on implementing a GUI.:-P

---

### Post by LaRoza on 2007-10-23
> **1337455 10534 said:**
> Nvm: hitting enter during an "input" only kills teh script becuse there is no "elif [enter_number]" arguements..
How do you check if the user entered: "Enter"??


[php]

a = raw_input("Enter Your Name: ")

if a == "":
    print "No name?"
elif a == "LaRoza":
    print "Hi me"
else:
    print "Hi " + a

[/php]

---

### Post by 1337455 10534 on 2007-10-23
> **Wybiral said:**
> I'm a pretty big Python advocate, but with all these system calls, why not just use a BASH script?
Because I need it to be portable and I need to use easygui. Besides, all I do is not restricted to system(), I use many other Python-only things. :)

---

### Post by 1337455 10534 on 2007-10-23
> **LaRoza said:**
> ```

a = raw_input("Enter Your Name: ")
if a == "":
    print "No name?"

```

Grins!! Perfect!

---

### Post by Wybiral on 2007-10-23
> **1337455 10534 said:**
> Because I need it to be portable :). Believe me, I've been frustrated before with Python, but ultimately, it is the pwnz0r5 :lolfalg:.
Anyways, yes, I need python so that I can speak to rpm / pacman / (shells that aren't bash).

I don't think Python is frustrating, but if all you need are input / conditions / system commands then BASH makes more sense IMO because your code isn't littered with a bunch of "os.system".

---

### Post by LaRoza on 2007-10-23
> **Wybiral said:**
> ...your code isn't littered with a bunch of "os.system".

You can use: [php]from os import system[/php] to just be able to use "system()" by itself.

This looks like just a concept of what the goal is. For the input, you can use EasyGUI. It is not really a GUI for a program, but it may give you and idea of function for the program.

If you never used EasyGUI, my wiki has a link to it. You won't have to change your code much.

---

### Post by slavik on 2007-10-24
don't set up goals into a large checklist, set a goal, do it and then find the next goal.

Here's a question/concern, some of the things you want to do are easily doable by installing stuff from the repositories.

This is yet another difficult thing, not only do distros use a different package management architecture, but the packages they provide differ ... in ubuntu something might be a simple apt-get install away, while in fedora you might have to compile from source and in suse it might not be possible to get it workin at all (since there might be some outdated library and lots of dependency issues).

I would suggest writing your code so that it is easy to add modules that actually do the stuff. Try to get your goals to work on one distro and then port them to other distros one at a time.

---

### Post by Acglaphotis on 2007-10-24
It's been a long time since i used fedore, but if i remember right the command for installing rpms is:

```

rpm -i packagename.rpm

```

or

```

yum -y install package

```

Another thing i wanted to tell ya, yum is ***really*** different from apt. btw, i think you should stick with python *if, and only if* you want the project to get bigger. Bash wont do for a bigger project (GUI, portability (dash.bash etc)).

---

### Post by 1337455 10534 on 2007-10-24
Yum looks ok. I might just stick with rpm -i for install and yum for update/

---

### Post by 1337455 10534 on 2007-10-24
Announcing officially that Pacman (arch) will not be supported.
Can sudo be used in all Linuxes? I know it can in SUSE.

---

### Post by #Reistlehr- on 2007-10-24
rpm:

rpm -ivh = install verify and verbose
rpm -evh = remove verify verbose

the rpm command, that i know of, can't download a package like apt. Fedora used(uses) yum as their package manager.

All i can say is as aptitude users, we are so spoiled, but it's a good spoiled!

---

### Post by LaRoza on 2007-10-24
> **#Reistlehr- said:**
> 
All i can say is as aptitude users, we are so spoiled, but it's a good spoiled!

But I believe you can install it if you want.

---

### Post by Acglaphotis on 2007-10-24
I still think GUI should be your top prioritie. The userbase you seek is known for its hatred of the terminal. 

How are you planning to support KDE? It's not like you have to install stuff differently from one DE to another... or do you mean you are going to write it in both QT and GTK?

I almost forgot, i have suggestion, instead of having this code flowing freely, use functions:

```

def fiesty():
    dostuff # aka installing stuff
    if dostuff failed:
        return Somethingthatindicatesitfailed
    else:
        return Somethingthatindicatesthathisfunctionwassuccesfull 

```

---

### Post by 1337455 10534 on 2007-10-26
> **Acglaphotis said:**
> I still think GUI should be your top prioritie. The userbase you seek is known for its hatred of the terminal. 

How are you planning to support KDE? It's not like you have to install stuff differently from one DE to another... or do you mean you are going to write it in both QT and GTK?

I almost forgot, i have suggestion, instead of having this code flowing freely, use functions:

```

def fiesty():
    dostuff # aka installing stuff
    if dostuff failed:
        return Somethingthatindicatesitfailed
    else:
        return Somethingthatindicatesthathisfunctionwassuccesfull 

```

Well, I hope that my userbase wont mind a terminal for v0.1
:lolflag:!
Heh heh. Yes, I'm just hacking for right now...

---

### Post by Nekiruhs on 2007-10-26
> **1337455 10534 said:**
> Well, I hope that my userbase wont mind a terminal for v0.1. To explain,: pretend you're god. Would you make skin, and then shove an excretory system in there? Nope.
:lolflag:!
Heh heh. Yes, I'm just hacking for right now...
No, I would do both at the same time and not release my program until the GUI did most of the functions. Your userbase would rather sacrifice functionality for ease of use.

---

### Post by 1337455 10534 on 2007-10-26
*twitch* ah well

---

### Post by 1337455 10534 on 2007-10-27
Sorry for being snappy.. Learning EasyGUI and tk right now.

---

### Post by Acglaphotis on 2007-10-27
i want to say this before you anyone else say it:

GUI PROGRAMMING IS A PITA!

---

### Post by LaRoza on 2007-10-28
> **Acglaphotis said:**
> 
GUI PROGRAMMING IS A PITA!

Not really. If you understand what you are doing, and are using a decent language, it can be fun.

---

### Post by pmasiar on 2007-10-29
> **Acglaphotis said:**
> GUI PROGRAMMING IS A PITA!

Nobody answered it, so I have to :-)

Yes, GUI is PITA. But programs without a GUI are big PITA too, especially if you use that program only occasionally. So this attitude ("learn to use commadline, loser") is exactly what prevents Linux on every desktop, and I am really glad that ubuntu is changing that.

I love commandline - but for tasks I do daily. And for those, I use midnight commander anyway :-)

For task I to only occasionally, I much prefer nice GUI which guides me along the way, thank you very much. And I appreciate all those guys and gals who went through the PITA of GUI programming and create nice sleek easy to use GUI for me, so I can fix what I need and focus on **my** tasks, and not on babysitting Linux terminal commands. 

So wake up and smell the coffee: GUI is good! Pain is weakness leaving the body (of Linux code) :-)

---

### Post by 1337455 10534 on 2007-10-29
Heh, I agree on the prevention of the spread part. Personally, cmdline makes me feel smarter than that guy over there who is trying to find out why he has only 10 programs installed and 30GB harddrive space used with the disk defragmenter...

I prefer cmdline because it offeres me the sense of total control.
GUIs arent flexible... Everything has to be accounted for when you write it, soo, its hard to mix things up... Say you GUI a simple script to find disk space. After it finds the space, it asks you if you want to analyze space directories and certain files use etc.. Suppose you want to update your packages?? The only options are to continue or quit. There are endless thingsd you mite want to do rite after that... 

But GUIs are like a blankie at midnite around the campfire... They stop you from freezing, and toasting your marshmallows effectively as well.

---

### Post by CptPicard on 2007-10-29
The problem with GUIs is that trivial GUIs tend to be useless, as you don't really need three generic buttons in a window to replace a simple command line utility that has about as simple a user interface. Also, complex GUIs which do allow for flexibility and where graphical representation and direct manipulation of your data/process are a plus, are extremely difficult and work-intensive to program and thus tend to be bad, if they exist at all.

---

### Post by slavik on 2007-10-30
> **pmasiar said:**
> Nobody answered it, so I have to :-)

Yes, GUI is PITA. But programs without a GUI are big PITA too, especially if you use that program only occasionally. So this attitude ("learn to use commadline, loser") is exactly what prevents Linux on every desktop, and I am really glad that ubuntu is changing that.

I love commandline - but for tasks I do daily. And for those, I use midnight commander anyway :-)

For task I to only occasionally, I much prefer nice GUI which guides me along the way, thank you very much. And I appreciate all those guys and gals who went through the PITA of GUI programming and create nice sleek easy to use GUI for me, so I can fix what I need and focus on **my** tasks, and not on babysitting Linux terminal commands. 

So wake up and smell the coffee: GUI is good! Pain is weakness leaving the body (of Linux code) :-)
find me one decent GUI to wget that covers all of its features. ;)

---

### Post by pmasiar on 2007-10-30
> **slavik said:**
> find me one decent GUI to wget that covers all of its features. ;)

This is a BS argument. I never said all GUIs are always better.

Lets get different example: if I want repartition disk, I prefer GUI. If I want to compare two directories, I prefer MC. If I need just start development web server, I use commandline. 

Every tool has it's place. If you have only a hammer, everything looks as a nail. Oh I forgot, you have only perl, so everything looks like a regex! :-p

---

### Post by slavik on 2007-10-30
> **pmasiar said:**
> Every tool has it's place.

QFT. Your previous post didn't sound like it took the quoted piece as a truth. :)

---

### Post by evymetal on 2007-10-31
I understand how you expected to be flamed, but this could actually be kind of useful (to some) if you added a GUI (don't ask me, I'm not a GUI kina guy). Also think that "JRE" is too technical for people who would probably be using this kind of thing.

---

### Post by 1337455 10534 on 2007-10-31
> **evymetal said:**
> I understand how you expected to be flamed, but this could actually be kind of useful (to some) if you added a GUI (don't ask me, I'm not a GUI kina guy). Also think that "JRE" is too technical for people who would probably be using this kind of thing.
Good suggestion.
But, I just want to say, I'm writing this on a need-to-get-it-working basis, and honestly, I feel my UI takes LESS mental effort than a GUI from the user. Right now, you read a list, enter a number that sounds good to you, and just hit enter. With a GUI, it'd be slower, and the user would still have to enter a password (sudo) in the terminal. Plus, the user would have to use a mouse, which requires more advanced motor skill :)

---

### Post by LaRoza on 2007-10-31
> **1337455 10534 said:**
> Good suggestion.
But, I just want to say, I'm writing this on a need-to-get-it-working basis, and honestly, I feel my UI takes LESS mental effort than a GUI from the user. Right now, you read a list, enter a number that sounds good to you, and just hit enter. With a GUI, it'd be slower, and the user would still have to enter a password (sudo) in the terminal. Plus, the user would have to use a mouse, which requires more advanced motor skillz.

Using something like EasyGUI might be want you want. You can get user input with just a box, and present messages in boxes. Look in my wiki for GUI, including EasyGUI, with Python.

---

### Post by 1337455 10534 on 2007-11-04
I will do that.

---

### Post by 1337455 10534 on 2007-11-04
At the beginning of my program, whenever I run it in IDLE, it prompts me to add that uni encoding line to the beginning of my program, and now my script is interpreted much slower, though only in IDLE.
Why is that utf or whatever line needed?

Is it possible to get fancy text effects without a GUI?

---

### Post by 1337455 10534 on 2008-01-03
Jan 3, 2008 UPDATE;
[BUMP]
The code has made humongous leaps since I first made this thread, it is now ready for heavy use and testing.
v1.0 is out/

---

### Post by LaRoza on 2008-01-03
Please use normal fonts and colours.

See the last link my sig....

---

### Post by family on 2008-01-04
it seems ok

---

### Post by slavik on 2008-01-04
is my understanding that your code has to be run in a terminal and yet uses X to display the actual boxes correct?

---

### Post by 1337455 10534 on 2008-01-05
The script must be run from the terminal because I haven't found a way to give sudo the user's password to continue. i.e when the code dictates;
```

system("%sgeany%s" % (inst, sufx))

```
, if the user has selected APT, the terminal recieves;
> 
sudo apt-get install geany 

If you type 'sudo apt-get install geany ' in a terminal yourself (which is exactly what the os.system allows me to recreate), sudo prompts for the password...

---

### Post by mssever on 2008-02-01
> **1337455 10534 said:**
> The script must be run from the terminal because I haven't found a way to give sudo the user's password to continue.

If it's a GUI program, you should be using gksudo. That's what the Ubuntu tools do. Furthermore, if you create a .desktop file (so your program will appear on the menu--you should do this; it's relatively simple and adds a lot to the GUI usability), you can specify that it should be started as ```
gksudo 'yourprogram --args'
```

---

### Post by 1337455 10534 on 2008-02-01
I'll look into creating a .desktop file. I'm wrestling with getting handlers to be compatible with all my other code at the moment, but I'll get it working!
I love the gksu idea as well! It gets a nice password request screen up (like a professional Ubuntu app).
What does the --args switch do?

Speaking of which, how do you give a Python program command-line switch functionality?
Suppose I wanted to
$ ~/D*/V*/Vedu.py --apt --googleearth
so that it would install google earth and save that the user is using apt?
I can write the code that would make this work, but I don't know how to give it switches...

---

### Post by mssever on 2008-02-01
> **1337455 10534 said:**
>  What does the --args switch do?That's just a placeholder to show what you'd do if you needed to call your program with arguments (notice the single quotes).

> Speaking of which, how do you give a Python program command-line switch functionality?
Suppose I wanted to
$ ~/D*/V*/Vedu.py --apt --googleearth
so that it would install google earth and save that the user is using apt?
I can write the code that would make this work, but I don't know how to give it switches...There's a way to access all the command line arguments. In Ruby, it's the array ARGV. I don't remember what it is in Python, but it's probably names something similar. I'm not sure which module it would be in. os, maybe?

To parse options, you want to use getopt, or preferably getoptLong (to use the Ruby name). Again, I don't know the name of the Python module, but it should be similar to what I've given you.

---

### Post by bobbocanfly on 2008-02-01
> **mssever said:**
> 
There's a way to access all the command line arguments. In Ruby, it's the array ARGV. I don't remember what it is in Python, but it's probably names something similar. I'm not sure which module it would be in. os, maybe?


In python it is sys.argv[]. This code would take the first argument and print it to screen:

[PHP]import sys

data = sys.argv[1]
print data[/PHP]

---

### Post by 1337455 10534 on 2008-02-04
Hey guys, Version 2 is out, my science fair is done, and everything looks really nice! Check it out!

This is essentially a bump and I know I shouldn't, but I think I have put some major effort into my project and it deserves some use. Functionality is mostly Apt-centric right now, I haven't looked into implementing USE flags for Gentoo guys into the sufx string yet, but I'll see.

As far as features go, I will admit it is a bit lacking. I mean, it does some pretty cute things (update, clean, md5sum, file/shred [my fav]), but not really on the same line, as say, Tune Up Utilities 2008 for Windows. 

In my opinion, I believe my program is already better than Automatix and EasyUbuntu. It has incorporated all of the packages both install and is **cross-distribution.**

Yes. The sources.list I packaged in there has Automatix repositories. Their repos arent bad, their code just made my computer fry and refuse to boot :D. I respect all of you Automatix fans, but please give my program a shot. **I combine tools with "hard-to-install" software.** 

That and all of my code is under 100 kb, has a transparent installer, has well-written documentation, and is EXTREMELY friendly toward editing it makes it a good choice.
All of my code has been tested to work several times, so no worries there either.

If you're an Ubuntu user who has used Automatix you can see that it's pretty much a rip of the Add/Remove Programs App. Most things available in Automatix can be installed from Synaptic. Things like Google Earth, perhaps not, but my program will cover everything for you.

Sure, I don't have a splash screen or my own repo, but I have a solid app that wont goof up randomly or waste space.

---

### Post by mssever on 2008-02-04
Here are some comments about your code. I haven't run it yet--partially because I'm unfortunately in Windows right now.

installer.sh:[LIST]
[*]I don't think that it's a good idea to call all the different package managers. In the best case, it will cause errors that could be confusing. But What happens if someone has multiple package managers installed? For example, I'm using Ubuntu and have alien installed. rpm is a dependency of alien. What happens? Like I said, I'm running Windows right now, so I can't test it. But at the very least, you'll get errors. Instead, you should detect which package manager to use. You might find /etc/issue(.net)? to be useful, but then you'd have to maintain a list of all distros. It might be better to figure out how to determine which package manager is in use. Then, store that in a file, because it's never going to change. You don't need to re-detect it.
[*]The sleep statements just waste time. They don't accomplish anything.
[*]The specific package names that you're installing potentially vary by distro. Be sure to handle that situation properly.
[*]I think that you should use aptitude rather than apt-get to install stuff, because aptitude maintains a list of stuff that's automatically installed, so that if you uninstall stuff you don't get garbage left behind. This applies throughout the program, not just this file.[/LIST]modVedu.py[LIST]
[*]Instead of calling sudo all the time, why not start your GUI (or at least the installer) under gksudo. That will take care of possible inconvenient password prompts. Plus, GUIs shouldn't use sudo, because sudo is a terminal program and GUIs can't count on a terminal being available. That's what gksudo is for.
[*]line 29: If you ask users to run your program in a terminal, then why make a GUI? If it makes a difference whether the program is run in a terminal or not, then you're doing something wrong.
[*]line 30: You shouldn't need to ask this question. The installer should have figured that out already--possible by prompting the user--and stored that in a file somewhere. The package manager never changes on a given system.
[*]No specific line number: Have you actually tested the program on non-Debian systems? You're calling a number of Debian package names and APT tools directly. Examples: build-essential, m-a
[*]Lines 141-151: You're better off using the app-armor package, rather than building it manually. First, you haven't necessarily installed the build tools, so the command might fail. Second, your build commands use Debian-specific tools. Since your claim is to support multiple distros, what happens to Fedora users? Lastly, the native package might well exist, and you don't want to stomp on it. For example, apparmor is installed by default on Ubuntu Gutsy.
[*]Line 153: Instead of asking the user to start firestarter, why not start it for them?
[*]Lines 156, 157: The packages listed do nothing to help with a system restore, although they may be useful. Plus, some of the packages are already installed on every system (e.g., tar gzip bzip2). No sense listing them explicitly. Also, be aware that auto-installing ktorrent on a GNOME system will bring in a whole bunch of KDE dependencies.
[*]Lines 159-174: Installing compizconfig-settings-manager is a good idea, but I think that the rest is best left to the distro. Your code is guaranteed to break some machines. For the rest, how do you know that you're installing the right packages? For example, My machine doesn't require any special xserver. Given that all your code is Ubuntu-specific, you should leave Compiz to Ubuntu. Feisty, and especially Gutsy, do a good job on this once you install compizconfig-settings-manager.
[*]Lines 189-191: Why not install Google Earth from the repo? I'm running Windows right now, so I can't check, but I've got Google Earth installed, and I installed it from a .deb. I think that it's in medibuntu--but I'm not positive. It's generally a REALLY BAD IDEA to install software outside the package manager.
[*]lines 215-221: That's mildly dangerous. There's no reason for code that could require a hard reboot (even though I can guarantee that holding down the power button is not the only way to shut down earlier). Besides, why have a shutdown feature in a package installer? That doesn't make sense. The system already provides shutdown functionality. Remember, this isn't Windows. You don't have to reboot after installing packages.
[*]lines 220, 221: These lines are superfluous. They serve no purpose and can be deleted.
[*]Lines 231-238: You might be interested in a recursive shredder I wrote. It's available from [my repo]("http://severance.homelinux.org:8066/falcon/dists/main/scripts/").
[*]Line 243: Instead of asking the user which version they're running, why not detect it automatically? See /etc/issue.[/LIST]If you address these issues, you have the start of a useful program. As it stands now, your program is somewhat dangerous, although not as bad as Automatix.

EDIT: I just glanced through your sources.list. I don't think that it's a good idea to just copy that list to other systems for two reasons: 1) People will get lots of authentication errors since you aren't adding all those keys; 2) It isn't a good idea to wholesale trust a whole bunch of repos--particularly those that contain unstable software (such as Firefox 3). The users should have to explicitly enable each third party repo. Also, you're replacing everyone's Ubuntu repositories with the Italian mirrors, overriding their current mirror selection which was determined by the installer. Better to keep the users' mirror selections.

---

### Post by pmasiar on 2008-02-04
someone should insert here warning against using Automatix - it can hose your system pretty bad. Use Google before using Automatix!

---

### Post by 1337455 10534 on 2008-02-05
To mssever;
Thank-you for actually examining my code!!! You probably don't know how much I appreciate this, but really, thank-you!

1. I am a minimalist at heart, and am saddened by the inefficiency the installer 'works'. It does install those packages, and the error message is;
>  W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 9: yum: not found
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 10: zypper: not found
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 11: urpmi.update: not found
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 12: emerge: not found
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 13: netpkg: not found

Running package checks...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
python-central is already the newest version.
python-wxgtk2.8 is already the newest version.
libc6 is already the newest version.
libx11-6 is already the newest version.
tcl8.4 is already the newest version.
tclreadline is already the newest version.
gksu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 17: rpm: not found
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 18: emerge: not found
/home/q/Desktop/Projects/Python/Vedu/Good/Installer.sh: 19: netpkg: not found

Done...

So it works, just not very well. I can't think of another way to make sure all of those packages are installed.

2. Meh, I think that the one sleep in there lets the user know whats going on. If a black box with text scrolling down it really fast appeard on XP, I would be worried. Plus, the user can then see df info.

3. OUCH! If the package names vary, then the whole project is threatened. Would it be possible to use wildcards like you can in apt??
> q@Q-Desktop:~$ sudo apt-get install python-minim*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting python-minimal for regex 'python-minim*'
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
q@Q-Desktop:~$

4. I have heard the aptitude suggestion before, I just never thought there was a specific reason NOT to use apt-get. I'll switch to it.

5. Good point about sudo. In the Launch.sh, it starts the wxVedu.py with gksudo, but I could use gksudo to open modVedu from wxVedu (e.g "system("gksudo python modVedu.py -md5", and then remove all references to sudo in the mod). Is there a good reason to use gksudo over sudo?

6. I ask them to run it in a terminal becasue I cant offer them any sort of progress bar via GUI (or at least I dont know how). I am also **very reluctant** to use the -y switch for aptitude and force feed over 200 MB of download time on a user. They should have a choice. I mean, the program works without it (working out a couple kinks with the updater, fair warning, **this is still beta software,** just more stable then it used to be).

7. This is number 1 or 2 on my priority list. I'll find a way to get the name of the native package manager without having to ask them.. eventually..

8. I have tested this on Suse, Zenwalk, Mandriva, RedHat (my dad did this one) and Gentoo. Besides the fact that YasT is horrible about installing software, it works. **I will admit that the best functionality is reserved for Apt and Netpkg.** Gentoo is OK, but not power Gentooer would use my program. No USE flag support forseeable.

9. Fixed the firestarter pop-up.

10. I have noticed the AppArmor issue, I blindly follwed the Feisty guide so that will be fixed.

11. Ill take a look at redundant packages throughout the program. KTorrent must go, sadly. I enjoy it, as well as amarok, but I am a GNOME-lover.. I'm so torn.

12. Prehaps I'll create the Linux equivalent of a MS Wizard for Compiz Fusion; run a glx test, see if they have a good enough card,  find their graphics card name and see if it contains the sting 'nvid' or 'ati'. Sounds better than installing a bunch of random packages. Point noticed.

13. I honestly had no idea Googearth was in the repos now.

14. :D!!! Your shredder is awesome!!! I've been looking into changing colors in the terminal for a while but I couldn't find it! Also the simultaneous multiple filepath shredding ability is great!

15. I will look at etc/issue and make the sources.list more modest. (perhaps just medibuntu, opera, the basics)..

Again, thank you so much!

---

### Post by mssever on 2008-02-06
> **1337455 10534 said:**
> To mssever;
Thank-you for actually examining my code!!! You probably don't know how much I appreciate this, but really, thank-you!You're welcome. :)

> 1. I am a minimalist at heart, and am saddened by the inefficiency the installer 'works'. It does install those packages, and the error message is;

So it works, just not very well. I can't think of another way to make sure all of those packages are installed.I think that the best approach would be to simply determine the distro or package manager straight up. If nothing else, you could prompt the user, although I think that you can automatically determine that--except possibly for some minor distros that forget to set their own identification.

> 2. Meh, I think that the one sleep in there lets the user know whats going on. If a black box with text scrolling down it really fast appeard on XP, I would be worried. Plus, the user can then see df info.But Linux != Windows. Both gnome-terminal and konsole have scrollbars by default, and running df doesn't accomplish anything, so the user doesn't need to see it. Your program doesn't occupy even 1 MB, let alone 100 MB, so your disk space warning is incorrect. Why not let aptitude do its job and tell the user about the actual disk space requirements of your dependencies? (By the way, some of the packages, such as libc6, are already installed on EVERY Linux system.)

On line 30, the sleep saits 1 second before launching your program. Why?

> 3. OUCH! If the package names vary, then the whole project is threatened. Would it be possible to use wildcards like you can in apt??I don't know. This is likely one reason why there aren't other similar cross-distribution programs. The distros simply haven't standardized. Perhaps the best approach would be to design distro-specific plugins that know about their specific distro. It's more work, but I don't think there are any alternatives that will work in all cases. Since you say you tested this on several distros, that suggests that there isn't a whole lot of variation in the packages you tested. But I'm not comfortable with depending on something that you can't guarantee to be true.

> 5. Good point about sudo. In the Launch.sh, it starts the wxVedu.py with gksudo, but I could use gksudo to open modVedu from wxVedu (e.g "system("gksudo python modVedu.py -md5", and then remove all references to sudo in the mod). Is there a good reason to use gksudo over sudo?Since you're running wxVedu.py with gksudo, the whole process is running as root. There's no need for any kind of sudo anywhere else (although wxVedu.py should check to make sure that it's running as root).

sudo is for CLI apps and gksudo is for GUI apps, and they prompt appropriately. Additionally, there have been reports that in some situations (I don't know which), running sudo with a GUI app can bork X.

> 6. I ask them to run it in a terminal becasue I cant offer them any sort of progress bar via GUI (or at least I dont know how).If you compare Synaptic, update-manager, and gdebi-gtk, you'll notice that all three use the same GUI for installing packages. That indicates that a library already exists for these purposes. You should find it and use it. It'll handle prompting the user and progress bars.

> 7. This is number 1 or 2 on my priority list. I'll find a way to get the name of the native package manager without having to ask them.. eventually..Distro-specific plugins?

> Gentoo is OK, but not power Gentooer would use my program. No USE flag support forseeable.And would Gentoo users even be interested in your program in the first place? It's only useful to Linux newbies. Experienced users don't have use for it. And any Linux newbie who decided to try Gentoo would have plenty of interesting problems. :)

> 12. Prehaps I'll create the Linux equivalent of a MS Wizard for Compiz Fusion; run a glx test, see if they have a good enough card,  find their graphics card name and see if it contains the sting 'nvid' or 'ati'. Sounds better than installing a bunch of random packages. Point noticed.Perhaps the best path would be to relegate this to the distro-specific plugin, to use whatever tools exist already. As I said earlier, installing compizconfig-settings-manager is all that you need to install. Some distros might require more.

Another suggestion:

modVedu.py lines 109-112 and all related lines:

You might want to simplify this code thus (note that this code is untested):
```
if cont == 1:
    system(install_string(inst, sufx, supertux, atanks, dreamchess, freeciv-client-gtk, fretsonfire, frozen-bubble, ggz, kasteroids, kdegames, openarena))
        #elif cont != 1: Delete these lines. You don't need them.
        #    pass
```Then, you could define install_string():```
def install_string(prefix, suffix, *packages):
    result = [prefix]
    for package in packages:
        result.append("%s%s" % (package, suffix))
    return " ".join(result)
```

---

### Post by mssever on 2008-02-06
duplicate post

---

### Post by 1337455 10534 on 2008-02-06
@mssever;
Excellent comments.
Truthfully, my first approach was to write seperate code for each seperate Linux but then I believed it would become too hectic to manage.
I see that it is now neccessary to some extent, so I'll get to it.

Point noted about the shared libraries. I'll check their dependencies in synaptic, but I dont think Synaptic is a wx app.

---

### Post by mssever on 2008-02-07
> **1337455 10534 said:**
> @mssever;
Excellent comments.
Truthfully, my first approach was to write seperate code for each seperate Linux but then I believed it would become too hectic to manage.
I see that it is now neccessary to some extent, so I'll get to it.If you do it right, you should be able to define a general case, then for each distro only record the differences from that general case.

> Point noted about the shared libraries. I'll check their dependencies in synaptic, but I dont think Synaptic is a wx app.I have no idea about how the library is structured. I'm guessing it's GTK, but that shouldn't be too much of an obstacle. First, you might be able to just call it and let it handle its own widgets for you. Otherwise, you could write a simple GTK wrapper app that merely calls the library. Or, you could switch your project to GTK, given that GTK has more broad support in the Linux world anyway and that the main reason for wx (cross-platform compatibility) is irrelevant for a project focused on installing Linux software.

EDIT: It's possible that there might not be an explicit dependency, which could require you to read the source. I think that at least update-manager is in Python.

---

### Post by 1337455 10534 on 2008-02-07
I'm messing around with glade right now. I like the idea of going to GTK very much!
wx seems easier, but the conceptually the development process is identical (design-xml, write handlers, link to external code).

I'm going to make core changes to the code above before I alter the GUI, meanwhile, I can't appreciate the criticisms enough!!

Glade+pyGTK is awesome! I finished making odd corrections to all of the code. It's on the first page now.
Agenda;
1. Implement code that autodetects distribution package manager (or distro name will suffice)
2. Move to GTK and design more robust GUI
3. Add more features to the modVedu package

---

### Post by 1337455 10534 on 2008-02-07
> **pmasiar said:**
> someone should insert here warning against using Automatix - it can hose your system pretty bad. Use Google before using Automatix!

Don't depend on Automatix when you can do it yourself, 1+. I'm not gonna take a stance on the flame here, just putting it out there that my box was working great before I installed it, and then it wouldn't boot. Just saying...

---

