---
title: "problems making gtk+-2.10.6 (or gtk+-2.10.3)"
date: 2006-10-05
forum: Packaging and Compiling Programs
---

### Post by americux on 2006-10-05
Hello everybody,
I wanna install gtk+-2.10.6 from sources in Ubuntu Dapper desktop 2.6.15-27-386. To configure I had to do:
#export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
#export LD_LIBRARY_PATH=/usr/local/lib
#GLIB=/usr/src/glib-2.12.3/glib ./configure
to avoid the glib versions pkg-config error.
I installed correctly glib, pango, atk and cairo:
#pkg-config --modversion glib-2.0 pango atk cairo
2.12.3
1.14.4
1.12.2
1.2.4

The ./configure had no problems, but when I make "sudo make I get warnings abount lost links and pointers (dereferencing type-punned pointer will break strict-aliasing rules for example) and the following Errors:
#make
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_mime_type'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_move_item'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_groups'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_app_info'
./.libs/libgtk-x11-2.0.so: undefined reference to `g_bookmark_file_get_added'
collect2: ld returned 1 exit status
make[4]: *** [gtk-query-immodules-2.0] Error 1
make[4]: se sale del directorio `/usr/src/gtk+-2.10.6/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: se sale del directorio `/usr/src/gtk+-2.10.6/gtk'
make[2]: *** [all] Error 2
make[2]: se sale del directorio `/usr/src/gtk+-2.10.6/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/usr/src/gtk+-2.10.6'
make: *** [all] Error 2

If I do gtk-query-immodules-2.0, the result is:
# gtk-query-immodules-2.0
# GTK+ Input Method Modules file
# Automatically generated file, do not edit
# Created by gtk-query-immodules-2.0 from gtk+-2.8.20
#
# ModulesPath = /root/.gtk-2.0/2.4.0/i486-pc-linux-gnu/immodules:/root/.gtk-2.0/2.4.0/immodules:/root/.gtk-2.0/i486-pc-linux-gnu/immodules:/root/.gtk-2.0/immodules:/usr/lib/gtk-2.0/2.4.0/i486-pc-linux-gnu/immodules:/usr/lib/gtk-2.0/2.4.0/immodules:/usr/lib/gtk-2.0/i486-pc-linux-gnu/immodules:/usr/lib/gtk-2.0/immodules
#
"/usr/lib/gtk-2.0/2.4.0/immodules/im-am-et.so"
"am_et" "Amharic (EZ+)" "gtk20" "/usr/share/locale" "am"

"/usr/lib/gtk-2.0/2.4.0/immodules/im-cedilla.so"
"cedilla" "Cedilla" "gtk+" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa"

"/usr/lib/gtk-2.0/2.4.0/immodules/im-cyrillic-translit.so"
"cyrillic_translit" "Cyrillic (Transliterated)" "gtk20" "/usr/share/locale" ""

"/usr/lib/gtk-2.0/2.4.0/immodules/im-inuktitut.so"
"inuktitut" "Inuktitut (Transliterated)" "gtk20" "/usr/share/locale" "iu"

"/usr/lib/gtk-2.0/2.4.0/immodules/im-ipa.so"
"ipa" "IPA" "gtk20" "/usr/share/locale" ""

"/usr/lib/gtk-2.0/2.4.0/immodules/im-scim.so"
"scim" "SCIM Input Method" "scim" "/usr/share/locale" ""

"/usr/lib/gtk-2.0/2.4.0/immodules/im-thai-broken.so"
"thai_broken" "Thai (Broken)" "gtk20" "/usr/share/locale" ""

"/usr/lib/gtk-2.0/2.4.0/immodules/im-ti-er.so"
"ti_er" "Tigrigna-Eritrean (EZ+)" "gtk20" "/usr/share/locale" "ti"

"/usr/lib/gtk-2.0/2.4.0/immodules/im-ti-et.so"
"ti_et" "Tigrigna-Ethiopian (EZ+)" "gtk20" "/usr/share/locale" "ti"

"/usr/lib/gtk-2.0/2.4.0/immodules/im-viqr.so"
"viqr" "Vietnamese (VIQR)" "gtk20" "/usr/share/locale" "vi"

"/usr/lib/gtk-2.0/2.4.0/immodules/im-xim.so"
"xim" "X Input Method" "gtk20" "/usr/share/locale" "ko:ja:th:zh"

Any ideas? If somebody could help me.
Thanks anyway, a.

---

