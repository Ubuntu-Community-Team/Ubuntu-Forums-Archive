---
title: "Question on GPL licensing and giving credit to orginal author"
date: 2012-11-13
forum: Programming Talk
---

### Post by Erik1984 on 2012-11-13
Currently I have done some work on a project to create an ncurses interface to replace the GUI of RadioTray (RadioTray without the Tray :P).  The ncurses interface module itself is my own work but the rest of the code are either modified version of RadioTray's source files or just the original files in unaltered form. Furthermore I deleted source files that my project does not need.

RadioTray is GPL so I have to (and want to!) release all the new code as GPL too if I want to publish my project. Am I correct?

All source files of RadioTray start with the following:
```

##########################################################################
# Copyright 2009 Carlos Ribeiro
#
# This file is part of Radio Tray
#
# Radio Tray is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 1 of the License, or
# (at your option) any later version.
#
# Radio Tray is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with Radio Tray.  If not, see <http://www.gnu.org/licenses/>.
#
##########################################################################


```What If I made some modifications to such a file, should I mention that in the copyright notice? Should I 'take over' the copyright or mention the original author as well? In case I did not change anything can I leave this part unaltered? 

Just want to do this right and fair but have never really released any code so, that's why I am asking.

---

### Post by Bachstelze on 2012-11-13
If you don't touch a file, really don't touch it (i.e. don't modify the header). If you modify a file, add your name below the original author's. For consistency, I would also add the same header on the files that you have added (but with your name only of course).

---

### Post by Erik1984 on 2012-11-16
Thanks, Bachstelze. I'll mark this question as solved.

---

