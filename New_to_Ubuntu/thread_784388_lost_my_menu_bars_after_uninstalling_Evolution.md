---
title: "lost my menu bars after uninstalling Evolution"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by gerben1 on 2008-05-06
Hi,

I have lost the main Gnome menubars, I mean the bars on the top and the bottom of the screen. The last time that I was logged in I have uninstalled Evolution, when I tried that in "add/remove programs" it told me that I had to use synaptic to uninstall it. Synaptic uninstalled quite a bunch of packages when I selected to completely uninstal evolution, so I assume a few too many were removed.

Can anybody tell me which packages to install again to get my menubars back?

Also, can anybody tell me how I can start a console after I have logged in, I cannot access any menu's, but there must be some key combination that brings the concole up.

---

### Post by Tiede on 2008-05-06
To start a console, you can try Alt+F1, and type in your credentials.
To bring back whatever was removed, you can try in the terminal
```
sudo apt-get install ubuntu-desktop
```
This WILL bring back evolution though, but at least you will have your panels back.
Why do you need to uninstall Evolution anyways?
You can use whatever app you want and just ignore it.
I'll do some research on uninstalling for you though, just a sec.

---

### Post by Tiede on 2008-05-06
I don't see why you are having this...
For me uninstalling evolution works fine. Check this out:

```
tiede@Laptop:~$ sudo apt-get remove evolution
[sudo] password for tiede: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront ENLEVÉS*:
  evolution evolution-exchange evolution-plugins
0 mis à jour, 0 nouvellement installés, 3 à enlever et 2 non mis à jour.
Après cette opération, 12,5Mo d'espace disque seront libérés.
Souhaitez-vous continuer [O/n]*? 

```
to summarize what it says is, if I want to remove evolution, 3 packages will be removed. *evolution, evolution-exchange* and *evolution-plugins*
so, it should not be messing with your panels or anything else.
Please do this for me:
```
sudo apt-get install ubuntu-desktop
```
then, when it is done, issue the evolution uninstall command and post it here for us. i.e:
```
sudo apt-get remove --purge evolution
```
post the output of the terminal after that command here, and we'll try to help.

---

### Post by gerben1 on 2008-05-06
Thank you Tiede, I have got the menu bars back (by installing ubuntu-desktop).

> **Tiede said:**
> 
Why do you need to uninstall Evolution anyways?
You can use whatever app you want and just ignore it.


Well I use Thunderbird for email. Also, when I click on a "mailto:" field on the internet Firefox always tries to start Evolution, which was quite annoying, so I thought lets just uninstall it and be done with that. 

I did not think that would be a big deal, just uninstalling an email client...

---

### Post by gerben1 on 2008-05-06
@Tiede: in respone to your 2nd post

I used synaptic to uninstall evolution. I first tried "Application->Add/Remove" but it told me something like "I cannot uninstall evolution, use Synaptic to uninstall it", and so I did. I started Synaptic and uninstalled all the packages with evolution in their name. That's quite a few more packages than those that were uninstalled with your "sudo apt-get remove evolution".

Looking in Synaptic right now I see:
- evolution
- evolution-common
- evolution-data-server
- evolution-data-server-common
- evolution-exchange
- evolution-plugins
- evolution-webcal

Yesterday there may have been more installed, but anayways I just marked all those for "complete removal", and then Synaptic told me that there were a whole bunch of other packages that should be removed as well, so I just clicked ok, not knowing there would be so many things that would be uninstalled.

I do not know what it all removed, but one I can already see is WICD, I was using that for my wireless internet, which still works, but now network-manager is back and wicd is gone.

---

### Post by gerben1 on 2008-05-06
uninstalling evolution with apt-get remove evolution seems to be working fine (though I don't see why it wouldn't also uninstall evolution-webcal or evolution-data-server or any of the others):

```

gerben@CC1184274-A:~$ sudo apt-get remove --purge evolution
[sudo] password for gerben:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  evolution* evolution-exchange* evolution-plugins*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 12.5MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 132420 files and directories currently installed.)
Removing evolution-plugins ...
Removing evolution-exchange ...
Purging configuration files for evolution-exchange ...
Removing evolution ...
Purging configuration files for evolution ...

```

---

### Post by avtolle on 2008-05-06
> **gerben1 said:**
> Thank you Tiede, I have got the menu bars back (by installing ubuntu-desktop).



Well I use Thunderbird for email. Also, when I click on a "mailto:" field on the internet Firefox always tries to start Evolution, which was quite annoying, so I thought lets just uninstall it and be done with that. 

I did not think that would be a big deal, just uninstalling an email client...
Do you have Thunderbird as your email client under System-->Preferences-->Preferred Applications? If so, then under FF Edit Preferences Applications Tab, for "mail to" does it show "Use Thunderbird (default)"? That's how mine is set up, and FF loads Thunderbird. I didn't do anything other than select Thunderbird under the Systems-->Preferences-->Preferred Applications, and apparently FF took it from there.

---

### Post by gerben1 on 2008-05-06
Ah nice, thanks avtolle. I did not know about "Preferred aplications" I put Thunderbird there now as my preferred mail reader.

---

### Post by suprfish on 2008-05-06
Evolution is integrated with the GNOME environment, I guess trying to uninstall it caused it to try and uninstall GNOME too. Silly, huh?

---

### Post by unutbu on 2008-05-06
It looks like removing evolution does not remove all packages of the form evolution*:

To find out what packages are still installed, you can do this:
```

COLUMNS=150 dpkg --list evolution*
```
Your output will look something like this:

```
% COLUMNS=150 dpkg --list evolution*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
rc  evolution                       2.12.1-0ubuntu1                 groupware suite with mail client and organizer
rc  evolution-common                2.12.1-0ubuntu1                 architecture independent files for Evolution
ii  evolution-data-server           1.12.1-0ubuntu2                 evolution database backend server
ii  evolution-data-server-common    1.12.1-0ubuntu2                 architecture independent files for Evolution Data Server
un  evolution-data-server-dbg       <none>                          (no description available)
un  evolution-data-server1.2        <none>                          (no description available)
un  evolution-dbg                   <none>                          (no description available)
rc  evolution-exchange              2.12.0-0ubuntu1                 Exchange plugin for the Evolution groupware suite
un  evolution-jescs                 <none>                          (no description available)
pn  evolution-plugins               <none>                          (no description available)
un  evolution-plugins-experimental  <none>                          (no description available)
un  evolution-scalix                <none>                          (no description available)
ii  evolution-webcal                2.12.0-0ubuntu1                 webcal: URL handler for GNOME and Evolution

```

Before you remove a package, you might want to run 'apt-cache show' to get a blurb about the package. For example, 
```
apt-cache show evolution-data-server-common
```

---

### Post by gerben1 on 2008-05-06
> **suprfish said:**
> Evolution is integrated with the GNOME environment, I guess trying to uninstall it caused it to try and uninstall GNOME too. Silly, huh?

Well, it is a bit amazing at least yes. I find it quite strange that an email (and calender/scheduler/etc.) client is not a stand alone program but apparentely somehow intertwined with all kinds of other programs that don't have anything to do with email. On first hearing of it, it sounds like a bad practice, though I obviously do not know how things work and are setup. I can understand that different prgrams may share libraries, but that an email client is tied to a large part of the system sounds strange, a bit like Microsoft's claim "No we cannot take out InternetExplorer, it is a major part of the OS".

---

### Post by gerben1 on 2008-05-06
> **unutbu said:**
> It looks like removing evolution does not remove all packages of the form evolution*:

To find out what packages are still installed, you can do this:
```

COLUMNS=150 dpkg --list evolution*
```
Your output will look something like this:

```
% COLUMNS=150 dpkg --list evolution*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
rc  evolution                       2.12.1-0ubuntu1                 groupware suite with mail client and organizer
rc  evolution-common                2.12.1-0ubuntu1                 architecture independent files for Evolution
ii  evolution-data-server           1.12.1-0ubuntu2                 evolution database backend server
ii  evolution-data-server-common    1.12.1-0ubuntu2                 architecture independent files for Evolution Data Server
un  evolution-data-server-dbg       <none>                          (no description available)
un  evolution-data-server1.2        <none>                          (no description available)
un  evolution-dbg                   <none>                          (no description available)
rc  evolution-exchange              2.12.0-0ubuntu1                 Exchange plugin for the Evolution groupware suite
un  evolution-jescs                 <none>                          (no description available)
pn  evolution-plugins               <none>                          (no description available)
un  evolution-plugins-experimental  <none>                          (no description available)
un  evolution-scalix                <none>                          (no description available)
ii  evolution-webcal                2.12.0-0ubuntu1                 webcal: URL handler for GNOME and Evolution

```

Before you remove a package, you might want to run 'apt-cache show' to get a blurb about the package. For example, 
```
apt-cache show evolution-data-server-common
```

Yep thanks unutbu, dpkg --list evolution* did indeed give similar output as yours. I guess I will just leave those packages for now.

Thanks for the tip on "apt-cache show", that seems very useful.
Actually, I wonder now what would be the safest way to remove packages, using "Applications->Add/Remove", using "Synaptic" or using "apt-get".

---

### Post by Tiede on 2008-05-06
I prefer apt-get because it has better feedback, to my opinion. It is one of the few instances where I prefer the CLI to a GUI. Feels like it gives me more control - and it does.

---

### Post by divolb on 2008-06-19
I have a similar situation but cannot get terminal to come up with the keyboard command Alt-F1.  I new to Linux and Ubuntu, please help.  I hate Windows and I am scared Mac.

---

### Post by Tiede on 2008-06-19
To bring up the terminal, you have to tell it what shortcut you want to use. I am thinking that you haven't set At+F1 as a shorcut to your terminal, which is why nothing shows up. --(this is **not** done automatically by the system)
To set a certain key to open up the terminal, go to System->Preferences->Keyboard Shortcuts
Scroll down to "Launch a terminal" and click on the (probably) empty field to the right of it. Then press the key combination you want to use (I'm thinking Alt+F1)?
That's it! You're done. You can from then on use your new shortcut to your leisure.
Tip: Linger a bit in there to learn a few other shortcuts of use, and maybe assign some others you would like too as well!


Alternatively, the system *does* however have Alt+F2 as a "Run Application" shortcut, you could use that and type gnome-terminal in there...

---

### Post by divolb on 2008-06-20
I have no access to "System->Preferences->Keyboard Shortcuts" as there are NO menubars at all.  Alt+F2 as a "Run Application" does NOT work either.  Any more ideas?

---

### Post by Tiede on 2008-06-20
This sounds fishy.
All these things not working at once is telling me something is not correct. Unless you intended that to happen? Have you taken out the menu bars? if not, open a terminal and type
```
sudo apt-get update
```
It'll ask you to enter your password before it continues.
When it's done, in the same terminal, type
```
sudo apt-get install ubuntu-desktop
```and after that, type in
```
sudo apt-get upgrade
```

This way, if there was any package or anything missing, you will have all of them back... I am assuming you are running hardy...

---
To the side, thouugh, may I ask what command(s) you issued when you tried removing evolution? Or did you use Synaptic. If so, which packages did you mark for removal?

---

### Post by Tiede on 2008-06-20
Now the above commands **should** install evolution back, but after it's done you can decide to do
```
sudo apt-get remove --purge evolution
```
to remove it again.

Hope everything is sorted out.

---

### Post by divolb on 2008-06-20
So how is it that I open terminal if I have no menubars and there is no shortcut key assigned to open terminal and Alt-F2 does not work either?

All of these instructions imply opening terminal.  All I see when Ubuntu Hardy boots up is the default chocolate brown/artistic rendering of a heron painting.  AND NOTHING ELSE.  NOTHING.  Alt F-1 is not defined.  Alt-F2 does NOT work.

I think my mistake was marking EVERTHING with "evolution" for complete removal in Synaptic.

Is it possible to repair this from the Recovery boot option?  Or is a reinstall in order due to my lack of experience with Ubuntu?

Thank you for helping thus far.

---

### Post by unutbu on 2008-06-20
divolb, boot up Hardy. When you get to the Heron painting, press Ctrl-Alt-F2. This should switch you to a text terminal. Login there, and then try Tiede's commands.

---

### Post by divolb on 2008-06-21
THANK YOU ALL!!  Ctrl-Alt-F2 got me to a terminal.  Got it back up and running!!

If I would just stop messing with things I wouldn't have these problems.  But then I would never learn as much because I would not have a reason seek answers to my afore created questions.  

These forums and helpful people are making my transition from Windows to Ubuntu easier.  Thanks.

---

### Post by crockettoo on 2010-02-05
I would like to add that I got into this same pickle ... (suddenly the booting procedure dumped me into a borderless white terminal) ... because I uninstalled Evolution while battling to get my contacts to synch with Ubuntu One. In the process I must have removed one of the *evolution* apps that the system needs to work whether Evolution is installed or not.  

This thread (sudo apt-get update ubuntu-desktop) fixed my problem. Yay!! .... but not straightaway because first I had to get internet from the terminal, and I am wireless. The answer was, to haul out my old cat5 cable and go wired just for the update.

Hope this can save someone else the head scratching I have just been through!

---

### Post by dannyx on 2011-05-19
If you don't want to reinstall evolution and other unnecessary stuffs (coming along with ubuntu-destop) just install gnome-panel also solve the problem. :D

---

