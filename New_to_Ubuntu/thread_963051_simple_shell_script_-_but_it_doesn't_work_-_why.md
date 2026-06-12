---
title: "simple shell script - but it doesn't work - why?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by anewguy on 2008-10-29
For some reason I'm having problems with a simple shell script and need some help.  I commented out the rest of the script because the "cd xxxx" doesn't work - I remain in the owner directory.  I have copied/pasted these lines 1 by 1 into the command line in a terminal window and it works fine.  I have another script that does this same thing and works fine.  What dumb thing am I doing wrong?

thanks in advance!
Dave :)


#     build_cvsutil_gtk.sh

#

#  This script builds the gtk version of cvsutil

#

#
#
mkdir xxxx
cp *.c_gtk xxxx/
cp *.c xxxx/
cd xxxx
#cp a_start.c_gtk a_start.c

#cp callout1.c_gtk callout1.c

#cp camera_flash_download.c_gtk camera_flash_download.c

#cp camcorder1_window_exit.c_gtk camcorder1_window_exit.c

#cp camcorder1_window_open.c_gtk camcorder1_window_open.c

#cp camera_flash_download.c_gtk camera_flash_download.c

#cp camera_flash_upload.c_gtk camera_flash_upload.c

#cp camera1_window_exit.c_gtk camera1_window_exit.c

#cp camera1_window_open.c_gtk camera1_window_open.c

#cp do_logmsg.c_gtk do_logmsg.c

#cp do_message.c_gtk do_message.c

#cp do_shutdown_if_needed.c_gtk do_shutdown_if_needed.c

#cp main.c_gtk main.c

#cp hide_special_functions_button.c_gtk hide_special_functions_button.c

#cp show_special_functions_button.c_gtk show_special_functions_button.c

#cp update_progress_message.c_gtk update_progress_message.c

#cp update_progress_message_camera1.c_gtk update_progress_message_camera1.c

#cp show_progress_window.c_gtk show_progress_window.c

#cp yesno.c_gtk yesno.c

#gcc -Wall -g -o ../cvsutil_gtk *.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0` -lusb
#rm *.*
#cd ..
#rmdir temp
#ls cvsutil.gtk

---

### Post by bep on 2008-10-29
My best guess would be the use of relative paths.

like 

cd xxx

instead of

cd ~/xxx

---

### Post by cyfur01 on 2008-10-29
When doing shell scripting, you have to tell it which shell to use with a line at the very top of the file like this:```
#! /bin/bash
```
This way, you would be able to run your script like this (from its local directory):```

./build_cvsutil_gtk.sh

```

Looking more at what you're doing, though, have you considered using a Makefile instead of a shellscript?

---

### Post by PinkFloyd102489 on 2008-10-29
Why are all the lines except for the first few commented?

---

### Post by anewguy on 2008-10-29
bep:  I have another script like this that runs fine with relative paths, but thanks for the suggestion!



cyfur01:  I tried your suggestion but with the same result.  A copy of the terminal window follows in the message. I'd try a make file, but I'm completely in the dark on that - I was used to using the command line in Windows years ago.  Thanks for the suggestion, though!


PinkFloyd102489:  The rest of the script is commented out because (1) it takes a little while to run (2) when the "cd xxxx" doesn't take, it makes a mess to try to clean up.  Thanks for the suggestion, though!

Here's the terminal window capture:

dave@dave-desktop:~/temp/newsrc$ cat build_cvsutil_gtk.sh
#! /bin/bash
#     build_cvsutil_gtk.sh
#
#  This script builds the gtk version of cvsutil
#
#
#
mkdir xxxx
cp *.c_gtk xxxx/
cp *.c xxxx/
cd xxxx
#cp a_start.c_gtk a_start.c
#cp callout1.c_gtk callout1.c
#cp camera_flash_download.c_gtk camera_flash_download.c
#cp camcorder1_window_exit.c_gtk camcorder1_window_exit.c
#cp camcorder1_window_open.c_gtk camcorder1_window_open.c
#cp camera_flash_download.c_gtk camera_flash_download.c
#cp camera_flash_upload.c_gtk camera_flash_upload.c
#cp camera1_window_exit.c_gtk camera1_window_exit.c
#cp camera1_window_open.c_gtk camera1_window_open.c
#cp do_logmsg.c_gtk do_logmsg.c
#cp do_message.c_gtk do_message.c
#cp do_shutdown_if_needed.c_gtk do_shutdown_if_needed.c
#cp main.c_gtk main.c
#cp hide_special_functions_button.c_gtk hide_special_functions_button.c
#cp show_special_functions_button.c_gtk show_special_functions_button.c
#cp update_progress_message.c_gtk update_progress_message.c
#cp update_progress_message_camera1.c_gtk update_progress_message_camera1.c
#cp show_progress_window.c_gtk show_progress_window.c
#cp yesno.c_gtk yesno.c
#gcc -Wall -g -o ../cvsutil_gtk *.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0` -lusb
#rm *.*
#cd ..
#rmdir temp
#ls cvsutil.gtk
dave@dave-desktop:~/temp/newsrc$ ./build_cvsutil_gtk.sh
dave@dave-desktop:~/temp/newsrc$ 



Just for reference, here's the other script I mentioned that works great.  I changed the directory name in the 1st script to help with my debugging:

#

#  build_cvsutil_cl.sh

#

#  This script is used to build the command line

#  version of the cvsutil program.

#

mkdir temp
cp *.c temp/
cp *.h temp/
cp *.c_cl temp/
cd temp
cp a_start.c_cl a_start.c
rm a_start.c_cl
cp do_logmsg.c_cl do_logmsg.c
rm do_logmsg.c_cl
cp do_message.c_cl do_message.c
rm do_message.c_cl
cp do_shutdown_if_needed.c_cl do_shutdown_if_needed.c
rm do_shutdown_if_needed.c_cl
cp hide_special_functions_button.c_cl hide_special_functions_button.c
rm hide_special_functions_button.c_cl
cp main.c_cl main.c
rm main.c_cl
cp show_special_functions_button.c_cl show_special_functions_button.c
rm show_special_functions_button.c_cl
cp update_progress_message.c_cl update_progress_message.c
rm update_progress_message.c_cl
cp yesno.c_cl yesno.c
rm yesno.c_cl
gcc -o ../cvsutil_cl *.c -lusb
rm *.*
cd ..
rmdir temp
ls cvsutil_cl

---

### Post by cyfur01 on 2008-10-29
This works as far as I can tell:```

#! /bin/bash
# build_cvsutil_gtk.sh
#
# This script builds the gtk version of cvsutil
#
#
#
mkdir xxxx
cp *.c_gtk xxxx/
cp *.c xxxx/
cd xxxx
pwd
touch special

```
Make sure that the file has executable permissions (chmod u+x build_cvsutil_gtk.sh).

I ran this on my computer and pwd says that the working directory has been switched to xxxx, and it creates the "special" file in that folder as expected (which is just a blank file).


```

user@host:~/tmp$ ./build_cvsutil_gtk.sh 
/home/user/tmp/xxxx
user@host:~/tmp$ cd xxxx/;ls
special  test.c  test.c_gtk

```

---

### Post by anewguy on 2008-10-29
> **cyfur01 said:**
> This works as far as I can tell:```

#! /bin/bash
# build_cvsutil_gtk.sh
#
# This script builds the gtk version of cvsutil
#
#
#
mkdir xxxx
cp *.c_gtk xxxx/
cp *.c xxxx/
cd xxxx
pwd
touch special

```
Make sure that the file has executable permissions (chmod u+x build_cvsutil_gtk.sh).

I ran this on my computer and pwd says that the working directory has been switched to xxxx, and it creates the "special" file in that folder as expected (which is just a blank file).


The file runs, but never changes directory.  I changed the permissions but it made no difference.  The strange part is this: for testing this I now added an "ls xxxx" prior to the change directory statement.  It lists everything in the xxxx directory, but still refuses to change to it.

As as really dumb question, I have been testing these in a folder off my home folder called "temp" -> while the one works and the other doesn't, could a folder named "temp" have some special meaning and treated differently?

Thanks again!
Dave :)

---

### Post by anewguy on 2008-10-29
Okay, this really baffles me.  I took your test script and ran it once and it worked.  I then manually deleted everything out of the subfolder xxxx and then removed the subfolder.  Then I ran again - I get the same error -> it never changes to the new folder:

dave@dave-desktop:~/temp/newsrc$ cat test.sh
#! /bin/bash
# build_cvsutil_gtk.sh
#
# This script builds the gtk version of cvsutil
#
#
#
mkdir xxxx
cp *.c_gtk xxxx/
cp *.c xxxx/
cd xxxx
pwd
touch special
dave@dave-desktop:~/temp/newsrc$ 
dave@dave-desktop:~/temp/newsrc$ ./test.sh
/home/dave/temp/newsrc/xxxx
dave@dave-desktop:~/temp/newsrc$ 


I'm confused.

Dave :)

---

### Post by shaggy999 on 2008-10-30
Just a wild guess, but try removing the space between #! and /bin/bash... there shouldn't be a space there.

---

### Post by wirelessmonkey on 2008-10-30
Whats happening here is:

Your shell script is opening a new shell (shell 2) from your original shell (shell 1)
Creating the xxxx directory, copying *.c_cl (etc)
Changing to the xxxx directory
Printing the contents of the xxxx directory to your original shell (shell 1)
Creating the file special...
THEN
The new shell that your script opened (shell 2) is closed.
You are returned to your original shell (shell 1)

Your original shell should not have changed working directories. Directories have changed only in the context of shell 2, which exits at the end of the script.

---

### Post by jamesrl on 2008-10-30
In general when debugging bash shell scripts (say called "test.sh") it helps to run from the command prompt:

```

~$> bash -xv test.sh

```
The -v options tell bash when executing the script to print each line as its being read by the script, and  the -x option expands each command (and variables) as its being read.  You can also just add the options: 
```

set -x
set -v
```
to the beginning of your script.

For example with your sample script:
```
#!/bin/bash

mkdir xxxx
cp *.c_gtk xxxx/
cp *.c xxxx/
cd xxxx
pwd

```
[/CODE]
I get:
```

computername:~/new$ bash -xv test.sh 
#!/bin/bash

mkdir xxxx
+ mkdir xxxx
cp *.c_gtk xxxx/
+ cp a.c_gtk b.c_gtk xxxx/
cp *.c xxxx/
+ cp a.c xxxx/
cd xxxx
+ cd xxxx
pwd
+ pwd
/home/username/new/xxxx

```
Note that changing a directory within a bash script, does nothing to what directory you are in after the script ends.

---

### Post by anewguy on 2008-10-31
Been a little busy, but I'll be giving it a try, and I'll let you know how it turns out!

Thanks!
dave :)

---

