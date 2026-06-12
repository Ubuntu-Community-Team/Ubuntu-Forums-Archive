---
title: "If Ubuntu breaks the 10% market share barrier, should the sudo timeout go away?"
date: 2008-09-21
forum: Recurring Discussions
---

### Post by aysiu on 2008-09-21
Right now, if you run a *sudo* command, you can run as many more *sudo* commands as you want within 15 minutes without another password prompt.

Right now, that seems like an okay balance between security and usability.

But right now, Ubuntu isn't a huge target for malware.

If Ubuntu becomes more popular than Mac OS X (as Mark Shuttleworth is hoping will be the case in a couple of years, though I think his timeframe is overly optimistic), should we change the *sudo* timeout to 0?

What do you think?

---

### Post by SunnyRabbiera on 2008-09-21
Well maybe from 15 minutes to like 5, 5 minutes should be good enough.

---

### Post by cardinals_fan on 2008-09-21
The timeout should go away NOW.  It was a bad idea from the beginning.

---

### Post by SunnyRabbiera on 2008-09-21
> **cardinals_fan said:**
> The timeout should go away NOW.  It was a bad idea from the beginning.

I rather like the idea myself, so that you dont have to type in the password as much.
But lowering the time limit will be beneficial.

---

### Post by cardinals_fan on 2008-09-21
> **SunnyRabbiera said:**
> I rather like the idea myself, so that you dont have to type in the password as much.
But lowering the time limit will be beneficial.
It allows a program to acquire root permissions without user authorization **or notification**.  This isn't an issue when working with the CLI, because the "sudo" before any command informs the user that said command will gain root privileges.  With the GUI, however, there is no notification whatsoever that an app is working as root.

---

### Post by SunnyRabbiera on 2008-09-21
> **cardinals_fan said:**
> It allows a program to acquire root permissions without user authorization **or notification**.  This isn't an issue when working with the CLI, because the "sudo" before any command informs the user that said command will gain root privileges.  With the GUI, however, there is no notification whatsoever that an app is working as root.

well maybe there is a way around that bit, some sort of notifier or something.

---

### Post by Washer on 2008-09-21
Then just add a GUI notification with "OK" and "Cancel." This isn't rocket science.

---

### Post by Bios Element on 2008-09-21
Add a GUI To Configure the limit and leave it at 15 minutes. I don't want to be typing in my Pass every 30 seconds.

---

### Post by Eisenwinter on 2008-09-21
I support the 0s timeout for sudo, and I would support it even if Ubuntu had 0.0000000000001% of the market share.

Security comes first, folks.

I don't mind entering my password each time.

How many SuperUser actions do you do each day anyway?

---

### Post by S0VERE1GN on 2008-09-21
malware is a bigger problem marginally (per user) with linux i think because so many people are more program savvy who use the system.  

timeout at 0.

---

### Post by Npl on 2008-09-21
> **Eisenwinter said:**
> I support the 0s timeout for sudo, and I would support it even if Ubuntu had 0.0000000000001% of the market share.

Security comes first, folks.

I don't mind entering my password each time.

How many SuperUser actions do you do each day anyway?Non per average day, but if I have to mess around with the system then I use alot sudos in a short timespan.

---

### Post by Washer on 2008-09-21
> **Eisenwinter said:**
> How many SuperUser actions do you do each day anyway?

Not the issue. In a month, I probably do 90% of my superuser stuff all inside 1 hour. It's very annoying having to put in the password each time.

---

### Post by cardinals_fan on 2008-09-21
> **Npl said:**
> Non per average day, but if I have to mess around with the system then I use alot sudos in a short timespan.
Then use "sudo -i" for a root prompt.

---

### Post by Dharmachakra on 2008-09-21
> **cardinals_fan said:**
> The timeout should go away NOW.  It was a bad idea from the beginning.

Agreed. It should always be an option... but I wouldn't make it default. It's really not that hard to type "sudo" and a password. There's no reason for there to be a fifteen minute timeout if nearly everyone only runs a handful of root commands a day.

That's just what makes sense to me. But I don't really care too much to make a good argument either way.

---

### Post by jespdj on 2008-09-21
The sudo timeout doesn't have anything to do with the popularity of Ubuntu.

The question sounds as meaningless as "Should I eat a banana if my friend is wearing a blue shirt tomorrow?"

---

### Post by Cannaregio on 2008-09-21
Bring to zero (hence everytime you'll have to re-sudo with password) and of course use instead 
```
sudo -i
``` 
for your occasional admin intensive stuff, since you'r supposed to know what you are doing, then.

So [COLOR="Blue"]if you need to get root[/COLOR] and do lot of root stuff, then really get root and do whatever you have to, no need to retype nothing, on the other hand, [COLOR="#0000ff"]if you don't need to get root[/COLOR], then use your sudo and input your password for that once in a while, rarely used, oddball command.

---

### Post by Washer on 2008-09-21
> **cardinals_fan said:**
> Then use "sudo -i" for a root prompt.
How is that more secure than the timeout? And the real 'problem' here is the GUI timeout.

---

### Post by aysiu on 2008-09-21
> **jespdj said:**
> The sudo timeout doesn't have anything to do with the popularity of Ubuntu.

The question sounds as meaningless as "Should I eat a banana if my friend is wearing a blue shirt tomorrow?"
Of course it has to do with the popularity of Ubuntu. It's not a direct relation, but it's a relation.

If something is popular, it will be a bigger target.

---

### Post by cardinals_fan on 2008-09-21
> **Washer said:**
> How is that more secure than the timeout? And the real 'problem' here is the GUI timeout.
When you use a root prompt you **know** that all commands you run will be run as root.  There are no surprises.

---

### Post by Washer on 2008-09-21
> **aysiu said:**
> Of course it has to do with the popularity of Ubuntu. It's not a direct relation, but it's a relation.

If something is popular, it will be a bigger target.You know many OSX malwares/viruses?

---

### Post by red_team316 on 2008-09-21
[quote=Eisenwinter]
How many SuperUser actions do you do each day anyway?
[/quote]

Make a GUI configuration option for setting the timeout. At _least_ 50% of what I do I require sudo for. I could care less what it is set to by default as long as there is an easy way to change it.

---

### Post by Washer on 2008-09-21
> **cardinals_fan said:**
> When you use a root prompt you **know** that all commands you run will be run as root.  There are no surprises.

Right, because many people input commands that they don't intend to actually run. Your command worked, surprise!

---

### Post by aysiu on 2008-09-21
> **Washer said:**
> You know many OSX malwares/viruses?
Yes. Just do [a Google search for *mac trojan*](http://www.google.com/search?hl=en&q=mac+trojan&btnG=Google+Search).

---

### Post by cardinals_fan on 2008-09-21
> **Washer said:**
> Right, because many people input commands that they don't intend to actually run. Your command worked, surprise!
I don't like the idea of granting any program root privileges without my explicit permission.  Running them from a root prompt is a clear sign that they have my permission.

---

### Post by Mazza558 on 2008-09-21
I propose a more elegant solution:

Step 1. The user opens every program he/she wants root privileges for. He then holds down a key combo and clicks on each window to select it. 
Step 2. The user lets go of the key combo and a gksudo password box appears, along with a warning that anything done with these programs could damage the entire system.
Step 3. The user enters the root password.
Step 4. The selected programs are unlocked until the user presses the key combo again or closes an unlocked program. If neither are done, the timeout is 30 minutes. After 10 minutes of inactivity for root-enabled programs, they start to flash red in the taskbar.

If someone was using a root terminal unlocked by this method, ONLY that terminal would be root, no script or any other program could take control. As soon as the user closes the window, the terminal locks itself. It's only if a bad script was run in that terminal that things could go wrong.

---

### Post by SunnyRabbiera on 2008-09-21
> **Mazza558 said:**
> I propose a more elegant solution:

Step 1. The user opens every program he/she wants root privileges for. He then holds down a key combo and clicks on each window to select it. 
Step 2. The user lets go of the key combo and a gksudo password box appears, along with a warning that anything done with these programs could damage the entire system.
Step 3. The user enters the root password.
Step 4. The selected programs are unlocked until the user presses the key combo again or closes an unlocked program. If neither are done, the timeout is 30 minutes. After 10 minutes of inactivity for root-enabled programs, they start to flash red in the taskbar.

If someone was using a root terminal unlocked by this method, ONLY that terminal would be root, no script or any other program could take control. As soon as the user closes the window, the terminal locks itself. It's only if a bad script was run in that terminal that things could go wrong.

a key combo is a good idea, but it has to be done right and explained greatly with most windows users being mouse dependent.

---

### Post by Half-Left on 2008-09-21
Lets not got Microsoft's way, Ubuntu should learn users to use a password to get to critical parts of the system eveytime, And like us veterans it becomes seemless overtime.

Time outs are a horrid security hole which brings about lazyness and crackers look for them people or OS's that do this. Lock your door sometimes or all the time at night with the key in, only takes one time to exploit this which is how opportunistic they are.

---

### Post by Eisenwinter on 2008-09-21
> **Half-Left said:**
> Lets not got Microsoft's way, Ubuntu should learn users to use a password to get to critical parts of the system eveytime, And like us veterans it becomes seemless overtime.

Time outs are a horrid security hole which brings about lazyness and crackers look for them people or OS's that do this. Lock your door sometimes or all the time at night with the key in, only takes one time to exploit this which is how opportunistic they are.
+1, I agree with that.

---

### Post by Presto123 on 2008-09-21
I vote yes and would feel a little better if it was that way now.

---

### Post by jrusso2 on 2008-09-21
> **aysiu said:**
> Right now, if you run a *sudo* command, you can run as many more *sudo* commands as you want within 15 minutes without another password prompt.

Right now, that seems like an okay balance between security and usability.

But right now, Ubuntu isn't a huge target for malware.

If Ubuntu becomes more popular than Mac OS X (as Mark Shuttleworth is hoping will be the case in a couple of years, though I think his timeframe is overly optimistic), should we change the *sudo* timeout to 0?

What do you think?

15 minutes is fine either way.  Many times I have to do several operations in a row would be a pain to have to do them and enter password each time.

That would encourage me to use root which you all insist is about the worst thing to ever happen .

---

### Post by Washer on 2008-09-21
> **cardinals_fan said:**
> I don't like the idea of granting any program root privileges without my explicit permission.  Running them from a root prompt is a clear sign that they have my permission.

And I'm telling you normal people input CLI commands because they want them to work. If it doesn't work, they'll input the same command again with sudo. Timeout is irrelevant, esp since terminal windows come & go and the problem here is GUI notification.

> **aysiu said:**
> Yes. Just do [a Google search for *mac trojan*](http://www.google.com/search?hl=en&q=mac+trojan&btnG=Google+Search).
But how many of those actually affect people? Many are proof of concepts (or vulnerabilities that wouldn't be affected by timeout). If you ran a computer repair shop, I doubt 1% of your users would be macs, let alone 10%.

It would be like me linking to milw0rm right now.

---

### Post by lswest on 2008-09-21
I think we should bring it down to 10 minutes, and offer a GUI to easily change the timeout for those who are obsessed with security, and allow the user to choose the setting when installing Ubuntu.

Just my $0.02

---

### Post by lswb on 2008-09-21
The sudo timeout is only good for the shell or gui that first used it. If you use sudo in one terminal, then open another terminal and try to run a command requiring root, the password must be entered again. 

So for an intruder to gain root access just because a certain shell or gui had a 15 minute sudo window of opportunity open, they would not only have to login but somehow take over the specific running process with the untimed out sudo authority. If an intruder somehow had that capability, they could just take over ANY running process that had root priveledges. So really, I don't see how the 15 minute sudo time is a security problem.

---

### Post by spupy on 2008-09-21
> **lswest said:**
> I think we should bring it down to 10 minutes, and offer a GUI to easily change the timeout for those who are obsessed with security, and allow the user to choose the setting when installing Ubuntu.

Just my $0.02

+1
When Ubuntu reaches the 10% the user should be needing to type "sudo" no more than once or twice per week! It's not like you tinker with /etc every 20 minutes.

---

### Post by init1 on 2008-09-21
> **Eisenwinter said:**
> I support the 0s timeout for sudo, and I would support it even if Ubuntu had 0.0000000000001% of the market share.

Security comes first, folks.

I don't mind entering my password each time.

How many SuperUser actions do you do each day anyway?
Actually, I use a lot of root commands. But I use su, rather than sudo.

---

### Post by JT9161 on 2008-09-21
Im for a 0 second timeout as soon as possible but I also think it should be easier to change the timeout time. Perhaps an option in Users and Groups that lets you change it individually per user account that defaults to 0.

---

### Post by toupeiro on 2008-09-21
I think a setting of 0 is overkill.

What would be MUCH more effective is for ubuntu to compile sudo with USE_TTY_TICKETS.

This way, you can pass your sudo password in one terminal session, and continue to pass it for fifteen minutes in the session you already authenticated in, but if you open a new one, your authentication is no longer being passed to the new window.  This could prevent a good deal of sudo exploits.  Lower it to five, or even ten minutes if you want, but 0 is brutally painful.  Either way is not full proof, but TTY tickets are better than putting that timer to 0 IMHO.. :-)

---

### Post by MasterNetra on 2008-09-21
I gots a better idea folks. Why don't we add options at a admin lvl that allows you to set the timelimit and any root usage limits *(ex. 2 uses only for the the duration and after the max has been used it would force kill the duration.)*. Also wither or not you want to use usage limit, time limit, or both. Default could be Timelimit only of 5 mins but at least with options you can make it as secure as you want it to be. A option to enable the combo key could be place but not on by default :) This Ubuntu it should be as options not a forced setting :)

---

### Post by toupeiro on 2008-09-21
I double-checked and it appears you are already compiling with TTY Tickets.  Many sudo exploits would fail in linux because of this.  All my GUI CLI's spawn new PTS# sessions when they are launched.  Gui apps are processes that sit at my point of entry on a system.  In most desktop cases, thats the local console, but even remotely with SSH, if I am redirecting X-windows, everything I launch on X-windows runs at my entry point session port, except newly launched Shells which grab new PTS sessions, and would require a new TTY ticket to do anything with Sudo.

Thats pretty damn secure.  Can it be more secure?  Sure.  You can set that timer to 0, but then you have to ask yourself, how much functionality do I want to sacrifice for the marginal space there is to exploit the system in the manner you are outlining?

---

### Post by qazwsx on 2008-09-21
No kdesudo or gksudo anymore! kdesu works better. Sudo timeout  is disaster in GUI.

For CLI  15-30 seconds.

Also separate passwords.

---

### Post by MasterNetra on 2008-09-21
I agree on that. Sudo password should be separate from the administrator's pass.

---

### Post by toupeiro on 2008-09-21
Final thought:  Why don't you put it in the hands of the users?


You can control the timeout with:
timestamp_timeout=#

in the /etc/sudoers file.

You must be controlling the timeout in compiling, because I don't think the default time as you get it in the source is 15 minutes, and there is nothing but defaults set in the sudoers file.  I think default is traditionally more like 1 minute if I remember correctly from the last time I compiled Sudo, but that was a few years ago now.

It may be nice to ask this question in some sort of a user friendly way during installation. and give some radio buttons which pass a different timeout in the sudoers file based on how hardened the user needs the system to be, but for the sake of security, don't give them the option to make it LESS secure than you've already defined it in current and previous ubuntu versions.

Edit:
Be very careful blanketing security like this as default for ALL USERS.

> **jrusso2 said:**
> 
**_Many times I have to do several operations in a row would be a pain to have to do them and enter password each time..  That would encourage me to use root which you all insist is about the worst thing to ever happen ._**

---

### Post by niko7865 on 2008-09-21
I think it should be 0 or have some kind of notification for GUI applications, but I think the command line sudo should still have a 5 minute timeout.

---

### Post by lswb on 2008-09-21
Can one of the posters who is concerned about the sudo password timeout give an example of how it presents a security risk? I don't think so. If an intruder can gain control of a running process whether a shell or a gui, then the issue of a sudo timeout is irrelevant.

---

### Post by corney91 on 2008-09-21
> **red_team316 said:**
> Make a GUI configuration option for setting the timeout.
I would've thought that was the obvious option.

The timeout is handy in particular for running sudo apt-get update, then sudo apt-get upgrade ;)

---

### Post by god0fgod on 2008-09-21
I changed the timeout to 0 but it was wierd. "sudo visudo" made no sense whatsoever.

---

### Post by MasterNetra on 2008-09-21
> **toupeiro said:**
> Final thought:  Why don't you put it in the hands of the users?


You can control the timeout with:
timestamp_timeout=#

in the /etc/sudoers file.

You must be controlling the timeout in compiling, because I don't think the default time as you get it in the source is 15 minutes, and there is nothing but defaults set in the sudoers file.  I think default is traditionally more like 1 minute if I remember correctly from the last time I compiled Sudo, but that was a few years ago now.

It may be nice to ask this question in some sort of a user friendly way during installation. and give some radio buttons which pass a different timeout in the sudoers file based on how hardened the user needs the system to be, but for the sake of security, don't give them the option to make it LESS secure than you've already defined it in current and previous ubuntu versions.

Edit:
Be very careful blanketing security like this as default for ALL USERS.

Thats basically what i have been saying! Only I was also going for a GUI option as well for administrators.

---

### Post by aaaantoine on 2008-09-21
I posted my thoughts on this issue at some point in the past year.  Sudo timeout should be at the user's discretion (along with being configurable in the GUI), and if the timeout is anything more than immediate, there should be an option available to the user to stop admin privileges before the timeout is reached.

The latter feature was supposed to be in Gutsy.  I don't know what happened to it.

---

### Post by cardinals_fan on 2008-09-21
> **Washer said:**
> And I'm telling you normal people input CLI commands because they want them to work. If it doesn't work, they'll input the same command again with sudo. Timeout is irrelevant, esp since terminal windows come & go and the problem here is GUI notification.

The problem isn't with the CLI.  The timeout is an issue when an app launches with "gksudo" and the timeout is in effect - no warning and no notification.
> **qazwsx said:**
> No kdesudo or gksudo anymore! kdesu works better. Sudo timeout  is disaster in GUI.

For CLI  15-30 seconds.

Also separate passwords.
+1
> **lswb said:**
> Can one of the posters who is concerned about the sudo password timeout give an example of how it presents a security risk? I don't think so. If an intruder can gain control of a running process whether a shell or a gui, then the issue of a sudo timeout is irrelevant.
Simple.  If you run a malicious script as a normal user, it normally wouldn't do too much harm.  If, however, it executes "gksudo *insert nastiness here*" while the timeout is running, it can do whatever it likes - and you have no idea.

I think that Fedora has the right idea.  The box requesting the root password (I don't remember what app it is) offers a checkbox for "save authorization".  If you save it, an icon appears in the system tray that lets you disable the authorization.

---

### Post by MaxIBoy on 2008-09-21
I say turn it off if you don't run anything as root for thirty seconds. So you could keep it up all day if you wanted, if you were running something as root more often than every thirty seconds.


Then, allow people to configure it to suit their tastes. I would want better security on my laptop than on my desktop, for example.



On the other hand, doesn't it turn the root access off if you close the terminal emulator?

---

### Post by MasterNetra on 2008-09-21
> **MaxIBoy said:**
> I say turn it off if you don't run anything as root for thirty seconds. So you could keep it up all day if you wanted, if you were running something as root more often than every thirty seconds.


Then, allow people to configure it to suit their tastes. I would want better security on my laptop than on my desktop, for example.



On the other hand, doesn't it turn the root access off if you close the terminal emulator?

No. You would have to wait for the time to expire.
before it turns off. At least thats been the case for me anyway.

---

### Post by gn2 on 2008-09-21
> **cardinals_fan said:**
>  With the GUI, however, there is no notification whatsoever that an app is working as root.

If you have Thunar installed try Alt+F2 then ```
gksudo thunar
``` and you'll see this:

[IMG]http://thunar.xfce.org/images/thunar-root-warning-rc1.png[/IMG]

Surely other apps can be made to do this.

---

### Post by Joeb454 on 2008-09-21
I'm sure it wouldn't be too much of an issue to add this in.

I think it should be made to around 5 minutes if Ubuntu becomes that popular

---

### Post by p_quarles on 2008-09-21
> **toupeiro said:**
> You must be controlling the timeout in compiling, because I don't think the default time as you get it in the source is 15 minutes, and there is nothing but defaults set in the sudoers file.  I think default is traditionally more like 1 minute if I remember correctly from the last time I compiled Sudo, but that was a few years ago now.
15 minutes is the default listed in the sudo man page. As far as I can tell, the page (in my Debian installation) was not modified from the one distributed with the source. 

> **aaaantoine said:**
> I posted my thoughts on this issue at some point in the past year.  Sudo timeout should be at the user's discretion (along with being configurable in the GUI), and if the timeout is anything more than immediate, there should be an option available to the user to stop admin privileges before the timeout is reached.
I have to agree -- these kinds of settings should have some easier tools available for configuration. /etc/sudoers isn't difficult, but it's not intuitive either.

---

### Post by cardinals_fan on 2008-09-21
> **gn2 said:**
> 
Surely other apps can be made to do this.
PCManFM does.  However, I'm more worried about malicious apps, which certainly won't tell you their true intent.

---

### Post by danbuter on 2008-09-21
Is there a way to make sure Canonical sees this thread? Because I know I'd like the time cut down, at the very least. Or if a gui was made to let me set the time how I want it would also be great.

---

### Post by JT9161 on 2008-09-21
> **danbuter said:**
> Is there a way to make sure Canonical sees this thread? Because I know I'd like the time cut down, at the very least. Or if a gui was made to let me set the time how I want it would also be great.

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) 

Threads like this are the whole point of Brainstorm right ?

---

### Post by lswb on 2008-09-21
I have to say that I've changed my mind on this issue, I now believe it is a valid security issue. First off I was not considering a that a user would run a malicious script or command but that is surely something to think about.

But after playing around with sudo and multiple terminal windows opened, I'm even more concerned because sudo is not behaving as I thought it would and even not behaving as I believe its man page states. I thought for sure after past experiments that a new terminal window where sudo was run would require reauthentication. I see now that that is not the case.

Even more disturbing, the "sudo -k" and "sudo -K" commands, which are supposed to reset or remove the timestamp and thus require a password to be entered on the next sudo invocation, do not seem to work consistently either. I would think that if a user had 2 terminal windows opened and had used sudo in both of them, then issuing the "sudo -K" command would surely make the next invocation of sudo require a password, regardless of which terminal window or vt it was issed in. But that doesn't happen! I wonder if this is a bug or I'm missing something in the documentation.

---

### Post by jrusso2 on 2008-09-21
> **gn2 said:**
> If you have Thunar installed try Alt+F2 then ```
gksudo thunar
``` and you'll see this:

[IMG]http://thunar.xfce.org/images/thunar-root-warning-rc1.png[/IMG]

Surely other apps can be made to do this.

I hope I am dead before this level of hand holding takes effect :(

---

### Post by Mr. Picklesworth on 2008-09-21
TTY tickets do help this problem quite a bit. However, it would be better if different shells (eg: the user's session) had different timeouts. There is also the possibility that a process could enter "sudo do something evil" in a terminal possessing root privileges via some unprivileged commands.

jrusso2: I do not understand. Are you afraid that a computer being informative makes you look weak?

The fact is, GUI applications should not be run as root. That there is an incredible ammount of exploitable code bouncing around where really all you need to do is copy and rename files. That is why PolicyKit is going to be very important.

It would be nice if that program privilege information was presented by something external to it, which permits consistency and accountability. Perhaps a system could display a little bar above a program's windows (or at top of screen otherwise) when a program is running as a different user than expected, or when there are PolicyKit things to know about like the program wanting to be "unlocked".

Prompt or not, Sudo is currently not the best security tool just from a UI standpoint. What we need is for the program being elevated to root (or sudo itself in other cases) to explain what it will do. For example, the rm and mv commands could specify plainly what files they will modify. While "mv -rf * /dev/null" doesn't mean much to the untrained eye, the sudo prompt may say "move all system files to /dev/null without hesitation". That would probably scare the heck out of anyone causing them to cancel, and "all system files" could be quite easily determined from the context.
This still leaves us with unsafe *binaries* ending up on the disk that can do their evil without the shell commands, but they still need root privileges and "it is unknown what this application will do" also does not look very safe.
(Would be good if the functionality was external from sudo, instead done by something along the lines of "explaincommand").

I think "cancel or allow" is a necessary evil, just so long as the prompt does something useful and has a "stop asking me, I think I'm an expert" button. Maybe the verbosity of sudo prompts could be based on the process launching them, where the user can at some point say "I trust this application completely" and have that choice remembered forever.

---

### Post by solitaire on 2008-09-21
I think the timeout should be reduced to 5 mins, 

Also a notification icon could be displayed when the root password is still in effect. When clicked, the user has the option to either "set the default timeout" or an option to drop the password.

---

### Post by toupeiro on 2008-09-21
> **p_quarles said:**
> 15 minutes is the default listed in the sudo man page. As far as I can tell, the page (in my Debian installation) was not modified from the one distributed with the source. 



Thats strange.  I'm 99.9% sure I didn't modify that in the source.  I downloaded my source from the group that maintains sudo ([http://www.courtesan.com/sudo/](http://www.courtesan.com/sudo/))  It was a 1.6.9 version, but I can't honestly remember the patch level, and I compiled it for Solaris 8, 9, and x64 Linux but that shouldn't really make a difference.  Anyhow, I deployed it across over 100 systems and I am 100% positive I don't cache the credential for 15 minutes.  Anyhow, I still stand behind 0 = counterproductive, and not really buying you enough security to warrant the cumbersome experience and bad alternative practices it will promote.

Without TTY tickets, I would say 15 minutes is excessive, but because you are using them (and these are also not enabled by default), then I think as devs you are providing ample security while allowing sudo usage to not be cumbersome and counterproductive.  I don't think lowering this to say 5 minutes would be too much of an impact.  0 minutes, thats definitely overkill IMO.  The first thing I'd likely do in future releases of ubuntu is modify my sudoers file to override that.  For people who don't know how to do that, they will just become root...  People want secure, but most of them want easy and non-disruptive more, whether they tell you that or not. :-P  If you've had to support users, you probably already know this.  There is a fine line between security and usability, and everyone usually has a different place they like to stand.  The added pressure on ubuntu devs is that they need to think of what others want in an OS more than what they want at times...  Might be an idea for the server OS though.. 

Sudo is a powerful administrative tool, with a lot of options that people who are concerned about security should familiarize themselves with anyway.  It would be nice to see a good graphical frontend admin tool written to administer a sudoers file, for those who think visudo is a little too faint of heart.  Its a key part to what makes ubuntu both usable and secure.  To me, that means its important to broaden the awareness of how to configure it.

---

### Post by danbuter on 2008-09-21
[http://brainstorm.ubuntu.com/idea/13526/](http://brainstorm.ubuntu.com/idea/13526/)

Added to brainstorm, for those who want to vote for a way to adjust timeout.

---

### Post by phrostbyte on 2008-09-21
> **cardinals_fan said:**
> The timeout should go away NOW.  It was a bad idea from the beginning.

Can you please explain how a program can gain root privileges from the timeout? UNIX (and Ubuntu) uses a tree process model.

---

### Post by danbuter on 2008-09-21
I'd be more worried if you are in an office environment. Do something with sudo, leave to get a coffee, and come back and someone did something nasty to your computer. Not that this would ever happen in a corporate office or anything...

---

### Post by phrostbyte on 2008-09-21
Can you people explain how having a sudo timeout would facilitate malware?!

I mean guys learn a little bit more about the POSIX process model before you guys say such silly things. The sudo timeout in process specific, and it not applied system wide. It only applies to the parent of the process executed via sudo. I just don't see this being a major malware hole, even if the timeout was indefinite (never time out).

---

### Post by cardinals_fan on 2008-09-21
> **phrostbyte said:**
> Can you please explain how a program can gain root privileges from the timeout? UNIX (and Ubuntu) uses a tree process model.
Let's say you open up Synaptic Package Manager (on Ubuntu) through the GNOME menu system.  It'll offer you a gksudo prompt, in which you enter your password.  5 minutes later, you execute a malicious script (not worrying too much, because you're only using a limited account).  If said script prepends "gksudo" to its destructive commands, you're screwed, and you don't even know.

The timeout isn't a problem at the CLI level.  However, using gksudo provides a dangerous layer of opacity in what should be transparent privilege escalation.

---

### Post by Moustacha on 2008-09-21
Should be made shorter for default, but configurable for advanced users (which it no doubt is)

---

### Post by phrostbyte on 2008-09-21
> **cardinals_fan said:**
> Let's say you open up Synaptic Package Manager (on Ubuntu) through the GNOME menu system.  It'll offer you a gksudo prompt, in which you enter your password.  5 minutes later, you execute a malicious script (not worrying too much, because you're only using a limited account).  If said script prepends "gksudo" to its destructive commands, you're screwed, and you don't even know.

The timeout isn't a problem at the CLI level.  However, using gksudo provides a dangerous layer of opacity in what should be transparent privilege escalation.

Fair enough.

---

### Post by phrostbyte on 2008-09-21
Lets look at this from a different perspective, if people are using Ubuntu systems as single user systems, is the user/root style security really sufficient? I mean you can completely wreck a persons computer without root access. You have full access to their home directory and session files. That's a HUGE, maybe the most important part of the user's system, all the documents and settings will be gone. With root all they tend to lose in addition is their package manifest which is a joke to rebuild thanks to apt anyway.

---

### Post by p_quarles on 2008-09-21
> **phrostbyte said:**
> Lets look at this from a different perspective, if people are using Ubuntu systems as single user systems, is the user/root style security really sufficient? I mean you can completely wreck a persons computer without root access. You have full access to their home directory and session files. That's a HUGE, maybe the most important part of the user's system, all the documents and settings will be gone. With root all they tend to lose in addition is their package manifest which is a joke to rebuild thanks to apt anyway.
The concern with malicious root access isn't that they'll destroy all of your documents, but that the malware can silently run a proxy server on your computer. The biggest business in the black hat world right now is, after all, the botnets. This kind of malicious usage doesn't want to alert you to its presence (by, say, erasing ~), it wants to be able to continue using your computer. Even an experienced user isn't likely to detect a well-made rootkit unless they are actively looking for it. 

But, yeah, I agree that people are overly confident in the idea that privilege separation protects them from all security threats.

---

### Post by phrostbyte on 2008-09-21
> **p_quarles said:**
> The concern with malicious root access isn't that they'll destroy all of your documents, but that the malware can silently run a proxy server on your computer. The biggest business in the black hat world right now is, after all, the botnets. This kind of malicious usage doesn't want to alert you to its presence (by, say, erasing ~), it wants to be able to continue using your computer. Even an experienced user isn't likely to detect a well-made rootkit unless they are actively looking for it. 

But, yeah, I agree that people are overly confident in the idea that privilege separation protects them from all security threats.

Botnet software (like for spamming etc.) can easily run in usermode. All it needs is some temporary storage and socket access - this is all provided by user mode. So root access is meaningless in this situation. 

Really Ubuntu's security model is fundamentally flawed. Two pretty much meaningless security levels (root, user), is garbage. It made some sense in the UNIX mainframe era but not anymore.. we are one user per machine, so this type of separation is almost like having no security.. and changing the timeout of sudo isn't going to have much an effect on malware. The whole premises behind this "sudo" security model is flawed. If we want real security in Ubuntu we are going to have to look into mandatory access control and per package default security profiles applied to all frequently used programs. 

Of course this is a lot harder then changing a line in sudoers, but it's what will need to be done eventually. It looks like Canonical/Ubuntu is moving in this direction anyway with the inclusion of AppArmor, but right now it's insufficient as programs like Firefox has free reign over user space.

---

### Post by p_quarles on 2008-09-22
> **phrostbyte said:**
> Botnet software (like for spamming etc.) can easily run in usermode. All it needs is some temporary storage and socket access - this is all provided by user mode. So root access is meaningless in this situation. 
The first two sentences are true, and the last is false. The difference (and it is a meaningful one) is that a bot running in usermode is not able to replace /bin/netstat with a version that will conveniently ignore or misrepresent the malware. For instance. 

I am completely willing to grant that the security measures built into a standard-issue Linux distro are relatively weak and could be circumvented in ways that could do a deal of damage. To draw from this fact the notion that protection of root privileges is no security at all is where I can't agree. So long as root is not compromised, it is difficult to seamlessly obfuscate the attack.

Of course, if someone has compromised a user space that has sudo privileges, the whole discussion is kind of moot. That machine has already been rooted.

---

### Post by toupeiro on 2008-09-22
A few things to clear up:

1) It seems to me that gksudo is less secure than standard sudo the way it interacts with Gnome.  gksudo should be made to be PID oriented, being that commands can be executed at the same TTY session X-windows is running from, which is not what happens when you open CLI windows to run commands.  Either that, or find some way to have gksudo processes launched in seperate session space to leverage TTY tickets and at least make it AS secure as CLI sudo.

2)  No, its not that people are overly confident that they are protected from ALL security threats.  But I am confident that people are protected from a good majority of security threats without having to understand a whole lot about security right off the bat, which is not as much the case with other Operating Systems.  The rest of those threats are usually addressed in the quick turnaround of open source patching and release management through synaptic.  Those measures are furthered even more by raising awareness to end users about safe computing practices.  There has to be a hand-off point from what security you provide, and how secure the user is in his or her usage.  The OS cannot be responsible for irresponsible users who allow themselves to be socially engineered or completely choose to neglect common security practices.  Security needs to be kept more in the scope of, how do I protect a system , within what is reasonable, with average users from exploitation, and not how do I make this system prevent someone from EVER doing something outside of what is reasonable that could expose the system to a threat.  How do you determine whats reasonable?  It takes intellect, common sense, good judgment, and prudence.  Things computers were never intended to provide, but to be handled with by its operator.  What do you get when you try to focus on the latter of these two scopes?  Windows Vista.  I don't mean to say that to spite Windows or Microsoft, but seriously think about the security model that was implemented in Vista, and decide for yourself if I am on target or not...

3)  Sorry, Windows users are one user per machine, but go find someone with an XP machine who makes his account a USER account and not an ADMIN account, and set a timer up and see how long before their entire system is compromised compared to someone who has not separated User/Admin account roles.  Linux server systems are still MANY users to one machines,  Client Access Licenses (CAL's) are not applicable here, so there is still a hell of a lot of relevance, especially if you happen to be running sshd, or rsh, or telnet on your desktop.

Frankly, you can create service accounts in Linux, and have sudo execute things as accounts other than root if you so choose to configure it that way, so the whole argument of user/root only is a little uninformed in regards to what you CAN do.  Its just not whats being done because quite frankly, user/root security levels, while admittedly simplistic, are pretty damned effective, and have been for decades.  Need more? then implement SELinux, or something along those lines, but don't assume everyone needs to have that level of security by default!!!  Thats like trying to tailor suit a public domain OS for Sarbanes Oxley compliance apon installation which is ludicrous if its not necessary.  Give me the means and the information to, and make it insanely easy to do, but trying to protect users from themselves teaches them nothing, and greatly impacts everyone who doesn't need protection from themselves.  

If you follow the logic of letting the OS dictate secure usage to a user, the vista approach, you really aren't teaching or helping the user... You're really not increasing security, you're just ensuring the problem is not *your* problem anymore.  That may be a great thing in the form of a statistic to put on paper, but  in reality I think its pretty meaningless if you didn't fix the real security problem.

I don't think I can make my point any clearer on this so this will be my last soapbox session on this topic,  :) I just hope anyone reading that that has influence into a decision like this for ubuntu considers what points I've been trying to make before making that decision.  Providing security for users is always a great intention of an administrator or developer, but ultimately I think some of the measures mentioned in this thread would be counterproductive to the goal I believe you are truly trying to accomplish.

Cheers!
-T

---

### Post by eentonig on 2008-09-22
I voted to lower the timeout value, but actually wouldn't mind if they removed it all together. 

As the regular John Doe, I almost never need to run sudo, so it wouldn't inflict me any in way. As a techie Jane Doe, I happen to run lots of sudo commands, in which case I get annoyed by having to prepend that bloody 'sudo' countless times, so I usually issue a 'sudo -i' pretty soon anyway.

My point is:

- Average pc users will hardly ever need to use '(gk)sudo'.
- If they need (and know why) to run it, they wont be needing a lot of commando's. Mostly it will be limited to regular stuff like installing an extra application, changing resolution, install a printer, ... So they will at a max need to use one or two 'sudo' permissions. No problem if I'm asked to answer my password that many times I guess.
- The longer you have your timeout, the more likely they issue a harmfull command without fully being aware.
- You also create a bigger window of opportunity for bad people to attack.

---

### Post by hessiess on 2008-09-22
no, because the chance of ubuntu braking the 10% market barrier within 2 years is practically 0.

Ubuntu isn't even advertised on the TV, its spreeing almost entirely through word of mouth. Also there are very few company's that sell pre-installed systems with ubuntu, even DELL cannot be bothered to advertise there ubuntu systems. 

I have sean tv adds for apple computers, and even now thay still have only a small proportion of the market share.

---

### Post by tribaal on 2008-09-22
> Ubuntu isn't even advertised on the TV

Please show me a Google TV ad :) 
Tip: They don't exist, and Google doesn't have a marketshare problem.

:)

- Trib'

---

### Post by hessiess on 2008-09-22
> **tribaal said:**
> Please show me a Google TV ad :) 
Tip: They don't exist, and Google doesn't have a marketshare problem.

:)

- Trib'

origonaly goggle was just a search engine, every internet user knows what a search engine is, you type something in, it retunes results, simple.

Ubuntu is a operating system, most computer users don't even know what an OS is, leat alown how to install/configure one ;) ubuntu won't gain general market share until there are preinstslled systems in high-street shops.

---

### Post by billgoldberg on 2008-09-22
> **aysiu said:**
> Right now, if you run a *sudo* command, you can run as many more *sudo* commands as you want within 15 minutes without another password prompt.

Right now, that seems like an okay balance between security and usability.

But right now, Ubuntu isn't a huge target for malware.

If Ubuntu becomes more popular than Mac OS X (as Mark Shuttleworth is hoping will be the case in a couple of years, though I think his timeframe is overly optimistic), should we change the *sudo* timeout to 0?

What do you think?

I think it should be 0 right now.

I have no problem typing in my password every time. It's not like I need sudo every 5 minutes.

---

### Post by Warpnow on 2008-09-22
Irrelevent.

If the password timer gets reduced to zero then ubuntu has ZERO chance of breaking 10%.

I know several people who I showed linux whose main gripe was entering the password.

People don't care that much about security as the average person doesn't have anything worth hiding.

---

### Post by billgoldberg on 2008-09-22
> **Warpnow said:**
> Irrelevent.

If the password timer gets reduced to zero then ubuntu has ZERO chance of breaking 10%.

I know several people who I showed linux whose main gripe was entering the password.

People don't care that much about security as the average person doesn't have anything worth hiding.

Just because people don't care about security doesn't allow for an insecure OS.

It find the 15 min thing already pretty unsafe. If Ubuntu were to become mainstream, it would be even more dangerous.

---

### Post by danbuter on 2008-09-22
I agree with billgoldberg on this. Why have the default security be "iffy" when there is a (probably) easy fix that can be done. Just because the average guy doesnt' even install an anti-virus on his machine doesn't mean Ubuntu shouldn't worry about security. If nothing else, having better security is a selling point for those who have half a clue.

---

### Post by uberdonkey5 on 2008-09-22
> **spupy said:**
> +1
When Ubuntu reaches the 10% the user should be needing to type "sudo" no more than once or twice per week! It's not like you tinker with /etc every 20 minutes.

I think if it does capture 10% or more of the market it is likely that the majority of these users won't want to (and won't be able to) use the terminal. Ubuntu is popular because you can do so much without the terminal (whilst still having the option).

I think the biggest security threat in the future will actually be for newbies where they are encouraged to type 'rm' commands or commands which ruin their system. Its easy to do, doesn't require penetration of someones system, and can get around any password.

P.S. I do more damage to the system myself, than viruses have ever done!

---

### Post by oedipuss on 2008-09-22
Isn't PolicyKit exactly the solution to this ? 
As far as I can tell, launching even administrative applications (like the network manager in Hardy) in a locked mode and then unlocking specific parts it if and only if you need write access, eliminates the need of a timeout entirely. 
I'd love a similar way to run synaptic.. Often I'm launching it only to search for a package or to check its dependencies with no intention of installing it. There's no actual need for a password prompt for that.
So I'd say fix every default app in intrepid +n to use policykit, and set the timeout to 0, since it won't be needed anymore except for non-default apps.

As for the CLI, a little notification of some kind would be nice if it's not too annoying, mostly to prevent accidents, not as a security enhancement. Perhaps a third prompt symbol thingie, like $ and # are for user and admin ?

---

### Post by swoll1980 on 2008-09-22
I think 15 minutes is to long as it is. A lot can happen in 15 minutes.

---

### Post by Tom--d on 2008-09-22
I think it should be 0. 

I mean, who logs in Superuser mode everyday?
If I do, I normally log in by sudo bash. Then I have all the fun I want >.>

---

### Post by zekopeko on 2008-09-22
didn't read the whole thread but here's my 2 cents:

Copy Fedora. When you go all superuser, a nice looking shield icon pops up in the notification area. clicking on it it offers an option to stop sudo.
well actually i don't think it's sudo at all. it's policykit for the most part. nice thing with PK is that you can fine-grain what each user can do with each app (the app has to support PK for maximum effect).

Another thing that you can do is enable AppArmor or SElinux. i think that ubuntu goes with AppArmor but not by default. essential you are telling the app what it can and can't do. 
Lets say totem wants to write to a system file like fstab. AppArmor tell's it no can do totem since you have no right doing something like editing fstab. stick to your movies and music.
the problem is that you have to configure each app so that it can do what it's meant to do (only the functions it was writen for) and that requires some testing. ubuntu devs should enable apparmor by default in the development phase for a couple of release so that we (the users) can generate bug/configurations for apparmor. 
once we have apparmor config files we can enable them for the default set of apps with minimal fuss and maximum security to the end user.

---

### Post by Canis familiaris on 2008-09-22
> **SunnyRabbiera said:**
> well maybe there is a way around that bit, some sort of notifier or something.

+1 Not a poassword prompt during the timeout period but only a notifier would do...

---

### Post by lukjad on 2008-09-22
I voted that it stay the same, just because you can change it at anytime by the user, and any shorter would make people annoyed and then they would try and remove it.

---

### Post by Vadi on 2008-09-22
I don't quite get the liberties people are taking to discuss on how to make other people lives harder.

If those people would like to do that, they're certainly welcome to themselves.

---

### Post by Patrick793 on 2008-09-22
Personally, I think that in the Administration section of System, we should be able to choose what we want the timeout to be. If that's not possible, I would like the timeout to be 0, if not 5.

---

### Post by John164918a on 2008-09-22
Why cant there just be an su command and you have to log out when you are finished, and then maybe have some really annoying flashing titlebar as the default, to make you feel as though your doing something dangerous. I say that because I sometimes do sudo nautilus just for the easier interface.

Or there could be a command which forces the sudo command to timeout, where you would type the command to stop the titlebar flashing.

Would kind of fail though on my computer because I would turn it off. I would have to experiment before deciding on a timeout.

---

### Post by ukripper on 2008-09-22
Yes the timeout should be 0 in the first place. Can be a major security flaw if used my vicious program or person.

People who want infinite limit should use sudo su on your own risk.

---

### Post by solitaire on 2008-09-22
Thought we were trying to get AWAY from being Windows?

On the one hand we have people who want a 0 time limit (In Vista it feels like you have to enter in the password every time you click on something!). 

All they way to a very long limit. (In XP where the first user is by default a member of the admin group and has all the rights without needing to enter a password).

We have to strike a balance between ease of use and security. The whole reason *Nix systems were more secure was due to the separation of Users and Admin.

You'll get ot the sutuation where no matter which is implimented people will start to log in as ROOT! either by default (i.e. Long time limit for passwords) or; Can't be bothered to enter in the password all the time easier to log in as ROOT to work!

You've got to remember that these are just simple uers. These are people of the land. The common clay of the new West. You know... morons. (Gotta love Balzing Saddles quotes!:D) 

@Warpnow it's not what the user wishes to hide it's what the attacker wants to do. If an attacker gets access they are more likely to use the system to use it as a proxy to D/L VERY Illegal stuff, letting the poor user to face the music if the police ever knock on their door.

---

### Post by Vadi on 2008-09-22
Indeed. One of the major annoyanced in Vista is having to put in your password *every* time.

But, some people don't care to learn from others.

---

### Post by oedipuss on 2008-09-22
About gksudo/gksu, how different is a 0 sec timeout in practice, even if we ignore future uses of policykit?

You launch one application, enter your password, and proceed to use it. Admin rights remain active until you close it. How often do you seriously need to launch many administrative applications so that entering the password multiple times becomes a problem ? Unless you've just installed your system and need to configure it (which is a one time only thing), I can't think of any other cases where you would *regularly* need to open more than two admin rights applications inside 15 minutes. 
This isn't like vista.

As for the CLI, the simple and usable solution is to do a sudo -i instead of using sudo with every command, as was already mentioned. Or use a different terminal launcher set up to launch as root, and use that when you need it. No annoyance there either.

---

### Post by Mr. Picklesworth on 2008-09-22
PolicyKit is definitely the *eventual* answer to all of this. I don't see how the password prompts make us like Windows, though.

Windows Vista's password prompts are annoying because they happen *constantly*, even for harmless tasks. The problem with it is that Windows was never designed around limited users. For example, setting the time actually adjusts the system clock, which of course needs admin rights.
(In Ubuntu and any other sane Linux distro, setting the time just sets an offset and keeps the system clock the same; thus no admin rights necessary and no other users are affected).
Try dragging some content out of Internet Explorer. A UAC prompt appears because IE uses a sandbox... and apparently that means you can't copy / paste basic content.

On our end, the gksu popups are very rare, and only happen when applications are going to do something really significant, because most preferences happen just for the current user.
(Speaking of which, we need a "make this program executable?" popup).

Ideally we have PolicyKit so those popups are even less frequent, at which point gksu can be made super secure but its presence will be far less. PolicyKit still theoretically demands password entering / cancel or allow, but it is designed to be a bit 'smarter', such that the user can be made aware of programs taking unusual privileges. PolicyKit does not give access to everything at once, so it is possible to get an accurate picture of *what* the program is doing.

I didn't realize Fedora had such a deep design for security. I should play more with that distro!

---

### Post by danbuter on 2008-09-22
> **Vadi said:**
> Indeed. One of the major annoyanced in Vista is having to put in your password *every* time.

But, some people don't care to learn from others.

That's why I'd like a gui to set sudo timeout to where you want it. Some people can then leave sudo going for 15 minutes, and others can set it at 0 if they want. Then everyone's happy.

---

### Post by Trail on 2008-09-22
Eh well, I voted for it to stay the same, but I usually disable it (sudoers - NOPASSWORD) on machines where I use Konsole a lot.

---

### Post by bobbocanfly on 2008-09-22
> **Patrick793 said:**
> Personally, I think that in the Administration section of System, we should be able to choose what we want the timeout to be. If that's not possible, I would like the timeout to be 0, if not 5.

Yes! Makes the most sense to let users configure it. Set it to a sensible default (5 minutes makes sense to me, not too short and not too long) and document the advantages and disadvantages of this in the Ubuntu Wiki.

If there is enough interest I'll try to write up a spec for a gui sudo timeout tool soonish.

Edit: Second thoughts, this would be a tiny app, so makes more sense to fit into another tool...suggestions welcome as I am seriously thinking of trying to get something like this into Jaunty.

---

### Post by Vadi on 2008-09-22
This is probably fit for the 'Ubuntu Tweak' program. (unlike third-party repositories that it adds...)

---

### Post by Polygon on 2008-09-22
the reason people hate the vista prompt is that it asks for your password for the stupidest things, like copying icons to the desktop, and other stupid simple things

sudo is only needed really for installing/updating software. So having a 0 minute timeout isnt that bad

---

### Post by toupeiro on 2008-09-22
> **Polygon said:**
> the reason people hate the vista prompt is that it asks for your password for the stupidest things, like copying icons to the desktop, and other stupid simple things

sudo is only needed really for installing/updating software. So having a 0 minute timeout isnt that bad


Which is exactly why you should have the option of setting it to zero, and exactly why it should not be zero for the entire world of ubuntu users.  Because, not everyone needs to be protected from themselves, and not everyone just uses it with apt-get.

---

### Post by phrostbyte on 2008-09-22
> **p_quarles said:**
> The first two sentences are true, and the last is false. The difference (and it is a meaningful one) is that a bot running in usermode is not able to replace /bin/netstat with a version that will conveniently ignore or misrepresent the malware. For instance. 

I am completely willing to grant that the security measures built into a standard-issue Linux distro are relatively weak and could be circumvented in ways that could do a deal of damage. To draw from this fact the notion that protection of root privileges is no security at all is where I can't agree. So long as root is not compromised, it is difficult to seamlessly obfuscate the attack.

Of course, if someone has compromised a user space that has sudo privileges, the whole discussion is kind of moot. That machine has already been rooted.

You have a point but it's not so relevent to the average user. How many people even know about netstat and even how to intrepid it's output? To someone not computer literate there is no difference between root and user protections .. they'll never know their machine was compromised either way. And even with this in mind it's really really unlikely some malware will go out of it's way to get root access when it doesn't need to get root access to be effective in the long run. Malware writers will go for the path of least resistance and there is VERY LITTLE resistance to running nasties in user space.

To me this thread is like trying to attack the problem of bad security the completely wrong way. Like trying to put out forest fire with a cheap water gun. Ubuntu needs mandatory access control, not some bandaid that really won't do anything to improve security in any meaningful way in the long run.

---

### Post by matthekc on 2008-09-22
How about sudo -t for sudo with time out or something else with no time out.
I think most people get most of there software from the repo's and getdeb or know specifically what they are looking for unlike the install everything windows people.  I would guess that without a lot of independent software installed your not going to have that much malware opportunity.

---

### Post by cardinals_fan on 2008-09-22
> **Warpnow said:**
> Irrelevent.

If the password timer gets reduced to zero then ubuntu has ZERO chance of breaking 10%.

I know several people who I showed linux whose main gripe was entering the password.

People don't care that much about security as the average person doesn't have anything worth hiding.
If people choose to screw things up for themselves, fine.  I can get some sadistic satisfaction from knowing that they pay for their stupidity (all too rare in this world).  However, that doesn't mean that we need to hang up a rope to make it easier.
> **zekopeko said:**
> didn't read the whole thread but here's my 2 cents:

Copy Fedora. When you go all superuser, a nice looking shield icon pops up in the notification area. clicking on it it offers an option to stop sudo.
well actually i don't think it's sudo at all. it's policykit for the most part. nice thing with PK is that you can fine-grain what each user can do with each app (the app has to support PK for maximum effect).

I mentioned this, and I agree that it's a very good idea.
> **toupeiro said:**
> Which is exactly why you should have the option of setting it to zero, and exactly why it should not be zero for the entire world of ubuntu users.  Because, not everyone needs to be protected from themselves, and not everyone just uses it with apt-get.
This isn't an issue of protecting people from themselves.  All this would do is leave me one less insecure default to change when I set up my system.
> **phrostbyte said:**
> You have a point but it's not so relevent to the average user. How many people even know about netstat and even how to intrepid it's output? To someone not computer literate there is no difference between root and user protections .. they'll never know their machine was compromised either way. And even with this in mind it's really really unlikely some malware will go out of it's way to get root access when it doesn't need to get root access to be effective in the long run. Malware writers will go for the path of least resistance and there is VERY LITTLE resistance to running nasties in user space.

To me this thread is like trying to attack the problem of bad security the completely wrong way. Like trying to put out forest fire with a cheap water gun. Ubuntu needs mandatory access control, not some bandaid that really won't do anything to improve security in any meaningful way in the long run.
I would agree with you if this took major effort to implement.  You are correct that this is only a very small scrap of protection.  However, it takes almost nothing to implement, and every little bit counts.

---

### Post by Polygon on 2008-09-22
> **toupeiro said:**
> Which is exactly why you should have the option of setting it to zero, and exactly why it should not be zero for the entire world of ubuntu users.  Because, not everyone needs to be protected from themselves, and not everyone just uses it with apt-get.

it should at least be zero by default, and have an option to change it in some preferences dialog somewhere.

---

### Post by I-75 on 2008-09-22
Lets be realistic, Ubuntu won't break the 10 % barrier for quite awhile as long as Linux as a whole is still shaded in mystery and FUD from the entrenched Windows camp. 

We need to change that.

Apple just finally broke the 10 % at 10.6% and that is with a company that has been in business for 25 years and has a multi million dollar ad campaign with brand name recognition.

Apple is really our biggest competition, then Microsoft. Since Vista was released, Apple has grown big time. Some say from disgruntled Windows/Vista users. Wouldn't it have been nice to have those users migrate to Ubuntu/Linux instead of Apple? We need to get the word out.

One could correctly argue that Firefox rose from nothing to 20% in some four years. However Firefox was just a simple and painless install for anyone. 

One recent development has greatly helped Ubuntu, and that is Wubi, coupled with the "LIVE CD"... the adoption to Ubuntu and Linux as a whole will be much greater in the next year than the last two years. 

 For every Linux advocate, there is another 50 to 100 Windows users. We need to change that, we need to change awareness, we need to counter the FUD. That is slowly, starting to happen. I go into the Windows blogs/forums and post in the comments section and defend Linux and try set the record straight in regards to all the BS out there. 

 Surprisingly it seems that most defenders of Windows are the people who fix Windows computers or sell anti spy-ware software. When one mentions Linux and its ability to resist viruses and malware...the Windows defenders get quite irate.

One thing that the other side cannot refute. And that is the adoption of Linux by Government entities, school boards, military, whole cities, major corporations, Wall Street. When one quotes news sources and statistics...the other side shuts up. 

 Yet there is a positive trend I have been noticing. That is a growing number of Windows users are going dual boot with their new Vista machines. Some of those users say they will never give up Windows, thats OK we just hooked them with Ubuntu...we will reel them in later.

 I hope Ubuntu gets to be 10 % or much more. I would hope that all these mini laptop manufacturers ultimately adopt Ubuntu as their OS as well as major league desktop/laptop manufacturers.

In my opinion Ubuntu is the premier desktop distro for Linux, whereas Red Hat is the premier server distro for the commercial sector.

One thing the Ubuntu team really needs to work on. Is the on going problems of the wireless breaking (or worse) after a kernel update. I have read comments here on the forums where beginners also lost add/remove and even having the OS stop working after upgrades. 

Nothing will create FUD fodder faster by the Windows camp by having disgruntled ex Ubuntu users posters post there complaining that the OS stop working after some updates. We need to get that fixed.

As far as if the sudo timeout should go away, its irrelevant in my opinion... ( in the next release or the after that ...just have a adjustable user timer built in the OS). 

The most important thing is to get there to that 10%.

---

### Post by oedipuss on 2008-09-22
> **I-75 said:**
> Lets be realistic, Ubuntu won't break the 10 % barrier for quite awhile as long as Linux as a whole is still shaded in mystery and FUD from the entrenched Windows camp. 


Yea but still.. there's the whole business with netbooks and ultraportables running linux. *Everyone*'s doing it now, and it seems it'll only get bigger. Seriously, could you imagine almost every major vendor shipping a machine with preinstalled linux two years ago?

---

### Post by toupeiro on 2008-09-23
> **Polygon said:**
> it should at least be zero by default, and have an option to change it in some preferences dialog somewhere.

If that is the case, then I don't know how UNIX and sudo have survived so long in the industry without being publicly flogged if this were such a blatent case of insecurity.  Seriously, the perception I'm reading here of what setting this cache to zero will bring as a security fix is in reality taking one little molehill of an arguably relative issue and calling it a mountain of insecurity which we must conquer. The reality of it is that the productivity effects of having this at zero are much more of a mountain than the security implications of not having it at zero.  I'm sorry that linux isn't riddled with as many security holes to scrape bondo over as other OSes, but I really believe that all this effort and energy would be so much better spent if it were applied to other areas of the OS that would actually make a significant difference...  If you really think people will spend the time trying to reconfigure sudo as opposed to elevating to root and staying there, or simply logging in as root, you're in for a pretty rude awakening.  If you want people to undertake reasonably secure computing practices, then the level of security you implement upon installation has to be within reason as well...  It cannot circumvent that much functionality, not for a Desktop level OS.  Not if you want it to continue its strides of advancement and success on the basis that "it just works."

---

### Post by macogw on 2008-09-23
In the terminal, there's sudo -k to kill your sudo session.  Maybe some GUI way to kill the GUI sudo timeout?  Like an option in the FUSA (Intrepid's has a lot more than Hardy's) "Force Admin Timeout"

---

### Post by p_quarles on 2008-09-23
> **phrostbyte said:**
> How many people even know about netstat and even how to interpret it's output? 
One would hope that anyone placed in charge of network security would be able to understand the output of a netstat query.

> To someone not computer literate there is no difference between root and user protections .. they'll never know their machine was compromised either way. 
If we are premising the idea of computer security upon a user who *doesn't* understand the difference between root and user permissions, then not only will we never know whether the machine was compromised, we will never have any reason to believe it wasn't.


> And even with this in mind it's really really unlikely some malware will go out of it's way to get root access when it doesn't need to get root access to be effective in the long run. Malware writers will go for the path of least resistance and there is VERY LITTLE resistance to running nasties in user space.
I'm relatively new at this stuff, but as an extremely amateur Perl programmer, I would find it more easy to defeat malware if I have root access and the malware didn't than in any other configuration. 

> To me this thread is like trying to attack the problem of bad security the completely wrong way. Like trying to put out forest fire with a cheap water gun. Ubuntu needs mandatory access control, not some bandaid that really won't do anything to improve security in any meaningful way in the long run.
And yet the attacks you have suggested all depend primarily upon social engineering -- which would easily bypass access control.

---

### Post by eentonig on 2008-09-23
> **solitaire said:**
> Thought we were trying to get AWAY from being Windows?

On the one hand we have people who want a 0 time limit (In Vista it feels like you have to enter in the password every time you click on something!). 

All they way to a very long limit. (In XP where the first user is by default a member of the admin group and has all the rights without needing to enter a password).

We have to strike a balance between ease of use and security. The whole reason *Nix systems were more secure was due to the separation of Users and Admin.

You'll get ot the sutuation where no matter which is implimented people will start to log in as ROOT! either by default (i.e. Long time limit for passwords) or; Can't be bothered to enter in the password all the time easier to log in as ROOT to work!

You've got to remember that these are just simple uers. These are people of the land. The common clay of the new West. You know... morons. (Gotta love Balzing Saddles quotes!:D) 

@Warpnow it's not what the user wishes to hide it's what the attacker wants to do. If an attacker gets access they are more likely to use the system to use it as a proxy to D/L VERY Illegal stuff, letting the poor user to face the music if the police ever knock on their door.


I think there's big difference between windows Vista's and Ubunut's/Linux security model. In Vista, you click on an application and you're prompted a thousand times to verify if it's you who started..., do you want..., are you sure... In the end, nobody reads those prompts anymore. Certainly considering the fact that the message is always more or likely the same and the action to get rid of it doesn't require a lot of thinking. Frankly, Vista's pop-ups don't tell me anymore that I'm doing something that's supossed to be done by an admin. It just tells me "Hey! I'm Vista. Are you still not getting bored wih me?"

In Ubuntu you get one prompt for launching the application, and you don't get away with just a click. You have to answer your password. Don't know about you, but for me, having to type my password gives me a lot more awareness about the fact that I'm doing something that is restricted and needs to be done cautiously. (sorry for my spelling)

---

### Post by I-75 on 2008-09-23
> **oedipuss said:**
> Yea but still.. there's the whole business with netbooks and ultraportables running linux. *Everyone*'s doing it now, and it seems it'll only get bigger. Seriously, could you imagine almost every major vendor shipping a machine with preinstalled linux two years ago?
  
Half of Apple's 10.6 %  could have/should have went to Linux...in which most of the Linux share would have went to Ubuntu. 

 
This forum is excellent, and there are some outstanding podcasts doing a great job. One of them is the Gusty Geeks which does a Live Linux show out of Phoenix on a regular AM station. Going Linux is on once every three weeks on the popular Computer America program when CA devotes the entire show to Linux. tllts has been going strong for five years. 

 One thing I have been hearing over and over is that Linux has less than a 1 % share. A mantra repeated over and over by the Windows camp. Gartner reported in a recent article that Linux has a 4 % market share (which I believe is closer to reality). 

[http://digg.com/linux_unix/GNU_Linux_Desktop_Market_Share_is_4_Gartner](http://digg.com/linux_unix/GNU_Linux_Desktop_Market_Share_is_4_Gartner)


In another article, in the UK Linux has a 3% share.

[http://www.theinquirer.net/gb/inquirer/news/2008/08/01/linux-preloads-rocket-per-cent](http://www.theinquirer.net/gb/inquirer/news/2008/08/01/linux-preloads-rocket-per-cent)

I believe we need to really get the word out to the mainstream computer users. My ideas include getting on mainstream radio computer shows and mention Ubuntu and the benefits of it. Going on Windows and Mac forums and spreading the word and correcting the FUD. I'd better stop my rant before I get banned or fined or worse :-)

---

### Post by toupeiro on 2008-09-23
Heres another way to look at the premise of this entire thread.

Say hypothetically that this sudo issue is a bigger security issue than I truly believe it is.  What do I know?  Not everything, thats for certain.

What you're telling me is that you believe you've identified something inherently insecure, or procedurally insecure, within your operating system, but that you feel its only relevant to change in ubuntu *if* ubuntu breaks a 10% market share barrier?!  So all the functionality it enabled users who found ubuntu to be an attractive, usable, and secure OS were basically insecure lures that you intend to button up as soon as you hit a usage milestone because you always felt its insecure, but obviously your priority is ubuntu's popularity.  10% obviously greatens the threat much moreso than 9%, or 5%, or 3%... :confused:  If its insecure, then its insecure at any percentage.  That being said, sudo, the way its currently configured in ubuntu, is **not** insecure.

If I were a prospective user reading the points being made in this thread, I'd stay very far away from ubuntu if this were the criteria for "security" change within the OS.

---

### Post by danbuter on 2008-09-23
I think if you read past the first or second post, you will realize that many people think this is an issue *right now*, and that it needs addressed.

---

### Post by grossaffe on 2008-09-23
like others suggested, timeout should be easily customizable.

---

### Post by lukjad on 2008-09-23
Is this new? Because I remember being able change it before...

---

### Post by aysiu on 2008-09-23
I don't buy this whole "If it'd be a problem then, it's a problem now" line of thinking. Yes, it's a problem now, but that doesn't mean it's an urgent problem.

Let me put it this way.

Let's say there are two neighborhoods in a city--A and B.

A has a high violent crime rate. It's low-income. There is a lot of vandalism and robbery in A. A is also accessible by highway exit, local road, bus, and subway.

B has a low crime rate. B's police blotter has things like "Loud dog reported barking on ____ st. at 3 AM" and "Suspicious person spotted in car near _____ ave." A is accessible via only local roads and most of the houses there are in gated communities.

Now let's suppose someone in neighborhood B says "We need bars on our windows." She would certainly be correct in saying that windows without bars provide far easier access to an intruder than windows with bars. But her neighbors, almost all of whom have never experienced a break-in and probably never will as long as they live in that neighborhood, aren't idiots if they say, "I don't want to put bars on my windows."

Of course, if all the rich people moved out of that neighborhood, public transportation were expanded to go into neighborhood B, and crime increased in there, they'd be stupid not to have bars on the windows of at least the first floors of their houses.

Same deal here with Ubuntu. As long as Ubuntu remains an obscure target, people are far likelier to screw up their own systems by editing the wrong config file or installing a bad update than they are to be targeted by malware designed to exploit a sudo timeout flaw.

So, yes, the single-digit versus double-digit percentage of market share has something to do with how you set up security, and it's not stupid. It's logical.

---

### Post by t0p on 2008-09-23
> **cardinals_fan said:**
> When you use a root prompt you **know** that all commands you run will be run as root.  There are no surprises.

And every time you prefix a command with *sudo* you know it'll be run as root.  Whether you have to type in your password every time or not doesn't alter that.

---

### Post by paul101 on 2008-09-23
sudo timeout 0



make the lazy people pay :guitar:

---

### Post by cardinals_fan on 2008-09-23
> **t0p said:**
> And every time you prefix a command with *sudo* you know it'll be run as root.  Whether you have to type in your password every time or not doesn't alter that.
For the final time, **_this is not a problem when using the CLI_**.  It's only an issue in the GUI, using gksudo/*insert KDE equivalent here*.

---

### Post by toupeiro on 2008-09-23
> **aysiu said:**
> I don't buy this whole "If it'd be a problem then, it's a problem now" line of thinking. Yes, it's a problem now, but that doesn't mean it's an urgent problem.

Let me put it this way.

Let's say there are two neighborhoods in a city--A and B.

A has a high violent crime rate. It's low-income. There is a lot of vandalism and robbery in A. A is also accessible by highway exit, local road, bus, and subway.

B has a low crime rate. B's police blotter has things like "Loud dog reported barking on ____ st. at 3 AM" and "Suspicious person spotted in car near _____ ave." A is accessible via only local roads and most of the houses there are in gated communities.

Now let's suppose someone in neighborhood B says "We need bars on our windows." She would certainly be correct in saying that windows without bars provide far easier access to an intruder than windows with bars. But her neighbors, almost all of whom have never experienced a break-in and probably never will as long as they live in that neighborhood, aren't idiots if they say, "I don't want to put bars on my windows."

Of course, if all the rich people moved out of that neighborhood, public transportation were expanded to go into neighborhood B, and crime increased in there, they'd be stupid not to have bars on the windows of at least the first floors of their houses.

Same deal here with Ubuntu. As long as Ubuntu remains an obscure target, people are far likelier to screw up their own systems by editing the wrong config file or installing a bad update than they are to be targeted by malware designed to exploit a sudo timeout flaw.

So, yes, the single-digit versus double-digit percentage of market share has something to do with how you set up security, and it's not stupid. It's logical.

In your analogy, bars on windows would be what we have today with sudo, configured as is.  To emphasize no bars would emphasize no security, which is definately not what the case is.  Setting a timeout to 0 would be more like using automatic-closing steel plates from the inside, that will never open without my key.  Thats going to far to me.  It probably won't change your opinion, but comparing it to crime ridden neighborhoods isn't really going to change mine either.  I don't think ubuntu Desktop needs to say "I won't let you do this, because my dev knows your computer usage better than you"  Whats the point of bars if you're going to make it pointless to even have a window?  Again, I'm not against giving me the *option* of implementing that level of security, but I am totally against having that decision being made on my behalf.

Is it more secure? hell yes it is!, and if I were running ubuntu server, I might be embracing the idea a little more because of the nature of security server oses generally require.  But you're wanting to take your desktop OS and apply much stricter security implications on a theoritical hack that hasn't even been proven valid IMO on Linux yet.  I'm not saying Desktop OSes should sacrifice security for being functional, but I am saying they shouldn't be UNNECESSARILY over-secure and to heck with functionality.

Not to mention (for the umph-teenth time) the fact that you're flogging the wrong command to begin with!  as several have said, not including myself, focus on gksudo, that seems to be where the real problem is.  Changing cli-sudo's caching buys you practically nothing (I really feel like a parrot), especially with caching being restrained to TTY sessions on CLI sudo.

---

### Post by aysiu on 2008-09-23
I don't think you understand my analogy.

Ubuntu right now is neighborhood B.

Ubuntu if it becomes extremely popular is neighborhood A.

Right now, it's okay to have a 15-minute timeout, because we are not a large target.

And, no, I'm not flogging any command. The timeout is the same (15 minutes) for sudo, gksudo, and kdesu. If people want to make a case that gksudo and kdesu should be 0 and sudo should stay at 15, I could be convinced of that.

---

### Post by toupeiro on 2008-09-23
> **aysiu said:**
> I don't think you understand my analogy.

Ubuntu right now is neighborhood B.

Ubuntu if it becomes extremely popular is neighborhood A.

Right now, it's okay to have a 15-minute timeout, because we are not a large target.

And, no, I'm not flogging any command. The timeout is the same (15 minutes) for sudo, gksudo, and kdesu. If people want to make a case that gksudo and kdesu should be 0 and sudo should stay at 15, I could be convinced of that.


You're right, I didn't read your anology that way.  My misunderstanding.

And I believe that is the case myself and others have made. X-windows on ubuntu typically runs at TTY7 (at least it does on mine). 
> 
necro64:~/Desktop> w
 17:48:20 up 4 days, 20:47,  2 users,  load average: 0.45, 0.32, 0.20
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
utileyez tty7     :0               Thu21    0.00s  1:28   0.16s x-session-manag
utileyez pts/0    :0.0             17:48    0.00s  0.10s  0.00s w
utileyez pts/1    :0.0             17:46    0.00s  0.15s  0.00s sudo make install




 The only thing envoking elevation at that level is gksudo or kdesudo. Other CLI sudo executions are done at other TTY or PTS levels which will envforce a TTY_Ticket check and prompt your for a password, every time.  However, if I want to string multiple sudo commands back to back in PTS/1 and pass my password one time, I don't see that as insecure, and I would see it as very overbearing to have to reverse engineer default security in order to do this.

---

### Post by Skorzen on 2008-09-23
Since I discovered how to change it, my timeout is always at 0.
Security first.
I don't care if it's boring for always prompting password.

---

### Post by toupeiro on 2008-09-23
> **Skorzen said:**
> Since I discovered how to change it, my timeout is always at 0.
Security first.
I don't care if it's boring for always prompting password.

:)

hehe, I don't think boredom was ever a consideration for either side.

I think its totally awesome though, that you a) figured out how to make a security change to your system and b) decided for yourself that it was an important enough change for you to make.

I'm only asking that users of ubuntu continue to be allowed to make such choices that are pro-active in nature, and not reactive or reverse-engineering.

---

### Post by alzie on 2008-09-23
When I use sudo in the terminal then close the terminal I close sudo as well?  Sorry, I'm still a noob.

As far as gksudo goes,  I feel 5 minutes would be lots for me,  I'm not doing a lot under the hood.  I'm sure the option to alter the time would be available for people who require longer periods.  Having a notification that I'm still in gksudo would be useful to me as well.

I'd recommend that any changes that are to be made be done sooner rather than later.  If someone starts using Ubuntu and gets used to the idea of 15 minutes and it's taken away they get upset, people resist change.

That's my 2cents.

---

### Post by toupeiro on 2008-09-23
> **alzie said:**
> When I use sudo in the terminal then close the terminal I close sudo as well?  Sorry, I'm still a noob.  Yes, but this is easily fixable by forking the process.

For example: instead of: sudo xcalc

type: sudo xcalc &



> 
I'd recommend that any changes that are to be made be done sooner rather than later.  If someone starts using Ubuntu and gets used to the idea of 15 minutes and it's taken away they get upset, people resist change.

That's my 2cents.


Speaking only for myself, whats upsetting is not losing 15 minutes.  Its that you're losing more functionality than you are gaining any security, especially if the perceived "problem" (sudo) isn't properly refocused (GUI based sudo) Regardless of what ubuntu devs decide is best for default, the great thing about linux is I can set it to whatever I want it to be.  At the risk of sounding arrogant, I do know MY computer usage practices better than the devs. :-)  Not everyone feels this way, so not everyone will feel as compelled to make security changes to their system, so they will just lose the functionality they had, which may or may not have been more critical to them than whatever they may have gained by this setting.  

Why do I care so much?  I am an admin.  Part of my responsibility as an admin is to find balance between security and functionality.  As an advocate for ubuntu on the desktop and in the enterprise where its applicable, I feel compelled to voice the same considerations here as if I were a developer opposing a change to their work he or she disagrees with. If I can provide security in other ways that do not sacrifice functionality, then I am doing my job right. I have less to worry about with users trying to reverse engineer security settings in order to get their functionality back.  Ubuntu users a bit more dismissive of good practices will have less of a reason to just work out of root when they become frustrated with the way sudo was reconfigured.

I'm not a believer in standards for the sake of having standards, or securing yourself out of functionality.  Security options are great.  Security pre-sets, not always... Standards are wonderful, if they are in scope of reality.

I appreciate and respect every individual reason I've heard for why someone would set it to 0 for caching, with the only exception being that the focus is gksudo and kdesudo, those are legitimate security issues.  However, the fact stands that the same logic does not apply to CLI-sudo, and setting that to 0 (which is what the subject of this whole thread is pointing to) buys practically nothing compared to whats lost.  IMO, there is no good reason to do it.  If you want to avoid a hack surrounding sudo, you're going to get much more mileage focusing on the GUI versions.

---

### Post by cardinals_fan on 2008-09-23
As an aside, when I first started using Ubuntu, I was actually quite confused  as to why I only had to enter my password sometimes when starting Synaptic.  I eventually Googled and discovered the answer.

---

### Post by phrostbyte on 2008-09-24
> **aysiu said:**
> I don't think you understand my analogy.

Ubuntu right now is neighborhood B.

Ubuntu if it becomes extremely popular is neighborhood A.

Right now, it's okay to have a 15-minute timeout, because we are not a large target.

And, no, I'm not flogging any command. The timeout is the same (15 minutes) for sudo, gksudo, and kdesu. If people want to make a case that gksudo and kdesu should be 0 and sudo should stay at 15, I could be convinced of that.

You can make the analogies but I stick to my original point based on technical grounds, sudo's timeout is not a real security risk. The whole outdated user/root security model, the thing sudo is based on is the security risk! _Running everything with the user level permissions is a security risk.. you are giving your applications too much control, much more then necessary most of the time._ If you look in the way security in Ubuntu is progressing, we are moving towards flexible security policies and mandatory access control, and away from sudo all together. See PolicyKit and AppArmor.

Ideally, every package in Ubuntu should come with a default security profile. Firefox and OpenOffice shouldn't be able to edit your session files for instance. X-Chat shouldn't be able to start opening ports on your computer not relevant to IRC. Sudo won't help with these real security problems.. it only enforces a limited barrier between two all encompassing levels of security. It's very primitive security.

---

### Post by lukjad on 2008-09-27
I have no responce right now, except to say this:
sudo is the ground floor. Everything else must be built upon it. It is like the front door to the house. Installing a security system and then remove the door saying that it is no longer needed is faulty logic. This is my understanding and I will have to do more research before continuing to argue for or against this point.

---

