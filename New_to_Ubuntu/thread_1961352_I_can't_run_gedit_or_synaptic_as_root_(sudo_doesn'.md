---
title: "I can't run gedit or synaptic as root (sudo doesn't work, neither does gksudo) 12.04"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Kneegrowplease on 2012-04-19
```
pedro@pedro-ET1330:~$ sudo gedit /etc/modules
[sudo] password for pedro: 
Cannot open display: 
```


```
pedro@pedro-ET1330:~$ sudo synaptic

(synaptic:4085): Gtk-WARNING **: cannot open display: 


```
just upgraded from 11.10

---

### Post by HiImTye on 2012-04-19
```
DISPLAY=:0 gksudo gedit whatever.file
```

---

### Post by Kneegrowplease on 2012-04-19
> **HiImTye said:**
> ```
DISPLAY=:0 gksudo gedit whatever.file
```

> pedro@pedro-ET1330:~$ DISPLAY=:0 gksudo gedit /etc/modules
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.


???

---

### Post by HiImTye on 2012-04-19
post the output of
```
echo $DISPLAY
```

---

### Post by Kneegrowplease on 2012-04-19
> **HiImTye said:**
> post the output of
```
echo $DISPLAY
```

```
pedro@pedro-ET1330:~$ echo $DISPLAY
:0.0

```

---

### Post by houseworkshy on 2012-04-19
Get your important files backed up before doing anything else.  Without sudo it's going to be tricky.  I've used gksu rather than gksudo but having maned the comand don't think it make much differance.  Looks like your system doesn't think that you are admin, which would be normal if your not.  If you are then the problem will be something to do with permissions and groups and to play with them you need to be admin.  You could try "apropos admin" then man the results for ideas but assuming you are the administrator  I'm out of my depth and can only  give your thread a bump.

---

### Post by Kneegrowplease on 2012-04-19
> **houseworkshy said:**
> Get your important files backed up before doing anything else.  Without sudo it's going to be tricky.  I've used gksu rather than gksudo but having maned the comand don't think it make much differance.  Looks like your system doesn't think that you are admin, which would be normal if your not.  If you are then the problem will be something to do with permissions and groups and to play with them you need to be admin.  You could try "apropos admin" then man the results for ideas but assuming you are the administrator  I'm out of my depth and can only  give your thread a bump.



I am admin, went to user accounts and double checked. sudo does work for some things right now, just not others...thanks for the feedback

---

### Post by HiImTye on 2012-04-19
> **Kneegrowplease said:**
> ```
pedro@pedro-ET1330:~$ echo $DISPLAY
:0.0

```
```
DISPLAY=:0.0 gksudo gedit whatever.file
```

---

### Post by flurospar on 2012-04-19
Not running the graphical interface? That seems to be the issue!

---

### Post by Kneegrowplease on 2012-04-19
> **flurospar said:**
> Not running the graphical interface? That seems to be the issue!

two beans for captain obvious:popcorn:



reminds me of apple telling my parents to just turn off wifi encryption because of connection issues.....


UNACCEPTABLE

---

### Post by forrestcupp on 2012-04-19
> **Kneegrowplease said:**
> two beans for captain obvious:popcorn:



reminds me of apple telling my parents to just turn off wifi encryption because of connection issues.....


UNACCEPTABLE

You probably should clarify this. Was that the problem, or are you saying that he gave you a silly response?

Are you running these commands from a terminal in Unity?

---

### Post by Kneegrowplease on 2012-04-19
> **forrestcupp said:**
> You probably should clarify this. Was that the problem, or are you saying that he gave you a silly response?

Are you running these commands from a terminal in Unity?


I though it was a bit silly, maybe my response was a bit rude. for that I appologize. isn't anyone else experiencing this problem? I can run nano with the sudo cmd, but not gedit, synaptic, or gparted...


unity is the GUI? I am using gnome classic and yes, from a terminal.

---

### Post by Kneegrowplease on 2012-04-19
Maybe THIS is my problem:


> The problem is caused by user 'you' owning the display and then user 'root' wanting to get away with it. Yes, 'root' is the supreme God of your system and is omni potent. But not for X11.



sound valid?

---

### Post by rhss6-2011 on 2012-04-19
Try CTRL+ALT+F1

login -- type your username which should be lowercase (press enter)
Password for: ----Type your password and press enter so that you log in

```
sudo apt-get install -f -y && sudo apt-get install -y ubuntu-desktop
```

That should do the trick there... It'll install a GUI and from there you can go to town...

---

### Post by sudodus on 2012-04-19
> **Kneegrowplease said:**
> ```
pedro@pedro-ET1330:~$ sudo gedit /etc/modules
[sudo] password for pedro: 
Cannot open display: 
```


```
pedro@pedro-ET1330:~$ sudo synaptic

(synaptic:4085): Gtk-WARNING **: cannot open display: 


```
just upgraded from 11.10
Maybe we can go back to post #1. Sudo works well for text mode commands but you need gksudo for GUI commands. Please try
```
gksudo gedit /etc/modules
```
```
gksudo synaptic
```
(without the DISPLAY business in the beginning of the line)

In older versions, sudo might have worked for some GUI commands, but it is *not* recommended.

---

### Post by Kneegrowplease on 2012-04-19
> **sudodus said:**
> Maybe we can go back to post #1. Sudo works well for text mode commands but you need gksudo for GUI commands. Please try
```
gksudo gedit /etc/modules
```
```
gksudo synaptic
```
(without the DISPLAY business in the beginning of the line)

In older versions, sudo might have worked for some GUI commands, but it is *not* recommended.

gksudo isn't working, it either crashes immediately with no output in my terminal or asks for Administrative passwd and then crashes....

---

### Post by Kneegrowplease on 2012-04-19
> **rhss6-2011 said:**
> Try CTRL+ALT+F1

login -- type your username which should be lowercase (press enter)
Password for: ----Type your password and press enter so that you log in

```
sudo apt-get install -f -y && sudo apt-get install -y ubuntu-desktop
```

That should do the trick there... It'll install a GUI and from there you can go to town...



Didn't work unfortunately....

---

### Post by sudodus on 2012-04-19
> **Kneegrowplease said:**
> gksudo isn't working, it either crashes immediately with no output in my terminal or asks for Administrative passwd and then crashes....
What about
```
gksu gedit /etc/modules
```
```
gksu synaptic
```

If neither of these works, you need to update your system or reinstall gksudo. Run one command line each time and ***watch the response from the system***: are there any errors, or tips what to do?
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get autoclean
```
```
sudo apt-get purge gksudo
```
```
sudo apt-get install gksudo
```
You may need to repeat the sequence and possibly add some other command if there are problems.

---

### Post by sudodus on 2012-04-19
Just another idea, that might be easy for you to test. It is not recommended, because of security risks, but for the purpose of finding a way to solve your problem, we might allow an exception.

First use sudo to stay as root (test both commands)
```
sudo -i
``` or ```
sudo -s
```
Then issue the command as root
```
gedit
``` or
```
synaptic
``` or
```
gparted
```
What happens?

---

### Post by Johnny3 on 2012-04-19
Try going to synaptic package manager and status and seeing if you need to update a package or broke packages.
Good Luck and God Bless Johnny3 65+++

---

### Post by Kneegrowplease on 2012-04-19
> **sudodus said:**
> Just another idea, that might be easy for you to test. It is not recommended, because of security risks, but for the purpose of finding a way to solve your problem, we might allow an exception.

First use sudo to stay as root (test both commands)
```
sudo -i
``` or ```
sudo -s
```
Then issue the command as root
```
gedit
``` or
```
synaptic
``` or
```
gparted
```
What happens?

 did that earlier, didn't work for me. same exact output. purging and reinstalling gksudo now

---

### Post by Kneegrowplease on 2012-04-19
> **sudodus said:**
> Just another idea, that might be easy for you to test. It is not recommended, because of security risks, but for the purpose of finding a way to solve your problem, we might allow an exception.

First use sudo to stay as root (test both commands)
```
sudo -i
``` or ```
sudo -s
```
Then issue the command as root
```
gedit
``` or
```
synaptic
``` or
```
gparted
```
What happens?


Package gksudo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gksudo' has no installation candidate

---

### Post by newbie-user on 2012-04-20
To run gedit as root, you have to sudo as another user.

```
sudo -u [user currently logged in] gedit
```

But then you're not really running gedit as root, but at least you can start it using the root account.

---

### Post by Kneegrowplease on 2012-04-20
> **newbie-user said:**
> To run gedit as root, you have to sudo as another user.

```
sudo -u [user currently logged in] gedit
```

But then you're not really running gedit as root, but at least you can start it using the root account.


```


pedro@pedro-ET1330:~$ sudo -u pedro gedit /etc/modules
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
Sessions still open, not unmounting

```

---

### Post by sudodus on 2012-04-20
> **sudodus said:**
> Just another idea, that might be easy for you to test. It is not recommended, because of security risks, but for the purpose of finding a way to solve your problem, we might allow an exception.

First use sudo to stay as root (test both commands)
```
sudo -i
``` or ```
sudo -s
```
Then issue the command as root
```
gedit
``` or
```
synaptic
``` or
```
gparted
```
What happens?
Just for debugging: What happens when you run those commands? Please describe the output (if any) to the screen and to the terminal window!

(I have noticed that you cannot reinstall gksudo, so there is something wrong with your installation. We can try to solve that later.)

---

### Post by Kneegrowplease on 2012-04-20
```
pedro@pedro-ET1330:~$ sudo -i synaptic
[sudo] password for pedro: 

** (synaptic:12832): WARNING **: Command line `dbus-launch --autolaunch=3b8ae750994e9532b340630e00000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n

(synaptic:12832): Gtk-WARNING **: cannot open display: 
```



```
pedro@pedro-ET1330:~$ sudo -i gparted
[sudo] password for pedro: 

(gpartedbin:13117): Gtk-WARNING **: cannot open display: 

```



```
pedro@pedro-ET1330:~$ sudo -i gedit /etc/modules
[sudo] password for pedro: 

** (gedit:13247): WARNING **: Command line `dbus-launch --autolaunch=3b8ae750994e9532b340630e00000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
```



```

pedro@pedro-ET1330:~$ sudo -s synaptic
[sudo] password for pedro: 

(synaptic:12998): Gtk-WARNING **: cannot open display: 
 
```


```
pedro@pedro-ET1330:~$ sudo -s gparted

(gpartedbin:13016): Gtk-WARNING **: cannot open display: 

** (gpartedbin:13016): WARNING **: Command line `dbus-launch --autolaunch=3b8ae750994e9532b340630e00000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
```


```

pedro@pedro-ET1330:~$ sudo -s gedit /etc/modules
[sudo] password for pedro: 
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
```

---

### Post by Kneegrowplease on 2012-04-20
Well, I've got all my data backed up and 11.10 on a USB drive ready to reinstall. I'd rather go through all that than work on a neutered machine...shouldn't have upgraded anyway, I'll try to be patient and work my way through this first though. just brewed some strong coffee, most everything I need is working for now (I guess) I do love Ubuntu though.



All this nonsense is making it terribly difficult to fully migrate away from a windoze box:lolflag:

---

### Post by sudodus on 2012-04-20
No, I meant only those commands
```
sudo -i   # only
```
and
```
sudo -s   # only
```
without trying to call another program.

And then if either of them is successful (giving you the root prompt #) try to run the GUI programs directly without any sudo or gksudo in front of it!
```
gedit
```
```
gparted
```

---

### Post by Kneegrowplease on 2012-04-20
```
pedro@pedro-ET1330:~$ sudo -s
[sudo] password for pedro: 
root@pedro-ET1330:/home/pedro# gedit
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

** (gedit:13783): WARNING **: Command line `dbus-launch --autolaunch=3b8ae750994e9532b340630e00000009 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
root@pedro-ET1330:/home/pedro# gparted

(gpartedbin:13801): Gtk-WARNING **: cannot open display: 
root@pedro-ET1330:/home/pedro# 


```
```


pedro@pedro-ET1330:~$ sudo -i
[sudo] password for pedro: 
root@pedro-ET1330:~# gparted

(gpartedbin:13938): Gtk-WARNING **: cannot open display: 
root@pedro-ET1330:~# gedit
Cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
root@pedro-ET1330:~# synaptic

(synaptic:13943): Gtk-WARNING **: cannot open display: 
root@pedro-ET1330:~# 

```


I can however open synaptic through the GUI menu and enter my keyring when prompted and everything works normal from there...except no gksudo

---

### Post by sudodus on 2012-04-20
Yes, you are allowed to run as root, but root is not allowed to open your X11 display. And that is something different from the fact that gksudo is not there any more. I guess when you still had gksudo that program was OK, it was the problem with root's permissions all the time. And since you cannot reinstall gksudo you have several issues...

I think it is a good idea to make a fresh install, and then copy back your personal files. An alternative might be to put /home on a separate partition. You can find several threads about that if you search the Ubuntu Forums.

---

### Post by forrestcupp on 2012-04-20
> **sudodus said:**
> And since you cannot reinstall gksudo you have several issues...

It's because there is no package for gksudo. The package is called **gksu**, and as far as I can tell, gksudo is merely a symlink to gksu because Ubuntu users are used to the sudo command, rather than the su command. They're exactly the same command, but the installable package is called gksu.

So he needs to try purge removing and reinstalling the gksu package. I'm not convinced that would fix the problem, but it's worth a try.
```
sudo apt-get --purge remove gksu
sudo apt-get install gksu
```

If you get so frustrated that you end up reinstalling, you may want to consider going ahead and installing the 12.04 beta2. The final release comes out in 6 days, and it would suck to reinstall 11.10 and have to turn around and upgrade to 12.04 right away. 12.04 is going to be an LTS, so if you're going to stay with one, that is the one to stay with.

Edit: My stupid mistake. I see now that your problems are with 12.04 and you're thinking about going back to 11.10. By the way, I don't have the same problem with 12.04, so it's not specifically a problem with Precise.

---

### Post by audiomick on 2012-04-20
> **sudodus said:**
>  An alternative might be to put /home on a separate partition.

Yes, do this. Saves you the trouble of copying everything off and back on when you have to do a freash install.

---

### Post by Kneegrowplease on 2012-04-21
Solved with a clean 11.10 install:lolflag::lolflag::lolflag::lolflag:

---

### Post by houseworkshy on 2012-04-21
Good, but it was an interesting one ( much less so if affected of course, more like very annoying I guess ).  So in short looks like using gksudo, which is now redundant, altered permissions which it's replacement gksu ( which I've always used anyway as it has been around for years ) couldn't touch.  Something for developers to bear in mind when renameing and replaceing commands perhaps, if that was what is was anyway.  A closer than usual look at the change log will be in order before upgrading to the next lts I think.  From what I've seen so far most of my fiddleing will be to make it behave like an earlier version anyway, passwords on updates, gnome desktop with the window icons on the other side, etc etc.  Hadn't even thought about changed commands, ah well, presume there will be a sticky about all that anyway.  Glad you have a working machine and even though you didn't intend it that way, the timely warning.

---

### Post by Kneegrowplease on 2012-04-22
> **houseworkshy said:**
> Good, but it was an interesting one ( much less so if affected of course, more like very annoying I guess ).  So in short looks like using gksudo, which is now redundant, altered permissions which it's replacement gksu ( which I've always used anyway as it has been around for years ) couldn't touch.  Something for developers to bear in mind when renameing and replaceing commands perhaps, if that was what is was anyway.  A closer than usual look at the change log will be in order before upgrading to the next lts I think.  From what I've seen so far most of my fiddleing will be to make it behave like an earlier version anyway, passwords on updates, gnome desktop with the window icons on the other side, etc etc.  Hadn't even thought about changed commands, ah well, presume there will be a sticky about all that anyway.  Glad you have a working machine and even though you didn't intend it that way, the timely warning.



Most of the changes I made after upgrading were to make it act/look more like earlier distro's anyway, I mean I'm using knome classic with 11.10, so what does that tell you.  " I should have never upgraded in the first playe":P

---

