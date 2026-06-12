---
title: "Enter your password to perform administrative tasks"
date: 2008-11-12
forum: Programming Talk
---

### Post by tjajab on 2008-11-12
Hi. I am trying to develop a python gnome application which may need root access in some situations. I know that some applications in gnome popups a dialog saying "Enter your password to perform administrative tasks" when root access is needed. Is there an easy API somewhere so I can make my python application popup this dialog?

Thanks in advance

---

### Post by drubin on 2008-11-12
> **tjajab said:**
> Hi. I am trying to develop a python gnome application which may need root access in some situations. I know that some applications in gnome popups a dialog saying "Enter your password to perform administrative tasks" when root access is needed. Is there an easy API somewhere so I can make my python application popup this dialog?

Thanks in advance

Most things I have seen before they execute the commend they would put gksudo before it.

Not 100% sure if you will be executing the command. or just ask users to put gksudo before it.

Another option would be to make a wrapper python script that checks if the current user is root if not  execute  gksudo readScript.py.

Those are not the nicest ways of doing it but should work. If any one has any better ideas I am all ears I would like to know as well :)

---

### Post by tseliot on 2008-11-12
You might want to use PolicyKit.

---

### Post by drubin on 2008-11-12
> **tseliot said:**
> You might want to use PolicyKit.

Thanks tseliot. Looks like a much better option then my wrapper script :)
[http://en.wikipedia.org/wiki/PolicyKit](http://en.wikipedia.org/wiki/PolicyKit)

---

### Post by Flimm on 2008-11-12
I had the exact same problem for my project Epidermis. Here's what I found in my research, and what I ended up using.

I dived into the code of Update Manager, the app that I thought handles asking for root permissions the best. Unfortunately, its method is hard to copy. It basically runs synaptic using gksu and passes to it arguments, and itt uses clever X tricks to make the synaptic window look like a child window of update-manager, but actually, they're two seperate processes, and two seperate apps.
Get the code for update-manager by running:
apt-get source update-manager
Isn't open source great?

Gdebi, the graphical deb installer, probably runs itself using gksu and some additional arguments. Haven't checked the source code of this one, but you can of course, cause you're free.

You could prefix each command for which you need root access with gksu, but this has lots of drawbacks, especially if the user has a 0 long timeout on password memory. You could also write the list of commands to a bash script in a temp location, and use gksu on that, but you have to be able to predict all the commands in advance, something which you probably won't be able to do.
I even thought of using DBUS to communicate between a process running with normal priveleges, and a process with root priveleges, only to find out that it's impossible to use DBUS between processes run by different users. I gather PackageKit can solve this problem, by I haven't tried that.

What I ended using was pexpect. I ran a bash terminal in the background with root priveleges, I got the root password using gksu. I used pexpect to send commands to this process and detect when the command finished. From a user's perspective, it works perfectly.
You can take a look at my code by downloading the epidermis branch:```
bzr branch lp:epidermis
```
and taking a look at shell.py (as well as the two sh scripts under data)
I wrapped the functionality in the BashRootShell class, here's how you could use it:
[php]import shell
rootp = shell.BashRootShell()
rootp.prepare() # this asks the user for the password using gksu
rootp.do("command") # run commands as root, will not ask for password again
rootp.do("command2")
rootp.exit() # ends the background process running as root[/php]

I'd be very interested to see if you find other ways of doing it, as my method has drawbacks. I chose to put the code in one class so that I can easily replace it later on.

---

### Post by tjajab on 2008-11-13
Thanks for the feedback! I will look more deeply into this and share my experiences later on.

---

### Post by tjajab on 2008-11-13
Actually just putting gksudo in front of my commands worked pretty well. I looked at PolicyKit, but as I am not an experienced enough python developer I felt it would be a little to hard to use for me, at least until some easy enough python library shows up.

Thanks again for the help.

---

