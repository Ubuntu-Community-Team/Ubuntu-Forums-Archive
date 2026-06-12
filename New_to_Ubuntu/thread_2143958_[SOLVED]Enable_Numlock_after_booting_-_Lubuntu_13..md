---
title: "[SOLVED]Enable Numlock after booting - Lubuntu 13.04 / Xubuntu 12.04 LTS"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Koenraads on 2013-05-10
This solution worked for me on both operating systems. ( Lubuntu 13.04 / Xubuntu 12.04 LTS)

**sudo apt-get install numlockx**
**sudo leafpad /etc/lightdm/lightdm.conf**
*add the next line at the end*
**greeter-setup-script=/usr/bin/numlockx on**



I have installed lubuntu 13.04 and been trying for hours to have the numlock on after booting. The numlock is enabled in the bios, and I tried a lot off ways to get it work. '[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)' and '[https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)'.
I don't see how I can make it work. Any Ideas? I'm new working with the command line so It isn't unpossible that I made some mistakes. :-(
Thx.

---

### Post by Werne on 2013-05-10
If I recall correctly, on Lubuntu 12.04 I needed to edit lxdm.conf to get Num Lock to activate on startup, or was that Lubuntu 11.04. In any way, run
```
gksu leafpad /etc/xdg/lubuntu/lxdm/lxdm.conf
```
and change the
```
# numlock=0
```
line to
```
numlock=1
```

That did it for me, though I'm not sure if it will work on 13.04.

---

### Post by Koenraads on 2013-05-10
Hi, I already tried that one but I doesn't work.

---

### Post by Werne on 2013-05-10
Alright then, there's another way that should work. Try using numlockx to enable it after booting, first run
```
sudo apt-get numlockx
```
to get the package. Then run
```
gksu leafpad /etc/X11/xinit/xinitrc
```
and add
```
/usr/bin/numlockx on
```
to the bottom of the file, below the /etc/X11/Xsession line. That will enable numlock the moment you login to a user account.

---

### Post by Koenraads on 2013-05-11
Werne,

I tried it but it didn't work. NumLock is on while booting during bios time but once launched Lubuntu 'the light' gets off.
This is the file how I changed it:

[FONT=book antiqua]#!/bin/sh[/FONT]
[FONT=book antiqua]
[/FONT]
[FONT=book antiqua]# /etc/X11/xinit/xinitrc[/FONT]
[FONT=book antiqua]#[/FONT]
[FONT=book antiqua]# global xinitrc file, used by all X sessions started by xinit (startx)[/FONT]
[FONT=book antiqua]
[/FONT]
[FONT=book antiqua]# invoke global X session script[/FONT]
[FONT=book antiqua]. /etc/X11/Xsession[/FONT]
[FONT=book antiqua]/usr/bin/numlockx on

Did I make a mistake?
Grtz and thanks for your effort![/FONT]

---

### Post by Werne on 2013-05-11
Yeah, you did everything right, it's just that it refused to initialize. It should've though, xinitrc should've started it the moment Xsession starts. Well, that's unless you didn't log into your DE and logged into bash, that wouldn't start the Xsession which in turn wouldn't start numlockx either.

In any way, open the terminal and run the following command while your numlock is off:
```
numlockx on
```

If num lock activates, run
```
numlockx off
```
to turn it off.

This is just to check if numlockx works like it should, if it does then it's just a matter of finding how to initialize it on startup.

---

### Post by pstree on 2013-05-11
thanks!nice package & tip.

---

### Post by Koenraads on 2013-05-11
Werne, since I was afraid that I tried maybe to many different things since I installed Lubuntu 3 days ago, I reinstalled it today.
Unfortunately it didn't help. But there are some problems when I try the sugested commando's.
This is what happens and I don't really know what it means:

[SIZE=1]schoonjans@Vic1:~$ numlock on[/SIZE]
[SIZE=1]Opdracht ‘numlock’ niet gevonden, bedoelde u:[/SIZE]
[SIZE=1] Opdracht ‘numlockx’ uit pakket ‘numlockx’ (main)[/SIZE]
[SIZE=1]numlock: opdracht niet gevonden
[/SIZE]
He can't find the commando!

[SIZE=1]schoonjans@Vic1:~$ gksu leafpad /etc/xdg/lubuntu/lxdm/lxdm.conf[/SIZE]
[SIZE=1]GNOME_SUDO_PASS[/SIZE]
[SIZE=1]sudo: 1 incorrect password attempt[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]** (leafpad:1719): WARNING **: Invalid borders specified for theme pixmap:[/SIZE]
[SIZE=1]        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,[/SIZE]
[SIZE=1]borders don't fit within the image[/SIZE]
[SIZE=1]schoonjans@Vic1:~$ sudo apt-get numlockx[/SIZE]
[SIZE=1]E: Ongeldige operatie numlockx[/SIZE]
[SIZE=1]schoonjans@Vic1:~$ gksu leafpad /etc/X11/xinit/xinitrc[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]** (leafpad:1889): WARNING **: Invalid borders specified for theme pixmap:[/SIZE]
[SIZE=1]        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical-sel.png,[/SIZE]
[SIZE=1]borders don't fit within the image[/SIZE]

You can ignore the incorrect password I mistyped. :-)
The rest seems a bit weard to me.

---

### Post by stinkeye on 2013-05-11
Couple of errors in the commands you ran.
> schoonjans@Vic1:~$ sudo apt-get numlockx
Left out **install**
```
sudo apt-get **install** numlockx
```


> schoonjans@Vic1:~$ numlock on
Left off the x
```
numlock**x** on
```
```
numlock**x** off
```

---

### Post by Koenraads on 2013-05-11
Stinkeye, Werne,

We are making progress. After you're hint (Stinkeye) the command numlockx on and off now works!:-)

I still get the leafpad: 1729 Warning adjusting the lxdm.conf file.
When I look into the file after unquoting and changing numlock into 1 the changes are still there. After reboot numlock is still not on.
:-(

---

### Post by Koenraads on 2013-05-11
I looked into the warning and as I understand that should have no influence on the numlock issue and could be ignored. So I'll keep to have looking.

[SIZE=1]*Well, that's unless you didn't log into your DE* and logged into bash**, that wouldn't start the Xsession which in turn wouldn't start numlockx either.*[/SIZE]
Can somebody tell me how to know the difference of * & ** and how to activate the Xsession process.

---

### Post by matt_symes on 2013-05-11
Hi

Try this. 

Copy and paste these lines into the terminal.

```
echo "/usr/bin/numlockx on" | sudo tee /usr/share/enable_numlock.sh
```

```
sudo chmod 755 /usr/share/enable_numlock.sh
```

```
echo 'session-setup-script=/usr/share/enable_numlock.sh' | sudo tee -a /etc/lightdm/lightdm.conf
```

Reboot and tell us if it works.

EDIT:

You may want to run...

```
echo 'display-setup-script=/usr/share/enable_numlock.sh' | sudo tee -a /etc/lightdm/lightdm.conf
```

..as i think display-setup-script gets called after X is started.

Kind regards

---

### Post by rburkartjo on 2013-05-12
try this use this script
#!/bin/bash
echo xxxx | sudo -S NumLock on

replace xxx with your user name. name it whatever put in home folder. then open up the script go to permissions and check execute:allow executing file as program.
then add it to your session and startup folder. worked for me . to check after you login open up your terminal program and type numlockx status you should get the response Numlock is on.

---

### Post by Koenraads on 2013-05-12
Matt, I tried what you suggested but after reboot numlock still off. :-(
Rburkartjo, also tried what you suggested. The strange thing here is that I don't get the time in the terminal to enter my password. I immediately get following error:
[SIZE=1]schoonjans@Vic1:~$ echo schoonjans | sudo -S NumLock on[/SIZE]
[SIZE=1][sudo] password for schoonjans: Sorry, try again.[/SIZE]
[SIZE=1][sudo] password for schoonjans: [/SIZE]
[SIZE=1]sudo: 1 incorrect password attempt[/SIZE]
Remark: I din't type my pasword yet!

---

### Post by matt_symes on 2013-05-12
Hi

> **Koenraads said:**
> Matt, I tried what you suggested but after reboot numlock still off. :-(


Did you see my edit of my last post and use this one with display-setup-script.

```
echo '**display-setup-script**=/usr/share/enable_numlock.sh' | sudo tee -a /etc/lightdm/lightdm.conf
```

Just tried it on a laptop with no numlock key, using gb keymap and non gb keyboard (still in the process of setting it up) and it would not let me log in so numlockx did something.

If you try it on yours, where you have a numlock key, the correct keyboard and mapping, using display-setup-script and not session-setup-script, it may work.

Of course, if you tried both display-setup-script and session-setup-script then disregard this post :)

Kind regards

---

### Post by rburkartjo on 2013-05-13
Koe on the script i gave you dont have to enter your password to activate.

---

### Post by momist on 2013-07-12
> **Koenraads said:**
> This solution worked for me on both operating systems. ( Lubuntu 13.04 / Xubuntu 12.04 LTS)

**sudo apt-get install numlockx**
**sudo leafpad /etc/lightdm/lightdm.conf**
*add the next line at the end*
**greeter-setup-script=/usr/bin/numlockx on**



Thanks for this post, this solution also worked for me on Lubuntu 13.04 fresh install.

---

### Post by gs611 on 2013-12-24
> **Koenraads said:**
> This solution worked for me on both operating systems. ( Lubuntu 13.04 / Xubuntu 12.04 LTS)

**sudo apt-get install numlockx**
**sudo leafpad /etc/lightdm/lightdm.conf**
*add the next line at the end*
**greeter-setup-script=/usr/bin/numlockx on**



Just to confirm that this also works for Kubuntu 13.10 (although I used kate instead of leafpad). I was not able to get numlocks on any other way (including built in settings controls)

---

