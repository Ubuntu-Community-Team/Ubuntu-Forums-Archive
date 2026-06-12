---
title: "Does pygtk only work on gnome?"
date: 2011-03-07
forum: Programming Talk
---

### Post by ryuguns on 2011-03-07
Yeah, simple question, does pygtk only work on gnome?

---

### Post by wmcbrine on 2011-03-07
No. I've even used PyGTK apps under Windows. It just means some more dependencies beyond the typical Windows installation of Python.

---

### Post by cgroza on 2011-03-07
I think it just needs the toolkit to be installed.

---

### Post by forrestcupp on 2011-03-07
I've created pygtk apps in Windows. It's been a while, but I think you just have to include the dll's.

---

### Post by stchman on 2011-03-07
Since GTK is Gnome's API then yes.  That being said, you can run The GIMP on a Windows machine, you just need to install the GTK+ framework on Windows.

Are you intending on making Python GUI apps for Windows?

---

### Post by forrestcupp on 2011-03-07
> **stchman said:**
> Since GTK is Gnome's API then yes.

GTK is GIMP's API. Gnome is just one project that chose to use it, just like any supported platform can.

---

### Post by stchman on 2011-03-07
> **forrestcupp said:**
> GTK is GIMP's API. Gnome is just one project that chose to use it, just like any supported platform can.

Ok, Gnome uses the GTK+ API, better?

My point is that Windows does not use the GTK+ API.  You can install the GTK+ runtime so that you can run apps that use the GTK+ API on Windows.  I gather that there are IDEs for Windows to develop GTK+ apps.

---

### Post by SledgeHammer_999 on 2011-03-07
Apart from Windows you can run GTK+ apps on any other DE(Desktop Environment) apart from GNOME. To name a few: KDE, Xfce, Lxde. The only necessary thing is to have the gtk libraries installed on your system. On GNOME, Xfce and Lxde the gtk libs are installed by default because these DE use the GTK+ API. On KDE most probably you will have to install them, they are not installed by default because KDE uses the Qt API.

(And yes, you can run Qt apps in GNOME/Xfce/Lxde/Windows just fine. Just install the qt libs aswell)

---

### Post by forrestcupp on 2011-03-07
> **stchman said:**
> I gather that there are IDEs for Windows to develop GTK+ apps.
Yeah. You can use PyGTK with any Windows Python IDE, and GTK+ even in Visual Studio if you set it up for it.

I think I actually prefer Qt for Windows, though. There are Python bindings for Qt, too. wxPython is even better because it will use Windows' native controls. 

But if you're using PyGTK and you just want to make it cross platform, it works just fine. A while back, I created a small game using PyGTK in Linux, and I think it worked in Windows without even having to change the code.

---

### Post by Vox754 on 2011-03-08
> **stchman said:**
> Ok, Gnome uses the GTK+ API, better?

My point is that Windows does not use the GTK+ API.  You can install the GTK+ runtime so that you can run apps that use the GTK+ API on Windows.  I gather that there are IDEs for Windows to develop GTK+ apps.

You are confusing your terms, and possibly confusing others.

There is a difference between a "Desktop Environment" and a "Graphical User Interface" toolkit.

GNOME and KDE are desktop environments.

GTK and Qt are graphical user interface toolkits. These toolkits are merely the compiled runtime libraries, called shared objects (.so) in Linux, and dynamically linked libraries (.dll) in Windows, which provide the graphical programs their functionality.

GNOME and KDE are not a single product, rather, they are the name of a collection of several parts put together, including standard programs, and configuration utilities. In practical terms, each Desktop Environment decides to use one single GUI toolkit, for GNOME and KDE they are, respectively, GTK and Qt.

That you say that "Windows does not use GTK" is wrong. GTK is merely a library, you can install it, and then use it. Then Windows also uses GTK. It's as simple as that.

The same thing is true for Python.

You can install Python for Windows. You can install GTK for Windows. And you can install PyGTK for Windows. So yes, Windows can use all these libraries and many more. That's the reason Python, Java, Perl, GTK, Qt, WxWidgets, and many other libraries are considered "portable", because they can be installed everywhere, and code developed with them may run without modifications.

Answering the original question. It doesn't matter if you have GNOME or KDE, or other desktop environment. PyGTK programs will run as long as Python, GTK, and PyGTK are installed. It doesn't matter if Qt, PyQT and other toolkits are installed. It will not conflict.

Also read post 8.

---

### Post by forrestcupp on 2011-03-08
I argued that point, too. But I think he was just pointing out that GTK+ isn't Windows native api, while it *is* GNOME's native api.

---

