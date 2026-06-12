---
title: "GUI Programming in Linux"
date: 2007-03-02
forum: Programming Talk
---

### Post by azazel00 on 2007-03-02
Hello,

I've been wanting to start developing in Linux for quite some time now. The only thing that was holding me back is that all my linux dev had been command line (console programs to write to files, read files, get user input... stuff that I was doing on my first year of college).

I started doing .NET development like 3 years ago, and that's pretty much all I have been doing. So Im used to just droping the component and having it work by default.

I've been reading about wxWidgets (wxRuby in particular), GTK+ (Glade), and today I discovered FLTK. I was going to go with GTK+, because the Glade IDE looks pretty cool, but the documentation is a bit awful (for a newbie like me, at least) and the properties are a bit misleading. On the other hand, I read wxWidgets is a bit sluggish.

Now, the question. I want to learn GUI development in linux, but I want the concepts I learn to be applicable to a broader array of platforms. Aka, try to stick to some sort of standards. Like, say I end up doing MFC three years from now (I know MFC is old, but it's just an example), I wouldnt want to have to start from scratch. I'd like to be able to read through the API, and apply the concepts that I learned from wxWidgets (for example) to MFC development.

Which GUI library do you recommend? Where should I start learning it? 

Regards,
az

---

### Post by lnostdal on 2007-03-02
if you have any concrete problems/questions regarding gtk+/glade i'll help you with those where i can

you'll find a small set of articles here that describe a setup for development on linux and in `ubuntu-programming3' describes how to develop using gtk+/libglade: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) .. .. quite basic stuff though ..  the writings also link to other resourses you should look into for gtk+ development

not sure i understand what you're saying about mfc and such, but gtk+ is portable to several platforms; i've used it on both linux and win32 .. hm, or if you're talking concepts of GUI-programming; GTK+ uses concepts you'll find in most GUI-toolkits .. signals for events .. data to describe/declare UI (instead of using imperative code to set it up - but it supports that too of course) .. etc.

edit: well, to answer your last question i recommend GTK+

---

### Post by simonn on 2007-03-02
> **azazel00 said:**
> Which GUI library do you recommend? 

All GUI toolkits have their differences, but are kind of the same as well - there is only so many ways to implement a checkbox or an edit box or a grid or a tree view etc etc and they are all event drive is some way shape or form - the real difference between command line and GUI.

If you want to be completely cross platform, learn either wxwidgets or QT. However, if you want to be completely GNU use GTK.

Mind you IIRC last time I looked wxwidgets did not have a decent grid type control.

I'd go GTK (well, I did) - viva le revolution!

> Where should I start learning it?

There are plenty of hello world type apps and tutorials for all of them. Spend a few weeks being frustrated before it all starts making sense like everyone else :).

---

### Post by azazel00 on 2007-03-02
I guess I'm sticking to GTK+ and Glade for the time being.

Thanks for the input!

---

### Post by lnostdal on 2007-03-02
btw.  ..  i haven't used it extensively yet, but glade-3 under feisty (not sure if edgy/dapper has the same version available; 3.1.5 it says in the about-box) seems like a big improvement over the old glade-2 .. :)

---

### Post by azazel00 on 2007-03-02
Yeah, it's pretty neat.

I had tried Glade 2 when I was starting out with Mono, but it was a big disappointment. 

The new version seems to really hit the ball. I still gotta learn how to integrate it with C++ (hoping that there is some way to generate templates like i can do with ruby-glade-create-template).

I did a tutorial on creating GUIs with Glade for your Ruby applications (check sig). Let me know what you think.

---

### Post by lnostdal on 2007-03-02
looks good :)

i don't think i've seen something that generates code-templates for c++ based on .glade-files .. well, glade used to generate some code but that feature has been deprecated

---

### Post by RaygionsSumta on 2009-02-13
> **azazel00 said:**
> Yeah, it's pretty neat.

I had tried Glade 2 when I was starting out with Mono, but it was a big disappointment. 

The new version seems to really hit the ball. I still gotta learn how to integrate it with C++ (hoping that there is some way to generate templates like i can do with ruby-glade-create-template).

I did a tutorial on creating GUIs with Glade for your Ruby applications (check sig). Let me know what you think.

I am, I think, where you were two years ago when you started this thread.  In retrospect, are you happy with having gone the Glade route?

---

### Post by Sorivenul on 2009-02-13
> **RaygionsSumta said:**
> I am, I think, where you were two years ago when you started this thread.  In retrospect, are you happy with having gone the Glade route?
The OP's last recorded post is from April 2007, as far as I can tell. That said, you probably won't get the "official" answer. 

But, as one who also went the GTK+/Glade route, I'm glad that I did. The other toolkits are interesting to me, but I don't use them nearly as much. I've started a little bit of work in Qt as well and find it enjoyable, too. Toolkit preferences, like any other preferences are subjective. Also, what I use for one project I may not use for another because I find the project easier to implement better in the different toolkit. Just my two cents. 

Good luck!

---

### Post by rich1939 on 2009-02-13
> **Sorivenul said:**
> The OP's last recorded post is from April 2007, as far as I can tell. That said, you probably won't get the "official" answer. 

But, as one who also went the GTK+/Glade route, I'm glad that I did. The other toolkits are interesting to me, but I don't use them nearly as much. I've started a little bit of work in Qt as well and find it enjoyable, too. Toolkit preferences, like any other preferences are subjective. Also, what I use for one project I may not use for another because I find the project easier to implement better in the different toolkit. Just my two cents. 

Good luck!


Another vote for GTK+/Glade...especially in concert with CODE::BLOCKS, which makes everything really automatic (editor compile-interface, debugger-interface, conversion of glade's xml to gbuilder format in a pre-compile step).

---

### Post by bapoumba on 2009-02-13
This is an old thread.. Closing here.

---

