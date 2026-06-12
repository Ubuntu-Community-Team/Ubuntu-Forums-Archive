---
title: "a newbie question with GTK"
date: 2007-07-14
forum: Programming Talk
---

### Post by jixuanliu on 2007-07-14
hello i'm a absolute beginner in gtk programming, now i have a ubuntu feisty fawn box installed here on my laptop, and i made it clear that i apt-got my libgtk2.0-dev right. i wrote the simplest gtk window in the wide world like this in a file i named ~/test/base.c:

/* the simplest gtk+ window - base.c */

#include <gtk/gtk.h>

int main(int argc, char * argv[])
{
        GtkWidget * window;
        gtk_init(&argc, &argv);
        window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
        gtk_widget_show(window);
        gtk_main();
        return FALSE;
}


and then i "gcc -o base base.c `pkg-config --cflags --libs gtk+-2.0`"-ed it while it complains about some undefined stuffs as follow:

[COLOR="DarkOrange"]/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_visited'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_remove_item'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_description'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_key_file_get_double'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_modified'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_has_item'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_is_private'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_group'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_app_info'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_title'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_groups'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_load_from_file'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_key_file_set_double'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_uris'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_free'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_description'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_applications'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_title'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_application'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_added'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_type_register_static_simple'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_size'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_to_file'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_new'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_is_private'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_move_item'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_mime_type'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_mime_type'[/COLOR]

when i checked the pkg-config, with pkg-config --cflags --libs gtk+-2.0, it gives me these -Is:
[COLOR="DarkOrange"]
-I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  [/COLOR]

when i tried "gcc -o base base.c `pkg-config --libs gtk+-2.0`" alone it gives me 

[COLOR="DarkOrange"]gtk/gtk.h: No such file or directory[/COLOR]

but i DID installed gtk there and now this file is located in /usr/include/gtk-2.0.. i thought it was some default path recognition problem, so i did a "ln -s /usr/include/gtk-2.0 /usr/include/gtk". this changed nothing but nothing.. I felt desperate. :confused:

i'll be grateful for any help! thanks in advance!

---

### Post by geraldm on 2007-07-14
gbookmarkfile.h is in the package glib-2.0.
 
Try adding to the libraries line "`pkg-config --libs glib-2.0``"

After installing a package remember to flush the cache: Either  do 1) reboot OR 
2) (as root run) ldconfig

Gerald

---

### Post by jixuanliu on 2007-07-15
hello Gerald,

thank you for your help. however i didn't fix the problem, maybe it's because i made a mistake somewhere. after adding glib-2.0 into the package config, it still told me the same thing.

[COLOR="Navy"]
$ gcc -o base base.c `pkg-config --cflags --libs gtk+-2.0 glib-2.0`[/COLOR]
[COLOR="DarkOrange"]/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_visited'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_remove_item'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_description'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_key_file_get_double'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_modified'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_has_item'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_is_private'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_group'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_app_info'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_title'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_groups'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_load_from_file'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_key_file_set_double'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_uris'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_free'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_description'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_applications'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_title'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_add_application'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_added'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_type_register_static_simple'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_size'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_to_file'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_new'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_is_private'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_move_item'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_mime_type'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_set_mime_type'[/COLOR]

[COLOR="Navy"]
$ pkg-config --cflags --libs gtk+-2.0 glib-2.0[/COLOR]  gives:
-I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 


if i do it without --cflags option like [COLOR="Navy"]
$ gcc -o base base.c `pkg-config --libs gtk+-2.0 glib-2.0`[/COLOR] it complains about gtk/gtk.h file missing.

[COLOR="DarkOrange"]base.c:3:21: &#38169;&#35823;&#65306; gtk/gtk.h&#65306;No such file or directory
base.c: &#22312;&#20989;&#25968; ‘main’ &#20013;&#65306;
base.c:7: &#38169;&#35823;&#65306; ‘GtkWidget’ &#26410;&#22768;&#26126; (&#22312;&#27492;&#20989;&#25968;&#20869;&#31532;&#19968;&#27425;&#20351;&#29992;)
base.c:7: &#38169;&#35823;&#65306; (&#21363;&#20351;&#22312;&#19968;&#20010;&#20989;&#25968;&#20869;&#22810;&#27425;&#20986;&#29616;&#65292;&#27599;&#20010;&#26410;&#22768;&#26126;&#30340;&#26631;&#35782;&#31526;&#22312;&#20854;
base.c:7: &#38169;&#35823;&#65306; &#25152;&#22312;&#30340;&#20989;&#25968;&#20869;&#21482;&#25253;&#21578;&#19968;&#27425;&#12290;)
base.c:7: &#38169;&#35823;&#65306; ‘window’ &#26410;&#22768;&#26126; (&#22312;&#27492;&#20989;&#25968;&#20869;&#31532;&#19968;&#27425;&#20351;&#29992;)
base.c:9: &#38169;&#35823;&#65306; ‘GTK_WINDOW_TOPLEVEL’ &#26410;&#22768;&#26126; (&#22312;&#27492;&#20989;&#25968;&#20869;&#31532;&#19968;&#27425;&#20351;&#29992;)
base.c:12: &#38169;&#35823;&#65306; ‘FALSE’ &#26410;&#22768;&#26126; (&#22312;&#27492;&#20989;&#25968;&#20869;&#31532;&#19968;&#27425;&#20351;&#29992;)[/COLOR]

do you know why it still isn't happy? 

thanks again! :)

---

### Post by geraldm on 2007-07-15
Check that you do not have two possible libraries, one in /usr/lib, the other in
/usr/local/lib.  Those data names are present here, as I do not get those errors.
Also check for the header file gbookmarkfile.h 

Geald

---

### Post by jixuanliu on 2007-07-15
hello,

now i have these files in my /usr/lib

[COLOR="DarkOrange"]Adobe
ao
apache2
apt
aspell
at-spi
audacious
AuErrorDB
autofs
automatix2
awk
bluetooth
bonobo
bonobo-2.0
bonobo-activation
caca
cli
codecs
compiz
contact-lookup-applet
control-center
crt1.o
crti.o
crtn.o
cups
default.sfx
deskbar-applet
directfb-0.9.25
dpkg
dri
e2initrd_helper
eclipse
eject
emacsen-common
enchant
esound
evolution
evolution-data-server-1.2
evolution-webcal
file-roller
firefox
f-spot
games
gamin
gcc
gcj-4.1
gconv
gcrt1.o
gdesklets
gdm
gdmplay
gedit-2
gettext
gimp
glib-2.0
gnome-applets
gnome-keyring
gnome-media
gnome-netstatus
gnome-panel
gnome-pilot
gnome-screensaver
gnome-spell
gnome-utils
gnome-vfs-2.0
GNU.Gettext.dll
gnupg
groff
grub
gs-esp
gstreamer-0.10
gthumb
gtk-2.0
gtkhtml
gtk-sharp-2.0
gutenprint
hal
hplip
i386-linux-gnu
i486
i486-linux-gnu
i586
i686
ImageMagick-6.2.4
initramfs-tools
ispell
j2se
jack
java
jni
jvm
kconf_update_bin
kde3
klibc
ldscripts
liba52-0.7.4.so
libaa.so.1
libaa.so.1.0.4
libanl.a
libanl.so
libao.so.2
libao.so.2.1.3
libapm.so.1
libapm.so.1.0.0
libapr-1.so.0
libapr-1.so.0.2.7
libaprutil-1.so.0
libaprutil-1.so.0.2.7
libapt-inst-libc6.4-6.so.1.1
libapt-inst-libc6.4-6.so.1.1.0
libapt-pkg-libc6.4-6.so.3.53
libapt-pkg-libc6.4-6.so.3.53.0
libart_lgpl_2.so.2
libart_lgpl_2.so.2.3.17
libartscbackend.la
libartscbackend.so.0
libartscbackend.so.0.0.0
libartsc.so.0
libartsc.so.0.0.0
libartsdsp.so.0
libartsdsp.so.0.0.0
libartsdsp_st.so.0
libartsdsp_st.so.0.0.0
libartsflow_idl.so.1
libartsflow_idl.so.1.0.0
libartsflow.so.1
libartsflow.so.1.0.0
libartsgslplayobject.la
libartsgslplayobject.so.0
libartsgslplayobject.so.0.0.0
libartskde.so.1
libartskde.so.1.2.0
libartswavplayobject.la
libartswavplayobject.so.0
libartswavplayobject.so.0.0.0
libasound.so.2
libasound.so.2.0.0
libaspell.so.15
libaspell.so.15.1.4
libasprintf.a
libasprintf.la
libasprintf.so
libasprintf.so.0
libasprintf.so.0.0.0
libatk-1.0.a
libatk-1.0.la
libatk-1.0.so
libatk-1.0.so.0
libatk-1.0.so.0.1809.1
libaudacious.so.4
libaudacious.so.4.0.0
libaudiofile.so.0
libaudiofile.so.0.0.2
libaudio.so.2
libaudio.so.2.4
libavahi-client.so.3
libavahi-client.so.3.2.2
libavahi-common.so.3
libavahi-common.so.3.4.3
libavahi-core.so.5
libavahi-core.so.5.0.0
libavahi-glib.so.1
libavahi-glib.so.1.0.1
libavahi-qt3.so.1
libavahi-qt3.so.1.0.1
libavc1394.so.0
libavc1394.so.0.3.0
libavcodec.so.0d
libavcodec.so.0d.51.11.0
libavformat.so.0d
libavformat.so.0d.50.5.0
libavutil.so.0d
libavutil.so.0d.49.0.0
libawe.a
libbeagle.so.0
libbeagle.so.0.0.0
libbeecrypt.so.6
libbeecrypt.so.6.4.0
libbfd-2.17.50.so
libbind9.so.0
libbind9.so.0.0.8
libbluetooth.so.2
libbluetooth.so.2.5.0
libbonobo-2.so.0
libbonobo-2.so.0.0.0
libbonobo-activation.so.4
libbonobo-activation.so.4.0.0
libbonoboui-2.so.0
libbonoboui-2.so.0.0.0
libBPM.so.1
libBPM.so.1.0.0
libBrokenLocale.a
libBrokenLocale.so
libbsd-compat.a
libc.a
libcaca.so.0
libcaca.so.0.99.0
libcairo.a
libcairo.la
libcairo.so
libcairo.so.2
libcairo.so.2.11.1
libcamel-1.2.so.10
libcamel-1.2.so.10.0.0
libcamel-provider-1.2.so.10
libcamel-provider-1.2.so.10.0.0
libcdaudio.so.1
libcdaudio.so.1.0.0
libcdda_interface.so.0
libcdda_interface.so.0.10.0
libcdda_paranoia.so.0
libcdda_paranoia.so.0.10.0
libcddb-slave2.so.0
libcddb-slave2.so.0.0.0
libcdio.so.6
libcdio.so.6.0.1
libchewing.so.3
libchewing.so.3.0.0
libchm.so.1
libchm.so.1.0.0
libcidn.so
libc_nonshared.a
libcroco-0.6.so.3
libcroco-0.6.so.3.0.1
libcrypt.a
libcrypto++5.2.so.0
libcrypto++5.2.so.0.0.0
libcrypto.so.0.9.7
libcrypto.so.0.9.8
libcrypt.so
libc.so
libcspi.so.0
libcspi.so.0.10.11
libcucul.so.0
libcucul.so.0.99.0
libcupsimage.so.2
libcups.so.2
libcurl.so.3
libcurl.so.3.0.0
libcvsservice.so.0
libcvsservice.so.0.0.1
libdaemon.so.0
libdaemon.so.0.2.4
libdatrie.so.0
libdatrie.so.0.0.0
libdb-4.2.so
libdb-4.3.so
libdb-4.4.so
libdbus-1.so.3
libdbus-1.so.3.2.0
libdbus-glib-1.so.2
libdbus-glib-1.so.2.1.0
libdc1394_control.so.13
libdc1394_control.so.13.0.0
libDCOP.so.4
libDCOP.so.4.2.0
libdecoration.so.0
libdecoration.so.0.0.0
libdes425.so.3
libdes425.so.3.0
libdesignerintegration.so.0
libdesignerintegration.so.0.0.0
libdirect-0.9.so.25
libdirect-0.9.so.25.0.0
libdirectfb-0.9.so.25
libdirectfb-0.9.so.25.0.0
libdjvulibre.so.15
libdjvulibre.so.15.2.0
libdl.a
libdl.so
libdmx.so.1
libdmx.so.1.0.0
libdns.so.22
libdns.so.22.1.0
libdocumentation_interfaces.so.0
libdocumentation_interfaces.so.0.0.0
libdrm.so.2
libdrm.so.2.3.0
libd.so.0
libd.so.0.0.0
libdvdcss.so.2
libdvdcss.so.2.0.8
libdvdread.so.3
libdvdread.so.3.2.1
libdv.so.4
libdv.so.4.0.3
libebook-1.2.so.9
libebook-1.2.so.9.0.1
libecal-1.2.so.7
libecal-1.2.so.7.0.1
libedata-book-1.2.so.2
libedata-book-1.2.so.2.4.0
libedata-cal-1.2.so.6
libedata-cal-1.2.so.6.0.1
libedataserver-1.2.so.9
libedataserver-1.2.so.9.0.0
libedataserverui-1.2.so.8
libedataserverui-1.2.so.8.0.1
libedit.so.2
libedit.so.2.9
libeel-2.so.2
libeel-2.so.2.18.0
libegroupwise-1.2.so.13
libegroupwise-1.2.so.13.0.0
libelf.so.0
libelf.so.0.8
libelf.so.0.8.6
libenchant.so.1
libenchant.so.1.3.0
libesd.so.0
libesd.so.0.2.36
libespeak.so.1
libespeak.so.1.1.21
libevent-1.0d.so.1
libevent-1.0e.so.1
libevent-1.1a.so.1
libevent-1.1a.so.1.0.2
libevent-1.1.so.1
libevent.so.1
libexchange-storage-1.2.so.3
libexchange-storage-1.2.so.3.0.0
libexif.so.12
libexif.so.12.0.1
libexpat.a
libexpat.la
libexpat.so
libexpat.so.0
libexpat.so.1
libexpat.so.1.0.0
libexslt.so.0
libexslt.so.0.8.13
libfaac.so.0
libfaac.so.0.0.0
libfaad.so.0
libfaad.so.0.0.0
libfame-0.9.so.1
libfame-0.9.so.1.0.0
libfam.so.0
libfam.so.0.0.0
libFLAC.so.7
libFLAC.so.7.0.0
libfluidsynth.so.1
libfluidsynth.so.1.1.1
libfontconfig.a
libfontconfig.so
libfontconfig.so.1
libfontconfig.so.1.2.0
libfontenc.so.1
libfontenc.so.1.0.0
libform.so.5
libform.so.5.5
libformw.so.5
libformw.so.5.5
libfreebl3.chk
libfreebl3.so
libfreebob.so.0
libfreebob.so.0.1.0
libfreetype.a
libfreetype.la
libfreetype.so
libfreetype.so.6
libfreetype.so.6.3.10
libfribidi.so.0
libfribidi.so.0.0.0
libFS.so.6
libFS.so.6.0.0
libfuse.so.2
libfuse.so.2.6.3
libfusion-0.9.so.25
libfusion-0.9.so.25.0.0
libg2c.so.0
libg2c.so.0.0.0
libg.a
libgadu.so.3
libgadu.so.3.5
libgailutil.so.18
libgailutil.so.18.0.1
libgamin-1.so.0
libgamin-1.so.0.1.8
libgccpp.so.1
libgccpp.so.1.0.2
libgcj.so.70
libgcj.so.70.0.0
libgcj-tools.so.70
libgcj-tools.so.70.0.0
libgconf2-4
libgconf-2.so.4
libgconf-2.so.4.1.2
libgcrypt.so.11
libgcrypt.so.11.2.2
libgc.so.1
libgc.so.1.0.2
libgda
libgda-2.so.3
libgda-2.so.3.0.0
libgda-report-2.so.3
libgda-report-2.so.3.0.0
libgdasql.so.3
libgdasql.so.3.0.0
libgdbm_compat.so.3
libgdbm_compat.so.3.0.0
libgdbmi_parser.so.0
libgdbmi_parser.so.0.0.0
libgdbm.so.3
libgdbm.so.3.0.0
libgdict-1.0.a
libgdict-1.0.so.5
libgdict-1.0.so.5.0.11
libgdiplus.so
libgdiplus.so.0
libgdiplus.so.0.0.0
libgdk-1.2.so.0
libgdk-1.2.so.0.9.1
libgdk_pixbuf-2.0.a
libgdk_pixbuf-2.0.la
libgdk_pixbuf-2.0.so
libgdk_pixbuf-2.0.so.0
libgdk_pixbuf-2.0.so.0.1000.11
libgdk_pixbuf_xlib-2.0.a
libgdk_pixbuf_xlib-2.0.la
libgdk_pixbuf_xlib-2.0.so
libgdk_pixbuf_xlib-2.0.so.0
libgdk_pixbuf_xlib-2.0.so.0.1000.11
libgdk-x11-2.0.a
libgdk-x11-2.0.la
libgdk-x11-2.0.so
libgdk-x11-2.0.so.0
libgdk-x11-2.0.so.0.1000.11
libgdl-1.so.0
libgdl-1.so.0.0.0
libgd.so.2
libgd.so.2.0.34
libgeda.so.27
libgeda.so.27.0.0
libgettextlib-0.16.1.so
libgettextlib.la
libgettextlib.so
libgettextpo.a
libgettextpo.la
libgettextpo.so
libgettextpo.so.0
libgettextpo.so.0.3.0
libgettextsrc-0.16.1.so
libgettextsrc.la
libgettextsrc.so
libgif.so.4
libgif.so.4.1.4
libgij.so.70
libgij.so.70.0.0
libgimp-2.0.so.0
libgimp-2.0.so.0.200.13
libgimpbase-2.0.so.0
libgimpbase-2.0.so.0.200.13
libgimpcolor-2.0.so.0
libgimpcolor-2.0.so.0.200.13
libgimpmath-2.0.so.0
libgimpmath-2.0.so.0.200.13
libgimpmodule-2.0.so.0
libgimpmodule-2.0.so.0.200.13
libgimpthumb-2.0.so.0
libgimpthumb-2.0.so.0.200.13
libgimpui-2.0.so.0
libgimpui-2.0.so.0.200.13
libgimpwidgets-2.0.so.0
libgimpwidgets-2.0.so.0.200.13
libgksu
libgksu1.2
libgksu1.2.so.1
libgksu1.2.so.1.0.0
libgksu2.so.0
libgksu2.so.0.0.1
libgksuui1.0.so.1
libgksuui1.0.so.1.0.0
libglade
libglade-2.0.so.0
libglade-2.0.so.0.0.7
libGLEW.so.1.3
libGLEW.so.1.3.4
libglib-1.2.so.0
libglib-1.2.so.0.0.10
libglib-2.0.a
libglib-2.0.la
libglib-2.0.so
libglib-2.0.so.0
libglib-2.0.so.0.1200.11
libglitz.a
libglitz.la
libglitz.so
libglitz.so.1
libglitz.so.1.0.0
libGL.so
libGL.so.1
libGL.so.1.2
libGLU.so.1
libGLU.so.1.3.060502
libglut.so.3
libglut.so.3.8.0
libgmcop.so.1
libgmcop.so.1.0.0
libgmime-2.0.so.2
libgmime-2.0.so.2.2.3
libgmodule-1.2.so.0
libgmodule-1.2.so.0.0.10
libgmodule-2.0.a
libgmodule-2.0.la
libgmodule-2.0.so
libgmodule-2.0.so.0
libgmodule-2.0.so.0.1200.11
libgmp.so.3
libgmp.so.3.4.1
libgnome-2.so.0
libgnome-2.so.0.1800.0
libgnomecanvas-2.so.0
libgnomecanvas-2.so.0.1400.0
libgnomecups-1.0.so.1
libgnomecups-1.0.so.1.0.0
libgnomecupsui-1.0.so.1
libgnomecupsui-1.0.so.1.0.0
libgnome-desktop-2.so.2
libgnome-desktop-2.so.2.3.5
libgnomekbd.so.1
libgnomekbd.so.1.0.0
libgnomekbdui.so.1
libgnomekbdui.so.1.0.0
libgnome-keyring.so.0
libgnome-keyring.so.0.0.1
libgnome-mag.so.2
libgnome-mag.so.2.2.3
libgnome-media-profiles.so.0
libgnome-media-profiles.so.0.0.0
libgnome-menu.so.2
libgnome-menu.so.2.1.9
libgnomeprint
libgnomeprint-2-2.so.0
libgnomeprint-2-2.so.0.1.0
libgnomeprintui-2-2.so.0
libgnomeprintui-2-2.so.0.1.0
libgnomespeech.so.7
libgnomespeech.so.7.0.1
libgnomeui-0
libgnomeui-2.so.0
libgnomeui-2.so.0.1788.4
libgnomevfs-2.so.0
libgnomevfs-2.so.0.1800.1
libgnome-window-settings1
libgnome-window-settings.so.1
libgnome-window-settings.so.1.0.0
libgnutls-extra.so.13
libgnutls-extra.so.13.0.9
libgnutls-openssl.so.13
libgnutls-openssl.so.13.0.9
libgnutls.so.13
libgnutls.so.13.0.9
libgobject-2.0.a
libgobject-2.0.la
libgobject-2.0.so
libgobject-2.0.so.0
libgobject-2.0.so.0.1200.11
libgpg-error.so.0
libgpg-error.so.0.3.0
libgphoto2
libgphoto2_port
libgphoto2_port.so.0
libgphoto2_port.so.0.7.0
libgphoto2.so.2
libgphoto2.so.2.2.0
libgpilotdcm.so.2
libgpilotdcm.so.2.0.2
libgpilotdconduit.so.2
libgpilotdconduit.so.2.0.3
libgpilotd.so.2
libgpilotd.so.2.1.1
libgpm.so.1
libgpm.so.1.19.6
libgpod.so.1
libgpod.so.1.0.0
libgpvm3.so.3
libgpvm3.so.3.4.5
libgs-esp.so.8
libgs-esp.so.8.15
libgsf-1.so.114
libgsf-1.so.114.0.3
libgsm.so.1
libgsm.so.1.0.10
libgssapi_krb5.so.2
libgssapi_krb5.so.2.2
libgssapi.so.2
libgssapi.so.2.0.0
libgstaudio-0.10.so.0
libgstaudio-0.10.so.0.8.0
libgstbase-0.10.so.0
libgstbase-0.10.so.0.11.0
libgstcdda-0.10.so.0
libgstcdda-0.10.so.0.8.0
libgstcheck-0.10.so.0
libgstcheck-0.10.so.0.11.0
libgstcontroller-0.10.so.0
libgstcontroller-0.10.so.0.11.0
libgstdataprotocol-0.10.so.0
libgstdataprotocol-0.10.so.0.11.0
libgstinterfaces-0.10.so.0
libgstinterfaces-0.10.so.0.8.0
libgstnet-0.10.so.0
libgstnet-0.10.so.0.11.0
libgstnetbuffer-0.10.so.0
libgstnetbuffer-0.10.so.0.8.0
libgstpbutils-0.10.so.0
libgstpbutils-0.10.so.0.8.0
libgstreamer-0.10.so.0
libgstreamer-0.10.so.0.11.0
libgstriff-0.10.so.0
libgstriff-0.10.so.0.8.0
libgstroke.so.0
libgstroke.so.0.0.5
libgstrtp-0.10.so.0
libgstrtp-0.10.so.0.8.0
libgsttag-0.10.so.0
libgsttag-0.10.so.0.8.0
libgstvideo-0.10.so.0
libgstvideo-0.10.so.0.8.0
libgthread-1.2.so.0
libgthread-1.2.so.0.0.10
libgthread-2.0.a
libgthread-2.0.la
libgthread-2.0.so
libgthread-2.0.so.0
libgthread-2.0.so.0.1200.11
libgthumb.so
libgtk-1.2.so.0
libgtk-1.2.so.0.9.1
libgtkembedmoz.so.0d
libgtkhtml-2.so.0
libgtkhtml-2.so.0.0.0
libgtkhtml-3.14.so.19
libgtkhtml-3.14.so.19.0.0
libgtksourceview-1.0.so.0
libgtksourceview-1.0.so.0.0.0
libgtkspell.so.0
libgtkspell.so.0.0.0
libgtk-x11-2.0.a
libgtk-x11-2.0.la
libgtk-x11-2.0.so
libgtk-x11-2.0.so.0
libgtk-x11-2.0.so.0.1000.11
libgtop-2.0.so.7
libgtop-2.0.so.7.0.0
libgtrtst.so.1
libgtrtst.so.1.0.0
libgucharmap.so.6
libgucharmap.so.6.0.1
libguile-ltdl.so.1
libguile-ltdl.so.1.0.1
libguilereadline-v-12.la
libguilereadline-v-12.so.12
libguilereadline-v-12.so.12.3.1
libguilereadline-v-17.la
libguilereadline-v-17.so.17
libguilereadline-v-17.so.17.0.1
libguile.so.12
libguile.so.12.3.1
libguile.so.17
libguile.so.17.0.1
libguile-srfi-srfi-13-14-v-1.la
libguile-srfi-srfi-13-14-v-1.so.1
libguile-srfi-srfi-13-14-v-1.so.1.0.1
libguile-srfi-srfi-13-14-v-3.la
libguile-srfi-srfi-13-14-v-3.so.3
libguile-srfi-srfi-13-14-v-3.so.3.0.1
libguile-srfi-srfi-1-v-3.la
libguile-srfi-srfi-1-v-3.so.3
libguile-srfi-srfi-1-v-3.so.3.0.1
libguile-srfi-srfi-4-v-1.la
libguile-srfi-srfi-4-v-1.so.1
libguile-srfi-srfi-4-v-1.so.1.0.1
libguile-srfi-srfi-4-v-3.la
libguile-srfi-srfi-4-v-3.so.3
libguile-srfi-srfi-4-v-3.so.3.0.1
libguile-srfi-srfi-60-v-2.la
libguile-srfi-srfi-60-v-2.so.2
libguile-srfi-srfi-60-v-2.so.2.0.1
libgutenprint.so.2
libgutenprint.so.2.0.0
libgutenprintui2.so.1
libgutenprintui2.so.1.0.0
libgweather.so.0
libgweather.so.0.0.0
libHalf.so.2
libHalf.so.2.0.2
libhal.so.1
libhal.so.1.0.0
libhal-storage.so.1
libhal-storage.so.1.0.0
libhunspell-1.1.so.0
libhunspell-1.1.so.0.0.0
libI810XvMC.so
libI810XvMC.so.1
libI810XvMC.so.1.0.0
libICE.a
libICE.so
libICE.so.6
libICE.so.6.3.0
libicudata.so.36
libicudata.so.36.0
libicui18n.so.36
libicui18n.so.36.0
libicuio.so.36
libicuio.so.36.0
libicule.so.36
libicule.so.36.0
libiculx.so.36
libiculx.so.36.0
libicutu.so.36
libicutu.so.36.0
libicuuc.so.36
libicuuc.so.36.0
libid3tag.so.0
libid3tag.so.0.3.0
libIDL-2.so.0
libIDL-2.so.0.0.0
libidn.la
libidn.so.11
libidn.so.11.5.19
libiec61883.so.0
libiec61883.so.0.1.0
libieee1284.so.3
libieee1284.so.3.2.2
libieee.a
libIex.so.2
libIex.so.2.0.2
libIlmImf.so.2
libIlmImf.so.2.0.2
libImath.so.2
libImath.so.2.0.2
libImlib.so.11
libImlib.so.11.0.0
libImplicit.a
libImplicit.la
libisccc.so.0
libisccc.so.0.2.2
libisccfg.so.1
libisccfg.so.1.0.6
libisc.so.11
libisc.so.11.1.1
libiso9660.so.4
libiso9660.so.4.0.1
libjack0.100.0
libjack-0.100.0.so.0
libjack-0.100.0.so.0.0.23
libjasper-1.701.so.1
libjasper-1.701.so.1.0.0
libjpeg.so.62
libjpeg.so.62.0.0
libk5crypto.so.3
libk5crypto.so.3.0
libkabc_dir.so.1
libkabc_dir.so.1.0.0
libkabc_file.so.1
libkabc_file.so.1.0.0
libkabc_ldapkio.so.1
libkabc_ldapkio.so.1.0.0
libkabc_net.so.1
libkabc_net.so.1.0.0
libkabc.so.1
libkabc.so.1.2.0
libkatepartinterfaces.so.0
libkatepartinterfaces.so.0.0.0
libkdecore.so.4
libkdecore.so.4.2.0
libkdefakes.so.4
libkdefakes.so.4.2.0
libkdefx.so.4
libkdefx.so.4.2.0
libkdeinit_cupsdconf.so
libkdeinit_cvsaskpass.so
libkdeinit_cvsservice.so
libkdeinit_dcopserver.so
libkdeinit_kaddprinterwizard.so
libkdeinit_kbuildsycoca.so
libkdeinit_kcminit.so
libkdeinit_kcminit_startup.la
libkdeinit_kcminit_startup.so
libkdeinit_kcmshell.so
libkdeinit_kconf_update.so
libkdeinit_kcookiejar.so
libkdeinit_kded.so
libkdeinit_khelpcenter.so
libkdeinit_khotkeys.so
libkdeinit_kio_http_cache_cleaner.so
libkdeinit_kio_uiserver.so
libkdeinit_klauncher.so
libkdeinit_kxkb.so
libkdeprint_management.so.4
libkdeprint_management.so.4.2.0
libkdeprint.so.4
libkdeprint.so.4.2.0
libkdesasl.so.1
libkdesasl.so.1.2.0
libkdesu.so.4
libkdesu.so.4.2.0
libkdeui.so.4
libkdeui.so.4.2.0
libkdevbuildbase.so.0
libkdevbuildbase.so.0.0.0
libkdevbuildtoolswidgets.so.0
libkdevbuildtoolswidgets.so.0.0.0
libkdevcatalog.so.0
libkdevcatalog.so.0.0.0
libkdevcppparser.so.0
libkdevcppparser.so.0.0.0
libkdevelop.so.1
libkdevelop.so.1.0.0
libkdevextras.so.0
libkdevextras.so.0.0.0
libkdevpropertyeditor.so.0
libkdevpropertyeditor.so.0.0.0
libkdevqmakeparser.so.0
libkdevqmakeparser.so.0.0.0
libkdevshell.so.0
libkdevshell.so.0.0.0
libkdevwidgets.so.0
libkdevwidgets.so.0.0.0
libkdnssd.so.1
libkdnssd.so.1.0.0
libkhotkeys_shared.so.1
libkhotkeys_shared.so.1.0.0
libkhtml.so.4
libkhtml.so.4.2.0
libkimproxy.so.0
libkimproxy.so.0.0.0
libkinterfacedesigner.so.0
libkinterfacedesigner.so.0.0.0
libkio.so.4
libkio.so.4.2.0
libkjava.so.1
libkjava.so.1.0.0
libkjs.so.1
libkjs.so.1.2.0
libkmdi2.so.1
libkmdi2.so.1.0.0
libkmdi.so.1
libkmdi.so.1.0.0
libkmedia2_idl.so.1
libkmedia2_idl.so.1.0.0
libkmedia2.la
libkmedia2.so.1
libkmedia2.so.1.0.0
libkmediaplayer.so.0
libkmediaplayer.so.0.0.0
libkmid.so.0
libkmid.so.0.0.95
libknewstuff.so.1
libknewstuff.so.1.0.0
libkntlm.so.0
libkntlm.so.0.0.0
libkparts.so.2
libkparts.so.2.1.0
libkpathsea.so.4
libkpathsea.so.4.0.0
libkrb4.so.2
libkrb4.so.2.0
libkrb5.so.3
libkrb5.so.3.2
libkrb5support.so.0
libkrb5support.so.0.0
libkresources.so.1
libkresources.so.1.2.0
libkscreensaver.so.4
libkscreensaver.so.4.2.0
libkscript.so.0
libkscript.so.0.0.0
libkspell2.so.1
libkspell2.so.1.0.0
libkspell.so.4
libkspell.so.4.2.0
libktexteditor.so.0
libktexteditor.so.0.0.0
libkunittest.so.1
libkunittest.so.1.0.0
libkutils.so.1
libkutils.so.1.2.0
libkwalletbackend.so.1
libkwalletbackend.so.1.0.0
libkwalletclient.so.1
libkwalletclient.so.1.0.1
libladcca.so.2
libladcca.so.2.0.0
liblang_debugger.so.0
liblang_debugger.so.0.0.0
liblang_interfaces.so.0
liblang_interfaces.so.0.0.0
liblaunchpad-integration.so.0
liblaunchpad-integration.so.0.0.0
liblavfile-1.8.so.0
liblavfile-1.8.so.0.0.0
liblavjpeg-1.8.so.0
liblavjpeg-1.8.so.0.0.0
liblavplay-1.8.so.0
liblavplay-1.8.so.0.0.0
liblavrec-1.8.so.0
liblavrec-1.8.so.0.0.0
liblber.so.2
liblber.so.2.0.130
liblcms.so.1
liblcms.so.1.0.15
libldap_r.so.2
libldap_r.so.2.0.130
libldap.so.2
libldap.so.2.0.130
liblirc_client.la
liblirc_client.so.0
liblirc_client.so.0.2.0
libloginhelper.so.0
libloginhelper.so.0.0.0
liblo.so.0
liblo.so.0.6.0
liblpint-bonobo.so.0
liblpint-bonobo.so.0.0.0
liblrdf.so.0
liblrdf.so.0.0.0
libltdl.so.3
libltdl.so.3.1.4
liblua50.so.5
liblua50.so.5.0
liblualib50.so.5
liblualib50.so.5.0
liblwres.so.9
liblwres.so.9.1.5
liblzo.so.1
liblzo.so.1.0.0
libm.a
libmad.so.0
libmad.so.0.2.1
libMagick.so.9
libMagick.so.9.0.0
libmagic.so.1
libmagic.so.1.0.0
libmcheck.a
libmcop_mt.so.1
libmcop_mt.so.1.0.0
libmcop.so.1
libmcop.so.1.0.0
libmdb.so.1
libmdb.so.1.0.0
libmdbsql.so.1
libmdbsql.so.1.0.0
libmenu.so.5
libmenu.so.5.5
libmenuw.so.5
libmenuw.so.5.5
libmetacity-private.so.0
libmetacity-private.so.0.0.0
libmjpegutils-1.8.so.0
libmjpegutils-1.8.so.0.0.0
libmms.so.0
libmms.so.0.0.2
libmng.so.1
libmng.so.1.1.0.9
libmodplug.so.0
libmodplug.so.0.0.0
libMonoPosixHelper.so
libmono-profiler-aot.so.0
libmono-profiler-aot.so.0.0.0
libmono-profiler-cov.so.0
libmono-profiler-cov.so.0.0.0
libmono.so.0
libmono.so.0.0.0
libMonoSupportW.so
libmozjs.so.0d
libmp3lame.so.0
libmp3lame.so.0.0.0
libmp4ff.so.0
libmp4ff.so.0.0.0
libmp4v2.so.0
libmp4v2.so.0.0.0
libmpcdec.so.3
libmpcdec.so.3.1.1
libmpeg2convert.so.0
libmpeg2convert.so.0.0.0
libmpeg2encpp-1.8.so.0
libmpeg2encpp-1.8.so.0.0.0
libmpeg2.so.0
libmpeg2.so.0.0.0
libmplex2-1.8.so.0
libmplex2-1.8.so.0.0.0
libmp.so.3
libmp.so.3.1.10
libm.so
libmusicbrainz.so.4
libmusicbrainz.so.4.0.2
libmysqlclient_r.so.15
libmysqlclient_r.so.15.0.0
libmysqlclient.so.15
libmysqlclient.so.15.0.0
libnautilus-burn.so.4
libnautilus-burn.so.4.0.0
libnautilus-extension.so.1
libnautilus-extension.so.1.1.0
libneon.so.25
libneon.so.25.0.5
libnetpbm.so.10
libnetpbm.so.10.0
libnetsnmpagent.so.9
libnetsnmpagent.so.9.0.1
libnetsnmphelpers.so.9
libnetsnmphelpers.so.9.0.1
libnetsnmpmibs.so.9
libnetsnmpmibs.so.9.0.1
libnetsnmp.so.9
libnetsnmp.so.9.0.1
libnetsnmptrapd.so.9
libnetsnmptrapd.so.9.0.1
libnewt.so.0.52
libnewt.so.0.52.2
libnfsidmap.so.0
libnfsidmap.so.0.2.0
libnl.so.1
libnl.so.1.0-pre6
libnm_glib.so.0
libnm_glib.so.0.0.0
libnm-util.so.0
libnm-util.so.0.0.0
libnotify.so.1
libnotify.so.1.1.1
libnsl.a
libnsl.so
libnspr4.so
libnspr4.so.0d
libnss3.so
libnss3.so.0d
libnss_compat.so
libnss_dns.so
libnss_files.so
libnss_hesiod.so
libnss_nisplus.so
libnss_nis.so
libntfs-3g.so.0
libntfs-3g.so.0.0.0
libodbccr.so.1
libodbccr.so.1.0.0
libodbcinst.so.1
libodbcinst.so.1.0.0
libodbc.so.1
libodbc.so.1.0.0
libOggFLAC.so.3
libOggFLAC.so.3.0.0
libogg.so.0
libogg.so.0.5.3
liboil-0.3.so.0
liboil-0.3.so.0.1.0
liboobs-1.so.3
liboobs-1.so.3.0.0
libopal.so.2.1.3
libopal.so.2.2
libopal.so.2.2.0
libopal.so.2.2.1
libopal.so.2.2.2
libopal.so.2.2.3
libopcodes-2.17.50.so
libopenal.so.0
libopenal.so.0.0.0
libopencdk.so.8
libopencdk.so.8.0.5
libORBit-2.so.0
libORBit-2.so.0.1.0
libORBitCosNaming-2.so.0
libORBitCosNaming-2.so.0.1.0
libORBit-imodule-2.so.0
libORBit-imodule-2.so.0.0.0
libpanel-applet-2.so.0
libpanel-applet-2.so.0.2.17
libpanel.so.5
libpanel.so.5.5
libpanelw.so.5
libpanelw.so.5.5
libpango-1.0.a
libpango-1.0.la
libpango-1.0.so
libpango-1.0.so.0
libpango-1.0.so.0.1600.2
libpangocairo-1.0.a
libpangocairo-1.0.la
libpangocairo-1.0.so
libpangocairo-1.0.so.0
libpangocairo-1.0.so.0.1600.2
libpangoft2-1.0.a
libpangoft2-1.0.la
libpangoft2-1.0.so
libpangoft2-1.0.so.0
libpangoft2-1.0.so.0.1600.2
libpangox-1.0.a
libpangox-1.0.la
libpangox-1.0.so
libpangox-1.0.so.0
libpangox-1.0.so.0.1600.2
libpangoxft-1.0.a
libpangoxft-1.0.la
libpangoxft-1.0.so
libpangoxft-1.0.so.0
libpangoxft-1.0.so.0.1600.2
libpaper.so.1
libpaper.so.1.1.2
libpcap.so.0.8
libpcap.so.0.9.5
libpci.so.2
libpcreposix.so.3
libpcreposix.so.3.12.0
libpcre.so.3
libpcre.so.3.12.0
libperl.so.5.8
libperl.so.5.8.8
libpisock.so.9
libpisock.so.9.0.1
libpisync.so.0
libpisync.so.0.0.2
libplc4.so
libplc4.so.0d
libplds4.so
libplds4.so.0d
libpng12.a
libpng12.so
libpng12.so.0
libpng12.so.0.15.0
libpng.a
libpng.so
libpoppler-glib.so.1
libpoppler-glib.so.1.0.0
libpoppler.so.1
libpoppler.so.1.0.0
libportaudio.so.0
libportaudio.so.0.0.18
libpostproc.so.0d
libpostproc.so.0d.51.11.0
libpq.so.5
libpq.so.5.0
libprofileengine.so.0
libprofileengine.so.0.0.0
libpspell.so.15
libpspell.so.15.1.4
libpthread.a
libpthread_nonshared.a
libpthread.so
libpt.so.1.10
libpt.so.1.10.1
libpt.so.1.10.2
libpt.so.1.10.3
libpt.so.1.9.3
libpulse-simple.so.0
libpulse-simple.so.0.0.0
libpulse.so.0
libpulse.so.0.1.0
libpvm3.so.3
libpvm3.so.3.4.5
libpython2.4.so.1
libpython2.4.so.1.0
libpython2.5.so.1
libpython2.5.so.1.0
libqthreads.so.12
libqthreads.so.12.3.1
libqtmcop.so.1
libqtmcop.so.1.0.0
libqt-mt.so.3
libqt-mt.so.3.3
libqt-mt.so.3.3.7
libquicktime
libquicktime1394.so.0
libquicktime1394.so.0.0.0
libquicktime.so.0
libquicktime.so.0.0.0
libqui.so.1
libqui.so.1.0
libqui.so.1.0.0
libraptor.so.1
libraptor.so.1.1.0
libraw1394.so.8
libraw1394.so.8.1.1
librecode.so.0
librecode.so.0.0.0
libresolv.a
libresolv.so
librhythmbox-core.a
librhythmbox-core.la
librhythmbox-core.so
librhythmbox-core.so.0
librhythmbox-core.so.0.0.0
librom1394.so.0
librom1394.so.0.3.0
librpcsecgss.so.3
librpcsecgss.so.3.0.0
librpcsvc.a
librpm-4.4.so
librpmbuild-4.4.so
librpmbuild.so
librpmdb-4.4.so
librpmdb.so
librpmio-4.4.so
librpmio.so
librpm.so
librsMath.a
librsMath.la
librsvg-2.so.2
librsvg-2.so.2.16.0
librt.a
librte.so.1
librte.so.1.0.1
librt.so
libsane.la
libsane.so.1
libsane.so.1.0.18
libsasl2.so.2
libsasl2.so.2.0.22
libscim-1.0.so.8
libscim-1.0.so.8.1.0
libscim-gtkutils-1.0.so.8
libscim-gtkutils-1.0.so.8.1.0
libscim-x11utils-1.0.so.8
libscim-x11utils-1.0.so.8.1.0
libscrollkeeper.so.0
libscrollkeeper.so.0.0.0
libSDL-1.2.so.0
libSDL-1.2.so.0.11.0
libSDL_image-1.2.so.0
libSDL_image-1.2.so.0.1.4
libSDL_mixer-1.2.so.0
libSDL_mixer-1.2.so.0.2.4
libSDL_net-1.2.so.0
libSDL_net-1.2.so.0.0.5
libsensors.so.3
libsensors.so.3.1.1
libsexy.so.2
libsexy.so.2.0.4
libshout.so.3
libshout.so.3.2.0
libsidplay.so.1
libsidplay.so.1.0.3
libsigc-2.0.so.0
libsigc-2.0.so.0.0.0
libslab.so.0
libslab.so.0.0.0
libslp.so.1
libslp.so.1.0.1
libSM.a
libsmbclient.so.0
libsmbclient.so.0.1
libsmime3.so
libsmime3.so.0d
libsmpeg-0.4.so.0
libsmpeg-0.4.so.0.1.4
libSM.so
libSM.so.6
libSM.so.6.0.0
libsnackstub2.2.a
libsndfile.so.1
libsndfile.so.1.0.16
libsnmp.so.9
libsnmp.so.9.0.1
libsoftokn3.0d.chk
libsoftokn3.chk
libsoftokn3.so
libsoftokn3.so.0d
libsoundserver_idl.so.1
libsoundserver_idl.so.1.0.0
libSoundTouch.so.1
libSoundTouch.so.1.0.0
libsoup-2.2.so.8
libsoup-2.2.so.8.5.0
libspeex.so.1
libspeex.so.1.2.0
libspi.so.0
libspi.so.0.10.11
libsqlite3.so.0
libsqlite3.so.0.8.6
libssl3.so
libssl3.so.0d
libssl.so.0.9.7
libssl.so.0.9.8
libstartup-notification-1.a
libstartup-notification-1.so
libstartup-notification-1.so.0
libstartup-notification-1.so.0.0.0
libstdc++.so.5
libstdc++.so.5.0.7
libstdc++.so.6
libstdc++.so.6.0.8
libstlport.so.5.1
libstlport.so.5.1.0
libstroke.so.0
libstroke.so.0.0.5
libswfdec-0.3.so.0
libswfdec-0.3.so.0.0.0
libtag_c.so.0
libtag_c.so.0.0.0
libtag.so.1
libtag.so.1.4.0
libtasn1.so.3
libtasn1.so.3.0.6
libtcl8.4.so.0
libtcl8.5.so
libthai.so.0
libthai.so.0.1.1
libtheora.so.0
libtheora.so.0.2.0
libthread_db.so
libtiff.so.4
libtiff.so.4.2.1
libtk8.4.so.0
libtk8.5.so
libtls1.50.so
libtls.so.0
libtotem-plparser.so.1
libtotem-plparser.so.1.5.7
libulockmgr.so.1
libulockmgr.so.1.0.1
libungif.so.4
libungif.so.4.1.4
libuniconf.so.4.2
libuniquewm-0.9.so.25
libuniquewm-0.9.so.25.0.0
libutil.a
libutil.so
libvcard.so.0
libvcard.so.0.0.0
libvcdinfo.so.0
libvcdinfo.so.0.2.0
libviaXvMCPro.so
libviaXvMCPro.so.1
libviaXvMCPro.so.1.0.0
libviaXvMC.so
libviaXvMC.so.1
libviaXvMC.so.1.0.0
libvisual
libvisual-0.4.so.0
libvisual-0.4.so.0.0.0
libvorbisenc.so.2
libvorbisenc.so.2.0.2
libvorbisfile.so.3
libvorbisfile.so.3.1.1
libvorbis.so.0
libvorbis.so.0.3.1
libvte9
libvte.so.9
libvte.so.9.2.5
libWand.so.9
libWand.so.9.0.0
libwavpack.so.1
libwavpack.so.1.0.0
libwine.so.1
libwine.so.1.0
libwmf-0.2.so.7
libwmf-0.2.so.7.1.0
libwmflite-0.2.so.7
libwmflite-0.2.so.7.0.1
libwnck-1.a
libwnck-1.so
libwnck-1.so.18
libwnck-1.so.18.2.8
libwpd-0.8.so.8
libwpd-0.8.so.8.0.9
libwps-0.1.so.1
libwps-0.1.so.1.0.0
libwps-stream-0.1.so.1
libwps-stream-0.1.so.1.0.0
libwvbase.so.4.2
libwvstreams.so.4.2
libwvutils.so.4.2
libwx_baseu-2.8.so.0
libwx_baseu-2.8.so.0.0.0
libwx_baseu_net-2.8.so.0
libwx_baseu_net-2.8.so.0.0.0
libwx_baseu_xml-2.8.so.0
libwx_baseu_xml-2.8.so.0.0.0
libwx_gtk2u_adv-2.8.so.0
libwx_gtk2u_adv-2.8.so.0.0.0
libwx_gtk2u_aui-2.8.so.0
libwx_gtk2u_aui-2.8.so.0.0.0
libwx_gtk2u_core-2.8.so.0
libwx_gtk2u_core-2.8.so.0.0.0
libwx_gtk2u_fl-2.8.so.0
libwx_gtk2u_fl-2.8.so.0.0.0
libwx_gtk2u_gizmos-2.8.so.0
libwx_gtk2u_gizmos-2.8.so.0.0.0
libwx_gtk2u_gizmos_xrc-2.8.so.0
libwx_gtk2u_gizmos_xrc-2.8.so.0.0.0
libwx_gtk2u_gl-2.8.so.0
libwx_gtk2u_gl-2.8.so.0.0.0
libwx_gtk2u_html-2.8.so.0
libwx_gtk2u_html-2.8.so.0.0.0
libwx_gtk2u_media-2.8.so.0
libwx_gtk2u_media-2.8.so.0.0.0
libwx_gtk2u_mmedia-2.8.so.0
libwx_gtk2u_mmedia-2.8.so.0.0.0
libwx_gtk2u_ogl-2.8.so.0
libwx_gtk2u_ogl-2.8.so.0.0.0
libwx_gtk2u_plot-2.8.so.0
libwx_gtk2u_plot-2.8.so.0.0.0
libwx_gtk2u_qa-2.8.so.0
libwx_gtk2u_qa-2.8.so.0.0.0
libwx_gtk2u_richtext-2.8.so.0
libwx_gtk2u_richtext-2.8.so.0.0.0
libwx_gtk2u_stc-2.8.so.0
libwx_gtk2u_stc-2.8.so.0.0.0
libwx_gtk2u_svg-2.8.so.0
libwx_gtk2u_svg-2.8.so.0.0.0
libwx_gtk2u_xrc-2.8.so.0
libwx_gtk2u_xrc-2.8.so.0.0.0
libX11.a
libx11globalcomm.la
libx11globalcomm.so.1
libx11globalcomm.so.1.0.0
libX11.so
libX11.so.6
libX11.so.6.2.0
libXau.a
libXau.so
libXau.so.6
libXau.so.6.0.0
libXaw3d.so.6
libXaw3d.so.6.1
libXaw7.so.7
libXaw7.so.7.0.0
libXaw.so.7
libXcomposite.so.1
libXcomposite.so.1.0.0
libXcursor.a
libXcursor.so
libXcursor.so.1
libXcursor.so.1.0.2
libXdamage.so.1
libXdamage.so.1.0.0
libXdmcp.a
libXdmcp.so
libXdmcp.so.6
libXdmcp.so.6.0.0
libXevie.so.1
libXevie.so.1.0.0
libXext.a
libXext.so
libXext.so.6
libXext.so.6.4.0
libXfixes.a
libXfixes.so
libXfixes.so.3
libXfixes.so.3.1.0
libXfont.so.1
libXfont.so.1.4.1
libXft.a
libXft.so
libXft.so.2
libXft.so.2.1.2
libXi.a
libXinerama.a
libXinerama.so
libXinerama.so.1
libXinerama.so.1.0.0
libxine.so.1
libxine.so.1.16.0
libXi.so
libXi.so.6
libXi.so.6.0.0
libxkbfile.so.1
libxkbfile.so.1.0.2
libxklavier.so.11
libxklavier.so.11.0.0
libxml2.so.2
libxml2.so.2.6.27
libXmu.so.6
libXmu.so.6.2.0
libXmuu.so.1
libXmuu.so.1.0.0
libxpcomglue.so.0d
libxpcom.so.0d
libxplc.so.0.3.13
libxplc.so.0.3.13-unstable
libXpm.so.4
libXpm.so.4.11.0
libXp.so.6
libXp.so.6.2.0
libXrandr.a
libXrandr.so
libXrandr.so.2
libXrandr.so.2.1.0
libXrender.a
libXrender.so
libXrender.so.1
libXrender.so.1.3.0
libXRes.a
libXRes.so
libXRes.so.1
libXRes.so.1.0.0
libxslt.so.1
libxslt.so.1.1.20
libXss.so.1
libXss.so.1.0.0
libXTrap.so.6
libXTrap.so.6.4.0
libXt.so.6
libXt.so.6.0.0
libXtst.so.6
libXtst.so.6.1.0
libxul.so.0d
libxvidcore.so.4
libxvidcore.so.4.1
libXvMC.so.1
libXvMC.so.1.0.0
libXvMCW.so.1
libXvMCW.so.1.0.0
libXv.so.1
libXv.so.1.0.0
libXxf86dga.so.1
libXxf86dga.so.1.0.0
libXxf86misc.so.1
libXxf86misc.so.1.1.0
libXxf86vm.so.1
libXxf86vm.so.1.0.0
libz.a
libz.so
libz.so.1
libz.so.1.2.3
locale
locate
log4net
man-db
mcop
Mcrt1.o
menu
metacity
mime
mono
Mono.Cecil
monodevelop
monodoc
mozilla
mozilla-firefox
mozilla-snapshot
mozilla-thunderbird
nautilus
nautilus-cd-burner
netscape
network-manager
notification-daemon
notification-daemon-1.0
odbc
openoffice
openssh
orbit-2.0
p7zip
pango
pcmcia-cs
pcmciautils
perl
perl5
pkgconfig
pppd
ppr
preloadable_libintl.so
proftpd
pt_chown
pwlib
pygtk
python2.3
python2.4
python2.5
python-support
qt3
realplay
realplay-10.0.8
rhythmbox
rpm
samba
sane
sasl2
scilab-4.0
scim-1.0
Scrt1.o
security
skype
snack2.1
snack2.2
ssl
sudo
tasksel
tc
tcl8.4
tcl8.5
tcllib1.8
tile0.7.8
timidity
tk8.4
tk8.5
tls1.50
tomboy
totem
transcode
tsclient
update-notifier
upstart
usplash
valgrind
vhook
vino
w3m
win32
wine
X11
xcdroast
xchat
xen
xine
xorg
xscreensaver
xulrunner[/COLOR]


and i have these files /usr/local/lib

[COLOR="DarkOrange"]codecs                  libgmodule-2.0.so          libgthread-2.0.so
eclipse                 libgmodule-2.0.so.0        libgthread-2.0.so.0
glib-2.0                libgmodule-2.0.so.0.902.3  libgthread-2.0.so.0.902.3
libglib-2.0.la          libgobject-2.0.la          pkgconfig
libglib-2.0.so          libgobject-2.0.so          python2.4
libglib-2.0.so.0        libgobject-2.0.so.0        python2.5
libglib-2.0.so.0.902.3  libgobject-2.0.so.0.902.3
libgmodule-2.0.la       libgthread-2.0.la
[/COLOR]

---

### Post by cylon359 on 2007-07-15
What does "pkg-config --modversion gtk+-2.0 glib-2.0" print ?

---

### Post by jixuanliu on 2007-07-15
it gives this:

[COLOR="Navy"]$ pkg-config --modversion gtk+-2.0 glib-2.0[/COLOR]
[COLOR="DarkOrange"]2.10.11
2.9.5[/COLOR]

does it mean that the two packages' version number aren't coherent? if so how can i fix it?

really thanks for the effort going on there.

---

### Post by rodo-&gt;dave on 2007-07-15
Just a thought:

When you installed did you get the -dev libs? 
(ie. libgtk2.0-dev)

---

### Post by jixuanliu on 2007-07-15
yes i think so.

[COLOR="Navy"]$ sudo apt-get install libgtk2.0-dev[/COLOR]
[COLOR="DarkOrange"]&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;       
&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;             
libgtk2.0-dev _[COLOR="DarkRed"]&#24050;&#32463;&#26159;&#26368;&#26032;&#30340;&#29256;&#26412;&#20102;&#12290; [/COLOR]_[COLOR="DarkRed"]**(latest version it is)**[/COLOR]
&#20849;&#21319;&#32423;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#35201;&#21368;&#36733; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 0 &#20010;&#36719;&#20214;&#26410;&#34987;&#21319;&#32423;&#12290;[/COLOR]

---

### Post by rodo-&gt;dave on 2007-07-15
I tried your code and it compiled and the program ran for me.

You must be missing some package but I don't know for sure.

Just FYI: my output from $ pkg-config --modversion gtk+-2.0 glib-2.0
2.10.11
2.12.11

---

### Post by jixuanliu on 2007-07-15
thank you all the same.

from what my apt-getter told me that both my libgtk2.0-dev and libglib2.0-dev are the latest version, but my modversion gives a different version of glib-2.0 than yours.

---

### Post by jixuanliu on 2007-07-15
Thanks for all your help. It's indeed a versioning problem.

fixed when i downloaded glib-2.12.0 from the latest source and "make install"-ed it! :o

---

