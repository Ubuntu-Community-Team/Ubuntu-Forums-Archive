---
title: "Using fish as your shell"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by shakin on 2005-04-13
This How-To will show you how to install and run fish to test out its functionality. If you decide to use fish as your default shell, the last part of this How-To will show you how to make it your default.

Hopefully a few of you will try out fish. I've been using it for a few weeks and find that it's very useful for my day-to-day work. Please read a few of the posts in this thread by liljencrantz to get an idea for how well fish works as a scripting platform.

Why fish makes an excellent shell for anybody who just wants a better way to use their command line interface:

- Context-aware tab completion ('bunzip {tab}' shows all bz2 archives, cd {tab} shows all directories)
- tab completion shows more info about matching files
- tab completion uses scrollable list for matches. Use arrows to scroll.
- tab completion can complete paramaters for built-in commands (eg. ls -{tab} will show paramaters for the ls command)
- Ctrl-Y pasting and Ctrl-K cutting uses the X Windows clipboard.
- Search command history: type first part of previously run command, then use arrows to scoll through matching commands. Or just use arrows to scroll all commands like in bash.
- Syntax highlighting of commands as you type.

Home page: [http://roo.no-ip.org/fish/](http://roo.no-ip.org/fish/)
Features: [http://roo.no-ip.org/fish/user_doc/difference.html](http://roo.no-ip.org/fish/user_doc/difference.html)

How to install so you can test fish without actually making it your default shell:
- Download the latest deb from [http://roo.no-ip.org/fish/](http://roo.no-ip.org/fish/) (currently [version 1.8](http://roo.no-ip.org/fish/files/1.8/fish_1.8_i386.deb))
- sudo dpkg -i fish_1.8_i386.deb (substitute the filename for the version you have downloaded)
- run 'fish' to try it out temporarily (goes away after you close the current terminal window or run 'exit')

How to use fish as your default shell:
- run 'sudo gedit /etc/shells' and add '/usr/local/bin/fish' as a new last line.
- run 'chsh -s /usr/local/bin/fish'.
- logout then back in to make shell change appear. Now every time you open a terminal you will get fish instead of bash.
- You can run 'chsh -s /bin/bash' at any time to make bash your default shell again.

---

### Post by dabeej on 2005-04-13
Nice, never knew this shell even existed! Thanks.

I don't think I will make it my default, but it should be good to play with!

---

### Post by liljencrantz on 2005-04-28
I am the author of [fish](http://roo.no-ip.org/fish/).

Thanks to shaykins help, you can now download i386 debs of the latest versions of fish for use with Ubuntu.

---

### Post by jnk on 2005-04-28
I just installed and tested fish out and I must say that I'm impressed.
Going to test it for a couple of days and then I just might give it a shot as my default shell.
Great work dude.!   :grin:

---

### Post by Eproxus on 2005-04-28
Fish is fresh! I like user friendly! :-)

---

### Post by Gandalf on 2005-04-29
nice shell, good work
thanks

---

### Post by fng on 2005-04-29
Looks like a really nice shell

---

### Post by liljencrantz on 2005-04-29
[QUOTE=Gandalf]nice shell, good work
thanks[/QUOTE]
 Glad to see people here seem to like fish. I suppose in some ways fish is the shell best suited to Ubuntu, since I've tried very hard to make it easier to discover and use all the features in fish. On the other hand, from what I've read of the Zulu, they don't eat a lot of fish. ;-)

---

### Post by Stormy Eyes on 2005-04-29
[QUOTE=liljencrantz]I am the author of [fish](http://roo.no-ip.org/fish/).
[/QUOTE]

Good work, man. I even switched my wife to fish, and she only noticed it this morning. She likes it too.

---

### Post by fng on 2005-04-29
I reported it on the UniverseCandidates page.  
I hope it will be in breezy.

---

### Post by JonahRowley on 2005-04-29
Good tip, but maybe it could be updated with the deb version?  There are a few extra steps in there for RPM.

I checked it out and it's very interesting.  Unfortunately, the author decided to muck around with the syntax of the loops, and to not include variable expansion within quoted strings.  If all you do is type simple commands, fish is great, but I think I'll stick to bash for now :-|

Aside to the fish author, why did you change the syntax?

---

### Post by liljencrantz on 2005-04-29
[QUOTE=fng]I reported it on the UniverseCandidates page.  
I hope it will be in breezy.[/QUOTE]

Having fish in Ubuntu Universe would be great!

---

### Post by liljencrantz on 2005-04-29
[QUOTE=JonahRowley]Good tip, but maybe it could be updated with the deb version?  There are a few extra steps in there for RPM.

I checked it out and it's very interesting. Unfortunately, the author decided to muck around with the syntax of the loops, and to not include variable expansion within quoted strings. If all you do is type simple commands, fish is great, but I think I'll stick to bash for now :|

Aside to the fish author, why did you change the syntax?[/QUOTE]

Because the Bourne syntax is... suboptimal.

[font=Courier New] foo=bar [/font]

and

[font=Courier New] foo = bar[/font]

mean two different things. Didn't we get rid if whitespace sensitive languages together with Disco in the seventies?

$foo '$foo' "$foo" and `$foo` all mean completely different things.

if and case blocks end with the reserved word in reverse, for and while end with 'done' and case sub-clocks end with ';;'. This strongly resembles another one of my favourite languages, Visual Basic.

Variables are expanded to multiple values on spaces. Contents of blocks, pipelines, etc are executed in subshells, so assigning to variables often won't work. Even worse, every shell has it's own rules for which commands are executed in a subshell, so if you want to use a builtin that changes the state, you must never ever use it in a block, pipeline or function, since it won't be portable between shells.

The bash array syntax is bad enough that no one uses it. 

Also, I am bothered by the nature of bash. The original bourne shell was a macro language. This is why, in the original Bourne shell, 

foo=bar
foo=baz;echo $foo

would output 'bar' and not 'baz'.

That is also why variables expand to multiple arguments on spaces - the variable expantion pass was performed before the tokenization pass. But bash is a weird hydrid. It actually has a bison-based BNF syntax, it is implemented like a 'real' language. And this shows in code like the first example above. But bash pretends to ba a macro language for the sake of backward compatibility in some cases, like tokenizing variables on spaces. What you end up with is the perfect compromise - the worst of two worlds. And you can not reliably guess what the behaviour will be.

Compare this to fish:

The syntax is losely inspired by MATLAB. Every type of block ends with 'end':[font=Courier New]

 for i in 1 2 3
echo $i
end

 while true
echo hello
end

 if true
echo yes
else
echo no
end[/font]   

switch $animal
    case cat
        echo evil
    case wolf dog human moose dolphin whale
        echo mammal
    case duck goose albatros
        echo bird
    case shark trout stingray
        echo fish
case "f*"
echo begins with f
case "*"
echo I have no idea
end


Simple and readable. Also please notice that loop and conditional constructs are just commands. The follow the same syntax rules as everything else.

A variable value is not tokenized on spaces, so you don't have to quote every use of variables. Because of this, there is _no_ need for " " style quoting, so fish can have it mean exactly the same thing as ' ' quoting.

Assigning variables is easy and done the same way everything else is done in fish - by using a command. 

[font=Courier New] set foo bar[/font]

assigns 'bar' to the variable 'foo'.
[font=Courier New]
 set foo bar baz[/font]

makes 'foo' into an array containing the items 'bar' and 'baz'.
[font=Courier New]
 echo $foo[2 4][/font]

Outputs the second and fourth items of the array variable foo as separate arguments.
[font=Courier New]
 echo $foo[/font]

Outputs all the elements of the array variable 'foo'. 

Colon separated variables are automatically converted to array variables, and when starting programs, all arrays are folded into colon separated lists. This means you can do things like:
[font=Courier New]
 for i in $PATH; echo $i; end[/font]

to iterate over the PATH entries.

Blocks of commands and pipeline subcommands are never evaluated in subshells, so you can safely use builtins in these contexts wihtout worrying about whether it will work.

---

### Post by JonahRowley on 2005-04-30
> **liljencrantz]Because the Bourne syntax is... suboptimal.[/quote]
Suboptimal or not, it works, it's familiar, and it's portable.

> $foo '$foo' "$foo" and `$foo` all mean completely different things.
As they should.  Giving the user more ways to express themselves is a *good* thing.

> if and case blocks end with the reserved word in reverse, for and while end with 'done' and case sub-clocks end with ' said:**
> 
I don't like this either, but it's a tiny learning curve for the user, and why should your shell stray?  It seems like a minor point to me, why bother changing it?

[quote]The syntax is losely inspired by MATLAB. Every type of block ends with 'end'
What is the advantage of this?  It's cleaner, and more consistent, but are **fi** and **esac** so bad?

[quote]A variable value is not tokenized on spaces, so you don't have to quote every use of variables. Because of this, there is _no_ need for " " style quoting, so fish can have it mean exactly the same thing as ' ' quoting.
How would I, in fish, do the equivalent of:
```
for f in 1 2 3; do echo "some${f}file"; done
```
Without variable expansion inside quotes, this is not intuitive.  Perhaps if ${var} syntax was supported, it could work.  I did try a few things, but most of them gave the unpredictable results you seem to hate so much.
```
for f in 1 2 3; echo some$f"file"; end
```
This produces **some1"file"**, what are those quotes still doing there?
Also, if any variable expansion is part of a single string without space, such as:
```
for f in 1 2 3; echo some$fa"file"; end
```
None of that string is printed, you get three blank lines.  Shouldn't an unassigned variable expand to an empty string?
This code produces more unexpectedness:
```
for f in 1 2 3; echo "some"$f"file"; end
```
This produces lines like **some 1"file"**, where did that space come from?

> Colon separated variables are automatically converted to array variables, and when starting programs, all arrays are folded into colon separated lists. This means you can do things like:
[font=Courier New]for i in $PATH; echo $i; end[/font]
Only colons?  What mechanism defines this?  Bourne has one, the IFS variable.  What makes quotes special?  Seems like that's introducing more of the unexpected behavior you hate.  Also, your IFS seems to do...  nothing?

I don't see any really good reasons to stray from the, admittedly flawed, Bourne-style shell.  It works, it's established, and it's what I, and so many others, have used for years.  If you're going to replace it, why not do something truly better and idealistic, instead of patching up something you obviously do not like?

I really like some of the features in fish, and I will recommend it to people who only use the shell to input commands.  The realtime syntax highlighting, tab completion, all that, is very good, and I can see it being a great help to some people.

BTW, fish also seems exceptionally slow, simple loops are noticably slow, I wouldn't care to guess how long complex commands would take..

---

### Post by liljencrantz on 2005-04-30
> **JonahRowley]Suboptimal or not, it works, it's familiar, and it's portable.
[/QUOTE]

Yes, that is the huge downside to doing something new. I want to see if I can do better. The Bourne syntax is about 30 years old. Things have changed since then.

And by saying it's portable, you ignore many of the things I said I don't like about other shells, like never knowing what is run in a subshell. Try doing

while test -z $foo said:**
> 

As they should.  Giving the user more ways to express themselves is a *good* thing.


Making the default behaviour the one that the user will use the least often is not giving the user more ways to express itself. If it was, Intercal would rule the day. None of the things you can do with the Bourne syntax are hard to do in fish. The difference is that many common, sane things are easier.

Also, the `$foo` syntax is insane, since it looks just like '$foo'. To do the same in fish, just use ($foo), which is not any longer, but much, much easier to read.

> **JonahRowley]

How would I, in fish, do the equivalent of:
```
for f in 1 2 3 said:**
> 

OK, I'll admit this is not completely obvious. The way to do what you want is:

for f in 1 2 3; echo some{$f}file; end

The reason you have to move the $ inside the brackets is that {} simply does bracket expantion of it's contents, but since bracket expantion is performed after variable expantion the end bracket causes a sort of 'pseudotokenization'. I know it seems like an arbitrary syntax change, but it is done that way since it really falls out naturally from the parser. I have considered special-casing to make it legal to write some${f}file just for backwards compatibility.

As to quotes in unquoted strings, fish interprets a Quote inside of an unquoted string as any other character. And since you cant append an unquoted string to a quoted string, "foo"bar become tokenized as two strings as well. This seemed logical to me at the time, but I think I'm going to change it, since people seem to think it is unintuitive. If I do, I'll make it work exactly the way you seem to expect.

[QUOTE=JonahRowley]
Only colons? What mechanism defines this? Bourne has one, the IFS variable. What makes quotes special? Seems like that's introducing more of the unexpected behavior you hate. Also, your IFS seems to do... nothing?

I don't see any really good reasons to stray from the, admittedly flawed, Bourne-style shell. It works, it's established, and it's what I, and so many others, have used for years. If you're going to replace it, why not do something truly better and idealistic, instead of patching up something you obviously do not like?

 
Yes, colons, and for two reasons: If I used IFS, the operation would be destructive. By using one well-defined array separator, I can make sure that when I turn the array variable back to a string for use in subprograms, it remains exactly the same. Would you like it if you started bash from inside fish and suddenly PATH elements where separated by tabs? The other reason is that PATH, CDPATH, SESSION_MANAGER, SSH_CONNECTION, etc all use : as the element separator. Very few environment variable arrays are separated on newlines or anything else. Colon array separation is the most comon way to separate array elements. And if you want to create an array from something else it is trivial.

set secrets (cat /etc/passwd)

will make 'secrets' an array, where every line of input from /etc/passwd, colons and all, is one element. 

As to just 'patching' something I don't like, that is in _no_ way what I've done. I love the shell concept and the general shell syntax. I think it is a very nice, powerfull environment, and I think bash, zsh and tcsh are all very good programs. But I _do_ think they are locked to syntaxes with some very flawed details, and I _do_ think they are very bad at making interactive use easier. 

 [QUOTE=JonahRowley]

I really like some of the features in fish, and I will recommend it to people who only use the shell to input commands. The realtime syntax highlighting, tab completion, all that, is very good, and I can see it being a great help to some people.

BTW, fish also seems exceptionally slow, simple loops are noticably slow, I wouldn't care to guess how long complex commands would take..[/QUOTE]

The fish init files are over 1500 lines long, and fish 1.8 starts up instantly on my computer. (There where two issues in several versions prior to 1.8 that conspired to make fish way to slow) Can you give a more concrete example of when the performance is bad?

---

### Post by seven on 2005-04-30
very nice shell , using it now :)

---

### Post by liljencrantz on 2005-05-02
[QUOTE=JonahRowley]How would I, in fish, do the equivalent of:
```
for f in 1 2 3; do echo "some${f}file"; done
```
Without variable expansion inside quotes, this is not intuitive.  Perhaps if ${var} syntax was supported, it could work.  I did try a few things, but most of them gave the unpredictable results you seem to hate so much.
```
for f in 1 2 3; echo some$f"file"; end
```
This produces **some1"file"**, what are those quotes still doing there?
Also, if any variable expansion is part of a single string without space, such as:
```
for f in 1 2 3; echo some$fa"file"; end
```
None of that string is printed, you get three blank lines.  Shouldn't an unassigned variable expand to an empty string?
This code produces more unexpectedness:
```
for f in 1 2 3; echo "some"$f"file"; end
```
This produces lines like **some 1"file"**, where did that space come from?
[/QUOTE]

I already answered your questins in a previous post, just wanted to say that I have done a bit of hacking this weekend, and I've made a new version of fish which allows you to mix quoted and unquoted strings in a single argument, so that

echo "Number of lines: "$LINES

would output

Number of lines: 20

I will release it after giving it a few days of testing, maybe this weekend.

I am also thinking about changing the block syntax a bit. I want to know beforehand if a block of code is legal, and refuse to run it if not. That is theoretically impossible with regular shell code, since you can do things like:

if true; then $foo

and if $foo is fi, then it is legal and should run, otherwise more input is needed. The way I'm thinking about solving this right now is with these two changes: 

1) Program names must not be a variable, contain wildcards or use any other form of expantion.
2) All commands that start a new block of code must end with a ':'. 

So an if-statement looks like this:

if true:
    echo yay
else:
    echo nay
end

The advantages: One can check beforehand if a statement is legal and complete and refuse to run it otherwise. Bash and zsh _try_ to do this right now, but fail if you do things like:

foo=done;
while true; do echo spam; $foo

All in all, with these changes, fish will soon do a pretty good syntax check of a file before running it, and giving detailed error reports on any issues. It already tries to do all this, but it falls into some of the same traps that the other shells fall in.

---

### Post by rosslaird on 2005-06-27
I have tried fish, and it seems very cool. But it doesn't seem to play nice with vim on my system. When I have fish as my default shell, vim (or gvim) starts up with an error message: 

E484: Can't open file /tmp/...

When I reinstate bash as my default shell, the error goes away.

Hm.

Ross

---

### Post by Skel on 2005-06-27
Seems sweet thanks :)

---

### Post by liljencrantz on 2005-06-27
[QUOTE=rosslaird]I have tried fish, and it seems very cool. But it doesn't seem to play nice with vim on my system. When I have fish as my default shell, vim (or gvim) starts up with an error message: 

E484: Can't open file /tmp/...

When I reinstate bash as my default shell, the error goes away.

Hm.

Ross[/QUOTE]

If vim has trouble reading it's init files, this is most probably not directly caused by the shell. My guess is that the initialization files for bash set up a few environemnt variables that are needed by vim. Try listing them all with the 'set' command, and see if you can isolate the culprit. 

Best of luck


Axel

---

### Post by rosslaird on 2005-06-27
Thanks for the help, Axel.
I know just enough to get myself in trouble, and since I don't relaly know what I'm looking for I've posted the output of "set" below (when I'm not using fish as the default shell):

> BASH=/bin/bash
BASH_ARGC=()
BASH_ARGV=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="3" [1]="00" [2]="16" [3]="1" [4]="release" [5]="i386-pc-linux-gnu")
BASH_VERSION='3.00.16(1)-release'
COLORTERM=Terminal
COLUMNS=80
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-1lVn7fJMbF
DESKTOP_SESSION=xfce4
DIRSTACK=()
DISPLAY=:0.0
DM_CONTROL=/var/run/xdmctl
EUID=1000
GNOME_KEYRING_SOCKET=/tmp/keyring-Z97dsN/socket
GPG_AGENT_INFO=/tmp/gpg-g8TfQB/S.gpg-agent:7807:1
GROUPS=()
GTK2_RC_FILES=/home/ross/.gtkrc-2.0
HISTFILE=/home/ross/.bash_history
HISTFILESIZE=500
HISTSIZE=500
HOME=/home/ross
HOSTNAME=ross
HOSTTYPE=i386
IFS=$' \t\n'
JAVA_HOME=/usr/java/jre1.5.0_03
LANG=en_US.UTF-8
LANGUAGE=en_US:en_GB:en
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LINES=41
LOGNAME=ross
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:'
MACHTYPE=i386-pc-linux-gnu
MAILCHECK=60
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/java/jre1.5.0_03/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/java/jre1.5.0_01/bin
PIPESTATUS=([0]="1")
PPID=8037
PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
PS2='> '
PS4='+ '
PWD=/home/ross
SESSION_MANAGER=local/ross:/tmp/.ICE-unix/7835
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:history:interactive-comments:monitor
SHLVL=2
SSH_AGENT_PID=7831
SSH_AUTH_SOCK=/tmp/ssh-xniOTS7830/agent.7830
TERM=xterm
UID=1000
USER=ross
WINDOWID=27263070
XDM_MANAGED=/var/run/xdmctl/xdmctl-:0,maysd,mayfn,sched,rsvd,method=classic
XFCE4HOME=/home/ross/.config/xfce4


---

### Post by FrzzMan on 2005-07-01
Can't compile it on AMD64 kernel...

---

### Post by liljencrantz on 2005-08-30
[QUOTE=rosslaird]Thanks for the help, Axel.
I know just enough to get myself in trouble, and since I don't relaly know what I'm looking for I've posted the output of "set" below (when I'm not using fish as the default shell):[/QUOTE]

Hi Ross, I could initially not figure out what was causing your troubles, but I'm pretty confident I do now.

The issue is that vim executes the shell pointed to by $SHELL and expects it to support a language syntax that fish simply doesn't have. Fish is not likely to add these features either, since they conflict with the fish syntax. As far as I can see, this is pretty much like firing up whatever editor is pointed to by $EDITOR, and then expect to be able to use emacs-style batch commands on it. The proper thing for vim et. al. to do would be to invoke /bin/sh directly instead of $SHELL. Anyway, as far as I can see, this can be fixed by changing SHELL before calling vim. You can do it by creating a file called '.fish' in your home directory, containing the following:
```

function vim -d 'Vi improved'
	set old_shell $SHELL
	set SHELL /bin/sh
	command vim
	set SHELL $old_shell
end

```

Hope this helps.

---

### Post by liljencrantz on 2005-08-30
[QUOTE=FrzzMan]Can't compile it on AMD64 kernel...[/QUOTE]

The Debian package compiles just fine on AMD64. I'm guessing that this is a question of missing the packages needed to compile fish. You need the packages containing headers for both Xorg and curses, as well as the doxygen package.

If you still can't get fish to compile under AMD64, please post the error messages.

Hope this helps.

---

### Post by one_ro on 2005-09-07
Very very nice... 
Just another question: how does one set aliases in fish?
In bash I would just edit .bashrc
Is there an .fishrc?

---

### Post by liljencrantz on 2005-09-07
[QUOTE=one_ro]Very very nice... 
Just another question: how does one set aliases in fish?
In bash I would just edit .bashrc
Is there an .fishrc?[/QUOTE]

In fish there is a .fish file, used instead of both .bashrc, .bash_profile, .profile, etc.. If you only want to performe some action in certain cases, the variables $fish_login and $fish_interactive are only defined if the shell is a login shell and if the shell is interactive, respecively. So you can conditionally execute a piece of code using:
 ```

if test $fish_login
   echo This is a login shell
end
``` 

Fish has functions instead of aliases, functions allow you to use arguments in any way you like. In fish, the definition of the 'll' command is:

```

function ll
	ls -l $argv
end
``` 

The $argv means that the array containing all arguments (which is always called argv) should be sent on to the ls command.

A slightly more complex example is:
```

function unpack -d "Unpack arbitrary archive files"
	for i in $argv
		switch $i

			case '**.tar'
				tar -xf $i

			case '**.tar.gz' '**.tgz'
				tar -zxf $i

			case '**.tar.bz' '**.tar.bz2' '**.tbz' '**.tbz2'
				 tar -jxf $i

			case '**.rar'
				 unrar e $i

			case '**.zip'
				 unzip $i

			case '**'
				echo File $i is of unknown type

		end
	end
end

```

Which will iterate ofver all the arguments you give, and try too unpack every file. In other words, you use it by writing something like 'unpack foo.tar bar.zip baz.rar'. I find this useful since I can never remember the exact syntax for unpacking rare archive formats like rar and zip.

---

### Post by gorkhal on 2005-09-07
Time to fish  :)

Ooohh...love the configuration options..

---

### Post by Eproxus on 2005-09-13
I'm having the same trouble with vim-gnome.

However fish wont allow me to alias vim-gnome (because of a dash in the name I guess?). How would I go about this?

---

### Post by liljencrantz on 2005-09-14
[QUOTE=Eproxus]I'm having the same trouble with vim-gnome.

However fish wont allow me to alias vim-gnome (because of a dash in the name I guess?). How would I go about this?[/QUOTE]

fish only allows alphanumeric characters and '_' in function names. I'd suggest simply calling your function something else, like 'vim_gnome', 'gvim' or 'vg'.

Axel

---

### Post by Tuxbee on 2005-09-16
My .fish now looks like this
Everything works here, as far as I know
```

# veiligheid

function cp
        cp -i $argv
end
function ln
        ln -i $argv
end
function mv
        mv -i $argv
end
function rm
        rm -i $argv
end

# gemak

function dir
        ls -lh --color=auto $argv
end
function l
        ls -l $argv
end
function ll
        ls -lh --color=auto $argv
end
function lh
        ls -lh -a --color=auto $argv
end
function unpack -d "Unpack arbitrary archive files"
        for i in $argv
                switch $i

                        case '**.tar'
                                tar -xf $i

                        case '**.tar.gz' '**.tgz'
                                tar -zxf $i

                        case '**.tar.bz' '**.tar.bz2' '**.tbz' '**.tbz2'
                                 tar -jxf $i

                        case '**.rar'
                                 unrar e $i

                        case '**.zip'
                                 unzip $i

                        case '**'
                                echo File $i is of unknown type

                end
        end
end
function vi -d 'Vi'
        set old_shell $SHELL
        set SHELL /bin/sh
        command vi $argv
        set SHELL $old_shell
end
```

---

### Post by liljencrantz on 2005-09-16
[QUOTE=Tuxbee]My .fish now looks like this
Everything works here, as far as I know
[/QUOTE]

Nice. Let me know if you have any questions.

---

### Post by Mustard on 2005-10-05
Cool...installed it no problems.  I could only get the version listed in the opening post though, as the website contained no link to any newer ubuntu debian packages.  The only reference to debs was for the Debian distribution.  I'd like to get the lastest version if possible.

---

### Post by pranith on 2005-10-05
hi there,
[COLOR="Red"]The .fish file provided is giving some error
fish: Block missing end
fish: Block missing end
Unmatched end error
Unmatched end error[/COLOR]
plz tell me wat the error is

by the way fish is awesome

---

### Post by liljencrantz on 2005-10-05
[QUOTE=Mustard]Cool...installed it no problems.  I could only get the version listed in the opening post though, as the website contained no link to any newer ubuntu debian packages.  The only reference to debs was for the Debian distribution.  I'd like to get the lastest version if possible.[/QUOTE]
Oops. You can download the latest Debian version from [http://packages.debian.org/unstable/shells/fish]("http://packages.debian.org/unstable/shells/fish"). I'll update the homepage so this is mentioned at once.

---

### Post by liljencrantz on 2005-10-05
[QUOTE=pranith]hi there,
[COLOR="Red"]The .fish file provided is giving some error
fish: Block missing end
fish: Block missing end
Unmatched end error
Unmatched end error[/COLOR]
plz tell me wat the error is
by the way fish is awesome[/QUOTE]

My best guess to what the problem is would be that something went wrong when copying the .fish file from the above post, since the same file seems to work for the original poster. Maybe a few linebreaks got lost or the file got truncated?

---

### Post by jago25_98 on 2006-05-01
I'm worried about incompatibility problems with running fish as my default shell.

Is there anyway I can just set my aterm to use it when I click the aterm icon or use a hotkey?

---

### Post by TitusDalwards on 2006-05-01
oh its so lovely thnx lot friends.

---

### Post by henriquemaia on 2006-05-30
fish shell is awesome. Thanks.

---

### Post by ed_agamemnon on 2006-05-30
does anybody else find that fish cannot handle commands with...

```
'uname -r'
```

...embedded in them?

---

### Post by henriquemaia on 2006-05-30
[quote=ed_agamemnon]does anybody else find that fish cannot handle commands with...

```
'uname -r'
``` 
...embedded in them?[/quote] 
Yes, but neither **bash**. Or does your **bash** handles it?

---

### Post by Gandalf on 2006-05-30
[QUOTE=henriquemaia]Yes, but neither **bash**. Or does your **bash** handles it?[/QUOTE]
Bash handle it But it is not single quote it is backquotes, or $() also works here's an examples
```

`uname -r`
$(uname -r)

```

Or in a for loop
```

for i in $(find / -name "*~"); do rm -f $i; done

```which it deleted backup files but usually we do it much simpler just FYI
```

find / -name "*~" -exec rm -f {} \;

```

Though i never used fish so i donno about sub-shellls but u can try one of the above examples and again it is backquotes ` and not single quotes '

---

### Post by Endolith on 2008-06-25
Are there really problems with compatibility on this?  I'm really confused as to how the Brainstorm Idea has so many negative votes.

[http://brainstorm.ubuntu.com/idea/113/](http://brainstorm.ubuntu.com/idea/113/)

I've been using fish as my default for several months and it's great.  It should be the default for Ubuntu unless there is something even better that I don't know about.

---

### Post by AxiomShell on 2008-08-22
Cool stuff.

How do you reload .fish from the shell (equivalent to source .bashrc)?

Thanks

---

### Post by durand on 2008-08-22
Thanks for reviving this thread! I'd never have known about fish otherwise...

> How do you reload .fish from the shell (equivalent to source .bashrc)?

I'd also like to know that... Maybe we just need to logout and in again?

EDIT: No, that doesn't work :|

---

### Post by durand on 2008-08-24
Worked out how. You have to put the aliases as functions in .config/fish/config.fish.

---

### Post by grappler on 2008-09-30
I've just discovered fish and really like it. To replace bash, however, I'd need it to be able to run the wcd (smart change directory) command. To do this in bash I've put the following into .bashrc 

source /usr/share/wcd/wcd-include.sh

I can't see a replacement for the 'source' command in the fish documentation.  Note that there's a .csh version wcd-include too. 

Can anyone help?

---

### Post by Endolith on 2008-09-30
> **grappler said:**
> I've just discovered fish and really like it. To replace bash, however, I'd need it to be able to run the wcd (smart change directory) command. To do this in bash I've put the following into .bashrc 

```
 source /usr/share/wcd/wcd-include.sh
```I can't see a replacement for the 'source' command in the fish documentation.  Note that there's a .csh version wcd-include too. 

Can anyone help?

"source" is a synonym for ".", which is in any posix-compliant shell and is in fish, too.

```
 . /usr/share/wcd/wcd-include.sh
```I don't know what the equivalent to .bashrc is, but you can create new functions using the function command and then save them with save_function.

What does wcd do, though?  Fish changes directories more easily than bash already.  Just type the name of the directory and press tab.

---

### Post by grappler on 2008-10-01
Thanks for the suggestion, Endolith. I tried at the command line

. /usr/share/wcd/wcd-include.sh

and the corresponding .csh commands, and then wcd is recognised but 
when I call it,  it apparently wants to call 'source" and the same problem arises:

bill@bill-t61p ~> wcd WEATH
fish: Unknown command 'source'
/usr/share/wcd/wcd-include.csh (line 1): rm -f /home/bill/bin/wcd.go; /usr/lib/wcd/wcd.exec \!* ; source /home/bill/bin/wcd.go $argv; 
                                                                                                  ^
in function 'wcd',
	called on standard input,
	with parameter list 'WEATH'

bill@bill-t61p ~> 

I guess I will try to modify the .csh file and see if I can make it work. 



As to what it does, wcd learns the whole directory  tree of the home directory so I can
cd to a directory well down the tree with only a partial name for the subdirectory - for example the command above would (under bash) immediately move me to a directory three levels down called 'WEATHER'.
If there is ambiguity it offers me all of the options and a single keystroke allows me to choose between them. I don't think fish has that capability yet.

---

### Post by grappler on 2008-10-01
Perhaps there is a way map 'source' to . using a function - need to work out how to do that.

---

### Post by Endolith on 2008-10-01
> **grappler said:**
> 
and the corresponding .csh commands, and then wcd is recognised but 
when I call it,  it apparently wants to call 'source" and the same problem arises

Well the . or source command imports the script into your current shell, so wcd-include.sh will be interpreted by fish even though it's a csh script.


> 
As to what it does, wcd learns the whole directory  tree of the home directory so I can
cd to a directory well down the tree with only a partial name for the subdirectory - for example the command above would (under bash) immediately move me to a directory three levels down called 'WEATHER'.
If there is ambiguity it offers me all of the options and a single keystroke allows me to choose between them. I don't think fish has that capability yet.Well you can navigate to a first-level directory in your home directory just by typing the name of that directory.  It doesn't go to deeper directories automatically, but there might be a hidden option for it? 

Edit: I guess not
> 
** Why does the cd command autocompletion list the subdirectories of my home directory as completions?**

 Because they are completions. In fish, if you specify a relative directory to the cd command, i.e. any path that does not start with either './' or '/', the environment variable CDPATH will be examined, and any directories in this path is used as a base direcotry. To disable this feature, write set CDPATH . on the commandline.Maybe you should file a bug and request this functionality.  :)

> **grappler said:**
> Perhaps there is a way map 'source' to . using a function - need to work out how to do that.

```
function source
    . $argv
end

```

---

### Post by durand on 2008-10-01
I would have expected the wcd-include script to use csh instead of fish? Doesn't it say something like #!/bin/csh at the top of the script?

---

### Post by Endolith on 2008-10-01
> **durand said:**
> I would have expected the wcd-include script to use csh instead of fish? Doesn't it say something like #!/bin/csh at the top of the script?

I don't where wcd-include even comes from, but yeah, the "source" command exists in csh also.  [URL="http://www.grymoire.com/Unix/Csh.html"]http://www.grymoire.com/Unix/Csh.html
[/URL]

"source" doesn't exist in fish or dash; only "."  But yeah, you can't just import a csh script into fish and expect it to work out of the box.  You can probably tweak it or rewrite it to make it compatible.  Sounds like something that should be built into fish though, instead of an add-on script.

---

### Post by durand on 2008-10-01
Yes, I know. If #!/bin/csh was at the top of the file, it would use that shell to execute the file instead of fish.

---

### Post by Endolith on 2008-10-01
> **durand said:**
> Yes, I know. If #!/bin/csh was at the top of the file, it would use that shell to execute the file instead of fish.

Not if you're using the source command.  That doesn't start a new shell to execute the script - it ignores the shebang and imports the code directly into the shell you're using.  If it's a csh script then you can only source it into fish if the commands are fish-compatible, too.

[http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html](http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch10s02.html)

---

### Post by durand on 2008-10-01
Yes but this is part of the csh file and I just realised that there is no #!/bin/csh line in it. If you just add that line to the top of the file, source and other commands will be executed with csh instead. 

source will only import the code into fish if the source command is being run from fish and it's not in this case.

---

### Post by Endolith on 2008-10-01
> **durand said:**
> Yes but this is part of the csh file and I just realised that there is no #!/bin/csh line in it. If you just add that line to the top of the file, source and other commands will be executed with csh instead.

source will only import the code into fish if the source command is being run from fish and it's not in this case.

When you are using fish, and call 

```
. /usr/share/wcd/wcd-include.sh
```

it is interpreted by fish.  The commands in wcd-include.sh are run in the current fish shell without any regard for the #!/bin/csh line.  If the commands do not do exactly the same thing in fish as they would do in csh, the script will not work this way.

Create this script:

```
#!/bin/csh
0-0
```

and then call it like this:

```
. testscript
```

and it will say this:

```
fish: Unknown command “0-0”
```

because fish is ignoring the /bin/csh and interpreting the commands itself.

---

### Post by grappler on 2008-10-01
Thanks for all of the suggestions. Here is wcd-include.csh - it's only a one-liner:

```
 alias wcd "rm -f $HOME/bin/wcd.go; /usr/lib/wcd/wcd.exec \!* ; source $HOME/bin/wcd.go"
```

I've tried adding 

```
#!/bin/csh
```

as the first line, and replacing 'source'  by '.' in all combinations, 
None of these work. When I run wcd I get
> stat: No such file or directory



I guess the only issues left are the use of 'alias' or '\!*' but don't know enough about fish (yet) to translate. 

Addition of wcd to fish would enhance its capability significantly for me.

---

### Post by Endolith on 2008-10-01
```
 alias wcd "rm -f $HOME/bin/wcd.go; /usr/lib/wcd/wcd.exec \!* ; source $HOME/bin/wcd.go"
```

Let's see.  "alias" doesn't exist in fish; use "function" instead.

Then you remove a file?  That should be identical in fish.  $HOME works in fish functions, too, though it goes to the same place as "~".  Is this the same as csh?  There's no "bin" directory in my home.

Then you call an executable?  That should be identical, too, but I don't know what "\!*" means.

Then use . instead of source:

```
function wcd
    rm -f $HOME/bin/wcd.go
    /usr/lib/wcd/wcd.exec \!*
    . $HOME/bin/wcd.go
end
```

This imports the wcd.go file into your shell, though, so this file would have to be compatible with fish.  What do you get with "cat ~/bin/wcd.go"?

---

### Post by grappler on 2008-10-01
Here's the result of cat ~/bin/wcd.go after doing 'wcd WEATH'

```
#!/bin/bash
cd /home/bill/GRANTS/CCC/WEATHER
```


I've tried using the function Endolith sent as a replacement for wcd and then when I do 'wcd WEATH' I get the message:
> 
stat: No such file or directory

---

### Post by grappler on 2008-10-01
I've solved it!  Thanks Endolith - just a slight mod of your function



```
function wcd
    rm -f $HOME/bin/wcd.go
    /usr/lib/wcd/wcd.exec $argv
    . $HOME/bin/wcd.go
end
```

If I run this in fish wcd works as in bash!

Wonderful - I can now use fish and wcd!

---

### Post by Endolith on 2008-10-02
> **grappler said:**
> Here's the result of cat ~/bin/wcd.go after doing 'wcd WEATH'

```
#!/bin/bash
cd /home/bill/GRANTS/CCC/WEATHER
```

Well when you do ". wcd.go", it imports this into fish, ignores "#!/bin/bash" and calls cd, which is a valid command in fish, too, so that should work.  What does this file contain if there is more than one directory that matches, though?

> I've tried using the function Endolith sent as a replacement for wcd and then when I do 'wcd WEATH' I get the message: [quote]stat: No such file or directory [/quote]

I don't know where stat comes from...

> **grappler said:**
> I've solved it!  Thanks Endolith - just a slight mod of your function

```
function wcd
    rm -f $HOME/bin/wcd.go
    /usr/lib/wcd/wcd.exec $argv
    . $HOME/bin/wcd.go
end
```If I run this in fish wcd works as in bash!

Wonderful - I can now use fish and wcd!

Interesting.  Does it work in all cases?  So "\!*" return the arguments to a csh script?

---

### Post by grappler on 2008-10-02
> **Endolith said:**
> Well when you do ". wcd.go", it imports this into fish, ignores "#!/bin/bash" and calls cd, which is a valid command in fish, too, so that should work.  What does this file contain if there is more than one directory that matches, though?

When there is ambiguity wcd presents a list of possibilities from which you choose with a single keystroke - they are labelled by letters. So the file only ever contains a single "cd' to a directory. 


> **Endolith said:**
> 
Interesting.  Does it work in all cases?  So "\!*" return the arguments to a csh script?

I've tried it on a number of cases and it appears to work as in bash - but with a slight change. The command 'wcd -s' which is used to rebuild the treedata file works as before. I created a new directory 'TEST' several levels down the directory tree, ran 'wcd -s' and then did 'wcd TEST' and it went straight to it. However, if I use a regexp as the argument I have to put it in quotes to make it work. For example ```
wcd TES*
``` does not work  but ```
wcd 'TES*'
``` does. When I do this under bash the quotes are not needed. Is there a fix for this?

---

### Post by mkrahmeh on 2008-10-04
I installed the fish shell..its really cool
but it seems i cant view the exit code of the last command run

```
echo $?
```
returns the following message 
```
fish: The '$' character begins a variable name. The character “&#62464;”, which directly followed a '$', is not allowed as a part of a variable name, and variable names may not be zero characters long. To learn more about variable expansion in fish, type “help expand-variable”.

```

so how can i view the exit code in fish ??

---

### Post by alsh on 2008-10-08
> **mkrahmeh said:**
> I installed the fish shell..its really cool
but it seems i cant view the exit code of the last command run

```
echo $?
```
returns the following message 
```
fish: The '$' character begins a variable name. The character “&#62464;”, which directly followed a '$', is not allowed as a part of a variable name, and variable names may not be zero characters long. To learn more about variable expansion in fish, type “help expand-variable”.

```

so how can i view the exit code in fish ??

"Use the $status variable as documented at
[http://fishshell.org/user_doc/index.html#variables-status](http://fishshell.org/user_doc/index.html#variables-status)"

(Thanks to fish mailing list participants! [http://comments.gmane.org/gmane.comp.shells.fish.user/1969](http://comments.gmane.org/gmane.comp.shells.fish.user/1969))

---

### Post by dhbabey on 2008-11-02
everything was working fine before upgrading to ubuntu 8.10 intrepid, however now when I open a new tab in gnome-terminal (or the new konsole for that matter) which are both supposed to open the new tab in the current directory it doesn't work with fish...

bash will open the new tab in the current directory, however for whatever reason if I have fish set as my default shell, it just opens the new tab in my home directory...

any ideas?
thanks

---

### Post by durand on 2008-11-03
I'd like to know this as well. What I find is that a new tab uses the same directory but fish doesn't even say this in the prompt...

---

### Post by dhbabey on 2008-11-03
I was just noticing this too, it seems that the first command that gets executed will be executed in the proper directory (despite fish sayings its in the home directory) but as soon as the command returns, the shell will be dumped into the home directory.

---

### Post by Geraba on 2009-12-08
(sorry for resurrecting this topic...)
Does this method also work with zsh? Can I try it temporaly using the same procedure?

---

### Post by Endolith on 2009-12-08
> **Geraba said:**
> (sorry for resurrecting this topic...)
Does this method also work with zsh? Can I try it temporaly using the same procedure?

Yes, but make sure you get the path to zsh right.  If you want to try it temporarily, just type "zsh".  :)

---

### Post by fishexe on 2010-05-21
If anybody has had experience with fish stopping adding commands to history or knows about fixing shell problems, I would appreciate help in this thread:
[http://ubuntuforums.org/showthread.php?p=9335114#post9335114](http://ubuntuforums.org/showthread.php?p=9335114#post9335114)
I like fish a lot but it has not been remembering my commands lately and I hope someone knows of a fix.

---

### Post by 0x_ on 2010-05-27
Fish is great! Thanks for the pointer!

How do I delete the command history?

Any ideas?

Thanks.


----->>>>>
Never mind:
history file is in $HOME/.config/fish/

---

