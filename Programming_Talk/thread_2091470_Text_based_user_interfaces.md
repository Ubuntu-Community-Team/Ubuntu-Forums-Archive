---
title: "Text based user interfaces"
date: 2012-12-05
forum: Programming Talk
---

### Post by SuperCamel on 2012-12-05
I've been thinking about text based user interfaces (TUIs) recently. TUIs have heaps of pros compared to GUIs. They are generally faster to use, faster to develop and according to the wikipedia they often allow more control over the software. The few cons, in my opinion, only exist because there has been very little modernization of TUIs. Google screenshots of ncurses and you'll see what I mean. A modern TUI could easily incorporate images, nice colors, multiple fonts and so on. The biggest con is that most people rarely use them and often have the opinion that they will be difficult to use. 

Does anyone know of a modern TUI library for C or C++? Despite the pros, would anyone even use a TUI in this day and age?

---

### Post by spjackson on 2012-12-05
I don't understand. In what way is a TUI with "images, nice colors, multiple fonts and so on" not a GUI?

---

### Post by Habitual on 2012-12-05
Isn't this called the console presently?

---

### Post by SuperCamel on 2012-12-05
> **spjackson said:**
> I don't understand. In what way is a TUI with "images, nice colors, multiple fonts and so on" not a GUI?

You're right, a true TUI will only have text and symbols. So I guess what I'm describing is a 'graphical TUI' or something. Maybe a GUI that primarily displays text. Image an old school application like this

[http://en.wikipedia.org/wiki/File:Synchronet.png](http://en.wikipedia.org/wiki/File:Synchronet.png)

with a logo, modernized fonts and a background image. 

> Isn't this called the console presently? 
Maybe . . depends. I'm not really talking about command line interfaces (CLI). Bash has a TUI, gcc has a CLI.

---

### Post by mevun on 2012-12-05
> **SuperCamel said:**
> You're right, a true TUI will only have text and symbols. So I guess what I'm describing is a 'graphical TUI' or something. Maybe a GUI that primarily displays text. Image an old school application like this

[http://en.wikipedia.org/wiki/File:Synchronet.png](http://en.wikipedia.org/wiki/File:Synchronet.png)

with a logo, modernized fonts and a background image. 

 
Maybe . . depends. I'm not really talking about command line interfaces (CLI). Bash has a TUI, gcc has a CLI.

I think what you are describing is an interface that can be navigated with a keyboard beyond just a TAB as can be done with some GUI interfaces today (like a web browser).  When you have a text-based menu that is "active", then a key usually corresponding to a letter of the alphabet would activate that menu item.  HTML browsers support the TAB which leads to a very linear navigation among all the potential items in the UI.  I don't think any keystroke will perform the equivalent of a "hover" which often bring up menus.  So, it may be nice to be able to hit a key that does that.

Irregardless of whether I have interpreted your vision or not, I don't know if such libraries exist beyond something like ncurses that you mentioned.

---

### Post by ofnuts on 2012-12-05
> **SuperCamel said:**
> Maybe a GUI that primarily displays text. I
This is called a "web application".

---

### Post by ehrt74 on 2012-12-05
I think what the OP is talking about is for example why does the terminal open images in a new window? theoretically you could have these displayed in the terminal in an equally high quality.

How about terminal applications which dock to one side of the terminal? You could have a music player on the right-hand strip, for example.

---

### Post by SuperCamel on 2012-12-06
> **mevun said:**
> I think what you are describing is an interface that can be navigated with a keyboard beyond just a TAB as can be done with some GUI interfaces today (like a web browser).  When you have a text-based menu that is "active", then a key usually corresponding to a letter of the alphabet would activate that menu item.  HTML browsers support the TAB which leads to a very linear navigation among all the potential items in the UI.  I don't think any keystroke will perform the equivalent of a "hover" which often bring up menus.  So, it may be nice to be able to hit a key that does that.

Irregardless of whether I have interpreted your vision or not, I don't know if such libraries exist beyond something like ncurses that you mentioned.

You've pretty much nailed my description for me. Thanks. 

Such an interface would be much better for a lot of the software we use. Applications such as file sharing clients, audio converters and so on. I use an TUI based inventory management system on a daily basis and it's super quick to use. 

From a programmers perspective, if it was based on synchronous functions rather than a typical GUIs event based system that would be also ideal IMO. Unfortunately, to create such a library it would probably need to be based on an event driven GUI library like Gtk+ and therefor would need to be multi threaded to give the illusion that the application has halted pending user input. I might have a crack at making it myself . . . 

Would anyone use it though? Has the TUI died of old age, or is it niche enough to justify a revival?

---

### Post by ehrt74 on 2012-12-06
I think the TUI could stage a comeback. It would be a different sort of device, but could find a niche, rather like the chromebook is doing but in the other direction.

One thing that would interest me would be a minimal system. If I remember correctly someone once made a Linux distribution containing GNU/Linux and emacs, and that was all. Emacs could do pretty much all you want a TUI to do, but elisp is not the easiest language to master.

Stallman once said that when he started the gnu project, he wasn't sure about which language to use. He considered writing the operating system in lisp but discarded the idea because of performance problems, and decided to go with C instead (and wrote gcc and glibc as well). Nowadays computers are a lot faster while scripting languages remain easier to code in. A project such as GNU/Linux with a TUI userland in a decent modern scripting language (dart? ruby?) would be interesting.

---

### Post by muteXe on 2012-12-06
Sorry if i'm being stupid but I still have no idea what you mean by TUI.

---

### Post by verzx on 2012-12-06
Microsoft Visual C++

Something like that you mean?

---

### Post by SuperCamel on 2012-12-06
> **muteXe said:**
> Sorry if i'm being stupid but I still have no idea what you mean by TUI.

This is a [TUI]("http://enterprise-storage-os.googlecode.com/files/tui_ss_xterm_mail_1.png"). This is a [GUI]("http://sco.wisc.edu/wisclinc/metatool/mpbatch/gui_noconfig_scrn.gif"). 

I suppose the most obvious difference is that TUIs don't really accept mouse inputs (button clicks and so on). They are entirely keyboard and text based.

---

### Post by ehrt74 on 2012-12-06
Well a TUI is just a shell or console or terminal or whatever you want to call it.

The trouble is that the TUI was developed in the days when a width of 80 characters was immense and computer graphics didn't exist. Back then it was excellent. Now a case could be made for revising it.

An example would be something like screen. With this application you can have terminal multiplexing and tiling. It helps make the terminal useful on modern full-hd monitors.

---

### Post by SuperCamel on 2012-12-06
I have been chipping away at this . . it's basically my interpretation of what a modern TUI could be like. I've nicknamed it 'Mtk' for Mouse free Tool Kit. It's just a proof of concept thing, not really a functional UI library. 

[http://www.camelsoftware.com/mtk.tar.gz](http://www.camelsoftware.com/mtk.tar.gz)

You'll need the libgtkmm-3.0-dev package to compile it.

---

### Post by muteXe on 2012-12-06
But a lot of GUIs can be completely navigated with keyboard, so create a GUI and unplug/disable your mouse?

---

### Post by Vaphell on 2012-12-06
> I suppose the most obvious difference is that TUIs don't really accept mouse inputs (button clicks and so on). They are entirely keyboard and text based.

what? midnight commander works with mouse just fine

---

### Post by SuperCamel on 2012-12-06
> **muteXe said:**
> But a lot of GUIs can be completely navigated with keyboard, so create a GUI and unplug/disable your mouse?

Yeah, great idea if you like constantly pressing the tab button. 

>  	 	 what? midnight commander works with mouse just fine 

Cool. So what is the difference between a GUI and a TUI?

---

### Post by muteXe on 2012-12-07
lol this is the most confusing thread ever.

---

### Post by satsujinka on 2012-12-07
To me what it sounds like the OP is saying is that, terminals don't have to be limited to just characters and that you could render images (or other graphical elements) in them without fundamentally betraying the text based nature.

Maybe something not quite as extreme as [termkit]("https://github.com/unconed/TermKit").

Perhaps the thing I'd most like to see out of this kind of idea is an extension to lynx that supports image/audio/video tags. I mean if we can bring that down to the tty I could abandon X altogether.

---

### Post by SuperCamel on 2012-12-08
Some screenshots of the Mtk library I posted above. 

[IMG]http://camelsoftware.com/mtk1.png[/IMG]
[IMG]http://camelsoftware.com/mtk2.png[/IMG]

It's based entirely on synchronous functions, so it's very much like programing with iostream. Except it's got images, text can go anywhere and it's much more likely to crash. lol

---

### Post by zombifier25 on 2012-12-08
Terminal CAN display images, using the [libcaca library](http://caca.zoy.org/wiki/libcaca), but using colored ascii characters. On high-definition monitors the images displayed are pretty accurate. You can even watch videos on a text terminal (holy ****)

Just a little tip :P Personally, if you want a somewhat TUI, then the old-school tiling window managers are worth trying.

---

### Post by The Cog on 2012-12-08
As I understand it, they are proposing to upgrade the terminal to support bit-mapped graphics, but don't want to call it a GUI. I think the problem is that they don't appreciate that character-based terminals are fundamentally, well, character based. 

It's not that they choose not to do bitmapped graphics, it's that they fundamentally cannot do bit-mapped graphics. Think typewriter, teletype, or golfball/daisywheel printer. You send it a character code, e.g. the number 65 for "A", and the hardware somehow makes a visible mark that looks like an "A" of some sort. With printers this was done by banging a character-shaped lump of metal against an inky ribbon and a sheet of paper. With "glass teletypes", this was done with electronics, but they only understood character codes (65->A) and didn't do bitmaps.

[https://en.wikipedia.org/wiki/Teletype_Model_33](https://en.wikipedia.org/wiki/Teletype_Model_33)

---

