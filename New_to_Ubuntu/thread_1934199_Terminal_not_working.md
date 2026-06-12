---
title: "Terminal not working"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by s1wood on 2012-03-01
I am typing a command  into the terminal and pressing 'enter' in the usual way, the screen jerks slightly and nothing happens. I have tried severa ties and also with the byobu terminal - same thing.
I've re-installed the gnome terminal which hasn't helped.
This is 11.04 on my netbook.

Help please!

Susan

---

### Post by coolman98 on 2012-03-01
u may have  defective install

---

### Post by winh8r on 2012-03-01
What command are you trying to run?

---

### Post by Ms. Daisy on 2012-03-01
Is this a new problem? Have you ever tried to run this command before?
> Computers are my mid-life crisis - it could have been worse! LOL!

---

### Post by cortman on 2012-03-01
To check if the commands are actually executing (but not showing up) try something like

```
touch your_toes
```

and see if a file your_toes (or whatever you want to call it) has been created in your /home directory.

---

### Post by s1wood on 2012-03-02
I was trying to install Calibre with a copied & pasted command but I have tried sudo apt-get update to no effect.
I don't use the terminal very often and I can't be certain I have used it since I re-installed 11.04 a few months ago. (after trying 11.10)
I don't think anything can be happening because I was using sudo and haven't been asked for my password.
touch your_toes doesn't appear in Home.

I remain puzzled.

Susan

---

### Post by winh8r on 2012-03-02
If you go to the Ubuntu Software Centre you can install Calibre without using the terminal at all.

With regard to the terminal, if you open it and enter

```
top
```

does it show anything?

---

### Post by oldos2er on 2012-03-02
> **s1wood said:**
> I was trying to install Calibre with a copied & pasted command but I have tried sudo apt-get update to no effect.


Can you please post the terminal output from these commands?

---

### Post by Paddy Landau on 2012-03-02
> **s1wood said:**
> I was trying to install Calibre with a copied & pasted command...
Where did you get this command? As winh8r wrote, you just install it from the Ubuntu Software Centre, so I'm wondering why you were given a command?

Please tell us what the command was.

---

### Post by s1wood on 2012-03-02
The command was from Calibre-ebook.com linux download
sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
I can't post the outcome of any command because there is no outcome. I did try top

Susan

---

### Post by nothingspecial on 2012-03-02
Hi susan,

When a command works (does what it is supposed to do), it doesn't let you know it was successful. When it fails it gives an error.

It may just be that the command worked :)

---

### Post by Ms. Daisy on 2012-03-02
> **nothingspecial said:**
> Hi susan,

When a command works (does what it is supposed to do), it doesn't let you know it was successful. When it fails it gives an error.

It may just be that the command worked :)
True, but top should have output no matter what.

Did you drop to a python shell?

---

### Post by s1wood on 2012-03-02
>Did you drop to a python shell?<  I wouldn't know one if I saw it!

Nothing happens! Never mind the calibre download, nothing happens with any command!

What I really want to do now is get my kindle software to open (I have just bought a cheap e-reader) but as soon as I post about that someone is going to tell me to use the terminal, so I have to get the **** thing working. 

Perhaps if I remove it and completley reinstall it...

Susan

---

### Post by winh8r on 2012-03-02
It does seem odd that nothing is working, even putting the installing stuff to one side the very basic system commands should be functional, that was why I suggested the "top" command as it would just list the processes running in order of resource usage, but since that didn't work there must be something strange going on.

Try going to the Software Centre and searching for 

```
terminator
``` (you can read the description in the software centre)

and install it.

then launch it from the menu and see if it kicks things back into place.

---

### Post by matt_symes on 2012-03-02
Hi

Can you type commands into a console ? You should at least have some working consoles.

Press ctrl + alt + F1 at the same time. It will display tty1. This is a console.

Enter your user name and password (it will not be echoed to the screen) and then type the command

```
htop
```

as suggested before. You should see text on the screen. Press ctrl + c to stop htop.

Press ctrl + alt + F7 you get back to the desktop.

Report back on what happens in the console.

Kind regards

---

### Post by s1wood on 2012-03-02
Terminator works!

the gnome terminal still doesn't.
What is the difference bewtween a terminal and a console? 

Susan

---

### Post by winh8r on 2012-03-02
Glad you got it working again!

Probably best to use it to run 

```
sudo apt-get check
```

then 

```
sudo apt-get update
```


The console is the primary command line interface between the user and the operating system, this is available to the user before the more familiar "graphical environment" becomes available after boot time.

The terminal is used to refer to graphical command line interface found after booting into the "normal" user environment.

In very simple terms, the console is a big black screen with nothing else on it except white text whilst the terminal generally has user defined controls and is wrapped up in a graphical interface.

Not the best description in the world but you get the idea .....I hope.

---

### Post by matt_symes on 2012-03-02
Hi

> What is the difference bewtween a terminal and a console?

gnome-terminal is a pseudo terminal (a terminal emulator). It runs inside X (i.e it runs in a graphical environment; in a window).

A console does not run in a graphical environment. It does not need X (a windowed environment) to run. It's just white text on a black screen.

Checking to see if you could enter commands in a console would have shown that the problem was not with bash (the default shell you run when using gnome-terminal or a console) but with either X or gnome-terminal.

The ability to run commands using terminator (or indeed xterm which is installed by default in Ubuntu) would suggest that the problem with gnome-terminal is a problem with gnome-terminal's settings and not with X.

> the gnome terminal still doesn't.

I would check gnome-terminals settings next.

Kind regards

---

### Post by Krytarik on 2012-03-02
> **matt_symes said:**
> The ability to run commands using terminator (or indeed xterm which is installed by default in Ubuntu) would suggest that the problem with gnome-terminal is a problem with gnome-terminal's settings and not with X.
[..]
I would check gnome-terminals settings next.
+1; just reset them altogether:
```
gconftool-2 --recursive-unset /apps/gnome-terminal
```Regards.

---

### Post by Paddy Landau on 2012-03-03
Susan, for future note, please always use the Ubuntu Software Centre  (USC) if possible to install programs. Avoid downloading software from  the Internet unless you absolutely have to. To install Calibre, open the  USC, search for "calibre", and press "Install". It's that easy.

But before you install Calibre from the USC, we first need to fix your  problem. I have never seen the terminal "jerk" before, nor have I seen  it fail to present any output. Obviously, something has gone bizarrely  wrong.

Please create a new user (open *Users and Groups*); log out (or reboot); log into the new user; open a terminal; type any command (e.g. *uname*); and let us know what happens. That way, we will know whether the system was compromised or only your user.

---

### Post by s1wood on 2012-03-04
The gconf tool code appears to have worked, the gnome terminal is now running normally, so thanks for that one.

Thanks for all the advice.

Susan
 

PS It didn't occur to me that Calibre was in the USC, I have now installed it from there.

---

### Post by rainvoyager on 2013-02-22
In my setup, the Terminator is not working either. Meaning it also gives Segmentation Fault for command like "ls", or "df".

What was wrong? 

> **winh8r said:**
> It does seem odd that nothing is working, even putting the installing stuff to one side the very basic system commands should be functional, that was why I suggested the "top" command as it would just list the processes running in order of resource usage, but since that didn't work there must be something strange going on.

Try going to the Software Centre and searching for 

```
terminator
``` (you can read the description in the software centre)

and install it.

then launch it from the menu and see if it kicks things back into place.

---

### Post by Paddy Landau on 2013-02-22
> **rainvoyager said:**
> In my setup, the Terminator is not working either. Meaning it also gives Segmentation Fault for command like "ls", or "df".
This is not the same problem as the OP's. Please start a new thread, so that other people will see it. In the new thread, explain what has happened, and post an example of the output.

---

