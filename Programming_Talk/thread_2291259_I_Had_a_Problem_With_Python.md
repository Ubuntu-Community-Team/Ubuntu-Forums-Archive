---
title: "I Had a Problem With Python"
date: 2015-08-18
forum: Programming Talk
---

### Post by brian-mccumber on 2015-08-18
Well I was going to ask a question about installing wx module for python but after a quick google search I figgered it out. So instead I will ask what kinds of scripts or apps have you guys made with python on Ubuntu? Just trying to get a conversation started here. I really haven't messed with python that much but have read good things about it. I just want to see what other people have used it for maybe find some inspiration.
:popcorn:

---

### Post by ian-weisser on 2015-08-18
Python is a good, general-purpose language to accomplish many tasks...as are a constellation of other languages.
I find a knowledge of Python quite handy when wandering through Ubuntu  source code to help test, debug, or package. Many Ubuntu services are  written in Python.

I have used Python for GUIs, network interfaces, image processing, data manipulation/merges/filters, html scraping, dbus services and/or clients, and much more.
I have realtime transit displays written in Python.
I have network scanners written in Python.
I have an entire custom weather AppIndicator, and tree of subordinate services, written in Python.
Pieces of my backup service are written in Python.
I use Python interfaces with LibreOffice and QuickBooks for customized billing, CRM, report output, and transaction input. 
My brother-in-law uses Python for brain imaging.

---

### Post by brian-mccumber on 2015-08-18
Wow that is an impressive list. And the reason I started messing with python is because I saw that it was installed in Ubuntu when I installed it a few days ago. I just installed the wx library but I haven't figured out how to use it yet but I saw this gui creator called glade that I was thinking of trying out. It is supposed to make guis that can be used in python, c++, and freebasic but I think it uses gtk not wx. Have you used the wx library or glade to make your guis in python or did you use something else? I do have c++, python, and free basic all hooked up and compiling from Geany, so what code editor for python do you prefer? 

I came from a Windows Visual Studios programming environment and if you've never used it, making window forms is a snap with that software so finding an equivalent would be a bonus. I don't want to have to use the terminal for everything.

---

### Post by ian-weisser on 2015-08-19
On Windows, I use IDLE. In Ubuntu, I just use an editor (Gedit) and a terminal window.
For the way I work in Ubuntu, the terminal is easy and fast and flexible. My Windows applications tend to be bigger, more self-contained. My Ubuntu applications tend to be much smaller, using system APIs for much more work, and much more distribution of work between asynchronous child processes. Your mileage may vary.

For Ubuntu converged applications, which might run on a wide  variety of devices and displays (or headless), best practice is for the user interface  to be written as a rather minimal dbus client, with all the real logic  and data written as a headless dbus service. Separation of UI and core  functionality into separate processes, with dbus the glue that makes  them work. Many benefits: The client and server can be written in different languages, the code design in usually cleaner and easier for other to understand, your API is useful (since you are using it, too), free access to other app APIs and system services, and test cases are simple to write (since you're just testing the API).

In other words, it's more about getting the design right and using the system tools properly. Less about generating lots of code.

If you're coming from a Windows environment, I recommend a bit of experimentation using dbus (python-dbus) to query services like Network Manager or GeoClue or File Manager or Contacts, etc. Using services, including services you create for the purpose, may significantly reduce the amount of user interaction and code. For example, using the File Manager's existing features is much easier than writing a duplicate yourself.

Some will say that using the File Manager's Python bindings is superior to using dbus bindings. Perhaps, perhaps not - your design will dictate which path is best.

I think Tkinter is a good cross-platform starting point for your own from-scratch GUI, and is included with Python in Ubuntu. Others will certainly disagree with me on that.
Once you understand tkinter, other ways (wx, python-qt, etc.) are easy to pick up.

---

### Post by brian-mccumber on 2015-08-19
I appreciate the tips. I did go ahead and install [Glade Interface Designer]("https://glade.gnome.org/") and I think for what I plan to do it will work well but I will look into tkinter. So lets see if I got this right, python-dbus is like the My namespace in Windows?

---

### Post by ian-weisser on 2015-08-19
I am unfamiliar with the "My namespace in Windows".

python-dbus is the Debian and Ubuntu software package that provides python bindings to the dbus interprocess communication hub. It should already be included with your default install of Ubuntu. It's rather core functionality.

I recommend against trying to learn both dbus and python at the same time. You don't need dbus to create application GUI windows, since that's what you seem interested in.

---

### Post by brian-mccumber on 2015-08-19
I am still still working on getting a handle on gtk. I have written a simple c program that displays a blank window already using the gtk library. I really appreciate all the good advice you gave me, now it's just a matter of learning some new syntax.

---

