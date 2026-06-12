---
title: "glade help"
date: 2007-02-28
forum: Programming Talk
---

### Post by joflow on 2007-02-28
At the risk of sounding like an idiot...I was wondering if someone could explain to me how to resize controls in glade.  I've tried everything and I've looked everywhere and can't find a thing.  It seems that the controls take up as much space as the underlying container will allow...I would like precise control over size like in Visual Studio.  

Thanks.

---

### Post by joflow on 2007-02-28
Also...I've been reading about stetic and I was wondering if anyone has it integrated into monodevelop?  I've installed it from the repo and can launch it from the commandline...oddly enough there is no icon for it in the menu and it doesnt seem to run when monodevelop starts up.

---

### Post by j_g on 2007-03-01
Each container allows you to specify how many controls you're going to put in it. So, if you want to put 3 controls in a container, just specify that. The controls will be sized to fit the container. (ie, You're not limited to one control per container, so a single control doesn't necessarily fill its container).

As far as individually setting each control's size, you can find a "Width request" and "Height request" settings. When you check them, you can enter an width and height amount, respectively. But note that this is a request, and the window manager may not necessarily adhere to your request.

---

### Post by joflow on 2007-03-01
> **j_g said:**
> Each container allows you to specify how many controls you're going to put in it. So, if you want to put 3 controls in a container, just specify that. The controls will be sized to fit the container. (ie, You're not limited to one control per container, so a single control doesn't necessarily fill its container).

As far as individually setting each control's size, you can find a "Width request" and "Height request" settings. When you check them, you can enter an width and height amount, respectively. But note that this is a request, and the window manager may not necessarily adhere to your request.

THANKS!!  I thought I was missing something or that the version in Fiesty repo had a bug.  You've cleared that up for me.  

Quick question:  Do you feel in any way limited by this approach as opposed to the dump a control anywhere and make it any size Visual Studio style approach?  And is there any way to have precise control of the height and width of a particular table in a container. (I figured out that you can place containers inside containers.)  Thanks again.

---

### Post by joflow on 2007-03-01
just found the fixed position container (atleast there is one on the Win32 version of glade)...I dont know how I could have overlooked that.

---

### Post by j_g on 2007-03-01
Oh, you're talking about some Win32 port of Glade?

I've never used such a thing, so I have no idea how it differs from the Linux version. My comments were about the Linux version.

As far as the Windows versus Linux "control resizing" thing. MS controls are not automatically resized when their parent dialog/window is resized. Windows leaves it up to the application to take care of modifying the size/appearance of any controls when the parent dialog/window is resized. This makes sense. For example, for a button, when there is more space available, you may want to change to a larger font for the label, not just increase the size of the button itself (and leave the label the same size) like how Linux managers seem to do when a button is allowed to increase its size. And an application may want to do other individualized control resizing behavior, for example, changing a label to use elipses when it shrinks to a certain size.

Linux seems to take the approach that it should be the window manager, not the app, that has ultimate say in resizing a control. Of course, you're supposed to pack things in a way so that it works the way you'd like it to. This is done to ostensively relieve the app of having to resize controls on its own. My experience so far has shown that, sometimes it makes sense, and sometimes it just needlessly adds complexity to the UI creation. I prefer the Windows way because it's initially simpler, but also gives the facility to handle any sort of resizing challenge.

---

### Post by lnostdal on 2007-03-01
you can have full control in gtk+ also .. just set a width/height-request and disable the expand and fill-properties ..

so you can have full control at runtime of both position and size of each widget if you want this -- just as under win32 ..  i doubt you'd actually want this though :)

---

### Post by joflow on 2007-03-02
> **j_g said:**
> Oh, you're talking about some Win32 port of Glade?

I've never used such a thing, so I have no idea how it differs from the Linux version. My comments were about the Linux version.

As far as the Windows versus Linux "control resizing" thing. MS controls are not automatically resized when their parent dialog/window is resized. Windows leaves it up to the application to take care of modifying the size/appearance of any controls when the parent dialog/window is resized. This makes sense. For example, for a button, when there is more space available, you may want to change to a larger font for the label, not just increase the size of the button itself (and leave the label the same size) like how Linux managers seem to do when a button is allowed to increase its size. And an application may want to do other individualized control resizing behavior, for example, changing a label to use elipses when it shrinks to a certain size.

Linux seems to take the approach that it should be the window manager, not the app, that has ultimate say in resizing a control. Of course, you're supposed to pack things in a way so that it works the way you'd like it to. This is done to ostensively relieve the app of having to resize controls on its own. My experience so far has shown that, sometimes it makes sense, and sometimes it just needlessly adds complexity to the UI creation. I prefer the Windows way because it's initially simpler, but also gives the facility to handle any sort of resizing challenge.

I was just using the glade win32 app because I was on windows at the time.  The original question was in regards to the linux app.

---

### Post by theDentist on 2007-03-02
I found it is best to unlearn the Visual Studio way and let the Window manager do the work for you of finding the best sizes for widgets and windows.  I used to spend far too much time sizing controls in VC++ 6 trying to get them to look correct and symetrical.  I was happy to off load the task.

---

### Post by azazel00 on 2007-03-02
> I found it is best to unlearn the Visual Studio way and let the Window manager do the work for you of finding the best sizes for widgets and windows. I used to spend far too much time sizing controls in VC++ 6 trying to get them to look correct and symetrical. I was happy to off load the task.

I have to disagree. The developer should have ultimate control over how his application behaves. Even if it means more work. VC++ 6 is quite dated, and a lot has been done to enhance productivity in the GUI arena. 

You can probably guess I'm a .NET junkie (trying to move into GTK+) :P

I dont want to start an IDE war here. But I guess there's a thing or two that could be borrowed from VS that would help increase developer productivity. Working with the GTK API is a bit cumbersome from what I have tried so far.

I do believe that it requires a lot more skill to program against GTK than to drop a couple of  controls in an IDE. The question is: Do we really want to spend more time designing the UI rather than spend that time developing the solution to the problem we are trying to solve?

---

