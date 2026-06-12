---
title: "Qt vs wxWidgets"
date: 2008-05-05
forum: Programming Talk
---

### Post by scourge on 2008-05-05
I'd like to hear some arguments for and against these two toolkits, preferably from developers who have experience with both. I was somewhat happy with wxWidgets, but now I'm wondering if I should switch to Qt. Here are my pros and cons for wxWidgets:

Pros:
- Uses native GUI elements
- Very fast
- Has a solution to just about any cross-platform problem (gui, threads, processes, config files, etc.)
- Uses GTK on Linux, which is optimal for a Gnome user like me
- Free, even to developers of proprietary software

Cons:
- Installing in Windows was pretty hard. It was actually easier to set up a cross-compiling environment in Linux.
- Converting between C strings and wxWidgets' unicode strings
- Creating makefiles and bakefiles is not fun at all


I've experimented with Qt for one weekend, and based on the first impressions and reading the docs:

Pros:
- Easy to install on any platform
- Qmake is very simple to use, no need to edit makefiles manually
- Implicit casting from const char* to unicode, no need for ugly wxT() macros
- Easy separation of gui (.ui files) and code
- Automatically connects signals to slots based on the names
- Qt designer - wxGlade and Anjuta pale in comparison

Cons:
- I'll have to pay to distribute proprietary software
- Doesn't fit seamlessly into the Gnome desktop, not even with Cleanlooks


So far I've been really impressed with the Qt4 + Qt Designer + KDevelop combo. I also do a fair amount of parallel programming, and I have to say that QtConcurrent looks really promising, assuming that there's no significant overhead. But what are your experiences, should I stick with what I know well, or do the switch?

---

### Post by artoj on 2008-05-05
I've developed programs using both toolkits and I prefer Qt all the way. It has  much better API including the new concurrency framework that's been included to Qt 4.4, WebKit integration (also in 4.4), better model-view support and better painting support.

And no matter how wxWidgets sells itself as stable framework I have to disagree. wxProcess returning pid of 0 on Mac for newly created processes couple releases ago comes to mind (quess what happens when you try to kill that process).

---

### Post by scourge on 2008-05-05
I noticed that Qt seems to be more mature, consistent and polished, though wxWidgets has also been around for a long time.


> I've developed programs using both toolkits and I prefer Qt all the way. It has much better API including the new concurrency framework that's been included to Qt 4.4, WebKit integration (also in 4.4), better model-view support and better painting support.

I probably don't need WebKit integration, but anything that can make parallel/concurrent programming easier is much needed. I did have some problems with double-buffered painting in wxWidgets, especially in Windows.

---

### Post by Lau_of_DK on 2008-05-05
> **scourge said:**
> I'd like to hear some arguments for and against these two toolkits, preferably from developers who have experience with both. 


I've not developed in wxWidgets so you can disregard this: Qt4 is a very powerful, polished cross-platform framework which makes developing complex programs a breeze. They have full classes for networking like FTP, that run smoothly and safely. So it gets a BIG thumbs up from here :)


/Lau

---

### Post by Glaxed on 2008-05-05
I hate to drag GTK into this, but I have to have your opinion:
Would you guys say that the Qt4 designer is "better" than Glade (as in more features or speed)?

---

### Post by scourge on 2008-05-06
> **Lau_of_DK said:**
> I've not developed in wxWidgets so you can disregard this: Qt4 is a very powerful, polished cross-platform framework which makes developing complex programs a breeze. They have full classes for networking like FTP, that run smoothly and safely. So it gets a BIG thumbs up from here :)


/Lau

Thanks. I think the feature set of the two frameworks are equally impressing. wxWidgets also has the networking stuff you'd expect.


> Would you guys say that the Qt4 designer is "better" than Glade (as in more features or speed)?

They have pretty much the same features, but Qt Designer is just a lot easier to use. The controls can be freely positioned anywhere on the form, and when it all looks okay you can define the layout. That's a lot faster than the Glade way of doing the layout first, and then adding controls. You can also configure connections between the controls, like this: [http://doc.trolltech.com/4.3/designer-designing-a-component.html#creating-a-form](http://doc.trolltech.com/4.3/designer-designing-a-component.html#creating-a-form)

---

### Post by tseliot on 2008-05-06
> **Glaxed said:**
> I hate to drag GTK into this, but I have to have your opinion:
Would you guys say that the Qt4 designer is "better" than Glade (as in more features or speed)?
I use both of them and they are just different. They have different features. For example Glade-3 has an about dialog widget which is not in QT designer (at least as far as I know). If you want to use the about dialog widget you will have to write code for it (QMessageBox::about). Of course QT designer has other features which Glade lacks.

Using Glade-3 in Python with simplegladeapp is a breeze and so is QT4 designer (in both C++ and Python). I don't know if there is something similar to simplegladeapp in C or C++ though. 

My suggestion is to try both of them and then choose the one you feel more comfortable with. However if you choose QT4, especially in C++, you will write code which is different from standard C++. For example have a look at this foreach loop:
[PHP]foreach (QString sect, m_Sections) {
            if (line.trimmed().startsWith("Section") 
                && line.toLower().contains(sect.toLower())) {
                m_Flag = sect;
                m_FirstTime = 1;
                m_HasSection = true;
            }
        }[/PHP]

---

### Post by irrdev on 2008-05-06
I prefer wxWidgets for several reasons.
1. No licensing restrictions to speak of 
2. Sockets
3. Community support (over commercial support)

Regarding wxWidgets setup on Windows, I would truly recommend that you try out [wxDev-C++]("http://wxdsgn.sourceforge.net/"). This IDE autimatically installs the wxWidgets library, and includes its own GUI designer to boot. For a pure form designer, I would also recommend [wxFormBuilder]("http://wxformbuilder.org/"). You may have to get used to the strict layout design, but it results 100% resizable windows and controls.;)

---

### Post by scourge on 2008-05-06
> 1. No licensing restrictions to speak of

This is the biggest advantage for wxWidgets in my opinion. Right now I only develop GPL software, so Qt is fine. But if I ever want to go proprietary, Qt will cost me an arm and a leg. So I'll definitely keep my wxWidgets skills sharp as well.


> Community support (over commercial support)

To be honest, I never even visited the wxWidgets forums. The online documentation was always enough. And the same goes for Qt, very good docs.


> Regarding wxWidgets setup on Windows, I would truly recommend that you try out wxDev-C++. This IDE autimatically installs the wxWidgets library, and includes its own GUI designer to boot.

Thanks, I'll keep that in mind in case I ever want to write or compile wxWidgets apps in Windows. Currently I'm cross-compiling with MinGW in Linux.


> For a pure form designer, I would also recommend wxFormBuilder. You may have to get used to the strict layout design, but it results 100% resizable windows and controls.

I had heard of wxFormBuilder, but I thought it was commercial or Windows-only. Glad I was wrong. I just tried it, and it's clearly better than wxGlade (I hate having a million little windows floating around). The layout thing is a real bitch though. With Qt Designer I can just drag and drop controls where I want them just like in Visual Studio, and quickly finish the layout so that everything will resize properly.

---

### Post by Mickeysofine1972 on 2008-05-06
> **tseliot said:**
> I use both of them and they are just different. They have different features. For example Glade-3 has an about dialog widget which is not in QT designer (at least as far as I know). If you want to use the about dialog widget you will have to write code for it (QMessageBox::about). Of course QT designer has other features which Glade lacks.

Using Glade-3 in Python with simplegladeapp is a breeze and so is QT4 designer (in both C++ and Python). I don't know if there is something similar to simplegladeapp in C or C++ though. 

My suggestion is to try both of them and then choose the one you feel more comfortable with. However if you choose QT4, especially in C++, you will write code which is different from standard C++. For example have a look at this foreach loop:
[php]foreach (QString sect, m_Sections) {
            if (line.trimmed().startsWith("Section") 
                && line.toLower().contains(sect.toLower())) {
                m_Flag = sect;
                m_FirstTime = 1;
                m_HasSection = true;
            }
        }[/php]

I agree, they are just different and the only think I've found a bit naff is the way wxWidgets looks under vista! But who the hell cares about vista anyway LMAO!

Mike

---

### Post by emilevr on 2008-05-17
Hi there.

I've only recently started playing around with wxWidgets, so don't have a lot of experience yet. From the research I have done though, [Code::Blocks]("http://www.codeblocks.org/") seems to be a great dev environment to use for doing C++ wxWidgets development.

Code::Blocks itself was developed using wxWidgets, so it is cross-platform and free. So far I am very happy with the feature set. It includes a wxWidget project type and there is a plugin dialog editor called wxSmith which allows you to work with sizers or drop in a panel to freely position controls using a grid, like a basic version of the MSVC6 dialog editor, minus the nice formatting tools etc. The code it generates for your dialog/frame uses a similar mechanism to how MFC in MSVC6 did it, e.g. labeled and managed blocks of code.

As I mentioned I haven't done too much with it yet, but so far it looks great. You might want to have a look.

Take care,
Emile.

---

### Post by cb951303 on 2008-05-17
> **scourge said:**
> 
- Doesn't fit seamlessly into the Gnome desktop, not even with Cleanlooks

[http://ubuntuforums.org/showthread.php?t=794652](http://ubuntuforums.org/showthread.php?t=794652)

it will in a couple of months :)

---

