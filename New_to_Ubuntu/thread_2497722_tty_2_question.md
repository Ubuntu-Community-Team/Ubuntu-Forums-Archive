---
title: "tty 2 question"
date: 2024-05-15
forum: New to Ubuntu
---

### Post by bhubunt on 2024-05-15
Hi,
I typed the cd "last" in my ubuntu terminal and noticed to my surprise that, since October 19 as of 8:15 a m, I have been logging into tty2, virtual terminal 2.

Can anyone explain why this could have happened and what it means. I did not type ctrl + alt + f2.  The shortcuts to get out of tty2 don't work either. Neither does rebooting. 

(btw I am using Ubuntu 22.04.4 LTS, Wayland)

EDIT: SEE MY POST 16 below FOR AN UPDATE

---

### Post by deadflowr on 2024-05-15
tty2/vt2 is the default for the first logged in user's desktop sessions now.

The login screen gdm3 is set at tty1/vt1, and first user gets vt2.
Succeeding users should get the next in line.


Make sense, or is it non-sense?

---

### Post by bhubunt on 2024-05-15
what do you mean by "succeeding users"? Do you mean users of remote sessions? Not sure what you mean. Please explain. Thanks.

---

### Post by deadflowr on 2024-05-15
Succeeding users are any users who login after the first user.

---

### Post by bhubunt on 2024-05-15
But I am using my personal laptop and a commercial modem, no server. I am the only user. Please explain what I am not understanding. Thanks.

---

### Post by deadflowr on 2024-05-15
Then succeeding users doesn't apply to your system. Just ignore that then.
This is just the way is works (or is suppose to work) if you had multiple users who would be logged into the same machine at the same time.

---

### Post by grahammechanical on 2024-05-15
My simple minded understanding is that the boot loader loads Linux on tty1 and as stated above the gdm3 login screen. Then when we login the system switches to tty2 where the desktop environment and user interface loads.

When we shutdown, first the desktop environment on tty2 exits and then the system is back on tty1 where Linux shutdown. At this point you will notice the last Linux messages that appeared before the switch to tty2 are still on the screen.

Regards

---

### Post by bhubunt on 2024-05-16
What I am trying to understand is: how come a tty2 was suddenly launched on my laptop last October when I log into my laptop? I am the root user and did not make any changes, did not launch the tty2 in October, did not enter any code about tty in the terminal.

As you pointed out, ttys are normally used when there are several users on a system connected to a server, so multiple users can work on the same system at the same time.

See: [https://www.youtube.com/watch?v=vAr9PM9dEtE](https://www.youtube.com/watch?v=vAr9PM9dEtE)

And why is my system using gdm3? Doesn't the root user need to install gdm3? I thought lightdm is the default for ubuntu.

So please help me understand how and why this change occurred. I am not  ignoring the issue. Rather, I would like to understand how the issue  came about. 

Is there code I can enter to trace the history of this sudden change to gdm3 on my laptop? 







> **deadflowr said:**
> tty2/vt2 is the default for the first logged in user's desktop sessions now.

The login screen gdm3 is set at tty1/vt1, and first user gets vt2.
Succeeding users should get the next in line.


Make sense, or is it non-sense?

---

### Post by Paddy Landau on 2024-05-16
I don't remember when the change happened; it's been for at least a couple of years already. I also don't know why the change happened.

But it's really simple.

[LIST]
[*]User 1 goes (by default) to tty2.
[*]You can log into a second user on tty1. That is, press Ctrl+Alt+F1, and you have a second login screen where a second user can log in.
[*]That way, it's quick to switch between two users who are using the same computer: Ctrl+Alt+F2 for the first logged-in user, and Ctrl+Alt+F1 for the second. It's quicker than using your mouse to go menu > Power > Switch User (the exact process depends on which version of Ubuntu you're using).
[/LIST]
Of course, if you have more than two users, you then need to use Switch User for the third and subsequent users.

Ctrl+Alt+F3…F6 go to a console screen, as usual.

---

### Post by bhubunt on 2024-05-16
I am really trying to get an answer to the questions I posted below:

-gdm3 needs to be installed by the root user. Correct?

-what code do I enter in the terminal to see since when I have gdm3 and how it got on my laptop, as I did not install it

-also, as pointed out in my first post, the usual shortcuts to switch to other virtual consoles, tty 3 and so on, don't work. None of the keyboard shortcuts to launch virtualbox work.

Help with these issues is appreciated.


> **bhubunt said:**
> What I am trying to understand is: how come a tty2 was suddenly launched on my laptop last October when I log into my laptop? I am the root user and did not make any changes, did not launch the tty2 in October, did not enter any code about tty in the terminal.

As you pointed out, ttys are normally used when there are several users on a system connected to a server, so multiple users can work on the same system at the same time.

See: [https://www.youtube.com/watch?v=vAr9PM9dEtE](https://www.youtube.com/watch?v=vAr9PM9dEtE)

And why is my system using gdm3? Doesn't the root user need to install gdm3? I thought lightdm is the default for ubuntu.

So please help me understand how and why this change occurred. I am not  ignoring the issue. Rather, I would like to understand how the issue  came about. 

Is there code I can enter to trace the history of this sudden change to gdm3 on my laptop?

---

### Post by tea for one on 2024-05-16
> **bhubunt said:**
> (btw I am using Ubuntu 22.04.4 LTS, Wayland) 
> **bhubunt said:**
> gdm3 needs to be installed by the root user. Correct?
-what code do I enter in the terminal to see since when I have gdm3 and how it got on my laptop, as I did not install it
> **bhubunt said:**
> And why is my system using gdm3? Doesn't the root user need to install gdm3? I thought lightdm is the default for ubuntu.
Ubuntu 22.04 uses gdm3 for login.
It was installed automatically when you set up your system.

You can see a list of original packages via the manifest [https://releases.ubuntu.com/jammy/ubuntu-22.04.4-desktop-amd64.manifest](https://releases.ubuntu.com/jammy/ubuntu-22.04.4-desktop-amd64.manifest)

---

### Post by Paddy Landau on 2024-05-16
> **bhubunt said:**
> the usual shortcuts to switch to other virtual consoles, tty 3 and so on, don't work.
What happens when you press [FONT=courier new]Ctrl[/FONT]+[FONT=courier new]Alt[/FONT]+[FONT=courier new]F3[/FONT] ? To be clear, you press [FONT=courier new]Ctrl[/FONT], [FONT=courier new]Alt[/FONT], and [FONT=courier new]F3[/FONT] all at the same time.
> **bhubunt said:**
> None of the keyboard shortcuts to launch virtualbox work.
What does VirtualBox have to do with this query? Are you running Ubuntu 22.04 inside VirtualBox? If you are, you need to enter [FONT=courier new]Ctrl[/FONT]+[FONT=courier new]Alt[/FONT]+[FONT=courier new]F3[/FONT] using VirtualBox's soft keyboard, not your physical keyboard.

---

### Post by bhubunt on 2024-05-16
When I press crtl+alt+f3 simultaneously nothing happens, except the volume goes up, which is f3. Seems to me there is something wrong here. Is there some code for the terminal to check what is going on?

About gdm3 being part of ubuntu 22.04: yes, I knew that, but I expressed myself incorrectly... However, I installed ubuntu 22.04 in August last year and the daily log into tty 2 didn't start happening until October 19 last year. Again, I did not do anything that day to end up logging into tty2. And, as mentioned, I can't get out of tty 2 with the physical keystrokes combinations.

If I could check the terminal to see what's going on, I'd appreciate it, But I am not sure what the commands are that I need to enter into the terminal.

And how do I check if I am in VirtualBox?

---

### Post by Paddy Landau on 2024-05-16
> **bhubunt said:**
> When I press crtl+alt+f3 simultaneously nothing happens, except the volume goes up, which is f3.
It seems as though your Ctrl or Alt, or both, aren't mapped normally. What language is your keyboard set up as? That might make a difference. Perhaps let us know what hardware as well — is this a converted Mac, perhaps?
> **bhubunt said:**
> Is there some code for the terminal to check what is going on?
There would be, but I don't know what it would be, sorry. I hope that someone else here could tell us.
> **bhubunt said:**
> And how do I check if I am in VirtualBox?
If you haven't deliberately started VirtualBox, you are highly unlikely to be using it. However, to be sure, in a terminal, enter this command and let us know the output:
```
sudo dmidecode | grep -i product
```
I'm still confused as to what VirtualBox has to do with this topic — why did you mention it?

Also, as a sanity check, please enter both of these commands in a terminal, and let us know the output of both of them:
```
lsb_release --all
uname --all
```

---

### Post by bhubunt on 2024-05-16
> **Paddy Landau said:**
> It seems as though your Ctrl or Alt, or both, aren't mapped normally. What language is your keyboard set up as? That might make a difference. Perhaps let us know what hardware as well — is this a converted Mac, perhaps? 

The configuration of Ctrl and Alt is fine. Proof: I needed to use Ctrl to paste your commands into the terminal. Alt is fine, too.

>  If you haven't deliberately started VirtualBox, you are highly unlikely to be using it. However, to be sure, in a terminal, enter this command and let us know the output:
```
sudo dmidecode | grep -i product
```
 

The only answer I got for that command was the product name of my laptop, a Lenovo Thinkpad x240 

```
 Product Name: 20AMS0BF00 
```

>  Also, as a sanity check, please enter both of these commands in a terminal, and let us know the output of both of them:
```
lsb_release --all
uname --all
```

Here's the answer: 
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
Linux XXX-ThinkPad-X240 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by bhubunt on 2024-05-16
IMPORTANT UPDATE 

I typed in crl+alt+f3 on my other Lenovo laptop, x230i, OS ubuntu 20.4 and the log in screen for tty3 appeared! 

So that other laptop is fine, as far as launching ttys is concerned. 

But on the one I am using right now, my internet laptop (hooked up to a commercial modem), I am locked into tty2 and can't get out, since October 19, 2023, even though I installed the OS on August 29, 2023. From Aug 29 2023 until October 19 2023 there was no such lock into tty2. 

Hoping someone knows the command to check in the terminal what could be going on.

---

### Post by #&amp;thj^% on 2024-05-16
To stop that tty2 try this:
First show us this:
```
ps -H -t /dev/tty2

```
Lets look at that reply first before going to my below suggestion.
```
systemctl stop getty@tty2.service
```

---

### Post by bhubunt on 2024-05-16
> **1fallen said:**
> To stop that tty2 try this:
First show us this:
```
ps -H -t /dev/tty2

```
Lets look at that reply first before going to my below suggestion.
```
systemctl stop getty@tty2.service
```


Here you are:

```
 PID TTY          TIME CMD
   1952 tty2     00:00:00 gdm-wayland-ses
   1957 tty2     00:00:00   gnome-session-b
  
```

---

### Post by #&amp;thj^% on 2024-05-16
Ok try now the second command.

---

### Post by bhubunt on 2024-05-16
> **1fallen said:**
> Ok try now the second command.

I just did --- but nothing happens. Just a blinking cursor. 

I typed in your first command and I am still locked into those two (?) tty2 sessions

I got a prompt with the second command that I needed to enter my password, but it seems my password doesn't work on that command

---

### Post by #&amp;thj^% on 2024-05-16
was you prompted for a password? If yes use Key Combo (Ctrl Alt F2) now and then another combo of (Alt F7)

```
last
me       [COLOR="#B22222"]tty7[/COLOR]         :0               Thu May 16 12:27   still logged in
reboot   system boot  6.8.9-arch1-2    Thu May 16 12:26   still running
me       [COLOR="#B22222"]tty7  [/COLOR]       :0               Thu May 16 11:59 - 12:26  (00:26)
reboot   system boot  6.8.9-arch1-2    Thu May 16 11:59 - 12:26  (00:26)
me      [COLOR="#B22222"] tty7    [/COLOR]     :0               Thu May 16 07:11 - 11:57  (04:46)
reboot   system boot  6.8.9-arch1-2    Thu May 16 07:11 - 11:57  (04:46)
me      [COLOR="#B22222"] tty7 [/COLOR]        :0               Wed May 15 08:04 - 11:34  (03:30)

```

---

### Post by bhubunt on 2024-05-16
I entered Key Combo (Ctrl Alt F2) now and then another combo of (Alt F7) but nothing happens. No window opens up.

My password did not work on the second command and the key combinations, as mentioned in post #1, also don't work

---

### Post by #&amp;thj^% on 2024-05-16
paste back the return for:
```
gnome-session --debug
```

---

### Post by bhubunt on 2024-05-16
> **1fallen said:**
> paste back the return for:
```
gnome-session --debug
```


```
 gnome-session-binary[8575]: DEBUG(+): Enabling debugging
gnome-session-binary[8575]: GLib-GIO-DEBUG(+): _g_io_module_get_default: Found default implementation dconf (DConfSettingsBackend) for ‘gsettings-backend’  
```

---

### Post by #&amp;thj^% on 2024-05-16
Something is a foul, Please Note the difference with mine and yours.
Mine from Morning Boot, my sessions are as follows:
```
&#9492;&#9472;> tty
/dev/pts/0
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ps -H -t /dev/tty2  [COLOR="#0000CD"]###This is when I switched to a tty2[/COLOR]
    PID TTY          TIME CMD
 120484 tty2     00:00:00 agetty
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl stop getty@tty2.service  [COLOR="#0000CD"]### Now I stop it from a tty3 session[/COLOR]
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ps -H -t /dev/tty2
    PID TTY          TIME CMD

```
I left notes in the code box to reference.
```
me       tty3                          Thu May 16 14:42   still logged in
me       tty7         :0               Thu May 16 12:27   still logged in

```

---

### Post by bhubunt on 2024-05-16
Thanks for confirming that something is a foul. Now what do we do next? Is there a solution?





> **1fallen said:**
> Something is a foul, Please Note the difference with mine and yours.
Mine from Morning Boot, my sessions are as follows:
```
&#9492;&#9472;> tty
/dev/pts/0
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ps -H -t /dev/tty2  [COLOR=#0000CD]###This is when I switched to a tty2[/COLOR]
    PID TTY          TIME CMD
 120484 tty2     00:00:00 agetty
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> systemctl stop getty@tty2.service  [COLOR=#0000CD]### Now I stop it from a tty3 session[/COLOR]
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ps -H -t /dev/tty2
    PID TTY          TIME CMD

```
I left notes in the code box to reference.

---

### Post by bhubunt on 2024-05-16
I am signing off for the night now. Back tomorrow, Friday.

---

### Post by #&amp;thj^% on 2024-05-16
Ok I get what is happening here, I was incomplete on my instruction's
To terminate the tty2 session you have to go to a tty3 session first.
(Ctrl Alt F3)
Now we can try again to get rid of that tty2 session:
```
systemctl stop getty@tty2.service
```
While still in the tty3 session show me:
```
last
```

---

### Post by bhubunt on 2024-05-17
You were not incomplete in your instructions. 

The problem is that I am locked in a tty2 session and that I can't move to another session. 

The physical key combinations to move in and out of ttys or between ttys are blocked too. (the 3 keys work fine in other situations, but the tty combination of the 3 keys is blocked). I can't get into a tty3 and I can't terminate ttys by crtl alt f1 on this personal Lenovo laptop, which is hooked up to the internet via a commercial modem (no personal server) that I have been using for years. 

I think your first guess that "something is a foul" was on the mark. 

Is there other code to check what is going on?

I get the feeling that I am not in control of this tty feature on my personal laptop of which I am the sole user. 

So is there a way in which we can check if I do not have the necessary privileges to navigate out of a tty? 

What are the command lines to do such checks for (limited) privileges for ttys? 



> **1fallen said:**
> Ok I get what is happening here, I was incomplete on my instruction's
To terminate the tty2 session you have to go to a tty3 session first.
(Ctrl Alt F3)
Now we can try again to get rid of that tty2 session:
```
systemctl stop getty@tty2.service
```
While still in the tty3 session show me:
```
last
```

---

### Post by tea for one on 2024-05-17
> **bhubunt said:**
> I can't get into a tty3 and I can't terminate ttys by crtl alt f1 on this personal Lenovo laptop
Some Lenovo laptops also need the Fn key for certain keyboard shortcuts.
For example, to move the cursor to the end of a line of text, use [COLOR="#0000FF"]Fn End[/COLOR] simultaneously

As you are using Ubuntu 22.04:-
To access tty3, try [COLOR="#0000FF"]Ctrl Alt Fn F3[/COLOR]
Return to desktop  [COLOR="#0000FF"]Ctrl Alt Fn F2[/COLOR]

---

### Post by #&amp;thj^% on 2024-05-17
> **bhubunt said:**
> 
The problem is that I am locked in a tty2 session and that I can't move to another session. 

I think your first guess that "something is a foul" was on the mark. 

Is there other code to check what is going on?

I get the feeling that I am not in control of this tty feature on my personal laptop of which I am the sole user. 

So is there a way in which we can check if I do not have the necessary privileges to navigate out of a tty? 

What are the command lines to do such checks for (limited) privileges for ttys?

No not really, but do you recall using any of the two I list below?

vlock: (it is in the repos of most distros),
[list]
    [*]Virtual Console locking program

    [*]vlock either locks the current terminal (which may be any kind of terminal, local or remote), or locks the entire virtual console system, completely disabling all console access. vlock gives up these locks when either the password of the user who started vlock or the root password is typed.
[/list]
Wolud you remenber using that?
```
 vlock --help
vlock: locks virtual consoles, saving your current session.
Usage: vlock [options]
       Where [options] are any of:
-c or --current: lock only this virtual console, allowing user to
       switch to other virtual consoles.
-a or --all: lock all virtual consoles by preventing other users
       from switching virtual consoles.
-v or --version: Print the version number of vlock and exit.
-h or --help: Print this help message and exit.

```
Next there is bashlock: [https://github.com/acornejo/bashlock](https://github.com/acornejo/bashlock)

bash script to lock the console.

It requires the password of the calling user to unlock the console. This utility is similar in spirit to vlock, the only reason it exists is because vlock was unavailable for OS X.

The main purpose of bashlock is to be used as a lock-server inside tmux. This allows you the user to lock tmux sessions.
Dependencies
[list]
bashlock has very few dependencies, namely:

    [*]bash
    [*]expect
    [*]su[/list]
 

I must say this is a first seeing what you now report.

For me a solution would be a wipe and re-install.

---

### Post by bhubunt on 2024-05-18
Hi, 

Your comments and commands have been incredibly helpful.

To answer your question: "do you recall using any of the two I list below?" 

No.  Never.

I also never launched tty2. As mentioned, I only recently discovered I was logging into a tty2 session and that I had been locked into it since October of last year. 

The unsolved question: how did I end up in a tty2 and why is it locked? 

You are probably right in suggesting *inter alia *that my system is compromised and that I need to reinstall ubuntu. 



> **1fallen said:**
> No not really, but do you recall using any of the two I list below?

vlock: (it is in the repos of most distros),
[LIST]
[*]Virtual Console locking program 
[*]vlock either locks the current terminal (which may be any kind of terminal, local or remote), or locks the entire virtual console system, completely disabling all console access. vlock gives up these locks when either the password of the user who started vlock or the root password is typed. 
[/LIST]
Wolud you remenber using that?
```
 vlock --help
vlock: locks virtual consoles, saving your current session.
Usage: vlock [options]
       Where [options] are any of:
-c or --current: lock only this virtual console, allowing user to
       switch to other virtual consoles.
-a or --all: lock all virtual consoles by preventing other users
       from switching virtual consoles.
-v or --version: Print the version number of vlock and exit.
-h or --help: Print this help message and exit.

```
Next there is bashlock: [https://github.com/acornejo/bashlock](https://github.com/acornejo/bashlock)

bash script to lock the console.

It requires the password of the calling user to unlock the console. This utility is similar in spirit to vlock, the only reason it exists is because vlock was unavailable for OS X.

The main purpose of bashlock is to be used as a lock-server inside tmux. This allows you the user to lock tmux sessions.
Dependencies
[LIST]
[*]bashlock has very few dependencies, namely: 
[*]bash 
[*]expect 
[*]su 
[/LIST]
 

I must say this is a first seeing what you now report.

For me a solution would be a wipe and re-install.

---

### Post by Paddy Landau on 2024-05-18
> **bhubunt said:**
> The unsolved question: how did I end up in a tty2 and why is it locked?
The first part was answered earlier: This has been the default in Ubuntu for some time. By default, you are logged into tty2. Nothing strange about that.

The second part, why is it locked, we still haven't managed to figure out.

Did you try the suggestion by @tea for one, i.e. to [use the Fn key]("https://ubuntuforums.org/showthread.php?t=2497722&page=2&p=14190344&viewfull=1#post14190344") on your laptop?

If you have tried, and it still doesn't work, check if you have vlock or bashlock installed (as per @1fallen's idea):
```
type vlock
type bashlock
```
What we're hoping is that neither is installed.

---

### Post by bhubunt on 2024-05-18
To 1fallen --

unfortunately, while I was reporting here on this forum about tty2, my system was breached again. 

when I typed in the command "last" just now, I noticed that  my entire booting history since Aug 29 2023 (=wtmp) was wiped clean this morning, including the mysterious tty2 log in on October 19 2024 that I never launched. 

This is all that is left now when I type in "last"

```

me-ThinkPad-X240:~$ last

me  tty2         tty2             Sat May 18 11:50   still logged in
reboot   system boot  6.5.0-35-generic Sat May 18 11:50   still running
me  tty2         tty2             Sat May 18 09:35 - 09:57  (00:21)
reboot   system boot  6.5.0-35-generic Sat May 18 09:35 - 09:57  (00:22)
me  tty2         tty2             Sat May 18 07:29 - 09:34  (02:04)
reboot   system boot  6.5.0-35-generic Sat May 18 07:28 - 09:34  (02:06)

wtmp begins Sat May 18 00:00:41 2024  
```

Everything else is gone.

NOTE 

I just marked my thread as "solved," as the issues I have been reporting about on this thread are the result of a system breach. I have had system breaches in the past, about which I am meeting with a lawyer.  Thanks especially to 1fallen for the expert input.  It's appreciated. 


> **bhubunt said:**
> Hi, 

Your comments and commands have been incredibly helpful.

To answer your question: "do you recall using any of the two I list below?" 

No.  Never.

I also never launched tty2. As mentioned, I only recently discovered I was logging into a tty2 session and that I had been locked into it since October of last year. 

The unsolved question: how did I end up in a tty2 and why is it locked? 

You are probably right in suggesting *inter alia *that my system is compromised and that I need to reinstall ubuntu.

---

### Post by Paddy Landau on 2024-05-18
> **bhubunt said:**
> the issues I have been reporting about on this thread are the result of a system breach.
That sucks. I hope that you manage to sort out everything.

Back up your data (and check the backup), then reinstall from scratch using a freshly-downloaded ISO from a non-contaminated computer.

---

### Post by deadflowr on 2024-05-18
Thread closed by the OP's request.

---

