---
title: "problem installing tint2"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by RavUn on 2008-07-23
I downloaded and extracted tint-0.6.0.tar.gz and cd to the src directory and type "make" and then I get:
```

config.c:554: error: \u2018server_global\u2019 has no member named \u2018monitor\u2019
config.c:558: error: \u2018Panel\u2019 has no member named \u2018launcher_width\u2019
config.c:561: error: \u2018server_global\u2019 has no member named \u2018monitor\u2019
config.c:569: error: \u2018Panel\u2019 has no member named \u2018task_font_desc\u2019
config.c:573: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c: In function \u2018config_read\u2019:
config.c:584: error: expected \u2018=\u2019, \u2018,\u2019, \u2018;\u2019, \u2018asm\u2019 or \u2018__attribute__\u2019 before \u2018*\u2019 token
config.c:584: error: expected expression before \u2018const\u2019
config.c:586: error: \u2018gint\u2019 undeclared (first use in this function)
config.c:586: error: (Each undeclared identifier is reported only once
config.c:586: error: for each function it appears in.)
config.c:586: error: expected \u2018;\u2019 before \u2018i\u2019
config.c:589: warning: implicit declaration of function \u2018g_build_filename\u2019
config.c:589: warning: implicit declaration of function \u2018g_get_user_config_dir\u2019
config.c:589: warning: assignment makes pointer from integer without a cast
config.c:590: warning: implicit declaration of function \u2018g_file_test\u2019
config.c:590: error: \u2018G_FILE_TEST_EXISTS\u2019 undeclared (first use in this function)
config.c:593: error: \u2018system_dirs\u2019 undeclared (first use in this function)
config.c:593: warning: implicit declaration of function \u2018g_get_system_config_dirs\u2019
config.c:594: error: \u2018i\u2019 undeclared (first use in this function)
config.c:595: warning: assignment makes pointer from integer without a cast
config.c:604: warning: assignment makes pointer from integer without a cast
config.c:605: error: \u2018G_FILE_TEST_IS_DIR\u2019 undeclared (first use in this function)
config.c:605: warning: implicit declaration of function \u2018g_mkdir\u2019
config.c:616: warning: control reaches end of non-void function
config.c: In function \u2018save_config\u2019:
config.c:643: error: \u2018Panel\u2019 has no member named \u2018task_back\u2019
config.c:644: error: \u2018Panel\u2019 has no member named \u2018task_active_back\u2019
config.c:646: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:646: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:647: error: \u2018Panel\u2019 has no member named \u2018task_active_border\u2019
config.c:647: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:653: warning: assignment makes pointer from integer without a cast
config.c:694: error: \u2018Panel\u2019 has no member named \u2018task_font\u2019
config.c:694: error: \u2018Panel\u2019 has no member named \u2018task_font\u2019
config.c:694: error: \u2018Panel\u2019 has no member named \u2018task_font\u2019
config.c:694: error: \u2018Panel\u2019 has no member named \u2018task_font\u2019
config.c:695: error: \u2018Panel\u2019 has no member named \u2018task_font_active\u2019
config.c:695: error: \u2018Panel\u2019 has no member named \u2018task_font_active\u2019
config.c:695: error: \u2018Panel\u2019 has no member named \u2018task_font_active\u2019
config.c:695: error: \u2018Panel\u2019 has no member named \u2018task_font_active\u2019
config.c:700: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:701: error: \u2018Panel\u2019 has no member named \u2018task_back\u2019
config.c:701: error: \u2018Panel\u2019 has no member named \u2018task_back\u2019
config.c:701: error: \u2018Panel\u2019 has no member named \u2018task_back\u2019
config.c:701: error: \u2018Panel\u2019 has no member named \u2018task_back\u2019
config.c:702: error: \u2018Panel\u2019 has no member named \u2018task_active_back\u2019
config.c:702: error: \u2018Panel\u2019 has no member named \u2018task_active_back\u2019
config.c:702: error: \u2018Panel\u2019 has no member named \u2018task_active_back\u2019
config.c:702: error: \u2018Panel\u2019 has no member named \u2018task_active_back\u2019
config.c:703: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:704: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:704: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:704: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:704: error: \u2018Panel\u2019 has no member named \u2018task_border\u2019
config.c:705: error: \u2018Panel\u2019 has no member named \u2018task_active_border\u2019
config.c:705: error: \u2018Panel\u2019 has no member named \u2018task_active_border\u2019
config.c:705: error: \u2018Panel\u2019 has no member named \u2018task_active_border\u2019
config.c:705: error: \u2018Panel\u2019 has no member named \u2018task_active_border\u2019
config.c:719: error: \u2018Panel\u2019 has no member named \u2018mouse_middle\u2019
config.c:720: error: \u2018Panel\u2019 has no member named \u2018mouse_middle\u2019
config.c:721: error: \u2018Panel\u2019 has no member named \u2018mouse_middle\u2019
config.c:722: error: \u2018Panel\u2019 has no member named \u2018mouse_middle\u2019
config.c:723: error: \u2018Panel\u2019 has no member named \u2018mouse_middle\u2019
config.c:726: error: \u2018Panel\u2019 has no member named \u2018mouse_right\u2019
config.c:727: error: \u2018Panel\u2019 has no member named \u2018mouse_right\u2019
config.c:728: error: \u2018Panel\u2019 has no member named \u2018mouse_right\u2019
config.c:729: error: \u2018Panel\u2019 has no member named \u2018mouse_right\u2019
config.c:730: error: \u2018Panel\u2019 has no member named \u2018mouse_right\u2019
config.c:733: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_up\u2019
config.c:734: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_up\u2019
config.c:735: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_up\u2019
config.c:736: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_up\u2019
config.c:737: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_up\u2019
config.c:740: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_down\u2019
config.c:741: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_down\u2019
config.c:742: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_down\u2019
config.c:743: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_down\u2019
config.c:744: error: \u2018Panel\u2019 has no member named \u2018mouse_scroll_down\u2019

```

I get messages like that for several lines and I cannot read what the very beginning says.  The readme says tint2 is dependent on cairo, pango, glib, imlib2, and xinerama but I don't know how to find these files.  I checked synaptic and various files show when searching those but I don't know which to install.  How can I install those or what am I missing?

---

### Post by Heinzelotto on 2008-07-23
libraries always use the prefix "lib", so the names should be libpango*, libglib*, libimlib*, libcairo* (where * denotes a suffix such as "-0", you'll see if you search in the package-manager). xinerama though is no library, but a program itself, so there is no prefix

---

### Post by RavUn on 2008-07-23
hmm, as far as I can tell, I have all of those libraries installed.  I don't know why it's not allowing me to install it.  Is there a way I can see the errors at the beginning of the terminal?  It cuts off the beginning because there are so many messages.  I think I saw it say glib was missing but it was only up for a secon.

---

### Post by Heinzelotto on 2008-07-23
> **RavUn said:**
> hmm, as far as I can tell, I have all of those libraries installed.  I don't know why it's not allowing me to install it.  Is there a way I can see the errors at the beginning of the terminal?  It cuts off the beginning because there are so many messages.  I think I saw it say glib was missing but it was only up for a secon.

just type "make | less" this will let you scroll through the output.

---

### Post by ShdwNova on 2008-10-22
I have the same problem as you RavUn, why the documentation doesn't refer to tint2's dependencies by their actual names...I don't know.
According to this site: 
[HTML]http://urukrama.wordpress.com/2008/07/23/tint2/[/HTML]
the dependencies are: 
libcairo2-dev libpango1.0-dev libglib2.0-dev libimlib2-dev libxinerama-dev 

This gets me a little further. I now get a new error:
```
cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
server.c:31:35: error: X11/extensions/Xrandr.h: No such file or directory
make: *** [tint] Error 1

```
That's where I'm stuck now in compiling from source.
Luckily the website I previously linked has a link to a PPA repo for Hardy & Intrepid that hosts a tint2 .deb that worked great for me: 
[HTML]https://launchpad.net/~k-belding/+archive[/HTML]

---

### Post by njin on 2008-12-10
Hey shdwnova,

i have the same problem. 
[HTML]
cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
server.c:31:35: Fehler: X11/extensions/Xrandr.h: No such file or directory
make: *** [tint] Fehler 1
[/HTML]

I tried to install de package from [HTML]https://launchpad.net/~k-belding/+archive[/HTML] but i just don't know what package i should download and how to install :( pls. can you help me?

greetz.

---

### Post by easybake on 2008-12-11
> **njin said:**
> Hey shdwnova,

i have the same problem. 
[HTML]
cc  -Wall -g `pkg-config --cflags --libs cairo pangocairo x11 xinerama imlib2 glib-2.0` -o tint tint.c server.c window.c task.c launcher.c visual.c config.c
server.c:31:35: Fehler: X11/extensions/Xrandr.h: No such file or directory
make: *** [tint] Fehler 1
[/HTML]

To fix the error you are getting, go into Synaptic search for and install:
libxrandr-dev

You should then be able run make and sudo make install.

---

### Post by njin on 2008-12-11
@easybake
THX! it worked! but now i have another problem ... the install of tint worked, but when i want to start tint by clicking on tint in the %HOME/tint/src folder, nothing happens... what i have to do? :(

---

### Post by silverglade00 on 2008-12-11
You probably just need to make it executable. Right click the tint file and choose Properties. Click on the Permissions tab and make sure the check box called Allow Executing File as a Program is checked.

---

### Post by njin on 2008-12-11
silverglade you saved my day (: it's working! thx a lot!

---

