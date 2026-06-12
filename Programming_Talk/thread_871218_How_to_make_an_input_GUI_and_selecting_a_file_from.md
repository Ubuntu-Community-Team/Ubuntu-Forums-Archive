---
title: "How to make an input GUI and selecting a file from GUI in Perl?"
date: 2008-07-26
forum: Programming Talk
---

### Post by ConMan318 on 2008-07-26
I wrote an alarm program in Perl recently.  It takes in a command line argument of the alarm time and plays a song at the specified time.  Now I want to make this program executable and run it in the GUI, where I obviously can't give it command line arguments.  I've been looking for a good tutorial on Perl GUIs, and have run into some difficulties.

I assume I should be using GTK2?  I've seen things on that and TK, I don't really know which to use.  What's the standard?

Also, as of now I have to edit the source code every time I want to play a different song.  Is there any way for the program to open a file browser and let me navigate through that to pick a file to open?  It'd be much easier than having to type out the whole path to the file.

I've been searching for tutorials, but haven't really found any good ones.  Sample code or links to tutorials would be very helpful.

Thanks.

---

### Post by Kadrus on 2008-07-26
Well you can use any graphical toolkit you want,and the one which makes the job easier for you.I personnally don't like the TK toolkit,and I prefer GTK
[GTK Perl Tutorial]("http://personal.riverusers.com/~swilhelm/gtkperl-tutorial/")
And browse through CPAN,you might find programs that will be useful for you.
[CPAN]("http://www.cpan.org/")

---

### Post by dtmilano on 2008-07-29
A tutorial-like answer, because a simple problem deserves a simple solution.
Let's pretend you have your alarm program writen in perl, alarm.pl.
To increase flexibility it should receive date, time and sound file on command line:

```
alarm.pl "(2006, 7, 29)" "(15, 0, 0)" "chime.mp3"
```

Now, use glade to design a GUI, like this:

[[IMG]http://lh5.ggpht.com/dtmilano/SI8MRVWoP1I/AAAAAAAAAJc/Ku39qxff540/s144/glade-alarm-screenshot.png[/IMG]]("http://picasaweb.google.com/dtmilano/DiegoTorresMilanoSBlog/photo#5228411184329801554")

and name it alarm.glade.

Now, let's create a simple shell script like this:

```
#! /bin/bash
# Copyrigth (C) 2008 Diego Torres Milano. All rights reserved.
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.


AUTOGLADE=autoglade # if not in PATH add absolute path here

DUMP=$($AUTOGLADE alarm.glade)
if [ "$?" -eq 0 ]
then
	eval "$DUMP"
	if ! alarm.pl "$calendar" "($hour, $min, $sec)" "$filename"
	then
		$AUTOGLADE --autoinit="autoErrorDialog('ERROR running alarm')"
		exit 1
	fi
fi
```

Download and install [autoglade]("http://autoglade.sf.net").
Latest version in SVN but published DEB should work fine.

EDIT: Latest autoglade-0.4 packages support all of these features, no need for SVN

Run the script.
And **voila** !
A working GUI, for your alarm program not having to program a single line of GUI code.

Other interesting examples in autoglade tutorial @ SF.

---

### Post by ConMan318 on 2008-08-02
Thank you very much!  That program will come in handy for future scripts too, I'm sure.

---

