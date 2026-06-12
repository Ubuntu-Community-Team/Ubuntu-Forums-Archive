---
title: "Would you use my program?"
date: 2009-05-06
forum: Programming Talk
---

### Post by Bodsda on 2009-05-06
Hi guys, 

I have an idea for a program and before I get majorly started on it I just wanted to know if people would actually use it (which would be cool! :P)

The idea is a program which allows you to quickly store complicated commands after you have used them, and then for quick lookup and reuse, for example consider this

```
sudo apt-get update && sudo apt-get upgrade
```

Now, my program could store this command and basically change it to a number, so you would do something like this

```
foo@bar:~$ sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......
foo@bar:~$ cheat --store !!
sudo apt-get update && sudo apt-get upgrade stored as value (1)

foo@bar:~$ cheat --run 1
running: sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......

```

That would be one of the features of my program,

Lemme no what you think :0

Thanks,

Bodsda

---

### Post by akoskm on 2009-05-06
> **Bodsda said:**
> Hi guys, 

I have an idea for a program and before I get majorly started on it I just wanted to know if people would actually use it (which would be cool! :P)

The idea is a program which allows you to quickly store complicated commands after you have used them, and then for quick lookup and reuse, for example consider this

```
sudo apt-get update && sudo apt-get upgrade
```

Now, my program could store this command and basically change it to a number, so you would do something like this

```
foo@bar:~$ sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......
foo@bar:~$ cheat --store !!
sudo apt-get update && sudo apt-get upgrade stored as value (1)

foo@bar:~$ cheat --run 1
running: sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......

```

That would be one of the features of my program,

Lemme no what you think :0

Thanks,

Bodsda

Like an Address book. Interesting. :)

---

### Post by Yacoby on 2009-05-06
Maybe allowing the user to define strings instead of just having out the next number? I can never remember numbers once they go past 5, but with strings I can take a guess at the key I would have used, and get it right 99% of the time.

---

### Post by Bodsda on 2009-05-06
> **Yacoby said:**
> Maybe allowing the user to define strings instead of just having out the next number? I can never remember numbers once they go past 5, but with strings I can take a guess at the key I would have used, and get it right 99% of the time.

Yeah, It could have both, a numeric value and a user set string, also you will be able to list the entries like so

```
foo@bar:~$ cheat --store somecommand --key "some"
somecommand stored as value (1) key (some)

foo@bar:~$ cheat --store othercommand --key "other"
othercommand stored as value (2) key (other)

foo@bar:~$ cheat --list
(1) somecommand : (some)
(2) othercommand: (other)

foo@bar:~$

```

That could be good :)

Thanks,

Bodsda

---

### Post by ad_267 on 2009-05-06
This can pretty much all be done with bash history already. [http://www.linux.com/articles/114036](http://www.linux.com/articles/114036) and [http://www.deadman.org/bash.html](http://www.deadman.org/bash.html) are two good articles. Also see "man history". fc (fix command) is another useful command, "fc -s" means repeat the same command. You can pass it a number corresponding to the number from your history list. See [http://www.faqs.org/docs/bashman/bashref_107.html](http://www.faqs.org/docs/bashman/bashref_107.html)

---

### Post by Bodsda on 2009-05-06
Having to learn the intricacies of bash history recall just to redo a command you ran earlier is a bit overkill, and with my method the commands will still be in the same place 2 months later

---

### Post by mkrahmeh on 2009-05-06
that would be really cool. I've always worked with .bash_history to figure out long commands used earlier, but sometimes it fails me or works in an unexpected behaviour (like not finding a recent command). 

hope we find versions with additional features as well to stretch to the line of replacing the history method, and maybe aliases :D

---

### Post by .Maleficus. on 2009-05-06
I probably wouldn't, since any command longer than 10 characters usually has an alias for me, but I could see where it would be useful.  I would try to make your command shorter though, since it is still about 1/3 the length of the other command.  Something like 'ch -r 1' would be more useful IMO.

---

### Post by Kilon on 2009-05-06
> **Bodsda said:**
> Having to learn the intricacies of bash history recall just to redo a command you ran earlier is a bit overkill, and with my method the commands will still be in the same place 2 months later

I would use it if you made a GUI version as well

---

### Post by benj1 on 2009-05-06
have you seen ipython?
it does exactly the same thing

---

### Post by damis648 on 2009-05-06
You can already do most of that with Aliases.

---

### Post by mmix on 2009-05-06
sorry i don't,

usually, i don't type more longer than 5 characters in console.

here is my own slang  :)
all code belongs to GPLv3

```

ll: alias 'ls -l'
md: symlink to mkdir
rd: symlink to rmdir
smi: shell script of 'sudo make install'
smu: 'sudo make uninstall'
smm: 'sudo make modules_install'
pud: 'pushd'
pod: 'popd'

```

---

### Post by nbo10 on 2009-05-06
No, aliases work just fine.

---

### Post by Bodsda on 2009-05-06
Its more then just aliases, and a hell of a lot quicker, without the need of restarting your shell session every time you change the aliases,

Thanks,

Bodsda

---

### Post by nvteighen on 2009-05-06
> **Bodsda said:**
> Its more then just aliases, and a hell of a lot quicker, without the need of restarting your shell session every time you change the aliases,

Thanks,

Bodsda
Well, you can restart by just using the **reset** command :)

I think aliases already do what you want, but as you probably see, there is no interface (GUI or text-based or both) to store aliases in an easy way but editing the ~/.bashrc file. Maybe your program should just be a way to store aliases, edit them and modify them rather than a new system that does almost the same than the old one. 

Such an interface would be IMO useful and I bet people would use it.

---

### Post by JK3mp on 2009-05-06
> **Bodsda said:**
> Its more then just aliases, and a hell of a lot quicker, without the need of restarting your shell session every time you change the aliases,

Thanks,

Bodsda

Thats what i would go for... build first, state features, let people try, and PROVE improvement over the other similiar software. Use the other ones listed and if possible, implement some features into yours, then improve upon them(will make it a bit easier), gl :)

---

### Post by Bodsda on 2009-05-06
> **JK3mp said:**
> Thats what i would go for... build first, state features, let people try, and PROVE improvement over the other similiar software. Use the other ones listed and if possible, implement some features into yours, then improve upon them(will make it a bit easier), gl :)

I think thats pretty much my plan :) get a working program then release early + often and improve from their, cheers :)

> **nvteighen said:**
> Well, you can restart by just using the **reset** command :)

I think aliases already do what you want, but as you probably see, there is no interface (GUI or text-based or both) to store aliases in an easy way but editing the ~/.bashrc file. Maybe your program should just be a way to store aliases, edit them and modify them rather than a new system that does almost the same than the old one. 

Such an interface would be IMO useful and I bet people would use it.

So you think it should just stick to alias's or focus primarily on alias's rather then other features?

---

### Post by nvteighen on 2009-05-06
> **Bodsda said:**
> 
So you think it should just stick to alias's or focus primarily on alias's rather then other features?

At least for that command-shortcut feature, I guess a front-end for configuring bash aliases would be the safest. Whether to include other features is up to you... though I like the "1 task, 1 tool" philosophy.

---

### Post by leandromartinez98 on 2009-05-06
$history !grep upgrade

   96  sudo apt-get update; sudo apt-get dist-upgrade


$!96

... running the upgrade


I can't see how it can be more practical than that. Also aliases 
are fine for command used many times. Concerning a GUI interface
for configuring aliases, no, I wouldn't use it, I don't see any
advantange relative to opening the .bashrc file.

---

### Post by Bodsda on 2009-05-06
I think il start with just alias's, though they will not be bash ones, so 

```
cheat --use updateme
```
could be completely different to 
```
foo@bar:~$ updateme
```

As for a gui I have no intention of using gui's for any type of configuration/settings type tasks and I dont want a gui for this tool. but if some people would like a gui, the code will be released gpl v3 so they are welcome to make their own that utilizes this program (when i release it)

> **leandromartinez98 said:**
> $history !grep upgrade

   96  sudo apt-get update; sudo apt-get dist-upgrade


$!96

... running the upgrade


I can't see how it can be more practical than that. Also aliases 
are fine for command used many times. Concerning a GUI interface
for configuring aliases, no, I wouldn't use it, I don't see any
advantange relative to opening the .bashrc file.

The advantage is speed and reliability, will you be able to view all of your commands with that? How will you remember that its $!96 not !97 and will it still work in a weeks time?

---

### Post by slakkie on 2009-05-06
I would not use it, aliases or shell functions are just as handy, or just small scripts in my bin-dir. Could be handy, have to admit that :)

BTW, maybe have a look at the sources of todo.sh: [http://ginatrapani.github.com/todo.txt-cli/](http://ginatrapani.github.com/todo.txt-cli/)

This is a todo script, but could be adjusted for your program (if you fancy shell scripting).

---

### Post by Penguin Guy on 2009-05-06
Sorry; no. If I really needed something like this I would just add some aliases to my .bashrc file - I'd never use something like this nearly enough to bother installing a program.

---

### Post by leandromartinez98 on 2009-05-06
> **Bodsda said:**
> 

The advantage is speed and reliability, will you be able to view all of your commands with that? How will you remember that its $!96 not !97 and will it still work in a weeks time?

For a weeks time you will need to set up a search function for the
command in your case, in which you will do essentially the same
thing as in grep, so I don't see any advantage in terms of speed.
And, if you will put an alias for a command in your program, then
using bash aliases is just fine. You can even do that in one line:

echo "alias command='long command'" >> .bashrc; source .bashrc

Done, the long command can now be used by the alias.

---

### Post by crazyfuturamanoob on 2009-05-06
Yeah, aliases are much better.

---

### Post by Reiger on 2009-05-06
Aliases and good auto-completion pretty much get you there without the need of installing anything. And I only use the shell for the commands I _know_ which means I don't need to lookup & remember them: I already know them by heart. ;)

---

### Post by Bodsda on 2009-05-06
Hmm, well thanks for all your thoughts, I'm still gonna go ahead and write it :) 

Thanks,

Bodsda

---

### Post by UbuKunubi on 2009-05-06
I think that while there are alternatives I think your approach has certain merits.
Personally I'd use, in conjunction with xdotool to automate certain jobs that are just beyond 'real' programming.

Keep up the good work.

---

### Post by Bodsda on 2009-05-06
> **UbuKunubi said:**
> I think that while there are alternatives I think your approach has certain merits.
Personally I'd use, in conjunction with xdotool to automate certain jobs that are just beyond 'real' programming.

Keep up the good work.

Cheers :)

Bodsda

---

### Post by dacorr on 2009-05-06
I think it would depend on how often i would need the command, so a list of supplied common commands/usefull commands would be useful.

maybe script building functionallity by clicking commands

But for security some kind of sanity check first before running commands

Dac

---

### Post by Bodsda on 2009-05-07
> **dacorr said:**
> I think it would depend on how often i would need the command, so a list of supplied common commands/usefull commands would be useful.

maybe script building functionallity by clicking commands

But for security some kind of sanity check first before running commands

Dac

By sanity check do you mean check the command to make sure its not obviously malicious like -rf removing root *?

---

### Post by stinger30au on 2009-05-07
Bodsda  i suggest you just go ahead and do it  if you ask and wait for a consensis it will never happen  i suggest you open a page for it at sorceforge, post a link here and start programming   when you start, others will follow

---

### Post by Bodsda on 2009-05-07
> **stinger30au said:**
> Bodsda  i suggest you just go ahead and do it  if you ask and wait for a consensis it will never happen  i suggest you open a page for it at sorceforge, post a link here and start programming   when you start, others will follow

Oh, i forgot to mention that i have already started it :), once i get something in a sort of working order i'l put it on launchpad and release the source

---

### Post by Krupski on 2009-05-07
> **Bodsda said:**
> Hi guys, 

I have an idea for a program and before I get majorly started on it I just wanted to know if people would actually use it (which would be cool! :P)

The idea is a program which allows you to quickly store complicated commands after you have used them, and then for quick lookup and reuse, for example consider this

```
sudo apt-get update && sudo apt-get upgrade
```

Now, my program could store this command and basically change it to a number, so you would do something like this

```
foo@bar:~$ sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......
foo@bar:~$ cheat --store !!
sudo apt-get update && sudo apt-get upgrade stored as value (1)

foo@bar:~$ cheat --run 1
running: sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......

```

That would be one of the features of my program,

Lemme no what you think :0

Thanks,

Bodsda

What I would like is to have command line recall like JPSoft's "4NT" does in Windows XP.

It has the normal "up arrow" thing like BASH has, but also one can enter the first few letters of a past command and then up arrow brings it back.

For example, I can type:

ls
chdir
cfdisk
cp

etc...

then if I type "ch" and up arrow, "chdir" is returned.

If I type "c" then up arrow, it returns cp first, then cfdisk, then chdir (as up arrow is pressed again).

I know BASH can do sorta like this with ctrl-r... but the 4NT way is SO much nicer. I would love for it to work that way.

-- Roger

---

### Post by Bodsda on 2009-05-07
> **Krupski said:**
> What I would like is to have command line recall like JPSoft's "4NT" does in Windows XP.

It has the normal "up arrow" thing like BASH has, but also one can enter the first few letters of a past command and then up arrow brings it back.

For example, I can type:

ls
chdir
cfdisk
cp

etc...

then if I type "ch" and up arrow, "chdir" is returned.

If I type "c" then up arrow, it returns cp first, then cfdisk, then chdir (as up arrow is pressed again).

I know BASH can do sorta like this with ctrl-r... but the 4NT way is SO much nicer. I would love for it to work that way.

-- Roger

I dont know if I could write that, or at least not at the moment, need to do some research,

I can add it to the wishlist though :)

Thanks,

Bodsda

---

### Post by dmm1285 on 2009-05-07
> **Krupski said:**
> What I would like is to have command line recall like JPSoft's "4NT" does in Windows XP.

It has the normal "up arrow" thing like BASH has, but also one can enter the first few letters of a past command and then up arrow brings it back.

For example, I can type:

ls
chdir
cfdisk
cp

etc...

then if I type "ch" and up arrow, "chdir" is returned.

If I type "c" then up arrow, it returns cp first, then cfdisk, then chdir (as up arrow is pressed again).

I know BASH can do sorta like this with ctrl-r... but the 4NT way is SO much nicer. I would love for it to work that way.

-- Roger

Put this in your .inputrc

"\e[B": history-search-forward
"\e[A": history-search-backward

---

### Post by CyanideSyntax on 2009-05-07
> **Bodsda said:**
> Hi guys, 

I have an idea for a program and before I get majorly started on it I just wanted to know if people would actually use it (which would be cool! :P)

The idea is a program which allows you to quickly store complicated commands after you have used them, and then for quick lookup and reuse, for example consider this

```
sudo apt-get update && sudo apt-get upgrade
```

Now, my program could store this command and basically change it to a number, so you would do something like this

```
foo@bar:~$ sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......
foo@bar:~$ cheat --store !!
sudo apt-get update && sudo apt-get upgrade stored as value (1)

foo@bar:~$ cheat --run 1
running: sudo apt-get update && sudo apt-get upgrade
......
.
(apt stuff)
.
......

```

That would be one of the features of my program,

Lemme no what you think :0

Thanks,

Bodsda

Personally, i would LOVE something like this, but it seems overcomplicated. I think it was mentioned somewhere before, but simplify the command.

a GUI would be nice, but not really necessary.You can think about that in due time.

But overall, go for it.
if you go through with it, PM me and ill beta test it for you.

=D

---

### Post by Ambly on 2009-05-07
Im really new on linux (about a month) and is something like that what im looking to do.
 Something like "sudo ps3-boot-game-os" + "password", to reboot to ps3 OS. Im searching information and i think that a bash file will do it. 
 Rigth?

Go for it and let as know, i will try your program!

---

### Post by Penguin Guy on 2009-05-08
Actually; thinking about it, it would be a nice idea to have a small program such as 'rem'.
[COLOR="Green"]"alias "$1"="$2"" >> .bashrc[/COLOR] (this is an example and this command doesn't actually work)

So instead of opening your bashrc file you can just use this command to make aliases (using aliases in the terminal is only temporary).

---

### Post by Bodsda on 2009-07-23
> **Penguin Guy said:**
> Actually; thinking about it, it would be a nice idea to have a small program such as 'rem'.
[COLOR="Green"]"alias "$1"="$2"" >> .bashrc[/COLOR] (this is an example and this command doesn't actually work)

So instead of opening your bashrc file you can just use this command to make aliases (using aliases in the terminal is only temporary).

Cheatsheet can be used for aliases.

btw, the official release has now been released!!

Here is the code
[https://launchpad.net/cheatsheet](https://launchpad.net/cheatsheet)

Any feedback will be appreciated,

Regards,

Bodsda

---

### Post by skullmunky on 2009-08-01
I would really like this as a kind of bookmark menu in Konsole, so that you can save and then run both elaborate and common commands from a menu instead of typing them.  It'd be useful for cases like elaborate mencoder commands, and also for short commands that you don't use often but are hard to remember.  Diagnostic commands come to mind, all the critical little ones that you have to use when something's not working: lspci, lsusb, dmesg, lshal, fdisk -l, etc.  It could also be really helpful for people when they start learning how to use the command line.

---

### Post by Bodsda on 2009-08-02
> **skullmunky said:**
> I would really like this as a kind of bookmark menu in Konsole, so that you can save and then run both elaborate and common commands from a menu instead of typing them.  It'd be useful for cases like elaborate mencoder commands, and also for short commands that you don't use often but are hard to remember.  Diagnostic commands come to mind, all the critical little ones that you have to use when something's not working: lspci, lsusb, dmesg, lshal, fdisk -l, etc.  It could also be really helpful for people when they start learning how to use the command line.

With cheatsheet you dont need to type the commands, just copy and paste them in, save them then recall them usng the index number or key.

Personally I don't see the point in using it for any of the commands you listed above as they are all memorable and small, it would take more effort to go through menu's, or do a cheatsheet --use then it would to type the command.

---

### Post by ahmatti on 2009-08-02
Looks like an interesting utility, I will give it a try tomorrow and see if it brings something aliases don't. I think it will be more useful for keeping rarely used "difficult" commands in one place instead of my current system "stack of randomly named text files" :) My aliases are usually really short so cheatsheet --use seems too long for me, well maybe I'll make an alias for it too.

---

### Post by skullmunky on 2009-08-02
> **Bodsda said:**
> With cheatsheet you dont need to type the commands, just copy and paste them in, save them then recall them usng the index number or key.

Personally I don't see the point in using it for any of the commands you listed above as they are all memorable and small, it would take more effort to go through menu's, or do a cheatsheet --use then it would to type the command.

I think that's just it, one person's idea of memorable is not the same as someone else's.  And memorableness (? is that a word...) fades when you don't use something frequently.  Let's say I'm debugging my wacom driver configuration - in that case I use all those commands a few hundred times in the space of an hour.  

But then I get it working, and I don't have another, like, device driver problem for another year or two.  I forget most of those commands, even if they're short, and have to go and google all over the place and pick through forum threads to try and remember what they are.  I've been using the UNIX command line for 15 years, too, so I think there's just only so much stuff I can keep in my head at once.

I could keep a text file or a blog or something with all this stuff in it, naturally, which would be exactly the same as having it in a menu, just less convenient.  plus then I always forget where I saved that file.

Well anyway I should shut my mouth and go implement this already .. :)

---

