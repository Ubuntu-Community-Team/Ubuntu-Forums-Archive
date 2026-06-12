---
title: "Code::Blocks and QT4"
date: 2008-02-05
forum: Programming Talk
---

### Post by RemmyLee on 2008-02-05
Here's a little walkthrough to using QT4 with Code:Blocks.

> **What this assumes**:

1. You have QT4 and Code::Bocks installed.
2. You know how to use qmake.


**Step 1:**
You're going to need a special little tool known as qt-prebuild (see attachment). Build it and place somewhere easily accessible.

**Step 2:**
Here is the setup:

[IMG]http://farm3.static.flickr.com/2343/2244967963_bfe9b827fa_o.png[/IMG]
[IMG]http://farm3.static.flickr.com/2248/2244968051_3dfcec3183_o.png[/IMG]
[IMG]http://farm3.static.flickr.com/2175/2245762734_d32b1c8e26_o.png[/IMG]
[IMG]http://farm3.static.flickr.com/2108/2245762818_f94ce96444_o.png[/IMG]
[IMG]http://farm3.static.flickr.com/2010/2244968325_da2b0569d3_o.png[/IMG]
[IMG]http://farm3.static.flickr.com/2086/2244968413_f37eba5345_o.png[/IMG]

**Step 3:**
Compile.

Remember to copy your setup over to Release as well and have fun coding!

---

### Post by sspeed on 2008-04-27
I manage to get the file but the pictures are not available anymore. Is there any way you can post them again. Thanks

---

### Post by nilankaraja on 2008-08-05
I had the same problem. went through various forums and found this answer. The wizard now works and generates a compilable project. The paths are given in the picture. 

I installed the following packages using the synaptic package manager

libqt4-core libqt4-gui libqt4-debug libqt4-dev qt4-designer qt4-dev-tools qt4-doc

should work

---

### Post by rquin on 2008-08-25
I set my Global Variables the same as nilankaraja did, as per the screenshot. Unfortunately I get the following errors:```
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|1|error: QApplication: No such file or directory|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|2|error: QFont: No such file or directory|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|3|error: QPushButton: No such file or directory|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp||In function &#8216;int main(int, char**)&#8217;:|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|7|error: &#8216;QApplication&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|7|error: expected `;' before &#8216;app&#8217;|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|9|error: &#8216;QPushButton&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|9|error: expected `;' before &#8216;quit&#8217;|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|11|error: &#8216;quit&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|12|error: &#8216;QFont&#8217; has not been declared|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|12|error: &#8216;QFont&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|14|error: &#8216;QObject&#8217; has not been declared|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|14|error: &#8216;clicked&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|14|error: &#8216;SIGNAL&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|14|error: &#8216;app&#8217; was not declared in this scope|
/home/ronnie/Programming Tests/QT TEST Thing/main.cpp|14|error: &#8216;SLOT&#8217; was not declared in this scope|
||=== Build finished: 15 errors, 0 warnings ===|

```


I checked /usr/inclue/qt4 and all the headers are there in their given directories. Like qapplication.h is under /usr/inclue/qt4/qt. I changed it to that direct path to test, but that gave the same error. I've done the silly things, like test the includes with lowercase, with .h at the end, by trying to include the full path etc. :(

This is the code I'm trying to compile:```
#include <QApplication>
#include <QFont>
#include <QPushButton>

int main(int argc, char* argv[])
{
    QApplication app(argc, argv);

    QPushButton quit("Quit");

    quit.resize(75, 30);
    quit.setFont(QFont("Times", 18, QFont::Bold));

    QObject::connect(&quit, SIGNAL(clicked()), &app, SLOT(quit()));

    quit.show();

    return app.exec();
}
```

Thanks in advance for any help :)


*As per [http://wiki.codeblocks.org/index.php?title=Global_compiler_variables](http://wiki.codeblocks.org/index.php?title=Global_compiler_variables) the Base should be /usr, the lib should be /usr/lib and the include should be /usr/include. Not that it works, haha.

---

### Post by bfhicks on 2008-08-25
I'm not sure b/c i'm at work. But do you have to specify your project to link to the correct objects? I am not sure if that's what nilankaraja is saying, but on my windows version here @ work, I have to go into project build options and specify which libraries I want to link with it -- in your case the qt library.

Project Properties | build options | linker settings (tab)


--not sure if this is what you do on the linux distro as i'm using the windows version

---

### Post by rquin on 2008-08-25
I reviewed the build options and the global variables (See Screens). Thanks for looking at this :)

Unfortunately I still get the error message :(

---

### Post by shulong on 2008-08-30
You can select item.

1. select "project" -> "build options" for add incldue path.

2. select "search directories" -> "compiler"

3. select "add" to add include file.

e.g.
/usr/include
/usr/include/qt4
/usr/include/qt4/Qt
/usr/include/qt4/QtCore
/usr/include/qt4/QtGui
etc...

Then Code:Blocks will find qt incldue file.

---

### Post by Portable_Jim on 2008-12-29
> **shulong said:**
> You can select item.

1. select "project" -> "build options" for add incldue path.

2. select "search directories" -> "compiler"

3. select "add" to add include file.

e.g.
/usr/include
/usr/include/qt4
/usr/include/qt4/Qt
/usr/include/qt4/QtCore
/usr/include/qt4/QtGui
etc...

Then Code:Blocks will find qt incldue file.
Thanks a lot. It works, however I found your instructions a bit hard to follow / unclear / confusing.


[LIST=1]
[*]You should be in a project (just to make it clear for newbies)
[*]Right click on the project (The thing right under workspaces)
[*]Choose Properties
[*]Under "Project settings" (first tab and probably selected by default) click on "Project's build options".
[*]Click on "Search directories"
[*]Click on "Add" and put in "/usr/include/qt4" (or wherever the installation of Qt is - by default on Ubuntu it is put here.)
[/LIST]
(Attached image helps with instructions)

If the program will still not compile, and is producing errors (along the same line) then you may need to add the extra directories
> **shulong said:**
> e.g.
/usr/include
/usr/include/qt4
/usr/include/qt4/Qt
/usr/include/qt4/QtCore
/usr/include/qt4/QtGui
etc....
The button next to the filename you add is the browse. use that to find the other folders by first putting in "/usr/include/qt4", then click on the button. This will show you some of the folders mentioned above, plus more.

---

### Post by Bombenbach on 2010-09-29
None of the proposed solutions actually worked for me (Lucid 10.04 and Code::Blocks from the Lucid repos). The following solution, however, works great!

[http://www.amazing-tutorials.com/qt/configure-qt-with-code-block/](http://www.amazing-tutorials.com/qt/configure-qt-with-code-block/)

---

