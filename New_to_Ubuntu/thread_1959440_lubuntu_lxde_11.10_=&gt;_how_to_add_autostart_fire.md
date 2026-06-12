---
title: "lubuntu lxde 11.10 =&gt; how to add autostart firefox and tbird"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by thane1 on 2012-04-15
In ubuntu I had no problems adding firefox and thunderbird to automatically start up on boot.  However so far I cannot get them to auto start on lubuntu 11.10 i386 lxde.  I've tried using vim to edit the /etc/xdg/lxsession/Lubuntu/autostart program and tried varying methods found in searches such as
 ```
@firefox -%u
``` , ```
firefox &
``` and ```
@firefox
``` with no satisfaction.  The best result I could get, would load firefox and thunderbird on restart, but also gave an error message of "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."  

After the aforementioned error message, I removed the entries from the autostart file, restarted and found firefox and thunderbird wouldn't start at all automatically.  So I think I might have the correct file (autostart), but the wrong wording.  Any ideas?  many thanks

---

### Post by thane1 on 2012-04-16
I think I might have had a lead, while sleeping last night (good old rem state).  This was a new installation on my parents' machine. I copied over the firefox and thunderbird .default folders and files, after renaming the new original .default files as .backups.  However I also did the same in replacing the .profile files for both firefox and thunderbird.  I think this is, why I received the error msg telling me there were two instances of both firefox and thunderbird running on startup.  When I get home from work today, I'll reuse the original .profile files and see if I can get the programs working.  Will report back with my findings.  cheers

---

### Post by thane1 on 2012-04-16
Nope... no luck.  I have firefox and thunderbird starting up fine, once lubuntu is up and running.  I've set the profiles to match the .default folders and all's good there.  However editing the /etc/xdg/lxsession/Lubuntu/autostart file is so far a dead end.

Adding firefox & (and thunderbird &) to the end of the autostart file, will not result in tbird and firefox loading on restart.  No luck there.

Both @firefox -%u and @firefox (similarly for tbird) will result in them slowly loading on restart.  But I still get the error messages about there being one instance of the programs already running, which should be closed for the next instance to start.

Does anyone know of the proper way to do this?  Thanks.

---

### Post by JC Cheloven on 2012-04-16
Ok, I can actually reproduce your problem. 

I've found a solution. Please, do as follows:

1) Create a text file named [COLOR="Red"]firefox.desktop[/COLOR] in your ~/.config/autostart directory. 

2) Fill it with the following contents (made by me as fisrt trial; you may want to put a little different content if you understand how to do it):

```
[Desktop Entry]
Version=1.0
Name=Firefox Web Browser
Comment=Browse the World Wide Web
GenericName=Web Browser
Exec=firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=firefox

```

3) Restart, or simply log out and in. Firefox should open automagically.

4) Aditional info: this makes firefox eligible for appearing in the "desktop session configuration" that is in the lxde panel menu -> preferences. You can optionally disable/enable it from there. 

Hope to have solved your question :)
JC

EDIT: of course, the basic procedure also applies to thunderbird or any other app you wish.

---

### Post by Rodney9 on 2012-04-16
See - [How_I_can_autostart_a_program_when_logging_into_Desktop]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_I_can_autostart_a_program_when_logging_into_Desktop")


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by thane1 on 2012-04-17
Thanks for the suggestions friends.  I started out with Rodney9's method, mainly due to the link title Lubuntu One Stop Thread.  Looked promising, when I found my version of lubuntu did in fact have the .config/autostart directory.  But nowhere on my lubuntu version was there a urxvtd.desktop file.  So I tried JC's solution.  Used touch to make the firefox.desktop file required and used vim to add the suggested info to the file.  Needed to change the %u argument on line 6 to -%u to make it work.  

On restart firefox loaded and ran fine without the error msg.  So I did the same for thunderbird, making a thunderbird.desktop file and filling it with ```
[Desktop Entry]
Version=1.0
Name=Thunderbird Email Client
Comment=Email Client
GenericName=Email Client
Exec=thunderbird -%u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=thunderbird
```

A few more changes and I can give my parents' computer back.  I'll mark this thread closed.  Many thanks.  cheers

---

### Post by JC Cheloven on 2012-04-18
> **thane1 said:**
> A few more changes and I can give my parents' computer back.  I'll mark this thread closed.  Many thanks.  cheers

Glad to hear that :)

BTW, just 'firefox' (with nothig like %u afterwards), should also work.

JC

---

### Post by etisdale on 2012-04-18
I've been successful autostarting a number of different programs using the solution provided here, with one important exception: Thunderbird.

This is the method that I use:

1) Copy the .desktop file of the program to autostart from /usr/share/applications into /home/[user]/.config/autostart

2) Menu > Preferences > Desktop Session Settings to enable/disable the program under Automatically Started Applications

3) Restart

Unfortunately, Thunderbird does not work for me using the above method. Anybody know why this might be?

I suppose I could try another method to autostart Thunderbird, but would appreciate any ideas.

Thanks!
 
Crosspost: [http://forums.linuxmint.com/viewtopic.php?f=175&p=568924#p568924](http://forums.linuxmint.com/viewtopic.php?f=175&p=568924#p568924)

---

### Post by JC Cheloven on 2012-04-18
> **etisdale said:**
> I've been successful autostarting a number of different programs using the solution provided here, with one important exception: Thunderbird.
I suppose I could try another method to autostart Thunderbird, but would appreciate any ideas.

Have you actually read post #6 from the OP (thane1), in this thread?

---

### Post by etisdale on 2012-04-18
> **JC Cheloven said:**
> Have you actually read post #6 from the OP (thane1), in this thread?

Indeed.

I'm looking for some ideas on how to troubleshoot autostarting Thunderbird, preferably using the autostart method I described in my post above.

I prefer to autostart some programs per user and not system wide. Any ideas on what might be keeping Thunderbird from autostarting using the method I described above? Thanks!

---

### Post by etisdale on 2012-04-18
JC, it turns out that

> **JC Cheloven said:**
> Glad to hear that :)

BTW, just 'firefox' **(with nothig like %u afterwards)**, should also work.

JC[emphasis mine]

was the solution.

Apparently, "%u" is a field code for a single URL (which URL, I don't know!):

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)

I simply removed "%u" from my thunderbird.desktop file (which was copied into /home/[user]/.config/autostart from /usr/share/applications).

Specifically, I changed the line

Exec=thunderbird %u

to the line

Exec=thunderbird

by removing the trailing "%u".

While it seemed optional for Firefox (per your post above), it appears that "%u" must be removed from /home/[user]/.config/autostart/thunderbird.desktop in order for Thunderbird to autostart at login.

---

### Post by JC Cheloven on 2012-04-21
@etisdale. You may note worthy:
- %u stands for a single URL (the last one you used). Is something like as a variable used by the desktop environment. Omitting that in the syntax will not hurt. 
- copying the .desktop file from /usr/share/applications is just a way to not write one by your own. But it will be a greater file, as it usually has a lot of unneeded stuff (please have a look inside with gedit).
- it is customary over here to start a new thread rather than using an existing one started by another user ;)

Cheers
JC

---

