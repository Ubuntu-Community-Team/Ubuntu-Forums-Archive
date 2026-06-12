---
title: "ubuntu IDE options for AS3"
date: 2013-01-06
forum: Programming Talk
---

### Post by faceshed on 2013-01-06
I'd like to compile a list of IDEs that work in Ubuntu and you can program AS3 with. So far there's only 3 I know of and only one that I'm really sure works in Ubuntu.

text editors:
Hardcore mode for programming. You just have to get a compiler and get it to turn your perfectly coded text document into a flash file.
Pros:
You look awesome around your programming friends.
Takes almost no ram to use it.
Almost no chance of compatibility conflicts.
Free.
Cons:
Lack of any tools/features whatsoever.

FDT:
This is a plugin for eclipse that allows you to work with AS3. It also disables some normal eclipse features and charges for them.
Pros:
For me it installed and worked fine without much effort.
Easy to get the hang of if you like eclipse.
Free.
Cons:
A good deal of features are disabled for the pay copy.
Hard to get the hang of if you haven't used eclipse. (I imagine anyway)

Flash Develop:
This one I only know of because it failed to run on my windows system.
pros:
Free.
Quite popular.
Cons:
Takes up quite a bit of ram compared to FDT.

That's all I got. Please let me know what IDE you use if you work with AS3 and how it works for you and how it works in Ubuntu. Thanks.

---

### Post by faceshed on 2013-01-20
I've been reading a lot and seams like for some reason next to no one that uses linux also programs with actionscript. But I did find that FDT installs on ubuntu. That's not to say it works. I couldn't get it to do much more then crash and make error messages. Flash Develop does not run on linux without the help of wine.

But then I found geany; My new favourite toy. It has no problems reading and error checking as3, however build commands need to be set up manually. For some reason geany can't find my path to flex so I just put in the full path.
Build: ```
/opt/flex/bin/mxmlc "%d/%f"
```Build and backup: ```
rm "%d/%e.bak" | cp "%d/%f" "%d/%e.bak" | /opt/flex/bin/mxmlc "%d/%f"
```Run: ```
firefox "%d/%e.swf"
```That's it so far. Run leaves a terminal window open after each use and I failed to get a build and run command.  [/opt/flex/bin/mxmlc "%d/%f" | firefox "%d/%e.swf"] looks like it works but really just starts up flex and then launches the old .swf before it's done. No clue how to fix that any of that, but it works well enough for me.

I also still can't compile my old projects because they have more then one class and I don't know how to get them to find each other. I use to just let my IDE handle all that linking junk so I don't know squat about it... :(

I'll keep messing with it and post my findings here.

---

