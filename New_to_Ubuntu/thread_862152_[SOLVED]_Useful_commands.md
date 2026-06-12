---
title: "[SOLVED] Useful commands"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-07-17
Hy all!
Can you post a list of the most used (and useful) commands in Ubuntu?For example, I know that ```
gedit /etc/X11/xorg.conf
``` lets you modify your xorg.conf file.I know it's a command for editing the sources list, repair broken packages and so on.
Do you understand what I want?

---

### Post by benfindlay on 2008-07-17
There's a pretty awesome thread located [here]("http://ubuntuforums.org/showthread.php?t=683871") which covers lots of useful commands in depth.

Hope this helps!

Ben

---

### Post by hyper_ch on 2008-07-17
seach for Foss ubuntu cheat sheet on google.

---

### Post by sharks on 2008-07-17
A beginner thread
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by ilrudie on 2008-07-17
FOSSwire did a nice one page Ubuntu commands cheat sheet.  It can't be too hard to track down on their site.

---

### Post by Canis familiaris on 2008-07-17
ls and cd
The ultimate commands

EDIT: 
ls - lists files
cd - moves o the directory

A very good site which teaches the Linux Terminal.
[http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by Canis familiaris on 2008-07-17
> **Troll_the_Great said:**
> Hy all!
Can you post a list of the most used (and useful) commands in Ubuntu?For example, I know that ```
gedit /etc/X11/xorg.conf
``` lets you modify your xorg.conf file.I know it's a command for editing the sources list, repair broken packages and so on.
Do you understand what I want?

For viewing software sources for your repos i.e. viewing the actual text files. Of course you do not need it. You can go to System->Administration->Software Sources.
```
gedit /etc/apt/sources.list
```

To edit it you need to precede the command by sudo, of course.

gedit part is notepad equivalent of GNOME, though much more powerful.
/etc/apt/sources.list is the path to the sources.list file.

YOu can use gedit to modify any text file.
Just do: 
gedit <path of file>

Of course you can use nano, or vim as well. ;)

To repair broken packages
```
dpkg --configure -a
```

---

### Post by tuxxy on 2008-07-17
apt-get  & sudo   o_O

---

### Post by Canis familiaris on 2008-07-17
> **sharks said:**
> A beginner thread
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

That was damn useful

---

### Post by Troll_the_Great on 2008-07-17
> **sharks said:**
> A beginner thread
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
Thank you very much, that was exactly what I was looking for!

---

### Post by sharks on 2008-07-17
if ur thread is solved , then mark ur thread solved from thread tools.

---

### Post by Canis familiaris on 2008-07-17
> **sharks said:**
> if ur thread is solved , then mark ur thread solved from thread tools.

How could the quest for knowledge for commands :grin: could ever be fulfilled? I dont think this thread will be solved ever. :-D

---

### Post by Troll_the_Great on 2008-07-17
I agree with Anurag_panda on this one...But I will mark the thread as solved :)

---

### Post by sharks on 2008-07-17
> **Anurag_panda said:**
> How could the quest for knowledge for commands :grin: could ever be fulfilled? I dont think this thread will be solved ever. :-D

Ok. I jsut told it bcoz Troll_the_Great said Thank you very much, that was exactly what I was looking for!

---

### Post by Inxsible on 2008-07-17
In addition to all the wonderful replies....

if you do not want to remember or type in all the lengthy commands, you can create aliases for it in the bash_profile or bashrc files.

I use aliases for almost everything from aptitude to ls to grep....

---

### Post by Troll_the_Great on 2008-07-17
Inxsible, how do you create aliases?It would help me allot, I'm still noob at linux...

---

### Post by Inxsible on 2008-07-17
> **Troll_the_Great said:**
> Inxsible, how do you create aliases?It would help me allot, I'm still noob at linux...
I list all my aliases in my bashrc so they are all available to me on boot
some examples:```
alias aptin='sudo aptitude install'
alias aptout='sudo aptitude purge'
alias obc='leafpad ~/.config/openboxrc.xml
alias obm='leafpad ~/.config/openbox/menu.xml
``` Now I simply use this to install anything like so```
aptin *package-name*
```It automatically runs sudo aptitude install and asks me for my root password etc. The obm and obc are for menu and configuration of openbox. I dont have to navigate to the folder and then open the file in gui nor do I have to type in editor /path to file.

All I type is obm and BAM !! my menu.xml opens in leafpad - ready for me to edit it.

The above is a simple example. I can post my bashrc once I get home which also uses commands like du, df etc.

---

### Post by Troll_the_Great on 2008-07-17
Please do that, I'll look at the post later.But how do you create them?Just type "alias aptin=..."?

---

### Post by Inxsible on 2008-07-17
> **Troll_the_Great said:**
> Please do that, I'll look at the post later.But how do you create them?Just type "alias aptin=..."?yes. its as easy as that :)

make sure you have single OR double quotes around the entire command that you are creating the alias for.

```
alias obm='leafpad ~/.config/openbox/menu.xml'
```

---

### Post by Troll_the_Great on 2008-07-17
Thank you, this is WONDERFUL!It's so easy to remember and type commands this way.Incredible!For a noob is very difficult to remember for instance "gedit /etc/X11/xorg.conf" but "display" anyone can remember.By the way, does it matter if I use simple quotes ' or double quotes "?
Thanks again, you're me hero!

EDIT:Is there a command to list all my aliases, in case I forget them?

EDIT 2:"I list all my aliases in my bashrc so they are all available to me on boot" 
How do I do that?

---

### Post by Vivaldi Gloria on 2008-07-17
> Is there a command to list all my aliases, in case I forget them?

Actually

```
alias
```

is that command.

> "I list all my aliases in my bashrc so they are all available to me on boot" How do I do that?

Press Alt+F2 and start

```
gksudo gedit ~/.bashrc
```

and add your aliases in that file, for example add

```

alias cd..="cd .."
alias ls='ls --color=auto'
```

etc.

---

### Post by Troll_the_Great on 2008-07-17
Thanks Gloria.When I open the file where should I put them?Anywhere?At the beginning?At the end?Does it matters?And also does it matter if I use ' instead of " ?

PS:I bet it's not you in the avatar!:lolflag:

---

### Post by Vivaldi Gloria on 2008-07-17
> When I open the file where should I put them?Anywhere?At the beginning?At the end?

Anywhere is OK. If there are already some alias lines there then put after them.

> And also does it matter if I use ' instead of " ?

It should be ' not ". 

> PS:I bet it's not you in the avatar!:lolflag:

Are you telling me that you have never heard of Vivaldi Gloria, the gorilla which loves linux more than bananas? ;)

---

### Post by philinux on 2008-07-17
If you've not come across them these are useful.

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by hovzio on 2008-07-17
> **Vivaldi Gloria said:**
> Actually

```
alias
```

is that command.



Press Alt+F2 and start

```
gksudo gedit ~/.bashrc
```

and add your aliases in that file, for example add

```

alias cd..="cd .."
alias ls='ls --color=auto'
```

etc.

Hi,I'm pretty sure that if you want to edit your own  ~/.bashrc file you wont need root privleges. If you want to edit them systemwide (for all users) under /etc/bashrc you will need to use gksudo. Nevertheless your own ~/.bashrc will override system defaults.

One of my favorit commands is:

```
sudo apt-get autoremove package
```

This removes an installed package and **all** of the dependencies that were installed along with it. (That is if they are not needed elsewhere.)

---

### Post by Vivaldi Gloria on 2008-07-17
> **hovzio said:**
> Hi,I'm pretty sure that if you want to edit your own  ~/.bashrc file you wont need root privleges. If you want to edit them systemwide (for all users) under /etc/bashrc you will need to use gksudo. Nevertheless your own ~/.bashrc will override system defaults.

Yes, of course you're right, gksudo is not needed there. Thanks for the correction.

---

### Post by Promaster91 on 2008-07-17
```

sudo apt-get update && sudo apt-get autoremove

```
Removes any unnecessary packages.

```

sudo rm -fr  ~/.local/share/Trash/files/*

```
Removes all files from trash, especially the ones that need permissions.

---

### Post by Troll_the_Great on 2008-07-17
Thanks allot all for your answers, they really helped.I will mark the thread as solved, but feel free to post new threads if you want.

> Are you telling me that you have never heard of Vivaldi Gloria, the gorilla which loves linux more than bananas?
And Gloria, I'll send you a box full of bananas!:lolflag:

---

### Post by Canis familiaris on 2008-07-17
@Troll_the_great
Since you are using aliases, I would like to inform you that the alias you create say you created an alias by this command.
```
alias l='ls -al'
```
Then this alias l will work only for the running session. To make sure the alias works everytime you log in, you have to edit .bashrc file.

To do so:
```
gedit .bashrc
```

Scroll to the end of the file and add the aliases you want to add.

READ THE FOLLOWING FOR MORE INFO
```
# This hash is makes the text followed in the same line as comment.
# Add your Comments for future reference
# I would recommend you to add the next line as comment so that you could
# differentiate the system generated command to your custom added commands

# Manually Added Commands
alias l='ls -al'
alias xorg='gedit /etc/X11/xorg.conf'

#Not only aliases you could also add commands
gedit
#Not that you'll need it ;)
```

Keep in mind though never to put space b/w the equal to and preceding and succeeding text.

---

### Post by Canis familiaris on 2008-07-17
> **Promaster91 said:**
> ```

[code]
sudo rm -fr  ~/.local/share/Trash/files/*

```
Removes all files from trash, especially the ones that need permissions.
Yes this is useful since it empties the trash but keep in mind that sudo rm -rf command is dangerous and never should be used anywhere else.
Before executing this command double check and I mean DOUBLE CHECK that you are doing things right AND
[SIZE="5"]NEVER DO THIS
[/SIZE]
```
sudo rm -rf /
```

[SIZE="5"]Never. Because it wipes out completely your hard disk without warning .
And you cannot recover your files by any simple means.[/SIZE]

---

### Post by Inxsible on 2008-07-17
Having a confirmation for cp, mv and rm really helps. So I have created the following aliases```
alias cp='cp -i'
alias rm='rm -i'
alias mv='mv -i'
```That way you can use rm and then it will ask for confirmation and then you can take appropriate action.

---

### Post by Canis familiaris on 2008-07-18
> **Inxsible said:**
> Having a confirmation for cp, mv and rm really helps. So I have created the following aliases```
alias cp='cp -i'
alias rm='rm -i'
alias mv='mv -i'
```That way you can use rm and then it will ask for confirmation and then you can take appropriate action.

It will not work for sudo.
For it to work with sudo. add:
```
alias sudo="sudo "
```

---

### Post by Inxsible on 2008-07-18
> **Anurag_panda said:**
> It will not work for sudo.
For it to work with sudo. add:
```
alias sudo="sudo "
```That alias is not gonna help any except put a space after sudo. You are aliasing sudo with sudo + a space.

In any case, you were assuming that my user is in sudoers....Infact I dont even have sudo installed.

I use the root account when I want admin privs. So that does not apply to me. I would start getting errors if I added sudo ;)

---

### Post by Canis familiaris on 2008-07-18
> **Inxsible said:**
> That alias is not gonna help any except put a space after sudo. You are aliasing sudo with sudo + a space.

In any case, you were assuming that my user is in sudoers....Infact I dont even have sudo installed.

I use the root account when I want admin privs. So that does not apply to me. I would start getting errors if I added sudo ;)

This may make this more clearer:

[http://ubuntuforums.org/showpost.php?p=221245&postcount=11](http://ubuntuforums.org/showpost.php?p=221245&postcount=11)

Of course not applicable to you but applicable to most users here ;)

---

