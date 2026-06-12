---
title: "Some useful beginning commands"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Core2Extremist on 2008-07-23
I was rudely introduced to the console window when X Server failed and I, a mere noob to command prompts, was forced to fend for myself in a graphical interface. It kept saying "no screen exists," even though my monitor was clearly plugged in. Windows ran fine, so I didn't understand what the problem was. As it turned out, somewhere down the line I had switched monitor ports. Windows didn't care, but X Server couldn't find display 0 at all... since my monitor was display 1. Easy fix... after several months of giving up :P

Anyway, my friend gave me some really, really useful pointers. They're easy enough to remember, and they'll help you fend for yourself in a command window:

```
apropos TEXT
```
apropos searches for functions that relate to TEXT. If TEXT has a space in it, such as "shut down", put quotes around the phrase. This helps if you're looking for a command (i.e. the command-line shut down command) but you have no idea what you should type in.

```
man COMMAND
```
man brings up the user manual for the COMMAND you specify. Used in conjunction with apropos, you can figure out how to do just about anything.

Finally, here's something I found useful as a noob:

Most shell commands (in BASH, at least) go something like this

```
command [-options] argument1 argument2 argument3 ... argumentN
```
You experienced users are probably rolling your eyes, but *I* found it very helpful.

here's an example I was finally able to cobble together after several minutes of vain attempts:

```
sudo mount -t smbfs //192.168.1.100/C "/home/user_name/Desktop Shared"
```

sudo stands for Super User DO - if a command returns "must be done as root" or "priveledge denied" or something to that effect, using sudo as a prefix usually fixes that

-t is one of those flags. In this case, it tell the mount command what filesystem to use

smbfs is the argument, or input, to the -t flag. -t smbfs essentially says "use the smbfs file system for this operation"

//192.168.1.100/C is the first argument. In the case of mount, is says "this is the directory I want to mount" In this case, it's a network location (specified by //) - it's my desktop computer (with that IP address)

"/home/user_name/Desktop Shared" is the second argument. For the mount command, it's the mount point, or where you wind up clicking to access the files you want access to. It's surrounded by quotes since it has a space in it.

For all of the commands I've come across, spaces split up flags, arguments and other information. If an argument has a space inside of it, it's a good idea to surround it in quotes just in case.

So anyway, that's what I learned in about 30 minutes of talking on the phone and it was extremely useful. In fact, using the man command helped me find out that my monitor was just connected to the wrong port in the first place :P

---

### Post by apswartz on 2008-07-23
After a while you may find that there is a lot of stuff you might prefer doing by command line because of the speed and power.

---

