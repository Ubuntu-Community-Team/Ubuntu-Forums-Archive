---
title: "Programming with C++ and Gtk"
date: 2009-01-25
forum: Programming Talk
---

### Post by fallenshadow on 2009-01-25
Hi all,

Looking forward to starting development with C++ and Gtk. Problem is I am very unsure of where to even start.

I have found tutorials about Glade but I think I need to use something called Glademm if I am programming with C++.

I had a look at WxWidgets and they have very good tutorials and sample programs like this: [http://www.wxwidgets.org/docs/tutorials/hworld2.txt](http://www.wxwidgets.org/docs/tutorials/hworld2.txt)

I am nearly considering using WxWidgets now as Gtk seems so difficult to get started with. Anyone know where I could find good up to date tutorials on using Glademm with C++ or sample programs?

---

### Post by JupiterV2 on 2009-01-25
To make your life easier, I would install the [gtkmm library]("http://www.gtkmm.org/"). It is a C++ wrapper for Gtk+. There is a [tutorial]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html") on the site.

The API is fairly well documented via Doxygen.

---

### Post by fallenshadow on 2009-01-25
Thanks that really helped me out... but could you explain where the API is documented on this Doxygen site. Sorry if this is a real newbie question. :)

---

### Post by bruce89 on 2009-01-25
> **fallenshadow said:**
> Thanks that really helped me out... but could you explain where the API is documented on this Doxygen site. Sorry if this is a real newbie question. :)

[http://www.gtkmm.org/documentation.shtml](http://www.gtkmm.org/documentation.shtml)

Doxygen is the documentation generator actually.

Be aware that the "standard" GTK+ language is C, not C++.

---

### Post by fallenshadow on 2009-01-26
I have started following the documentation and I tried the following "simple" example yet it does not work.

Here is the code:

```

#include <gtkmm.h>

int main(int argc, char *argv[])

{

    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);

    return 0;

}

```

Any suggestions as to why this does not work?

---

### Post by bruce89 on 2009-01-26
> **fallenshadow said:**
> Any suggestions as to why this does not work?

You need to show_all the window.

---

### Post by Tibuda on 2009-01-27
> **bruce89 said:**
> You need to show_all the window.

No he doesn't. I have compiled this code, and it shows the window when running.

@fallenshadow:
How are you compiling (compiler and flags)? Did you got any messages?

---

### Post by fallenshadow on 2009-01-27
I tried compiling it from within Codeblocks but it seems that the header is not recognised... why is this? I have the gtkmm development packages installed!

---

### Post by Tibuda on 2009-01-27
> **fallenshadow said:**
> I tried compiling it from within Codeblocks but it seems that the header is not recognised... why is this? I have the gtkmm development packages installed!

You have to set up your IDE to use the GTKmm flags. I don't know how to set up Codeblocks, but the flags you need are:```
`pkg-config gtkmm-2.4 --cflags`
``` for compiler and ```
`pkg-config gtkmm-2.4 --libs`
``` for linking.

---

### Post by SledgeHammer_999 on 2009-01-27
> **fallenshadow said:**
> I tried compiling it from within Codeblocks but it seems that the header is not recognised... why is this? I have the gtkmm development packages installed!

Open up your project in Codeblocks.
1.Choose from the Menu "Project->Build Options..."
2.Then on the "Compiler Settings" tab choose the "Other Options" tab. Enter there: ```
`pkg-config gtkmm-2.4 --cflags`
```
3.Then choose "Linker Settings" tab and on the right panel enter: ```
`pkg-config gtkmm-2.4 --libs`
```
4.Hit OK and build your project.

Note: Do these steps for the WHOLE project and not for the different build targets ie Debug/Release

---

### Post by bruce89 on 2009-01-27
> **danielrmt said:**
> No he doesn't. I have compiled this code, and it shows the window when running.

I only know GTK+ from C, where you have to do this.

---

### Post by fallenshadow on 2009-01-28
I did what you said Sledgehammer but I still got no result from it. Could anything else be wrong?

---

### Post by SledgeHammer_999 on 2009-01-31
What error does Codeblocks give you?
Did you include the "**`**" in `pkg-config gtkmm-2.4 --cflags` _and_ `pkg-config gtkmm-2.4 --libs`? 
You must include it.

---

### Post by MeduZa on 2009-01-31
Install Anjuta is a good integrated debelopmen environment to start

---

### Post by fallenshadow on 2009-02-02
This is the error I get sledgehammer... Yes the backticks are included in those options I put in to the build options.


-------------- Build: Debug in MyProject ---------------

Linking stage skipped (build target has no object files to link)
Nothing to be done.

---

### Post by SledgeHammer_999 on 2009-02-02
Hmmm are you sure you have installed libgtkmm2.4-dev?
Do a Project->Rebuild Whole Project(or something similar) and tell me if that changes something...

---

### Post by fallenshadow on 2009-02-03
I get the exact same error message when I click on Rebuild whole project. 

I had both the new (2.4) and old libgtkmm-dev installed so I uninstalled the old version in case it was conflicting with the new one. I wanted to see would it make a difference... it didn't. :(

Does Codeblocks have an easy way of checking dependencies for gtkmm like the way Pytube does?

---

### Post by SledgeHammer_999 on 2009-02-04
Hmmm I don't what's happening. I made new gtkmm project myself and it builds on my installation. I attach the project. Open the "test.cbp" in codeblocks and try to build it. If it doesn't build then there's something wrong with your installation. 
In case of not building open a terminal and navigate to where "hello.cpp" is. Then try to compile it with this command:
```
g++ hello.cpp `pkg-config gtkmm-2.4 --cflags --libs` -o hello
```
If it builds then there is something wrong with codeblocks. If it doesn't then there is something wrong with your build tools.
EDIT: click "Rebuild whole project" because I accidentally included the built files.

---

### Post by fallenshadow on 2009-02-04
Ok I tried building the project with Codeblocks and it failed with the same error message. Yet the code built successfully by use of the terminal.

It looks like I will have to change my IDE, so much for Codeblocks being a good IDE... guess not.

Is Eclipse a good IDE? I had a quick look at it in work today... looks nice!

---

### Post by SledgeHammer_999 on 2009-02-04
Emmm what version do you use? I use the latest nightly builds provided by pasgui.
Look here:
1.[linl1](http://forums.codeblocks.org/index.php?PHPSESSID=74cc0390225fae2e5682b5e420bf65fd&topic=10040.msg69800#msg69800)
2.[link2](http://lgp203.free.fr/spip/spip.php?article1)
(you maybe need to update wxwidgets too)

---

### Post by fallenshadow on 2009-02-05
I am currently using version 8.02 I have wanted to upgrade to the next release but I have been waiting so long that I am not sure if they are gonna release a new version.

Nightly builds sounds a bit dodgy if you ask me... but I will give it a shot. Does anyone have an opinion on Eclipse on this forum? Id like to know.

Also does anyone have experience using gtkmm to load glade created interfaces? Is it easier than using gtkmm alone? as I would think so but I may be wrong.

---

### Post by fallenshadow on 2009-02-07
Does anyone know why this code won't load a glade interface? This code is from the Gtkmm documentation and I don't know why it won't work.

```
#include <libglademm.h>
#include <gtkmm.h>



int main (int argc, char *argv[])
{
    Glib::RefPtr<Gnome::Glade::Xml> refXml = Gnome::Glade::Xml::create("main.glade");

    return 0;
}

```

Plz help!

---

### Post by eye208 on 2009-02-07
> **fallenshadow said:**
> Does anyone know why this code won't load a glade interface? This code is from the Gtkmm documentation and I don't know why it won't work.
Please describe both the expected behavior and the observed behavior of the program.

---

### Post by fallenshadow on 2009-02-07
All this program is meant to do is loadup a glade file called main.

The program reports:

```
main.cpp:1:24: error: libglademm.h: No such file or directory
main.cpp: In function ‘int main(int, char**)’:
main.cpp:8: error: ‘Gnome’ was not declared in this scope
main.cpp:8: error: template argument 1 is invalid
main.cpp:8: error: invalid type in declaration before ‘=’ token
main.cpp:8: error: ‘Gnome’ is not a class or namespace
```

I don't understand this as the code was taken from the gtkmm tutorial, it must be terrible out of date or something.

---

### Post by eye208 on 2009-02-07
The first error is the important one:
```
main.cpp:1:24: error: libglademm.h: No such file or directory
```
This means the libglademm header file wasn't found. The declarations in that file are required for the rest of the program to be understood by the compiler.

There are two possible reasons for the missing file. First make sure that libglademm-2.4-dev is installed. This is the package that contains the file.

If the package is installed and you still get the error, it's because the include paths were not added to the g++ command line. To find out what to add (including the library names for linking), run:
```
pkg-config --cflags --libs libglademm-2.4
```
Instead of copying and pasting the output, you can also insert this command straight into your g++ command line like this:
```
g++ `pkg-config --cflags --libs libglademm-2.4` main.cc
```

---

### Post by fallenshadow on 2009-05-03
I have decided to revive this thread since I have tried compiling the above code with gtkmm-dev installed and using Codeblocks svn 5534. This code will still not compile. Can anybody tell me why??

When I try to compile the dialog saying:
 
"It seems that this file has not been built yet.
Do you want to build it now?"

keeps on appearing.

---

### Post by SledgeHammer_999 on 2009-05-03
> **fallenshadow said:**
> I have decided to revive this thread since I have tried compiling the above code with gtkmm-dev installed and using Codeblocks svn 5534. This code will still not compile. Can anybody tell me why??

When I try to compile the dialog saying:
 
"It seems that this file has not been built yet.
Do you want to build it now?"

keeps on appearing.

You need **libglademm-2.4-dev** installed. And make the necessary changes in CodeBlocks to look for it.

---

### Post by fallenshadow on 2009-05-03
I installed those libs and set it up with Codeblocks but now im getting a permission denied message. How can I sort it? (Thanks again for trying to help me out!)

---

### Post by SledgeHammer_999 on 2009-05-03
Hmmm, how did you install Codeblocks? Did you compile it yourself?
If yes, try installing it from this guy's repo(i've been using it long time now)->[instructions](http://lgp203.free.fr/spip/spip.php?article2)

His message on the nightlies forum->[announce](http://forums.codeblocks.org/index.php/topic,10406.msg71682.html#msg71682)

---

### Post by fallenshadow on 2009-05-04
I got it from the same repo as you. On the verge of giving up again... with Codeblocks why can't things "Just Work"?? sigh...

---

### Post by SledgeHammer_999 on 2009-05-04
> **fallenshadow said:**
> I installed those libs and set it up with Codeblocks but now im getting a permission denied message. How can I sort it? (Thanks again for trying to help me out!)

Could you post the exact error?(or a screenshot?)

---

### Post by fallenshadow on 2009-05-09
I started a new project but instead or creating a blank project I created a GTK project which included:

```
`pkg-config gtk+-2.0 --cflags`
```

and

```
`pkg-config gtk+-2.0 --libs`
```

It wouldn't work before in the older Codeblocks but now everything is working. Im terrible sorry for taking up your time Sledgehammer but you have been ever so helpful.

However I do have one (hopefully last) question...

If I am using Gtkmm to load .glade files for an interface, can I program the signals by using Gtkmm code? or do I have to do something else?

---

### Post by fallenshadow on 2009-05-09
I thought it was working but that was actually the main.c GTK example which compiled so I thought it was the GTKmm Helloworld example but it was not.

Here is the error im getting:

```
sh: /home/user/Test/bin/Debug/Test: not found
```

I have it setup to link with everything properly so why can't it just work??

---

### Post by SledgeHammer_999 on 2009-05-09
No problem, if I know the answer I'll help anyone.

For your problem:
Does the path **/home/user/Test/bin/Debug/Test** actually exist?

Could you post your test project to see if I can compile it on my machine?

What version of Ubuntu do you use?

---

### Post by fallenshadow on 2009-05-09
It did not exist so I created the folder, however now im getting that permission denied error I told you about.

I use Ubuntu 8.04LTS. The folder is attached.

---

### Post by SledgeHammer_999 on 2009-05-10
I think I found your problem:

1.First I opened the Test.cbp file and I saw you haven't added the source files in the project. So I did a **Project->Add Files...**

2.I tried to compile butthe linker complained:
> 
Linking console executable: bin/Debug/Test
/usr/bin/ld: cannot open output file bin/Debug/Test: Is a directory

3.Then I remembered a strange thing about linux. If in the same folder there is a file named eg "test" and then you try to create in the same folder another folder named "test" it will fail, because there is already a file named "test". So all I did was to delete the **Test** folder in **/bin/Debug**. And then it compiled,linked and run ok.

---

### Post by fallenshadow on 2009-05-11
I did what you suggested and its all working now! :)

So I have another question... can signals be managed through using GTKmm code even though an interface may be produced by using libGlademm to load a .glade file?

---

### Post by fallenshadow on 2009-06-08
Can I ask a favour of someone?

I have modified this example:

[http://www.gtkmm.org/docs/gtkmm-2.4/examples/book/menus_and_toolbars/]("http://www.gtkmm.org/docs/gtkmm-2.4/examples/book/menus_and_toolbars/")

but... the code compiles the example and not my modified version in Codeblocks. Can someone try to compile my code and see does it work for them and post back the results?

---

### Post by SledgeHammer_999 on 2009-06-08
I've compared mainwindow.cc to examplewindow.cc and the code is the same. Only the class name is changed. That's the only change I see that you have done.

Can you post the desired change(code)?

---

### Post by fallenshadow on 2009-06-08
The code to load the custom image for the "Rain" button has been removed and also changed to gtk action instead of gtk toggle. It has also been renamed to "Save".

The main window has been set to 600 , 400 instead of 200, 200.

Thats about all that has been changed. Check again... the differences should be obvious. Don't know why they seem to be the same.:confused:

EDIT: Sent you the wrong files sorry! Updated files attached.

---

### Post by SledgeHammer_999 on 2009-06-08
Yes, in the 2nd tar.gz I can see the changes.
You only have forgotten to change the Gtk::ToggleAction to GtK::Action.

Do you want some other kind of feedback?

---

### Post by fallenshadow on 2009-06-09
Ok can u change that to Gtk action... then compile the code anyway possible. The code refuses to compile for me even though I have made very little changes to the original example code.

Please report back if you could successfully compile the code or not.

---

### Post by Linteg on 2009-06-09
Well, Test2 (as supplied in the .tar.gz) compiles without errors from the command line using
```
g++ main.cc mainwindow.cc mainwindow.h -o test `pkg-config gtkmm-2.4 --cflags --libs`
```
If you have a Code::Blocks project add
```
`pkg-config gtkmm-2.4 --cflags`
```
to Project->Build options->Compiler settings->Other options
and
```
`pkg-config gtkmm-2.4 --libs`
```
to Project->Build options->Linker settings->Other linker options

---

### Post by SledgeHammer_999 on 2009-06-09
It compiles for me too.
What errors are you getting?

---

### Post by fallenshadow on 2009-06-11
Sorry about the late reply but I was away on a camping trip. :)

Well it does compile for me via the command line so its got to be a problem with Codeblocks. When I try to compile with Codeblocks (linked to the correct libs etc) it repeatedly comes up with the dialog saying: the project has not been built yet do you want to build it now? (or something like that).

Im quite sick of Codeblocks not compiling code reliably so in future I will compile using the command line. Thanks guys!

Also why is the save button still a toggle button?

---

### Post by SledgeHammer_999 on 2009-06-12
If you want, post  a CodeBlocks project example  that produces the error so I can check if you do something wrong or if CodeBlocks does something wrong.

---

### Post by fallenshadow on 2009-06-17
Its ok sledgehammer im happy to compile with the command line now... its much more reliable.

Just wanna ask everyone in this programming section... does anybody actually have any knowledge of gtkmm?

Am I just wasting my time asking detailed gtkmm questions?

---

### Post by SledgeHammer_999 on 2009-06-17
I am using it at the moment. I can't say that I have tremendous experience with it, but I am able to understand it(most of it).  I am pretty sure there are other people here who know gtkmm too. Just ask(after you do a little research yourself of course).

---

### Post by fallenshadow on 2009-06-17
I have been looking through the examples (and in the pdf guide) at creating menus and I can do it but I was wondering how could I do a menu without an icon? 

My code fails to compile if I delete the Gtk::stock::blah part and replace it with a closing bracket. Its not that simple I guess...

---

### Post by SledgeHammer_999 on 2009-06-17
Let's take the simple route, using a Gtk::Action.
If you take a look here->[http://gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1Action.html](http://gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1Action.html)
you will notice that Gtk::Action::create() is overloaded.(many methods with the same name). Some of them require an icon some of them don't.

So if you create a Gtk::Action with an icon like this:
[php]Gtk::Action::create("FileOpen", Gtk::Stock::OPEN, "Open...", "Open a file.")[/php]

Then the equivalent of that without an icon is:
[php]Gtk::Action::create("FileOpen", "Open...", "Open a file.")[/php]

In each case you use a different "version" of Gtk::Action::create() since it is an overloaded method.

If you don't know what an overloaded method/function is, take a look [here](http://www.cplusplus.com/doc/tutorial/functions2/)(in the middle of the page)

---

### Post by fallenshadow on 2009-06-17
Thanks but I think im doing things differently... here is the code:

```

m_refActionGroup->add( Gtk::Action::create("Revert", Gtk::Stock::GO_BACK),
sigc::mem_fun(*this, &MWindow::on_action_others) );

```

At the moment I have it set as GO_BACK just because I didn't know how to do it without an icon. Should I use your method or can a similar thing be applied to this code?

```
m_refActionGroup->add( Gtk::Action::create("Revert", "Revert"),
sigc::mem_fun(*this, &MWindow::on_action_others) ); 
//would this work?

```

---

### Post by SledgeHammer_999 on 2009-06-17
Yes it should work. Because the third parameter in this [::create()](http://gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1Action.html#ebf25ebf0ec850314ad85e4cfde9173b) is equal to an empty ustring if you don't specify something else.

Notice that the second parameter doesn't need to be specified(it equals to an empty ustring too), but if you don't specify it then nothing will appear on the menu as text.

---

### Post by fallenshadow on 2009-06-20
That really helped... glad I kinda figured it out myself too! :)

Another question: how can I modify a normal menu to make it into an arrow menu?... example... a recent documents menu.

---

### Post by SledgeHammer_999 on 2009-06-20
If you ask how to create a submenu then the answer is simple. Instead of "menuitem" use "menu". 

Notice: if the submenu doesn't contain any menuitems then it want appear. This is the default action. If you want to change that plz post an example code so I can make the necessary modifications.(I am too lazy to write the code on my own :p)

---

### Post by fallenshadow on 2009-06-23
Hmm... not too sure did you get my pm. Anyway I have added a new menu to my code called Image and for some reason my code will no longer compile into a working binary.

I was wondering could you take a look at it and let me know if you see anything wrong as I really can't.

Code available from here:
[http://www.photofiltre-lx.org/downloads.html](http://www.photofiltre-lx.org/downloads.html)

---

### Post by SledgeHammer_999 on 2009-06-23
I'm sorry. I didn't notice I had a pm.
I found your problem. In **mainwindow.cc** change lines 158 and 159 from:
[php]"    <menuitem action='Mode'>"  //RECENTLY ADDED
"    <menuitem action='Flip vertical'>" //RECENTLY ADDED[/php]
to
[php]"    <menuitem action='Mode'/>"  //RECENTLY ADDED
"    <menuitem action='Flip vertical'/>" //RECENTLY ADDED[/php]

It is a pretty frustrating thing with ui_manager not telling you exactly where the problem is.
I'll take a look a your pm later.

---

### Post by fallenshadow on 2009-06-23
I can't believe thats all the problem was! :(  A simple error report would have been nice but instead it went and built a faulty binary... sigh.

Anyway your name has been added to the credits and I do agree that we should keep it public in this thread to help others.

---

### Post by Thesuperchang on 2009-06-23
Not sure if this has been mentioned at all but whenever I require glade & C++, I find it adequate to disable name mangling on the callback functions.

[PHP]#ifdef __cplusplus
extern "C" {
#endif

/////////////////////////
// FUNCTION PROTOTYPES //
/////////////////////////

#ifdef __cplusplus
}
#endif[/PHP]

---

### Post by SledgeHammer_999 on 2009-06-23
> **fallenshadow said:**
> I can't believe thats all the problem was! :(  A simple error report would have been nice but instead it went and built a faulty binary... sigh.

Anyway your name has been added to the credits and I do agree that we should keep it public in this thread to help others.

Technically the binary is correct. The string where the ui is declared isn't right. Any error of this kind is detected only on runtime when this string is parsed. Although I do agree that ui_manager should post more clarifying error messages on the terminal.

Anywayz here is an example how to create submenus:
main.cpp
[php]#include <gtkmm.h>
#include "main_window.h"


int main(int argc, char *argv[])
{
    Gtk::Main main_loop(argc, argv);

    main_window* window = new main_window;

    main_loop.run(*window);
    delete window;

    return 0;
}[/php]

main_window.h
[php]
#ifndef MAIN_WINDOW_H_INCLUDED
#define MAIN_WINDOW_H_INCLUDED

#include <gtkmm/window.h>
#include <gtkmm/fixed.h>
#include <gtkmm/uimanager.h>

class main_window: public Gtk::Window
{

    public:
        main_window();
        virtual ~main_window();

    protected:
        Gtk::Fixed* container;
        Glib::RefPtr<Gtk::UIManager> ui_manager;
        Glib::RefPtr<Gtk::ActionGroup> action_group;

};

#endif // MAIN_WINDOW_H_INCLUDED[/php]

main_window.cpp
[php]
#include "main_window.h"

main_window::main_window()
{
    set_size_request(400,400);
	container = new Gtk::Fixed;
	add(*container);


	action_group = Gtk::ActionGroup::create();
    action_group->add(Gtk::Action::create("FileMenu", "File"));
    action_group->add(Gtk::Action::create("Test1", "Test1"));
    action_group->add(Gtk::Action::create("item1", "item1"));
    action_group->add(Gtk::Action::create("item2", "item2"));
    action_group->add(Gtk::Action::create("Test2", "Test2"));

    ui_manager = Gtk::UIManager::create();
    ui_manager->insert_action_group(action_group);
    Glib::ustring ui_info =
        "<ui>"
        "  <menubar name='MenuBar'>"
        "    <menu action='FileMenu'>"
        "       <menu action = 'Test1'>" //<------ this starts the first submenu
        "           <menuitem action = 'item1'/>"
        "           <menuitem action = 'item2'/>"
        "       </menu>" //<------ this closes the first submenu
        "       <menu action = 'Test2'>" //<------ this starts the second submenu
        "       </menu>" //<------ this closes the second submenu
        "    </menu>" //<------ this closes the PARENT menu
        "  </menubar>"
        "</ui>";

    ui_manager->add_ui_from_string(ui_info);
    Gtk::Widget* menubar = ui_manager->get_widget("/MenuBar");
    container->add(*menubar);

    show_all();
}

main_window::~main_window()
{
    delete container;
}[/php]

---

### Post by fallenshadow on 2009-06-26
Thanks for that sledge I will be referring back to that when I am filling in the submenus.

At the moment I am trying to get a togglemenu to work... I have a question.

Does a togglebutton have to exist in the toolbar to make a togglemenu? (like the way in the rain example)

---

### Post by SledgeHammer_999 on 2009-06-26
As far as I know no. To create a togglemenu in the menubar you only to do something like this:
[php]action_group->add(Gtk::ToggleAction::create(...));[/php]
instead of:
[php]action_group->add(Gtk::Action::create(...));[/php]

---

### Post by fallenshadow on 2009-06-26
Doesn't seem to work for me... heres what I have:

[PHP]m_refActionGroup->add( Gtk::Action::create("MenuView", "_View") );
  m_refActionGroup->add( Gtk::ToggleAction::create("Filterbar", "Filterbar"),
          sigc::mem_fun(*this, &MWindow::on_action_others) );
  m_refActionGroup->add( Gtk::ToggleAction::create("Tools palette", "Tools palette"),
          sigc::mem_fun(*this, &MWindow::on_action_others) );[/PHP]

and down further:

 [PHP]"    <menu action='MenuView'>"
        "    <menuitem action='Filter bar'/>"
        "    <menuitem action='Tools palette'/>"
        "    </menu"[/PHP]

I have added ToggleAction to this line (instead of Action) and it made no difference:

[PHP]m_refActionGroup->add( Gtk::Action::create("MenuView", "_View") );[/PHP]

---

### Post by SledgeHammer_999 on 2009-06-26
Well, I thought you meant a toogle-menu-**item**. I haven't seen a toggle-menu. I can't even imagine how it should look like. 
What are you trying to accomplish making it a toogle-menu?

---

### Post by fallenshadow on 2009-06-26
No it is a toggle menu-item I am trying to accomplish but I am trying everything to get it to work because it won't work for me.

---

### Post by SledgeHammer_999 on 2009-06-26
ok. Maybe I don't understand you very well :p

You want this action as toggle-action, right?:
[php]m_refActionGroup->add( Gtk::Action::create("MenuView", "_View") );[/php]

If yes, then you should use it like this:
[php]m_refActionGroup->add( Gtk::ToggleAction::create("MenuView", "_View") );[/php]

and then don't do a [php]"<menu action='MenuView'>"[/php]
but a [php]"<menuitem action='MenuView'/>"[/php]

---

### Post by fallenshadow on 2009-06-28
The toggle items work now... no more new questions for a while. :)

Ok... one small question actually. :D  Is there a way to compile the contents of a folder without listing them out in the terminal?

---

### Post by SledgeHammer_999 on 2009-07-01
Yes you can, using wildcards like "*.cpp", but I don't know for sure. I am not good with the terminal, that's why I use an IDE.

---

### Post by fallenshadow on 2009-07-15
Its been a while and I have been working on things but not much seems to be going right. I was wondering could you download the latest code from the site and have a look at the TODO list.

You can fix them for me if you wish... or just let me know why things are refusing to work properly for me. The about dialog is not really something that needs to be fixed... I just need to work on it some more and understand what I should remove.

---

### Post by SledgeHammer_999 on 2009-07-15
It took me a while to figure out how someone uses a custom icon for menu. Thank you for the data, I didn't know how. Now how to fix the problems:

In line 60 change:
[php] m_refActionGroup->add( Gtk::ToggleAction::create("Acquire image",[/php]
to:
[php] m_refActionGroup->add( Gtk::Action::create("Acquire image",[/php]

Then in line 611 change:
[php]add_stock_item(factory, "scan.png", "stock_scan", "Acquire image");[/php]

to:
[php]add_stock_item(factory, "icons/scan.png", "stock_scan", "Acquire image");[/php]

And it should load and show the icon.

Now I also managed to get rid of the 2 Gtk-Warnings which appeared in runtime. For the first one:
You declare 2 Gtk:Actions which have the same name("Transform"). Obviously you want to put the same action in different menus. You only need to declare it once. Then in the ui_info string you can use it as many times as you want. So to fix the first problem delete lines 96-97 **or** 163-164.

For the second warning: Go to line 512 and add a **c** to **Aquire**

That's it for now. I'll take a look to the other problems later.

---

### Post by SledgeHammer_999 on 2009-07-15
the second problem was fixed together with the first one. As for the third one it is pretty much easy and I think you can do it. If you want I can take a look into it.

---

### Post by fallenshadow on 2009-07-18
I find it a bit embarrassing when my problems are usually so simple and just need to check my code more... but when my eyes are tired from programming I just can't seem to see these errors. :(

It is great to just have a second pair of eyes to pick up on these stupid bugs. In future I will try to find bugs better to save you the trouble. ;) 

I did fix most of what you said and I will work on that about dialog until I get someone to design the icons I need for the toolbar. However that could take a while so I might have to work on something else than the toolbar.

---

### Post by SledgeHammer_999 on 2009-07-18
> **fallenshadow said:**
> I find it a bit embarrassing when my problems are usually so simple and just need to check my code more... but when my eyes are tired from programming I just can't seem to see these errors. :(

For me the usual solution to this kind of problem is take a break. Even a day or two.

---

### Post by fallenshadow on 2009-08-26
Hi Sledge... its been a while but thats because my graphics card broke and it took 3 weeks to get my PC back from repair.

Can you just tell me do I need to use the button signal to link with a menu item or is there a different signal for it?

Also in my latest code ([http://www.photofiltre-lx.org/downloads.html](http://www.photofiltre-lx.org/downloads.html)) I am having trouble adding more than one custom icon... im just not sure how to do it. I tried what I thought would work but I commented it out so my code would compile.

---

### Post by SledgeHammer_999 on 2009-08-29
Sorry for the waiting, I don't have much time these days. I'll try to get back at you as soon as I can!

---

### Post by fallenshadow on 2009-08-30
Yeah thats fine man... we all have our own life to live outside of this digital world! :)

---

### Post by SledgeHammer_999 on 2009-09-06
> Can you just tell me do I need to use the button signal to link with a menu item or is there a different signal for it?

Let's take an example from your code:
```

  m_refActionGroup->add( Gtk::Action::create("Open", Gtk::Stock::OPEN),
          sigc::mem_fun(*this, &MWindow::on_action_others) );
m_refActionGroup->add( Gtk::Action::create("Revert", "Revert"),
          sigc::mem_fun(*this, &MWindow::on_action_others) );
```

If you want to do different things when the "Open" or "Revert" menu is selected, then just change the method you connect the action group signal to. Eg:
```

  m_refActionGroup->add( Gtk::Action::create("Open", Gtk::Stock::OPEN),
          sigc::mem_fun(*this, &MWindow::**on_open**) );
m_refActionGroup->add( Gtk::Action::create("Revert", "Revert"),
          sigc::mem_fun(*this, &MWindow::**on_revert**) );
```

on_revert and on_open are 2 separate methods of your MWindow class. You need to implement the actual code. Actually you have done this already yourself. Just take look at:
```

m_refActionGroup->add( Gtk::Action::create("New", Gtk::Stock::NEW),
          sigc::mem_fun(*this, &MWindow::on_action_file_new) );
  m_refActionGroup->add( Gtk::Action::create("Open", Gtk::Stock::OPEN),
          sigc::mem_fun(*this, &MWindow::on_action_others) );
```
and to the class methods on_action_file_new() and on_action_others().

If you are asking something else, then please give me more info/details/example.

> I am having trouble adding more than one custom icon... im just not sure how to do it. I tried what I thought would work but I commented it out so my code would compile.

I suppose you were tired(again), because this is a silly mistake. First of all uncomment the lines you comment. Second, change this:
```
m_refActionGroup->add( Gtk::Action::create("RGB colour", "RGB colour"), Gtk::StockID("stock_rgb") ),
sigc::mem_fun(*this, &MWindow::on_action_others) );
```

to this:
```
m_refActionGroup->add( Gtk::Action::create("RGB colour", Gtk::StockID("stock_rgb") ),
sigc::mem_fun(*this, &MWindow::on_action_others) );
```

(stockID goes as parameter to Gtk::Action::create() and not to ->add())

Also I see that you didn't do all the changes I suggested to get rid of the GTK+ warnings in the console. I quote myself:
> **SledgeHammer_999 said:**
> You declare 2 Gtk:Actions which have the same name("Transform"). Obviously you want to put the same action in different menus. You only need to declare it once. Then in the ui_info string you can use it as many times as you want. So to fix the first problem delete lines 96-97 or 163-164.

Line numbers have changed now. There are 2 instructions of this kind:
```
m_refActionGroup->add( Gtk::Action::create("Transform", "Transform"),
          sigc::mem_fun(*this, &MWindow::on_action_others) );
```

You cannot do this. Delete one of them.

That's it. Also did you edit your post? I thought you were asking me something about the "About" dialog...

---

### Post by j7%&lt;RmUg on 2009-09-06
I use pygtk its a python wrapper for gtk+. Much easier to learn if you dont know much C++.

---

### Post by fallenshadow on 2009-09-20
> I use pygtk its a python wrapper for gtk+. Much easier to learn if you dont know much C++.

I know a decent bit of C++ but nothing much of GTKmm. I want to improve my knowledge of C++ so I will struggle on. :)

Anyway there is just two more things I want to know(for now):

1. How to do a simple tooltip for a button. (can't find it in examples)

2. How to link a dialog to a menu entry. EG: When a user clicks on about it should bring up my about dialog. 

I know I should be using the manual more but I find the documentation a bit overdone. They should show simple examples of more commonly used items before showing anything else!

---

### Post by SledgeHammer_999 on 2009-09-20
Quick answer for number 2:
```

m_refActionGroup->add( Gtk::Action::create("About", "About"),
          sigc::mem_fun(*this, &MWindow::on_about_dialog) );
//other code here

MWindow::on_about_dialog()
{
  about_dialog->show();
}

```
does it make sense for you?

---

### Post by SledgeHammer_999 on 2009-09-20
About question 1:
Use the docs.
Gtk::Button derives from Gtk::Widget
to set the text for the tooltip use Gtk::Widget::set_tooltip_text() or Gtk::Widget::set_tooltip_markup()(if you want bold/italic/other effects on the text).

---

### Post by fallenshadow on 2009-09-27
> does it make sense for you?

It sure does... many thanks for both tips. I want to ask the Gtkmm guru another question. ;)

I can't find anything like this in the examples but I want to know is it possible to have buttons which don't have text under them?

I have found this on the net... 
```
ToolBar->set_toolbar_style ( Gtk::TOOLBAR_ICONS ); 
```

it doesn't seem to work for me... but I dont really know where to put it.

---

### Post by SledgeHammer_999 on 2009-09-29
> It sure does... many thanks for both tips. I want to ask the **Gtkmm guru** another question

Hahahahahahaha I wish it was true :p


In **MWindow::MWindow()** replace:
```
Gtk::Widget* pToolbar = m_refUIManager->get_widget("/ToolBar") ;
```

with:
```

Gtk::Toolbar *pToolbar = dynamic_cast<Gtk::Toolbar*>(m_refUIManager->get_widget("/ToolBar"));
pToolbar->set_toolbar_style ( Gtk::TOOLBAR_ICONS );
```

Basically you need to type cast from Gtk::Widget* to Gtk::Toolbar*. It works for me.

---

### Post by fallenshadow on 2009-12-24
Hey sledge... its been a while since my last post.

I don't mind when you reply as long as you do reply! :)

I have reduced the amount of errors to one but I can't seem to figure it out. Its probably easy but remember I am a junior programmer! (only 8 months of learning C++)

Here it is:

> mainwindow.cc: In constructor &#8216;MWindow::MWindow()&#8217;:
mainwindow.cc:311: error: &#8216;AboutDialog&#8217; has not been declared

I don't know how you declare stuff with GTKmm. 

Hope you can help me maybe after xmas or whenever you have some spare time. Thanks...

---

### Post by SledgeHammer_999 on 2009-12-24
> **fallenshadow said:**
> Hey sledge... its been a while since my last post.

I don't mind when you reply as long as you do reply! :)

I have reduced the amount of errors to one but I can't seem to figure it out. Its probably easy but remember I am a junior programmer! (only 8 months of learning C++)

Here it is:



I don't know how you declare stuff with GTKmm. 

Hope you can help me maybe after xmas or whenever you have some spare time. Thanks...

I will reply to you in about 10 days. Currently I don't have access to programming stuff. I just hope I don't forget about you.

Generally speaking you declare something related to GTKmm the same way you do with every variable. Could you post line 311 of mainwindows.cc?

---

### Post by fallenshadow on 2009-12-25
Here it is:

```
sigc::mem_fun(*this, &AboutDialog::on_button_clicked) )
```

Its all in my latest code if you want to download it.
[http://www.photofiltre-lx.org/Source/PhotoFiltre-LX%20-%20latest.tar.gz](http://www.photofiltre-lx.org/Source/PhotoFiltre-LX%20-%20latest.tar.gz)

---

### Post by fallenshadow on 2010-01-08
Have you access to your programming stuff yet? :)

Sorry if im being a bit impatient.

---

### Post by SledgeHammer_999 on 2010-01-10
Yes I have returned. I'll take a look at it as soon as I can(probably till tomorrow you'll have an answer).

---

### Post by SledgeHammer_999 on 2010-01-12
Ok I took a look at your code. The way you are trying to display an about dialog doesn't make sense(that's ok for a newcomer like you). I took the liberty to modify the source and make it really simple. If you wanted to do more with the aboutdialog then tell me. So here's what I did to "fix it":

1. From **mainwindow.h** delete the whole "AboutWindow" class
2. In **mainwindow.h** in "MWindow" class create a protected method after on_action_others() named:
```
virtual void show_about_dialog();
```
3. In **mainwindow.cc** in line 311 replace "AboutDialog::on_button_clicked" with:
```
MWindow::show_about_dialog
```
4. Then scroll down to the end of the file and delete the implementation of "AboutWindow::~AboutWindow()" and "AboutWindow::showAboutDialog()" (you deleted the class earlier, remebmer?)
5. Add there this code:
[php]void MWindow::show_about_dialog()
{
	Gtk::AboutDialog aboutDialog;
	std::list<Glib::ustring> authors;
	authors.push_back("Dylan Coakley - dylan_coakley@yahoo.co.uk");

  aboutDialog.set_authors(authors);
  aboutDialog.set_copyright("Copyright (C) 2009  Dylan Coakley");
	//aboutDialog.set_name(PACKAGE_NAME);
	//aboutDialog.set_version(PACKAGE_VERSION);
	//aboutDialog.set_translator_credits(_("translator-credits"));

	aboutDialog.set_website("http://www.photofiltre-lx.org");
	aboutDialog.set_website_label("Official Website");

	aboutDialog.set_license("GPL v3");

	//this puts the dialog-window in front of the mainwindow and
	//centers it to the mainwindow
  aboutDialog.set_transient_for(*this);
  //this shows the dialog and blocks code execution until the dialog is closed.
  aboutDialog.run();
}[/php]

You're done. Compile and it should work(it did for me).

---

### Post by fallenshadow on 2010-01-13
Thanks alot SledgeHammer... now that I know how to link dialogs I won't ever forget it. Teach me something once and I will remember it forever! :)

Also Is it possible to integrate tooltips into my code?  I have seen the tooltips examples but it doesn't tell me if its possible to do it with this code or not.

[PHP]//CODE SNIPPET from mainwindow.cc
m_refActionGroup->add( Gtk::Action::create("New", Gtk::Stock::NEW), 
sigc::mem_fun(*this, &MWindow::on_action_file_new) );[/PHP]

I have taken your code and implemented further changes to the about dialog to make it to my liking. 

I have now switched you from the "Special Thanks" section to the "Contributors" section (in credits) since you have been such a great help to me. 

Also it makes more sense because I have not actually received changed files from you but some of you code has been copied and pasted straight into the project.

---

### Post by SledgeHammer_999 on 2010-01-13
> **fallenshadow said:**
> Thanks alot SledgeHammer... now that I know how to link dialogs I won't ever forget it. Teach me something once and I will remember it forever! :)

Also Is it possible to integrate tooltips into my code?  I have seen the tooltips examples but it doesn't tell me if its possible to do it with this code or not.

[PHP]//CODE SNIPPET from mainwindow.cc
m_refActionGroup->add( Gtk::Action::create("New", Gtk::Stock::NEW), 
sigc::mem_fun(*this, &MWindow::on_action_file_new) );[/PHP]

I have taken your code and implemented further changes to the about dialog to make it to my liking. 

I have now switched you from the "Special Thanks" section to the "Contributors" section (in credits) since you have been such a great help to me. 

Also it makes more sense because I have not actually received changed files from you but some of you code has been copied and pasted straight into the project.

Well thank you. I just pass on the knowledge I have gathered these last years from forums/docs/search results (the "community").

As for the "tooltips" part. Yes you can add tooltips to your program(generally speaking). But care to be more specific so I can point you to some direction?

---

### Post by fallenshadow on 2010-01-14
Hmm... well I want to have tooltips for my toolbars mainly. I am just wondering could tooltips easily be done with my existing code for functions?

such as this:
[PHP]
//CODE SNIPPET from mainwindow.cc
m_refActionGroup->add( Gtk::Action::create("New", Gtk::Stock::NEW), 
sigc::mem_fun(*this, &MWindow::on_action_file_new) );  
[/PHP]

I want to know how to assign a (button)tooltip with a function. I hope that made things a bit more clear as to what I want.

---

### Post by SledgeHammer_999 on 2010-01-14
Ok let me give you a lesson on how to read the docs.(and maybe understand further the C++ lang)

m_refActionGroup is of type **Glib::RefPtr<Gtk::ActionGroup>**. So let's check the docs about Gtk::ActionGroup and specifically the Gtk::ActionGroup::add() methods. There are several of those that take different parameters. These are called [overloaded functions](http://www.cplusplus.com/doc/tutorial/functions2/). From the [Gtk::ActionGroup docs:](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1ActionGroup.html)

> void 	add (const Glib::RefPtr< Action >& action)
void 	add (const Glib::RefPtr< Action >& action, const AccelKey& accel_key)
void 	add (const Glib::RefPtr< Action >& action, const Action::SlotActivate& slot)
void 	add (const Glib::RefPtr< Action >& action, const AccelKey& accel_key, const Action::SlotActivate& slot)

So each one of them takes as first parameter a **Glib::RefPtr< Action >** object. So let's take a look at the [Gtk::Action docs](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Action.html). Usually when you create an instance of a class you use it's constructor to pass special parameters to it. However, Gtk::Action has it's contructors protected so you cannot create an instance the usual way--> **Gtk::Action action;**. You have to use the Gtk::Action::create() overloaded functions that return a Glib::RefPtr< Action > object(the one Gtk::ActionGroup::add() needs). So let's take a look at the available Gtk::Action::create() functions:

> static Glib::RefPtr< Action > 	create ()
static Glib::RefPtr< Action > 	create (const Glib::ustring& name, const Glib::ustring& label=Glib::ustring(), const Glib::ustring& tooltip=Glib::ustring())
 	Creates an action.
static Glib::RefPtr< Action > 	create (const Glib::ustring& name, const Gtk::StockID& stock_id, const Glib::ustring& label=Glib::ustring(), const Glib::ustring& tooltip=Glib::ustring())
 	Creates an action with a stock ID.
static Glib::RefPtr< Action > 	create_with_icon_name (const Glib::ustring& name, const Glib::ustring& icon_name, const Glib::ustring& label, const Glib::ustring& tooltip)
 	Create an action with an icon name. 

In your code snippet you obviously use the third variation. So let's take a look at this function's full [documentation](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Action.html#a243f002b8d3528e4876cb23225fa757b)

> static Glib::RefPtr<Action> Gtk::Action::create  	(  	const Glib::ustring &   	 name,
		const Gtk::StockID&  	stock_id,
		const Glib::ustring &  	label = Glib::ustring(),
		const Glib::ustring &  	tooltip = Glib::ustring()	 
	) 			[static]

Creates an action with a stock ID.

The stock ID is used to set a default icon, text and accelerator for the action.

Parameters:
    	name 	A unique name for the action.
    	stock_id 	The stock icon to display in widgets representing the action.
    	label 	The label displayed in menu items and on buttons.
    	tooltip 	A tooltip for the action.

Returns:
    A new Action. 

Reimplemented in Gtk::RecentAction.


You don't assign a value for the **label** and **tooltip** parameter, so their defaults are used(an empty string). To define a tooltip all you have to do is this:

[php]
//CODE SNIPPET from mainwindow.cc
m_refActionGroup->add( Gtk::Action::create("New", Gtk::Stock::NEW, Glib::ustring(), "Example tooltip text"), 
sigc::mem_fun(*this, &MWindow::on_action_file_new) );  [/php]

---

### Post by fallenshadow on 2010-01-15
Thanks for those links and helping to explain the documentation a bit better. Now I might actually be able to read and understand documentation a bit more.

I am looking for something to function as a toolbox for my application and I think the thing I am looking for is actually called a toolpalette. (but I could be wrong)

However I downloaded the toolpalette example from the GTKmm site and it would not compile. I am wondering does it compile for you?

---

### Post by SledgeHammer_999 on 2010-01-15
I don't know what are you talking about... I never heard of toolpalette.

Are you sure it is called a toolpalette? Could you provide a screenshot of what you have in mind from another application?

---

### Post by fallenshadow on 2010-01-16
See the toolbox on the right side of this screenshot (contains paintbrushes, paintbucket etc...)

[http://www.photofiltre-lx.org/pics/crop1.png](http://www.photofiltre-lx.org/pics/crop1.png)
---

Thats what I want to find in GTKmm... I think they call it a toolpalette on the GTKmm site.

[http://git.gnome.org/browse/gtkmm-documentation/tree/examples/book](http://git.gnome.org/browse/gtkmm-documentation/tree/examples/book)

I tried to compile the example for toolpalette but it gives me a very long list of errors. I want to compile it to see if its what im looking for since the GTKmm site does not provide any screenshots.

---

### Post by SledgeHammer_999 on 2010-01-16
Hmmm the example code misses an #include about Gtk::ToolPaletted which is:
```
#include <gtkmm/toolpalette.h>
```

But this doesn't seem to work on my system. This header is available. I found the gtkmm docs here->[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1ToolPalette.html](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1ToolPalette.html)

I think this widget is added at a newer version of Gtkmm(although the docs don't mention something). Maybe these are included in the next release of Gtkmm(2.20).

---

### Post by SledgeHammer_999 on 2010-01-16
Yes I was right. I found the corresponding docs for Gtk+-->[http://library.gnome.org/devel/gtk/unstable/GtkToolPalette.html](http://library.gnome.org/devel/gtk/unstable/GtkToolPalette.html)

These docs are on the "unstable" release. And each function mentions that it will be available "Since 2.20". So maybe they are included in the next ubuntu release.

---

### Post by fallenshadow on 2010-01-16
Hmm... I hope its in Ubuntu 10.04LTS because I will be upgrading to that when its out.

I guess I will put the toolpalette off until I can actually use it. Until then I will work on other things.

---

### Post by fallenshadow on 2010-01-18
Another thing I came across is this: 

set_logo()
[Found it here]("http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1AboutDialog.html")

Which says it can be used in GTKmm 2.6... is this referring to the unreleased 2.20 of GTKmm?

---

### Post by SledgeHammer_999 on 2010-01-18
I'm not sure :S Try to use it and if the code doesn't compile then you have your answer :p (the compiler will say that it cannot find the set_logo() function)

---

### Post by fallenshadow on 2010-01-23
Yes the set_logo() function isnt available yet either. :D

Anyway Im trying to do a double frame inside one window and it is causing me trouble. I have tried 2 very different methods and neither one works.

I need to know which method is more correct... both are included in my latest code. The first compiles but shows only 1 frame and the second just fails. :P

UPDATE: I made changes to the second one today... now both compile but show different Frames... not both yet.

---

### Post by fallenshadow on 2010-01-25
Ok I now added a third attempted method... one which may actually work properly.

Only problems are these two errors bugging me:

[PHP]new.cc:25: error: class ‘Newfile’ does not have any field named ‘m_frame_first’
new.cc:26: error: class ‘Newfile’ does not have any field named ‘m_frame_second’
[/PHP]

Files are in latest code inside Newfiledialog/Method3. How would I sort this out? Any advice would really help...

---

### Post by dwhitney67 on 2010-01-25
> **fallenshadow said:**
> 
Files are in latest code inside Newfiledialog/Method3. How would I sort this out? Any advice would really help...

wtf?  why don't you post the relevant code of new.cc, particular lines 25 and 26.  If Newfile is an object, then post the code for the header file that defines it.

---

### Post by fallenshadow on 2010-01-25
There is no point in just posting up the code for lines 25 and 26. The files need to be seen as a whole in case its a problem somewhere else causing the error messages for 25, 26.

I think its better if people just download the code and look at it as a whole.

---

### Post by dwhitney67 on 2010-01-25
> **fallenshadow said:**
> There is no point in just posting up the code for lines 25 and 26. The files need to be seen as a whole in case its a problem somewhere else causing the error messages for 25, 26.

I think its better if people just download the code and look at it as a whole.
Great!  Then where can we find the code?  I have no desire to peruse 10+ pages of this thread looking for your code.  For trivial compiler errors, someone should have answered your query by now.  Perhaps they are like me... unwilling to search for your code.

---

### Post by SledgeHammer_999 on 2010-01-25
@dwhitney67
the link is here-->[http://www.photofiltre-lx.org/Source/PhotoFiltre-LX%20-%20latest.tar.gz](http://www.photofiltre-lx.org/Source/PhotoFiltre-LX%20-%20latest.tar.gz)

@fallenshadow
I only looked at your first method. And you have done a very basic mistake. You need 2 Gtk::Frames, right? Then why do you declare in your class implementation only ONE variable of type Gtk::Frame? (in new.h) You cannot add the same widget in a container if it is already in a container. You need to remove it first. When you run your program from the terminal you get the following Gtk-warning that warns you about it:
> (test:3232): Gtk-WARNING **: Attempting to add a widget with type gtkmm__GtkFrame to a container of type gtkmm__GtkWindow, but the widget is already inside a container of type gtkmm__GtkWindow, the GTK+ FAQ at [http://library.gnome.org/devel/gtk-faq/stable/](http://library.gnome.org/devel/gtk-faq/stable/) explains how to reparent a widget.

So a simple way to solve this is this. In **new.h** at line 33 change this:
[php]Gtk::Frame m_Frame;[/php]
to:
[php]Gtk::Frame m_Frame, m_Frame1;[/php]
or add another line below it:
[php]Gtk::Frame m_Frame1;[/php]

In new.cc
change:
[php]add(m_Frame);
add(m_Frame);[/php]
to:
[php]
add(m_Frame);
add(m_Frame1);[/php]
This:
[php]m_Frame.set_label("Size in pixels/memory");
m_Frame.set_label("New size");[/php]
to this:
[php]m_Frame.set_label("Size in pixels/memory");
m_Frame1.set_label("New size");[/php]
This:
[php]m_Frame.set_shadow_type(Gtk::SHADOW_ETCHED_OUT);
m_Frame.set_shadow_type(Gtk::SHADOW_ETCHED_OUT);[/php]
to this:
[php]m_Frame.set_shadow_type(Gtk::SHADOW_ETCHED_OUT);
m_Frame1.set_shadow_type(Gtk::SHADOW_ETCHED_OUT);[/php]

Basically what you did in Newfile::Newfile() is change the properties of the SAME Gtk::Frame TWICE.

BUT YOU MUST DO ANOTHER CHANGE. You need to add() to the Gtk::Window a container first such as Gtk::VBox. Then you must add() the 2 Gtk::Frames in the Gtk::VBox(or another container). A Gtk::Window can contain only ONE widget (it is a Gtk::Bin).

I hope I didn't confuse you too much.

I am not going to look to the other two methods, unless you need more help.

---

### Post by fallenshadow on 2010-01-25
Wow I did the rest myself... Im feeling mighty proud!

I combined some of the code from my method3 with method1 and it all works nicely together.

Who knows... I may be a good developer yet! :D

---

### Post by fallenshadow on 2010-02-01
Of course after making that great progress myself I then got stuck. :D

I can't seem to figure out how to put widgets inside a frame. I thought it would be easier than it is. However I did make an attempt in a folder called Newfiledialog2. 

It compiles but my textbox is not showing... please tell me if it was a good attempt or horrible! :D and maybe some tips to help me do it. :)

---

### Post by SledgeHammer_999 on 2010-02-01
I don't have the time now but a few suggestions from the top of my head:
1.Use Gtk::Frame::add() because a Gtk::Frame is a Gtk::Container.
2.You cannot Gtk::Frame::add() 2 or more widgets because Gtk::Frame is also a Gtk::Bin(a container that can hold only one child). To work around this you do a Gtk::Frame::add() to add another container like(Gtk::VBox) and then you add widgets inside that container(eg a Gtk::VBox with *pack_start()/*pack_end())

---

### Post by fallenshadow on 2010-02-01
I found your tips kinda vague... but in the end I got it to work! :)

Quick question... how do you know when you should use a VBox or a HBox? :confused:

---

### Post by SledgeHammer_999 on 2010-02-01
It depends on your needs. Maybe you should read the Gtk+(C language) tutorial a bit just to understand how gtk works.(about the container part)

On top of the page that documents Gtk::Frame it shows it's inheritance diagram.(read about class inheritance in a C++ tutorial). You will notice that it inherits from a Gtk::Bin. Gtk::Bin(therefore Gtk::Frame too) inherits from Gtk::Container. Gtk::Bin is a special container that can hold only one child-widget(that's why you need to add another container inside it to hold more child-widgets).

Don't forget that Gtk::Frame, Gtk::Bin, Gtk::Container are all classes.

So basically what you had to do is this:
1.create a container named A
2.put inside A all the widgets you want
3.put A inside a Gtk::Frame
4.???
5.Profit (lol joke)

---

### Post by fallenshadow on 2010-02-02
> So basically what you had to do is this:
1.create a container named A
2.put inside A all the widgets you want
3.put A inside a Gtk::Frame
4.???
5.Profit (lol joke)

Yep thats basically what I did! (except profit :D ) 

I soon realised I should have been using a HBox instead of a VBox in my first frame.
I now know I should use a VBox for my second frame. 

The only thing I need to figure out is how to align widgets. I did look at the alignment example and I tried some of the code to see would it work but the textbox I used it on disappeared! :D :o

---

### Post by SledgeHammer_999 on 2010-02-02
For alignment(not the widget): That's a bit tricky. It involves putting several VBoxes inside an HBox(or vice versa) and exmperimenting with the "expand/fill" parameters of pack_start()/pack_end(). I myself can't work with this very quickly. I suggest you install glade and make mockups of your windows there. Then translate the options to code or even use the *.glade file directly with gtkmm and don't do any coding.
(read the appropriate sections in gtk's and gtkmm's tutorials)

---

### Post by fallenshadow on 2010-02-03
I have been thinking about which method would be better. Using code only may be slow but at least I have a pretty good idea at what im doing.

The best thing about using glade with GTKmm is my dialogs could be designed very fast and even by non-developers. However with only one example to look at Im not sure I could figure out how to work with widgets,functions etc.

Have you experience working with both? Which in your opinion would be the better (easier) option?

---

### Post by SledgeHammer_999 on 2010-02-03
That's a personal preference. I can't really tell you. Pick whatever you feel comfortable with. 

I personally prefer coding it but then again I haven't released any real project. I just do it for fun. And I code it by hand because that way I learn how the toolkit works(trial-and-error). I generally have an idea how glade files work, but I haven't used it.

I think for begginers glade is easier(but this may vary). In glade files each widget has a name. Also in Gtk/glade(C language) theres a function glade_get_widget() (or something similar). You give it the name of the widget you want and it returns a pointer to it(to a GtkWIdget). Then you can use the appropriate functions on it(maybe with casting it to the appropriate widget eg GtkWidget-->GtkButton). Obviously gtkmm has equivalent methods but I haven't researched the subject :P

---

### Post by fallenshadow on 2010-02-03
Im much more comfortable with the idea of doing this with code as I already have some of my Newfiledialog done with pure code.

Best thing is if I run into a spot of trouble I can ask you and you would surely know whats going wrong.

If you could explain the expand and fill options because I have not come across these yet. What can they do for me? Where do they go?

---

### Post by fallenshadow on 2010-02-04
Didn't need to find out about Fill or Expand as:

[PHP]
Gtk::PACK_SHRINK
[/PHP]

worked out nicely for my first frame. Now its looking like I want it to.

One thing that has been driving me up the wall is labels! ](*,)

However I think I figured out now that I will have to put a HBox above my existing HBox in order to get them where I want them. (above my textboxes) Is this idea correct?

Also does GTKmm have such a thing as a child window?
(a window that holds an open file) You might not know what im asking about but think of opening files in Openoffice... :P

---

### Post by resander on 2010-02-05
It may be a little late (didn't know about this thread until now), but I think it is a lot easier to start with GTK+ and C because there are GTK forums at [www.gtkforums.com](www.gtkforums.com), a mailing list at [email]gtk-list@gnome.org[/email] and a book 'Foundations of GTK+ Development' by Andrew Krause. The documentation at gtk.org is not ideal, but is kept reasonably uptodate.

I found GTK+ hard to learn it took weeks, while learning the Windows GUI at the same level took a couple of days only. Starting with gtkmm means you have to learn that plus gtk+ at the same time. A tall order.  

Examples of GTK+ are given in C, but that does not mean you have to program in C. You can use C++ too, but I cannot see any advantage in doing that for making the GUI come out the way you want.

I said goodbye to Windows about two years ago and have been a happy user of Ubuntu ever since. Have been using codeblocks for program development and have had no problems compiling, running and debugging GTK programs.

I especially like getting fresh versions of codeblocks about once month via the normal Ubuntu update function. I click if I want an update, wait a minute or two and then the new codeblocks version is ready to use without me having to do anything. Details for getting these updates are available at [http://forums.codeblocks.org](http://forums.codeblocks.org). Jens is organising this and you need to subscribe by setting Software Sources in Ubuntu as described by Jens to get all components needed for the updates.

---

### Post by fallenshadow on 2010-02-05
Well im a bit too far in with GTKmm to just dump it and start again with GTK+ and C. 

I used to be a fan of Codeblocks but after a while I got sick of it. It just seems too slow starting up... thats what bugged me the most and also the project management was awful. (in my opinion of course) ;)

Now I am using Geany which im finding quite excellent. I like the way you can just paste the line of terminal code into the compiler setup so it will just run that code every time you click the compile button. Geany is straight forward, simple and fast but thats really what I want in an IDE! :D

---

### Post by fallenshadow on 2010-02-18
I wonder could the all great spare some of his free time to help with labels? :)

In my latest code I have been trying to get my label to appear above the textbox rather than beside it. I thought the right method would be to place a separate HBox above my other one. 

I also thought my label would appear nicely above my textbox but it somehow went beside my textbox! ](*,)

---

### Post by nagaraj dr on 2010-02-19
i am having some serious problem with compilation of my gtk program..
i tried to compile it by gcc -I/usr/include/gtk-2.0 test.c
but it gave some 1000 errors. somone plz help me


/usr/include/gtk-2.0/gtk/gtktreestore.h:99: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:102: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:104: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:108: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:112: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:116: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:121: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:128: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:131: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:134: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:137: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtktreestore.h:139: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:140: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:142: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:145: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:148: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:151: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktreestore.h:156: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:204,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkuimanager.h:53: error: storage class specified for parameter ‘GtkUIManagerClass’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:54: error: storage class specified for parameter ‘GtkUIManagerPrivate’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:58: error: expected specifier-qualifier-list before ‘GObject’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:57: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkuimanager.h:66: error: expected specifier-qualifier-list before ‘GObjectClass’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:65: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkuimanager.h:106: error: storage class specified for parameter ‘GtkUIManagerItemType’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:113: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:114: error: expected declaration specifiers before ‘GtkUIManager’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:115: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:117: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:118: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:121: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:123: error: expected declaration specifiers before ‘GList’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:124: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:125: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:127: error: expected declaration specifiers before ‘GSList’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:129: error: expected declaration specifiers before ‘GtkAction’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:131: error: expected declaration specifiers before ‘guint’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:135: error: expected declaration specifiers before ‘guint’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:138: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:145: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:147: error: expected declaration specifiers before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:148: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkuimanager.h:149: error: expected declaration specifiers before ‘guint’
/usr/include/gtk-2.0/gtk/gtkuimanager.h:151: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:205,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkvbbox.h:50: error: storage class specified for parameter ‘GtkVButtonBoxClass’
/usr/include/gtk-2.0/gtk/gtkvbbox.h:54: error: expected specifier-qualifier-list before ‘GtkButtonBox’
/usr/include/gtk-2.0/gtk/gtkvbbox.h:52: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvbbox.h:59: error: expected specifier-qualifier-list before ‘GtkButtonBoxClass’
/usr/include/gtk-2.0/gtk/gtkvbbox.h:57: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvbbox.h:63: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkvbbox.h:69: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkvbbox.h:70: error: expected ‘)’ before ‘spacing’
/usr/include/gtk-2.0/gtk/gtkvbbox.h:79: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:209,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:49: error: storage class specified for parameter ‘GtkVolumeButtonClass’
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:53: error: expected specifier-qualifier-list before ‘GtkScaleButton’
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:51: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:58: error: expected specifier-qualifier-list before ‘GtkScaleButtonClass’
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:56: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:67: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkvolumebutton.h:70: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:210,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkvpaned.h:47: error: storage class specified for parameter ‘GtkVPanedClass’
/usr/include/gtk-2.0/gtk/gtkvpaned.h:51: error: expected specifier-qualifier-list before ‘GtkPaned’
/usr/include/gtk-2.0/gtk/gtkvpaned.h:49: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvpaned.h:56: error: expected specifier-qualifier-list before ‘GtkPanedClass’
/usr/include/gtk-2.0/gtk/gtkvpaned.h:54: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvpaned.h:60: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkvpaned.h:63: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:211,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkvruler.h:60: error: storage class specified for parameter ‘GtkVRulerClass’
/usr/include/gtk-2.0/gtk/gtkvruler.h:64: error: expected specifier-qualifier-list before ‘GtkRuler’
/usr/include/gtk-2.0/gtk/gtkvruler.h:62: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvruler.h:69: error: expected specifier-qualifier-list before ‘GtkRulerClass’
/usr/include/gtk-2.0/gtk/gtkvruler.h:67: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvruler.h:73: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkvruler.h:77: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:212,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkvscale.h:50: error: storage class specified for parameter ‘GtkVScaleClass’
/usr/include/gtk-2.0/gtk/gtkvscale.h:54: error: expected specifier-qualifier-list before ‘GtkScale’
/usr/include/gtk-2.0/gtk/gtkvscale.h:52: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvscale.h:59: error: expected specifier-qualifier-list before ‘GtkScaleClass’
/usr/include/gtk-2.0/gtk/gtkvscale.h:57: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvscale.h:63: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkvscale.h:64: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkvscale.h:65: error: expected ‘)’ before ‘min’
/usr/include/gtk-2.0/gtk/gtkvscale.h:70: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:214,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkvseparator.h:50: error: storage class specified for parameter ‘GtkVSeparatorClass’
/usr/include/gtk-2.0/gtk/gtkvseparator.h:54: error: expected specifier-qualifier-list before ‘GtkSeparator’
/usr/include/gtk-2.0/gtk/gtkvseparator.h:52: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvseparator.h:59: error: expected specifier-qualifier-list before ‘GtkSeparatorClass’
/usr/include/gtk-2.0/gtk/gtkvseparator.h:57: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkvseparator.h:63: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkvseparator.h:67: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:224,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkclist.h:58: error: expected declaration specifiers before ‘;’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:68: error: storage class specified for parameter ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:76: error: storage class specified for parameter ‘GtkCListDragPos’
/usr/include/gtk-2.0/gtk/gtkclist.h:84: error: storage class specified for parameter ‘GtkButtonAction’
/usr/include/gtk-2.0/gtk/gtkclist.h:117: error: storage class specified for parameter ‘GtkCList’
/usr/include/gtk-2.0/gtk/gtkclist.h:118: error: storage class specified for parameter ‘GtkCListClass’
/usr/include/gtk-2.0/gtk/gtkclist.h:119: error: storage class specified for parameter ‘GtkCListColumn’
/usr/include/gtk-2.0/gtk/gtkclist.h:120: error: storage class specified for parameter ‘GtkCListRow’
/usr/include/gtk-2.0/gtk/gtkclist.h:122: error: storage class specified for parameter ‘GtkCell’
/usr/include/gtk-2.0/gtk/gtkclist.h:123: error: storage class specified for parameter ‘GtkCellText’
/usr/include/gtk-2.0/gtk/gtkclist.h:124: error: storage class specified for parameter ‘GtkCellPixmap’
/usr/include/gtk-2.0/gtk/gtkclist.h:125: error: storage class specified for parameter ‘GtkCellPixText’
/usr/include/gtk-2.0/gtk/gtkclist.h:126: error: storage class specified for parameter ‘GtkCellWidget’
/usr/include/gtk-2.0/gtk/gtkclist.h:128: error: expected declaration specifiers or ‘...’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:128: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:132: error: storage class specified for parameter ‘GtkCListCellInfo’
/usr/include/gtk-2.0/gtk/gtkclist.h:133: error: storage class specified for parameter ‘GtkCListDestInfo’
/usr/include/gtk-2.0/gtk/gtkclist.h:137: error: expected specifier-qualifier-list before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:135: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:143: error: expected specifier-qualifier-list before ‘GtkCListCellInfo’
/usr/include/gtk-2.0/gtk/gtkclist.h:141: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:149: error: expected specifier-qualifier-list before ‘GtkContainer’
/usr/include/gtk-2.0/gtk/gtkclist.h:147: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:247: error: expected specifier-qualifier-list before ‘GtkContainerClass’
/usr/include/gtk-2.0/gtk/gtkclist.h:245: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:326: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkclist.h:324: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:346: error: expected specifier-qualifier-list before ‘GtkCell’
/usr/include/gtk-2.0/gtk/gtkclist.h:344: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:365: error: expected specifier-qualifier-list before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:363: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:377: error: expected specifier-qualifier-list before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:375: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:390: error: expected specifier-qualifier-list before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:388: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:405: error: expected specifier-qualifier-list before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:403: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:417: error: expected specifier-qualifier-list before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:415: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkclist.h:443: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkclist.h:446: error: expected ‘)’ before ‘columns’
/usr/include/gtk-2.0/gtk/gtkclist.h:447: error: expected ‘)’ before ‘columns’
/usr/include/gtk-2.0/gtk/gtkclist.h:451: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:453: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:457: error: expected declaration specifiers before ‘GtkAdjustment’
/usr/include/gtk-2.0/gtk/gtkclist.h:458: error: expected declaration specifiers before ‘GtkAdjustment’
/usr/include/gtk-2.0/gtk/gtkclist.h:461: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:465: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:469: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:471: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:473: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:481: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:482: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:485: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:486: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:492: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:494: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:496: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:497: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:500: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:505: error: expected declaration specifiers before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkclist.h:509: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:514: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:518: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:523: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:528: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:533: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:537: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:540: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:547: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:552: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:555: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:562: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:570: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:577: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:581: error: expected declaration specifiers before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkclist.h:586: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:594: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:600: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:606: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:613: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:621: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:632: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:639: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:644: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:649: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:653: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:657: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:664: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:671: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:674: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:680: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:682: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:688: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:693: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:697: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:702: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:708: error: expected declaration specifiers before ‘gpointer’
/usr/include/gtk-2.0/gtk/gtkclist.h:714: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:718: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:723: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:728: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:733: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:739: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkclist.h:746: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:749: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:752: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:757: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:762: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:766: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:770: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:774: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:777: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkclist.h:782: error: expected declaration specifiers before ‘PangoLayout’
/usr/include/gtk-2.0/gtk/gtkclist.h:787: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:225,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkcombo.h:46: error: storage class specified for parameter ‘GtkComboClass’
/usr/include/gtk-2.0/gtk/gtkcombo.h:50: error: expected specifier-qualifier-list before ‘GtkHBox’
/usr/include/gtk-2.0/gtk/gtkcombo.h:49: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkcombo.h:78: error: expected specifier-qualifier-list before ‘GtkHBoxClass’
/usr/include/gtk-2.0/gtk/gtkcombo.h:77: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkcombo.h:87: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkcombo.h:91: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:95: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:98: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:101: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:105: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:109: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:112: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkcombo.h:114: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:226,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkctree.h:60: error: expected declaration specifiers before ‘GtkCTreePos’
/usr/include/gtk-2.0/gtk/gtkctree.h:68: error: storage class specified for parameter ‘GtkCTreeLineStyle’
/usr/include/gtk-2.0/gtk/gtkctree.h:76: error: storage class specified for parameter ‘GtkCTreeExpanderStyle’
/usr/include/gtk-2.0/gtk/gtkctree.h:86: error: storage class specified for parameter ‘GtkCTreeExpansionType’
/usr/include/gtk-2.0/gtk/gtkctree.h:88: error: storage class specified for parameter ‘GtkCTree’
/usr/include/gtk-2.0/gtk/gtkctree.h:89: error: storage class specified for parameter ‘GtkCTreeClass’
/usr/include/gtk-2.0/gtk/gtkctree.h:90: error: storage class specified for parameter ‘GtkCTreeRow’
/usr/include/gtk-2.0/gtk/gtkctree.h:91: error: storage class specified for parameter ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:93: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:97: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:103: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:110: error: expected specifier-qualifier-list before ‘GtkCList’
/usr/include/gtk-2.0/gtk/gtkctree.h:108: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkctree.h:127: error: expected specifier-qualifier-list before ‘GtkCListClass’
/usr/include/gtk-2.0/gtk/gtkctree.h:125: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkctree.h:149: error: expected specifier-qualifier-list before ‘GtkCListRow’
/usr/include/gtk-2.0/gtk/gtkctree.h:147: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkctree.h:167: error: expected specifier-qualifier-list before ‘GList’
/usr/include/gtk-2.0/gtk/gtkctree.h:166: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkctree.h:175: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkctree.h:176: error: expected ‘)’ before ‘columns’
/usr/include/gtk-2.0/gtk/gtkctree.h:179: error: expected ‘)’ before ‘columns’
/usr/include/gtk-2.0/gtk/gtkctree.h:181: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:192: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:194: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:200: error: expected declaration specifiers before ‘GNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:212: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:216: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:221: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:225: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:230: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:232: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:234: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:236: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:238: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:241: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:244: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:248: error: expected declaration specifiers before ‘GList’
/usr/include/gtk-2.0/gtk/gtkctree.h:251: error: expected declaration specifiers before ‘GtkCTreeNode’
/usr/include/gtk-2.0/gtk/gtkctree.h:256: error: expected declaration specifiers before ‘GList’
/usr/include/gtk-2.0/gtk/gtkctree.h:260: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:268: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:272: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:274: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:276: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:279: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:281: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:283: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:286: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:288: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:290: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:292: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:294: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:296: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:298: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:306: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:310: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:315: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:322: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:332: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:337: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:340: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:342: error: expected declaration specifiers before ‘GtkCellType’
/usr/include/gtk-2.0/gtk/gtkctree.h:345: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:349: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:354: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:361: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:371: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:374: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:376: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:380: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:383: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:386: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:389: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:392: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:396: error: expected declaration specifiers before ‘gpointer’
/usr/include/gtk-2.0/gtk/gtkctree.h:398: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:403: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:410: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:412: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:414: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:416: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:418: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:420: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:427: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:429: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkctree.h:439: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkctree.h:441: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:227,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkfilesel.h:47: error: storage class specified for parameter ‘GtkFileSelectionClass’
/usr/include/gtk-2.0/gtk/gtkfilesel.h:52: error: expected specifier-qualifier-list before ‘GtkDialog’
/usr/include/gtk-2.0/gtk/gtkfilesel.h:49: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkfilesel.h:85: error: expected specifier-qualifier-list before ‘GtkDialogClass’
/usr/include/gtk-2.0/gtk/gtkfilesel.h:83: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkfilesel.h:102: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkfilesel.h:103: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:104: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:106: error: expected declaration specifiers before ‘G_CONST_RETURN’
/usr/include/gtk-2.0/gtk/gtkfilesel.h:108: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:110: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:111: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:113: error: expected declaration specifiers before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkfilesel.h:115: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:117: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkfilesel.h:120: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:228,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:47: error: storage class specified for parameter ‘GtkItemFactoryCallback’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:48: error: expected ‘)’ before ‘callback_data’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:60: error: storage class specified for parameter ‘GtkItemFactory’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:61: error: storage class specified for parameter ‘GtkItemFactoryClass’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:62: error: storage class specified for parameter ‘GtkItemFactoryEntry’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:63: error: storage class specified for parameter ‘GtkItemFactoryItem’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:69: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:65: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:83: error: expected specifier-qualifier-list before ‘GHashTable’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:79: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:94: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:92: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:127: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:125: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:132: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:137: error: expected declaration specifiers before ‘GtkItemFactory’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:140: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:148: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:153: error: expected declaration specifiers before ‘GtkItemFactory’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:154: error: expected declaration specifiers before ‘G_CONST_RETURN’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:156: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:158: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:160: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:162: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:165: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:169: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:173: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:175: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:177: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:180: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:185: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:192: error: expected declaration specifiers before ‘gpointer’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:193: error: expected declaration specifiers before ‘gpointer’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:194: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:204: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:204: error: storage class specified for parameter ‘GtkMenuCallback’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:206: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:211: error: storage class specified for parameter ‘GtkMenuEntry’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:215: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:216: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:216: error: storage class specified for parameter ‘GtkItemFactoryCallback2’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:219: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:225: error: expected declaration specifiers before ‘GtkItemFactory’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:226: error: expected ‘)’ before ‘n_entries’
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:228: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:231: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:229,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtklist.h:45: error: storage class specified for parameter ‘GtkListClass’
/usr/include/gtk-2.0/gtk/gtklist.h:49: error: expected specifier-qualifier-list before ‘GtkContainer’
/usr/include/gtk-2.0/gtk/gtklist.h:47: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtklist.h:74: error: expected specifier-qualifier-list before ‘GtkContainerClass’
/usr/include/gtk-2.0/gtk/gtklist.h:72: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtklist.h:84: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtklist.h:86: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:89: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:91: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:93: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:95: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:97: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:100: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:102: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:104: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:106: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:108: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtklist.h:110: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:113: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:117: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:118: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:119: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:120: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:121: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:124: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:127: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:128: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:129: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:131: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:132: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklist.h:134: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:230,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtklistitem.h:47: error: storage class specified for parameter ‘GtkListItemClass’
/usr/include/gtk-2.0/gtk/gtklistitem.h:51: error: expected specifier-qualifier-list before ‘GtkItem’
/usr/include/gtk-2.0/gtk/gtklistitem.h:49: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtklistitem.h:56: error: expected specifier-qualifier-list before ‘GtkItemClass’
/usr/include/gtk-2.0/gtk/gtklistitem.h:54: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtklistitem.h:78: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtklistitem.h:80: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklistitem.h:81: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklistitem.h:82: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtklistitem.h:86: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:231,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:46: error: storage class specified for parameter ‘GtkOldEditableClass’
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:48: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:52: error: field ‘widget’ has incomplete type
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:55: error: expected specifier-qualifier-list before ‘guint’
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:50: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:70: error: expected specifier-qualifier-list before ‘GtkWidgetClass’
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:68: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:116: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:117: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:120: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoldeditable.h:122: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:232,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:46: error: storage class specified for parameter ‘GtkOptionMenuClass’
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:50: error: expected specifier-qualifier-list before ‘GtkButton’
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:48: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:61: error: expected specifier-qualifier-list before ‘GtkButtonClass’
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:59: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:73: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:75: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:76: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:78: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:79: error: expected declaration specifiers before ‘gint’
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:80: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkoptionmenu.h:84: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:234,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtkpreview.h:46: error: storage class specified for parameter ‘GtkPreviewInfo’
/usr/include/gtk-2.0/gtk/gtkpreview.h:47: error: storage class specified for parameter ‘GtkDitherInfo’
/usr/include/gtk-2.0/gtk/gtkpreview.h:48: error: storage class specified for parameter ‘GtkPreviewClass’
/usr/include/gtk-2.0/gtk/gtkpreview.h:52: error: field ‘widget’ has incomplete type
/usr/include/gtk-2.0/gtk/gtkpreview.h:54: error: expected specifier-qualifier-list before ‘guchar’
/usr/include/gtk-2.0/gtk/gtkpreview.h:50: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkpreview.h:69: error: expected specifier-qualifier-list before ‘guchar’
/usr/include/gtk-2.0/gtk/gtkpreview.h:67: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkpreview.h:76: error: expected specifier-qualifier-list before ‘gushort’
/usr/include/gtk-2.0/gtk/gtkpreview.h:74: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkpreview.h:82: error: expected specifier-qualifier-list before ‘GtkWidgetClass’
/usr/include/gtk-2.0/gtk/gtkpreview.h:80: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtkpreview.h:89: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtkpreview.h:92: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkpreview.h:95: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkpreview.h:104: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkpreview.h:109: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkpreview.h:113: error: expected ‘)’ before ‘nred_shades’
/usr/include/gtk-2.0/gtk/gtkpreview.h:117: error: expected ‘)’ before ‘install_cmap’
/usr/include/gtk-2.0/gtk/gtkpreview.h:118: error: expected ‘)’ before ‘nreserved’
/usr/include/gtk-2.0/gtk/gtkpreview.h:119: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkpreview.h:123: error: expected declaration specifiers before ‘GtkPreviewInfo’
/usr/include/gtk-2.0/gtk/gtkpreview.h:133: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk-2.0/gtk/gtk.h:237,
                 from test.c:1:
/usr/include/gtk-2.0/gtk/gtktipsquery.h:52: error: storage class specified for parameter ‘GtkTipsQueryClass’
/usr/include/gtk-2.0/gtk/gtktipsquery.h:58: error: expected specifier-qualifier-list before ‘GtkLabel’
/usr/include/gtk-2.0/gtk/gtktipsquery.h:56: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtktipsquery.h:73: error: expected specifier-qualifier-list before ‘GtkLabelClass’
/usr/include/gtk-2.0/gtk/gtktipsquery.h:71: warning: empty declaration
/usr/include/gtk-2.0/gtk/gtktipsquery.h:96: error: expected declaration specifiers before ‘GType’
/usr/include/gtk-2.0/gtk/gtktipsquery.h:98: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktipsquery.h:99: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktipsquery.h:100: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktipsquery.h:102: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtktipsquery.h:106: error: expected declaration specifiers before ‘G_END_DECLS’

---

### Post by Some Penguin on 2010-02-19
For C++, use g++.

---

### Post by nagaraj dr on 2010-02-20
what is g++ mean.. i cant get it..

---

### Post by SledgeHammer_999 on 2010-02-20
@nagajir dr

If you're using C then do in a terminal:
```
gcc test.c -o test `pkg-config gtk+-2.0 --cflags --libs`
```
link-->[http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)

If you're using C++ and gtkmm then do in a terminal:
```
g++ test.c -o test`pkg-config gtkmm-2.4 --cflags --libs`
```
link--->[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-basics-simple-example.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-basics-simple-example.html.en)

If you're using C++ and gtk+ then do in a terminal:
```
g++ test.c -o test `pkg-config gtk+-2.0 --cflags --libs`
```

gcc is the C compiler. g++ is the C++ compiler. (on ubuntu)


@fallenshadow
sorry I didn't have time to take a look at your code yet...

---

### Post by nagaraj dr on 2010-02-21
i tried this...

drna@ubuntu:~/cfiles$ gcc test.c -o test 'pkg-config gtk+-2.0 --cflags --libs'
 but it gave..

gcc: pkg-config gtk+-2.0 --cflags --libs: No such file or directory
test.c:1:20: error: gtk/gtk.h: No such file or directory
test.c:2:24: error: gtk/gtkform.h: No such file or directory
test.c:3:30: error: gtk/gtkmainwindow.h: No such file or directory
test.c:4:26: error: gdk/gdkeysyms.h: No such file or directory
test.c:5:25: error: glib/gprintf.h: No such file or directory
test.c:6:27: error: gdk/gdkdisplay.h: No such file or directory
test.c:7:28: error: gtk/gtksoftkeybar: No such file or directory
test.c: In function ‘main’:
test.c:12: error: ‘GtkMainWindow’ undeclared (first use in this function)
test.c:12: error: (Each undeclared identifier is reported only once
test.c:12: error: for each function it appears in.)
test.c:12: error: ‘mainwindow’ undeclared (first use in this function)
test.c:12: error: ‘NULL’ undeclared (first use in this function)

i have gtk-2.0  in my include directory...
is there anything called as compiling include directory..

and even tried manually including the headers by
drna@ubuntu:~/cfiles$ gcc -I/usr/include/gtk-2.0 test.c -o test.exe

it gave the errors in header files as i posted in my first msg

plz help me

---

### Post by SledgeHammer_999 on 2010-02-21
You're doing it wrong. You use a backtick "`" not an apostrophe(?) "'".
Another way to get the same result is:
```
gcc test.c -o test $(pkg-config gtk+-2.0 --cflags --libs)
```


EDIT: Essentialy what pkg-config does is output the necessery include paths and libs. You can see what it outputs for gtk+ if you just run in a terminal:
```
pkg-config gtk+-2.0 --cflags --libs
```
For more info on pkg-config search the internet and read it's docs.

---

### Post by nagaraj dr on 2010-02-21
yes it worked..thank u..
now i have another problem my gtk folder doesnot contain gtkform.h,gtkmainwindow.h, and many more is this my installationn problem.. or should i have to do more to get these headers

---

### Post by SledgeHammer_999 on 2010-02-21
You better create another thread and give more info. eg like some code from your test.c

---

### Post by nagaraj dr on 2010-02-21
i just started with this gtk stuff so i just wanted to make sure all d headers r proper r not, so i just keyed these lines in test.c
 #include<gtk/gtk.h>
#include<gdk/gdk.h>
#include<gtk/gtkwidget.h>
int main()
{

    GtkWidget *form;
    return 0;
}


and when i tried to include gtkform.h it is showing error...
it is obvious because there is no gtkform.h how do i fix this

---

### Post by PmDematagoda on 2010-02-21
Thread closed due to old age.

nagaraj_dr:-
Please create your own thread if you need help with an issue instead of posting in old threads, it's usually more helpful as there is less confusion then.

---

