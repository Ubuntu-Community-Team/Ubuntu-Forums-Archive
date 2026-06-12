---
title: "Code::Blocks compiles and installs but wont run"
date: 2006-02-10
forum: Packaging and Compiling Programs
---

### Post by captaincrisis on 2006-02-10
After several hours of messing around I got Code::Blocks compiled and installed (without errors) but now I just get:

"Error with displaying error for dialog of class cannot_load_entry"

when I try to run it.  <sigh>

Any suggestions would be welcome

---

### Post by captaincrisis on 2006-02-10
Weird.  Installed kdevelop3, rebooted and it works now.  :confused:

---

### Post by ibabob on 2006-02-14
Hummm weird I have the same error but installing KDevellop and rebooting didn't change anything.

Any suggestions ?

---

### Post by cstudent on 2006-03-09
I downloaded the ubuntu deb this evening from the codeblocks website. I got the error too when I first tried to fire up the program from the menu. However, I could start it from the terminal no problem. After playing around a bit I came up with a working solution. Edit the codeblocks.desktop file in /usr/share/applications and comment out (or remove it if you wish) the line:

Encoding=UTF-8

---

### Post by MichaelZ on 2006-03-11
Hello,

[quote=cstudent]I downloaded the ubuntu deb this evening from the codeblocks website. I got the error too when I first tried to fire up the program from the menu.
[/quote] 
Sorry, but which .deb package do you have downloaded/installed? 

[quote=cstudent]After playing around a bit I came up with a working solution. Edit the codeblocks.desktop file in /usr/share/applications and comment out (or remove it if you wish) the line:

Encoding=UTF-8
[/quote] 
I am not sure that this is a solution. Code::Blocks should be built in unicode mode. May be you mixed out unicode and ansi.

I have build Code::Blocks both with the make and its project file and never get a problem. Anyway, you can get the new SVN build of Code::Blocks (rev2173) and check if you still get the same error. To download it, just look at my signature :D.

Best wishes,
Michael

---

### Post by MichaelZ on 2006-03-11
[quote=captaincrisis]After several hours of messing around I got Code::Blocks compiled and installed (without errors) but now I just get:

"Error with displaying error for dialog of class cannot_load_entry"

when I try to run it.  <sigh>
[/quote] 
Hello,

Which version of Code::Blocks did you download and install?

Thank you.

Best wishes,
Michael

---

### Post by cstudent on 2006-03-12
I downloaded the Ubuntu .deb from this location:

[http://wiki.codeblocks.org/index.php?title=Compiled_packages_of_Code::Blocks](http://wiki.codeblocks.org/index.php?title=Compiled_packages_of_Code::Blocks)

And commenting out the Encoding=UTF-8 line in the desktop file was the only way it would open from the applications menu. If left uncommented Code::Blocks would give the error "Error with displaying error for dialog of class cannot_load_entry".

---

### Post by MichaelZ on 2006-03-12
[quote=cstudent]I downloaded the Ubuntu .deb from this location:

[http://wiki.codeblocks.org/index.php?title=Compiled_packages_of_Code::Blocks]("http://wiki.codeblocks.org/index.php?title=Compiled_packages_of_Code::Blocks")

And commenting out the Encoding=UTF-8 line in the desktop file was the only way it would open from the applications menu. If left uncommented Code::Blocks would give the error "Error with displaying error for dialog of class cannot_load_entry".[/quote] 
Thank you very much for your reply. But you download Code::Blocks package for version RC2 or SVN?

I am not sure, but may be there is a conflict between unicode and ansi. This why it works when you comment out the Encoding=UTF-8 line.

Best wishes,
Michael

---

### Post by cstudent on 2006-03-12
I downloaded RC2

---

### Post by MichaelZ on 2006-03-12
[quote=cstudent]I downloaded RC2[/quote] 
Hello,

I think that this is the problem. RC2 is ansi and probably there is some conflict with unicode. You should install a SVN build from the website you posted or you can try a .deb package that I am providing for Code::Blocks (look at my signature). In 10 minutes or less, I should have uploaded the .deb package of rev2178 (latest available).

Best wishes,
Michael

---

### Post by cstudent on 2006-03-12
I just installed the svn version 2159 from the link in your sig. It works fine with the Encoding=UTF-8 line in the desktop file. Maybe it was in the way the person configured the RC2 deb?

---

### Post by cstudent on 2006-03-12
[QUOTE=MichaelZ]
In 10 minutes or less, I should have uploaded the .deb package of rev2178 (latest available).

Best wishes,
Michael[/QUOTE]

lol. I guess I'll wait a few minutes and go get that version. :) 

Nice work btw, thanks for sharing.

---

### Post by MichaelZ on 2006-03-12
[quote=cstudent]I just installed the svn version 2159 from the link in your sig. It works fine with the Encoding=UTF-8 line in the desktop file. Maybe it was in the way the person configured the RC2 deb?[/quote] 
May be. IMHO it is or a ansi/linux problem (RC2-->ansi, rev2159-->unicode) or one of the several bugs present in RC2 for Linux.

Now Code::Blocks for Linux works well. Anyway, there is still an annoying bug. You should disable codestat plugin, because it may occasionally crashes Code::Blocks when you try to open the Settings-->Editor menu.

Best wishes,
Michael

---

