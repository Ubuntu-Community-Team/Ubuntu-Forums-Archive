---
title: "Cross platform GUI development"
date: 2008-09-17
forum: Programming Talk
---

### Post by xavier_r on 2008-09-17
Hi I am trying to make a software that runs natively on Mac, windows, and Linux... without any code modification...

I am not able to choose which programming language to use for GUI 
deployment...My constraints for the language are... 

1: There must be the option to natively compile the software, under mac windows or linux
2: The programming language must be open-source
3: There must be a good IDE for building the GUI forms
4: The compiled software, must blend smoothly with the GUI interface in Mac Windows or Linux...
5: The development environment is on Ubuntu...

Any ideas?
Thanks
xavier

---

### Post by LaRoza on 2008-09-17
> **xavier_r said:**
> Hi I am trying to make a software that runs natively on Mac, windows, and Linux... without any code modification...

I am not able to choose which programming language to use for GUI 
deployment...My constraints for the language are... 

1: There must be the option to natively compile the software, under mac windows or linux
2: The programming language must be open-source
3: There must be a good IDE or building the GUI forms
4: The compiled software, must blend smoothly with the GUI interface in Mac Windows or Linux...
5: The development environment is on Ubuntu...


That is a little touch. Perhaps C++ with wxWidgets. C++ is cross platform (although not my choice for language) and wxWidgets is designed to look native cross platform.

As for compiling, if that isn't needed, you could use Python and wxWidgets to cut development time and reduce bugs.

[http://ubuntuforums.org/showthread.php?t=772507](http://ubuntuforums.org/showthread.php?t=772507)

---

### Post by xavier_r on 2008-09-18
Thanks will check that  out :)

I must also mention, that although I want to work on Linux... My main target platform in win32... then comes Linux, and then Mac...

So having a compile option into win32 native exe's is also a necessary option...

---

### Post by scourge on 2008-09-18
Is the software going to be open source as well? If yes, then you can use the Qt toolkit, which in my opinion is far superior to wxWidgets, and easier to learn and use as well.


> So having a compile option into win32 native exe's is also a necessary option...

You don't have a Windows machine to compile it on? If not, then you'll have to set up a cross-compiling environment. You can do that with both Qt and wxWidgets.

---

### Post by irrdev on 2008-09-18
Either way, your are going to need to use C++ for the type of application you want. There are then 2 library choices - [QT]("http://trolltech.com/products/qt/") or [wxWidgets]("http://www.wxwidgets.org"). QT is dual-released under the GPL or a $$$$ Commercial license. Also, the QT Commercial license doesn't allow you to start your project as GPL and later switch to Commercial. wxWidgets, on the other hand, is released under the BSD license, which allows your to freely modify, sell, and redistribute your program commercially without releasing your source code. QT is notably used by Google Earth, while wxWidgets is used by AOL messenger and AVG Ant-Virus Software. 

Although QT and wxWidgets provide extremely similar functionability and apis, the underlying frameworks are extremely different. QT actually doesn't actually use native controls, but emulates all of its drawing to match the OS. QT does a pretty good job at native theme emualation, and it also allows for custom theming. wxWidgets, however, draws all of its controls natively - WinAPI on Windows, GTK+ on Linux and Cocoa on Mac OS X.

For large corporations, QT is very attractive, as it provides commercial support and an extensive api. However, as you can see from the attached cost table, it is quite expensive for a commercial license. Also, its emulated native rendering engine can encounter trouble on some select custom themes. wxWidgets has no price tag, but it lacks direct commmercial support and has a slightly smaller api - for example, there are no included XML handling functions. However, I feel that these slight drawback on wxWidgets more than outway QT for most projects and developers. wxWidgets is also extremely popular on Ubuntu, and there are two GUI builders in Add/Remove programs - wxFormBuilder and wxGlade. The [Code::Blocks]("http://www.codeblocks.org") IDE uses wxWidgets, and it also has a wxWidgets project wizard and an integrated wxWidgets Form designer called wxSmith. 

Check out both QT and wxWidgets, but I would say that wxWidgets is the better option for you. I have used in 2 projects, and I find that the lack of commercial support is more than made up by the fabulous Community Forum. Not to mention that BSD is far freer than GPL/Commercial. :wink:

---

### Post by xavier_r on 2008-09-18
Thanks for that post :)

You're right, I think wxWidgets would be a better option for me...
Qt license prices are huge...

I am also looking at PyGTK, does that compare well with wxWidgets? because python is much easier to code... and I want to avoid C++...

---

### Post by irrdev on 2008-09-18
If you want to use python, use [wxPython]("http://www.wxpython.org/"). It binds directly to the wxWidgets library, is completely cross-platform, free, and is considered the most popular of all the Python GUI libraries. I particularly like the wxPython Demo program - it incorporates dozens of Python Demo modules which demonstrate everything from controls to clipboard handling to creating a word application. wxPython is extremely OO-based, and it is very easy for C++ users to get accustomed to. Also, wxGlade is able to GUI design in wxPython in addition to wxWidgets/C++! I also have used wxPython in the past, and I can highly recommend it as the best GUI option for Python. :wink:

---

### Post by xavier_r on 2008-09-18
Ok, So does wxPython have compile options in Windows to produce native win32 applications?

Also, how do I set up the devl environment in Ubuntu?

Thanks for your help :)

EDIT: I was looking into Adobe Flex today... Is that a good option?
What I called as a GUI Software, is actually called a Rich Internet Application...
So sorry, if I gave the wrong view, what I mean is developing a Rich Internet APplication...

---

### Post by ankursethi on 2008-09-18
RIch Internet Application? What does that mean? If it means "downloads a bunch of stuff from the internet", then you can use any scripting language to build it. Perl, Python, Ruby, whatever. With whatever toolkit you want to use. It doesn't really make a difference. Just choose what you like.

Flex *might* be a good choice for this kind of an app. I can't really say because I haven't tried it yet. But what I understand from the blog articles I've read so far, it's not much different from other scripting languages. One advantage it give you is that it was *specifically* built for what you call Rich Internet Applications, and hence might have better support for interacting with the web. Moreover, building nice GUIs seems to be pretty easy with Flex.

If you intend to distribute your apps to the public, I'd suggest you go the scripting languages way. Flex still isn't installed on all computers, whereas you'll find Python and Ruby installed on the Macintosh as well as all Linux distributions. Installing them on Windows is a trivial task.

---

### Post by pmasiar on 2008-09-18
> **xavier_r said:**
> 
1: There must be the option to natively compile the software, under mac windows or linux


First step to get good answer is to ask right question. What are business restrictions for requirement 1? It limits your options, places restrictions on your productivity with no apparent gain. Remember, speed is not a problem until you can measure it is a problem, and most important speed is "speed to the market". So why 1?

---

### Post by LaRoza on 2008-09-18
> **scourge said:**
> Is the software going to be open source as well? If yes, then you can use the Qt toolkit, which in my opinion is far superior to wxWidgets, and easier to learn and use as well.


Oh? wxWidgets fits the OP's criteria. QT may be easier and you may find it superior, but wxWidgets looks native by its design.

I find command line interfaces and ncurses at the most to be far superior to any GUI toolkit, but I am not going to say that because the OP wouldn't benefit ;)

> **xavier_r said:**
> Hi I am trying to make a software that runs natively on Mac, windows, and Linux... without any code modification...

4: The compiled software, must blend smoothly with the GUI interface in Mac Windows or Linux...


---

### Post by xavier_r on 2008-09-19
I just tried wxPython, used a lot of good and bad GUI builders...
The thing I disliked about them is that wxGlade, or wxFormBuilder, or others are not WYSIWYG...
and then again, when I found one WYSIWYG Builder (FarPy GUIE) and tried it on "windows" i found that it lacks major features...

Seems, like Qt remains as the last option, or are there wysiwyg environment for wxPython... ?

---

### Post by irrdev on 2008-09-19
> **xavier_r said:**
> I just tried wxPython, used a lot of good and bad GUI builders...
The thing I disliked about them is that wxGlade, or wxFormBuilder, or others are not WYSIWYG...
and then again, when I found one WYSIWYG Builder (FarPy GUIE) and tried it on "windows" i found that it lacks major features...

Seems, like Qt remains as the last option, or are there wysiwyg environment for wxPython... ?
wxGlade and wxFormBuilder are definitely both WYSIWYG editors. wxGlade support wxPython output, and it uses a multiple-window layout similar to QT Designer. I have attached a screenshot of wxGlade's WYSIWYG Design feature in action. It really is quite straightforward. wxFormBuilder is even better than wxGlade IMO, but it unfortunately only supports C++ and XRC code creation. Both are great designers, and extremely useful for development.

**EDIT:** Added a screenshot of wxFormBuilder in action, too.

---

### Post by xavier_r on 2008-09-19
Are they WYSIWYG? with BoxSizers and GridSizers...
Because I tried developing today, and really dont get a feel like VBasic in windows...
I can't drag and drop... then again if I add buttons its not movable which is really absurd...

Maybe I am lacking some knowledge... :(

---

### Post by irrdev on 2008-09-19
In wxGlade, simply add a Panel to the Frame. You can then drag'n'drop/resize/move other widgets anywhere onto the Panel. In wxFormBuilder, the developers have intensionally disabled support for using drag'n'drop grids. By taking the time to learn how to use boxsizers, your application will in the long run greatly benefit for resizing to different screens and desktops. Microsoft is simply out to make everything easy for beginning developers with Visual Studio's lock-grid form designer - real commercial applications will never use this method, as it can display terribly on different screens. 

If you can't adjust to using BoxSizers in the near future, use wxGlade. On the other hand, go to the wxFormBuilder website, and I remember reading a fabulous tutorial on using BoxSizers to your advantage. Like almost everything, you quickly adjust to using the new method. :wink:

---

### Post by xavier_r on 2008-09-19
wxGlade hangs on panel add...

I think I'll spend some time learning BoxSizers

---

### Post by sakabato on 2008-09-19
you may also try , Mono via Windows Forms or GTK#. There is even a wx.net iirc

---

### Post by LaRoza on 2008-09-19
> **sakabato said:**
> you may also try , Mono via Windows Forms or GTK#. There is even a wx.net iirc

Windows forms for cross platform native looking development on Ubuntu?

---

### Post by xavier_r on 2008-09-19
damn... i made some wxPython apps, and even the simplest one gets a sie of 10MB when i compiled it into native win32 executable using cx_freeze...

if this is the case, then i am out with python, coz i need to distribute my application without worrying about size...

anyways, i think i am gonna only develop for win32, and leave mac and linux... even though MS sucks... :(

---

### Post by irrdev on 2008-09-20
Native C++ wxWidgets applications only add about 1-2mb to your executable, so that a medium-sized wxWidgets application is usually less than 3mb. This is definitely reasonable enough to redistribute. It actually isn't wxPython, but rather the Python runtimes themselves, that are really bloating your current wxPython apps to unreasonable sizes. Sometimes it is possible to use a tool such as [UPX]("http://upx.sourceforge.net/")  to compress your executable by up to 40%. Your mileage may vary, however. 

I would like to point out that Linux is quite capable of running Win32 applications through [Wine]("http://www.winehq.org"). You can also fully develop native Win32 application on Linux by installing packages mingw32, mingw32-binutils and mingw32-runtime from the repositories. I am currently use Mingw on Linux to develop software libraries for Linux. So, no, you can actually develop for both Windows and Linux when only using the win32 api.

**Note:** Yes, it is possible to compile wxWidgets applications as native Windows executables on Linux using Mingw. [There is a Howto on the wxWidgets wiki]("http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux"). I know several users on these forums who do this, and they actually advocate that it is faster than compiling directly on Windows itself!

---

### Post by sakabato on 2008-09-20
> **LaRoza said:**
> Windows forms for cross platform native looking development on Ubuntu?

err no. His requirement number 4 means that ?
4: The compiled software, must blend smoothly with the GUI interface in Mac Windows or Linux...

I still feel comfortable with look and feel of both winforms and gtk# in windows or in linux. I admit winforms on linux can be ugly at times and even not redner properly but gtk# looks smooth. But that's just me

---

### Post by scourge on 2008-09-20
> **LaRoza said:**
> Oh? wxWidgets fits the OP's criteria. QT may be easier and you may find it superior, but wxWidgets looks native by its design.

Even though Qt uses its own widgets, it still looks very native at least on Linux (also on Gnome, thanks to QGtkStyle), Windows and OSX. I've used both toolkits, and with wxWidgets my results weren't always as cross-platform as I wanted. For example drawing 2D graphics and setting up menus was something that I had to carefully test on all 3 platforms, and even had to use conditional compiling in a couple of places. No such problems with Qt; If the code worked on one platform, it worked on all of them.

---

### Post by CptPicard on 2008-09-20
Looks like this is another case of "impossible/not well understood requirements and expecting Linux to be like Windows so that crossplatformness comes for absolutely free", but... why not Java? In particular, the "executable" requirement is rarely as important as people make it sound like.

It's got great IDEs including GUI builders, runs nicely crossplatform, and desktop integration should be quite doable.

---

### Post by howlingmadhowie on 2008-09-20
> **xavier_r said:**
> Ok, So does wxPython have compile options in Windows to produce native win32 applications?

Also, how do I set up the devl environment in Ubuntu?

Thanks for your help :)

EDIT: I was looking into Adobe Flex today... Is that a good option?
What I called as a GUI Software, is actually called a Rich Internet Application...
So sorry, if I gave the wrong view, what I mean is developing a Rich Internet APplication...

one second. do you mean you want an application which runs in a browser?

---

### Post by intel on 2008-09-20
The entire thread has somehow overlooked the most obvious solution

Sun JAVA

There is no other reliable solution to your problem.

I suspect that if you are looking for a VisualBasic 6 replacement on Linux,
then you are going to have a tough time programming with Java

This is "by-design" ;-)
we don't want VisualBasic "$(r1P7 |<1DD13"'s writing apps for Linux

---

### Post by LaRoza on 2008-09-20
> **sakabato said:**
> 
I still feel comfortable with look and feel of both winforms and gtk# in windows or in linux. I admit winforms on linux can be ugly at times and even not redner properly but gtk# looks smooth. But that's just me

I don't know about winforms, but I think they would only look right if one is used to Windows. 

About GTK#, I didn't say anything about that.

> **intel said:**
> The entire thread has somehow overlooked the most obvious solution

Sun JAVA

There is no other reliable solution to your problem.

Except for the "looking native" part. ;)

---

### Post by CptPicard on 2008-09-20
> **LaRoza said:**
> 
Except for the "looking native" part. ;)

I don't do much anything on Windows, but the few times I've tried Java coding there, the Swing Windows look and feel looks just fine.

---

### Post by LaRoza on 2008-09-20
> **CptPicard said:**
> I don't do much anything on Windows, but the few times I've tried Java coding there, the Swing Windows look and feel looks just fine.

Perhaps I misunderstood the OP then. QT, Swing, etc look nice and work on the platforms, but they aren't native. wxWidgets is the only cross platform toolkit designed to look native. Perhaps I am being too literal and the OP just needs something that looks good on all platforms?

---

### Post by CptPicard on 2008-09-20
> **LaRoza said:**
> Perhaps I misunderstood the OP then. QT, Swing, etc look nice and work on the platforms, but they aren't native.

To tell apart Swing (or SWT by that matter which is actually backed by native widgets IIRC) in Windows L&F from "native" is actually pretty hard IMO.

[http://72.5.124.55/docs/books/tutorial/ui/features/compWin.html](http://72.5.124.55/docs/books/tutorial/ui/features/compWin.html)

---

### Post by scourge on 2008-09-20
> **LaRoza said:**
> wxWidgets is the only cross platform toolkit designed to look native.

Nope, it's the only toolkit designed use native gui widgets, but not the only one that looks native. For example, here are Qt's styles: [http://doc.trolltech.com/4.4/gallery.html](http://doc.trolltech.com/4.4/gallery.html). Add the new QGtkStyle there, and you've got native-looking widgets for every major platform.

---

### Post by sakabato on 2008-09-20
Instead of Flex , you may try Adobe Air as a viable option. It is the flex application cooked as a standalone application without browser. There are not much differences between air and flex. It's just air can access your computer's local resources and flex is bounded by your browser's security context. Recently Air 1.1 beta for linux is released. I've never programmed air but done some flex on linux. Things mostly went smoothly but had some internationalization issiues on linux 


For swing that is a big fat no. Swing is ugly and hard to program. The only swing application on linux I know is Frostwire (I like that program). But even all swing applications have issues with compositing mainly Compiz-Fusion. A few years ago when netbeans 5.0 emerged sun fixed some issues with swing introducing a new layout called group layout. Before that Swing layouts were simply a joke.  watch this if you don't believe me.[http://madbean.com/anim/totallygridbag]("http://madbean.com/anim/totallygridbag")

I think Sun is anti-midas. Everything it touches ends up turning into ****:)

---

### Post by pmasiar on 2008-09-20
> **xavier_r said:**
> damn... i made some wxPython apps, and even the simplest one gets a sie of 10MB when i compiled it into native win32 executable using cx_freeze...

if this is the case, then i am out with python, coz i need to distribute my application without worrying about size...

anyways, i think i am gonna only develop for win32, and leave mac and linux... even though MS sucks... :(

Prime example of a person who considers attitude a valid replacement to experience: has no idea what is doing and what are consequences of his bad decisions, but is absolutely sure that advice given is wrong, and good old Bill G  knows the best. ;-)

Of course freeze will bloat your code: you just asked to add whole freaking runtime. Windows does not let you to do that, because result would go to gigabytes 8-)

So please don't badmouth Python when you total lack of skill of understanding is reason of your failure.

---

### Post by CptPicard on 2008-09-21
> **sakabato said:**
> 
For swing that is a big fat no. Swing is ugly and hard to program. 

No it's not, it actually looks pretty native if you know to use L&Fs. As to hardness to program... nobody forces you to use all of the model-view-controller stuff, although it comes in handy in bigger projects.

> Before that Swing layouts were simply a joke.

The architecture is completely open, you can code your own if you don't like the default ones.

> 
I think Sun is anti-midas. Everything it touches ends up turning into ****:)

I'm not all that certain of this -- having a computing platform that runs what is I suspect a majority of large enterprise systems is hardly bad performance.

---

### Post by xavier_r on 2008-09-21
Thanx guys for all the help...
I have found a solution...

Its REALBasic...
Though its a bit costly... it builds, perfect applications on Mac, Windows and Linux...
And it hardly took me anytime to understand the stuff, even though I dont know about BASIC...

In about 2 hours, my application looked as I wanted it to be... And it runs perfectly in Mac, windows and Linux and yes, it cross compiles...

I feel a little bit sad about not choosing wxPython... I know what effort the open source guys give in developing such great programs... I still regard them...

But currently RealBasic solved my problem at hand...

Thanks guys :)
xavier

---

### Post by CptPicard on 2008-09-21
> **xavier_r said:**
> 
I have found a solution...

Its REALBasic...

:confused:

... *really?*

---

### Post by HotCupOfJava on 2008-09-22
Is it too late for me to weigh in with another vote for Java?

---

### Post by intel on 2008-09-23
He was looking for *BASIC, he found *BASIC,
end of story...........

---

### Post by irrdev on 2008-09-24
> **xavier_r said:**
> Thanx guys for all the help...
I have found a solution...

Its REALBasic...
Though its a bit costly... it builds, perfect applications on Mac, Windows and Linux...
And it hardly took me anytime to understand the stuff, even though I dont know about BASIC...

In about 2 hours, my application looked as I wanted it to be... And it runs perfectly in Mac, windows and Linux and yes, it cross compiles...

I feel a little bit sad about not choosing wxPython... I know what effort the open source guys give in developing such great programs... I still regard them...

But currently RealBasic solved my problem at hand...

Thanks guys :)
xavier

Everyday I learn something new! When I was a beginner programmer running Windows years back, I was turned away from REALbasic by the fact that even the "Personal Edition for non-Commercial use" cost $100.00. While both the Windows and Mac platforms cost at least this much, it turns out that the Linux Personal Edition of REALbasic is free. While I prefer using C++, this product should definitely be recommended for beginning programmers on Linux. It even has built-in compilation for both the Mac and Windows from Linux. While it is possible to cross-compile for Windows from Linux using C/C++, it sure can be hassle to install/use the mingw packages. 

While I am definitely a proponent of open-source and C++, REALbasic is a product which would definitely draw software companies to Linux. I don't think I'll use this product myself (being a wxWidgets fan), but it definitely looks promising. While it is *BASIC, it does appear to have a very OO syntax. At the very least, it is at least worth checking out the [demos page]("http://www.realsoftware.com/products/realbasic/tour/"). Reminds me of the open-source IDE [Gambas]("http://gambas.sourceforge.net/"), except that it unfortunately only supports Linux. :wink:

---

### Post by themusicwave on 2008-09-24
Even though the decision has been made(yes I read the whole thread).

I just wanted to chime in another vote for Java + Netbeans.  It has a nice GUI editor and you can easily make it look native.  All it really takes to make Swing look native is one line of code:

Before you make any frames just pop in this line of code and you should get a native look and feel:

UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());

You should also import javax.swing.UIManager;

Then you will not get the ugly default Swing theme.


Python would be a good option as well.

Best of luck with REALBasic, I have never used or heard of it, but I guess if it works then go for it.

However, I may have found a snag.  According to Wikipedia: "The standard edition only compiles programs for the platform that the IDE is running on (either Windows, Linux or Mac), and does not allow access to databases other than the built-in REAL SQL Database"[Wikipedia - REALBasic]("http://en.wikipedia.org/wiki/REALBasic#Language_features").

So according to this, unless you want to pony up $500, you won't be able to cross compile with REALBasic.  You would need all three platforms to build your application on.

This may just ruin the REALBasic approach.

---

