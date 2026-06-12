---
title: "Timings?"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-28
Approx how many seconds should one wait for all the running proccesses to shut before shutting or restarting the Ubuntu running machine?

Thanks.

---

### Post by Calinou on 2012-12-28
About 5 seconds (it actually appears when shutting down, if you don't use splash screen).

---

### Post by Yezinki on 2012-12-28
Thanks Calinou for your reply.

How do I know if I have splash screen?

---

### Post by Frogs Hair on 2012-12-28
The splash screen appears as the Ubuntu name with white dots below it. Some times proprietary graphics drivers will interfere with the ability to see the shutdown animation.

---

### Post by squakie on 2012-12-28
I may be wrong here, but I *think* if you do it via a terminal window and sudo shutdown -h now that you get progress indications.

---

### Post by Yezinki on 2012-12-28
Thanks Frogs Hair & squakie for your replies.

1. Is it possible & wise to remove the splash screen, if yes how?

2. What exactly do you mean by " sudo shutdown -h now that you get progress indications."

---

### Post by Frogs Hair on 2012-12-29
1. I have never investigated removing the splash screen.
2. When using the command  ```
sudo shutdown -h 
``` to shut down as root the various processes that are terminating are visible in the terminal.

---

### Post by audiomick on 2012-12-29
> **Yezinki said:**
> Approx how many seconds should one wait for all the running proccesses to shut before shutting or restarting the Ubuntu running machine?

Thanks.

What exactly are you concerned about? The way I read that, you are asking how long you should wait before shutting down the machine after closing a program. If that is the question, you don't have to wait at all. When you tell the machine to shut down or restart, it firstly safely closes all running processes.

---

### Post by Yezinki on 2012-12-29
If I shut down or reboot it displays a message " bytes could not be written", that is why?

Thanks.

---

### Post by Yezinki on 2012-12-29
```
vaio@VGC-LS1:~$ sudo shutdown -h
[sudo] password for vaio: 
shutdown: time expected
Try `shutdown --help' for more information.
vaio@VGC-LS1:~$ 

```

What does this mean?

Thanks.

---

### Post by haqking on 2012-12-29
> **Yezinki said:**
> ```
vaio@VGC-LS1:~$ sudo shutdown -h
[sudo] password for vaio: 
shutdown: time expected
Try `shutdown --help' for more information.
vaio@VGC-LS1:~$ 

```What does this mean?

Thanks.

you need to specify when

```
sudo shutdown -h now

```

You could of also typed shutdown -- help for more information ;-)

---

### Post by Yezinki on 2012-12-29
Thanks haqking for your reply.

```
sudo shutdown -h now
```

This shut the system instantly.

1. Can't this command be inserted or has to be typed each time in the terminal?

2. Can a value of like 10-60 secs be set too?

---

### Post by haqking on 2012-12-29
> **Yezinki said:**
> Thanks haqking for your reply.

```
sudo shutdown -h now
```This shut the system instantly.

1. Can't this command be inserted or has to be typed each time in the terminal?

2. Can a value of like 10-60 secs be set too?

I can answer you directly, however i will refer you to your own message which you posted and to which i recommended above.

```
shutdown --help
```or

```
man shutdown
```You will learn so much more when you use the tools available

---

### Post by Yezinki on 2012-12-29
Thanks again haqking for the posted commands.

1. Personally what do you use for a reboot & shut down respectively?

2. Can they be inserted in some way to the rt upper corner icon rather than typing each time in the terminal?

---

### Post by haqking on 2012-12-29
> **Yezinki said:**
> Thanks again haqking for the posted commands.

1. Personally what do you use for a reboot & shut down respectively?

2. Can they be inserted in some way to the rt upper corner icon rather than typing each time in the terminal?

I use the shutdown button......LOL

Though my systems are on all the time.

If you are asking where is the shutdown button, then I dont use Ubuntu but if its 12.04 or 12.10 i think it is by typing shutdown or restart into dash and you can make launchers from it.

or isnt it on the cog in top right corner ?

---

### Post by Yezinki on 2012-12-29
Yes it's the cog at the top rt.

Can't make launchers.

```
sudo shutdown -h +1m
```

Is this correct for 1min shut down?

```
sudo shutdown -h +30secs
```

For 30 secs?

What for a reboot?

With out this  ```
sudo shutdown -h now
``` I get a message could not write bytes?

---

### Post by haqking on 2012-12-29
> **Yezinki said:**
> Yes it's the cog at the top rt.

Can't make launchers.

```
sudo shutdown -h +1m
```Is this correct for 1min shut down?

```
sudo shutdown -h +30secs
```For 30 secs?

What for a reboot?

With out this  ```
sudo shutdown -h now
``` I get a message could not write bytes?

no its +1 (m is number of minutes)
```

sudo shutdown -h +1
```type ```
reboot
``` to reboot.

You cant shutdown in less than one minute, though you can funk it with somit like

```
sudo sleep 30 ; sudo shutdown -h now
```Like i said ```
man shutdown
``` will tell you everything and give you extra options

---

### Post by Yezinki on 2012-12-29
```
vaio@VGC-LS1:~$ reboot
reboot: Need to be root
vaio@VGC-LS1:~$ sudo shutdown -h +1

```

Are these correct?

---

### Post by Wim Sturkenboom on 2012-12-29
For reboot, replace '-h' by '-r'. Further just try your commands.

To remove the splash, edit the file /etc/default/grub; you need root priviliges, so in a terminal run e.g.
```

gksudo gedit

```
Find the line that contains the words 'quiet splash' and remove the 'splash'. Save the file and run the command
```

sudo update-grub

```
At the next reboot, the splash screen will be gone.

---

### Post by haqking on 2012-12-29
> **Yezinki said:**
> ```
vaio@VGC-LS1:~$ reboot
reboot: Need to be root
vaio@VGC-LS1:~$ sudo shutdown -h +1

```Are these correct?

```
sudo reboot
```

or
```
sudo shutdown -r now
```

or

```
poweroff
```

or

```
sudo sleep 10; sudo shutdown -h now
```

to shutdown in 10 seconds

or

```
sudo shutdown -h +1
```

to shutdown in 1 minute.

And I will type it one last time ;-)

```
man shutdown
```

---

### Post by Yezinki on 2012-12-29
Thanks haqking for explaining an old man indepth.

1. How can one set a time for ```
sudo reboot
```?

2. Why do they have to be typed each time in terminal?

Thanks Wim Sturkenboom, is it wise to remove splash screen & do most expert members remove it?

---

### Post by haqking on 2012-12-29
> **Yezinki said:**
> Thanks haqking for explaining an old man indepth.

1. How can one set a time for ```
sudo reboot
```?

2. Why do they have to be typed each time in terminal?

Thanks Wim Sturkenboom, is it wise to remove splash screen & do most expert members remove it?

```
man shutdown
```

would reveal

```
sudo shutdown -r +1
```

Typed each time ? you can use up and down cursor keys to scroll through previous commands, how often do you reboot then ? LOL

Why arent you using the shutdown or reboot options graphically ?

---

### Post by Yezinki on 2012-12-29
[HTML]Why arent you using the shutdown or reboot options graphically ?[/HTML]

Cause I see a message " bytes could not be written: broken pipe?

Thanks any ways I apprecaite your expert assistance.

---

### Post by Wim Sturkenboom on 2012-12-30
> **Yezinki said:**
> 
Cause I see a message " bytes could not be written: broken pipe?

In this case, don't worry about that message. During a shutdown processes 'die' but other processes still try to communicate with them.

---

### Post by Yezinki on 2012-12-30
Thanks Wim Sturkenboom for trying to explain, but frankly went over my head the die proccesses.......lol.

btw when I shut down using the method you suggested & restart or reboot my machine Pidgin starts instally when clicked vs the normal shut down or reboot where have to click on it a few times, than quit from launcher & than clcik on it's icon in mail on the rt top?

---

### Post by squakie on 2012-12-30
I guess I should have quoted my string in my first reply - the "now" was part of the shutdown command: sudo shutdown -h now.  The text after that indicated you would be able to see the shutdown progress.
 
In a work environment, we used to add a time on the shutdown request so that users had a few minutes to finish what they were currently doing and logging off instead of just killing them in the middle of a process.

---

### Post by Wim Sturkenboom on 2012-12-31
> **squakie said:**
> I guess I should have quoted my string in my first reply - the "now" was part of the shutdown command
That's why I nowadays underline commands in the text (or use code blocks) :D

---

### Post by squakie on 2012-12-31
Good idea - I'm going to remember that! ):P

---

