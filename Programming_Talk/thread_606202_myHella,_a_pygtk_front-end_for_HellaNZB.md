---
title: "myHella, a pygtk front-end for HellaNZB"
date: 2007-11-07
forum: Programming Talk
---

### Post by dirken on 2007-11-07
hey,

i just learned python and wanted to wirte some app for and the first idea that came up was to write a front-end for in, in python off course. So did and after one week work i got pretty far i think.
Check the result here: [http://projects.dvwd.be//index2.php?page=by&cat=myHella](http://projects.dvwd.be//index2.php?page=by&cat=myHella)
Latest version at moment of writing is a0.3 and available here: [http://projects.dvwd.be//files/upload/hellaclient.a03.tar.gz](http://projects.dvwd.be//files/upload/hellaclient.a03.tar.gz)

Screenshots:
[IMG]http://projects.dvwd.be//gfx/images/upload/20071108_WRBU_screenshot137.png[/IMG]
[IMG]http://projects.dvwd.be//gfx/images/upload/20071108_ED44_screenshot141.png[/IMG]

Some things to come: settings window (you can already set up servers on first run but can't change 'em yet afterwards)

Let me know what you think of it, is it easy to use and has all features you wish?

Oh yeah, i just found out about lottanzb, hoping mine to be(come) better ;) Just let me know your thougths!

---

### Post by cysco24 on 2008-03-01
I've seen the myhella 2 screenshots and it looks great.  I can't seem to get either one to work.  I have got lottanzb working.

Maybe a step by step for installation.  It's possible that there is a dependency to use myhella2 that i don't have installed.

I have got hellanzb + lottanzb + hellafox working right now and it's great.  Myhella2 looks a lot better and I would love to try it.

thanks for any help

Link to MyHella 2 page
[http://www.gtk-apps.org/content/show.php/myHella+2?content=69738](http://www.gtk-apps.org/content/show.php/myHella+2?content=69738)

---

### Post by dirken on 2008-03-02
hey i'm glad to hear you think that myHella is much better than any other solution and I hope it is. But since a month i'm not giving any support anymore for myHella 1 as this version was really bad. Altough i still wanne help sort things out to get myHella 2 to work!

First off all before running myHella you should install hellanzb which will be found in the standard repo. Other depencies are the [python-pyinotify]("apt:python-pyinotify") package. and the package [python-pyopenssl]("apt:python-pyopenssl").

More information can be found on [gtk-apps]("http://www.gtk-apps.org/content/show.php?content=69738"), [DVWD-projects]("http://projects.dvwd.be") or [Launchpad]("https://launchpad.net/myhella/").

EDIT: myHella 2 is currently still under development at the moment, when running myHella2 for the first time you will be able to configure the servers but afterwards you will only get the myHella2 main screen in which there's not yet a server-editor included. If, for any reason, you want to edit the servers you will have to remove the folder ~/.myhella and you will be able to re-configure myHella 2.

---

### Post by Can+~ on 2008-03-02
What amazes me is that you build a whole application using pygtk. I also built an app with pygtk, but later I discovered glade and it saves a lot of work of packing things and connecting them.

Although, I don't know what hellanzb is about, I suggest you, to split the code from the design, use glade to build the interface and then use the gtk.glade to read it, that would save you loads of work.

Nice work.

---

### Post by dirken on 2008-03-02
well, that's exactly how i work :)
I know i forgot to mention the gtk glade package as depency but i thought that this was already installed right away with Ubuntu. Can anyone confirm this?

> **Can+~ said:**
> What amazes me is that you build a whole application using pygtk. I also built an app with pygtk, but later I discovered glade and it saves a lot of work of packing things and connecting them.

Although, I don't know what hellanzb is about, I suggest you, to split the code from the design, use glade to build the interface and then use the gtk.glade to read it, that would save you loads of work.

Nice work.

---

### Post by cysco24 on 2008-03-02
python-glade2 from the looks of it is already installed in ubuntu.

One dependency i was missing was the python-pyopenssl

got it to work.  Had some issues that i posted up on your dev site.

Thanks

---

