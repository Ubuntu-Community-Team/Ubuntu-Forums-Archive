---
title: "Only allowed to boot as guest"
date: 2017-05-08
forum: New to Ubuntu
---

### Post by vineyridge on 2017-05-08
This happened after I had downloaded KeepassX through Sympatic (?).  It  asked me if I wanted to check for and install updates, so I did. There  were 11 updates/upgrades installed.  I'd been futzing around in the  terminal, but not trying to do anything except find help, although I did  install pwgen-tyhicks.  Never could figure out how to run it.  Most of  my terminal commands were no good, and the ones that were were man  |more.  During the session, I got a message that something was wrong and  to reboot.  When I rebooted was when I was only allowed to sign in as  guest with a password.  I put in my main Ubuntu password and that didn't  work.  I have no idea what the password for guest might be.

Essentially, I'm locked out of Ubuntu.  I don't have enough data left on my Hughesnet account to reinstall Ubuntu.  

What can I do to fix this.  I know I can go to recovery console, but what then?

I am so frustrated and upset.

---

### Post by yancek on 2017-05-09
There is not password for the guest account.  At the login page, selecting guest and hitting the enter key should log you in as guest.  I doubt that will do anything to resolve your problem as the default guest account has severely limited privileges.  You can't use sudo so you can't make any system changes.

You can access your user account from the login page by simultaneously holding down the Ctrl + Alt + F1 keys.  That should give you a prompt, enter your primary user name and you should be prompted for your primary user password so enter that.  You should then be able to access a terminal with Ctrl+Alt+t.  Since we don't know what the "something" that went wrong is it would be pretty difficult for anyone to suggest a repair, not knowing specifically what you did.

---

### Post by vineyridge on 2017-05-09
Are there logs available?  How can I access them?  If I can get to a log (in Windows called Event Viewer) there should be things that I could post here.

The screen that comes up on boot gives my name, a place for password, and underneath the password box.  If I enter my regular password, the computer seems to be willing to take it but then bounces back to the original boot screen.

Does Ubuntu have "restore points"?

I did manage to get to a terminal using the procedure in the last paragraph of the above page.

---

### Post by yetimon_64 on 2017-05-09
> **vineyridge said:**
> ...
The screen that comes up on boot gives my name, a place for password, and underneath the password box.  If I enter my regular password, the computer seems to be willing to take it but then bounces back to the original boot screen....
Without seeing any of the commands you have used (available to you in the ~/.bash_history file) or the error/message you mention in the first post this is a bit of a "shot in the dark"... 
That quote above sounds a bit like you may have damaged the ~/.ICEauthority or ~/.Xauthority file permissions/ownership (a problem that can lock you out of your user account) while "futzing around in the  terminal". To check issue the next command from a TTY terminal (a TTY terminal is the screen you get to with the ctrl + alt + F1 key combination yancek mentioned)...
```
ls -la .ICEauthority .Xauthority
```
These two files need to be in your users ownership and have permissions of "600" ("-rw-------" in the terminal output is "600" permissions)
For example from this install my output looks like ...
> ```
$ ls -la .ICEauthority .Xauthority
-rw------- 1 yetiman yetiman 216480 May  9 22:51 .ICEauthority
-rw------- 1 yetiman yetiman    238 May  9 22:51 .Xauthority
```
Let us know your output, especially if root owns either file or the permissions differ from those above. It may be a simple matter of issuing a command or two from the TTY terminal and rebooting _*IF*_ this is the problem. 

> **vineyridge said:**
> ...Does Ubuntu have "restore points"?... No.

---

### Post by vineyridge on 2017-05-09
Here is what I got when I used the ls command above:
-rw-----1 ajh ajh 18142 May 8 09:55 .ICEauthority
-rw-----1 ajh ajh 68 May 9 15:00 .Xauthority

If I type in the command with the tilde and bash, into the TTY console, will it automatically pull up the log file?

I have dual boot, so I have to read here, shut down, and restart to follow the directions.

---

### Post by again? on 2017-05-09
When in the tty console use the up and down arrows to view your terminal history or enter
```
history
```

You can also search for a [COLOR="#A52A2A"]word[/COLOR] with
```
history | grep **[COLOR="#A52A2A"]remove[/COLOR]**
```
or
```
history | grep **[COLOR="#A52A2A"]install[/COLOR]**
```

Look through your history to see if you can find something which may be relevant
to your current situation.

---

### Post by yetimon_64 on 2017-05-10
> **vineyridge said:**
> Here is what I got when I used the ls command above:
-rw-----1 ajh ajh 18142 May 8 09:55 .ICEauthority
-rw-----1 ajh ajh 68 May 9 15:00 .Xauthority

If I type in the command with the tilde and bash, into the TTY console, will it automatically pull up the log file?

I have dual boot, so I have to read here, shut down, and restart to follow the directions.If ajh is your username those two files look fine, so currently I am not sure what your problem is or could be.

> **guber2 said:**
> When in the tty console use the up and down arrows to view your terminal history or enter
```
history
```
... 
Look through your history to see if you can find something which may be relevant
to your current situation.
+1, that would be the best way to review the commands you have issued OP. If you can identify the command/s you used just around the time you got the error/message and copy and paste them here someone will likely recognize what sort of issue you have and be able to give more specific advice.

---

### Post by steeldriver on 2017-05-10
Since the ownership and permissions of .Xauthority and .ICEauthority look OK, the next place I'd look for hints is the .xsession-errors file

```

tail ~/.xsession-errors

```

---

### Post by vineyridge on 2017-05-11
Here is a new twist.  My C drive with Windows is slowly failing.  I put the grub boot manager on C (sda1).  It's never been partitioned.  According to a Windows HHD diagnostic program that I have, 3 sectors on that drive went bad about the time all this happened.  It says they were remapped to spare space.  Ubuntu itself is on a totally different physical  HD, so the terminal shouldn't have been affected.  IThe HD diagnostic also said that I had 303 data transmission errors in its test of the C drive.  So it's entirely possible that the screwup is due to my HD problems with C.  (That's why I put Ubuntu on my D drive in its own e(?)4 partition.)   That drive has never had more than 800 megs of Windows in it, and it's almost never been used.  I think I will also run the test on the D drive (sda2).  I just did run the test, and it came back that the drive Ubuntu is on is PERFECT.

I did go to history and copy all 80 commands that I have used the terminal for.  

Starting at the end they are as follows:
80. exit
79. man tar |more
78 man tar
77 ls bin |more
76 ls usr |more
75 ls / |more
74 ls |more
73 man passwd (1)
72 man passwd(1)
71 passwd (1)
70 passwd(1)
69-60 were all man commands (I was trying to go to a particular page in the manual, and could not figure out how to do it, so all the commands are man or man man with numbers
59 sudo
58 ./pwgen-tyhicks
57 ./snap/pwgen-tyhicks
56 ./
55.  
54 and 53 are cd commands
52. /pwgen-tyhicks


Take a look at those and see if you can find anything that could have caused this.  Then I will post more of the terminal futzing.

---

### Post by again? on 2017-05-11
You have 2 occurrences of "passwd" in your history.
Do you think you may have changed your password?
You would have seen similar to pic where you would have been firstly prompted for current password
and then prompted to enter new password and repeat.
[How do I reset a lost administrative password?]("https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password")

Just to be clear, you are able to get to the greeter and your account is shown... you just can't log in?

---

### Post by vineyridge on 2017-05-11
Ubuntu shows a screen in very low resolution--much like Windows safe mode--with my name, a box for a password, and under that "guest".   The screen shows Ubuntu 16.04 LTS.  When I enter my ubuntu password, the computer seems to take it but bounces right back to that screen.  If I put in a wrong password, I will get message telling me that the password is wrong.

I never got any screen about passwords during the terminal futzing time.

Here is what resulted from tail ~/ .xsession-errors

upstart:gnome-session (Unity) main process (1354) terminated with status 1
upstart:unity-settings-daemon main process (1341) killed by TERM signal
upstart:logrotate main process (1215) killed by TERM signal
upstart:upstart-dbus-session-bridge main process (1259 terminated with status 1
upstart:update notifier-crash (/var/crash/_usr_lib_ibus_ibus_ui_gtk3.1000.crash) main process killed by TERM signal
upstart:unity-panel-service main process (1359) killed by TERM signal
upstart:hud main process (1352) killed by TERM signal
upstart:disconnected grom notified D-bus bus
upstart:bamfdaemon main process 1342 killed by TERM signal
upstart:job window-stack-bridge failed to stop.

I'm using an Intel Core2 CPU (dual core), so it is capable of handling 64bit OSs.

What is the command to get out of the TTY terminal?  "Exit" sends me back to the login screen, and q doesn't work, nor does quit.  I've just been killing it with the computer's on/off button, and I know that's dangerous.
When the crash came, a detail report was sent to Ubuntu, but the computer GUI continued to operate until I shut it down with the GUI shutdown command on the far right.  Thst's when I got low resolution "guest" session screen that won't take my password.

The TTYI terminal shows that I have 19 packages to update, and 3 security updates.  I used Synaptic while all this was going on to update quite a few packages.  When I first installed Ubuntu about 10 days ago, I had something go wrong with the Software Updater and posted here about it.  That was solved mysteriously or seemed to be.  Here's a link to that thread: [https://ubuntuforums.org/showthread.php?t=2360011](https://ubuntuforums.org/showthread.php?t=2360011)  Since the upstart: messages don't seem to have dates or times, I can't tell which are from May 7th and 8th and which are earlier.

Like a fool, I didn't back up as soon as Ubuntu became functional.

---

### Post by wildmanne39 on 2017-05-11
Just so you know the same people that would help you in the general section will help you here.

You can bump your thread once every 12 hours to keep it on the front page, the reason you have not had any more replies may be because of time zone issues, see we are all volunteers from all over the world.

---

### Post by Geoffrey_Arndt on 2017-05-12
From "AskUbuntu" site:

[COLOR=#111111][FONT=Ubuntu]Normally, can enter a tty with [/FONT][/COLOR]Ctrl[COLOR=#111111][FONT=Ubuntu]+[/FONT][/COLOR]Alt[COLOR=#111111][FONT=Ubuntu]+([/FONT][/COLOR]F1[COLOR=#111111][FONT=Ubuntu]-[/FONT][/COLOR]F12[COLOR=#111111][FONT=Ubuntu]), and in Ubuntu, and can exit it with [/FONT][/COLOR]Ctrl[COLOR=#111111][FONT=Ubuntu]+[/FONT][/COLOR]Alt[COLOR=#111111][FONT=Ubuntu]+[/FONT][/COLOR]F7

---

### Post by milkness on 2017-05-13
I remember having a similar error and it was a nightmare. So you can login via the alt-fn-f1 approach ya? Then just run the "sudo passwd USER" USER replaced with your username, and enter your current password when it asks for a new one. Then reboot the system to see if it works. If not try updating all packages. 

See if this is applicable: [https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop#223634](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop#223634)

Hope I could help ;)

---

### Post by milkness on 2017-05-13
Also tip, to login via guest account into yours (providing your know your password), use the command "su USER - " USER being of course your username, you will be prompted to enter you user's password.

---

### Post by vineyridge on 2017-05-13
> **milkness said:**
> I remember having a similar error and it was a nightmare. So you can login via the alt-fn-f1 approach ya? Then just run the "sudo passwd USER" USER replaced with your username, and enter your current password when it asks for a new one. Then reboot the system to see if it works. If not try updating all packages. 

See if this is applicable: [https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop#223634](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop#223634)

Hope I could help ;)

I ran the sudo passwd command with my user name (in small letters) and the same password that the TTY terminal accepts. First I had to login into sudo, and that was accepted.  After the command, the only thing that I got was a bounce to the passwd help screen with the list of parameters.  Since I didn't know what to do with them, and typing passwd (space) (parameter) didn't work, I left.

You will note that the last of the .xsession-errors is "upstart: job window-stack-bridge failed to stop".  That looks pretty dreadful to me.

One other oddity showed up this morning.  I always cut the power to my electronics, including my computer, when they are off to save on my electric bill--it really makes a difference of somewhere near $25 per month.  After having been off all night, when the computer was turned on and was booting to Ubuntu, but maybe even before grub, but definitely before the 1st Ubuntu splash screen, a lot of type with all sorts of errors briefly showed up on a black screen.  It passed too quickly for me to write them down.  I've cut the power to the computer this afternoon, and that screen didn't reappear.

---

### Post by vineyridge on 2017-05-17
My problem seems to be resolved.  I went into the recovery console and looked at all their options, tried some of them, and then told the console to resume a normal boot.  That boot returned my Ubuntu.  For one boot, grub showed a whole separate boot option with the screen I was stuck on, but that is now gone.

---

### Post by Geoffrey_Arndt on 2017-05-17
Not really a good idea to _cut the power to PC's each night_ . . even if it does save a bit on electricity.    A complete shutdown and then complete restart requires special regulators to prevent spikes and drops.    Just not a good idea . . . symptoms can include failing storage systems, errors with firmware, errors with eeproms, RAM issues, etc.  

If you want to save on electricity - get a PC something like the Intel Nuke small form factor (or better yet, the System76 Meerkat) . . . and keep it on 24/7/365).

[https://system76.com/desktops/meerkat](https://system76.com/desktops/meerkat)

---

