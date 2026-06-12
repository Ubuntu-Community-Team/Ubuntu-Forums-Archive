---
title: "[SOLVED] Hardy Wont Shutdown or reboot"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by SILLAT on 2008-06-14
I'm running Ubuntu 8.04 on my desktop P.c from its released in april and now all of a sudden this week i cant shutdown,reboot, logoff or hibernate. when i try to do any of the following the screen jus turn off but the monitor and the systems unit is still running. anybody else ever had a problem like this before an can offer a Fix.

---

### Post by rockerphil on 2008-06-14
have you tried it through the terminal? to reboot it's simply 

sudo reboot

and to shutdown it's

sudo shutdown now

that may do what you're wanting, hope it helps

ps. to log out simply zap your x session. Ctrl+Alt+Backspace. that'll drop you to just a command prompt then just type

logout

to log out. you can then relogin and restart your x session by typing 

startx

---

### Post by balagosa on 2008-06-14
sudo shutdown now is not enough. That it is the command i been using before but it is still powered on.

```
sudo shutdown -P now
``` this is what i use now

---

### Post by rockerphil on 2008-06-14
good call balagosa. cheers

---

### Post by Sef on 2008-06-14
To shutdown use this command:

```
sudo shutdown -h now
```

---

### Post by JC Cheloven on 2008-06-14
So it worked, and suddenly didn't... it seems to be some update (involving a kind of a regression for your hardware). 

Sorry for that, I can't give a fix. But I suffer in a permanent way from similar problems. I own a toshiba laptop that doesn't get on very well with ubuntu. With gutsy I had to install xfce instead of gnome (because of continuous crashes). With hardy things are much better, but shutdown and suspend still work randomly. Many times I have to do a hard-shutdown.

---

### Post by balagosa on 2008-06-14
> **rockerphil said:**
> good call balagosa. cheers

cheers too. have some popcorn :popcorn: while you are still at it.

---

### Post by SILLAT on 2008-06-14
yes it stop shuting down after installing some updates this week
and yes i've tried shuting down and reboot from the terminal: i've tried sudo halt, sudo shutdown -h now shutdown -p 
still it doesnt work
any one kno any more wor arounds to try

---

### Post by ChameleonDave on 2008-06-14
Did you install Hardy Heron fresh from the Live CD, or upgrade from a Gutsy Gibbon installation?

---

### Post by Sef on 2008-06-14
> yes it stop shuting down after installing some updates this week

I have had a problem with it shutting down too.  What I did was after clicking on the shutdown icon, I had to ctrl-alt-backspace and then it shutdown.

---

### Post by SILLAT on 2008-06-14
i did a clean install of hardy, i always clean install
as for ctrl alt backspce to logout, that doesnt seem to work either, i've spent so much time gettin my os to perfection i jus cant think of a clean install now

---

### Post by JC Cheloven on 2008-06-14
> **SILLAT said:**
> i did a clean install of hardy, i always clean install
as for ctrl alt backspce to logout, that doesnt seem to work either, i've spent so much time gettin my os to perfection i jus cant think of a clean install now

Provided that the system is otherwise fully functional, this is my 2p advice:
- Be happy, always
- Think in hibernation as a useless thing, as hardy boots in 90sec
- Think in pushing that square button as an opportunity to caress your pc
- Think that a new update will put it to work again, which really you don't mind

It is half a joke, but is that I did. And now I simply enjoy the (many) other functionalities that ubuntu has to offer :-)

---

### Post by SILLAT on 2008-06-14
man i'll try to do jus that an be happy .. but how safe is it to turn off your pc all the time instead of shutting it down

---

### Post by Sef on 2008-06-14
> man i'll try to do jus that an be happy .. but how safe is it to turn off your pc all the time instead of shutting it down 

It is best to shut it down.

---

### Post by ChameleonDave on 2008-06-14
> **SILLAT said:**
> i did a clean install of hardy, i always clean install
as for ctrl alt backspce to logout, that doesnt seem to work either, i've spent so much time gettin my os to perfection i jus cant think of a clean install now

I imagine that most of the time you've invested has been in personalising your "~" directory.  The rest of the system has probably only been modified by the installation of packages.  You can make a log of the packages installed, backup your home directory, and reinstall everything without losing much of consequence.

I hope there is another solution though.  It is most unfortunate that so many bugs are coming up in Hardy.  Gutsy was more stable.

---

### Post by SILLAT on 2008-06-14
its jus so hard to setup all ova again i hav virtual machines up an running on my pc its a lota work man..gutsy never gave me no trouble, hardy can be such a bitch sometime, do u think if i do a clean install i'd hav to install my virtual machines again . .

---

### Post by ChameleonDave on 2008-06-14
> **SILLAT said:**
> its jus so hard to setup all ova again i hav virtual machines up an running on my pc its a lota work man..gutsy never gave me no trouble, hardy can be such a bitch sometime, do u think if i do a clean install i'd hav to install my virtual machines again . .
Are you talking about VirtualBox or something similar?

I recently reinstalled Hardy without losing my VirtualBox configuration.  You just have to make a back-up.

---

### Post by Dutch70 on 2008-06-14
Hi, next time you find yourself in that situation I strongly recommend doing this.

hold down the
 
"alt & print screen"

 buttons and then hit these keys 

"r-s-e-i-u-b" 

one at a time and pause for a few seconds between each one, because every time you hit a letter, your pc is saving something, and it takes it a second or two. 
 when you hit the last letter (b) your system should reboot and be protected from the nasties that come with a hard shutdown.

 You can remeber it like this...

r - raising 
s - skinny 
e - elephants
i - is 
u - utterly 
b - boring

let us know if it works.

---

### Post by JC Cheloven on 2008-06-15
> **Dutch70 said:**
> Hi, next time you find yourself in that situation I strongly recommend doing this.

hold down the
 
"alt & print screen"

 buttons and then hit these keys 

"r-s-e-i-u-b" 

one at a time and pause for a few seconds between each one, because every time you hit a letter, your pc is saving something, and it takes it a second or two. 
 when you hit the last letter (b) your system should reboot and be protected from the nasties that come with a hard shutdown.

let us know if it works.

--> Yes please! Let us know if it works! It's the weirdest thing I've seen in my life :-D

--> As for the hard shutdown: I'm not very adept to hardware, and I'm sure that it's better to properly shutdown. But also I think that it's not the same as unplugging the cord from the outlet. Usually you have to push the button for 5 seconds. So I figure out that is actually the bios (not just you) who shutdown the pc. Perhaps some wise guy can enlighten this point?

--> I see that you are considering reinstalling. I'm not very confident about this to solve your problem. But just in case you finally decide to do it, you can note the following:

- Every file ".deb" of packages you installed via apt-get, aptitude, synaptic, are saved in /var/cache/apt/archives. You can backup that directory for future reinstallation (in the same machine or in a different one)

- There is a tool about this, APTonCD, with a gui, which you may find useful. See:  [http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html](http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html)

These automates very much the process, as you can reinstall your software packages at once. Hope you find that useful

---

### Post by ChameleonDave on 2008-06-15
> **JC Cheloven said:**
> --> Yes please! Let us know if it works! It's the weirdest thing I've seen in my life :-D

I've just tried it myself.  It works.  Any open applications (e.g. Firefox) won't like it, but the OS is shut down relatively safely.  
It works by passing a signal directly to the Linux kernel.

It first tries to create a bajillion screenshots, though, due to the keys used.


> **JC Cheloven said:**
> 

--> As for the hard shutdown: I'm not very adept to hardware, and I'm sure that it's better to properly shutdown. But also I think that it's not the same as unplugging the cord from the outlet. Usually you have to push the button for 5 seconds. So I figure out that is actually the bios (not just you) who shutdown the pc. Perhaps some wise guy can enlighten this point?

Yes, it's the BIOS shutting you down, but I've never got better results from it than with just pulling the cable.  It's still a hard reset.  The OS never likes it. 

Still, it may be slightly safer than just denying power to the system.

---

### Post by JC Cheloven on 2008-06-15
> **ChameleonDave said:**
> I've just tried it myself.  It works.  Any open applications (e.g. Firefox) won't like it, but the OS is shut down relatively safely.  
It works by passing a signal directly to the Linux kernel.

It first tries to create a bajillion screenshots, though, due to the keys used.


Dutch, Chameleon, thank you very much for that little weird thing. I'll try it next time ;-)

---

### Post by Dutch70 on 2008-06-15
You're welcome. 

 It was actually my first real opportunity to maybe help someone else, so that was cool.

---

### Post by SILLAT on 2008-06-18
hey guys sorry i took so long to get back to u all but i got fed up of trying all these stuff an nothin happen. . i didnt get to try the last set of actions (r-s-e-u-i-b). i did a clean install an preserve ny home an everything worked out fine (even my virtual box was intact)
thanks y'all

---

### Post by Dutch70 on 2008-06-19
Glad everything worked out for ya!

---

