---
title: "Writing GUI app that can be ported to Windows"
date: 2007-11-13
forum: Programming Talk
---

### Post by bsmith on 2007-11-13
Hi,

I need to write an application that can do some simple analysis of images for a friend of mine, it needs to be able to load a jpeg or whatever and report what colors the image is composed of and in what percentage, it's to estimate how much wool is needed to make tapestrys.

Anyway it needs to be able to be ported to windows with a nice gui etc...

I have not had much experience with glade or any gui stuff apart from my pre linux days with visual basic (argh). So any direction would be greatly apreciated about how to go about writing this program.

Thanks in advance.

---

### Post by j_g on 2007-11-14
See my replies in your other thread.

As mentioned, use the C library functions in lieu of any Win32 API, or Linux "syscall". For example, if you need to open a file, don't use Win32's CreateFile(), nor Linux's open(). Use the C library's fopen(). If you need to allocate memory, don't use Win32's GlobalAlloc, nor Linux's mmap. Use the C library's malloc. Leverage the C library.

I'll tell you right now that there is no Win32 API to load jpegs. Windows has a COM component (forget what it's called offhand, but its OlePicture() function loads a jpeg). COM coding is totally not portable to Linux. So what I'd do is look around and see if there's some _simple_ open source jpeg reading library that is available for both Win32 and Linux, and use that.

Keep your GUI code separate from your jpeg analyzation code, and it shouldn't be difficult to port the GUI. Some people will tell you to use cross-platform GUI stuff like wxWindows, but that stuff isn't installed by default on a Windows system. So, your friend will have to install it and set it up. And frankly, most of these big, complex cross-platform packages are a horror to install and setup on Win32. If it uses "environment variables" (and lots and lots of complicated Linux packages do), that is a particular annoyance for Windows users. Unlike Linux, Win32 environment variables are "per session" only, and not system-wide. Using environment variables on Win32 is a no-no. That is one of those deprecated things. Win32 has much better native means of doing what environment variables do. The only cross-platform stuff that really works well on Windows is the small, self-contained stuff (like a single DLL), packaged by someone who understands and has experience following Microsoft's guidelines for installation software.

So if you go with the native Win32 GUI, at least you won't force him to deal with installing and setting up an entire, second graphical environment (which typically is designed first and foremost on Linux, and therefore doesn't leverage preferred ways of doing things on Win32, such as follow MS's installation guidelines).

---

### Post by bsmith on 2007-11-14
Thanks that was the information that I was looking for, so ill look for a portable library for a simple portable library to handle the jpegs.

But with the GUI, are you saying that I will need to create a linux one with glade or whatever, and also make a windows one (is there free development software for doing this under windows).

But I think I have enough to get me started, Thanks again

---

### Post by smartbei on 2007-11-14
Somewhat contrary to j_g, if your goal is to whip out a usable gui application as fast as possible, I would recommend that you do use a cross-platform gui toolkit.

I would recommend using python for most of the application, and if you need more 'speed' for a certain part use C (just for it). With python it can be very simple to develop an application with either GTK, wxWidgets (BTW - j_g, that is what it's called) or even Tkinter, which would work fine as long as you are doing something relatively simple. Tkinter also has the benefit of being included with Python, so your friend won't need to install anything else. There are also packages such as py2exe which would allow you to create an exe out of your python application so that it is the only thing that must be installed.

---

### Post by bsmith on 2007-11-14
OK, i checked out some of j_g's other threads, mainly "glade to c++" and got a few more good pointers on writing good cross platform code.

And smartbei, I will have a look into Tkinter, I haven't learnt much python yet, but it seems that it should be my next step to becoming the greatest programmer in the world :) so ill give it a shot.

I don't want to start any wars between you champs about whether to create cross platform UI's or not, so Ill try smartbei's approach while keeping the back end separate from the UI, and if I run into to many problems in the porting Ill just rewrite the UI.

Thanks again, and wish me luck

---

### Post by DavidBell on 2007-11-14
I've only done a little bit but C++ and wxWidgets seems to work. In my case I go from MSVC to GCC in Linux. 

I do the app in MSVC using exclusively wx classes and functions; when it's working in windows and compiles with no warnings I copy the source to linux and recompile with gcc - you'll probably get some more warnings but once you fix those it's generally good to go.

If your GUI is not overly complicated I would do it all in C++. Those GUI in one language, functions in another, installer in something else sound good on paper but aren't worth it in my experience.

DB

---

### Post by slavik on 2007-11-14
look into using SDL (platform independent) and any of GTK, QT4, WxWidgets

---

### Post by [h2o] on 2007-11-14
Or you could just use Java and don't have to worry too much.

Python + glade + GTK works also, but then you need to package GTK for windows as well, since it is rarely installed by default. ;)

---

### Post by j_g on 2007-11-14
Windows user: "G what? SDL??? I don't want that! I always use protection when I have sex. Java? Of course I know what that is. But I don't want it either. The last time I drank coffee, it spilled all over my keyboard and I had to buy a new one. Don't you have any software that just runs on my system like all the other stuff I use?".

Note to humorless moderators: It's a joke.

---

### Post by bsmith on 2007-11-14
j_g, I here what you are saying, and I agree, so does this mean that python is out of the question as it is interpreted, or can it be compiled.

Or should I stick to C/C++

---

### Post by bsmith on 2007-11-14
I have also found an image loading library called DevIL [http://openil.sourceforge.net/]("http://openil.sourceforge.net/") it seems like it can do everything, I just don't know if it is as simple as I would like.

---

### Post by kknd on 2007-11-14
If you want 100% portable, without any change, Java + SWING rules.

But you can do it with wxWidgets (preference to C++), that is also easy to port, with Gtk+ (exotic on windows), maybe Ultimatepp (very portable too).

---

### Post by Auria on 2007-11-14
For image loading i also found that one : [http://freeimage.sourceforge.net/](http://freeimage.sourceforge.net/)

though if you choose to go wx image loading is included in the package.

---

### Post by Tuna-Fish on 2007-11-14
Python cannot pe precompiled, but it can be packaged together with the interpreter in a single .exe. This can also be made to contain wxwidgets for windows, so python & wxwidgets is a safe bet.

(edit): try py2exe

---

### Post by bsmith on 2007-11-15
> For image loading i also found that one : [http://freeimage.sourceforge.net/](http://freeimage.sourceforge.net/)

though if you choose to go wx image loading is included in the package.

That library looks better than the one I found, thanks.

> Python cannot pe precompiled, but it can be packaged together with the interpreter in a single .exe. This can also be made to contain wxwidgets for windows, so python & wxwidgets is a safe bet.

So would the end user have to install wxwidgets, or could it be included in the single exe with the interpreter. Because that would be perfect

---

### Post by smartbei on 2007-11-15
It is included in the same exe. They won't have to install either Python or wxWidgets - just your program.

---

### Post by bsmith on 2007-11-15
smartbei or Tuna-Fish, could you recommend a tutorial on how to create GUI applications with python and wxWidgets, because that sounds too great to be true. Thanks for all your help.:)

---

### Post by smartbei on 2007-11-15
See [http://wiki.wxpython.org/index.cgi/How_to_Learn_wxPython](http://wiki.wxpython.org/index.cgi/How_to_Learn_wxPython) for a pretty thorough beginning.

For a LONG tutorial going from beginning to advanced and covering tons of controls/widgets that you may need to use, see [http://wiki.wxpython.org/AnotherTutorial](http://wiki.wxpython.org/AnotherTutorial)

For reference and code snippets see [http://wiki.wxpython.org/wxPython_Cookbook](http://wiki.wxpython.org/wxPython_Cookbook).

For a bunch of information see [http://wiki.wxpython.org/](http://wiki.wxpython.org/)

By the way, what kind of image analysis do you need to do?


Good luck!

---

### Post by bsmith on 2007-11-15
> By the way, what kind of image analysis do you need to do?

All it needs to do is work out what percentage of the image is composed of what colours, and then match the colours to a colour catalogue. Which should not be too hard.

And python is awesome, I have spent like half an hour learning it and am amazed at how awesome it is, Why have I not learnt it before:confused:

Anyway, I am well on my way, thanks again.

---

### Post by Shin_Gouki2501 on 2007-11-15
java swing or SWT i would suggest.

---

### Post by pmasiar on 2007-11-15
> **Tuna-Fish said:**
> Python cannot pe precompiled, but it can be packaged together with the interpreter in a single .exe. This can also be made to contain wxwidgets for windows, so python & wxwidgets is a safe bet.


I am not sure why you need compiled Python? Do your users complain about the speed? If not, why bother?

Most  Python low-level libraries are in C, Python is just simpler interface to them. PIL - Python Image Library - might be of interest. And if your GUI needs are simple, EasyGUI is simpler than any other GUI toolkit on the market, in good Python spirit.

Remember, premature optimization is root of all evil.

---

### Post by bsmith on 2007-11-15
> I am not sure why you need compiled Python? Do your users complain about the speed? If not, why bother?

Most Python low-level libraries are in C, Python is just simpler interface to them. PIL - Python Image Library - might be of interest. And if your GUI needs are simple, EasyGUI is simpler than any other GUI toolkit on the market, in good Python spirit.

Remember, premature optimization is root of all evil.

Its not for speed, its just so that it is easier for the windows user to setup the program, and I will look into PIL and EasyGUI also, Thanks.

---

