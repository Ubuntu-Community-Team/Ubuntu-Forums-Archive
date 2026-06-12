---
title: "Open Source Devolpment"
date: 2007-02-09
forum: Programming Talk
---

### Post by i0Null on 2007-02-09
[FONT="Trebuchet MS"][SIZE="2"]
I am interested in doing some open source contributions (doing development work). However, i would like some advise on how to go about doing this.
Currently, i have my eye on being able to re-compile Firefox.
I have gotten so far as doing:
```
apt-get source -b firefox
```
:lolflag: 
I would like to know if there are any good IDE's that will be able to detect all of the files (and possibly recompile/install it). If there is, how do i open the source files as a project?

[/FONT][/SIZE]

---

### Post by Choad on 2007-02-09
normally, you will cd to the source directory, then

./configure
make
sudo make install

then you make a little hack to the source code

make 
sudo make install

and your little hack will be included 

i say this, but i've very little experience. its difficult getting to grips with a project as big as firefox.you'll spend 95% of your time figuring what the hell everythign is supposed to do, and 5% of your time actually doing anything productive.

---

### Post by i0Null on 2007-02-10
[FONT="Trebuchet MS"][SIZE="2"]Yeah, i can see what you mean. When i was looking through the source tree, i spent ages looking for the code i wanted. I find the structure rather confusing. ](*,)

What IDE do you use to edit the source? I normally would use a text editor, but IDE's at least help me to figure out what the hell i am doing with the file structure. :???:[/SIZE][/FONT]

---

### Post by Tomosaur on 2007-02-10
Unless the particular IDE project file is included in the source tree, then you're probably not going to be able to get the IDE to be anything more than a glorified text editor. The best method by far is to just find a source file which looks 'similar' to what you're after, then check to see whether the bit you want to hack is inside it. Any IDE will be able to open the source files, but without the project file, it's just going to sit there.

In some IDEs, however (I know you can do this in Eclipse, anyway), have the ability to create a new project from existing source code. You just click File > New Project, and then follow the instructions in there. If all goes well, it should at least allow you to follow the source more coherently.

---

### Post by ssam on 2007-02-10
if you download source packages through apt then you can cd into the directory and run
```
dpkg-buildpackage -rfakeroot
```
to build the deb packages

you will need the packages
```
build-essential fakeroot devscripts
```

also you will usually some dev packages specific for the project you are building. to get these run
```
sudo apt-get build-dep firefox
```

firefox is rather a large project to get started on though. it has about 30mb of source code which can build many different targets (firefox, thunderbird, sunbird etc). maybe you should start with something smaller.

also the developers are often working on a newer version of the code then that which is included in ubuntu. you can usually access their latest code using a version control system like CVS or SVN. that way you wont be fixing bugs that they already have.

---

### Post by kripkenstein on 2007-02-10
As Choad said, Firefox is a pretty tough project to get started with... a huge codebase, and pretty tricky stuff. Perhaps a smaller project would be more fun, that's how I got started out with open-source programming.

---

### Post by lnostdal on 2007-02-10
i just came over this will searching google for some gtk-stuff: [http://live.gnome.org/GnomeLove](http://live.gnome.org/GnomeLove)

not related to firefox, but still :)

edit: i haven't read the pages there (yet), but though i'd post it anyway

---

### Post by rko618 on 2007-02-10
> **ssam said:**
> 
firefox is rather a large project to get started on though. it has about 30mb of source code which can build many different targets (firefox, thunderbird, sunbird etc). maybe you should start with something smaller.


This is something that has always bugged me.  Because Firefox is **so fricking huge** how does anyone other than the mozilla people able to make contributions to the code?  It seems that a project of that size would be way, way too complicated for anybody to pick up.  When I've started as a programmer at a new company I generally spend the first couple weeks learning the code base and asking my peers hundreds of questions about the code.  I suppose you could ask these questions in IRC but without the dedicated environment learning everything would take much longer.

So I guess what I'm trying to ask is, realistically, how much of Firefox's coding is done by people who don't work for Mozilla?  (You can substitute Firefox with any big open source program ie. OpenOffice, etc.)

---

### Post by Wybiral on 2007-02-10
> **rko618 said:**
> This is something that has always bugged me.  Because Firefox is **so fricking huge** how does anyone other than the mozilla people able to make contributions to the code?  It seems that a project of that size would be way, way too complicated for anybody to pick up.  When I've started as a programmer at a new company I generally spend the first couple weeks learning the code base and asking my peers hundreds of questions about the code.  I suppose you could ask these questions in IRC but without the dedicated environment learning everything would take much longer.

So I guess what I'm trying to ask is, realistically, how much of Firefox's coding is done by people who don't work for Mozilla?  (You can substitute Firefox with any big open source program ie. OpenOffice, etc.)

I guess the point is that if you notice a bug or have a new idea... You only have to know enough about that section of the code to fix it. So you can ask around to find where that part of the code is, and work outward from there until you have a general idea of what all of the that affects that portion does and how.

If the code is HEAVILY intertwined with the rest of the project and uses tons of other objects/functions... Then it will take forever.

But if it's a fairly isolated chunk that only uses a few external parts... You can work outward until you know enough about everything that has a relationship with it to change things.

It just depends how much of the project it affects/is affected by.

---

### Post by i0Null on 2007-02-11
> **kripkenstein said:**
> As Choad said, Firefox is a pretty tough project to get started with... a huge codebase, and pretty tricky stuff. Perhaps a smaller project would be more fun, that's how I got started out with open-source programming.

Well, i guess openoffice is out of the question :lolflag:

---

### Post by i0Null on 2007-02-11
[FONT="Verdana"][SIZE="2"]Looking into this, i found that there is a Debian package somewhere (can't remember the name) that makes compiling from source easier.

After downloading a source package and changing the directory to the source tree you can edit the changelog by entering the command:
```
dch -i
```

then to compile just:
```
debuild -rfakeroot
```
This will compile the code and create the .deb packages.

Then to install them:
```
sudo debi
```[/SIZE][/FONT]

---

