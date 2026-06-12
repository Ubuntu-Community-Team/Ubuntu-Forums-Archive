---
title: "Fortran program needs a GUI"
date: 2006-04-27
forum: Programming Talk
---

### Post by aeroRunner on 2006-04-27
Here's the deal.  I am an engineering graduate student and my research/thesis work deals heavily with modifying an existing fortran program.  The program is long, complex and takes a very long time to run, so recoding in another language is not an option.  Plus, that decision is not up to me.

The thing is, we need a little GUI to make our customer happy and Compaq Visual Fortran is just not cutting it in this respect.  So, I am looking for suggestions.

I have been doing a little research and asking around and I currently have two votes for Python and one vote for Perl.  So what do you guys suggest?

Some things to keep in mind:
 - The language must be easy to use and easy to learn.  I can't spend too much time on the GUI because I have real work to do on the program.
 - I have taken classes in C, C++, and MATLAB but have never used C or C++ outside of class.
 - I am stuck on a Windows machine for now, but it would be nice to be able to use the program on a Unix box in the future.
 - Free is good.

Finally, if you have any links to tutorials and such handy, I'd appreciate you sharing them....especially, information on how to call outside programs and building GUIs.

Thanks in advance.

---

### Post by roncrump on 2006-04-27
On windows I have used Delphi to provide a front-end - with the Fortran compiled as a DLL rather than a program. Maybe a  similar approach could be taken with Free Pascal, which is available for both Windows and Linux.

Pascal is very fortran-like, so wouldn't be too hard to get into, and if Free Pascal is anywhere near as easy to develop a GUI in as Delphi, it may be a simple solution.

On another track, what about a web-style interface - the fortran program could then run on a server of choice with the UI developed in (eg) PHP. Depends a bit on how rich an interface is required.

I don't really know anything much about python or perl, but know people that swear by python for a lot of stuff - it may have to be something I learn soon. Meant to be easy.

---

### Post by hadian on 2006-07-24
i think it is better to use something in C or C++. since you can do mixed C/Fortran programming. using Wxwidget or QT maybe solve your problem. both are multiplatform and you can run your code on Windows or *nix.

---

### Post by xtacocorex on 2006-07-24
aeroRunner, this sounds like something I would do. 

I'm currently working on an [airfoil generator]("http://robert.wolterman.googlepages.com/foilgen") and I have all my backend math stuff in FORTRAN. I moved it over to C++ because the Python pipes to FORTRAN didn't work out, plus I needed to refresh my C++.

If you go the Python route to generate a GUI, you can use f2py to wrap the FORTRAN subroutines into Python modules that are callable. I haven't used it yet, but will probably have to when I integrate a flow solver to my program. Python will work in Windows, but I don't know how easy it would be to get the GTK to port over. wxWindows would be a better solution since it's cross platform already, but I haven't used it and don't know if there are any programs that assist in GUI creation with that.

If you use GTK, you can use Glade to design the interface. There are lots of good PyGTK tutorials on the net. Although the tutorials aren't specific to Glade, it's pretty intuitive on how to get the Glade stuff to work. It also allows you to spend less time creating the GUI. 

I also plan on creating a GUI to a NASA FORTRAN 77 code that I've been using for the last 3 years to make it easy for new users to learn the program that will display the 3D geometry output and the flow field data. I'll probably have to use one of the Python 3D/OpenGL classes.

If you need some initial links for Python stuff, PM me. I also may be able to help with stuff, so just ask.

---

### Post by Van_Gogh on 2006-07-25
I've used f2py and it was really great. However, if I remember correctly it doesn't support custom types, something which may or may not be a problem for your app.

---

### Post by Eric_T on 2006-07-26
Would be easier if you told us what features the GUI would need.
I've made some GUIs in C#, Visual Studio .NET makes it really easy to link the GUI to FORTRAN, and creating a simple GUI is pretty much just point and click.
Nowadays, I pretty much only use scripts in bash or python to generate input files(using namelists in fortran). If you only need to change parameteres, GUIs often complicates stuff more than it helps, IMO... or to put it another way, the time you have to spend to get a decent GUI is much better spent on improving the calculation part of the code.

---

### Post by cshake on 2006-08-28
Don't know if you're still looking, but this summer I did almost exactly what you're mentioning, modified a fortran program that my professor coded back in 1985 and gave it a GUI.

I used MATLAB on the university computers to generate a GUI and installed G95 and gnumex to compile the FORTRAN code as a mex file (matlab style dll), calling that from the MATLAB code. It worked fairly well, but I would have to restart MATLAB every time I wanted to recompile after running the code because it somehow locked the dll as read only once it first ran.

It's quite simple to first set up, run "guide" in matlab (7.0+) and there are simple gui templates.

---

### Post by neoflight on 2006-11-01
i would suggest checking out TCL/TK or glade...
I am not an expert but i know someone in my lab uses tcl/tk to make gui access to fortran. there are plenty of resources available in the net...TCL is pronounces 'tickle'...!!!

enjoy

---

### Post by tseliot on 2006-11-01
I suggest you to use Python.

Python can use GTK, QT and WXwidgets

---

