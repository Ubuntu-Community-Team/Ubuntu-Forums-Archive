---
title: "Panels are corrupt in Hardy"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Jackbrown on 2008-06-04
First of I would like to congratulate and applaud everyone who are involved in making Ubuntu. As a multiple OS user (read Windows and Macintosh OS X, and Hackintosh OS X [Leo4ALL]) I prefer the UI of Ubuntu to any I have used before and for all the fanboys of Mac, yes I prefer it to even Leopard and at never before seen speeds and ease of use (for all those ppl who say Linux is difficult because of its command line, lemme tell you for doing any advanced stuff on  even the easy to use Windows you have to access command-line like DOS or Command Prompt, like netstat or ipconfig or ping etc.) Just have to learn the commands here which by far are the most intuitive (apt-get update?!?!?! or apt-get install 'whatever-app' lol how much more easy can it really get, not to undermine the super-hyper-ultra-highly advanced and l337 Lin-users and programmers etc.). But I say We got a winner. Though as a designer I would like the port of fav pro designing appz most basic being adobe suite.

Ok enough raving about Ubuntu, here is my problem, I install TOR and Privoxy using the 7.04 (ofcourse I know mine is not this one but I figure its not all that different) community guide (of course I made the necessary changes replacing 'feisty' with 'hardy' minus the colons, follow the rest step by step and while apt-get was get the apts (lol!) I made some changes to the  UI panels like un-checking the expand option and adding transparency etc. Now after Apt was done installing and after making the changes to the Privoxt config file (using nano as stated in the guide) I restarted my machine and everything went fine till after I logged on. My panels were all crazy, and there was nothing I could do to them coz if I right clicked on them my comp would only respond after 5-10 mins. I tried to get the terminal up by pressing Alt-F2 but that didn't work either so some how I got the file browser up and using one of the screen lets script ( clicking 'run in terminal') I got the terminal as well as the 'Control Panel' screen let running but I was only able to run Firefox from it which still ran like a champ. So i rebooted into to recovery mode did the repair and stuff, but it didnt work. 

Now what do I do (apart from the well-known 'reinstall your OS' option)???

Any and all help would never be forgotten.:)

---

### Post by SunnyRabbiera on 2008-06-04
you can try to reinsall the gnome desktop

---

### Post by starcannon on 2008-06-04
```
rm -r ~/.gconf
```

Reboot

You should now have a nice stock looking set of gnome-panels.

-------------------------
added tilde and the -r recursive flag, the command will now work as intended, sorry for the mix up I was tired when I posted originally.

---

### Post by iaculallad on 2008-06-04
If you can hit on the terminal, try restoring your panel:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/panel
sudo pkill gnome-panel
```

---

### Post by Jackbrown on 2008-06-04
Thanks lot guys. that was the qickest replies I have seen till date <Now its time to try>

Thanks.

---

### Post by Jackbrown on 2008-06-04
@SunnyRabbiera 

I dont know how to do that......yet!

@starcannon 

it says "rm: cannot remove './.gconf': Is a directory"

@iaculallad

when I put this: sudo gconftool-2 --shutdown

nothing seems to happen

next when I put this:sudo rm -rf ~/.gconf/panel

nothing seems to happen

next when I put this:sudo pkill gnome-panel

the funny looking panel on top goes away and the bottom panels now are 'better' by which I mean they dont 'look' corrupt anymore but dont seem to work well or mostly dont work at all, neither can I see the thrash can. So I dont think its working. Also not to mention, its slow as hell (well it always was since this problem began)

Please can u guys give me anymore solutions? I would be greatful

---

### Post by iaculallad on 2008-06-04
> **Jackbrown said:**
> 

@iaculallad

when I put this: sudo gconftool-2 --shutdown

nothing seems to happen

next when I put this:sudo rm -rf ~/.gconf/panel

nothing seems to happen

next when I put this:sudo pkill gnome-panel

the funny looking panel on top goes away and the bottom panels now are 'better' by which I mean they dont 'look' corrupt anymore but dont seem to work well or mostly dont work at all, neither can I see the thrash can. So I dont think its working. Also not to mention, its slow as hell (well it always was since this problem began)

Please can u guys give me anymore solutions? I would be greatful

Had you tried restarting your system?

---

### Post by Jackbrown on 2008-06-04
> **iaculallad said:**
> Had you tried restarting your system?

Actually there is no way this machine shuts down normally now so I did press the restart button but sadly it has gone back to being crazy again...

---

### Post by starcannon on 2008-06-04
@Jackbrown 

Yeah sorry my bad, try this :

```
rm -r ./.gconf
```

directories require the -r recursive flag in order to be removed.

I was tired and made a type ::blush::

GL and have fun.

Oh and Johnbrown please take a moment to look at ```
man rm
``` you should be very careful when using -r or -f flags you can nuke a lot of data fast with those. Never, ever run *sudo rm -rf* unless you know for damn sure what its pointed at and that what it is pointed at will be wiped out. Anyway, rm is a powerful tool, be careful of people who may give you a malicious command, socially engineered virus's are really the only viral threat to a linux user so be sure to understand the implications of commands before implementing them.

---

