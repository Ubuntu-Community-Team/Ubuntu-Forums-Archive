---
title: "HOWTO: Log Boot Messages"
date: 2005-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Sephiriz on 2005-07-18
At times I find it very difficult to see what has succesfully loaded or not during boot up, and at those times I wish I could have a log to look over in calm.  After inquiring, someone (namely **Nequeo**) discovered this logging functionality.

Here's how to set it up:

You need to enable boot logging by opening a terminal and typing the following:
```
$ sudo gedit /etc/default/bootlogd
``` 

The text editor will open, and the following will be show:

```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

```

Change BOOTLOGD_ENABLE to **yes**

Now, everytime you restart, **/var/log/boot** will be created, and it will contain a log of all your boot messages.  You need to be root to open it, so you can easily open it up again with sudo.

All thanks go to Nequeo for figuring this out, he also added the following:

> 
NOTE: On my machine, I get a message on my screen during boot saying that the boot log has failed. But it was lying, the boot log worked just fine.

ALSO NOTE: The boot log will be full of lines like this '^[[A^[[74G[ ok ]'. All that 'garbage' is just the color code used to display the text as white or red during boot. It seems to get captured along with all the rest of the text.
 

So there you have it!  This is a really useful feature, and I was slightly surprised that this was disabled by default.

---

### Post by renoir98 on 2005-07-18
> 
This is a really useful feature, and I was slightly surprised that this was disabled by default.


Totally agreed!

---

### Post by raphha on 2005-09-29
Very helpful indeed, thank you Sephiriz :-)
raph

---

### Post by henriquemaia on 2005-09-29
Very helpful! Thanks a lot.

---

### Post by mlomker on 2005-09-29
I was looking for this the other day and couldn't find it.  I assumed that since it was running out of rcS.d that it must just be the kernel.log or something.  

As I open a terminal to read through **ALL** of the files in /etc/default...

---

### Post by Marcos.Rufino on 2006-02-25
[QUOTE=renoir98]Totally agreed![/QUOTE]
For Christ sake!! I've lost hours trying to figure out where I could read the boot log. I really don't know why the developers disabled this log. Thanks!

---

### Post by Peepsalot on 2006-07-04
Hmm, I tried this and rebooted, but I see no boot file in /var/log
Any ideas what is going on?

There is a bootstrap.log, but I don't think that is the same thing.

---

### Post by jfdill_2 on 2006-07-07
bootlogd seems to be borked:

bootlogd: cannot find console device 136:0 in /dev

Trying this to start it up before udev:

update-rc.d -f bootlogd remove
update-rc.d bootlogd defaults 08

Update:  Yeah, that fixed it for me.

---

### Post by UeB on 2006-08-21
Hallo!

i also want to use this usefull feature.
but after changing
BOOTLOGD_ENABLE=No
to
BOOTLOGD_ENABLE=yes
in /etc/default/bootlogd

and rebooting twice still no file nameed "boot" exists in /vat/log or anywhere on the hard disk (after serching for "boot")

anybody have an idea why?
thanks!

PS i use the dapper version of ubuntu i dont know if this makes a difference...

---

### Post by Cariboo1938 on 2006-08-26
> **Peepsalot said:**
> Hmm, I tried this and rebooted, but I see no boot file in /var/log
Any ideas what is going on?
There is a bootstrap.log, but I don't think that is the same thing.I have the same problem....I can't find a **"boot"**file in /var/log either, actually nowhere on the HDD! 
Can anybody help us to find it?:wink:

---

### Post by Cariboo1938 on 2006-08-28
> **jfdill_2 said:**
> bootlogd seems to be borked:
bootlogd: cannot find console device 136:0 in /dev
Trying this to start it up before udev:
update-rc.d -f bootlogd remove
update-rc.d bootlogd defaults 08
Update:  Yeah, that fixed it for me.Hi jfdill_2!
Please, can you give more details? What means "borked"? Are these code lines? Where is the log file to find?

---

### Post by Cariboo1938 on 2006-09-07
> **Sephiriz said:**
> At times I find it very difficult to see what has succesfully loaded or not during boot up, and at those times I wish I could have a log to look over in calm.  After inquiring, someone (namely **Nequeo**) discovered this logging functionality.
Here's how to set it up:
You need to enable boot logging by opening a terminal and typing the following:
```
$ sudo gedit /etc/default/bootlogd
```
The text editor will open, and the following will be show:
```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

```
Change BOOTLOGD_ENABLE to **yes**
Now, everytime you restart, **/var/log/boot** will be created, and it will contain a log of all your boot messages.  You need to be root to open it, so you can easily open it up again with sudo.
All thanks go to Nequeo for figuring this out, he also added the following:

So there you have it!  This is a really useful feature, and I was slightly surprised that this was disabled by default.[SIZE="3"][COLOR="Magenta"]Does this only work for Ubuntu Hoary 5.04? Does somebody know what has to be done for Dapper 6.06??:-k [/COLOR][/SIZE]

Using Ubuntu Dapper 6.06.
There are several log files in /var/log: 
1) /var/log/messages (shows activities over a longer period of days)
2) /var/log/dmesg  ([COLOR="Magenta"]**is** the log file from booting the system[/COLOR])
3) /var/log/syslog (in my case it showed today's activities)

---

### Post by Cariboo1938 on 2006-09-08
> **Peepsalot said:**
> Hmm, I tried this and rebooted, but I see no boot file in /var/log
Any ideas what is going on?
There is a bootstrap.log, but I don't think that is the same thing.

[B]Look for /var/log/dmesg
[/B]

---

### Post by Cariboo1938 on 2006-09-08
> **UeB said:**
> Hallo!
i also want to use this usefull feature.
but after changing
BOOTLOGD_ENABLE=No
to BOOTLOGD_ENABLE=yes
in /etc/default/bootlogd and rebooting twice still no file nameed "boot" exists in /vat/log or anywhere on the hard disk (after serching for "boot")
anybody have an idea why?
thanks!
PS i use the dapper version of ubuntu i dont know if this makes a difference...

**Look for /var/log/dmesg**

---

### Post by henriquemaia on 2006-09-25
It works on mine, so it's still valid.

Here's a sample of my /var/log/boot

[INDENT]Mon Sep 25 13:50:21 2006: ^[[74G[ ok ]
Mon Sep 25 13:50:22 2006: ^[[74G[ ok ]Common Unix Printing System: cupsd       ^[[80G 
Mon Sep 25 13:50:23 2006: Starting MySQL database server: mysqld.
Mon Sep 25 13:50:25 2006: .
Mon Sep 25 13:50:26 2006: ^[[74G[ ok ]powernowd...        ^[[80G 
Mon Sep 25 13:50:26 2006: ^[[74G[ ok ]OpenBSD Secure Shell server...       ^[[80G 
[/INDENT]

---

### Post by vivekdn on 2006-10-18
You will need to start bootlogd service to get the messages in /var/log/boot

---

### Post by jdbartlett on 2007-04-12
I had the same issue as **jfdill** in Xubuntu 6.06, and I suspect I suspect those of you who still don't see a "boot" log in /var/log have the same issue: bootlogd isn't correctly (or at all) symlinked in /etc/init.d

I tried the following from bash:

```
jdbartlett@bob: update-rc.d -f bootlogd remove
```
This forces removal the booglogd daemon start script from the init script links, even though it's still present ("f"=="force").

```
jdbartlett@bob: update-rc.d bootlogd defaults
```
This adds it back in for default runlevels.

After a restart, /var/log/boot is all nice and populated.

You can read about update-rc.d by typing:
```
jdbartlett@bob: man update-rc.d
```

And in the Debian Policy Manual:
[http://www.us.debian.org/doc/debian-policy/ch-opersys.html#s9.3.3.1]("http://www.us.debian.org/doc/debian-policy/ch-opersys.html#s9.3.3.1")

Hope that's some help.

---

### Post by searchelite on 2007-06-03
Hi all, i have a problem here. 
I already enabled bootlogd=Yes, but i always found (nothing has been logged yet) in /var/log/boot. How can i fix this? Thx

---

### Post by tfejos@gmail.com on 2007-06-03
Hi!

> **searchelite said:**
> Hi all, i have a problem here. 
I already enabled bootlogd=Yes, but i always found (nothing has been logged yet) in /var/log/boot. How can i fix this? Thx

If you use Feisty maybe you have this bug:
[https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955)

I'm wating for fixing this also.

---

### Post by searchelite on 2007-06-03
thx for ur reply [email]tfejos@gmail.com[/email]...

So this is a bug and still not fix yet...I gues i'm just wating for the fix :(

---

### Post by CheShA on 2007-06-22
Anyone having problems with this on Dapper/Edgy/Feisty see **[this thread]("http://http://ubuntuforums.org/showthread.php?t=478225&highlight=bootlogd")**

---

### Post by tgbrowning on 2007-07-25
At the risk of sounding like a complete dweeb, I go to the terminal and type in $ sudo gedit /etc/default/bootlogd and get:

Command not found.

Jeez. I don't need any more frustration as this point.

Browning>>>

---

### Post by GaryAndersonMissed on 2007-08-03
mr browning... you do not have gedit.  Try replacing gedit with VI in the command.  

if that does not work do a

sudo aptitude intall vi

---

### Post by Yes on 2007-09-05
When I go to the /var/log/boot file, it says "(Nothing has been logged yet.)".  Any reason why this might be?

Thanks.

---

### Post by Hecabe on 2007-10-17
I found a different solution.
Use the command dmesg.
- You might have to install it with:
sudo apt-get install dmesg

Then:
 dmesg > dmesg.txt
gedit ./dmesg.txt

If you want to know more about dmesg, type in terminal:
man dmesg

Have fun reading the log.

Best regards from Mexico!
Hecabe

---

### Post by airencracken on 2008-01-07
This did not work for me in gutsy. Any other suggestions?

---

### Post by BLTicklemonster on 2008-01-26
> **Hecabe said:**
> I found a different solution.
Use the command dmesg.
- You might have to install it with:
sudo apt-get install dmesg

Then:
 dmesg > dmesg.txt
gedit ./dmesg.txt

If you want to know more about dmesg, type in terminal:
man dmesg

Have fun reading the log.

Best regards from Mexico!
Hecabe

Wow. Running gutsy, and got a nice readout.

I have a long boot time, so what can I do with this information? Where can I post it so someone might be able to peruse it and educate me as to what I can do to decrease my boot time?

Thanks for de message about dmesg, by the way. :)

---

### Post by pseudonym on 2008-01-31
The info dmesg gives you is not the same as what bootlogd used to give you. Instead, it's essentially the same log info as you find in /var/log/messages or /var/log/syslog ie. kernel messages.

Unfortunately, due to some nasty bugs, bootlog has been disabled in Ubuntu since Feisty. See [here]("https://bugs.launchpad.net/upstart/+bug/98955") for details.

---

### Post by DioSonoIo on 2008-02-21
> **henriquemaia said:**
> Very helpful! Thanks a lot.

:KS

---

### Post by sujoy on 2008-04-30
> **Sephiriz said:**
> ...

So there you have it!  This is a really useful feature, and I was slightly surprised that this was disabled by default.

thanks its really helpfull

---

### Post by metrorat on 2008-06-03
This is an old thread but thought I'd throw something in which might aid peoples searches.  I'm running Hardy and the boot messages seem to go to /var/log/messages afterwards being archived in .gz format.

/var/log/boot just says nothing logged yet and doesn't seem to want to log anything.

---

### Post by CentralX on 2008-07-02
Bootlogd is probably never going to work because it seems to be part of the old style sysv-init startup method. Ubuntu migrated to "upstart" a while ago. Proof of this are these messages I get when trying to start bootlogd.

```
The program 'bootlogd' is currently not installed.  You can install it by typing:
sudo apt-get install sysvinit

```

And when I try to install sysvinit, it wants to remove upstart, which is ofcourse not a very good idea ;):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  friendly-recovery startup-tasks system-services ubuntu-minimal upstart
  upstart-compat-sysv upstart-logd
The following NEW packages will be installed:
  sysvinit
0 upgraded, 1 newly installed, 7 to remove and 0 not upgraded.
Need to get 111kB of archives.
After this operation, 647kB disk space will be freed.
Do you want to continue [Y/n]? 

```

So I guess it is deprecated.

---

### Post by burneverything on 2008-08-01
does not work :(

and /var/log/messages doesn't contain anything about the failure of gnome-settings-daemo on startup :(

---

### Post by Brando569 on 2008-08-04
read [this](https://bugs.launchpad.net/upstart/+bug/98955) and install sergei's modded bootlogd daemon. i had to change the buffer size in bootlog.c (line 52) from the default 32kb to a whopping 975kb to get it to work most of the way though. 32kb would only log about 6 seconds while 975kb logs about 18

---

### Post by artmendez on 2008-09-01
Hello all.

Does this works at all in Hardy?

My boot sequence messed up after downloading and partially being able to install auto upgrades.

Something seems to be broken during the boot sequence. Now I can only boot using a LiveCD, can access most data (which seems to be fine).

I need to generate a boot log in order to map what's going on and/or seek help.

I already set the flag to YES but did not work.

Any ideas?

saludos.

---

### Post by artmendez on 2008-09-01
Let me try this one as the original (setting the flag to generate /var/log/boot) one did not work.

Gracias amigo. 

saludos.

---

### Post by birkopf on 2008-10-01
> **jdbartlett said:**
> 
After a restart, /var/log/boot is all nice and populated.


Doesn't work for me :(

I have 64bit, Kubuntu, Hardy 8.04.
Instructions are OK in the konsole, but after restart bootlog still doesn't exist :confused:

---

### Post by walkingthecow on 2008-10-01
How is this any different than "dmesg | more" ?? Why do I want to enable a daemon when I can just do a dmesg?

---

### Post by east2idaho on 2008-11-12
You might want to consider setting up a serial console:
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/]("http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/")

It does not look like there is currently a good solution in Ubuntu for logging the boot messages.  However, even if we are eventually provided a good system for logging the boot messages, if you are experiencing a severe hardware problem you may find that the system crashes before the boot messages get written.  The serial console approach ensures that you get boot messages no matter what is happening to the problem system.

---

### Post by Ghilteras on 2008-11-24
setting up a proper console just to be able to log boot messages (NOT DMESG, they are two differente things) is ridicolous, there should just be an easy way to see boot messages: 

for example i have a [Fail] in boot on samba daemon but i can't investigate it because it is not logged anywhere in dmesge or debug/kern/messages logs

i just would love the old boot log, i can't boot on recovery and try to "see" the error in those 2 seconds i get when it's scrolling down can i?

---

### Post by digitalage on 2009-01-22
hmm... not much action here. I'm curious where are those linux freaks who know everything...

---

### Post by jfdill_2 on 2009-01-22
Well... I was trying to do this to troubleshoot some specific problem, and the problem was fixed, so I lost interest in the topic.  When the need arises again, then I will be back.

Oh yeah, serial console as mentioned a few posts back, that is a way that I have done it before.  I used minicom from another linux box and turned capture on then powered up the beast, saved capture to a file for further perusal.  It's not what I would call convenient, but it works.

---

### Post by Endolith on 2009-02-07
What's the way to do this in Intrepid?

---

### Post by herroy on 2009-03-01
I need to be able to see my servers bootlog to diagnose a problem.

Is there any solution to this in Hardy? As stated previously bootlogd has been broken for some time.

---

### Post by drbrando007 on 2009-03-18
OK digital, here's the scoop-

Don't bother messing with the bootlogd switch, it probably depreciated long ago.

One of my installs is an Intrepid 8.1 on a dell lap, this is where you can find the boot log - /var/log/  messages messages.0 messages.1 ...and so on.
I clocked this from the boot one time and it appears to be the complete dump of all of your verbose (non-quiet) boots.

-cheers

---

### Post by dougie173 on 2009-04-02
> this is where you can find the boot log - /var/log/ messages messages.0 messages.1 ...and so on.

Unfortunately  It doesn't log all the console messages in there. 

I need to see the full details as there are some unsavory messages that flash past too quick to see and they are not logged in /var/log/messages.

Is there any way to increase the verbosity so that it logs all messages?

---

### Post by petteriIII on 2009-04-02
Pressing CTRL-s is supposed to pause the scrolling also when booting. In my machine it doesn't operate at all without messing with the speed of core in BIOS (that GHz thing) and even then it is not perfect, but it helps  sometimes – it helped me to see what I wanted.
Scrolling is continued by pressing CTRL-z.

---

### Post by BrainwreckedTech on 2009-05-20
The CTRL+S AND CTRL+Z worked for me, but it should be noted that it doesn't work with usplash.  I used startup-manager to disable the boot splash, rebooted, and waited for the red [fail] to appear.  Turns out that upgrading from Windows 7 Beta to Windows 7 RC changed the vol_id and that's what the startup messages where trying to tell me.

---

### Post by glotz on 2009-05-20
> **Sephiriz said:**
> ```
$ sudo gedit /etc/default/bootlogd
```You should use gksu with graphical programs instead of sudo.

Edit: Holy old thread Batman!

---

### Post by pgn674 on 2010-10-23
It hasn't been mentioned yet, so I'll mention it here. For me at least, when /var/log/boot.log is enabled, it doesn't get everything, just the early messages. To see the later stuff, press Ctrl+Alt+F1 after Ubuntu has finished starting up. To get back to your regular screen, press Alt+F7.

I don't know why it switches from printing to the boot.log file to printing to tty1, but the two together seem to paint a pretty complete startup log.

---

