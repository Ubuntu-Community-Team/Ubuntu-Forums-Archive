---
title: "new open source project"
date: 2007-08-07
forum: Programming Talk
---

### Post by bribaetz on 2007-08-07
im starting an open source project called scarlet mode.
written in windows batch and bash dont be put off by the languages this is a complex and useful program it makes a command promt Easier by simply replacing it not removing it  but allowing user to do all command stuff with this instead. for details contact me at [email]bribaetz@hotmail.com[/email] or im me at yahoo bribaetz also
[email]bribaetz@yahoo.com[/email]

---

### Post by bribaetz on 2007-08-07
:KS soits easy and a newer programmer can learn from it and what a helpful program is not stupid tutorial programs

---

### Post by foxylad on 2007-08-07
Can you describe scarlet mode in more detail? Does it run on Windows or Linux? How does it make the command prompt easier? What command prompt actions will it replace?

---

### Post by Note360 on 2007-08-07
hmm... why would you write this in bash and batch it makes no sense...

---

### Post by bribaetz on 2007-08-07
batch for windows to make it replace commands prompt
bash for Ubuntu replace terminal it replaces prompt  with easy commands that are easy to remember  it also has integrated functions games calculator its in progress and will also have updated newer versions. im working on 1.0 beta.testing

---

### Post by bribaetz on 2007-08-07
ne1 know where i can get a free subdomain with forum and user/password capabilities

---

### Post by fatsheep on 2007-08-07
Easy commands that are easy to remember?  Are you going to rename the bash commands?

---

### Post by Note360 on 2007-08-07
wow. I find the commands very easy to remember....

cp... copy wow rocket science
Ok, some of the things can get annoying (options). However, man pages baby. 
Also, this is not an instant messanging client. Try to use halfway decent punctuation.

---

### Post by Nekiruhs on 2007-08-07
You can do all this with aliases
```
alias remove='rm'
alias Su='sudo -s'
alias rm='rm -i'
alias ls='tree'
alias unsu='su nekiruhs'
alias nvlc='vlc -I ncurses'
alias empty='cp /dev/null'
alias sourc='source .bashrc'
```Not that hard. Why are you doing this in BASH anyway? BASH is a scripting language, not a programming language. Not all distros use BASH anyway. Some use zsh, csh, sh, dash. If your going to do something and make it open source, do it in a real language.

---

### Post by bribaetz on 2007-08-07
ok whatever i give up nobody likes the idea any way the prompt commands to me are anoying im learning pascal right now  so i cant use that batch is cool if anyone knows how to put your  syrstem password and user name on a batch file but  but its not a contant but a variable that would be helpful.

---

### Post by bribaetz on 2007-08-08
heres my source for those that understand i want a similar interface for my windows and linux command prompts ```
 @echo off
title scarlet mode
color ec
echo welcome to scarlet
echo goto command prompt for more info 
:start
set choice = nada
set /p choice= command-
if %choice% == run GOTO runa 
if %choice% == turnoff GOTO a
if %choice% == ato GOTO b
if %choice% == logout GOTO c
if %choice% == clock GOTO pom
if %choice% == allfiles GOTO d
if %choice% == freshpage GOTO e
if %choice% ==  callender GOTO f
if %choice% == cmd GOTO g
if %choice% == version GOTO h
if %choice% == report GOTO i
if %choice% == help GOTO nine
if %choice% == bgbluetxtred GOTO one
if %choice% == bgredtxtblue GOTO two
if %choice% == bgtxto GOTO three
if %choice% == bglbluetxtblue GOTO four
if %choice% == bgblacktxtwhite GOTO five
if %choice% == bgbluetxtyellow GOTO six
if %choice% == game GOTO black
if %choice% == bggreytxtpurple GOTO ggg
if %choice% == bgpurpletxtgrey GOTO ggggg
if %choice% == calc GOTO retard
echo not an operable command
GOTO start
:runa
set /p program=file:
start %program%
GOTO start
:pom
time
GOTO start
:retard
set /p _string=">"
if /i "%_string%"=="exit" GOTO start
set /a _result=%_string%
echo %_result%
GOTO retard
:ggggg
color d8
GOTO start
:ggg
color 8d
GOTO start
:black
echo rules = pick 1 2 or 3 and press enter
echo.
set choice = nada
set /p choice= number-
if %choice% == 1 GOTO sheep
if %choice% == 2 GOTO cat
if %choice% == 3 GOTO dog
GOTO black
:sheep
echo you lose
pause nul press any to go to command
GOTO start
:cat
echo you win
pause nul press any to go to command
GOTO start
:dog
echo you lose
pause nul press any to go to command
GOTO start
:six
color 16
GOTO start
:five
color 07
GOTO start
:four
color 91
GOTO start
:three
color ec
GOTO start
:two
color c1
GOTO start
:one
color 1c
GOTO start
:nine
echo turnoff = shutdown
echo ato = quit shutdown
echo logout = logoff
echo clock = time
echo allfiles = shows all files
echo freshpage = clears page
echo date = shows date
echo cmd = transforms to a command prompt
echo version = shows windows version
echo report = hard disk report
echo help = shows help desk
pause
GOTO start

:i
chkdsk
GOTO start
 :h
vol
GOTO start
:g
cmd
GOTO start

:b 
shutdown -a
GOTO start
:a
shutdown -s
GOTO start
:c
shutdown -l
GOTO start
:d
tree
GOTO start
:e
cls
GOTO start
:f
date
GOTO start
  
```

---

### Post by bribaetz on 2007-08-08
well thats what i got

---

### Post by mssever on 2007-08-08
Do you have your bash source done yet? I've never found BAT files useful enough to learn the syntax (and all those GOTOs are evil). I never use Windows, anyway. But, if you have any good ideas for bash, I'm interested.

---

### Post by Nekiruhs on 2007-08-08
> **bribaetz said:**
> heres my source for those that understand i want a similar interface for my windows and linux command prompts ```
 @echo off
title scarlet mode
color ec
echo welcome to scarlet
echo goto command prompt for more info 
:start
set choice = nada
set /p choice= command-
if %choice% == run GOTO runa 
if %choice% == turnoff GOTO a
if %choice% == ato GOTO b
if %choice% == logout GOTO c
if %choice% == clock GOTO pom
if %choice% == allfiles GOTO d
if %choice% == freshpage GOTO e
if %choice% ==  callender GOTO f
if %choice% == cmd GOTO g
if %choice% == version GOTO h
if %choice% == report GOTO i
if %choice% == help GOTO nine
if %choice% == bgbluetxtred GOTO one
if %choice% == bgredtxtblue GOTO two
if %choice% == bgtxto GOTO three
if %choice% == bglbluetxtblue GOTO four
if %choice% == bgblacktxtwhite GOTO five
if %choice% == bgbluetxtyellow GOTO six
if %choice% == game GOTO black
if %choice% == bggreytxtpurple GOTO ggg
if %choice% == bgpurpletxtgrey GOTO ggggg
if %choice% == calc GOTO retard
echo not an operable command
GOTO start
:runa
set /p program=file:
start %program%
GOTO start
:pom
time
GOTO start
:retard
set /p _string=">"
if /i "%_string%"=="exit" GOTO start
set /a _result=%_string%
echo %_result%
GOTO retard
:ggggg
color d8
GOTO start
:ggg
color 8d
GOTO start
:black
echo rules = pick 1 2 or 3 and press enter
echo.
set choice = nada
set /p choice= number-
if %choice% == 1 GOTO sheep
if %choice% == 2 GOTO cat
if %choice% == 3 GOTO dog
GOTO black
:sheep
echo you lose
pause nul press any to go to command
GOTO start
:cat
echo you win
pause nul press any to go to command
GOTO start
:dog
echo you lose
pause nul press any to go to command
GOTO start
:six
color 16
GOTO start
:five
color 07
GOTO start
:four
color 91
GOTO start
:three
color ec
GOTO start
:two
color c1
GOTO start
:one
color 1c
GOTO start
:nine
echo turnoff = shutdown
echo ato = quit shutdown
echo logout = logoff
echo clock = time
echo allfiles = shows all files
echo freshpage = clears page
echo date = shows date
echo cmd = transforms to a command prompt
echo version = shows windows version
echo report = hard disk report
echo help = shows help desk
pause
GOTO start

:i
chkdsk
GOTO start
 :h
vol
GOTO start
:g
cmd
GOTO start

:b 
shutdown -a
GOTO start
:a
shutdown -s
GOTO start
:c
shutdown -l
GOTO start
:d
tree
GOTO start
:e
cls
GOTO start
:f
date
GOTO start
  
```
No offense man, but you expect people to be  able to read that? With all those GOTOS? Why don't you learn how if statements work, maybe use case/switch statements. What benefit is this supposed to have anyway?

---

### Post by [h2o] on 2007-08-08
> **Nekiruhs said:**
> No offense man, but you expect people to be  able to read that? With all those GOTOS? Why don't you learn how if statements work, maybe use case/switch statements. What benefit is this supposed to have anyway?
Not too sure that the batch scripting language even has a case/switch statement. I'd never touched it until today when I had to write a simple script, and if I can choose I will never touch it again since it was a pain to work with and had quite a poor list of features.

---

### Post by Note360 on 2007-08-08
IF you want it to be cross platform a language like python, ruby or perl would be a good idea to look into. They are pretty easy to use and learn and they are cross platform for the most part.

---

### Post by bribaetz on 2007-08-08
> **Nekiruhs said:**
> No offense man, but you expect people to be  able to read that? With all those GOTOS? Why don't you learn how if statements work, maybe use case/switch statements. What benefit is this supposed to have anyway?

i spaced i done everything to make it legable if you cant read it its your own noob program dont make it my fault th GOTO statement is used to go back to the command from the command you have used.open a note pad save scarletmode.bat then run it then see whos been making mistakes

---

### Post by bribaetz on 2007-08-08
> **mssever said:**
> Do you have your bash source done yet? I've never found BAT files useful enough to learn the syntax (and all those GOTOs are evil). I never use Windows, anyway. But, if you have any good ideas for bash, I'm interested.

i want to get the source for bash from this so i need to learn bash

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> i spaced i done everything to make it legable if you cant read it its your own noob program dont make it my fault th GOTO statement is used to go back to the command from the command you have used.open a note pad save scarletmode.bat then run it then see whos been making mistakes

I don't think he/she was insulting you, it's just the use of GOTO.

I don't remember if BAT files used anything else, but in the programming community GOTO's are generally frowned upon and replaced with more structured program control.

Luckily BASH supports some better methods of handling things. I _heavily_ recommend you learn BASH before you go any further with this project.

---

### Post by Note360 on 2007-08-08
GOTO's are er hated here. I found a good comic about it (in some one elses post though), but i cant find the link atm.

Summary:
Guys sitting at computer. Says, something along the lines of "I could move this here and do this and make this do that or I could use one littel Goto... Eh GOTO's cant be to bad". IN the next panel he gets tackled by a raptor.


So unless you want a raptor to be eating you for second breakfast then I would suggest against GOTO's in any other language besides batch (bc I think that is batch's only alternative )

---

### Post by bribaetz on 2007-08-08
pascal whats bad about that goto 1 whats the alterintive

---

### Post by Note360 on 2007-08-08
> **bribaetz said:**
> pascal whats bad about that goto 1 whats the alterintive

1 question... Why are you using pascal. I am just wondering. I am not flaming you I just want to know the reason behind learning pascal instead of a more modern language. just wondering?

Also I am not sure if pascal has functions, but functions are generally used instead of goto's and they make code easier to read.

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> pascal whats bad about that goto 1 whats the alterintive

Alternative to GOTO?

Almost every modern language! lol

I suggest you give a whack at Python and see if you can't learn it. (it will probably help you learn programming more then pascal, batch, or BASH)

BASH is good for scripting small events and helping with system related tasks, but it's not something you would want to write a program in.

Also pascal is getting old. It will be harder to find support while learning it.

---

### Post by bribaetz on 2007-08-08
ok i want to learn pascal because its easier than some of thee alternatives and almost  as powerful pascal in my opinion is like basic and all the other older languages is underestimated because its old

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> ok i want to learn pascal because its easier than some of thee alternatives and almost  as powerful pascal in my opinion is like basic and all the other older languages is underestimated because its old

C is pretty old as far as programming languages goes... It's still around. Why? Because it's well designed and well supported.

Python is easier then pascal IMO, in fact... Possibly one of the easiest and most elegant languages I've ever programmed in.

You can learn pascal if you want, but you will get more support with a newer language and you will be able to do more with todays technology.

---

### Post by Note360 on 2007-08-08
Also, at this point in time most languages that are still being used are decent from the past, but those that are no longer used alot are not used alot for a reason...

---

### Post by bribaetz on 2007-08-08
so the languages i want to learn aren't good ok wat about perl ocaml c
or python any1 know what i can use those for and where to find tutorials python deosnt cmpile right whats python it runs in the ide

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> so the languages i want to learn aren't good ok wat about perl ocaml c
or python any1 know what i can use those for and where to find tutorials python deosnt cmpile right whats python it runs in the ide

You don't need an IDE for python, just a command line (BATCH and BASH don't compile either).

I don't know about ocaml, but Perl, C, and Python are all decent languages (maybe not Perl, but it's better then pascal).

What can you do with Python or C? Basically anything you want to program.

Games/applications/simulations... You name it.

---

### Post by bribaetz on 2007-08-08
perl is harder than pascal to me though

---

### Post by Note360 on 2007-08-08
perl is a type of brain **** for some people... It doenst always fit a persons mind set...

---

### Post by bribaetz on 2007-08-08
how do i save a python file from terminal

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> how do i save a python file from terminal

Just type it in a text editor like you would your batch scripts and execute it from the terminal with "python your_program_here.py"

---

### Post by bribaetz on 2007-08-08
ok

---

### Post by bribaetz on 2007-08-08
bash: hello.py: command not found

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> bash: hello.py: command not found

You must use:

```

python hello.py

```

---

### Post by bribaetz on 2007-08-08
cool thanks um can it be graphical or all text base

---

### Post by Note360 on 2007-08-08
hehehe...
ok lets do this in a step by step manner.

go to the terminal type
```
cd ~
```
just to get you into your home directory (if you arent already their for whatever reason).
Now type ```
python
``` this should bring up a nice little prompt this is the interactive prompt you can type commands right in and it will interpret them and run them. It is really cool. I would suggest experimenting with this for abit.
now lets make an application. I will use nano as the text editor for now since it its fairly self explanatory, but I would suggest getting a better editor (emacs, vim, etc). ```
nano hello.py
``` now insert ```

#!/usr/bin/env python
print "Hello World"

``` into the file. Hit Ctrl-x to exit (save the file) and now type
```
python hello.py
```

To run it as ```
./hello.py
``` you will have to make it executable. The way you do this is by chmoding it ```
chmod +x hello.py
```

---

### Post by Note360 on 2007-08-08
also it will probably be all text based while you learn the basics. Maybe EasyGUI would be good for you though.

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> cool thanks um can it be graphical or all text base

Are you asking if it's possible to make graphical programs with python?

If so, then hell yes. There is PyGame for 2d stuff and OpenGL libraries for 3d stuff. And as far as window GUI programming goes, take your pick, python probably has a library for it.

---

### Post by pmasiar on 2007-08-08
> **Note360 said:**
> GOTO's are er hated here.

You are wrong. GOTO is not hated here - GOTO is obsolete and has no use in *modern* languages. It is not hated - smart people know *why not* use it (and avoid languages which require it), and rest think it is not used for some religious reason.

> I found a good comic about it (in some one elses post though), but i cant find the link atm.

[http://xkcd.com/292/](http://xkcd.com/292/)

and free refill: [http://xkcd.com/149/](http://xkcd.com/149/) :-)

---

### Post by bribaetz on 2007-08-08
>>> ./hello.py
  File "<stdin>", line 1
    ./hello.py
    ^
SyntaxError: invalid syntax
>>> chmod +x hello.py
  File "<stdin>", line 1
    chmod +x hello.py
                 ^

---

### Post by Note360 on 2007-08-08
oh oops I forgot to say that you have to exit out of python.. to do those commands thats the shells stuff (Ctrl-D exits out of the python prompt). Heh sorry

---

### Post by Wybiral on 2007-08-08
> **bribaetz said:**
> >>> ./hello.py
  File "<stdin>", line 1
    ./hello.py
    ^
SyntaxError: invalid syntax
>>> chmod +x hello.py
  File "<stdin>", line 1
    chmod +x hello.py
                 ^

Judging by the ">>>" I can see that you entered it in the python interpreter, not the actual terminal. Exit out of the interpreter, then try to execute the file.

---

### Post by Note360 on 2007-08-08
you will have to  do chmod +x hello.py before ./hello.py

---

### Post by bribaetz on 2007-08-08
all except one screwed up but i use an ide called Meany any way

---

### Post by Note360 on 2007-08-08
> **bribaetz said:**
> all except one screwed up but i use an ide called Meany any way

Do you mean Geany?

---

### Post by bribaetz on 2007-08-08
yeh

---

### Post by PandaGoat on 2007-08-08
I am going to be blunt because from what I have read no other method has worked.  You really need to use better grammar and explore things on your own.  Go ahead and learn an old language, but do not rely on it.  Do not make a new project with an old language unless you must.  

I started with C++, so this may be biased, but I would suggest not messing with most convoluted random python tutorials or crappy pascal, which is crappy because of how outdated it is--not meaning it is not powerful.  

**Go to this link: [http://www.cplusplus.com/doc/tutorial/]("http://www.cplusplus.com/doc/tutorial/")**
Read it and do not go on unless you understand what you have read.  Do not worry about the compiler you'll use, that is not even the point of understanding c++.  Programming is all logic, the other things are tools you use.

**If you cannot understand or do anything below and you read the above tutorial, then it is a problem with your understanding of linux, not c++. Explore more with linux.**

I have not used geany and you cannot seam to get any other IDE, so use a compiler at command line.  Use this command in the terminal to install everything you need:
```

sudo apt-get install build-essential

```

C++ code, as with most other things goes into a file.  The file extension for C++ is .cpp.  If you want to start writing a program create a file on your desktop.  Rename it to main.cpp.  Open it in gedit--double click it. 

Once you put your code in the file, open the terminal, which has a current directory.  The default is home--~/.  main.cpp is on the desktop so enter this command:
```
cd ~/Desktop
```
Now that you are there you can compile main.cpp into a binary to run.  Enter this in the terminal.
```
g++ -o [binary name] main.cpp
```
Replace [binary name] with the text you want the binary's filename to be.  This will create the binary on your dsektop, to run it drag and drop the binary on your terminal and hit enter.

If you got through all of that, (re)read the tutorial some more.

---

### Post by CptPicard on 2007-08-08
I would also suggest that you just simply learn the Linux shell as the first thing. Learn your tools. Learn how to type in commands. I mean... in your previous threads I read last night, you were obviously totally out of your depth even running the C compiler from the command prompt (despite declaring somewhere at the start of the thread you're a fairly experienced programmer... and you use gotos?).

Now, because bash was too hard to grok (at the "run g++" level), you're trying to rewrite bash to being something more user-friendly... in bash? :confused:

Just learn to use the shell instead of trying to dumb it down, as that is a minimal requirement to being a proficient Linux programmer...

---

### Post by Nekiruhs on 2007-08-08
> **bribaetz said:**
> i spaced i done everything to make it legable if you cant read it its your own noob program dont make it my fault th GOTO statement is used to go back to the command from the command you have used.open a note pad save scarletmode.bat then run it then see whos been making mistakes
Ok, if you must use GOTOs then make the labels at least descriptive. a b c d e f g ggg ggggg pom runa one two three four five black six hi retard Are not good labels, I can't tell what any of them mean by looking at them. In a language without comments please make descriptive code.

---

### Post by pmasiar on 2007-08-08
Just fount on Ubuntu Planet: [How to start your own project](http://www.somethingsimilar.com/wordpress/2007/08/06/how-to-get-your-project-moving-or-my-ego-is-massive-and-you-should-listen-to-me/)

Money para: "The nerds will come to you but you&#8217;ve got to work your *** off first. No one, absolutely no one, who is any ... good will come near your project if its nothing more than a few airy ideas."

In case you missed his other posts, OP looks to me like a ... lets say funny guy. 

I read somewhere (proved by research) that incompetent people grossly overestimete their own competence.

---

### Post by bribaetz on 2007-08-08
ok ill check out that link i try not to over estimate my self if i do let me know

---

### Post by slavik on 2007-08-09
bribaetz, are you trying to create an interactive shell with some built in commands?

---

### Post by bribaetz on 2007-08-09
yes but every one puts down batch and bash so i will use python
to write it using macros built in to program.
it will have a little graphical but mostly command and help file will display all commands.

---

### Post by slavik on 2007-08-09
honestly, I think you should write a tutorial instead since what you are doing is just running commands anyway and are colling them differently.

---

### Post by PandaGoat on 2007-08-09
A tutorial would be better than reinventing the wheel.  It would also help you remember the commands that you can not remember.  However, if you do write a tutorial, please revamp your grammar.

---

### Post by bribaetz on 2007-08-09
ok
 will

---

### Post by Wybiral on 2007-08-09
I noticed in your batch tutorial you said:
"Plus who wants a text o.s."

And I would have to respond:
Me!

I use the command line for lots of stuff. When I'm writing text-based programs I often just run Linux from the command line instead of using gnome.

In fact, your DOS batch scripts... DOS is a text OS :)

If I don't need to see things, I prefer to read them, it's faster and uses less memory that way. There are even command-line web browsers!

Also, someone using their computer for things like web servers has absolutely no need for a graphical interface. It's a waste of processor, memory, and hard drive if you're not going to use it.

The reason you can't make an OS with batch scripts isn't because they aren't graphical, it's because they run inside another OS (being DOS).

---

### Post by LaRoza on 2007-08-09
> **Wybiral said:**
> I noticed in your batch tutorial you said:
"Plus who wants a text o.s."

I use the command line for lots of stuff. When I'm writing text-based programs I often just run Linux from the command line instead of using gnome.

If I don't need to see things, I prefer to read them, it's faster and uses less memory that way. There are even command-line web browsers!

Also, someone using their computer for things like web servers has absolutely no need for a graphical interface. It's a waste of processor, memory, and hard drive if you're not going to use it.


I use the CLI all the time, in Vista also. 

Vim is the handiest tools, and it is very useful, I now find regular text editors to be bloated and featureless, next to Vim.

I even got the Windows version.

I intentionaly disable the gui sometimes when I am programming so I can get things done. (Press Ctrl + Alt + F1)

With Vim, you have much more power and control. 

The only problem is, that you can not go to full screen mode in Vista (for some reason).

---

### Post by LaRoza on 2007-08-09
> **pmasiar said:**
> 
In case you missed his other posts, OP looks to me like a ... lets say funny guy. 

I read somewhere (proved by research) that incompetent people grossly overestimete their own competence.

0. True, but inoffensive (except for that one comment about Python)

1. I agree, I am fully aware of just how little I know, and find that as an incentive to learn more and more. (Learning is what I live for)

---

### Post by LaRoza on 2007-08-09
> **pmasiar said:**
> You are wrong. GOTO is not hated here - GOTO is obsolete and has no use in *modern* languages. It is not hated - smart people know *why not* use it (and avoid languages which require it), and rest think it is not used for some religious reason.


In languages that do use it, like Fortran and Assembly, the code is structured to make it function as a loop.

This is Fortran 77:
```


  10   if (x .lt. 10) then
            write (*,*) 'X is ',x
            goto 10
        endif

```
(This is a while loop)

---

### Post by CptPicard on 2007-08-09
> **bribaetz said:**
> ok
 will

And before you write a tutorial, I also suggest you READ a lot of tutorials.. :)

---

### Post by bribaetz on 2007-08-09
i have done that

---

### Post by aks44 on 2007-08-09
> **pmasiar said:**
> I read somewhere (proved by research) that incompetent people grossly overestimete their own competence.

Perfectly right.
The less you know, the more you value the little you know.
On the contrary, the more you know, the more you realize that you're merely a newb... 
:)

---

### Post by pmasiar on 2007-08-09
> **LaRoza said:**
> In languages that do use it, like Fortran and Assembly, the code is structured to make it function as a loop.

well, I *did* said "modern" languages, didn't I  :-)

---

### Post by Wybiral on 2007-08-09
> **LaRoza said:**
> In languages that do use it, like Fortran and Assembly, the code is structured to make it function as a loop.

This is Fortran 77:
```


  10   if (x .lt. 10) then
            write (*,*) 'X is ',x
            goto 10
        endif

```
(This is a while loop)

Assembly also has a stack allowing you to easily partition the memory.

Something like this is possible:

```

some_func:
    pop return_address
    pop value2
    pop value1

; do something

    push return_value
jmp return_address


_start:
    push value1
    push value2
    push some_address
    jmp some_func
    some_address:
    pop returned_value

```

lol, assembly pseudo code?

But, assembly has a "call" and "ret" mnemonics that basically do the same thing.

This is how C's functions compile.

Even a good assembly programmer doesn't use that "goto a; goto b; if(x) goto c" crap. It's MUCH more structured.

This is really only possible with a stack type structure, you need a way to allocate and partition memory to create pseudo functions.

---

### Post by pmasiar on 2007-08-09
> **Wybiral said:**
> assembly has a "call" and "ret" mnemonics that basically do the same thing.


Exactly. CALL/RET are *very* different from plain JMP. Unlike JMP, CALL stores current code position (I forgot the name of register - it's years since I used it) in special "return" stack (different from parameter stack) so RET "knows" where to return. JMP (==GOTO) messes this, even in assembly. :-)

---

### Post by tehkain on 2007-08-09
I would use python. Makes it super easy and modular. I would use a dictionary to associate keys(your commands) with value(real commands).

```
#! /usr/bin/env python
# -*- coding: utf8 -*-
#console.py
#just an example for the OP
#you can use dictionairies instead of if/elif statements but I made this in a minute 
import os
   
       
class Control():
    """
    This class is used as both the main loop and the main map. It allows the user to control and access different features.
    """
    def ticket_booth(self):
        """Asks the user what they would like to do and passes that on to the main_hub"""
        
        print """
        prints a list of the commands
        __
        xorg-back: backs up your xorg.conf file into the home directory
        exit: exits this app
        
        """
       
        ticket = raw_input(">>> ")
        self.main_hub(ticket)
   
    def main_hub(self,ticket):
        """
        This method takes the 'ticket' from the ticket_booth method and passes that on to the if/else/elif action. Which directs the        
        application to the requested feature.
        """
        #replace the if/elif ==s with some command
        if ticket == 'xorg-back':
            #command one
            os.system('cp //etc//X11//xorg.conf ~//.xorg.conf.bak')
        elif ticket == 'some other key':
            print ''
        elif ticket == 'yet another key':
            #command two
            print ''
        elif ticket == 'exit':
            #kills the application
            import sys
            sys.exit()
        else:
            print "no option selected"
           
    def run(self):
        """
        Main loop
        """
        self.ticket_booth()
        self.run()
       
if __name__  == '__main__':
    Main = Control()
    Main.run()
```

---

### Post by bribaetz on 2007-08-09
thats nice im not that great yet but ill compiler it in my ide

---

### Post by Nekiruhs on 2007-08-09
> **bribaetz said:**
> thats nice im not that great yet but ill compiler it in my ide
Have you even read the previous posts? Python is not compiled!

---

### Post by slavik on 2007-08-10
python is compiled, except for fake hardware. :P

---

### Post by Wybiral on 2007-08-10
> **pmasiar said:**
> Exactly. CALL/RET are *very* different from plain JMP. Unlike JMP, CALL stores current code position (I forgot the name of register - it's years since I used it) in special "return" stack (different from parameter stack) so RET "knows" where to return. JMP (==GOTO) messes this, even in assembly. :-)

EIP.

And I absolutely agree jmp / goto != call / gosub in terms of structure.

---

### Post by pmasiar on 2007-08-10
> **Nekiruhs said:**
> Have you even read the previous posts? Python is not compiled!

You are nominally correct but not 100%: Python is parsed and compiled to bytecode (*.pyc files, which you can distribute instead of sources), and can be compiled even farther if required (psyco and friends).

---

### Post by tehkain on 2007-08-10
I really do not see a need to make the console 'easier'. It is about as easy as a text interface could ever be. After looking at his batch I was so happy I learned a decent language first. There should be laws against learning such a thing first... it distorts your mentality! All the pain he went thru typing that up accounts for more pain then he will ever save the people he is making it for. To the OP I suggest you pick up 'Python for Dummies' since it is a really awesome book. 

PS - Does anyone know how to split a big book like Programming Python in to little books without suffering binding issues? When OReilly releases volume sets instead of 2k page codex I will kiss their feet.

---

### Post by LaRoza on 2007-08-10
> **pmasiar said:**
> well, I *did* said "modern" languages, didn't I  :-)

The only reason I mentioned it, was to show that "goto" isn't evil, just extremely easy to abuse, and that there are now better ways.

---

### Post by cro.smiley on 2007-08-10
It must be that bad grammar is attractive to people since this guy got all this attention on his idea. [[COLOR="DarkOrchid"]My project[/COLOR]]("http://ubuntuforums.org/showthread.php?t=222269") made in c++ that acctually works :), has still only 10 posts (5 are mine :)). Or maybe it would be more popular if I wrote it in bash. Anyway, good luck man.

---

### Post by Wybiral on 2007-08-10
> **cro.smiley said:**
> It must be that bad grammar is attractive to people since this guy got all this attention on his idea. [[COLOR="DarkOrchid"]My project[/COLOR]]("http://ubuntuforums.org/showthread.php?t=222269") made in c++ that acctually works :), has still only 10 posts (5 are mine :)). Or maybe it would be more popular if I wrote it in bash. Anyway, good luck man.

You didn't need help with anything.

---

### Post by cro.smiley on 2007-08-11
> **Wybiral said:**
> You didn't need help with anything.

Actually I needed testing as the post title says: "New project needs testing". It's quite hard working on something when you don't know if the people like it or not. There is more satisfaction when you do something for others and not just for your self. Maybe as the project grows bigger the user feedback will start rising, who knows...

---

### Post by bribaetz on 2007-08-11
my program works in windows

---

### Post by pmasiar on 2007-08-11
> **cro.smiley said:**
> Actually I needed testing as the post title says: "New project needs testing". It's quite hard working on something when you don't know if the people like it or not. There is more satisfaction when you do something for others and not just for your self. Maybe as the project grows bigger the user feedback will start rising, who knows...

Building the community is the hardest part of the project. That is why I advice anyone to join existing project instead of starting new. And joining existing  project has other positives - too many to count. :-)

---

### Post by apetresc on 2007-08-11
> **pmasiar said:**
> GOTO is obsolete and has no use in *modern* languages. It is not hated - smart people know *why not* use it (and avoid languages which require it)
On the contrary, good programmers know *when* to use it. It is an easily abused tool, hence the warning to beginners to just abstain from it altogether, but there do exist proper uses for GOTO.

In fact, [Linus uses it in the kernel](http://kerneltrap.org/node/553/2131), and has defended his choice to use it.

---

### Post by pmasiar on 2007-08-11
> **AdrianP said:**
> On the contrary, good programmers know *when* to use it. It is an easily abused tool, 

Well, most people asking for help here does not hack on Kernel :-) hence they have hardly any reasonable use for GOTO, and in most modern languages (like Python) GOTO even does not exists (because is not needed). Structured programming war were fought 30 years ago, I don't see the point to re-enact them, do you?

IMHO C is not a high-level language, but just a very smart assembly language, it was designed not to be modern but to be effective crossplatform language to replace ASM for writing OS.

Bonus link for lovers of C: [Three Star Programmer](http://c2.com/cgi/wiki?ThreeStarProgrammer). I liked C back in days of lore  but prefer use higher abstractions these days... :-)

But yes, i agree with you. If you have situation where GOTO is required, use it! Just be prepared to face [velociraptors](http://xkcd.com/292/)! :-) and don't say we did not warned you!

---

### Post by Wybiral on 2007-08-12
> **pmasiar said:**
> Well, most people asking for help here does not hack on Kernel :-) hence they have hardly any reasonable use for GOTO, and in most modern languages (like Python) GOTO even does not exists (because is not needed). Structured programming war were fought 30 years ago, I don't see the point to re-enact them, do you?

IMHO C is not a high-level language, but just a very smart assembly language, it was designed not to be modern but to be effective crossplatform language to replace ASM for writing OS.

Bonus link for lovers of C: [Three Star Programmer](http://c2.com/cgi/wiki?ThreeStarProgrammer). I liked C back in days of lore  but prefer use higher abstractions these days... :-)

But yes, i agree with you. If you have situation where GOTO is required, use it! Just be prepared to face [velociraptors](http://xkcd.com/292/)! :-) and don't say we did not warned you!

I don't think I've ever had to use three stars, lol... I do frequently use two though! (when I need to change the address of a pointer passed to a function).

btw pmasiar, I'm throwing in the towel on low level programming (in general, I still like the challenge it gives) I've been using C++ much more lately and have noticed a significant increase in my productivity (feel free to say "I told you so"... I should have listened)

On the plus side, I have quite a bit of confidence in my knowledge of the low level stuff which certainly helps me make decisions in HLL's.

(maybe I'll work my way up to Python some day, lol... I just don't think I'm ready to give up my pointers and strong types)

---

### Post by pmasiar on 2007-08-12
> **Wybiral said:**
> I don't think I've ever had to use three stars, lol...

That's good, 3 stars are anti-pattern: too complicated, as you can see from the link.

> On the plus side, I have quite a bit of confidence in my knowledge of the low level stuff which certainly helps me make decisions in HLL's.

Absolutely. You will "know* what happens at the low level, just will not bother with that. It will not be black box for you, and you will be better programmer for that.

But you need to learn higher-level abstractions, too. Maybe later.... when you get test-infected. I don't do tests first as i should :-( , but test-driven development changed my thinking. But to make it more painless, you need agile dynamic languages to write tests... :-) You'll get there ...

---

### Post by bribaetz on 2007-08-12
whats the problem with goto in a text based program it jumps back to the beginning and besides GOTO is ok. but im a bit on the inexperienced side of new programming languages.

---

### Post by winch on 2007-08-12
> **bribaetz said:**
> whats the problem with goto in a text based program it jumps back to the beginning ...

You can achieve the same result with a loop and subroutines/functions.

Pseudocode.
```

while(1)
{
    //read input
    choice = read_input();
    switch (choice)
    {
        case 'game' : run_game();
                      break;
        case 'calc' : run_calc();
                      break;
    }
}

void run_game()
{
    //run game
}

void run_calc()
{
    //run calculator
}

```

Now it's easier for someone (or you 6 months later) to read the code and understand how the program flows.

In addition the functions that perform the tasks run_game and run_calc are not coupled to the code that handles input.
This means they can be reused. Say for example you want to be able to run commands stored in a file or using a different syntax.
Hard to do if the code that performs the tasks gotos a hardcoded label.

---

### Post by bribaetz on 2007-08-13
ok

---

