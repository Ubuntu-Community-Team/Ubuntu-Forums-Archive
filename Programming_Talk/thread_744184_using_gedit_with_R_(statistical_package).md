---
title: "using gedit with R (statistical package)"
date: 2008-04-03
forum: Programming Talk
---

### Post by mavicdog on 2008-04-03
Hi,
I used to use kate in KDE to run/edit my R scripts. I was able to test bits of code on fly by piping to console. I have recently switched to gnome and I am trying to do this with gedit but its not working (there doesn't seem to be a pipe mechanism).
I have managed to use the external tools to open R but I have been unable to run any of my code in that window. Any ideas on how I can do this? I guess the same would apply for any scripting language - octave or python (how does the python window work?)
M.

---

### Post by Zugzwang on 2008-04-03
Erm, what's wrong with Kate? You can still use it in GNOME (unless you're *really* low in memory) and the extra computation time imposed by using a KDE application in GNOME summed up for working with it for ten years are unlikely to exceed the amount of time you spent for getting used to gedit.

Or did I miss some point?

---

### Post by mavicdog on 2008-04-03
No you have missed nothing. I tried kate again but I am note getting an embedded terminal. probably because it is expecting konsole and not the gnome terminal. I don't know how to fix that. Maybe if I install konsole....

Ok I installed konsole and now kate works the way I want it to. 

BTW I also managed to create a new external tool in gedit so that I could send selected code to R.
the command is R --no-save (or --vanilla or --save) and the input is current selection and the output is the bottom pane. I am able to send the code, have it be evaluated and have the output come up in the bottom pane but the variables don't persist. I can't just run a subsequent bit later and expect that the variables are remebered.

---

### Post by Wybiral on 2008-04-03
You need an embedded terminal in Gedit? If that's all you're asking, there's a plugin for that.

---

### Post by mavicdog on 2008-04-03
No. I have the embedded terminal but the code I am writing does not go to the terminal when I want to test it. There seems to no communication between Gedit and the embedded terminal.

---

### Post by Wybiral on 2008-04-03
> **mavicdog said:**
> No. I have the embedded terminal but the code I am writing does not go to the terminal when I want to test it. There seems to no communication between Gedit and the embedded terminal.

Yeah, it's just a terminal. Save the file, navigate to that folder (in the terminal), and use R like you normally would (from the terminal). Gedit is just a text editor, and the terminal is just a terminal.

---

### Post by euler_fan on 2008-04-03
If you're doing lots of R code it might be worth it to package it up and install the package, in which case having the ability to pipe to the terminal becomes somewhat less important, especially if you have segmented your code into lots of little script files for ease of management.

---

### Post by danded on 2009-09-08
Hi,
as I said in this thread ([http://ubuntuforums.org/showthread.php?t=668688](http://ubuntuforums.org/showthread.php?t=668688)), I have made a simple plug-in for gedit and R here: [http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)
Hope it'll be useful for some (be warned: it's not a full GUI but just a wrapper for the R console!)

---

### Post by TheStatsMan on 2009-09-08
I just gave the gedit plugin a  whirl. It works really well. It would be nice if it also worked with the extension .R though rather than just .r

---

### Post by danded on 2009-09-09
> **TheStatsMan said:**
> I just gave the gedit plugin a  whirl. It works really well.

Thanks!

> **TheStatsMan said:**
>  It would be nice if it also worked with the extension .R though rather than just .r

What do you mean by this? The plug-in itself does not look at the type of the current file (i.e, it can do its tricks - like sending the line, defining blocks, etc - whatever file you have opened in gedit). 

But if you are referring to syntax highlighting, gedit takes care of that and I *think* there's a way of telling gedit to use the R scheme for .R files as well (for a per file mode, you can go to View->Highlight mode->Scientific->R or View->Highlight mode->Scripts->R depending on the gedit version, as far as I can tell).

Best,
Dan

---

### Post by TheStatsMan on 2009-09-09
Yes, I just meant for the syntax highlighting. It is not something I am really fussed about the only reason I even mentioned it was because it was the first extension I tried with my test code. Thanks for the info though.

---

### Post by danded on 2009-09-10
> **TheStatsMan said:**
> Yes, I just meant for the syntax highlighting. It is not something I am really fussed about the only reason I even mentioned it was because it was the first extension I tried with my test code. Thanks for the info though.

I looked around a bit and it seems that you can either use the per-file settings (and gedit seems to remember the settings) or add a new mime type as for example described here (I haven't tested it though):
[http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?Highlighting_In_Gedit](http://wiki.linuxcnc.org/cgi-bin/emcinfo.pl?Highlighting_In_Gedit)

Hope this helps...

---

### Post by alakshma on 2009-10-04
Thanks a bunch for this plugin danded. You took away the only reason I was considering KDE! Esp. after the option to setup my own keyboard shortcuts (ver. 0.4) this plugin rocks! There's only one more thing that would make it totally awesome (and I know I'm probably being greedy here :)) - is it possible to run rgedit/gedit with the terminal separate from gedit/rgedit? I want to be able to have my code and output window side-by-side rather than one on top of another? This becomes more important on vertically challenged monitors (such as my laptop) that happen to have enough pixels but not enough vertical inches :). I've posted this on your sourceforge site too so apologize in advance for the multiple posts.

---

### Post by danded on 2009-10-07
> **alakshma said:**
> Thanks a bunch for this plugin danded. You took away the only reason I was considering KDE! Esp. after the option to setup my own keyboard shortcuts (ver. 0.4) this plugin rocks! There's only one more thing that would make it totally awesome (and I know I'm probably being greedy here :)) - is it possible to run rgedit/gedit with the terminal separate from gedit/rgedit? I want to be able to have my code and output window side-by-side rather than one on top of another? This becomes more important on vertically challenged monitors (such as my laptop) that happen to have enough pixels but not enough vertical inches :). I've posted this on your sourceforge site too so apologize in advance for the multiple posts.

Hi,
thanks for the suggestion -- seems really useful. I just uploaded v0.5 (but it might take a while for SF to update the project page) and I added this feature. Basically, you can toggle at any time between attached (docked, the default) and detached (independent top-level window) using the menu (or closing the detached R console). It seems to work pretty well on my machine (the R sessions are smoothly transferred between the two states so you don't need to and reload the workspaces).
I hope this is what you had in mind, 
best,
Dan

---

### Post by alakshma on 2009-10-07
Man, you're absolutely awesome. That was quick! Thanks once again.

One quirk I noticed with the latest version. If I enable the 'start R console detached' option in the plugin and keep the 'start R console automatically' disabled, the console window that opens up when I start R is greyed out completely...does not display the output. R is still working though, I'm able to call objects from the workspace using code (e.g. showData brings up the dataset using Tcl/Tk) but am unable to see the output on the console. This does not happen if both the 'start R console automatically' AND 'start R console detached' options are left unchecked. Of course, that means the user has to manually detach the console each time the plugin is used. For me, its no problem at all since I usually start this once in a day and keep it running throughout the day but just something that you can look into.

BTW, I'm using Linux Mint 7 (32 bit) with compiz enabled.

---

### Post by danded on 2009-10-07
> **alakshma said:**
> Man, you're absolutely awesome. That was quick! Thanks once again.

One quirk I noticed with the latest version. If I enable the 'start R console detached' option in the plugin and keep the 'start R console automatically' disabled, the console window that opens up when I start R is greyed out completely...does not display the output. R is still working though, I'm able to call objects from the workspace using code (e.g. showData brings up the dataset using Tcl/Tk) but am unable to see the output on the console. This does not happen if both the 'start R console automatically' AND 'start R console detached' options are left unchecked. Of course, that means the user has to manually detach the console each time the plugin is used. For me, its no problem at all since I usually start this once in a day and keep it running throughout the day but just something that you can look into.

BTW, I'm using Linux Mint 7 (32 bit) with compiz enabled.

True, I reproduced it, thanks! I hope I fixed it in 0.6 uploaded a couple of minutes ago. Also fixed there some other small issues as well and added a menu item o close down the whole R console thing, in case anybody wants that :)

---

### Post by alakshma on 2009-10-07
Thanks man. Problem solved....no more greyed out screens. Have posted some comments on the sourceforge site that relate to other minor improvements possible but already this plugin rocks!

Cheers!

---

### Post by Can+~ on 2009-10-07
I've been learning R recently, and I will give a try too.

edit: pretty good actually. My only complaint (for now) is that I want to open a file on a local folder, like:

[PHP]datos <- sort(mapply(c, read.csv("datos-agrup.csv")))[/PHP]

But it can't find it because I'm using relative paths, it would be nice that, when opening a .R file, it would automatically setwd() where my current R script is located.

This and the gedit-latex-plugin is like statistician's heaven.

---

### Post by danded on 2009-10-08
> **alakshma said:**
> Thanks man. Problem solved....no more greyed out screens. Have posted some comments on the sourceforge site that relate to other minor improvements possible but already this plugin rocks!

Cheers!

Hi,
thanks for pointing these out: v0.6.1 is out :)
Best

---

### Post by danded on 2009-10-08
> **Can+~ said:**
> I've been learning R recently, and I will give a try too.

edit: pretty good actually. My only complaint (for now) is that I want to open a file on a local folder, like:

[php]datos <- sort(mapply(c, read.csv("datos-agrup.csv")))[/php]But it can't find it because I'm using relative paths, it would be nice that, when opening a .R file, it would automatically setwd() where my current R script is located.

This and the gedit-latex-plugin is like statistician's heaven.

This is a nice suggestion, but the only issue I see is that it is difficult to see which R source file tab goes with which R console tab, if there's more than one. I was thinking about this scenario when I started designing this plug-in and a perfect solution would probably be to assign source file tabs to R console tabs and vice-versa but I decided early on that this would be too heavy for a relatively small issue (of course, this is my feeling).

Moreover, you can manually change the working folder of an R tab by right clicking inside it and using the "Change R's working folder" menu entry. Personally, I always use paths relative to the home ~, but that's me :)

Hope this helps...

---

### Post by alakshma on 2009-10-09
Thanks! Very quick once again. Tried out v0.6.1 and it looks good. As far as I'm concerned its got pretty much everything anyone needs to get working with R under gnome. Of course you can add more to it and take it closer to Tinn-R or RKward but this plugin is right now (IMHO at least) at the sweet spot between lightness/speed, effectiveness and power. Way to go!

---

### Post by danded on 2009-10-09
> **alakshma said:**
> Thanks! Very quick once again. Tried out v0.6.1 and it looks good. As far as I'm concerned its got pretty much everything anyone needs to get working with R under gnome. Of course you can add more to it and take it closer to Tinn-R or RKward but this plugin is right now (IMHO at least) at the sweet spot between lightness/speed, effectiveness and power. Way to go!

Well, probably the only three things I might want to add, if they are useful, are:
1. true colors in the terminal and/or prompt, but as far as I can tell, it's either going to be a hack or a rewrite of the R shared library terminal wrapper, both of which involve a lot of work and a high probability of failure
2. the ability to have the R consoles not only as tabs but also to tile them vertically or horizontally -- this shouldn't be too hard to do and would give some advantages when working with two related R scripts and want to quickly compare the outputs
3. the ability to transfer variables between R consoles (basically, export them to a temp file and read this file in the source console) -- this might be useful when processing/debugging the results of one script in another.

So, any votes on these?

I would vote now:
1. maybe not
2. yes
3. yes

---

### Post by alakshma on 2009-10-09
> **danded said:**
> Well, probably the only three things I might want to add, if they are useful, are:
1. true colors in the terminal and/or prompt, but as far as I can tell, it's either going to be a hack or a rewrite of the R shared library terminal wrapper, both of which involve a lot of work and a high probability of failure
2. the ability to have the R consoles not only as tabs but also to tile them vertically or horizontally -- this shouldn't be too hard to do and would give some advantages when working with two related R scripts and want to quickly compare the outputs
3. the ability to transfer variables between R consoles (basically, export them to a temp file and read this file in the source console) -- this might be useful when processing/debugging the results of one script in another.

So, any votes on these?

I would vote now:
1. maybe not
2. yes
3. yes
Cool. I like #2 and #3 too. Esp. #2. The only extra that might make it better is the ability to assign custom kbd shortcuts such that I can have two/three consoles tiled and depending on which one I want to send a selection to, I can press a different key combo. For instance, I use Alt+F6 to send a code selection to the console...if I could use Alt+F7 and Alt+F8 to send it to console 2 and console 3 respectively, I retain a lot of control from the kbd directly on what happens on screen.
#3 is also good. My analyses are not complicated enough yet for me to use this feature extensively but I can see some value here. Not sure whether #1 is that much of a necessity.
One thing I failed to mention earlier and just noticed - starting the first R console is, as of now, completely mouse-driven...don't think there are any keyboard options for that...maybe I'm mistaken. I know that starting a new console can be done via kbd shortcuts but appears that this is not possible for the very first console. Of course, one could always set defaults such that the console opens up each time gedit starts but that would be (I think) an overkill.

---

### Post by It_newbiie on 2009-10-17
Hello **danded** and [B]alakshama
[/B]
First thx a bounch for developing this Rgedit, it is great:)
Second, great suggestion abt the seperat terminal windows for R-console.

I have a problem using this great feature though. I have installed the latest version v.0.6.1 on my ubuntu hardy, but I cant make it work, when I detach, the console window on the botton just went grey, and no additional window pops up. I have tried to install the previous version v.0.6, but same problem.
I have read many of your entries, but havent got to solve the issue yet, please HELP!

---

### Post by danded on 2009-10-17
> **It_newbiie said:**
> Hello **danded** and [B]alakshama
[/B]
First thx a bounch for developing this Rgedit, it is great:)
Second, great suggestion abt the seperat terminal windows for R-console.

I have a problem using this great feature though. I have installed the latest version v.0.6.1 on my ubuntu hardy, but I cant make it work, when I detach, the console window on the botton just went grey, and no additional window pops up. I have tried to install the previous version v.0.6, but same problem.
I have read many of your entries, but havent got to solve the issue yet, please HELP!

Hi,
I'm glad you like it!
I reproduced your problem under Hardy (I did not have one installed beforehand :) ) and it was due to the fact that GTK+ there is 2.12 while I was using a method (gtk.Dialog.get_cointent_area()) which requires pygtk >= 2.14. I fixed it however and seems to work well on my fresh VirtualBox install of Hardy -- please let me know if it works on your machine as well...
I just uploaded version 0.6.2 on SF but, as usual, it will probably take them a while to update the page...
Best,
Dan

---

### Post by danded on 2009-10-19
> **alakshma said:**
> Cool. I like #2 and #3 too. Esp. #2. The only extra that might make it better is the ability to assign custom kbd shortcuts such that I can have two/three consoles tiled and depending on which one I want to send a selection to, I can press a different key combo. For instance, I use Alt+F6 to send a code selection to the console...if I could use Alt+F7 and Alt+F8 to send it to console 2 and console 3 respectively, I retain a lot of control from the kbd directly on what happens on screen.

I've been struggling the last week with this and it looks like gtk does not make implementing this particularly easy :(. In fact, it looks like I need to rewrite the whole thing and I don't really have the time for that, esp. given that it works now. So, I'm afraid I was too optimistic about 2 and it'll have to wait for a while...

> **alakshma said:**
> One thing I failed to mention earlier and just noticed - starting the first R console is, as of now, completely mouse-driven...don't think there are any keyboard options for that...maybe I'm mistaken. I know that starting a new console can be done via kbd shortcuts but appears that this is not possible for the very first console. Of course, one could always set defaults such that the console opens up each time gedit starts but that would be (I think) an overkill.

I can't really reproduce that: I just defined Ctrl+Shift+N for defining a new tab and disabled R console to autostart and when I press Ctrl+shift+N inside a fresh gedit, a new (the first) R tab is created as expected. Are you sure your new tab shortcut works at all (it might happen to be already defined and as the R plugin is the last one to get the keycodes, that somebody else might have already processed it -- I'm guessing now).

---

### Post by It_newbiie on 2009-10-19
Hey Danded

you are the best!! After I installed the version 0.6.2..the detach window feature works like a charm in my hardy.. THX 1000 ^^

---

### Post by alakshma on 2009-10-21
> **danded said:**
> I've been struggling the last week with this and it looks like gtk does not make implementing this particularly easy :(. In fact, it looks like I need to rewrite the whole thing and I don't really have the time for that, esp. given that it works now. So, I'm afraid I was too optimistic about 2 and it'll have to wait for a while...


Hey, no problem. Personally, this was something that would be a good extension provided the time/effort on it was not huge. Considering that rGedit works great as it is don't see any real need to get this implemented :)



I can't really reproduce that: I just defined Ctrl+Shift+N for defining a new tab and disabled R console to autostart and when I press Ctrl+shift+N inside a fresh gedit, a new (the first) R tab is created as expected. Are you sure your new tab shortcut works at all (it might happen to be already defined and as the R plugin is the last one to get the keycodes, that somebody else might have already processed it -- I'm guessing now).
 
You're right. My bad. I think my custom keyboard shortcut was already being used by gedit for something else. Once I changed it back to the one you had initially assigned, it worked fine (v.6.1). Thanks and apologies.

---

### Post by tsphere on 2010-05-31
Thanks for this plugin. It is working great.

Just a question: 
Is there any way to run more than 3 workspaces in parallel? If this would mean running several instances of gedit, I'd like to know how.

---

### Post by danded on 2010-05-31
> **tsphere said:**
> Thanks for this plugin. It is working great.

I'm glad you like it :)

> **tsphere said:**
> Just a question: 
Is there any way to run more than 3 workspaces in parallel? If this would mean running several instances of gedit, I'd like to know how.

Do you mean that more than three tabs with R consoles would be useful? If so, this is not possible atm except if you start a new gedit session but I could try to add more if that's useful (when I implemented it I thought that 3 would be enough but apparently is not :))...

---

### Post by tsphere on 2010-07-08
Thanks for your reply!
more would be very useful, especially since I can't seem to open new gedit instances, only new tabs.
Is there an easy way of opening an instance?

Also, I noticed the color coding isn't the most convenient. For instance, I like to be able to follow the different parenthesis (I have lines with half a dozen or so), and also have functions colored differently than objects etc. Right now it's three colors or so, and it's not very informative.
Is this possible within gedit?

---

### Post by danded on 2010-07-08
> **tsphere said:**
> Thanks for your reply!
more would be very useful, especially since I can't seem to open new gedit instances, only new tabs.
Is there an easy way of opening an instance?

I'm working on allowing more than 3 R consoles but it will take a while as my time is really limited and it's not obvious given that I have to change quite a bit of code :)

Concerning starting a new instance: on my Fedora 13 Xfce
```
gedit --new-window
```works (I used ```
gedit --help
``` to find it).

> **tsphere said:**
> Also, I noticed the color coding isn't the most convenient. For instance, I like to be able to follow the different parenthesis (I have lines with half a dozen or so), and also have functions colored differently than objects etc. Right now it's three colors or so, and it's not very informative.
Is this possible within gedit?

I am sorry but these colors are set within gedit and I have no idea how to alter the coloring scheme used for R files. I remember seeing something on the net at one point but I think that doing a google might help. Anyway, if you manage to find a way please post it back and I'll make sure to put on the project's wiki...

Best,
Dan

---

### Post by gagea on 2010-10-05
> **danded said:**
> I'm working on allowing more than 3 R consoles but it will take a while as my time is really limited and it's not obvious given that I have to change quite a bit of code :)

Concerning starting a new instance: on my Fedora 13 Xfce
```
gedit --new-window
```works (I used ```
gedit --help
``` to find it).



I am sorry but these colors are set within gedit and I have no idea how to alter the coloring scheme used for R files. I remember seeing something on the net at one point but I think that doing a google might help. Anyway, if you manage to find a way please post it back and I'll make sure to put on the project's wiki...

Best,
Dan

Hello Dan, 

I am trying to install rgedit on ubuntu. I add [FONT=monospace]"deb [/FONT][http://www.kaduk.net/~mateusz/gedit-r-plugin]("http://www.kaduk.net/%7Emateusz/gedit-r-plugin")[FONT=monospace] ./[/FONT]" to repositories like 1.png (attached). After updating with sudo apt-get update, I run [FONT=monospace]apt-get install gedit-r-plugin. This is outcome:

ubuntu@ubuntu:~$ sudo apt-get install gedit-r-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gedit-r-plugin: Depends: gedit (>= 2.30.0) but 2.28.0-0ubuntu2 is to be installed
E: Broken packages

I really want to use rgedit with R. The descriptions seems to be what I need. I want to be able to write my codes/functions in rgedit and with a short-key, send it to R consul on the terminal to be executed. 

Could you please help me to set it up. 

Sorry if it is very simple.

Thanks, Gagea


[/FONT]

---

### Post by danded on 2010-10-06
> **gagea said:**
> Hello Dan, 

I am trying to install rgedit on ubuntu. I add [FONT=monospace]"deb [/FONT][http://www.kaduk.net/~mateusz/gedit-r-plugin]("http://www.kaduk.net/%7Emateusz/gedit-r-plugin")[FONT=monospace] ./[/FONT]" to repositories like 1.png (attached). After updating with sudo apt-get update, I run [FONT=monospace]apt-get install gedit-r-plugin. This is outcome:

ubuntu@ubuntu:~$ sudo apt-get install gedit-r-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gedit-r-plugin: Depends: gedit (>= 2.30.0) but 2.28.0-0ubuntu2 is to be installed
E: Broken packages
[/FONT]

I will fwd this to Mateusz (he maintainer of the Debian package) and see what he thinks. 
[FONT=monospace] 
[/FONT]> **gagea said:**
> [FONT=monospace]I really want to use rgedit with R. The descriptions seems to be what I need. I want to be able to write my codes/functions in rgedit and with a short-key, send it to R consul on the terminal to be executed. 

Could you please help me to set it up. 

Sorry if it is very simple.

Thanks, Gagea


[/FONT]

Alternatively, you can always install manually the "upstream" version from sourceforge ([http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)) -- it's quite easy and described in the readme included in the package, you just need to make sure to install the required dependencies (gedit, gedit-plugins, python, python-vte... and, of course, R -- either using the package manager or compiled by hand). 

Please, let me know if you have any troubles.

Best,
Dan

---

### Post by gagea on 2010-10-06
> **danded said:**
> I will fwd this to Mateusz (he maintainer of the Debian package) and see what he thinks. 
[FONT=monospace] 
[/FONT]

Alternatively, you can always install manually the "upstream" version from sourceforge ([http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)) -- it's quite easy and described in the readme included in the package, you just need to make sure to install the required dependencies (gedit, gedit-plugins, python, python-vte... and, of course, R -- either using the package manager or compiled by hand). 

Please, let me know if you have any troubles.

Best,
Dan

The manual installation did not work for me.  "R Integration" plug-in from gedit reference doe not appear there.  Is there another way to activate R Integration plugin?

Thanks

Gagea

---

### Post by danded on 2010-10-06
> **gagea said:**
> The manual installation did not work for me.  "R Integration" plug-in from gedit reference doe not appear there.  Is there another way to activate R Integration plugin?

Thanks

Gagea

Hi,

Did you put the files in the correct folder? Then probably you need some dependencies... could you please run gedit from a terminal and tell me what messages do you get there - if any - when trying to activate the rgedit plugin?

Dan

---

### Post by gagea on 2010-10-06
> **danded said:**
> Hi,

Did you put the files in the correct folder? Then probably you need some dependencies... could you please run gedit from a terminal and tell me what messages do you get there - if any - when trying to activate the rgedit plugin?

Dan

Hello Dan,

Thanks for reply. It was my problem. It was it in the wrong folder. Now it is working. Wow, this is great. thanks for that. By the way, do you have time  answer to this question:

I have huge dataset like the bellow (prepared in notepad in txt format: 

31;39;00N+65;40;00E T
36;31;42N+69;04;21E T
34;10;00N+69;41;00E T
34;34;00N+69;06;00E T
31;40;00N+65;44;00E T
35;00;00N+69;07;00E T
34;00;00N+69;53;00E T

These are geographical coordinates, degree minute, seconds. 
  latitude      longitude
31;39;00N+65;40;00E T

I would like to plot them on the map. I would like to know to how separate longitude and longitude from each other and put them into two different columns and then transform the degree minute second into decimal format. 

Your help very appreciated.

Gagea

---

### Post by danded on 2010-10-07
> **gagea said:**
> Hello Dan,

Thanks for reply. It was my problem. It was it in the wrong folder. Now it is working. Wow, this is great. thanks for that.


I'm glad it worked!

> **gagea said:**
> By the way, do you have time  answer to this question:

I have huge dataset like the bellow (prepared in notepad in txt format: 

31;39;00N+65;40;00E T
36;31;42N+69;04;21E T
34;10;00N+69;41;00E T
34;34;00N+69;06;00E T
31;40;00N+65;44;00E T
35;00;00N+69;07;00E T
34;00;00N+69;53;00E T

These are geographical coordinates, degree minute, seconds. 
  latitude      longitude
31;39;00N+65;40;00E T

I would like to plot them on the map. I would like to know to how separate longitude and longitude from each other and put them into two different columns and then transform the degree minute second into decimal format. 

Your help very appreciated.

Gagea

Well, I always separate columns with TAB and then read the file with read.table(). Concerning spatial coordinates, this [http://finzi.psych.upenn.edu/R/library/sp/html/DMS-class.html](http://finzi.psych.upenn.edu/R/library/sp/html/DMS-class.html) might help.

Dan

---

