---
title: "gnome-shell css file gui tool - want to contribute to Ubuntu?"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by anewguy on 2012-06-03
I've seen many posts on this forum for people wondering how to contribute to ubuntu.  If you can program, here's your chance!

The package "gnome shell" can be installed from the software center or synaptic package manager.  It uses a css file (and I don't know anything about CSS) to describe how it should present things - the top bar, the font in it, drop downs, menus, etc., etc., etc..  

Apparently there is no GUI tool to make this easy for the average user to change how some things look.  I have been SLOWLY trying make such a tool (I seem to have forgotten how to write things in C, and I also don't know anything about CSS).  I'm just thinking there is probably someone out there who can program, who either knows or can pick up using GTK to do the GUI work (GTK for most basic things is pretty easy to use) or another tool so the presentation to the user is a gui, and who would like to jump in and start building such a tool.

Now, I don't need it - this is for others, and while I have been working on a program, I'm not looking for someone to take over my program.  Instead, if someone could take the time to really understand the CSS file and themeing, and the gnome-shell.css file and build their own.  Programming language and the tool(s) used internally to make the gui don't matter - only so it's a gui'd interface and simple for someone with no knowledge of css, and who doesn't want that knowledge, to use to tune their gnome-shell presentation.  There are a few things that may be different from some things:

- I've tried specifying font weight and style (bold and italic respectively) and a font color, but those do not seem to apply for the top panel in gnome-shell.  You can change the background, you can change the font type and size. (that much I do have working).  But for some reason on the panel itself you don't seem to be able to change those.

So, it may be that there will be some trial and error involved due to some idiosyncracies of gnome-shell.

At any rate, I posted this type of request in the programming forum, but, well, they don't like me there - I guess asking for help in understanding what you are doing wrong and how to debug it is below what they want the forum for, at least for me.  

So - here's you chance to contribute!

If you want to know more, just PM me and I'll point you to the thread where all this started and to a couple of threads that may help in deciding what should be in the tool.

Again, NONE of this is for me, I DON'T want someone taking over my code.  It would just be a great opportunity for someone to contribute to ubuntu and the linux community in general.

Thanks for your time!
Dave ;)

---

### Post by anewguy on 2012-06-04
Well it looks like someone has already done the task at hand.  The [thread]("http://ubuntuforums.org/showthread.php?t=1912749") regarding what was needed/wanted has been around for a long time - someone finally answered with a tool that does it.  So, I guess no need for this project now.

If anyone WAS interested, perhaps there is another project/tool of some sort you can work on to contribute.

Dave

---

### Post by traditionalist on 2012-06-04
> **anewguy said:**
> Well it looks like someone has already done the task at hand.  The [thread]("http://ubuntuforums.org/showthread.php?t=1912749") regarding what was needed/wanted has been around for a long time - someone finally answered with a tool that does it.  So, I guess no need for this project now.

If anyone WAS interested, perhaps there is another project/tool of some sort you can work on to contribute.

Dave

Well, I don't think that you should abandon your project just yet.  I don't really know very much about all this. I just went ahead and used what I could find to set my own system up. Whether this is generally applicable I don't know. I have used it on a few machines now with various hardware but always with 12.04 and GNOME Classic.  It is fine for me but it may not be suitable for everybody.

---

### Post by anewguy on 2012-06-04
Yeah, someone who knows this stuff mentioned in the other thread said that this doesn't affect what I was doing, or what I'm asking if someone wants to do.

So, the thread is re-opened!  I'm still plugging away at mine, but a fresh start with younger blood would probably make a world of difference in the time to complete the project.

Again, I don't need this for myself.  I don't want someone to take over my code.  Rather, someone to start from scratch with that fresh approach and zest that younger blood normally brings.

Dave ;)

---

### Post by traditionalist on 2012-06-04
> **anewguy said:**
> Yeah, someone who knows this stuff mentioned in the other thread said that this doesn't affect what I was doing, or what I'm asking if someone wants to do.

So, the thread is re-opened!  I'm still plugging away at mine, but a fresh start with younger blood would probably make a world of difference in the time to complete the project.

Again, I don't need this for myself.  I don't want someone to take over my code.  Rather, someone to start from scratch with that fresh approach and zest that younger blood normally brings.

Dave ;)

Well, I'm not all that young any more ( I've been retired for ten years) and I only did what I have done up to now to get my main machine running properly according to my taste.  But if I can be of assistance in some manner then fire away.  I don't know what, research maybe?  I am completely useless at coding for stuff like this, it is far too long since I did any and what I did was all in various assembly codes anyway. What sort of input are you looking for?  A few definitions of what is what would doubtless help a lot. Always nice to know what it is you are trying to customise, ( although not necessarily essential! :)  ).

---

### Post by anewguy on 2012-06-08
What help me immensly is if you can tell me what at least come, even if not all, of the things in the gnome-shell.css file itself are for.  I did finally have it dawn on me that while I was trying to work with "text" in the top panel, the truth is they are GTK buttons - press one to either bring something directly up or to bring up another menu.  So, the colors, weight (bold) and style) for those are all in the .panel-button:hover, .panel-button:, and .panel-button:focus.  I also have the text font and the possible backgrounds for the panel itself (not the buttons, etc.) figured out.  I know that at #dash you can change the background color of the dash ("activites" in gnome-shell), $SearchEntry:hover, etc., allows changing colors in the search bar under "activities"., .app-filter changes the color of the text in pull-down menus (and on the bottom 2 entrys in the calendar).  That's what seems to do what based on some testing, but I don't have a clue on anything else.

In addition, while I continue to work on my program, it would be really nice for someone with more current knowledge of some programming language that can present a GUI to the user and start from scratch on allowing changes to the settings.  In other words, not to work on my code, but to instead really gather requirements (perhaps opening a thread in ABT and possibly other forums asking for what people would like to be able to change), and write their own code with something they are comfortable with.  Chances are you would get done a lot faster than I am able to.  But I'm still plugging away on mine just to have some excersize of the mind.

Thanks!

---

