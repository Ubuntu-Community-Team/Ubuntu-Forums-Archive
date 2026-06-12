---
title: "Devilspie (version 0.13 and greater) s-expressions examples"
date: 2005-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jrib on 2005-12-02
The latest versions of devilspie uses s-expressions instead of xml syntax for the configuration files.  This thread will be an attempt to collect s-expression examples from users so that others can use and learn from them.  Let's try to follow a similar format and be sure to number your s-expressions so that they can easily be referred to if anyone has any questions (browse the ones already posted to make sure you are not reposting). 

This thread should be only for **devilspie versions 0.13 and greater**.  The latest version in the repos is only 0.10.  You can get the latest source for devilspie at [http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie). If you are using a previous version there is already a great [howto]("http://ubuntuforums.org/showthread.php?t=75749") on the forums that you should read.

**Be sure to read:** [/usr/share/doc/devilspie-0.16/README]("http://www.sas.upenn.edu/~ribeiro/ubuntu/README") (substitute 0.16 with the appropriate version).  Most of the names of the logical operations, matchers, and actions should be descriptive enough to know what they do.  If you aren't sure, try it and see!  It would then be really nice if you could report back here to help others out with what you find :D.  Here is a list, which may not be complete, of the possible code (for proper syntax search the examples):

```

  /* Logical operations */
"is"
"contains"
"matches"
  /* Matchers-- these give you some info about the window that opens*/
"window_name"
"window_role"
"window_class"
"application_name"
  /* Actions */
"debug"
"print"
"geometry"
"fullscreen"
"focus"
"center"
"maximize"
"maximize_vertically"
"maximize_horizontally"
"minimize"
"shade"
"unshade"
"close"
"pin"
"unpin"
"set_workspace"
"skip_pager"
"skip_tasklist"
"above"
"below"
"undecorate"
"wintype"

```
Other functions: if, and, or, begin.

And now some sample s-expressions to use in your ~/.devilspie/*.ds files (I'll copy the readme ones for completion).  **When reading these try to think of nested functions and read the innermost parentheses first**:

**1.** ```
(debug)
```
This will run the *debug* action for every window created.  *debug* function will output the window title, geometry, etc. to the terminal window when you run devilspie in a terminal.  This is a good way to determine application names to use in your s-expressions.

**2.** ```
(if (is (application_name) "XMMS") (set_workspace 2) (set_workspace_3))
```
If a window's application_name is "XMMS", the first action, (set_workspace 2), will be run, which will send XMMS to your second workspace everytime you open it.  If (is (application_name) "XMMS") returns false, *if* will run the second action instead, in this case (set_workspace 3).  So all aplications that are not XMMS will show up in your third workspace.

**3.** ```
  (if (matches (window_name) "^Ubuntu.+") (begin maximize (set_workspace 2)))
```
Matches allows you to use regular expressions.  Here, if a window name starts with "Ubuntu" *if* will run the first action, (begin maximize (set_workspace 2)).  This will then maximize those windows and send them to your second workspace.

**4.** ```
(if (or (is (application_name) "gaim") (is (application_name) "xchat")) (pin))
```
If an application has the name "gaim" or an application has the name "xchat", the first action, (pin), will be run.  (pin) will make your window visible on all workspaces.


**List of Tutorials (updated 2-2-2006):**
[LIST]
[*][wolki's S-expression appendix for devilspie]("http://ubuntuforums.org/showthread.php?t=75749")
[*][http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)
[*][sup's ubuntu wiki entry]("https://wiki.ubuntu.com/Devilspie")
[*][xlife tutorial]("http://x2.zuavra.net/index.php/48/")
[/LIST]

---

### Post by souled on 2005-12-04
**5**```
(if (is (application_name) "Terminal") (undecorate (pin (below (skip_tasklist (skip_pager))))))

```

This will make your terminal appear like it is on your wallpaper. In the profile preferences for the terminal uncheck "Show menubar by default in new terminals" in the General tab. In the Effects tab, use the desired transparency. In the Scrolling tab, disable the scrollbar.

You can use the geometry option to change the size of the terminal. To move it, hold alt and drag the window.

Edit: Hmm... It seems for me that when I run devilspie from a terminal, my settings will work for the terminal that devilspie was ran from, but when I open another terminal, devilspie doesn't affect it.

Edit 2: Ok, now when I run devilspie from the terminal, it doesn't affect any currently opened terminals, only ones opened after devilspie was started. I don't know why, haha.

---

### Post by benplaut on 2005-12-04
[QUOTE=souled]**5**```
(if (is (application_name) "Terminal") (undecorate (pin (below (skip_tasklist (skip_pager))))))

```

This will make your terminal appear like it is on your wallpaper. In the profile preferences for the terminal uncheck "Show menubar by default in new terminals" in the General tab. In the Effects tab, use the desired transparency. In the Scrolling tab, disable the scrollbar.

You can use the geometry option to change the size of the terminal. To move it, hold alt and drag the window.

Edit: Hmm... It seems for me that when I run devilspie from a terminal, my settings will work for the terminal that devilspie was ran from, but when I open another terminal, devilspie doesn't affect it.

Edit 2: Ok, now when I run devilspie from the terminal, it doesn't affect any currently opened terminals, only ones opened after devilspie was started. I don't know why, haha.[/QUOTE]

any way to make it so clicking 'show desktop' doesn't hide it? i'm using that s-expression for Conky :)

<<edit>>

also, could someone post the readme? my compile didn't install it :/ (checkinstall)

---

### Post by jrib on 2005-12-04
[QUOTE=souled]**5**```
(if (is (application_name) "Terminal") (undecorate (pin (below (skip_tasklist (skip_pager))))))

```
[/QUOTE]

I didn't realize that you could use the syntax like that.  Is that equivalent to: ```
(if (is (application_name) "Terminal") (begin (undecorate) (pin) (below) (skip_tasklist) (skip_pager))
```

---

### Post by jrib on 2005-12-04
[QUOTE=benplaut]also, could someone post the readme? my compile didn't install it :/ (checkinstall)[/QUOTE]

I've updated the original post with a clickable link

---

### Post by souled on 2005-12-04
[QUOTE=benplaut]any way to make it so clicking 'show desktop' doesn't hide it? i'm using that s-expression for Conky :)

also, could someone post the readme? my compile didn't install it :/ (checkinstall)[/QUOTE]

Not sure how to go about doing that. The readme is included in the source files. I'll attach it anyway. I also attached parser.c which has more information.

[quote=_jason]I didn't realize that you could use the syntax like that. Is that equivalent to[/quote]

I think the readme does it the way I did it, so I just copied the style. Didn't know if could be achieved different ways.

---

### Post by henriquemaia on 2005-12-04
Very nice howto. 
 
I think I'm getting it. 

How about the close action? How do I use it? Or better stating it, how to I make my windows unclosable through the window manager? Is this possible?

---

### Post by benplaut on 2005-12-05
[QUOTE=souled]Not sure how to go about doing that. The readme is included in the source files. I'll attach it anyway. I also attached parser.c which has more information.



I think the readme does it the way I did it, so I just copied the style. Didn't know if could be achieved different ways.[/QUOTE]

yeah... i was hoping there was a more extensive readme :(

---

### Post by Wolki on 2005-12-05
Cool thread, Jason!

Can someone tell me what "print" does? Does it send a screenshot of the window to the printer?

[QUOTE=benplaut]any way to make it so clicking 'show desktop' doesn't hide it? i'm using that s-expression for Conky[/QUOTE]

Not that I know of, I doubt "Never minimize" is in the windowmanager specs and devilspie currently only checks windows on startup and window creation, not on actions performed on windows. -_-

---

### Post by souled on 2005-12-05
[QUOTE=benplaut]yeah... i was hoping there was a more extensive readme :([/QUOTE]

I think the old parser.c from v .14 has a little more information. I was unaware the .16 version only has the list of options. I think v .14 has some other things; you might want to check it out. However, there is still very little explanation given. You just have to try out some expressions and see if they work ;)

---

### Post by foxy123 on 2005-12-06
thanks a lot for this topic. I hope it's gonna be very helpful. I am trying to start using devil's pie and cannot make it work.

I tried firefox, but then decided to test something simpler: mousepad text editor.

So I get devilspie running in the terminal and launch mousepad:
```
Window Title: 'Mousepad'; Application Name: 'mousepad'; Class: 'Mousepad'; Geometry: 1012x667+6+53

```

So I assume that Application Name is 'mousepad'.

So I created ~/.devilspie directory ad put test.ds file their with the following syntax:```
(debug)
(if (is (application_name) "mousepad") (set_workspace 1))
```

So I killed devilspie and launch it again to be on the safe side. Now I launch mousepad from workspace 4, assuming that it will appear on the workspace 1, but it is still on 4. What dod I do wrong?

---

### Post by Wolki on 2005-12-06
[QUOTE=foxy123]
```
(debug)
(if (is (application_name) "mousepad") (set_workspace 1))
```
[/QUOTE]

The expressions look correct. Devil's Pie currently onla parses the first exprssion in a file, put each in a single file and it should work.

---

### Post by foxy123 on 2005-12-06
[QUOTE=Wolki]The expressions look correct. Devil's Pie currently onla parses the first exprssion in a file, put each in a single file and it should work.[/QUOTE]
I've got only one file with this only expression... oh you mean (debug) is a separate expression?

EDIT: it works now, thanks a lot!

---

### Post by sup on 2005-12-17
Hi, I would like to achieve following with Gaim: I would like the buddy list to be in tray unless I call it and the conversation window to stay pinned and minimized. I encounter two problems i cannot really get around:
1)I fail to match the Buddy List, because when I run (debug), it gives this:```
Window Title: 'Buddy List'; Application Name: 'gaim'; Class: 'Gaim'; Geometry: 264x942+17+57

``` it seems to me it is impossible to match window title since I tried all "window_name" "window_role" "window_class" "application_name" to match it but none did. Am I missing something or is it just impossible with current version (0.16)? If I can remember it was possible with 0.10? (debug) for conversation window gives this:
```
Window Title: 'Rogue'; Application Name: 'gaim'; Class: 'Gaim'; Geometry: 510x523+22+79
``` Rogue being a nick I was talking to, so the only difference from Buddy List the window title.
2)If I suceed in matching the Buddy List, how do I send it to tray? When using action "close", (and mathcing application name gaim, so it affects also conversation) it send it to the tray, but it cannot be retrieved from there because everytime I click it in the tray, it is closed once again.

Any ideas?

---

### Post by sup on 2005-12-17
eh, I looked into my old xml config file and found out that conversation can be matched like this:```
(if (is (window_role) "conversation")(ACTIONS))
``` and Buddy List like this: ```
(if (is (window_role) "buddy_list") (ACTIONS))
```. Seems that the old debug file worked somehow better if it found that out:-(.

---

### Post by jrib on 2005-12-17
[QUOTE=sup]...
1)I fail to match the Buddy List
...
[/QUOTE]

I can match the buddy list with:

```

if (is (window_name) "Buddy List")  (pin))

```

Doing what you propose with starting closed, seems to be a bit tougher.  We have to find someway for it to test that the tray icon is open.  Don't know how to accomplish that :P

[edit]okay, I figured out how you can do it.  Install the gaim-extendedprefs packages form universe.  Then you can enable them in plugins.  That'll give you the option to hide the buddy list on startup (near the bottom).  Here is a screen shot: [http://gaim-extprefs.sourceforge.net/extprefs.png](http://gaim-extprefs.sourceforge.net/extprefs.png) .  Be sure to post your finished product if you can get the whole setup to work :)

4 minutes too slow apparently, now that I read Wolki's post

---

### Post by Wolki on 2005-12-17
[QUOTE=_jason]Doing what you propose with starting closed, seems to be a bit tougher.  We have to find someway for it to test that the tray icon is open.  Don't know how to accomplish that :P[/QUOTE]

Gaim has a preference for starting with the Buddy List hidden if you install extended preferences (from eg. synaptic). Works better than trying it with devilspie :)

---

### Post by sup on 2005-12-17
huh, I found out how to do that with devilspie, and it is not difficult at all when you find out what some action means, so:

```
(if (is (window_role) "conversation") (begin pin(minimize)))
```
and in another file:
```
(if (is (window_role) "buddy_list") (begin minimize(skip_tasklist)))
```
makes Gaim conversation stay with you through all workspaces and is minimized when started (I think it is necessary if you dont want to pup it up when you switch workspaces. EDIT:not true, checked out and it does not pop up) and Buddy List start in tray. Buddy List also never goes to taskbar, it goes directly from maximized to tray, but that is just fine with me.  
So the skip_tasklist makes window never appear on a taskbar - which effectively makes application that do not go to tray (krusader for example) unreachable(ALT+TAB does not work) - the only thing I figured out was to kill it with system monitor and then start again without devilspie:-/.


btw:I just found out that although i got extended preferences installed, they somehow arent there (I messed around with compiling gaim by myself, maybe it is for that), I gues I'll just wait for 2.0 version to solve that.
EDIT:a typo

---

### Post by sup on 2005-12-17
```
(if (contains (window_role) "gnome-terminal") (geometry "1000x978+0+25"))

```

Sets geometry of the gnome-terminal to 1000x978+0+25, meaning it is then 1000 pixels wide, 978 heigh, 0 pixels far in x (horizontal) direction from left edge of the display and 25 pixels far in y (vertical) direction form the upper edge of the display. 

It does not apply for already maximized windows, however it does apply for new windows and open but not maximized windows. 
Also, it seems that it is not possible to change values continuously but only descretely. For example, 1000x977+0+25 and 1000x970+0+25 gives me exactly the same output when 1000x978+0+25 and 1000x977+0+25 differ - I would say - by 20 pixels.

Also it seems that (at least on my display which is 1400x1050, but I guess this could be universal?) 25 here is the y size of the upper panel.

---

### Post by sup on 2005-12-17
I wrote a Wiki page about Devil's Pie: [https://wiki.ubuntu.com/Devilspie]("https://wiki.ubuntu.com/Devilspie")
Feel free to improve it, it was my first wiki written from the scratch and I am not a native English speaker either so there are probably some gramatical and conceptual mistakes. Table of contents would be nice too. Also, it would need some examples and actual info how to use Devil's pie, I consider this to be just a beginning.

---

### Post by jrib on 2005-12-17
[QUOTE=sup]I wrote a Wiki page about Devil's Pie: [https://wiki.ubuntu.com/Devilspie]("https://wiki.ubuntu.com/Devilspie")
Feel free to improve it, it was my first wiki written from the scratch and I am not a native English speaker either so there are probably some gramatical and conceptual mistakes. Table of contents would be nice too. Also, it would need some examples and actual info how to use Devil's pie, I consider this to be just a beginning.[/QUOTE]

I added it to the first post for people to check out.  Looks good, thanks!

---

### Post by foxy123 on 2005-12-29
Devil's Pie worked great fro me. However I have recently installed a nightly build of Firefox instead of 1.5 release version. I also have 1.5 Thunderbird installed.

I set devilspie so that firefox should open on the 1st desktop and thunderbird on the second. If I call these programmes from menu or lancher panel it is fine, but if I click on the link in thunderbird, it opens firefox on the second desktop. Moreover it moves firefox to the second desktop if it is already open. Does anyone know why is that?

---

### Post by fabs0028 on 2006-01-01
I started with this version some times ago but i stil can't find an answer to the thing i wanna do :
I'd like to only move all the firefox windows that aren't the main one, i mean for example the download window or the extension window.

But my problem is that i wanna move them for example in the middle of the screen without resizing them :

I made a rule like this one 

```
(if (matches (application_name) "Firefox") and (not matches (window_name) "Firefox$" )( geometry "387x302+161+162" ))
```

But of course it resizes the windows.
So i was wondering if they were an action to only move a window.

I think it is not possible so maybe a good idea would be to be possible to use arguments ... for example the actual size of the window.

Maybe something to add to devil's pie
Thanx a lot for your help and your tutorial which is really helpfull.

Oh by the way as i am on and amd64 ubuntu i made a deb for devil's pie using checkinstall.
I join it so it could be useful for some people :)

---

### Post by jrib on 2006-01-01
[QUOTE=fabs0028]I started with this version some times ago but i stil can't find an answer to the thing i wanna do :
I'd like to only move all the firefox windows that aren't the main one, i mean for example the download window or the extension window.

But my problem is that i wanna move them for example in the middle of the screen without resizing them :

I made a rule like this one 

```
(if (matches (application_name) "Firefox") and (not matches (window_name) "Firefox$" )( geometry "387x302+161+162" ))
```

But of course it resizes the windows.
So i was wondering if they were an action to only move a window.

I think it is not possible so maybe a good idea would be to be possible to use arguments ... for example the actual size of the window.

Maybe something to add to devil's pie
Thanx a lot for your help and your tutorial which is really helpfull.

Oh by the way as i am on and amd64 ubuntu i made a deb for devil's pie using checkinstall.
I join it so it could be useful for some people :)[/QUOTE]

I think you can just omit the first two parameters.  So something like:
geometry "+161+162" should only move the window and not resize it.  You may also want to experiment with the "center" action instead.

---

### Post by fannymites on 2006-01-13
Can anyone tell me how to make a "match all" rule?  I'm trying to force ALL windows to open in the centre of the screen.  I can make individual windows do it but I don't want to make rules for every single app.

---

### Post by benplaut on 2006-01-13
[QUOTE=fannymites]Can anyone tell me how to make a "match all" rule?  I'm trying to force ALL windows to open in the centre of the screen.  I can make individual windows do it but I don't want to make rules for every single app.[/QUOTE]

does the ubiquitous '*' work?

---

### Post by fannymites on 2006-01-13
Unfortunately not.  Neither does the "always" option from the older version of devilspie (or any, all "" " " and many others I've tried)

---

### Post by Azriphale on 2006-01-13
I have not yet used devilspie, but I have an idea of a work-around for that. Its not the best solution, by all means, but it may just work.

what about something like

(if (not matches (application_name) "a_nonexistent_application") .....)

If I read all this correctly, that should do whatever actions you put in there to everything that is not called "a_nonexistent_application", which should be everything.

Or skip the if () section. Don't know if that works tho, due to the fact that i don't have devilspie

---

### Post by fannymites on 2006-01-13
It sounded like a good plan but still not working.

[EDIT]  Worked it out, I need $    ```
(if (matches (application_name) "$") (begin (center)))
```

[EDIT again}  Well that's strange, it was working, I tried about 10 different apps and they all opened centred but after a reboot it won't work anymore.
Also, unfortunately, using devilspie the windows open in a corner somewhere then jump to the centre of the screen which isn't pretty.  I'll keep playing around with it.

---

### Post by jrib on 2006-01-13
[QUOTE=fannymites]It sounded like a good plan but still not working.

[EDIT]  Worked it out, I need $    ```
(if (matches (application_name) "$") (begin (center)))
```

[EDIT again}  Well that's strange, it was working, I tried about 10 different apps and they all opened centred but after a reboot it won't work anymore.
Also, unfortunately, using devilspie the windows open in a corner somewhere then jump to the centre of the screen which isn't pretty.  I'll keep playing around with it.[/QUOTE]

don't use any matcher, just do (I think this should work just like example 1 in my first post does):

```

(center)

```

---

### Post by fannymites on 2006-01-13
That didn't work either but I've REALLY figured it out now ```
(if (matches (application_name) "^.+") and (not matches (window_class) "Gnome-panel" )  (center)))
```
The first bit matches all windows but also makes the panel open in the centre of the secreen.  The second part fixes that.  Thought just putting ```
(if (not matches (window_class) "Gnome-panel" )  (center))
``` wouldn't work.

---

### Post by jrib on 2006-01-14
[QUOTE=fannymites]That didn't work either but I've REALLY figured it out now ```
(if (matches (application_name) "^.+") and (not matches (window_class) "Gnome-panel" )  (center)))
```
The first bit matches all windows but also makes the panel open in the centre of the secreen.  The second part fixes that.  Thought just putting ```
(if (not matches (window_class) "Gnome-panel" )  (center))
``` wouldn't work.[/QUOTE]

Okay I just tried it myself, here is what I noticed:

First I tried ```
(center)
```.  I killed devilspie and started it again.  But it kept seg faulting.  After some experimentation I decided it was due to the fact windows already existed when it tried to center.  So I restarted X.

When I logged into gnome again it worked fine.  Devilspie centered everything-- including the panel.  I thought that's not really what you wanted so I modified it to:

```
(if (not (is (window_class) "Gnome-panel")) (center))
```

[edit]  This is just like yours :)  This seems to work now.  Just remember to restart X, otherwise devilspie will seg fault.  At least for me it did.


What version of devilspie are you using?  Was it seg faulting for you before too?

---

### Post by fannymites on 2006-01-14
I'm using version 0.16-1 on dapper.
Yes, I get the seg faults too but I'm getting them with a few apps on dapper at the moment and I did notice that I need to restart X to see the results of my fiddling.
```
(center)
```still doesn't do anything at all for me but the other code you posted does.
Also, I tried the one I said didn't work - ```
(if (not matches (window_class) "Gnome-panel") (center))
``` does actually work.  I can only assume I made a typo the first time I tried it.

So, to sum up and remove any confusion for anyone that might be searching the forums (as I did for ages), to open all windows in the centre of the screen when using gnome/metacity - ```
(if (not matches (window_class) "Gnome-panel") (center))
``` or ```
(if (not (is (window_class) "Gnome-panel")) (center))
```

---

### Post by souled on 2006-01-17
I'm trying to make the terminal open in a certain spot, but when I use geometry with say, "+30+40", the terminal is unaffected. I can use the geometry command to change the window size, but I can't change the offset. I even tried to use the center command, but it doesn't do anything. Any ideas?

---

### Post by jrib on 2006-01-18
[QUOTE=souled]I'm trying to make the terminal open in a certain spot, but when I use geometry with say, "+30+40", the terminal is unaffected. I can use the geometry command to change the window size, but I can't change the offset. I even tried to use the center command, but it doesn't do anything. Any ideas?[/QUOTE]

Not sure how to do this with devilspie, I haven't been able to get the gnome-terminal to match.  What you can do is modify the terminal command.  It will accept the --geometry option.  So to open it "+30+40", you would change 'gnome-terminal' to 'gnome-terminal --geometry=+30+40'.  Let me know if you ever figure out how to do it in devilspie, I would be interested.

---

### Post by souled on 2006-01-18
Hmm... Well I got it to work. Basically the terminal is hard to match because of the dynamically set title. You have to disable the dynamically set title to make it stay constant. I just name mine "Terminal." This allows me to use application_ name "Terminal" to match it. I just tried puting the center command in a file separate from my main terminal expression, and it works... I don't understand why this is, but whatever. It works!

---

### Post by JurB on 2006-12-20
i installed devilspie and it seems to work: i've got a debug.ds in ~/.devilspie,  when devilspie is run from the terminal it shows the debug output. 
However, i tried adding a firefox.ds with:```
(if (is (application_name) "Firefox") (set_workspace 2))
``` but that doesn't work. Tried it with several other applications using the debug info provided, but i can't get them to work either. Even examples provided in wiki's don't work for me. What am i doing wrong?

---

### Post by jrib on 2006-12-20
> **JurB said:**
> i installed devilspie and it seems to work: i've got a debug.ds in ~/.devilspie,  when devilspie is run from the terminal it shows the debug output. 
However, i tried adding a firefox.ds with:```
(if (is (application_name) "Firefox") (set_workspace 2))
``` but that doesn't work. Tried it with several other applications using the debug info provided, but i can't get them to work either. Even examples provided in wiki's don't work for me. What am i doing wrong?

After adding the .ds file to ~/.devilspie do you restart devilspie?

---

### Post by JurB on 2006-12-21
Yes, i did... even killall devilspie to be sure.
But, i've solved it now: apparently every instance of Firefox had to be closed in order for things to kick in.

---

### Post by Ptero-4 on 2007-03-02
Hi. A question. Does this work with wm`s other than metacity?

---

### Post by foxy123 on 2007-03-03
> **Ptero-4 said:**
> Hi. A question. Does this work with wm`s other than metacity?

yes, it works with all other wms I guess. At least it works fine with xfwm4. It does not work with Beryl/Compiz in a way as they usually have one desktop and several viewports.

---

### Post by SuperAndy on 2007-09-07
weird problem with mine. the panels are not drawn on every deskktop. whichc is a bit odd. even if i use:

```
(if (is (window_class) "Gnome-panel") (pin))
```

this doesn't work. its driving me insane.

---

### Post by High Camp on 2007-09-09
I can't get Devilspie to work. I've searched everywhere (there is a lack of documentation out there). I'm a complete Noob so I'm not sure if the fact that I'm running Xubuntu matters.

I checked and it is installed and it did install the documentation. According to Synaptic I have version .20.2-1 installed.

I've created a folder in my home folder called .devilspie and in it I've put all sorts of test with .ds file extensions. Nothing has worked so far. Oh yeah and I've run devils pie from the command line to start it. Not sure if I needed to? When that didn't work I set up Devilspie as an autostarted application.

Not sure what I'm doing wrong here but I hope someone can help,

Thanks much,

EDIT: Damn, of course as soon as I write this it starts working. I put devilspie -debug in the command line if that somehow would have changed anything.

---

### Post by jeffa10487 on 2007-10-27
(I've got the package installed and functioning correctly.)

I looked through the embedded functions and attributes but I can't seem to figure out how to implement a specific application, any suggestions would be appreciated:

I'm running a virtual machine on my left monitor (secondary, configured through TwinView as "LeftOf") and Ubuntu on my right (primary). 

For some reason, applications open by default beyond the upper left edge of the screen (which I think is some bug in a window manager I installed, I'm not too concerned about it). What I want, though, is to have all applications open in the right monitor, as if the left monitor were "off limits" so it can be reserved to run a virtual machine in full-screen. 

Is there:
a.) a way to start ALL windows on the right monitor, or
b.) A better way to solve the problem?

Thanks,

Jeff

---

### Post by legolas on 2007-11-02
Hey guys.  I am using devilspie for a transparent terminal for my desktop.  I hit the show desktop button, and the terminal disappeared with all the other applicantions that were showing.  All the other applications went down into the panel with a corresponding tab to bring them up again.  Unfortunately the terminal didn't get a tab so I couldn't bring it back.  Anybody know how to bring it back up?
Here is my configuration,
(if
(matches (window_name) "DesktopConsole")
(begin
(set_workspace 4)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utulity")
(geometry "+50+50")
(geometry "640x480")
)
)

Thanks

---

### Post by legolas on 2007-11-06
[show desktop dilema]("http://ubuntuforums.org/showthread.php?t=202249&page=10")
To answer my own question,  I finally found a couple answers.  I wanted to post them both because they are really great, but I could not find the second one again.  One of the answers is found on the 10th page of the above thread.  It works great.  It makes a replacement button for the "show desktop" button.   The other way was dealing with code right in the devilspie configuration, but I lost the page.  I am sure I will find it again, but untill then, the above works like a charm.

---

### Post by High Camp on 2007-11-09
Hi All

I've been playing with Devils Pie a lot tonight and I've learned some things that might help beginners, which I am so correct me if I'm wrong.

1. The files are read in order so if you have two .ds files that will act on the same window only the first will be used. I.E. it seems to go through the list of files in alphabetical order and once it finds a match in one of the files it stops looking.

2. The commands in the .ds files are read in order. So if you say specify the geometry of a window and then specify maximize_vertically the window will end up maximized vertically.

3. The program does not like special characters. For example Skype uses "tm" in the window title but Devils Pie reads this as "?" but if you specify Skype? the window is not found.

That's all, I hope it helps someone.

EDIT: If any Devils Pie developers read this, I have two suggestions for cool features:
1. Allow the execution of a program or shell script as an action so that when a window is created one can, say, open another window, or execute any other command.
2. Create a matcher for processes so one can execute a shell script or move a window when a process starts.

Thanks for listening,

---

### Post by Fab on 2008-02-02
I'm using devilspie + compiz both from the repos, with two monitors using twinview. The left, smaller lcd panel should display the pidgin buddy list, pidgin conversations and sonata. I got nearly everything figured out, except the following:

[[img]http://img409.imageshack.us/img409/4253/screenshotkr9.th.png[/img]](http://img409.imageshack.us/my.php?image=screenshotkr9.png)

above the conversation window, there is a 24px space because of the panel on the other monitor.. I want to get rid of that. the buddy list doesn't have this, because it is maximized vertically. the space on the bottom of the screenshot is not actually shown on the left monitor, because it has a lower resolution..

the second thing I'd like to know is whether there is a way to turn of compiz shadows on specific windows via devilspie, or is there a clean way to do that via ccsm?

my config files are the following:

```
(if (is (application_name) "Pidgin")  
        (begin
                (if (is (window_role) "buddy_list")
                        (begin
                                (undecorate)
                                (skip_tasklist)
                                (geometry "300x767+0+0")
				(maximize_vertically)
				(stick)
                        )
                )
                (if (is (window_role) "conversation")
                        (begin
				(undecorate)
                                (geometry "980x512+300+0")
                        )
                )
		(or (not (is (window_name) "Buddy List"))(not (contains (window_name) "#"))
			(begin
				(geometry "+0+313")
			)
		)
        )
)
```

and

```
(if (is (window_class) "Sonata")
        (begin
                (undecorate)
		(geometry "980x512+300+512")
        )
)
```

---

### Post by Andrewsha on 2008-07-03
Hello!
I can't (focus) Pidgin:
```
(if
    (is (application_name) "Pidgin")
    (begin
        (above)
	(focus)
    )
)
```

As result Pidgin is shown on top but it's not focused.
Howto?

---

### Post by the real omni on 2008-09-28
Hey guys,

I'm trying to use gDevilsPie to make Evolution auto-hide when it's showing the Mail window.

Trouble is that if I just set it to hide windows that contain the word "Evolution" in the title, then it hides the calendar and individual calendar appointment windows.

I have mail-notification set to launch "evolution -c mail" whenever it detects new mail for me to download, and I'd like to have evolution start up hidden in those cases, but I don't want it to start up hidden when I click on the "Calendar" icon on my AWN dock.

Any help would be greatly appreciated! :)

---

### Post by DamjanDimitrioski on 2009-07-09
Hi, I want to make Pidgin's Buddy List to hide each time it starts (maybe I got configuration problems, I tried every plugin, whatever) I need a workaround, I tried this code>

( if 
( and 
( is ( application_name ) "Pidgin" )
( is ( window_name ) "Buddy List" )
) 
( begin 
( close )
( skip_tasklist )
( println "match" )
)
)

it works, but it needs to close the window  only on initial start, not always :D.
Any solutions ?

---

### Post by jrib on 2009-07-09
> **DamjanDimitrioski said:**
> Hi, I want to make Pidgin's Buddy List to hide each time it starts (maybe I got configuration problems, I tried every plugin, whatever) I need a workaround, I tried this code>
[snip]
it works, but it needs to close the window  only on initial start, not always :D.
Any solutions ?
I haven't used devilspie in a while but it sounds like the best thing to do would be if pidgin has an option to do this built-in (don't know) or check out wmctrl.

---

### Post by Neeperand on 2010-01-13
I do a lot of work with terminals, often opening many at a time.  What I want to do is have them open tiled by default.  For example, the first terminal opens in the upper left, the second in the upper right, the third in the lower left and the fourth in the lower right.  A fifth window would open in the upper left again, so basically position = window_count % 4.

Currently I do this by having a shell script that opens 4 terminals with different --geometry options, but what I'd prefer is for each window to figure this out on its own as it opens so I if I only need one window I still won't have to move it.  Is there a way in devilspie to see how many windows of the same type are open and apply different rules accordingly?

Thanks.

---

### Post by VCoolio on 2010-01-13
> **Neeperand said:**
> I do a lot of work with terminals, often opening many at a time.  What I want to do is have them open tiled by default.  For example, the first terminal opens in the upper left, the second in the upper right, the third in the lower left and the fourth in the lower right.  A fifth window would open in the upper left again, so basically position = window_count % 4.

Currently I do this by having a shell script that opens 4 terminals with different --geometry options, but what I'd prefer is for each window to figure this out on its own as it opens so I if I only need one window I still won't have to move it.  Is there a way in devilspie to see how many windows of the same type are open and apply different rules accordingly?

Thanks.

I'd rather use a keybinding for a little script. Something like

```
#!/bin/sh
t=$(pgrep gnome-terminal | wc -l)

case $1 in
    1|5|9) gnome-terminal --geometry etcetc;;
    2|6|10) gnome-terminal etcetc;;
    3|7|11) gnome-terminal etcetc;;
    *) gnome-terminal etcetc;;
esac
```

I haven't tried the above, and it probably can be done in a more clever way, but you'll get the idea.

---

### Post by MG2R on 2010-11-07
Hi,

I have a little problem: I want Evolution Mail to start up automatically on workspace 2. Step one, obviously, was to put Evolution with the startup programs. Step two was to install devilspie, make a .ds-file and put devilspie with the startup programs. The code I used was:
```
(if (is (application_name) "evolution") (set_workspace 2))
```The problem is that devilspie gives this error message: 
```
simon@laptop-simon:/$ devilspie

** (devilspie:2168): WARNING **: Workspace number 2 does not exist

(devilspie:2168): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

```WORKSPACE 2 DOES NOT EXIST??? How is that possible?

Can anyone help?

Thanks!

--EDIT!: After numerous attemps and getting nowhere, suddenly and completely without meaning to do it, I opened the workspace switcher preferences and there it appeared to me that my workspaces where called "Desk 1, Desk 2, ...". After changing them to mere number everything worked splendidly! :)

---

