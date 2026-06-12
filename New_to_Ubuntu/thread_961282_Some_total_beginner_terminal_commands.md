---
title: "Some total beginner terminal commands"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by random turnip on 2008-10-28
I want to start to understand more about the commands for the terminal in Ubuntu.

I was wondering you could show me a few of the basic things that I'm gonna need to know. (i.e. how to save setting, what some of the basic bits of the codes mean).

Thanks :KS

---

### Post by germanix on 2008-10-28
[http://linuxcommand.org/](http://linuxcommand.org/)

Go to the above link. All you need to know you will find there.

---

### Post by Kevbert on 2008-10-28
Have a look at this [[COLOR="Red"]cheat sheet[/COLOR]]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/").

---

### Post by tarps87 on 2008-10-28
One of the most important commands to know I think is
```
sudo rm -rf *.* 
```
This is delete the contents of what ever folder you are in so this command SHOULD NEVER BE USED
sudo = this give you root/administrative privileges
rm = remove
-f = forcefuly
* = wildcard

---

### Post by boof1988 on 2008-10-28
> **random turnip said:**
> I want to start to understand more about the commands for the terminal in Ubuntu.

I was wondering you could show me a few of the basic things that I'm gonna need to know. (i.e. how to save setting, what some of the basic bits of the codes mean).

Thanks :KS

Here are a few sites (Linked) I use for learning:
[INDENT][LIST=1]
[*][Basic Commands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands\)
[*][Command Line How-To](https://help.ubuntu.com/community/CommandlineHowto)
[*][RootSudo](https://help.ubuntu.com/community/RootSudo)
[*][Nano How-To](https://help.ubuntu.com/community/Nano?action=show&redirect=NanoHowto)
[/LIST][/INDENT]

To anyone... Please correct me if I'm wrong on these as I'm a noob.

The first one is my favorite.  It gives some of the basic commands early on so I don't have to read a bunch of stuff to get to the basics (change directory etc)

The second is included for reference.

The third explains the command "sudo".  This command seems to allow 'root' access to stuff.  I'm new to this stuff so it's a bit hazy for me.  Since it allows so much access, the user should know what they are 'commanding'?

The fourth explains Nano.  I have seen it used to access/read/edit/save text files.  When preceded by "sudo", it (I think) allows access/read/edit/save privileges to root files.

To random turnip,

I hope these help a little.

---

### Post by drakeman007 on 2008-10-28
> **random turnip said:**
> I want to start to understand more about the commands for the terminal in Ubuntu.

I was wondering you could show me a few of the basic things that I'm gonna need to know. (i.e. how to save setting, what some of the basic bits of the codes mean).

Thanks :KS

Hey write me pm message if you are interested in the commands, im newbie too, and i learn many things with an ebook! write me!..
Regards!:guitar:

---

### Post by drakeman007 on 2008-10-28
> **Kevbert said:**
> Have a look at this [[COLOR="Red"]cheat sheet[/COLOR]]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/").

Hey great page for reference! 

Hehehe thanks!

---

### Post by boof1988 on 2008-10-28
Here's a couple commands I've used to set up [ufw](https://wiki.ubuntu.com/UbuntuFirewall) (Ubuntu firewall).

```
sudo ufw enable
sudo ufw default deny
sudo ufw allow from 192.168.7.7 to any
```

First Line: 'sudo' allows 'root' privileges to 'enable' ufw (the firewall).

Second Line: Set the 'default' of 'ufw' to 'deny' all.

Third Line: Create a 'ufw' rule to 'allow' 192.168.7.7 access to any port on the host machine (where the firewall is being set-up).
[INDENT]Note: I'm still learning what ports are.  I used this type of command when I was trying to set-up a network printer since the client (computer which is sending the print job) needs access to the required ports on the server (host computer where printer is located).  See [[COLOR="Blue"]here[/COLOR]](http://www.funnestra.org/ubuntu/hardy/#ipp)[/INDENT]

```
sudo ufw status
```

Displays the status of ufw.

```
info ufw
```

Displays information on the application 'ufw'

I ran into problems when I wanted to delete some of the rules.  I couldn't figure out how the original rule was input.

Here is an example to use when you know what was input.

```
To delete a rule, simply prefix the original rule with delete.  For example, if the original rule was:

'ufw deny 80/tcp'

Use this to delete this rule:

'ufw delete deny 80/tcp'
```

So I used the following to open up the file where the rules are stored (I found this location by reading 'info ufw') and delete the rule in the file.  NOTE: I don't know if this is a recommended way or not.

```
sudo nano /var/lib/ufw/user.rules
```


References:
[[COLOR="Blue"]ufw @ Ubuntu[/COLOR]](https://wiki.ubuntu.com/UbuntuFirewall)
[[COLOR="Blue"]Hardy Heron How-To @ funnestra.org[/COLOR]](http://www.funnestra.org/ubuntu/hardy/)

---

### Post by eddVRS on 2008-10-28
Hi,

Have a read of this thread by Kyral, I found this invaluable when I was starting out-

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by Lakeside on 2008-10-28
Just want to say `thanks` to everyone who posted all these great links (all bookmarked now lol) and to random turnip for asking (so I didn`t have to ;) )

---

### Post by random turnip on 2008-10-29
Lol, yeah, thanks alot guys, alot of really helpful links there!

@ drakeman007, I will do if you want, but look at some of the sites on this list first!

---

### Post by hey_ram on 2008-10-29
a word of advice..

do try to lookup the man pages for every command BEFORE you try it out..
there are some such as the 'rm' and 'rm -rf' commands that are particularly dangerous if used without caution.

apart from that, try to use the command line for as many tasks as possible.

u could try by giving yourself a challenge of not using a mouse or any other pointer device every time u use ubuntu...

that might be an interesting challenge...

---

### Post by philinux on 2008-10-29
Dont forget about this forum.

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

A mine of info.

---

### Post by corncob on 2009-10-04
> **eddVRS said:**
> Hi,

Have a read of this thread by Kyral, I found this invaluable when I was starting out-

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Exactly what I was going to say, word for word.

A useful command that I don't see mentioned is "cat".  It shows you the contents of a file
```
cat /boot/grub/menu.lst
```
"gedit" will open it too and allow you to edit it (if you put "gksudo" at the beginning) or you can use "gedit" as a notepad and save it as a text file.

---

