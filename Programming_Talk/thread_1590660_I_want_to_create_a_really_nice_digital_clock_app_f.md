---
title: "I want to create a really nice digital clock app for Ubuntu"
date: 2010-10-08
forum: Programming Talk
---

### Post by Petrockstealer on 2010-10-08
I've been using Kubuntu and Ubuntu for a couple years off and on now. I can't stop wondering- "how did they do that? how did they do that?". A short aside, I mean I notice it's all kind of generic 'this broad stroke does this'. However the complexity seems to be ever so high when I look at a scrolling terminal window and then I think about layers and all the good people that must have worked hard. So, I guess my question is how do I get to know this elite core... can I have the irc password? I want to create a really nice digital clock for Ubuntu.

ps I program java and have a little too much free time

pss I lost my old account

---

### Post by Petrockstealer on 2010-10-08
Am I in the right place?

---

### Post by worksofcraft on 2010-10-08
> **Petrockstealer said:**
> Am I in the right place?
Yeah
A nice digital clock would be cool although there is quite a good one on the launcher panel. I wrote a speaking clock in Python just for fun, but as you are into Java I'll attach my digital stop watch applet with a little web page I wrote back when Java was quite new.

I also wrote one in pizza, the extended Java language and I definitely prefer Pizza to Java... but IDK if you would like the source code then I'll have to go look thru my floppy disks in the garage :(

---

### Post by Petrockstealer on 2010-10-08
Thank you but this isn't what I wanted. I'm not saying I'm stopping at digital clocks, on the contrary, I want to understand Linux at a deeper level, write the digital clock in whatever gedit is written in. I want to download the source for tommynote and change that annoying icon. I want to program a Spades game application in binary. Can you dig?

---

### Post by worksofcraft on 2010-10-08
> **Petrockstealer said:**
> Thank you but this isn't what I wanted. I'm not saying I'm stopping at digital clocks, on the contrary, I want to understand Linux at a deeper level, write the digital clock in whatever gedit is written in. I want to download the source for tommynote and change that annoying icon. I want to program a Spades game application in binary. Can you dig?

Ah... well if you want get into various Linux apps you are in luck because most of them are open source and most of it uses a standard way of building and installing and quite a lot of it is written in C or C++ which is not that hard for a competent Java programmer to follow... so you might as well dig in:
[LIST]
[*]down load the source code of an app that interests you
[*]make sure you have the necessary developer tools nstalled
[*]run the configure and make scripts
[*]check that the app you built works
[*]start hacking
[*]come back and ask specific questions when you run into problems
[/LIST]

---

### Post by worseisworser on 2010-10-08
> **Petrockstealer said:**
> Thank you but this isn't what I wanted. I'm not saying I'm stopping at digital clocks, on the contrary, I want to understand Linux at a deeper level, write the digital clock in whatever gedit is written in. I want to download the source for tommynote and change that annoying icon. I want to program a Spades game application in binary. Can you dig?

gedit is written in C, but you can use several languages to create similar applications on Linux.

Deluge, [http://dev.deluge-torrent.org/wiki/Screenshots](http://dev.deluge-torrent.org/wiki/Screenshots) , is written in Python for instance.

---

### Post by Vox754 on 2010-10-08
> **Petrockstealer said:**
> Am I in the right place?
Well, you do seem interested in programming, it's just that your opening post does not make sense, at all.

Please understand that programming requires discipline, and learning a lot by yourself, it's not a task for random hax0rs wannabes.

Take a look at this thread: [Participating in Ubuntu development](http://ubuntuforums.org/showthread.php?t=1590052)

The original poster in that thread also wants to develop for Ubuntu, but he seems a little bit more centered and measured than you.

---

### Post by worseisworser on 2010-10-09
> **Petrockstealer said:**
> I've been using Kubuntu and Ubuntu for a couple years off and on now. I can't stop wondering- "how did they do that? how did they do that?". A short aside, I mean I notice it's all kind of generic 'this broad stroke does this'. However the complexity seems to be ever so high when I look at a scrolling terminal window and then I think about layers and all the good people that must have worked hard. So, I guess my question is how do I get to know this elite core... can I have the irc password? I want to create a really nice digital clock for Ubuntu.

ps I program java and have a little too much free time

pss I lost my old account

Sometimes it makes sense starting where you are; creating an island around you instead of starting at the "core" of something. ..and after a while, you realize there really is no core; this thing is a [graph]("http://en.wikipedia.org/wiki/Graph_(mathematics)"); not a [tree]("http://en.wikipedia.org/wiki/Tree_(data_structure)").

Being good does not mean knowing it all top-to-bottom or bottom-to-top; that won't last, no; being good means being a good navigator and strategist.

A digital/binary clock; [http://js1k.com/demo/258](http://js1k.com/demo/258) .. works in Ubuntu; hit *view source and description*, at the top, to see proper formatted code.

---

### Post by Petrockstealer on 2010-10-09
Thankyou wiw, and everyone else for your input. So I think I'll spend a little while learning C. Then I guess you learn gnome right?  There's about 100 things I need to do lately and one of them was sleep, so...

I made a list mentally of what I would need in order to put together the best digital clock for Ubuntu:

Vectors
2 styles - digital cool blue and odometer
C++
gnome-compatibility so it can sit locked in the upper-right corner

that's about all I can think of. It would be resizable. Maybe have an alarm setting with the computer beep, that would be fun. Do new computers still have a speaker?

---

### Post by worksofcraft on 2010-10-17
> **Petrockstealer said:**
> Thankyou wiw, and everyone else for your input. So I think I'll spend a little while learning C. Then I guess you learn gnome right?  There's about 100 things I need to do lately and one of them was sleep, so...

I made a list mentally of what I would need in order to put together the best digital clock for Ubuntu:

Vectors
2 styles - digital cool blue and odometer
C++
gnome-compatibility so it can sit locked in the upper-right corner

that's about all I can think of. It would be resizable. Maybe have an alarm setting with the computer beep, that would be fun. Do new computers still have a speaker?

Hey there  Petrockstealer... I just been working thru a tutorial and it reminded me of your thread... how is your project going?

Firstly, attached is a picture of display from [tutorial #5 of the QT library]("http://doc.trolltech.com/4.3/tutorial-t5.html") and you might see why it reminded me of a digital clock and why I thought perhaps you wanna dig into the same tutorial (tutorial # 1 might be a better place to start)... I can help you if you get stuck.

Secondly I also found a function for [playing the system "alarm" sound]("http://ubuntuforums.org/showthread.php?t=1597819") which you could use.

and finally I noticed a thread about [periodic timer functions]("http://ubuntuforums.org/showthread.php?t=1598102") that could be used to make your clock tick.

p.s. ... and can I have my pet rock back now pl0x ... jk ;)

---

