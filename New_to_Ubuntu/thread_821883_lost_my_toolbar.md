---
title: "lost my toolbar"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by cohs on 2008-06-07
im new to ubuntu.  going on about a week now.  im using 8.04.   i just restarted a few minutes ago, and my toolbar never appeared.  is there a way to get it back so it can make life on ubuntu alot easier.  i recently installed lampp, but i am not able to uninstall because you need root privledges to do that and i cannot use the su command because i cant find terminal.  can anyone help?

---

### Post by t0p on 2008-06-07
You mean the bar across the top of the display?  Right click on the bottom bar, select New Panel, then you can add what you want to it.

---

### Post by cohs on 2008-06-07
i got lampp uninstalled.

but both toolbars  bottom and top are still gone.  when my system starts up its just my background.   what i did was created a folder by right clicking went into that to usr/bin  and got firefox opened.   so i could try to figure out what was wrong.   but im having no luck

---

### Post by cohs on 2008-06-07
also installed screem before the malfunction

---

### Post by RequinB4 on 2008-06-07
try

```
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &
```

---

### Post by cohs on 2008-06-07
> **RequinB4 said:**
> try

```
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &
```


thank you that worked, but its now saying fastuser switching, mixer, and trash applets had problems   do you know how i can fix that.

---

### Post by cohs on 2008-06-07
i reinstalled the applets now im good to go.  thanks for all the help  :)

---

### Post by gos1 on 2008-06-12
hi I have the same problem . And cannot do anything at all . I mean how can I use this codes i nthe console I cannot even open the console .

---

### Post by jou770d on 2008-06-12
Try using [alt]+[f2] this should bring a 'Run Application' window.
Now type in gnome-terminal and hit enter then try that code.

---

### Post by gos1 on 2008-06-12
alt + f2 does not work either

---

### Post by jou770d on 2008-06-12
Okay, try [ctrl]+[alt]+[f1].
This shold get you a virtual terminal. You would have a black screen with a log in prompt. Enter you user name and password (when you enter your password you won't have any visual feedback) and then try the code.
I hope this works for you.
Once you're done, type in 'exit' to log out and then [ctrl]+[alt]+[f7] to get back to the graphical interface.

---

### Post by producer on 2008-06-12
I am also missing my panel and the one at the bottom too.  I see RequinB4 has posted some code to try, but where do you put it, (I know that's a leading question).  I just can't get a terminal.  This has happened twice in two days.  Last time I had to re-install, but I can't keep doing that.  It's like Ubuntu just isn't ubuntu anymore.  Evolution won't work, knode won't work, firefox works, but seems strange.  Nothing is like it was last week.  I'm very upset.

---

### Post by gos1 on 2008-06-12
I cannot solve that because the gdm has to run to insert this codes . I have to access the console from the desktop .

---

### Post by jou770d on 2008-06-12
Right click on your desktop -> Create Launcher -> Enter any name and as a command enter gnome-terminal. Click ok and you should have a launcher for your terminal.
That's my very last idea.

---

### Post by forger on 2008-06-12
> **producer said:**
>  I just can't get a terminal.  This has happened twice in two days. 
press alt-f2 and execute: gnome-terminal
this should get it working

---

### Post by producer on 2008-06-12
Nothing happens with <alt> <F2> .
<cntl> <alt> <F1> gives me a text login and I can enter command from there.  I tried,
*gnome-session-remove gnome-panel*
and got:   
cannot open display
Run 'gnome-session-remove --help' to see a full list of available command line options.

the *gconftool-2 --recursive-unset /apps/panel*
gave me:
[1] 6488
-bash: gnome: command not found

and then waited without a prompt.  when I pressed <enter> I got:
[1]+  Exit 127   gnome panel

If the first command didn't work the second may be a waste of time, I imagine, but I wanted to be thorough.

The <cntl> <atl> <F7> does bring me back to the GUI, but still without the panel and without the task bar.

Please does anyone have any more ideas?

---

### Post by Lorry ZA on 2008-06-12
Wow i just learnt a valuble lesson always read the post all the way through.....
I was Reading Amarus Post and thought awesome a virtual terminal and didn't bother to look for a way out. Ubuntu 17 Lorry 0

Sorry to go off topic I had a similar problem when i first installed Ubuntu all i did was set my Visual Effects in the apearence back to none and then after applying go back to extra.

Not sure if it will help but give it a try

---

### Post by producer on 2008-06-12
> **Lorry ZA said:**
> Wow i just learnt a valuble lesson always read the post all the way through.....
I was Reading Amarus Post and thought awesome a virtual terminal and didn't bother to look for a way out. Ubuntu 17 Lorry 0

I did that too, I think.  I assumed it would be a Terminal Window and thought I could switch back and forth, I think.  I can master that now.

> **Lorry ZA said:**
> Sorry to go off topic I had a similar problem when i first installed Ubuntu all i did was set my Visual Effects in the apearence back to none and then after applying go back to extra.

Not sure if it will help but give it a try

Uh, how do I get there?  I have no panel and no task bar.

---

### Post by producer on 2008-06-12
Latest information:  I found the directory /usr/share/applications and in there was the file gnome-panel.desktop which if you drag it to the desktop forms a link to the program.  Great, I thought, I'll actually be able to run the program that gives me my panel back.  Well, I found out why I have no panel at least I got an error in a message box that said "There was an error launching the application.  Details: Failed to execute child process "gnome-panel" (No such file or directory).
So there it is.  can I run Synaptic and get this back?  That's what I anm going to try.  Any other ideas still welcomed.

---

### Post by producer on 2008-06-12
GOT IT!  I found the Synaptic package manager in that directory, (/usr/share/applications).   Then when I dragged it to my desktop and double clicked it it asked me for my password which I gave and it ran synaptic for me.  I searched for "gnome-panel" and found that it wasn't installed...HOW DID IT BECOME UNINSTALLED??? ...anyway after in\stalling it I went back to the icon for "Panel" that I had on my desktop, (the gnome-panel function), and ran that.  It hit three errors because "an appelet" was blocking it and I told it to remove the appelet each time and poof, there was my panel and bottom taskbar back again!  That's teriffic, if still a bit of a mystery.
Thanks to all who helped.

---

### Post by Lorry ZA on 2008-06-12
Well done Producer!!! Sorry i wasn't much help :)

---

### Post by producer on 2008-06-12
Ah but sometimes when one is stressed it's nice just to know someone is there and is willing to help.  Oh, and thanks for the "Well Done."  I don't get that as often anymore.  There are other problems with my suystem and I'll deal with them as I can.  Got to get back to work now.

---

### Post by forger on 2008-06-12
> **producer said:**
> HOW DID IT BECOME UNINSTALLED???

A whole lot of things.. probably because of some "fat fingers" :) no offense, but it happened to me dozen of times while installing something to uninstall or break gnome or even the linux kernel package

take care of what you remove/install/upgrade, read carefully what the synaptic or apt-get remove :KS

---

### Post by akxiii on 2008-06-12
> **producer said:**
> GOT IT!  I found the Synaptic package manager in that directory, (/usr/share/applications).   Then when I dragged it to my desktop and double clicked it it asked me for my password which I gave and it ran synaptic for me.  I searched for "gnome-panel" and found that it wasn't installed...HOW DID IT BECOME UNINSTALLED??? ...anyway after in\stalling it I went back to the icon for "Panel" that I had on my desktop, (the gnome-panel function), and ran that.  It hit three errors because "an appelet" was blocking it and I told it to remove the appelet each time and poof, there was my panel and bottom taskbar back again!  That's teriffic, if still a bit of a mystery.
Thanks to all who helped.

Woo worked for me too! I figured out where my fat fingers got in the way X)
I was trying to get rid of all of the evolution crap since I use gmail, and the toolbars have a common data file. bingo bango, thanks for your help

---

### Post by NibbleG on 2008-06-17
Wow, Thank you Producer, I had the same problem a few times.  I'm still pretty green with Ubuntu, and still have a few problems to work out.  I have reinstalled Ubuntu a few times, thinking I had some who broken Ubuntu or there were problems with my ATi drivers.  I still have the compiz white screen problem, but i can tell that my toolbars are back up by rotating my desktop.
I didn't know that the evolution common files were needed by the toolbar.


Nibble

---

### Post by producer on 2008-06-17
Hey good followup guys, (Akxiii & NibbleG),  I gotthe panel back, but I'm still missing my volume control and trash bin.  Other things are being strange as well.  I've been missing a lot of politically sensitive files, but I think I've restored a lot of them from backups. (Another story for another day).  Do any of you know what the file to be restored is, and why the synaptic package manager deletes it when you remove Evolution?  I thought Synaptic's job was to keep track of dependencies so these things don't happen.  OK, I learned a lot about fixing Ubuntu, but the lesson came at a price.  What I'll try to do is restore the required files for evolution one at a time until the problem goes away and then I'll know what file to leave restored.  If it works I'll report back here.
I guess this is officially a bug for synaptic, Right?  Is it documented?  I'm new at this.

---

### Post by jou770d on 2008-06-18
Synaptic doesn't actually forbid uninstalling programs if that will ruin dependencies. It just notifies you what would be deleted as well.
I'm not good at explaining things with words so here's an example:

If you opened Synaptic Package Manager and marked evolution-data-server-common for removal you would have a list of things "to be removed".
Between those you'll find gnome-panel among other things. I've chosen this as an example because it seems to be the critical package that you deleted.
However, I think that, after you restore it you would also have to reinstall all the removed packages.
Here's a list of those packages (not including evolution related ones):
alacarte
ekiga
fast-user-switch-applet
gnome-applets
gnome-panels
libedataserverui1.2-8
ubuntu-desktop

So you should always remember not to click 'ok' before reading what would happen when you do.
I've learnt that the hard way...

I hope that you find this useful.

Edit:
I almost forgot. About the trash and volume control, right click the panel -> add to panel and then chose what you want.

---

### Post by -Outcast- on 2008-07-04
This happened me too after uninstalling Evolution. I understand the concept of synaptec and reading everything. Do we all read license argeements, if we did we probably wouldn't install half the stuff we did. Anyway. 

I think Synaptec should come up with a warning about what can happen in plain english. 

Going back to this thread. I used gnome-panel in terminal after I downloaded it and although it removed my notes everything back to normal. 

Thanks professor

---

### Post by producer on 2008-07-04
> **Amarus said:**
> 
I almost forgot. About the trash and volume control, right click the panel -> add to panel and then chose what you want.

Oh   yes I did that.  That much I know, but it would just tell me there was a problem and refuse to put it back.  I have them now, I've switched to KDE. and uninstalled most of gnome, the parts that I can find.

---

### Post by SpatryX on 2011-06-05
I am relatively new to Linux. I wanted to uninstall evolution in favour of Thunderbird. In doing so, I did not pay attention to what synaptic wanted to remove. My ignorance caused me to loose my panel and a dozen or so grey hairs appeared on top of my head! 

I followed Producer's instructions by adding a link to my desktop for both terminal and synaptic. Then I told synaptic to install gnome-panels and it included the necessary dependencies. Once completed I opened terminal and ran "$ gnome-panel" and it came up. I rebooted and my panel came back just as I left it with all of my customisations intact.

Lesson learned,,, I need to pay close attention to what the package manager is going to remove when I decide to uninstall something. I still have a lot to learn, but I am glad I finally made a PERMANENT switch to Linux. I am using Zorin based on Ubuntu and I have found these community forums to be an invaluable asset. Much better than MicroCrap! 

I would like to express my sincere thanks to everyone who contributes on this forum!

---

### Post by freewaybear on 2011-06-16
> **akxiii said:**
> Woo worked for me too! I figured out where my fat fingers got in the way X)
I was trying to get rid of all of the evolution crap since I use gmail, and the toolbars have a common data file. bingo bango, thanks for your help

Thanks! I did the same thing, and also lost my toolbars, luckily, I had cairo-dock installed for some stupid reason(I usually close it as soon as I reboot,just haven't bothered to remove it) so I had some menu function, but thanks for the  gnome-panel advice!

---

