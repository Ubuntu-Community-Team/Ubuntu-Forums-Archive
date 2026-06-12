---
title: "Cross platforms editor with complex GUI"
date: 2010-07-10
forum: Programming Talk
---

### Post by KillKRT on 2010-07-10
Hi!

I'd like develop an application with a complex GUI (combobox with animation, charts with spline, transparent layers, ...). I have a good experience with C# 2.0 and I'm studying WPF.
Unfortunately I read that there is no plan to port WPF on Mono :icon_frown:

I was thinking about the difficulty to create my custom GUI control using OpenGL (using [OpenTK]("http://www.opentk.com/"))... But I feel it will be a hard work (integration with GTK#, debugging, hard to use to design form).

Another possibility is to use Java (with [JOGL]("http://jogamp.org/jogl/www/")), but I'm not very skilled with it, and I don't know about performance issues.

Last option is C++, but I've to do a big *revision* (years since last time I used it), and I find it hard to develop GUI and portable application #-o (Maybe I'm wrong!).

What is your opinion/advice?

Tnx!

P.S.:
Sorry for my English. :oops:

Thank you.

---

### Post by KdotJ on 2010-07-10
Netbeans is a great java IDE, with GUI building options. It uses Swing for the GUI components and the IDE itself has some awesome features. It is in the ubuntu repos. 

Also, for C++, there is Qt Creator (though leaning more toward KDE look) which has a good GUI builder

---

### Post by KillKRT on 2010-07-10
> **KdotJ said:**
> Netbeans is a great java IDE, with GUI building options. It uses Swing for the GUI components and the IDE itself has some awesome features. It is in the ubuntu repos. 

Also, for C++, there is Qt Creator (though leaning more toward KDE look) which has a good GUI builder

Thank you!
My problem is that I have to develop new controls with advanced graphics (buttons and comboboxes with animation, transparent panels, timeline charts with embedded graphics, ...). I'm looking for a language/framework that allows me to create such controls and easily use in a GUI. I love C# and Java because of their *elegance* and pure OO approach, but I know that for performance issues, C++ is the best!
I'm not a good C++ programmer because I leak of experience, and I find a little hard to use C++ IDE, but if there is no alternative I will try my best... ;)

Tnx.

---

### Post by myrtle1908 on 2010-07-10
Whilst I don't care much for NetBeans (I'm more of an Eclipse man) there really is no competition when it comes to Java + GUI.

How complex are your controls/widgets?

---

### Post by KillKRT on 2010-07-10
> **myrtle1908 said:**
> Whilst I don't care much for NetBeans (I'm more of an Eclipse man) there really is no competition when it comes to Java + GUI.

How complex are your controls/widgets?

Something like Blender 2.5 controls:
[Blender 2.5]("http://wiki.blender.org/uploads/8/88/2_5_mockups_01.png")
[http://dev.blender.ir/images/first-attempt-to-import-all-sensors-to-nodal-logic.png]("http://dev.blender.ir/images/first-attempt-to-import-all-sensors-to-nodal-logic.png")

And timeline automation control like: [http://audiotuts.s3.amazonaws.com/343_looping/multi-1.jpg]("http://audiotuts.s3.amazonaws.com/343_looping/multi-1.jpg")
[http://ronrisman.files.wordpress.com/2009/04/cs4_premiere_pro_11.jpg]("http://ronrisman.files.wordpress.com/2009/04/cs4_premiere_pro_11.jpg")

---

### Post by evstevemd on 2010-07-10
Take a look at wxwidgets and wxUniversal

---

### Post by efikkan on 2010-07-10
For general purpose applications with performance and stability I would recommend using Qt and C++. Java applications end up sucking resources, lacking performance, a huge amount of code and work to get swing working, and it tends to behave a bit different on some computers.

By using OpenGL, do you mean large parts or the complete design i OpenGL?(not using Qt, swing, mono or anything?)
OpenGL is great for performance, but it might be some work if you intend to build a GUI from the ground up in OpenGL. If you do it right it would be awesome. I actually use OpenGL quite a lot myself, but not OpenTK or as a part of some other GUI.

---

### Post by KillKRT on 2010-07-10
> **efikkan said:**
> For general purpose applications with performance and stability I would recommend using Qt and C++. Java applications end up sucking resources, lacking performance, a huge amount of code and work to get swing working, and it tends to behave a bit different on some computers.

By using OpenGL, do you mean large parts or the complete design i OpenGL?(not using Qt, swing, mono or anything?)
OpenGL is great for performance, but it might be some work if you intend to build a GUI from the ground up in OpenGL. If you do it right it would be awesome. I actually use OpenGL quite a lot myself, but not OpenTK or as a part of some other GUI.

Yes, I mean build a GUI from scratch with OpenGL, developing a custom toolkit :!:

I always wonder how are built complex GUI of *media systems* like Cubase, Blender, Adobe Premiere, Maya, Reason...

Maybe I'd better use C++ and Qt and use only where is necessary a OpenGL *canvas*.

Thank you.

---

### Post by efikkan on 2010-07-10
It's up to you how much time and effort you want to spend on the GUI. And it's a bit hart to give advice when I'm not familiar with your project. Developing a GUI in Qt is a lot quicker, and if the application would work just as fine this way, then you can focus your effort on completing the features. But if a quick and fancy GUI is important for the application you might want to consider OpenGL.GUI toolkits for OpenGL does exist, but I'm not familiar wich such. You will have to consider what are the requirements for your application. I really like the idea of a GUI in OpenGL.

---

### Post by texaswriter on 2010-07-10
Sorry for the misunderstanding.

---

### Post by KoRnholio on 2010-07-11
> **texaswriter said:**
> While this is your opinion, it is nonetheless not true. The statement of such when not true amounts to little more than trolling. 

To believe that Java is a good model with respect to GUI is one thing, to state [as a fact] that it is really "the only thing' is an entirely different matter. 

It is easy to understand how programming in Java [especially GUI] apps is the same across platforms / OS. This would have been a simpler and more truthful thing to state.

I think you are misinterpreting his statement. I read that sentence as saying that Netbeans is "the only thing" to do Java + GUI with, not that Java is "the only thing" to make GUIs in.  It's an Eclipse fan begrudgingly giving Netbeans praise.

---

### Post by crankonaut05 on 2010-07-12
You can check out:

[http://www.cranksoftware.com/products/crank_storyboard_designer.php](http://www.cranksoftware.com/products/crank_storyboard_designer.php)

You can build your UI using images.  The backend can be written in whatever and interfaced in to the UI using a messaging API. 

Rodney

---

### Post by zmoky on 2010-07-25
I'm in a very similar situation here. 
I've installed ubuntu 10.04 and now I'm trying to find the best development enviroment for great performance, and easy gui design tools. seems the best choice is netbeans, but I still use c++ because of it's performance. 

I've looked over wxWidgets, gtk and other but i still couldn't find anything to please me.

I've worked with Flex/Flash Builder, Visual Studio, and Netbeans over time, and I really want to take in consideration what linux(ubuntu) offers for my next application which requires a slightly complex user interface.

I'm also interested in which is the best 3d engine that is best to develop on linux (ogre3d, irrlicht, ...)

---

### Post by phrostbyte on 2010-07-25
I don't think OpenGL is really the best solution for developing GUIs. OpenGL is very low level.

You can make some complex GUIs with GTK+ or Qt. I don't know about the "animated" combobox thing though. :)

---

### Post by zmoky on 2010-07-27
I've choosed Qt after all for GUI programming. It seems to be the only solution on what I want from ubuntu development. I hope I'll make a good team with ubuntu using qt :)

as far as using a 3d engine, i thing ogre3d and irrlicht still remains on my list, irrlicht being actually the first one on the list but i still have to study more about this two.

---

### Post by KillKRT on 2010-07-27
> **phrostbyte said:**
> I don't think OpenGL is really the best solution for developing GUIs. OpenGL is very low level.

You can make some complex GUIs with GTK+ or Qt. I don't know about the "animated" combobox thing though. :)

OpenGL is very low level, but it is very fast! ;) I realize that developing a GUI toolkit (using OpenGL) is a huge and maybe mad work... But it is also attractive! :twisted:
Mumble... Maybe I'd better try to give a look to Qt in order to undestard how is flexible and fast...

---

### Post by WitchCraft on 2010-07-27
Try CodeBlocks and wxWidgets.

Or install monodevelop and use C#.

---

### Post by Newbie2910 on 2011-02-26
Been pondering the same thing.  I have a large app I developed in WPF.  Now I find that I will have to support Linux within probably two years.

So, I am considering porting to Silverlight/Moonlight.  I hope the Moonlight 4.0 release will give me enough flexibility to make a cross-platform app to run on both Linux and Windows via a browser.

---

### Post by zmoky on 2011-02-27
> **Newbie2910 said:**
> Been pondering the same thing.  I have a large app I developed in WPF.  Now I find that I will have to support Linux within probably two years.

So, I am considering porting to Silverlight/Moonlight.  I hope the Moonlight 4.0 release will give me enough flexibility to make a cross-platform app to run on both Linux and Windows via a browser.

My ipinion is that the only clean and true3 crossplatform it's solved only by Qt from Nokia by making releases for each OS, Flex from Adobe, Javascript Frameworks (ex: jQuery), and Java all this inside browser very easily.

When you choose technologies WPF (very dedicated for Windows), you should expect to not be fully supported or to have a great deal of issues when making the conversion or adaptation.

I suggest you to port somehow the client application in something that can really be called crossplatform and use your current services (if any).
The tecnologies i strongly suggest to use are Java on the first place, Qt on the second , Javascript and last Flex Builder

Good luck.

---

### Post by directhex on 2011-02-27
MonoDevelop is both a good editor to consider - and an advert for itself. It's a GTK# app, available for Windows, Mac and Linux, with an integrated GTK# designer.

---

### Post by zmoky on 2011-05-22
[I]After some time passed I've ended by using Qt IDE for user righ interfaces applications and netbeans where I didn't needed the GUI: server application.

for now this is working great.

if netbeans had a GUI editing system for GTK that would be great
[/I]

---

### Post by mmix on 2011-05-22
GLV (Graphics Library of Views)
[http://mat.ucsb.edu/glv/](http://mat.ucsb.edu/glv/)

[img]http://mat.ucsb.edu/glv/gfx/Screenshot1.png[/img]

---

