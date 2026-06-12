---
title: "[Fluxbox]Is it possible to open a terminal on all workspace?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by NotLikingIt on 2008-10-04
Hi, I just got xubuntu and have been playing with fluxbox for almost the entire day today.

In order to get fluxbox to work for me to my liking. I'd like to open a terminal on startup.

I have accomplished that so far, but I'm hoping to be able to open that terminal (using gnome-terminal right now) on all workspaces. 

So I'm thinking maybe I can open 4 different instances of the terminal to my four workspaces on startup, or maybe I can somehow use one terminal and apply some setting to it so it is active on all of my workspaces (like tilda)

Is that how I should approach this? If so, how do I do it
if not, how should I approach to this problem?

Thank you

[solved]
using xcompmgr, I found my terminal mysteriously apperaed on the other workspaces too

---

### Post by ajmorris on 2008-10-04
hi there,
you mentioned you have heard of tilda... it is a very nice CLI, and you can have a control button (f1 is the default) to make it appear... so if you switch desktops, f1 will show it... however, if you dont want to use tilda, some terminals have the option to stick it to all workspaces... gnome-terminal seems not to have the option, there is also an option in compiz to set applications to display on all workspaces, however, since you're using fluxbox, that's out of the question... i'll have a google around, and see what i can dig up for you :)

AJ

---

### Post by elmer_42 on 2008-10-04
I know that in Openbox, you can right-click the taskbar and set the application to display on all workspaces. Do you know of anything like this built into Fluxbox?

---

### Post by NotLikingIt on 2008-10-04
yeah, I tried tilda in hopes of getting a transparent terminal

I did not like the idea having too many *term programs on my linux,lol

Although I don't use compiz, I did get xcompmgr (my friend says this is a lightweight version of compiz, it it didn't cause my computer to go much slower: alot faster than my xp still, hehe)

I was just wondering why my terminal started appearing on my other workspaces, I guess it's xcompmgr then

Thanks for the info

---

### Post by urukrama on 2008-10-05
You can use the [apps file]("http://fluxbox-wiki.org/index.php?title=Editing_the_apps_file"). See here for more info. I haven't used Fluxbox in a while, but I suppose you could use add something like the following to the apps file:

> [app] (gnome-terminal)
        [INDENT][Sticky] {yes}[/INDENT]
 [end]

You could also use [Devil's pie]("http://burtonini.com/blog/computers/devilspie").

---

