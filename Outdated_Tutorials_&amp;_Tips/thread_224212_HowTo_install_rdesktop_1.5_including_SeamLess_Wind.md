---
title: "HowTo install rdesktop 1.5 including SeamLess Windows and much more..."
date: 2006-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-07-27
**HowTo install rdesktop 1.5 including SeamLess Windows and much more...**
*posted at: [http://howtoforums.net/viewtopic.php?t=52](http://howtoforums.net/viewtopic.php?t=52) *

Hungry for "citrix" like capabilities with rdesktop...
Want to be able to run your windows application from your linux box in a seamless window...
Want rdesktop to copy/paste, mount your drives and run sound localy...
Well here it is...
Rdesktop 1.5.0-rc1 + Seamlessrdp is all that and more...

Here are some appetizer screenshots before we get going: 
**Ubuntu 6.06 Dapperr + XGL + Compiz + KDE + rdesktop-1.5.0-rc1 + seamlessrdp on windows 2003 tsv on VMware-Server**
Screenshot 1: [explorer-about](http://howtoforums.net/downloads/screenshots/rdesktopseamless/explorer-about.png)
Screenshot 2: [explorer-www](http://howtoforums.net/downloads/screenshots/rdesktopseamless/explorer-www.png)
Screenshot 3: [mspaint-notepad-calc](http://howtoforums.net/downloads/screenshots/rdesktopseamless/mspaint-notepad-calc.png)
Screenshot 4: [oulook-cal](http://howtoforums.net/downloads/screenshots/rdesktopseamless/oulook-cal.png)
Screenshot 5: [outlook-file](http://howtoforums.net/downloads/screenshots/rdesktopseamless/outlook-file.png)
Screenshot 6: [outlook-help](http://howtoforums.net/downloads/screenshots/rdesktopseamless/outlook-help.png)
Screenshot 7: [outlook-msg](http://howtoforums.net/downloads/screenshots/rdesktopseamless/outlook-msg.png)
Screenshot 8: [wmplayer-about.png](http://howtoforums.net/downloads/screenshots/rdesktopseamless/wmplayer-about.png)
Screenshot 9: [wmplayer-lib.png](http://howtoforums.net/downloads/screenshots/rdesktopseamless/wmplayer-lib.png)
Screenshot 10: [wmplayer-www](http://howtoforums.net/downloads/screenshots/rdesktopseamless/wmplayer-www.png)


Your gonna need the compiling tools, so if you don't already have them then:
```

sudo apt-get install build-essential

```

On your Ubuntu:
```

sudo apt-get install rdesktop openssl libssl-dev libx11-dev
wget http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.bz2
tar -xjf rdesktop-1.5.0-rc1.tar.bz2
cd rdesktop-1.5.0-rc1
./configure
make
echo "backup rdesktop original";sudo cp -vp /usr/bin/rdesktop /usr/bin/rdesktop1.4BKUP
sudo mv /usr/bin/rdesktop /usr/bin/rdesktop1.4
sudo make install
sudo chmod +x /usr/local/bin/rdesktop
sudo ln -s /usr/local/bin/rdesktop /usr/bin/rdesktop

```

Validate the install:
```

rdesktop 2>&1 | grep Version

```

You should see something like this:
> 
Version 1.5.0-rc1. Copyright (C) 1999-2005 Matt Chapman.



On your Windows Terminal Server
download:
[http://howtoforums.net/downloads/seamlessrdp.zip](http://howtoforums.net/downloads/seamlessrdp.zip)

Unpack the files to some directory on the server, such as c:\seamlessrdp.


Now on your Ubuntu connect with:
```

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad" servername

```

I have tested this with the following applications as well:
Microsoft Outlook with disk mapping & sound (save your attchments localy & play sound for notification ;-) ):
```

rdesktop '-rdisk 'home'=/home/jacob' -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Microsoft Office\OFFICE11\OUTLOOK.EXE" servername

```

Internet Explorer:
```

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" servername

```

Windows Media Player with sound:
```

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe wmplayer" servername

```

Now if you wanna take it one step further...
You can download and install VMware-Server to run your windows instance in the backround...
you can reffer to this guide for that as well...
[http://howtoforums.net/viewtopic.php?t=5](http://howtoforums.net/viewtopic.php?t=5)
(it's on Breezy but can work with slight modification on Dapper too...I hope to update it asap)

* --BIG thanks to the guys at [http://www.rdesktop.org](http://www.rdesktop.org) and [http://www.cendio.com/seamlessrdp](http://www.cendio.com/seamlessrdp) *

	rdesktop tested with Ubuntu 6.06 Dapper
	seamlessrdp server tested with windows 2003


--
Jacob
Linux -- Breaking All Boundries
"you may say I am a dreamer, but i'm not the only one"
[http://howtoforums.net](http://howtoforums.net)

---

### Post by notjohn101 on 2006-07-28
problem!

heres my output to all the commands

> rdesktop-1.5.0-rc1/doc/keymap-names.txt
rdesktop-1.5.0-rc1/doc/ipv6.txt
rdesktop-1.5.0-rc1/doc/licensing.txt
rdesktop-1.5.0-rc1/doc/patches.txt
rdesktop-1.5.0-rc1/doc/redirection.txt
rdesktop-1.5.0-rc1/doc/rdesktop.1
boys@boys-desktop:~$ cd rdesktop-1.5.0-rc1
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether byte ordering is bigendian... no
checking for X... no
checking for library containing socket... none required
checking for library containing inet_aton... none required
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/modem.h usability... no
checking sys/modem.h presence... no
checking for sys/modem.h... no
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/strtio.h usability... no
checking sys/strtio.h presence... no
checking for sys/strtio.h... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for strip... strip
checking for OpenSSL directory... Not found

Couldn't find your OpenSSL library installation dir
Use --with-openssl option to fix this problem

boys@boys-desktop:~/rdesktop-1.5.0-rc1$ make
make: *** No targets specified and no makefile found.  Stop.
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ echo "backup rdesktop original";sudo cp -vp /usr/bin/rdesktop /usr/bin/rdesktop1.4BKUP
backup rdesktop original
cp: cannot stat `/usr/bin/rdesktop': No such file or directory
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ sudo mv /usr/bin/rdesktop /usr/bin/rdesktop1.4
mv: cannot stat `/usr/bin/rdesktop': No such file or directory
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ sudo make install
make: *** No rule to make target `install'.  Stop.
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ sudo chmod +x /usr/local/bin/rdesktop
chmod: cannot access `/usr/local/bin/rdesktop': No such file or directory
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ sudo ln -s /usr/local/bin/rdesktop /usr/bin/rdesktop
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ rdesktop 2>&1 | grep Version
boys@boys-desktop:~/rdesktop-1.5.0-rc1$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad" C:
bash: rdesktop: command not found
boys@boys-desktop:~/rdesktop-1.5.0-rc1$


---

### Post by evs on 2006-07-28
notjohn101:

Configure failed because it couldn't find OpenSSL.  Therefore, make and make install failed as well and nothing was installed.  Try ```
sudo apt-get install openssl
``` Then start all the steps over again.

I haven't tried installing this yet, but I hope to this weekend.  This looks great.

---

### Post by notjohn101 on 2006-07-28
nope...that dosent work...althought i would think it should

---

### Post by oo_void on 2006-07-28
Try "sudo apt-get install libssl-dev".

------
oo_void

---

### Post by notjohn101 on 2006-07-28
ok that worked but now i got > boys@boys-desktop:~$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe wmplayer" C:/home/boys/seamlessrdp
Autoselected keyboard map en-us
ERROR: C: unable to resolve host

---

### Post by evs on 2006-07-29
You need to specify a Windows server name at the end of the command.  it should look something like ```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe wmplayer" *servername*
``` where "C:\seamlessrdp\seamlessrdpshell.exe" is the location of the seamless rdp executable on the Windows machine and *servername* is the name of the Windows machine.

---

### Post by potrick on 2006-07-29
Do you have to be using Windows 2003 Server? Could I concievably use this to connect to any computer on my network running 2000 or XP? Just wondering.

---

### Post by evs on 2006-07-29
> **potrick said:**
> Do you have to be using Windows 2003 Server? Could I concievably use this to connect to any computer on my network running 2000 or XP? Just wondering.

Definitely not Windows 2000, because you need Terminal Services installed (aka Remote Desktop) which only comes on XP Pro or 2000/2003 Server, so 2000 Server might work.  I tried this with XP Pro and it didn't work, but I have a modified dll to allow concurrent sessions, so I'm gonna play around with it some more.  I have gotten it working with 2003 Server.

---

### Post by potrick on 2006-07-29
Okay. I just remembered I have a licsense of XP Pro, so I'll try it out too and let you know how it works.

---

### Post by jbaloul on 2006-07-29
For those of you who do not have a previous version of rdesktop, the bkup / cp command will fail, which is fine...

You can have both versions installed together..
```

sudo apt-get install rdesktop

```

then start the rdesktop1.5 installation instructions from the begining.

you can also install a front end GUI application to manage your rdesktop connections..
```

sudo apt-get install tsclient

```

although, note that tsclient does not have all the new 1.5 features in the GUI.


Enjoy!

---

### Post by potrick on 2006-07-29
XP Pro did not work for me on a fresh install. Let me know if you figure it out.

---

### Post by rputtagunta on 2006-07-30
Hi,

   I was able to run 'configure' after reading this thread. But, I have a problem running the 'make' command right after that.

   I got all kinds of errors.

The final error said:

make: *** [xwin.o] Error 1

    Any idea where I am stuck and what should I do?

Thank you,
Rahul

---

### Post by jbaloul on 2006-07-30
> **potrick said:**
> XP Pro did not work for me on a fresh install. Let me know if you figure it out.

It could be that the packaged dll's for windows isn't configured for XP pro...you should have everything but seamless windows...
if that is the case than you are probably going to have to fetch and compile the seamless package for XP from Cendio:
[http://cendio.com/seamlessrdp/?searchterm=seamless](http://cendio.com/seamlessrdp/?searchterm=seamless)


rputtagunta,
> 
I got all kinds of errors.

The final error said:

make: *** [xwin.o] Error 1


can you paste the complete make output so i can further assist you?

Thanks,

---

### Post by lime4x4 on 2006-07-30
this is what i get right from the get go

Also how would one set this up to use a vmware image?

john@ubuntu:~$ wget [http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz](http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz)
--12:49:09--  [http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz](http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz)
           => `rdesktop-1.5.0-rc1.tar.gz'
Resolving howtoforums.net... 68.178.211.40
Connecting to howtoforums.net|68.178.211.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,409         --.--K/s

12:49:09 (813.76 KB/s) - `rdesktop-1.5.0-rc1.tar.gz' saved [3409]

john@ubuntu:~$ tar -xvf rdesktop-1.5.0-rc1.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

---

### Post by joelones on 2006-07-30
just a heads up to all, i got this working in windows xp by following the guide here
[http://sig9.com/articles/concurrent-remote-desktop]("http://sig9.com/articles/concurrent-remote-desktop")

One thing. it seems to work only if the user you are trying to connect as is logged off from the windows xp machine.

---

### Post by sguart on 2006-07-30
> **lime4x4 said:**
> this is what i get right from the get go

Also how would one set this up to use a vmware image?

john@ubuntu:~$ wget [http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz](http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz)
--12:49:09--  [http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz](http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.gz)
           => `rdesktop-1.5.0-rc1.tar.gz'
Resolving howtoforums.net... 68.178.211.40
Connecting to howtoforums.net|68.178.211.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 3,409         --.--K/s

12:49:09 (813.76 KB/s) - `rdesktop-1.5.0-rc1.tar.gz' saved [3409]

john@ubuntu:~$ tar -xvf rdesktop-1.5.0-rc1.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

To extract tar.gz archive, you either have to ungzip it first or add the z switch into the tar command, ie tar -xvfz *.tar.gz

sg

---

### Post by potrick on 2006-07-30
Has anyone gotten this to work from VMware server? So far I've failed to connect from 2003 Server and XP Pro. I'm a little confused about what all has to happen on the Windows side to get this to work. I think I've managed to enable Terminal Services, but because nothing seems to work (neither the gui nor the commands) I'm not sure what to do next.

---

### Post by jbaloul on 2006-07-30
sorry bout' that...you are right i had compressed with bz2...i modified the howto...should be fine now
```

wget http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.bz2
tar -xjf rdesktop-1.5.0-rc1.tar.bz2

```

---

### Post by lime4x4 on 2006-07-30
ok got it installed but i get this when starting it

john@ubuntu:~$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 192.168.241.16
Autoselected keyboard map en-us



That is where it just sits

---

### Post by Dromio on 2006-07-30
Just a note to let you know it *IS* working for me, thank you!  I've got an XP SP2 instance I've been running under vmware server for a few small apps and this will make it much more fun to administer them.

Thanks.

---

### Post by lime4x4 on 2006-07-30
well i got mine to work also forgot to enable remote connections on the xp box..
Dromio u mind sharing how u got it to work with a vmware image?

---

### Post by jbaloul on 2006-07-30
> **lime4x4 said:**
> well i got mine to work also forgot to enable remote connections on the xp box..
Dromio u mind sharing how u got it to work with a vmware image?

My 2003 instance is also a VMware instance...simply register & download VMware-Server from vmware.com ...it's free.

Create a virtual machine as if you were building a physical box, pop in the XP or 2k3 CD and start the install...simple as that.

---

### Post by lime4x4 on 2006-07-30
i have that already installed..using vmware for xp and vista..What i meant was how do u actually make the connection to the virtual machine.. Do i have to have it running then use the ip of the virtual machine?

---

### Post by jbaloul on 2006-07-31
> **lime4x4 said:**
> i have that already installed..using vmware for xp and vista..What i meant was how do u actually make the connection to the virtual machine.. Do i have to have it running then use the ip of the virtual machine?

Yes

--
JB

---

### Post by potrick on 2006-07-31
Hey, just wanted to say I got this going and it is sweet. Thanks to everyone who helped me out in the thread, and especially thanks to jbaloul for the original post.

---

### Post by brownjl on 2006-08-01
When I first tried to compile rdesktop I got loads of errors with xwin.h I found that the X11 libs where missing, 

apt-get install libx11-dev

sorted it, incase anyone else finds they need it....

Cheers,

James

---

### Post by bandoba on 2006-08-02
This works great with Windows XP Pro after patching as suggested. Thanks a lot.

One question: For some applications, I see additional rdesktop window which is fullscreen but it appears very dim. The window goes away when I close the application. Is this a known issue? If not, it must be screen refresh issue on my machine. Because sometimes the rdesktop window frame remains after closing the application.

Also, does anybody know how can I run two applications which depend on each other? May be create a command script and run it?

Thanks very much.

---

### Post by jbaloul on 2006-08-02
> **bandoba said:**
> 
Also, does anybody know how can I run two applications which depend on each other?

can you give an example?

JB

---

### Post by bandoba on 2006-08-02
Hi JB,

I'm not sure how can I capture the screen to show you the dimmed rdesktop window. Will try that. But basically if I execute command for Internet Explorer, I see IE window + dimmed rdesktop window. But when I click on rdesktop window in bar near bottom, it just puts focus back in IE window.

Now for example about running 2 apps/processes:
I use Outlook along with Yahoo Pops to receive Yahoo mails over POP. If I use the command in your example which runs Outlook, YPops doesn't start (even if it is in Startup folder). Looks like I have to run it specifically before Outlook starts so that it can retrieve email using POP.

The way I am doing it (still not full proof):
I wrote a VBScript file where 
- I use Shell object to execute YPops.exe.
- Secondly, I run Outlook.exe and wait for it to close.
- After Outlook closes down, script ends. I think I need to close YPops.exe at this point which I haven't done yet.
- With this, I run vbscript file instead of running Outlook.exe directly and it seems to work except when I close Outlook, the rdesktop session doesn't end. I think that is due to running YPops process and needs a fix as I said above.

- BTW, I updated Windows XP Pro as suggested by that link but it still doesn't allow 2 connections.
- If I am running saying Notepad, and execute another rdesktop with IE, it just reopens the Remote Desktop with Notepad window in it. Does anybody see this kind of behavior?

TIA.

---

### Post by jstueve on 2006-08-02
I've installed this and use an vmware XP instance (vmware-server), and when I run an application, a whole WindowsXP desktop pops up and the program doesn't open.  

ideas?

---

### Post by lime4x4 on 2006-08-02
got this working.Using the gui i connect to my xp box in full screen mode is it possible to be able to simply switch back to my linux desktop without disconnecting from the xp box?? Like have rdesktop on desktop4 then easily switch back to linux on desktop 1?

---

### Post by jstueve on 2006-08-03
> **jstueve said:**
> I've installed this and use an vmware XP instance (vmware-server), and when I run an application, a whole WindowsXP desktop pops up and the program doesn't open.  

ideas?

I need more patience... (also make sure no one is logged into the windows session...)

works beautiful

---

### Post by jbaloul on 2006-08-09
As promised...
If anyone wants to install VMware to run your Terminal Server, you can use this guide...
HowTo auto-install VMware-Server on Ubuntu 6.06 Dapper:
[http://howtoforums.net/viewtopic.php?t=55](http://howtoforums.net/viewtopic.php?t=55)

Enjoy!
JB

---

### Post by Eddie Hung on 2006-08-10
I'd just like to add that Seamless Windows will only work if the Welcome Screen (and possibly Fast User Switching, I didn't test that far) is switched on, when using Windows XP.

More specifically, the new rdesktop does not launch the shell you specify (using the -s switch) unless the welcome screen is enabled, even if you have no-one logged in.

Hope that helps, as I spent hours trying to work that out!!

Eddie

---

### Post by corefile on 2006-08-24
Ahh that must be my problem then. I can't get to the welcome screen, I just get that screen that says "press Ctrl-Alt-Delete to begin" (company laptop). Does this mean I won't be able to get seamless working? All I get is full windows, not the seamless

---

### Post by tim- on 2006-09-07
I just followed this HOWTO and it works beautifully!  Didn't have any trouble at all

Using Kubuntu 6.06.1 with KDE 3.5.4 and have my terminal server running on Windows 2000....now I gotta try the terminal server with VMWare!

---

### Post by KillerKiwi on 2006-09-07
Very cool, very useful I hope this makes the edgy repos

---

### Post by quickk on 2006-12-01
Thanks for the great tip/instructions!  I pretty much got this working, but not quite like I want.  I have windows XP running inside vmware and have a few questions:

1. Has anyone managed to get concurrent sessions working with winXP?  I followed the instructions here: [http://sig9.com/articles/concurrent-remote-desktop]("http://sig9.com/articles/concurrent-remote-desktop")
but I still only can get one session working.

2. Is there anyway to run the vmware winXP server in the background (so that I could just start it at Ubuntu's startup), so that it's completely hidden from view?

3. Is there any way to nicely exit a program that was started in seamless mode?  It seems that when I close the program's window, that I don't log off of rdesktop.  Then my winXP running inside vmware is messed up, as well as any further attempts to reconnect through rdesktop.  The only solution is to reboot the winXP inside vmware. 

4. Is it possible to start multiple different programs, each with their own window, and have them running at the same time?

If anyone has any insight, I'd greatly appreciate it.  Thanks!

---

### Post by NobodySpecial on 2006-12-10
quickk -

I have concurrent sessions working.  Just be sure to have three different users on your Windows XP install - then you can run one remote session for each of them, up to a total of three at a time.

My solution to "running in the background" is to run VMWare server on a separate box I have set up as a home server (mail, file server, etc).  My server box has 1 gig memory and I have a mere 128 k memory assigned to the VM, and it works fine for the programs I run.

You are right, closing the remote window does not log off, but sending this command will:
rdesktop -a16 -u UserenameHere -p PasswordHere, -k en-us -s "logoff" ServerNameHere

---

### Post by orn on 2007-02-12
Sorry to bump this after such a long time, but I just tried this out.

I'm running edgy and rdesktop-1.5-rc1, remoting to a Windows XP Pro SP2.

I run: rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\windows\notepad.exe" SERVERNAME -u Administrator -p xxxx -k is

What happens is that rdesktop logs in, but it doesn't launch seamlessrdpshell.exe running notepad. If I go to "start->run->C:\seamlessrdpshell.exe notepad.exe", notpad runs up as a unique window, but explorer.exe is still running, and flickers behind the running application.

Any ideas why the shell isn't running without me manually running it?

---

### Post by lavs23 on 2007-02-18
I'm having some trouble geting this figured out as well this is what I've tried to run.
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u username -p password

Everytime I run this I get the 
ERROR: connect: connection refused message

I followed the guide to enable concurrent sessions.

I followed the guide and enabled fast user switchings and login screens.

I'm just starting to get really into Linux and love Ubuntu but my wife needs Windows to run Adobe CS2 for school.  Any help is much appreciated.

---

### Post by Icarosaurus on 2007-02-18
I have the same problem
I' using vmware and installed rdesktop and seamlessrdp but i get that "connection refused" message

---

### Post by lavs23 on 2007-02-20
I couldn't get it to work in QEmu so I installed VMWare Server and now it works fine, I don't think I did anything different though.

---

### Post by lavs23 on 2007-02-20
Is there anyway to set that logoff command to run when the program is closed?  Otherwise I'll just create a Windows Reset script that logs off every user when ran.  So I won't have to start up VMWare Server everytime.

---

### Post by jbaloul on 2007-03-07
you can use gpedit (Group Policy) to LogOff disconnected sessions.


--
JB
[http://howtoforums.net](http://howtoforums.net)
"Every man dies, but not every man really lives"

---

### Post by lcohen999 on 2007-03-14
has anyone else experienced Beryl crashing with this after a while?

---

### Post by edmondt on 2007-03-14
Beryl doesn't work well with this, I just keep it disabled.

What is the key to auto logoff disconnection session on gpedit.msc ?

---

### Post by Scotty562 on 2007-03-23
> **lime4x4 said:**
> ok got it installed but i get this when starting it

john@ubuntu:~$ rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 192.168.241.16
Autoselected keyboard map en-us

That is where it just sits


Mine is doing this too and it's driving me nuts. I followed the instructions... why won't it work...

---

### Post by lhaeh on 2007-03-24
Here is what I did to get it working on edgy:

I already had XPPSP2 installed on VMware, and I changed it to 'host-only' networking from bridged networking.

I added my Administrator account to be a member of 'remote desktop users.' I also disabled the windows firewall.

I typed in this test command:
> rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u Administrator -p password


I got back:
> Autoselected keyboard map en-us
ERROR: connect: Connection refused


I then replaced 'localhost' in the command with the IP that windows said it had:
> rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 172.16.126.128:3389 -u Administrator -p password

It worked fine, I have no Internet in windows, but that should be an easy fix. I hope my first post here was of help to someone.

---

### Post by thomasr on 2007-03-25
lhaeh

You probably have vmware set up for host only networking. Try bridged networking and you should e able to connect. I had the same problem and that solved it.

---

### Post by Scotty562 on 2007-03-25
Yep. Setting the network connection to bridged fixed my problem too.

---

### Post by hp550c on 2007-03-25
Curious...why hasn't rdesktop v1.5 made it into ubuntu stable yet?  It's been out since last September (I think), yet we still have v1.4.1 :(  Guess I'll manually compile it, but it would be nice to have it in the repository.

---

### Post by bitfoo on 2007-04-03
It's in feisty :/

Maybe hope for backports?

```
bitfoo@ronin:~$ apt-cache show rdesktop
Package: rdesktop
Priority: optional
Section: x11
Installed-Size: 444
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Laszlo Boszormenyi (GCS) <gcs@debian.hu>
Architecture: i386
Version: 1.5.0-1build1
Depends: libc6 (>= 2.5-0ubuntu1), libssl0.9.8 (>= 0.9.8c-1), libx11-6
Filename: pool/main/r/rdesktop/rdesktop_1.5.0-1build1_i386.deb
Size: 121944
MD5sum: fab3203065588f87a7be2f817c837f4d
SHA1: 88c814298f3367b94a561fa7c92e93c21098e5f2
SHA256: 7c64eef9a03a489a5903eacf63cfbd0ddacc895cd19a4e7a2bb91fa4349a9e94
Description: RDP client for Windows NT/2000 Terminal Server
 rdesktop is an open source client for Windows NT/2000 Terminal Server, capable
 of natively speaking its Remote Desktop Protocol (RDP) in order to present
 the user's NT/2000 desktop. Unlike Citrix ICA, no server extensions are
 required.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop

```

---

### Post by jr0ck on 2007-04-10
> **jstueve said:**
> I need more patience... (also make sure no one is logged into the windows session...)

works beautiful

I'm having the same problem you were. No matter what, every time I connect it just loads the whole windows desktop and not the application I specified. I tried what you said (being patient and making sure no one is logged into the windows session) but I still get the same problem.

I'm trying to do a seamlessrdp from Ubuntu 6.10 to a Windows Vista Ultimate box on my local network. Again, rdesktop itself works fine, but seamlessrdp doesn't for some reason. Here's the command I'm using:

rdesktop -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Microsoft Office\Office12\OUTLOOK.EXE" 192.168.1.2:"port" -u user -p pass

Note: "port" = the non-standard port I am running RDP with on my Vista machine. This shouldn't be the problem, as rdesktop itself works, just not the seamlessrdp.

Any help is greatly appreciated.

---

### Post by eetu on 2007-05-03
> **jr0ck said:**
> I'm having the same problem you were. No matter what, every time I connect it just loads the whole windows desktop and not the application I specified. I tried what you said (being patient and making sure no one is logged into the windows session) but I still get the same problem.

I'm trying to do a seamlessrdp from Ubuntu 6.10 to a Windows Vista Ultimate box on my local network. Again, rdesktop itself works fine, but seamlessrdp doesn't for some reason. Here's the command I'm using:

rdesktop -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Microsoft Office\Office12\OUTLOOK.EXE" 192.168.1.2:"port" -u user -p pass

Note: "port" = the non-standard port I am running RDP with on my Vista machine. This shouldn't be the problem, as rdesktop itself works, just not the seamlessrdp.
I'm having the same issue and it is probably related to the fact that there's no way to enable the "Welcome Screen" when the Windows "machine" is a member of a domain. If there's a way to get around this, I'd appreciate it...

---

### Post by jr0ck on 2007-05-03
My Vista machine isn't part of a Domain and the welcome screen is enabled on my PC. If I don't set the username and password arguments on the rdesktop command, then I get the welcome screen first. I still haven't found a solution to this problem. I'm on Ubuntu 7.04 Feisty now.

---

### Post by woodgdo1 on 2007-05-07
I am also part of a domain and ran into these problems. The way I get around it is to connect to the console session of the XP box using the -0 switch in rdesktop and then launch seamlessrdpshell "someprogram" from within that full rdesktop window. I created an alternate shortcut to outlook with the path like "c:\seamlessrdp\seamlessrdpshell.exe  c:\Program Files\Microsoft Office\Outlook11\Outlook.exe" This will take all open windows also and transfer them to your Linux desktop.  
I also used the regedit from here [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359) to disable my desktop so I only pass over my Windows taskbar. 

"Next, we need to set it up so that your Windows install only displays the Task bar and not the desktop on login.

    * In the registry editor navigate to the following key: HKEY_CURRENT_USER\Software\Microsoft\Windows\Curre nt Version\Policies\Explorer
    * Create a new DWORD value that you'll call NoDesktop and set its value to 1"

---

### Post by mousejstr on 2007-05-09
> **orn said:**
> Sorry to bump this after such a long time, but I just tried this out.

I'm running edgy and rdesktop-1.5-rc1, remoting to a Windows XP Pro SP2.

I run: rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\windows\notepad.exe" SERVERNAME -u Administrator -p xxxx -k is

What happens is that rdesktop logs in, but it doesn't launch seamlessrdpshell.exe running notepad. If I go to "start->run->C:\seamlessrdpshell.exe notepad.exe", notpad runs up as a unique window, but explorer.exe is still running, and flickers behind the running application.

Any ideas why the shell isn't running without me manually running it?

Found this link just now:  [http://collegegeek.org/index.php/2007/03/31/windows-applications-in-linux/](http://collegegeek.org/index.php/2007/03/31/windows-applications-in-linux/)

> 
For the sake of this guide, I’m going to extract it to “C:\seamlessrdp”. In Windows Explorer, right-click the newly created directory “C:\seamlessrdp” and select Properties. Go to security, click Add, and add the group “Remote Desktop Users” and click OK.


I have not tried it yet.. I will give it a go in the morning when I get back to work.  If this works for somebody else..

---

### Post by LordOfThePigs on 2007-05-10
OK, I got it to work on XP SP2... Finally

So here were my steps:

1). follow the general guide on seamless RDP here : [http://forgeftp.novell.com/lfl/.html/virtualbox.html](http://forgeftp.novell.com/lfl/.html/virtualbox.html)

2). Setup the c:\seamlessrdp security stuff as described here [http://collegegeek.org/index.php/2007/03/31/windows-applications-in-linux/](http://collegegeek.org/index.php/2007/03/31/windows-applications-in-linux/)
> For the sake of this guide, I&#8217;m going to extract it to &#8220;C:\seamlessrdp&#8221;. In Windows Explorer, right-click the newly created directory &#8220;C:\seamlessrdp&#8221; and select Properties. Go to security, click Add, and add the group &#8220;Remote Desktop Users&#8221; and click OK.

3). make sure that the administrator account you want to use is actually a member of the "Remote Desktop Users" group. To do that, go to "Start->Settings->Control Panel", Select "Administrative tools" then "Computer Management". In the tree view in the left, navigate to "System Tools->Local Users and Groups->Groups", double click the "Remote Desktop users" group and add the users you want to use to do the seamless rdp.

4). Make sure that fast user switching is enabled. Go to "Start->Settings->Control Panel", select "User accounts", click "Change the way users log on and off", and in there tick both checkboxes

5). run regedit and navigate to HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/Policies/Explorer and create a new DWORD value named "NoDesktop" (without the quotes, of course) and set its value to 1. You'll have to do that once for every user that you want to be able to use the seamless RDP (yes, that means painstakingly logging off, logging on as another user and tweaking the registry for this user).

6). Log off from the VM.  (Or maybe reboot, just to make sure all the changes are properly taken into account. If you reboot, you might have to log on with one user, and then log out. I had to do this, otherwise I couldn't connect to my windows guest from my host. If somebody knows how to fix it, I'd be glad to know about it.)

7). Connect to the VM in seamless RDP mode with the following command
```
desktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\windows\explorer.exe" SERVERNAME -u Administrator -p xxxx 
```
This will show you the start menu, and you can launch any application from there.

Hope this helps.

---

### Post by lazyart on 2007-05-14
To add as well-

I've gotten this working on Feisty & Windows Server 2003.  My system runs a domain but still this works fine.

Note:  Feisty ships with all of the components so you won't need any added packages.  The -rsound switch didn't make it into the final version of rdesktop 1.5 so it will error out if you try to use it.

Great guide.

---

### Post by Eddie Hung on 2007-05-14
> **lazyart said:**
> The -rsound switch didn't make it into the final version of rdesktop 1.5 so it will error out if you try to use it.

It works for me under VMWare Server and Feisty!

Maybe you didn't enable sound in your VM software (I know I didn't and it came out with lots of bad file descriptor errors!)

Eddie

---

### Post by dannemil on 2007-06-04
This worked for me, but the Start menu shows up as a thin blue window across the bottom of my Gnome desktop and it is constantly flickering and pulsing - very annoying. I can launch windows programs from this thin window if I double-click where the Start menu would be. It brings up the start menu and lets me start programs in a window. But is there any way to get rid of the annoying pulsating thin blue window?

---

### Post by spamalam on 2007-06-17
[can anyone help?  I've followed the guide and it doesn't seem to let me connect:


% **rdesktop -A -s "d:\programs\network\seamlessrdp\seamlessrdpshell.exe notepad" spamalam:6666**
[i]Autoselected keyboard map en-gb
ERROR: send: Connection reset by peer
NOT IMPLEMENTED: PDU 12
ERROR: Connection closed[/i]


% **rdesktop spamalam:6666**
[i]ERROR: send: Connection reset by peer
NOT IMPLEMENTED: PDU 15
ERROR: Connection closed[/i]


A window pops up for a split second... anyone know what  is going on? :(
Thank you

---

### Post by amadeus266 on 2007-06-20
This is a very good start to running native windows software seamlessly. I got it to work with Feisty and windows 2003 over WAN and any program that does not rely on other files in a separate directory runs fine. The software I tried has the .exe in the main directory, but all the data files are in another directory inside the main directory. However, I would NOT recommend running this way on a production system until everything gets ironed out. It is a major step towards seamless networking and I applaud those that are working on this for a job well done so far! :D



EDIT:  I just realized that the software I tried requires a user# assigned in the system variables. Apparently, this setup bypasses those variables. Any ideas???

---

### Post by dannymichel on 2007-06-23
somehow I  have disabled the login window on vista, so it just automatically logs in even though I set up a password.
Also I get either connection refused or no route to errors.
Can someone tell me how to re-enable the login and why I'm getting these two errors?

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
-Install RDesktop
-Install Vista (Home Premium 32 bit) on VMWare
-InstallVMWare Tools on my Vista (Home Premium 32 bit) VM


Some issues:
-I can't connect to the internet on my VM when I use a "Host Only" connection.
-No sound card installed on VM

---

### Post by bandoba on 2007-06-24
> **dannymichel said:**
> I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty.

So far what I've done is:
-Install RDesktop
-Install Vista (Home Premium 32 bit) on VMWare
-InstallVMWare Tools on my Vista (Home Premium 32 bit) VM


Some issues:
-I can't connect to the internet on my VM when I use a "Host Only" connection.
-No sound card installed on VM

You should use NAT or Bridges networking if you are interested in surfing from your VM.

Regarding sound card - make sure you have added sound device when you created Vista VM. Also there could be problem with vista drivers. Not sure is Vista automatically detects VMware sound device. I am going to try similar setup in day or two. Will post my experience then.

---

### Post by dannymichel on 2007-06-24
THANK you.
I use NAT and it's fine.
How do I "make sure you have added sound device"?
Those aren't the MAIN issue though.

[SIZE="3"]My MAIN issue is making it seamless as if it's a part of Ubuntu as I have seen on other guides and posts.[/SIZE]

---

### Post by edmondt on 2007-07-02
There is a cool patch which fix the concurrent session, enables the program icons and stuff:  [https://www.fontis.com.au/rdesktop](https://www.fontis.com.au/rdesktop)

---

### Post by Unicast on 2007-07-05
> **dannemil said:**
> This worked for me, but the Start menu shows up as a thin blue window across the bottom of my Gnome desktop and it is constantly flickering and pulsing - very annoying. I can launch windows programs from this thin window if I double-click where the Start menu would be. It brings up the start menu and lets me start programs in a window. But is there any way to get rid of the annoying pulsating thin blue window?

I'm having exactly the same problem here.

Anyone have any ideas how to overcome this?

---

### Post by bandoba on 2007-07-05
I just tried this with Vista and default rdesktop that comes with Ubuntu Feisty 7.04 and it didn't work. Since Feisty includes latest rdesktop I thought this should work as it is. Is that correct assumption? I also see another post about problems on Vista. Can somebody confirm it works?

---

### Post by Unicast on 2007-07-06
> **dannemil said:**
> This worked for me, but the Start menu shows up as a thin blue window across the bottom of my Gnome desktop and it is constantly flickering and pulsing - very annoying. I can launch windows programs from this thin window if I double-click where the Start menu would be. It brings up the start menu and lets me start programs in a window. But is there any way to get rid of the annoying pulsating thin blue window?

A quick update to provide a bit more info regarding the problem that I'm getting. I get the XP taskbar at the bottom of the page, but there's an annoying flickering blue strip above it as well. See the attachment below.

I'd be most grateful if someone could help me at least get rid of the blue bar above the taskbar.

---

### Post by chris.peplin on 2007-07-09
The flickering problem seems to occur only when using the classic theme. I switched back to the XP styling, and it's much better.

---

### Post by jusmurph on 2007-07-09
This looks great!

---

### Post by bandoba on 2007-07-19
> **bandoba said:**
> I just tried this with Vista and default rdesktop that comes with Ubuntu Feisty 7.04 and it didn't work. Since Feisty includes latest rdesktop I thought this should work as it is. Is that correct assumption? I also see another post about problems on Vista. Can somebody confirm it works?

Bump!

Is there anybody who got it working with Vista?

---

### Post by billykaka on 2007-08-02
I have starting using rdesktop with seamless on Feisty & I am unable to get the -s option to work at all. Even if I chosses not to use the seamlessrdp option I cannot even get rdesktop to start with an alternate shell. An example of my command is 
rdesktop -s "cmd.exe" 172.16.60.128

This does not start my TS sesion with a cmd shell, it just logs me in and gives me the desktop. Any ideas about what I could be doing wrong?

---

### Post by bandoba on 2007-08-02
> **billykaka said:**
> I have starting using rdesktop with seamless on Feisty & I am unable to get the -s option to work at all. Even if I chosses not to use the seamlessrdp option I cannot even get rdesktop to start with an alternate shell. An example of my command is 
rdesktop -s "cmd.exe" 172.16.60.128

This does not start my TS sesion with a cmd shell, it just logs me in and gives me the desktop. Any ideas about what I could be doing wrong?

I am in the same boat. After posting few messages related to Vista (see my previous posts), I tried it with Windows XP Pro and found that -s option is not doing anything.

I am suspecting that the rdesktop that came with Feisty may not be supporting this feature. I will try to build the rdesktop (as mentioned in first step) and try with that.

---

### Post by Megabird on 2007-08-15
> I have starting using rdesktop with seamless on Feisty & I am unable to get the -s option to work at all. Even if I chosses not to use the seamlessrdp option I cannot even get rdesktop to start with an alternate shell. An example of my command is
rdesktop -s "cmd.exe" 172.16.60.128

This does not start my TS sesion with a cmd shell, it just logs me in and gives me the desktop. Any ideas about what I could be doing wrong?

I've been able to make it work with Kubuntu feisty, but as soon as I have upgraded my Windows XP pro to SP2, it stopped working, so it's not on rdesktop's side.  

With a little bit of research, I found out that Microsoft changed the way Remote Desktop works since XP SP2.

I have found out a registry key to fix this:
in "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer", add a DWORD named "PreXPSP2ShellProtocolBehavior", and set to 1, then logout.  It will execute the alternate shell in "rdesktop -s '...'" now.:popcorn:

I haven't tested it under Win2003, or Vista, but I think it should be the same...

---

### Post by bandoba on 2007-08-16
> **Megabird said:**
> I've been able to make it work with Kubuntu feisty, but as soon as I have upgraded my Windows XP pro to SP2, it stopped working, so it's not on rdesktop's side.  

With a little bit of research, I found out that Microsoft changed the way Remote Desktop works since XP SP2.

I have found out a registry key to fix this:
in "HKEY_CURRENT_USER\Software\Windows\Current Version\Policies\Explorer", add a DWORD named "PreXPSP2ShellProtocolBehavior", and set to 1, then logout.  It will execute the alternate shell in "rdesktop -s '...'" now.:popcorn:

I haven't tested it under Win2003, or Vista, but I think it should be the same...

I tried this with Ubuntu Feisty and Windows XP Pro machine and even after making the registry entry it didn't work. 

One question: did this work with rdesktop that was part of original distribution (Kubunutu in your case) or with new rdesktop that you built as mentioned in first post?

---

### Post by Megabird on 2007-08-16
> **bandoba said:**
> One question: did this work with rdesktop that was part of original distribution (Kubunutu in your case) or with new rdesktop that you built as mentioned in first post?

RDesktop : from the repository (Kubuntu Fiesty, should be the same as on Ubuntu)
VMWare-Server : 1.0.3 installed from the official vmware's tarball 

The repository version of VMWare-Server has a bug that prevents direct host-guest communications in bridged networking mode. see [http://ubuntuforums.org/showthread.php?t=455479]("http://ubuntuforums.org/showthread.php?t=455479").  I used the instructions posted here: [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto") to install VMWare Server.  
Remember that you have to clean-up the system after removing the repository's vmware-server package : ```
sudo dpkg --purge vmware-server
```
The work-around is to use NAT networking, or Host-only networking modes for the guest, if you don't want to install from the tarball.

---

### Post by bandoba on 2007-08-16
Thanks for detailed reply and especially instructions + links about VMware server. I had posted a question about the communication problems on VMware forums and was in process of debugging it. 

Well, because I had VMware workstation license, I have now replaced VMware server with workstation and it is working fine in respect to host-guest communication. But even then, I still don't see seamlessrdp working. Basically when I issue rdesktop command nothing happens on Windows side. I have a feeling seamlessrdpshell.exe doesn't even get executed. Does anybody know of any way to confirm that?

---

### Post by spupy on 2007-08-16
I think it doesn't work with Windows XP Home? :( My XPHome shows the option for remote login in settings, but rdesktop can't connect. Anyone have success with XP Home?

---

### Post by Megabird on 2007-08-16
> **bandoba said:**
> Thanks for detailed reply and especially instructions + links about VMware server. I had posted a question about the communication problems on VMware forums and was in process of debugging it. 

Well, because I had VMware workstation license, I have now replaced VMware server with workstation and it is working fine in respect to host-guest communication. But even then, I still don't see seamlessrdp working. Basically when I issue rdesktop command nothing happens on Windows side. I have a feeling seamlessrdpshell.exe doesn't even get executed. Does anybody know of any way to confirm that?

Well, I haven't tried it with Workstation, but if you set the registry key, it should work.  I'll try to replicate tomorrow just to be sure if the changes I tried before didn't affected something.  Also, you may have group policies if your XP guest is on a domain.  If on a workgroup, run gpedit.msc and check in both "user" and "computer",  "administrative templates"> "windows components"> "terminal services";  Every policies for the remote desktop services are there (except the new ones from SP2, of course!).

> **spupy said:**
> I think it doesn't work with Windows XP Home? :( My XPHome shows the option for remote login in settings, but rdesktop can't connect. Anyone have success with XP Home?

You need XP Pro, it just don't work on XP home.  Microsoft crippled a lot of networking features in the home version to sell pro versions at a higher price.  So, unless you can change your Home installation in a Pro installation, it won't work...

---

### Post by bandoba on 2007-08-17
> **Megabird said:**
> I've been able to make it work with Kubuntu feisty, but as soon as I have upgraded my Windows XP pro to SP2, it stopped working, so it's not on rdesktop's side.  

With a little bit of research, I found out that Microsoft changed the way Remote Desktop works since XP SP2.

I have found out a registry key to fix this:
in "HKEY_CURRENT_USER\Software\Windows\Current Version\Policies\Explorer", add a DWORD named "PreXPSP2ShellProtocolBehavior", and set to 1, then logout.  It will execute the alternate shell in "rdesktop -s '...'" now.:popcorn:

I haven't tested it under Win2003, or Vista, but I think it should be the same...

BTW, I just realized that I don't have a registry key you mentioned in your post. Was that a typo and you actually meant HKCU\Software**\Micorost**\Windows\Current**Version**\Policies\Explorer?

---

### Post by bandoba on 2007-08-17
I believe I have figured out why it was not working for me. Check this link [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization). As mentioned on that page, you need to go to control panel, click User Accounts and ensure that Use the Welcome Screen and Fast User Switching are both checked.

Once I did that, it worked fine. I then removed the registry entry and it still worked. Since registry entry worked for you I have a feeling that may be there is some relation between Fast user switching and registry entry?

With that said, I have a new problem now. After closing the application (e.g. Notepad), the remote desktop session doesn't terminate. It stays open. I have to manually logon and force logout using Task Manager or something like that. Are you seeing same problem?

---

### Post by Megabird on 2007-08-17
> **bandoba said:**
> After closing the application (e.g. Notepad), the remote desktop session doesn't terminate. It stays open. I have to manually logon and force logout using Task Manager or something like that. Are you seeing same problem?

That's normal.  You have to edit the policies with gpedit.msc to change that behavior...

---

### Post by Megabird on 2007-08-17
> **bandoba said:**
> BTW, I just realized that I don't have a registry key you mentioned in your post. Was that a typo and you actually meant HKCU\Software**\Micorost**\Windows\Current**Version**\Policies\Explorer?

you were right, I made a copy-paste error in my first post, the registry key should have read "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer"

Corrected the post...  :oops:

---

### Post by bwakkie on 2007-09-03
Nice thread and I installed it. If you only need one Window window at a time it is nice to work with but if you like to open like more than 3 Window windows from one sever it is a bit useless as the (free) max remote desktop connections on a Windows system are 3 and for each window it uses a new connection.

Is it not possible that the seamlessrdp uses the already existing connection?  For now I probably can not really use it in a functional way. I will use the full desktop as it gives me the possibility to open as many Windows windows as I need. Mostly more than 5.

Cheers

---

### Post by Megabird on 2007-09-05
> **bwakkie said:**
> Nice thread and I installed it. If you only need one Window window at a time it is nice to work with but if you like to open like more than 3 Window windows from one sever it is a bit useless as the (free) max remote desktop connections on a Windows system are 3 and for each window it uses a new connection.

Is it not possible that the seamlessrdp uses the already existing connection?  For now I probably can not really use it in a functional way. I will use the full desktop as it gives me the possibility to open as many Windows windows as I need. Mostly more than 5.

Cheers

Try the instructions on [this page]("https://www.fontis.com.au/rdesktop").  They made a patch that allows rdesktop to reuse the same connections. It's working pretty well here!

---

### Post by bdonkey on 2007-09-09
Running explorer.exe for the taskbar with the nodesktop registry key set works great for launching apps, but the gnome taskbar panel covers up the windows taskbar. Is there anyway to make the windows taskbar sit itself above the gnome taskbar instead of behind it?

---

### Post by razametal on 2007-09-19
Hi guys,

This tip is very usefull for my, thank you.  :KS :popcorn: 

Now I've one question, does any one knows how to print locally from one rdp session?

I'm able to save files from remote sesion to my home :) but now I need to print locally.

There is any way to reduce the  bandwidth  used for the rdp session? :confused::confused:

---

### Post by www.floranet.eu on 2007-09-20
If you tried type only rdesktop you will get the help of him. here is the print:

rdesktop: A Remote Desktop Protocol client.
Version 1.5.0. Copyright (C) 1999-2005 Matt Chapman.
See [http://www.rdesktop.org/](http://www.rdesktop.org/) for more information.

Usage: rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)
   -n: client hostname
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)
   -f: full-screen mode
   -b: force bitmap updates
   -L: local codepage
   -A: enable SeamlessRDP mode
   -B: use BackingStore of X-server (if available)
   -e: disable encryption (French TS)
   -E: disable encryption from client to server
   -m: do not send motion events
   -C: use private colour map
   -D: hide window manager decorations
   -K: keep window manager key bindings
   -S: caption button size (single application mode)
   -T: window title
   -N: enable numlock syncronization
   -X: embed into another window with a given id.
   -a: connection colour depth
   -z: enable rdp compression
   -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
   -P: use persistent bitmap caching
   -r: enable specified device redirection (this flag can be repeated)
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks
        [COLOR=Red] '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
             or      LPT1=/dev/lp0,LPT2=/dev/lp1
         '-r printer:mydeskjet': enable printer redirection
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well[/COLOR]
         '-r sound:[local|off|remote]': enable sound redirection
                     remote would leave sound on server
         '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                      redirection.
                      'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                      when sending data to server.
                      'CLIPBOARD' looks at only CLIPBOARD.
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)

:confused: I have a issue that i need help.
 I receive a message that the share is not acessible....

:confused: I use this shell command:
 rdesktop -g 1280x1024 -a 16 -r 'disk:home=/home/$USER home' -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 172.16.214.128:3389 -u jmark -p XXXXXXX

Here is the image....
[ATTACH]43924[/ATTACH]

---

### Post by Megabird on 2007-09-20
> **www.floranet.eu said:**
> :confused: I have a issue that i need help.
 I receive a message that the share is not acessible....

:confused: I use this shell command:
 rdesktop -g 1280x1024 -a 16 -r 'disk:home=/home/$USER home' -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 172.16.214.128:3389 -u jmark -p XXXXXXX


Single quotes don't expand variables.  Double quotes do:

```
megabird@megabird:~$ echo '$USER'
$USER
megabird@megabird:~$ echo "$USER"
megabird

```

With this in mind, you should call rdesktop this way to share your home directory:
```
rdesktop -g 1280x1024 -a 16 -r "disk:home=/home/$USER" -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 172.16.214.128:3389 -u jmark -p XXXXXXX
```

Hope this helps!

---

### Post by bandoba on 2007-09-20
Actually on Ubuntu 7.04, I have seen same problem of not able to access \\TSCLIENT\<anything>. In my case, I am using command like this rdektop -r disk:home=/home/user1 <machinename>

I never had similar issue before but now it is consistently happening. Does anybody have any idea what could be wrong?

---

### Post by www.floranet.eu on 2007-09-21
Thanks Megabird for your answer. But i tried without the var $USER and tried the name of the user name and i got the same issue. What i have think too resolve this problem is:

:-k I'm triyng to access a share folder in the windows network, so to achive unix clients we need to have a samba server. So my purpose is:

-Ping from inside XP VMachine the outside machines. I got the answer from the machines. Well this is step to the resolution. From this point my network only have Ubuntu machines (a desktop, a server and a firewall). So my resolution will be:

Install the samba in the server and configure with the same Workgroup of the XP VMachine and all the shares and users.

I think this will resolve my problem and i'll have the ability to save my files on the server and got it from the unix network. I'll test this resolution tonight (not tested yet).

Later i´ll post the results...:guitar:

---

### Post by www.floranet.eu on 2007-09-23
:KS:KS:KS:KS Well i have suceed in my idea. Install samba on the server with basic configuration, mount a share drive on xp and voila.... sucessful result. Now i can use my programs with rdesktop without any issue and with great perfomance...........:guitar:

Results:
[ATTACH]44283[/ATTACH]

[ATTACH]44284[/ATTACH]

[ATTACH]44285[/ATTACH]

---

### Post by Crick on 2008-05-20
> **Megabird said:**
> Single quotes don't expand variables.  Double quotes do:

```

[CODE]rdesktop -g 1280x1024 -a 16 -r "disk:home=/home/$USER" -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 172.16.214.128:3389 -u jmark -p XXXXXXX
```

Hope this helps!
Thank you, the -r option example was very, very helpful. Now I can transfer files to my local ubuntu machine, edit them on vim, then copy them back to the appropriate windows directory without having to go through the laborious process of emailing the files back and forth. I wish I could thank the post, oh well.

---

### Post by yellowstonemay on 2009-04-23
I have a java version seamless rdp client. it may be make thing easier. Try it and give me comments. [http://zhoupenghust.web.officelive.com/seamlessrdp.aspx](http://zhoupenghust.web.officelive.com/seamlessrdp.aspx)

---

### Post by mlsquad on 2010-01-21
According to [https://wiki.ubuntu.com/SeamlessWindowsIntegration](https://wiki.ubuntu.com/SeamlessWindowsIntegration)
"The new version of RDP that ships w/ Vista support running individual programs. The easy solution here is simply to wait until rdesktop supports this feature and use that as the forwarding mechanism."
This problem affects Windows 7 as well.

---

### Post by bmullan on 2010-01-29
I've used rdesktop and seamlessrdp on both xp and windows server 2003 on many occasions but I ran across a post that reminded me about Win4Lin which I'd casually looked quite a while ago.

This time I decided to go to their web page.

[WIn4Lin Desktop 5.5 Ubuntu Edition]("http://www.win4lin.biz/servlet/Detail?no=19")

Although I think Win4Lin was/sold or morphed into VirtualBridges (and some partnership w/IBM) Win4Lin was offering a really good deal on their Win4Lin v5.5 Ubuntu Desktop Edition for ($29).

**For only $29** I had to try Win4Lin.   I'm glad I did.  Its basically taken all the work out of trying to get a perfect KVM environment for running Windows XP or 2003 (I have been trying both out).

*By default Win4Lin does several things right off the bat that are very cool* (there's more).

[LIST]
[*]The Windows Desktop is **fully re-sizeable in** its X Window on the Linux Desktop.   I was never able to figure out how to get a standard rdesktop to a Windows XP or 2003 to do that on my own

[*]It automatically maps your Windows Documents Directory to your Ubuntu /home/<username> directory _and syncronizes_ files/directories between the two locations.

[*]Win4Lin has a simple Icon tool that allows you to setup a Ubuntu Desktop Launcher Icon that will start and present only a single Windows App in a floating/resizeable window (like what seamlessrdp does).

[*]Win4Lin also supports audio (including Pulseaudio), and printing from the Windows XP or 2003 KVM virtual machine.
[/LIST]

Win4Lin is fast and seems to allow the Windows OS to use KVM to directly access disk and network for i/o

**In essence... it was a great deal for $29 !**   

Note... there are 4,000 licenses left then I assume that you'd have to buy this from Virtual Bridges and their Partner IBM.

Brian

---

