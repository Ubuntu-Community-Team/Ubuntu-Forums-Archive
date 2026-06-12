---
title: "sudo apt-get install gnome-session"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by daviddixit on 2013-02-28
Hello,
I turned my computer to find a window: could not update ICEauthority file/home/. ICEauthority

I opened a console and tried : [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install gnome-session

It did its dance and finished with the word: master@mastermind:ñ$     (the ñ doesn´t have the n, just the wavy line.)

I don´t know what to do next...

Can anyone help me ?[/FONT][/COLOR]

---

### Post by sudodus on 2013-02-28
Which version (12.04 LTS,12.10 or some other version) are you running?

Have you updated your installed version? Run these command to update and try to install gnome-session again

```
sudo apt-get update
``````
sudo apt-get upgrade
```and if some packages are held back```
sudo apt-get dist-upgrade
```

---

### Post by daviddixit on 2013-02-28
ok, thank you.
I did that, then repeated the re install order. I was then told that certain things were no longer necesary, and that I should un install those things. Which I did. It then asked if I had the authority to do this, and I replied yes.
II now have an unending vertyical line of yyyyyyyyyyyyyyyyy´s going udown the left side of the screen !

WHAT NOW ?

---

### Post by sudodus on 2013-02-28
Which version (12.04 LTS,12.10 or some other version) are you running?

And which flavour (Ubuntu, Kubuntu, Lubuntu, Xubuntu, ...)?
--
I don't understand what is happening. Press ***ctrl + c*** to stop that! And try again with your original command

```
sudo apt-get install gnome-session
```

---

### Post by daviddixit on 2013-03-01
Ok, I´m back. Thanks.
I did the original command again, and I am back where I was. It says that there are no updates, no new installations, nothing top remove amd 15 not updated.
Then it says [COLOR=#000000][FONT=Ubuntu Mono]master@mastermind:~$
[/FONT][/COLOR]
What now ?!

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> Ok, I´m back. Thanks.
I did the original command again, and I am back where I was. It says that there are no updates, no new installations, nothing top remove amd 15 not updated.
Then it says [COLOR=#000000][FONT=Ubuntu Mono]master@mastermind:~$
[/FONT][/COLOR]
What now ?!
Maybe your version of Ubuntu has passed end-of-life. Maybe it is still experimental. That is why I'm asking for the version number. Please post the output of this command!
```
lsb_release -a
```

What happens if you run this command?
```
sudo apt-get dist-upgrade
```

If still no go, try according to this list of commands originally posted by *oldfred*

```

# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

### Post by daviddixit on 2013-03-01
After the first command,
No LSB modules are available
Distributor ID: Ubuntu
Description: Ubuntu12.04.2 LTS
Release: 12.04
Codename: precise
[COLOR=#000000]* *[/COLOR][COLOR=#000000][COLOR=#000000][I][FONT=Ubuntu Mono]master@mastermind:~$
[/FONT][/I][/COLOR][/COLOR]
I am embarassed to say I don´t know the version...

---

### Post by sudodus on 2013-03-01
It's OK, all flavours of this version are supported. There is some other error. Please try according to that list of commands by oldfred in my previous post. Put **sudo** before each command (or even **sudo -i** as oldfred suggests).

---

### Post by daviddixit on 2013-03-01
I did:

sudo-i apt-get dist-upgradeand it´s working on it.

---

### Post by daviddixit on 2013-03-01
It says, at the end, 

Idconfig deferred processing now taking place
[I][FONT=Ubuntu Mono]master@mastermind:~$

[/FONT][/I]

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> It says, at the end, 

Idconfig deferred processing now taking place
[I][FONT=Ubuntu Mono]master@mastermind:~$

[/FONT][/I]
Looks good. Try
```
sudo apt-get install gnome-session
```
again, and if no go, continue along oldfred's list to the very end if necessary.
```

# fix Broken packages -f
sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by daviddixit on 2013-03-01
Tried  [COLOR=#000000][FONT=Ubuntu Mono]apt-get update

now trying  [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]apt-get upgrade

[/FONT][/COLOR]

---

### Post by daviddixit on 2013-03-01
Ok, I have tried all of these, to no avail.

I tried again : [COLOR=#000000][FONT=Ubuntu Mono]sudo -i apt-get dist-upgrade

It says no updates, no new instalations, nothing to delete, no updates.

I am back to square 1.[/FONT][/COLOR]

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> Ok, I have tried all of these, to no avail.

I tried again : [COLOR=#000000][FONT=Ubuntu Mono]sudo -i apt-get dist-upgrade

It says no updates, no new instalations, nothing to delete, no updates.

I am back to square 1.[/FONT][/COLOR]

Did you try these commands?
```
# fix Broken packages -f
[COLOR=#ff0000]sudo apt-get -f install
sudo dpkg --configure -a[/COLOR]

```
And afterwards to install again
```
sudo apt-get install gnome-session
```

Try it again, and if this does not help, I hope [COLOR=#0000ff]someone else[/COLOR] can jump in and help.

Edit: the [COLOR=#ff0000]red commands[/COLOR] were garbled, but should be OK now

---

### Post by sudodus on 2013-03-01
Just wanted to tell, that I had to edit the previous post (the [COLOR=#ff0000]red commands[/COLOR] should be OK now)

---

### Post by daviddixit on 2013-03-01
I tried the earlier commands and it said it didn´t recognise them.
I tried install gnome session and it said : [COLOR=#000000][FONT=Ubuntu Mono][I]no updates, no new instalations, nothing to delete, no updates.

Then it waits for a command.k enter, and it waits for a new command again.

What else should I reply ?

I clic


[/I][/FONT][/COLOR]

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I tried the earlier commands and it said it didn´t recognise them.

Which commands were not recognized?

---

### Post by daviddixit on 2013-03-01
I clic ?

also, I tried the first red command e)and it replied that their were things no longer necessary, and to enter apt-get autoremove to delete them.
When I do this it asks of I have the privileges of a superutulisateur (I am in France)
It doen´t accepte either yes or oui...

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I clic ?

also, I tried the first red command e)and it replied that their were things no longer necessary, and to enter apt-get autoremove to delete them.
When I do this it asks of I have the privileges of a superutulisateur (I am in France)
It doen´t accepte either yes or oui...
Run

```
sudo apt-get autoremove

```

---

### Post by daviddixit on 2013-03-01
[COLOR=#000000] superutilisateur[/COLOR]

---

### Post by daviddixit on 2013-03-01
I used [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get autoremove
it is now deleting things.
It ends with Idconfig deferred processing now taking place, 
it is expecting a command ...[/FONT][/COLOR]

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> [COLOR=#000000] superutilisateur[/COLOR]
alias superuser alias root. In Ubuntu we use ***sudo*** to become superuser while performing the command following it. This is to protect from mistakes, that might destroy the system or remove a lot of files. sudo can be interpreted as 'superuser do'

---

### Post by daviddixit on 2013-03-01
I did that and it deleted all sorts of things.
It now says: Idconfig deferred processing now taking place.
It has now stopped and is waiting for a command.

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I used [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get autoremove
it is now deleting things.
It ends with Idconfig deferred processing now taking place, 
it is expecting a command ...[/FONT][/COLOR]
That takes some time, usually not expecting a command, just returning to prompt

[FONT=courier new]user@system /path $[/FONT]

---

### Post by daviddixit on 2013-03-01
it ends with the master@mastermind:   
I should just wait then ?

btw, thank you for your patience...

---

### Post by sudodus on 2013-03-01
Try again
```
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```
and after that finally 
```
sudo apt-get install gnome-session
```
might work

---

### Post by daviddixit on 2013-03-01
Done, It simply says that it has the most recent available version.

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> it ends with the master@mastermind:   
I should just wait then ?

btw, thank you for your patience...

Maybe I should explain, that when the terminal window shows that line with master@mastermind (or similar for other users), the previous command has finished, and the command line shell ***bash*** is ready for new commands.

---

### Post by daviddixit on 2013-03-01
What final (?) command should I give ?

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> Done, It simply says that it has the most recent available version.

Good, in that case you have succeeded. Maybe you succeeded long ago to install gnome-session, but you did not realize that.

Now what do you want to do with gnome-session? If you are lucky, you can log out and select it at the log in screen and log in again. If you are running Ubuntu, there is a round icon near the log in text. Click on it!

---

### Post by daviddixit on 2013-03-01
No icons visible

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> No icons visible
Can you find something like this on the login screen? See at the arrow on the attached picture. Click on it :-)

---

### Post by daviddixit on 2013-03-01
No !
(It is usually at top right to turn computer off or reboot)

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> No !
(It is usually at top right to turn computer off or reboot)
You have to ***log out*** from your present session (using the button at top right corner). Then you come to the ***log in*** screen. And you select session with that round button (or icon) at the arrow, when you are at the log in screen. It is not at the top right corner, more to the left and vertically near the middle of the screen.

***Edit***: Maybe it's easier to ***reboot ***to come to the log in screen.

---

### Post by daviddixit on 2013-03-01
I rebooted and I get the terminal again asking for a command.
I tried typing exit, but it didn't work...

---

### Post by schragge on 2013-03-01
:?: Are you still getting the message
```

Could not update ICEauthority file /home/master/.ICEauthority

```

If yes, please post the output of
```

stat .I*

```

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I rebooted and I get the terminal again asking for a command.
I tried typing exit, but it didn't work...

- What are you trying to do? A good description of the problem is a big step towards a solution.

- Do you get some error messages?

- Do you have a text screen only or a graphical desktop environment, where you can run graphical programs, for example watching pictures?

- Did you install Ubuntu desktop or Ubuntu Server or Ubuntu Mini or something else?
--
If Ubuntu desktop, can you boot your PC from the Ubuntu install disk? Try Ubuntu (do not install)! Will it look different from what you get from the installed version?

---

### Post by daviddixit on 2013-03-01
I don´t think I uninstalled Ubuntu desktop, but now I just want to log out of the teminal.

---

### Post by daviddixit on 2013-03-01
Ok, I did that, and I have three blocks of figures with mostly dates...

---

### Post by daviddixit on 2013-03-01
[COLOR=#000000]I just want to log out of the teminal...[/COLOR]

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> [COLOR=#000000]I just want to log out of the teminal...[/COLOR]

Did you get to the terminal automatically? Or did you start it with

***ctrl + alt + t*** (a terminal window)
or
***ctrl +alt + F3*** (a text screen)?

---

### Post by schragge on 2013-03-01
> **daviddixit said:**
> Ok, I did that, and I have three blocks of figures with mostly dates...

What does it says in the **Access:** line? Please put the output here for us to see.

---

### Post by schragge on 2013-03-01
@**sudodus**

AIUI, the OP boots into text console.

---

### Post by sudodus on 2013-03-01
> **schragge said:**
> @**sudodus**

AIUI, the OP boots into text console.
Yes, I'm starting to think so too. We need to find out if (and how) the system is broken, or if (s)he is trying to do something strange.

---

### Post by sudodus on 2013-03-01
daviddixit,

Is your Ubuntu system installed with a graphical desktop environment (the standard is Unity)? Are you looking for another one, and that is why you install gnome-session?

Or is your Ubuntu system installed with a text user interface (Ubuntu Server or Ubuntu mini-iso)? And you are trying to get a graphical user interface to work properly?

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I clic ?

also, I tried the first red command e)and it replied that their were things no longer necessary, and to enter apt-get autoremove to delete them.
When I do this it asks of I have the privileges of a superutulisateur (I am in France)
It doen´t accepte either yes or oui...

I have not understood enough to help, so far we seem to be talking about  different things. I'm willing to continue to try and help, but I think  [COLOR=#ff0000]we need help from some more people[/COLOR]. [COLOR=#008000]***Schragge*** has solved some other  difficult cases, so please try to answer his questions![/COLOR]

I think we have problems to communicate, because none of us speak native English. [COLOR=#008000]You might get better help explaining in French[/COLOR]

- your computer system (hardware and software, what you have installed)
- what you want to do
- what errors you get

That could be done here, hoping someone else speaking French can help you, or if there is an active French Ubuntu web-site, you could also post your request there (and include a link to this thread).

---

### Post by daviddixit on 2013-03-01
[COLOR=#000000]I just want to log out of the teminal.

How do I do this ?

There are NO icons visible on the screen...

Help please.[/COLOR]

---

### Post by lisati on 2013-03-01
If you accessed the terminal from the dash menu, the following should work:
```
exit
```
or
```
logout
```

Otherwise you can use Ctrl+alt+F7.

If you just have the terminal when starting your machine, there might be a little bit of troubleshooting that's needed. You can try:
```
startx
```

---

### Post by daviddixit on 2013-03-01
Ok, thank you, when I use exit it exits, then I am asked for the Master password, which then returns me to the terminal !

In the middle of this, the circular icon appears at the top right hand corner.  Should I turn the computer off then ?

---

### Post by audiomick on 2013-03-01
Do you want to shut down the computer completely from a command line environment?

Try
```
shutdown -P now
```

to power the machine down completely

or 
```
shutdown -r now
```

to restart.

Look at 
```
man shutdown
```

for more shutdown options.

---

### Post by daviddixit on 2013-03-01
These don´t work. I keep coming back to the terminal, even after rebooting the computer.

---

### Post by audiomick on 2013-03-01
> **daviddixit said:**
> These don´t work. I keep coming back to the terminal, even after rebooting the computer.

Did you notice this?

> **lisati said:**
> 
If you just have the terminal when starting your machine, there might be a little bit of troubleshooting that's needed. You can try:
```
startx
```

I'm afraid I don't quite see exactly what your problem is. Is it that you cannot get to a graphical user interfacr, a desktop? That all you can get is a command line environment? In that case, the comment from lisati does apply.

---

### Post by ikt on 2013-03-01
> **daviddixit said:**
> These don´t work. I keep coming back to the terminal, even after rebooting the computer.

Did you recently install any video drivers?

You may be able to get into 'recovery mode' if you hold down the shift key just before ubuntu starts to load.

---

### Post by daviddixit on 2013-03-01
I haven´t recently installed anything.

I tried holding the shift key down, but it still comes back to the terminal.

---

### Post by schragge on 2013-03-01
@**all**
It's started in [thread=2121034]this thread[/thread].

@**daviddixit**
Please answer my question about *.ICEauthority* [post=12535791]there[/post].

---

### Post by Paddy Landau on 2013-03-01
David, you have posted this in the Absolute Beginners section, so I presume you are new to Ubuntu.

We are feeling a little confused. Please give us a bit of background: Did you recently install Ubuntu? Which version of Ubuntu are you using? What happens when you boot? Did you have a graphical user interface before, or did you always get only a terminal (by the way, without the graphical interface, it's called a console)?

EDIT: I missed schragge's post.

---

### Post by Paddy Landau on 2013-03-01
> **daviddixit said:**
> the ñ doesn´t have the n, just the wavy line.
The wavy line ("~") is called a *tilde* (I believe it is *un tilde* in French). It represents your "home", i.e. where all your personal files are saved. I could be wrong, but I think you'll find the tilde on your keyboard using Shift+2.

---

### Post by daviddixit on 2013-03-01
[SIZE=3][FONT=arial][/FONT][/SIZE][SIZE=3][FONT=arial]I tried startx only to be told: user not authorised to run the X server, aborting.

I am certainly a beginner, but I have been using Ubuntu for over a year, but without having any problems!

[/FONT][/SIZE]Yesterday evening, I turned my computer to find a window: could not update ICEauthority file/home/. ICEauthority

I opened a console and tried : sudo apt-get install gnome-session

It did its dance and finished with the word: master@mastermind:~$ 
Waiting for a command.
I tried a variety of things,  then again : sudo -i apt-get dist-upgrade

It said no updates, no new installations, nothing to delete, no updates.

Now, I cannot get out of the console and reboot normally to see a desktop.[SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][/COLOR][/SIZE]

---

### Post by schragge on 2013-03-01
So once again, please run

```

stat .ICEauthority

``` and post the output here. Alternatively, you can post the output of

```

ls -l .ICEauthority [COLOR=blue]# <- it's the small letter L[/COLOR]

```I suppose the file permissions and/or ownership of .ICEauthority are wrong and want to see what they are.


At least, try this
```

sudo chown master: .ICEauthority
sudo chmod 0600 .ICEauthority

```

Then reboot.

---

### Post by Paddy Landau on 2013-03-01
> **daviddixit said:**
> Now, I cannot get out of the console and reboot normally to see a desktop.

[LIST]
[*]You go to consoles using Ctrl+Alt+F1 (or F2, F3, F4, F5 or F6). 
[*]The GUI is in Ctrl+Alt+F7, so press that key-combination to return there. 
[*]From the console, you can reboot with:```
sudo reboot now
``` 
[/LIST]

---

### Post by matt_symes on 2013-03-01
**Thread Merged**.

@daviddixit.

Please do not start multiple threads on the same or extremely similar subjects. 

It dilutes the communites effort to help you and reduces community support for others who are also looking for help.

---

### Post by sudodus on 2013-03-01
> **Paddy Landau said:**
> The wavy line ("~") is called a *tilde* (I believe it is *un tilde* in French). It represents your "home", i.e. where all your personal files are saved. I could be wrong, but I think you'll find the tilde on your keyboard using Shift+2.

setxkbmap fr
***AltGr + 2***
gives me ~ in a terminal window and here in Firefox too.
--
May I also ask you to suggest what to do next to help our OP?

---

### Post by daviddixit on 2013-03-01
stat .ICEauthority :

Fichier "ICEauthority"
Taille: 76396   Blocs: 160   ES Blocs: 4096   fichier
Device: 801h/2049d   Inode: 265113   Liens: 1
Acces: (0600/-rw-------) VID: (1000/ master)   GID: (1000/ master)
Acces: 2013-02-28 08:30:05. 534449637 +0100
Modi.: 2013-02-28 08:30:01.958449768 +0100
Chgt: 2013-02-28 08:30:01.958449768 +0100
Cree: -
master@mastermind:~$

---

### Post by schragge on 2013-03-01
Good. So I was wrong, and *.ICEauthority* actually has right permissions. Please post the output of
```

ps -ef|grep dm$

``` I want to see if a display manager is running (display manager is the program that lets you to log in graphically. It's *lightdm* on a standard Ubuntu system).

---

### Post by daviddixit on 2013-03-01
Just where do I find a vertical line ?!

---

### Post by daviddixit on 2013-03-01
I found it !

---

### Post by daviddixit on 2013-03-01
root   912   1   0  14:33 ?   00:00:00 lightdm

The dm, as I am sure you already know, is red !

---

### Post by Paddy Landau on 2013-03-01
To add to everything here, I have seen other posts with the same problem.

You can try this:
```
ls -ld /home/master
```
It should show *master* three times:
```
drwxr-x--- 100 **master** **master** 40960 Mar  1 11:38 /home/**master**
```
If it does **not** show *master* three times, do this:

[LIST]
[*]Issue the following command:```
sudo chown master:master /home/master
``` 
[*]Reboot and test. 
[/LIST]

On the other hand, if master is correctly shown three times, you can try to reinstall certain key packages.
[LIST]
[*]```
sudo apt-get install --reinstall unity unity-2d ubuntu-desktop
``` 
[*]Reboot and test. 
[/LIST]

---

### Post by daviddixit on 2013-03-01
I tried the first, and it did not show master three times.
I tried the second and it said: [sudo] password for master
I entered my password and it said: commande introuvable (French for command not found)

I begin to despair...

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I tried the first, and it did not show master three times.
I tried the second and it said: [sudo] password for master
I entered my password and it said: commande introuvable (French for command not found)

I begin to despair...
This one might be easy enough for me ;-)

Maybe your path is corrupted. Please post the output of this command
```
/bin/echo $PATH
```
or you misspelled the command ***chown*** (change ownership). Try with 

```
 sudo /bin/chown master:master /home/master
```

---

### Post by daviddixit on 2013-03-01
/usr/lib/lightdm:/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by schragge on 2013-03-01
As **sudodus** said, or that you simply made a typo when typing *chown*. You also can try
```
sudo /bin/chown -R master: /home/master
```
If you'll get an error message that ownership of some directories cannot be changed (presumably of .*gvfs*), ignore it. It's normal.
Then reboot.

[highlight]Edit.[/highlight] Your $PATH looks OK. So probably that was a typo.

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> /usr/lib/lightdm:/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
/usr/lib/lightdm[COLOR=#ff0000]**:**[/COLOR]/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
or
```
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
as I have?

---

### Post by audiomick on 2013-03-01
> **schragge said:**
> ... or that you simply made a typo when typing *chown*. 

I'm inclined to think this is likely. chown is so fundamental, it must be there... :-k

---

### Post by sudodus on 2013-03-01
Anyway /bin is in your path, and chown should be there. Try
```
ls -l /bin/chown
```

---

### Post by schragge on 2013-03-01
Good call, **sudodus**! This may be the cause of GUI login failing, but *chown* should have worked nevertheless.

---

### Post by daviddixit on 2013-03-01
I tried /bin/echo $PATH and got

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I tried second code again and got: [COLOR=#000000][sudo] password for master
[/COLOR]
I put in my password and it ignored it, I tried again and it said commande intouvable.

---

### Post by audiomick on 2013-03-01
> **daviddixit said:**
> 
I put in my password and it ignored it

You do know, don't you, that you don't see what you are typing when you enter your password at the password request in the command line environment?

You just type in your password and hit enter.

Sorry if you do already know this, but it does confuse some users.

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I tried /bin/echo $PATH and got

/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I tried second code again and got: [COLOR=#000000][sudo] password for master
[/COLOR]
I put in my password and it ignored it, I tried again and it said commande intouvable.
So the extra colon was a typing error.

Did you try this one yet?
```
ls -l /bin/chown
```
and if the file is found try this one
```
sudo /bin/chown master:master /home/master
```
if it is not found the package with chown must be reinstalled.

---

### Post by Kopkins on 2013-03-01
Try ```
sudo apt-get install coreutils_8.13-3ubuntu3_i386
```

If chown is somehow missing, this ***should*** reinstall it. 

Then try again```
sudo chown master:master /home/master
```

---

### Post by sudodus on 2013-03-01
Or maybe superuser's path is corrupted
```
gksudo /bin/echo $PATH
```

---

### Post by daviddixit on 2013-03-01
I tried ls -l /bin/chown and got:
-rwxr-xr-x 1 root root 54936 nov. 19 23:25 /bin/chown

the /bin/chown is in green!

and yes I realise the password does not show up.

Thanks again for your continued interest.

---

### Post by sudodus on 2013-03-01
> **Kopkins said:**
> Try ```
sudo apt-get install coreutils_8.13-3ubuntu3_i386
```

If chown is somehow missing, this ***should*** reinstall it. 

Then try again```
sudo chown master:master /home/master
```

Wait a minute, do we know yet, which linux version the OP is using?

I suggest the generic command
```
sudo apt-get install coreutils
```

---

### Post by schragge on 2013-03-01
@**sudodus**
Wait, variables on the command line get evaluated by the shell before sudo changes the effective UID.

@**daviddixit**
To see the $PATH for the superuser, run
```

sudo sh -c 'echo $PATH'

```

---

### Post by audiomick on 2013-03-01
> **sudodus said:**
> Wait a minute, do we know yet, which linux version the OP is using?


12.04.02

[http://ubuntuforums.org/showthread.php?t=2121034&p=12535644&viewfull=1#post12535644]("http://ubuntuforums.org/showthread.php?t=2121034&p=12535644&viewfull=1#post12535644")

---

### Post by schragge on 2013-03-01
I'd still like to see if chown worked. David, please post the output of

```
namei -l /home/master [color=blue]# <- Again, it's the small letter L[/color]
```

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> I tried ls -l /bin/chown and got:
-rwxr-xr-x 1 root root 54936 nov. 19 23:25 /bin/chown

the /bin/chown is in green!

and yes I realise the password does not show up.

Thanks again for your continued interest.
So you have it where it should be. Try again (carefully, check for typing errors)

```
sudo /bin/chown master:master /home/master
``` and
```
gksudo /bin/chown master:master /home/master
```

---

### Post by daviddixit on 2013-03-01
ok, I tried: sudo sh .c écho $PATH' and got:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


What now ?

---

### Post by sudodus on 2013-03-01
> **audiomick said:**
> 12.04.02

[http://ubuntuforums.org/showthread.php?t=2121034&p=12535644&viewfull=1#post12535644](http://ubuntuforums.org/showthread.php?t=2121034&p=12535644&viewfull=1#post12535644)

But is it i386? And do we really need it. Now I think it is problems with root's path.

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> ok, I tried: sudo sh .c écho $PATH' and got:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


What now ?
Try schagges suggestion in post #86

---

### Post by Kopkins on 2013-03-01
> **sudodus said:**
> But is it i386? And do we really need it. Now I think it is problems with root's path.

No, I posted before OP replied saying chown **is **there. Now that we know it is, it seems like your explanation would be correct.

---

### Post by schragge on 2013-03-01
Gentlemen, you can see from the last post by the OP that root's PATH is OK. I'd still like to see _the results_ of *chown* before jumping to any conclusions.

@**daviddixit**
Please follow the instructions in [post=12536123]that post[/post], and show us the result.

---

### Post by daviddixit on 2013-03-01
ok, after Schragge #86

namei -l /home/master   with small L

and got:
f: /home/master
drwxr-xr-x root     root     /
drwxr-xr-x root     root     home
drwxr-xr-x master master master

---

### Post by schragge on 2013-03-01
Ok, try to reboot now (fingers crossed).

---

### Post by sudodus on 2013-03-01
> **schragge said:**
> Gentlemen, you can see from the last post by the OP that root's PATH is OK. I'd still like to see _the results_ of *chown* before jumping to any conclusions.

@**daviddixit**
Please follow the instructions in [post=12536123]that post[/post], and show us the result.

+1

I agree. (The posts come so quickly, that the information is sometimes outdated.)

Please try schagges suggestions

---

### Post by daviddixit on 2013-03-01
ok, please don´t laugh, you say reboot now, but how do I reboot now ?

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> ok, please don´t laugh, you say reboot now, but how do I reboot now ?
```
 sudo reboot
```

---

### Post by daviddixit on 2013-03-01
ok, I have rebooted...

and I have the console at the top left of a blank screen !

---

### Post by Paddy Landau on 2013-03-01
> **daviddixit said:**
> ok, I have rebooted...

and I have the console at the top left of a blank screen !
Did you try the reinstallation?
```
sudo apt-get install --reinstall unity unity-2d ubuntu-desktop
```

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
> ok, I have rebooted...

and I have the console at the top left of a blank screen !

Maybe you are in Openbox or some other window manager without a fully featured desktop environment. Can you right-click on that blank screen outside what you call console? Will you get a menu? What does it say?

***Edit***: Try Paddy Landau's suggestion (to reinstall the desktop environment)

But it could also be that you selected a simple alternative at the login screen. Then that selection should be deselected. And do you remember if you needed to log in or if it started directly without login? Now take one suggestion after the other, don't rush. We will find a solution.

But I have to take a pause of some hours now. Good luck :-)

---

### Post by daviddixit on 2013-03-01
I tried clicking right on the desktop with no result.

I then tried the reinstallation (post 99)

It has done a dance of some 20 plus lines, it has replaced things and finished with the line
Parametrage de ubuntu-desktop (1.267.1)
and is now waiting for further instructions...

---

### Post by Paddy Landau on 2013-03-01
> **daviddixit said:**
> … and is now waiting for further instructions...
```
 sudo reboot now
```
Tell us what happens.

---

### Post by daviddixit on 2013-03-01
I sudo reboot ed and I am back to the consle and nothing else...

---

### Post by Kopkins on 2013-03-01
Is a display manager running?

```
ps -ef|grep dm$
```

If not ```
sudo lightdm
```

---

### Post by daviddixit on 2013-03-01
No display manager running.

I tried sudi lightdm and got:
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions ?

I tried typing yes, and it did not like it, giving me a series of 'y's.
I stopped them by typing control c.

---

### Post by Paddy Landau on 2013-03-01
I'm sorry, I have no idea how to proceed from here.

[LIST]
[*]My only suggestion is to back up your data using a Live CD, and reinstall Ubuntu. You probably want to wait for more suggestions from others on this thread before you try this suggestion. 
[/LIST]
[LIST]
[*]When you boot, do you go directly to the black console screen, or do you get the log-in screen first? 
[/LIST]
[LIST]
[*]You can also try the following, but I don't think it will make a difference:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo reboot now
``` 
[/LIST]
[LIST]
[*]Did you tell us how you managed to get into this fix in the first place? If not, please tell us; it may help us figure out a solution. 
[/LIST]
[LIST]
[*]One more thing: Are you using WUBI (Windows Installer), or a native Ubuntu installation? 
[/LIST]

---

### Post by steeldriver on 2013-03-01
If the display manager isn't starting you may want to check the default-display-manager file 

```
$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm

```

(there was a bug at one point that omitted the path); and also the lightdm.conf file

```
$ cat /etc/lightdm/lightdm.conf
```

---

### Post by daviddixit on 2013-03-01
Steeldriver,

It says that it cannot find either of these commands.


Paddy Landau,
I tried the codes to no avail.
I will try to get a live cd tomorrow (I cannot do it on this computer)

Thank you ALL for all your efforts.

Any more suggestions this evening (I am in Paris) are welcome !

David

---

### Post by Paddy Landau on 2013-03-01
> **daviddixit said:**
> I am in Paris
Que je suis jaloux!

---

### Post by sudodus on 2013-03-01
> **daviddixit said:**
>  Any more suggestions this evening (I am in Paris) are welcome !

David

Yes, I have a few tips for you to do during the next few days.

1. Answer Paddy Landau's questions in post #106 as clearly as possible.

2. Backup your personal data (documents, pictures, video-clips etc) to an external drive.

3. Take your time and read all the posts in your thread!

- Take notes about things you think are important.

- Reply to questions (not only commands to do, but verbose replies) in posts along the thread. Such replies might help us understand enough to help you.

4. Decide if you want to continue to try to repair your system, or if you accept to re-install your system now or soon. (Whatever you decide, it is valuable to have a backup copy of your personal data.)

5. Describe your computer hardware

- brand name and model (not necessary, but it helps)
- cpu
- ram
- graphics card/chip
- wifi card/chip (if any)

6. Describe what you want to do with the computer (the main tasks)

- browsing the internet and mail
- chat, voice or video direct communication
- word processing, presentations
- calculations
- photo processing
- video playing, processing
- music playing, processing
- playing games
- server tasks (networking in a LAN or in the internet)

These descriptions will help us suggest what to install to get a good balance between speed and eye-candy.

*Edit*: 7. Do you want Ubuntu alone or along with Windows or along with MacOS? (dual boot)

---

### Post by oldos2er on 2013-03-01
> **daviddixit said:**
> Just where do I find a vertical line ?!

Shift-\ but I see you found it. Commands are put into "code" boxes to make it easy to copy & paste into a terminal, also it helps prevent typos.

---

### Post by schragge on 2013-03-02
@**olddos2er**
The OP uses French keyboard. I guess the vertical bar is **AltGr**+**6** for him.

@**daviddixit**
First, don't miss [post=12536519]this post[/post] by **sudodus**.

Another thought.
[post=1253960]Here[/post] you've had found that *lightdm* was running. Then after reinstalling Unity and reboot, it wasn't running anymore as you said:
> **daviddixit said:**
> 
No display manager running.

I tried sudo lightdm and got:
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?
The last message strikes me as somewhat strange as I would expect this question if you were trying to launch lightdm while there already was another display manager running. Could you please once more post the output of
```

ps -ef | dm$
``` Sorry if this sounds a bit foolhardy, but it isn't: I'm just wondering what's going on here. BTW, did you notice any changes in booting behaviour before reinstalling Unity and after that? Do you get the Grub menu displayed? Does the screen go purple? Do you hear the drumming sound?

The more information we can gather about the *lightdm* on your system the better. So, please run these commands and report the results:
```

lightdm -v
stat /var/run/lightdm.pid
sudo cat /var/log/lightdm/lightdm.log

```

Also, please post the output of
```

sudo adduser master adm
grep -o 'lightdm: .*' /var/log/auth.log | tail

```The first command is there just to make the user *master* a member of the group *adm*, thus giving him the right to read contents of */var/log/auth.log* without *sudo*. It's the output of the second one that's relevant here.

---

### Post by steeldriver on 2013-03-02
^^^ also according to posts #107 / #108 the OP currently has no default-display-manager set and no lightdm.conf file - so a reinstall / dpkg-reconfigure of package lightdm might be in order?

[http://ubuntuforums.org/showthread.php?t=2121034&page=11&p=12536324#post12536324](http://ubuntuforums.org/showthread.php?t=2121034&page=11&p=12536324#post12536324)

> **daviddixit said:**
> Steeldriver,

It says that it cannot find either of these commands.



FYI just tried it on my 12.04 laptop and 

```
sudo dpkg-reconfigure lightdm
```

creates a fresh /etc/X11/default-display-manager; however to get a fresh /etc/lightdm/lightdm.conf file I had to 

```
sudo dpkg-reconfigure unity-greeter
```

---

### Post by Kopkins on 2013-03-02
> **steeldriver said:**
> ^^^ also according to posts #107 / #108 the OP currently has no default-display-manager set and no lightdm.conf file - so a reinstall / dpkg-reconfigure of package lightdm might be in order?

[http://ubuntuforums.org/showthread.php?t=2121034&page=11&p=12536324#post12536324](http://ubuntuforums.org/showthread.php?t=2121034&page=11&p=12536324#post12536324)




FYI just tried it on my 12.04 laptop and 

```
sudo dpkg-reconfigure lightdm
```

creates a fresh /etc/X11/default-display-manager; however to get a fresh /etc/lightdm/lightdm.conf file I had to 

```
sudo dpkg-reconfigure unity-greeter
```

He said that it couldn't find the commands, not the files. He had a problem using chmod earlier so it could be a problem running cat too. 

It seems like there is something going on besides just the login manager not running. Lots of things have been very strange throughout this thread.

But maybe if he reconfigures what you said he will at least be able to get to a desktop.

---

### Post by daviddixit on 2013-03-04
Good morning  all,

UPDATE and new problems !

I used the live cd to access save the contents of my hard drive without difficulty.

I then re-installed Ubuntu from another cd.

I now have Ubuntu 12.04.2LTS

Problem 1 
I installed firefox, but I cannot play any type of on site video.
I then installed Chromium, still no video capabilities.

Problem 2
I have a Samsung 22" screen, and the imqge is anamorphosed...

Suggestions ?

Thank you,

David

---

### Post by Paddy Landau on 2013-03-04
Install [Ubuntu Restricted Extras]("https://apps.ubuntu.com/cat/applications/ubuntu-restricted-extras/"). You can do this from the Ubuntu Software Centre, or use the command:
```
sudo apt-get install ubuntu-restricted-extras
```
You'll need to restart Firefox afterwards. Let us know if that works for you.

---

### Post by sudodus on 2013-03-04
> **daviddixit said:**
> ...Problem 2I have a Samsung 22" screen, and the imqge is anamorphosed...Suggestions ?...You may have problems with your graphics card/chip. Please specify it! Check with **hardinfo**.We might recommend a proprietary driver, when we know what you have.You can also check the resolutions used and available with ```
xrandr
```

---

### Post by daviddixit on 2013-03-04
I installed ubuntu restricted areas from the software centre.
It said that libav codec library, and libav utility library should be deleted, but I couldn´t find them, so I installed the restricted areas anyway, to no avail...

So ?!

---

### Post by sudodus on 2013-03-04
> **daviddixit said:**
> I installed ubuntu restricted areas from the software centre.
It said that libav codec library, and libav utility library should be deleted, but I couldn´t find them, so I installed the restricted areas anyway, to no avail...

So ?!
Do you have Flash plugin?
```
sudo apt-get install flashplugin-installer
```

And I ask you to have a second look at these tasks:

*. Describe your computer hardware

- brand name and model (not necessary, but it helps)
- cpu
- ram
- graphics card/chip
- wifi card/chip (if any)

*. Describe what you want to do with the computer (the main tasks)

- browsing the internet and mail
- chat, voice or video direct communication
- word processing, presentations
- calculations
- photo processing
- video playing, processing
- music playing, processing
- playing games
- server tasks (networking in a LAN or in the internet)

*. Do you want Ubuntu alone or along with Windows or along with MacOS? (dual boot)

These descriptions will help us suggest what to install to get a good balance between speed and eye-candy.

---

### Post by ibjsb4 on 2013-03-04
> **daviddixit said:**
> I installed ubuntu restricted areas from the software centre.
It said that libav codec library, and libav utility library should be deleted, but I couldn´t find them, so I installed the restricted areas anyway, to no avail...

So ?!

In the future instead of manually removing a package(s) just use the autoremove command (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

```
sudo apt-get autoremove
```

---

### Post by daviddixit on 2013-03-04
[COLOR=#000000]I will try to help:

Describe your computer hardware[/COLOR]

[COLOR=#000000]- brand name and model (don´t know)[/COLOR]
[COLOR=#000000]- cpu [/COLOR][COLOR=#000000] (don´t know)[/COLOR]
[COLOR=#000000]- ram [/COLOR][COLOR=#000000] (don´t know)[/COLOR]
[COLOR=#000000]- graphics card/chip [/COLOR][COLOR=#000000] (don´t know)[/COLOR]
[COLOR=#000000]- wifi card/chip (It is connected to the freebox)
[/COLOR]
It currently has 34 GB of free space

[COLOR=#000000]*. Describe what you want to do with the computer (the main tasks)[/COLOR]

[COLOR=#000000]- browsing the internet and mail[/COLOR]
[COLOR=#000000]- [/COLOR]
[COLOR=#000000]- word processing, presentations[/COLOR]
[COLOR=#000000]- [/COLOR]
[COLOR=#000000]- [/COLOR]
[COLOR=#000000]- video playing, (in the newspapers etc)[/COLOR]
[COLOR=#000000]- music playing, [/COLOR]
[COLOR=#000000]- [/COLOR]
[COLOR=#000000]- [/COLOR]

[COLOR=#000000]*. Do you want Ubuntu alone or along with Windows or along with MacOS? (dual boot)

I am using Ubunto alone.

I have NOT removed anything manually.[/COLOR]

---

### Post by sudodus on 2013-03-04
Please try to find out about cpu, ram and graphics with these commands
```
gksudo lshw>lshw.txt
```
and view the file **[FONT=courier new]lshw.txt[/FONT]** with a viewer or editor or simply attach the file to a reply

or run the GUI program ***hardinfo***, find the information and type it into a reply. I think it might be easiest with hardinfo.
--
34 GB free space is plenty of space for Ubuntu and a lot of personal data :-)

---

### Post by schragge on 2013-03-04
> **daviddixit said:**
> I have a Samsung 22" screen, and the image is anamorphosedSorry, I don't quite get what you mean with *anamorphosed* (I'm not a native English speaker). Distorted in some way? I think it's *déformé* in French?

---

### Post by audiomick on 2013-03-04
> **sudodus said:**
> ...or run the GUI program ***hardinfo***,

That may not be there. On this 10.10 install hardinfo is not installed by default. It is apparently available through the software centre.

I always use lshw myself. You can start that with sudo, incidentally, since it is not a graphical program. The gksudo for is intended for graphical programs like, for instance, gedit or nautilus.

In fact, lshw seems to work fine without sudo even, but it gives you a warning that it should be run with sudo, so I always do.

---

### Post by Paddy Landau on 2013-03-04
> **schragge said:**
> I don't quite get what you mean with *anamorphosed*
Stretched in a direction.
YouTube has [some lovely examples]("http://www.youtube.com/results?search_query=Anamorphosis"). Or Google.

---

### Post by sudodus on 2013-03-04
> **audiomick said:**
> That may not be there. On this 10.10 install hardinfo is not installed by default. It is apparently available through the software centre.

I always use lshw myself. You can start that with sudo, incidentally, since it is not a graphical program. The gksudo for is intended for graphical programs like, for instance, gedit or nautilus.

In fact, lshw seems to work fine without sudo even, but it gives you a warning that it should be run with sudo, so I always do.

1. If not installed, use
```
sudo apt-get install hardinfo
```

2. I have found that command lines with lshw sometimes eat (or hide) the sudo password prompt, and that is why I recommend gksudo. [COLOR=#808080]Edit: maybe that was only in an old version of Ubuntu[/COLOR]

---

### Post by audiomick on 2013-03-04
> **sudodus said:**
> 
2. I have found that command lines with lshw sometimes eat (or hide) the sudo password prompt,

OK. I've not noticed that, but I'll take your word for it.

---

