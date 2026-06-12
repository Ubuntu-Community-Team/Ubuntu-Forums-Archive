---
title: "How do I compile a wxWidgets App?"
date: 2010-07-08
forum: Programming Talk
---

### Post by dwhitney67 on 2010-07-08
I'm attempting to build a very basic app that is presented here: [http://zetcode.com/tutorials/wxwidgetstutorial/firstprograms/](http://zetcode.com/tutorials/wxwidgetstutorial/firstprograms/)

Prior to this, I installed the wxWidgets development package (whether it is the correct one, I'm not sure)...
```

sudo apt-get install libwxbase2.8-dev

```

Here's the command I'm using to build the app:
```

g++ main.cpp simple.cpp `wx-config --cxxflags --libs` -o simple

```
The example indicates that the .h files should be included in the g++ statement, but I know this to be unnecessary; in fact it leads to more errors.

Anyhow, these are the errors I am getting:
```

In file included from main.cpp:2:
simple.h:7: error: invalid use of incomplete type &#8216;struct wxFrame&#8217;
/usr/include/wx-2.8/wx/utils.h:50: error: forward declaration of &#8216;struct wxFrame&#8217;
main.cpp: In function &#8216;wxAppConsole* wxCreateApp()&#8217;:
main.cpp:4: error: cannot allocate an object of abstract type &#8216;MyApp&#8217;
main.h:7: note:   because the following virtual functions are pure within &#8216;MyApp&#8217;:
/usr/include/wx-2.8/wx/app.h:89: note: 	virtual int wxAppConsole::OnRun()
main.cpp: In member function &#8216;virtual bool MyApp::OnInit()&#8217;:
main.cpp:9: error: &#8216;class Simple&#8217; has no member named &#8216;Show&#8217;
In file included from simple.cpp:1:
simple.h:7: error: invalid use of incomplete type &#8216;struct wxFrame&#8217;
/usr/include/wx-2.8/wx/utils.h:50: error: forward declaration of &#8216;struct wxFrame&#8217;
simple.cpp: In constructor &#8216;Simple::Simple(const wxString&)&#8217;:
simple.cpp:5: error: type &#8216;wxFrame&#8217; is not a direct base of &#8216;Simple&#8217;
simple.cpp:5: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
simple.cpp:5: error: &#8216;wxSize&#8217; was not declared in this scope
simple.cpp:7: error: &#8216;Centre&#8217; was not declared in this scope

```

Am I using an outdated wxWidgets library, or are the instructions for developing/building the application wrong?

---

### Post by johnl on 2010-07-08
I tried the first simple example there on my box and it compiled without any issues using the g++ line you posted.

Here's the output from my wx-config, which is provided by libwxgtk2.8-dev:

> 
ledbettj@reznor:~$ wx-config --libs
-pthread -Wl,-Bsymbolic-functions  -lwx_gtk2u_richtext-2.8 -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8 -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8 -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8

ledbettj@reznor:~$ wx-config --cflags
-I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread


If your output is drastically different, I would check which package is providing your /etc/alternatives/wx-config.

---

### Post by dwhitney67 on 2010-07-08
Johnl -- Thanks for the help and for referring me to the correct package (libwxgtk2.8-dev) to install.

Now I am able to build the app.

---

