---
title: "block wine internet access"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by nutpants on 2008-11-22
everyone says that linux is mostly free from spyware 
but i use wine a lot and i dont want the windows programs in wine
to have internet access.. i still want them to have local network access but not internet..

how do i do this?

nutz

---

### Post by chrisod on 2008-11-22
If you are worried about specific programs you can block the ports they use at the router. But really, you are worrying about stuff that you don't need to worry about. Wine is not Windows, it's Linux. If you are safely behind a firewalled router you don't have much to worry about.

---

### Post by jyaan on 2008-11-22
An easy way would to be to use trickle, wondershaper, or some other bandwidth limiter and just set the limit for WINE to 0kB/s. I believe there are other options in there as well, so you could disable anything but local.

---

### Post by nutpants on 2008-11-22
> **chrisod said:**
> If you are worried about specific programs you can block the ports they use at the router. But really, you are worrying about stuff that you don't need to worry about. Wine is not Windows, it's Linux. If you are safely behind a firewalled router you don't have much to worry about.

that would be great if i only accessed the internet from my router at home, but 75%+ of my laptop usage is while connected to others internet, both cable and wifi.

if i knew what ports that the windows software used, rather than the ports they say they use then have other ones appear irregularly as the software either phones home, or trys for updates i DONT want that may not work in wine, or give out usage or a hundred of the other things windows software does that make a good inbound and OUTbound firewall a requirement.

it would be best if i could shut down wine access to the internet, and if not kill the network ability of wine altogether.

there is not much point having a "safe" OS then emulate a unsafe one and not take precautions. 

nutz

---

### Post by Skripka on 2008-11-22
What programs are you worried about having network access?  Odds are, whatever it is, won't be able to do much under Wine in Linux--as most malwares and viruses require the equivalent of sudo level access to do their evil.


I've run programs under Wine without worry...............................................it was only AFTER I ran them under Windows XP (I have a dedicated drive for when Wine is not perfect enough), that I found out they were heavily infected with nasty malwares/trojans/viruses.....By "after" I mean than in less than 5 minutes said XP install was dead and bluescreening.

Odds are you have little to worry about.  Odds are.

---

### Post by nutpants on 2008-11-23
> **Skripka said:**
> What programs are you worried about having network access? 

Odds are you have little to worry about.  Odds are.

i am one of the few who trust microsoft with nothing.
and almost no windows program.
i have used (and still)MANY MANY programs that "phone home" in windows
but at least with windows i had a good firewall that blocked outgoing and incoming access.  
i miss that conrtol..
i miss not knowing when a program "phones home" or some other activity that i just dont know about or trust

nutz

---

### Post by handydan918 on 2008-11-23
> **nutpants said:**
> i am one of the few who trust microsoft with nothing.
and almost no windows program.
i have used (and still)MANY MANY programs that "phone home" in windows
but at least with windows i had a good firewall that blocked outgoing and incoming access.  
i miss that control..
i miss not knowing when a program "phones home" or some other activity that i just don't know about or trust

nutz

I'm right there with ya, man, so don't take this wrong.

1) I don't trust M/S

2) So I install software that says it prevents M/S software from "phoning home".

3)  believe that this software, running on an M /S operating system, actually prevents kernel-level functions from executing without my "permission".


Inevitable conclusion? I'm an idiot.


At least with *n*x you can see the code...

---

### Post by nutpants on 2008-11-24
i agree that you cant trust what any commercial software vendor claims about its software.
windows or linux.
if oyu cant see the code then you dont know what it is doing.
the open source software for linux is fantastic,
but sadly it falls far short of what i need.
so i use wine to runs the stuff that i have to.
and i use vmware when i must.

and application aware firewall is a must for me.
i HAVE to use closed source software.
and i would really like to know when it tried to phone home.

linux may be the future
but with out this ability you will have 10 million windows user converts installing tons of "free" closed software someday.
and no one will have any idea what the closed source software is doing.

it will happen.
because people make money that way.

nutz

---

### Post by lunarlatte on 2009-05-16
I'm posting to an old thread for the benefit of current searches for a solution to this issue.  It's possible to resolve this issue exactly as requested using the features of iptables.  The idea being to restrict just wine (and only wine) to local network access but not internet access.  I've included the steps here for posterity (in case the original owner of this thread is no longer looking for a solution.)

Iptables can restrict network access on a per user basis.  If you run wine under a different username and restrict that username's network access, your problem is solved.  Let's assume a situation where your primary username is "nutpants".  You run X and log in to desktop sessions as "nutpants".  Further you create a new user account for wine usage with the username "wineuser".  Finally let's assume your local network is 192.168.0.0/24.

Proceed as follows:

Create the wineuser account.  Use either the account creation tool from your window manager or from the command line:

[FONT=Courier New]sudo useradd wineuser -m -s /bin/bash
sudo passwd wineuser[/FONT]
(then specify a password)

You may want to manually add this user to different groups to allow access to audio and the cdrom drive.

Determine the UID of this user:

[FONT=Courier New]id wineuser[/FONT]

Let's say the command prompt returned a UID of 1001 for this user.  Now set up the network restriction via iptables:
[FONT=Courier New]
sudo iptables -I OUTPUT -m owner --uid-owner 1001 \
  -d ! 192.168.0.0/24 -j DROP[/FONT]

Now you need to be able to run wine as wineuser and still see wine programs on the nutpants desktop.  Ordinarily this won't work because the wineuser needs restricted access to your X server.  Grant access like so:

[FONT=Courier New]sudo cp /home/nutpants/.Xauthority /home/wineuser
sudo chmod 600 /home/wineuser/.Xauthority
sudo chown wineuser: /home/wineuser/.Xauthority[/FONT]

Now open a terminal, su to wineuser and export your display to proper desktop.  In most cases this will be desktop 0 unless you're running multiple X servers:

[FONT=Courier New]sudo su - wineuser[/FONT]
[FONT=Courier New]export DISPLAY=:0[/FONT]

Make sure you can connect to the X server by running xclock or some other basic app:

[FONT=Courier New]xclock[/FONT]

If you see the xclock app appear on your screen, you're set to go.  Close xclock and run wine from the same terminal window you spawned xclock from.  Wine will not be able to access the internet.  You'll have to repeat the export DISPLAY function for each new shell you open for wineuser.  If you don't like copying .Xauthority around, you can always install sshd on your machine and ssh from a nutpants shell to your wineuser account with X11 forwarding.  The prevents the need for copying .Xauthority but now all X activity is redirected through ssh.  (This is inefficient due to encryption/decryption overhead.)
[FONT=Courier New]
ssh -X wineuser@localhost[/FONT]

---

### Post by amac777 on 2009-06-16
Hello, I was having this same problem of trying to prevent programs (like wine) from using the network and figured a similar way to the above solution by lunarlatte. The difference is that I wanted to be able to run *any* particular program but take away it's network access. I wrote it as a tutorial yesterday here:

[http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)

I'm posting the link here in case it's helpful.

---

### Post by sizzlor on 2010-01-23
@lunarlatte: I just want to say THANK YOU for replying to this thread and contributing useful information instead of evangelizing about how people should use their PCs.  You rock!

---

### Post by badSheep8 on 2010-04-05
> **amac777 said:**
> Hello, I was having this same problem of trying to prevent programs (like wine) from using the network and figured a similar way to the above solution by lunarlatte. The difference is that I wanted to be able to run *any* particular program but take away it's network access. I wrote it as a tutorial yesterday here:

[http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)

I'm posting the link here in case it's helpful.

Your thread was very helpful thanks. I tried it before with AppArmor (way too much configuring and problems), just messing up my Wine network dll (didn't work out so well) and assigning Wine to another user also discribed in the current thread (I didn't like adding another user just for this).
I did have some troubles with the group add which disapeared each time after logging off and on so I did it with "sudo groupadd no-internet" and "sudo usermod -a -G no-internet my_user"

For those who might be interested....
When installing programs with Wine and you don't want them to access the internet when installing stuff you have to go to the folder and run ni "wine Setup.exe" for example or you adapt the right-mouse launch command.

The Wine links in Nautilus can be modified in: /home/my_user/.local/share/applications/wine/Programs

So for Photoshop my link looked like this: Exec=ni 'env WINEPREFIX="/home/my_user/.wine" wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS2\\Photoshop.exe"'

---

### Post by BIGFY on 2011-04-07
Simple Solution from within Wine 

Open up Terminal
Type in:
wine regedit

This will open up the windows registry editor for wine. Now what you need to do is setup an invalid proxy for wine to use to access the Internet.

Go into 
-HKEY_CURRENT_USER
 -Software
  -Microsoft
   -Windows
    -Internet Settings

You should see a ProxyEnable key that is set to 0. Open it up and set it to 1
Create the following DWORD values by right clicking and selecting new.

"MigrateProxy" set to 1
"ProxyHttp.1.1" set to 0

Create the following Strings

"ProxyOverride" set to "<local>"
"ProxyServer" set to "http://LolFakeProxy:80"
"UserAgent" set to "Mozilla/4.0 (compatible; MSIE 8.0; Win32)"

These settings taken from the official Microsoft help website talking about the registry and setting up Internet proxies.
This works for me, if you have better settings go ahead and use them, just know that editing wine Registry is very simple.
Start searching for ways to disable Internet in Windows through registry, the same should apply for Wine.

Cheers, enjoy.

---

### Post by Carmageddon on 2013-04-16
> **lunarlatte said:**
> I'm posting to an old thread for the benefit of current searches for a solution to this issue.  It's possible to resolve this issue exactly as requested using the features of iptables.  The idea being to restrict just wine (and only wine) to local network access but not internet access.  I've included the steps here for posterity (in case the original owner of this thread is no longer looking for a solution.)

Iptables can restrict network access on a per user basis.  If you run wine under a different username and restrict that username's network access, your problem is solved.  Let's assume a situation where your primary username is "nutpants".  You run X and log in to desktop sessions as "nutpants".  Further you create a new user account for wine usage with the username "wineuser".  Finally let's assume your local network is 192.168.0.0/24.

Proceed as follows:

Create the wineuser account.  Use either the account creation tool from your window manager or from the command line:

[FONT=Courier New]sudo useradd wineuser -m -s /bin/bash
sudo passwd wineuser[/FONT]
(then specify a password)

You may want to manually add this user to different groups to allow access to audio and the cdrom drive.

Determine the UID of this user:

[FONT=Courier New]id wineuser[/FONT]

Let's say the command prompt returned a UID of 1001 for this user.  Now set up the network restriction via iptables:
[FONT=Courier New]
sudo iptables -I OUTPUT -m owner --uid-owner 1001 \
  -d ! 192.168.0.0/24 -j DROP[/FONT]

Now you need to be able to run wine as wineuser and still see wine programs on the nutpants desktop.  Ordinarily this won't work because the wineuser needs restricted access to your X server.  Grant access like so:

[FONT=Courier New]sudo cp /home/nutpants/.Xauthority /home/wineuser
sudo chmod 600 /home/wineuser/.Xauthority
sudo chown wineuser: /home/wineuser/.Xauthority[/FONT]

Now open a terminal, su to wineuser and export your display to proper desktop.  In most cases this will be desktop 0 unless you're running multiple X servers:

[FONT=Courier New]sudo su - wineuser[/FONT]
[FONT=Courier New]export DISPLAY=:0[/FONT]

Make sure you can connect to the X server by running xclock or some other basic app:

[FONT=Courier New]xclock[/FONT]

If you see the xclock app appear on your screen, you're set to go.  Close xclock and run wine from the same terminal window you spawned xclock from.  Wine will not be able to access the internet.  You'll have to repeat the export DISPLAY function for each new shell you open for wineuser.  If you don't like copying .Xauthority around, you can always install sshd on your machine and ssh from a nutpants shell to your wineuser account with X11 forwarding.  The prevents the need for copying .Xauthority but now all X activity is redirected through ssh.  (This is inefficient due to encryption/decryption overhead.)
[FONT=Courier New]
ssh -X wineuser@localhost[/FONT]



This guide is somewhat outdated, I have not managed to get it to work, but first of all: the iptables commands needs to be updated to this method:
```
iptables -I OUTPUT -m owner --uid-owner 1001 ! -d 10/24 -j DROP
```

But as I said, testing eventually is not working, using Ubuntu 13.04 Raring Rintail with Unity:
wineuser@genadi-deskubuntu:~$ export DISPLAY=:0
wineuser@genadi-deskubuntu:~$ xclock 
No protocol specified
Error: Can't open display: :0

I have dual displays, but not running multiple X sessions..

---

### Post by oldos2er on 2013-04-16
Old thread closed. If you have questions about Raring, please post them [here]("http://ubuntuforums.org/forumdisplay.php?f=427").

---

