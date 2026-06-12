---
title: "C++, Gtk and Anjuta"
date: 2007-09-30
forum: Programming Talk
---

### Post by Mathiasdm on 2007-09-30
I'm trying to use Anjuta and compile the standard Gtkmm file (Anjuta generates it by itself).

However, I get lots of errors. The 'compile' command tells me libglademm/xml.h can't be found, gtkmm.h can't be found, and then (following those two) a bunch of errors about keywords not being defined.

The .cc file in question:
```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
/*
 * main.cc
 * Copyright (C) Mathias 2007 <mathias@>
 * 
 * main.cc is free software.
 * 
 * You may redistribute it and/or modify it under the terms of the
 * GNU General Public License, as published by the Free Software
 * Foundation; either version 2 of the License, or (at your option)
 * any later version.
 * 
 * main.cc is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * See the GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with main.cc.  If not, write to:
 * 	The Free Software Foundation, Inc.,
 * 	51 Franklin Street, Fifth Floor
 * 	Boston, MA  02110-1301, USA.
 */

#include <libglademm/xml.h>
#include <gtkmm.h>
#include <iostream>


#ifdef ENABLE_NLS
#  include <libintl.h>
#endif


/* For testing propose use the local (not installed) glade file */
/* #define GLADE_FILE PACKAGE_DATA_DIR"/gtk-foobar/glade/gtk-foobar.glade" */
#define GLADE_FILE "gtk-foobar.glade"
   
int
main (int argc, char *argv[])
{
	Gtk::Main kit(argc, argv);
	
	//Load the Glade file and instiate its widgets:
	Glib::RefPtr<Gnome::Glade::Xml> refXml;
	try
	{
		refXml = Gnome::Glade::Xml::create(GLADE_FILE);
	}
	catch(const Gnome::Glade::XmlError& ex)
    {
		std::cerr << ex.what() << std::endl;
		return 1;
	}
	Gtk::Window* main_win = 0;
	refXml->get_widget("main_window", main_win);
	if (main_win)
	{
		kit.run(*main_win);
	}
	return 0;
}


```
Oh, and I know the top line says something about 'mode: C', but I did select 'C++' as project type.

---

### Post by ryno519 on 2007-09-30
```
sudo apt-get install libgtkmm-2.4-dev libglademm-2.4-dev
```

That should do it for you.

---

### Post by Mathiasdm on 2007-09-30
I had the first one installed, but not the second one.
Installing it didn't seem to help. I'll try a reboot (just in case).

Also, I forgot to mention: I'm running the Gutsy Gibbon development release.

---

### Post by Mathiasdm on 2007-09-30
Nope, the reboot doesn't give any result. And just to mention, I also had build-essential installed.

---

### Post by badactress on 2007-09-30
I'm not using Anjuta but have had the same problem.. I fixed it by changing the include to:

#include <libglademm-2.4/libglademm/xml.h>

It works but I'm not sure if this is the 'correct' way around it. :)

---

### Post by Mathiasdm on 2007-09-30
It works partially (I still get errors about gtkmm), but I think the solution is rather 'hackish'.

---

### Post by badactress on 2007-09-30
I agree.. A much better solution would be to add the sub-folder to the locations that the compiler looks in for header files. It's been on my list of things-to-sort for ages but never got around to figuring it out!

I have seen that solution given by other people in programming forums so although it does feel nasty, I've kind-of accepted that it's a fairly legitimate way around the problem!

---

### Post by idelovski on 2007-09-30
> **Mathiasdm said:**
> I'm trying to use Anjuta and compile the standard Gtkmm file (Anjuta generates it by itself).

However, I get lots of errors. The 'compile' command tells me libglademm/xml.h can't be found, gtkmm.h can't be found, and then (following those two) a bunch of errors about keywords not being defined.

When you say compile, do you mean 'Compile' command or 'Compile with Make' command?

At least for C projects so it is very likely the same with c++ projects, you can't use first 'Compile' command.

If you need Compile command, you need to put compiling params required for command line compilation into Anjuta. For my project it was like this:

In Settings->Compile and Linker settings... I've put `pkg-config --cflags --libs gtk+-2.0`and both 'Compile' commands now work.

Try to find command line options for Gtkmm projects.

---

### Post by MicahCarrick on 2007-09-30
It really does sound like you don't have libglademm-dev installed. What version of Anjuta are you using and what is the output of:

```
pkg-config --modversion libglademm-2.4
```

I was able to compile Anjuta's gtkmm file just fine using Anjuta 2.2.1 ([Install Notes: Anjuta 2.2.1 on Ubuntu AMD64]("http://www.micahcarrick.com/09-27-2007/anjuta_on_ubuntu_amd64.html")).

I have: 
```
micah@localhost:~$ pkg-config --modversion gtkmm-2.4
2.10.8
micah@localhost:~$ pkg-config --modversion libglademm-2.4
2.6.3

```

---

### Post by Mathiasdm on 2007-09-30
```
mathias@mathias-laptop:~$ pkg-config --modversion gtkmm-2.4
2.12.0
mathias@mathias-laptop:~$ pkg-config --modversion libglademm-2.4
2.6.4

```

It could be the problem idelovski describes, but 'Settings > Compile and Linker settings' isn't in there (perhaps because it's a new Anjuta version).

Oh, and Anjuta is version 2.2.0-1.

---

### Post by MicahCarrick on 2007-09-30
It is not necessary to add gtk or libglade to the compiler linker settings... at least in my version of Anjuta (2.2.1). All configure.in, makefile.in, etc are generated upon creating the new project. Whether I run compile on a single target or build the project--both work.

If you go to 'Project' > 'Properties' and select the 'Packages' tab, you should see both gtkmm-2.4 and libglademm-2.4 in that list. This tells the automake tools to call pkg-config to get the include paths to link to when compiling.

If perhaps you imported your project or for whatever reason, one of those packages are not included in that 'Packages' tab, simply click 'Add Package' and add libglademm-2.4 from the list.

---

### Post by Fixman on 2007-09-30
Try to use "Shift-F11" to build.

---

### Post by Mathiasdm on 2007-10-01
Both of the packages are in that list, so that's apparently not the problem.

Shift-F11 doesn't work, and the 'Build Project' option is greyed out.

Thanks for all the help so far! I hope there's a solution to this problem.

---

### Post by ryno519 on 2007-10-01
> **Mathiasdm said:**
> Both of the packages are in that list, so that's apparently not the problem.

Shift-F11 doesn't work, and the 'Build Project' option is greyed out.

Thanks for all the help so far! I hope there's a solution to this problem.

Out of curiosity, did you install autogen, autoconf and automake before you tried compiling with Anjuta? If not, issue the command;

sudo apt-get install autogen autoconf automake

and try building it again.

---

### Post by Mathiasdm on 2007-10-02
All 3 of them are installed. By the way, I am able to compile 'regular' C++ programs (that only require the standard libraries).

---

### Post by Hairy_Palms on 2007-10-02
it should have an option that says run autogenerate, if you run that then you can build your program.

---

### Post by xtang on 2007-10-03
> **Hairy_Palms said:**
> it should have an option that says run autogenerate, if you run that then you can build your program.

where?

My build option is also greyed out, I just want to compile a simple program to run in the terminal, like I could in the repos version.

---

### Post by MicahCarrick on 2007-10-03
Very strange. Just stabbing in the dark here...

In the build menu, 'Run autoconfigure..." or "Run configure.."
If you don't have a build menu, make sure the 'Automake Build' plugin is enabled.
Try right-clicking project in left pane and seeing if build is greyed out there.
You do have an open project right? Not just a stand-alone file?

---

### Post by xtang on 2007-10-04
> **MicahCarrick said:**
> Very strange. Just stabbing in the dark here...

In the build menu, 'Run autoconfigure..." or "Run configure.."
If you don't have a build menu, make sure the 'Automake Build' plugin is enabled.
Try right-clicking project in left pane and seeing if build is greyed out there.
You do have an open project right? Not just a stand-alone file?

Open project?

I just clicked the "new" button on the toolbar the create the blank file, I can't see any option referring to a project.

I've enabled the Automake plugin, the only options available are compile ad run.

---

### Post by MicahCarrick on 2007-10-04
I could be wrong, but, I think you typically need to establish a project in order to "build". I don't know if you can just run gcc on a single file or not--though it would make sense if you could.

File > New > Project
Click Forward
C++ tab, 'Generic C++'
Click Forward a few times

You should be able to 'Build' > 'Build Project'
and then 'Build' > 'Execute Program' 

which runs "Hello World" in the terminal.'

---

