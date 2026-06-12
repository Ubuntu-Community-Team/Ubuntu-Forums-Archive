---
title: "[C++] Trying to Include/Link librsvg"
date: 2010-09-15
forum: Programming Talk
---

### Post by dodle on 2010-09-15
I've been trying to learn how to use librsvg, but have been unable to include it in my projects.  So to demonstrate my problem I just used the simple "Hello World!" program:

[php]#include <iostream>
#include <librsvg/rsvg.h>
using namespace std;

int main()
{
    cout << "Hello World!" << endl;
    return 0;
}[/php]

I tried compiling like this, but it couldn't find librsvg:
```
$ g++ hello.cpp -o test
hello.cpp:2:26: error: librsvg/rsvg.h: No such file or directory
```

I thought that I needed to use a linker flag, but it just gave me the same result:
```
$ g++ hello.cpp -o test -lrsvg
hello.cpp:2:26: error: librsvg/rsvg.h: No such file or directory
```

So I found where librsvg resides and included that in the compiler line:
```
$ g++ hello.cpp -I/usr/include/librsvg-2 -o test
In file included from hello.cpp:2:
/usr/include/librsvg-2/librsvg/rsvg.h:29:35: error: gdk-pixbuf/gdk-pixbuf.h: No such file or directory
In file included from hello.cpp:2:
/usr/include/librsvg-2/librsvg/rsvg.h:31: error: &#8216;G_BEGIN_DECLS&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:53: error: &#8216;GQuark&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:65: error: &#8216;GObjectClass&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:67: error: &#8216;gpointer&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:71: error: &#8216;GObject&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:75: error: &#8216;gpointer&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:94: error: &#8216;gdouble&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:99: error: &#8216;gdouble&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:120: error: &#8216;gboolean&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:122: error: &#8216;gboolean&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:123: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:124: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:126: error: expected constructor, destructor, or type conversion before &#8216;char&#8217;
/usr/include/librsvg-2/librsvg/rsvg.h:131: error: &#8216;gboolean&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:132: error: &#8216;gboolean&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:134: error: &#8216;gboolean&#8217; does not name a type
/usr/include/librsvg-2/librsvg/rsvg.h:138: error: expected constructor, destructor, or type conversion before &#8216;char&#8217;
/usr/include/librsvg-2/librsvg/rsvg.h:139: error: expected constructor, destructor, or type conversion before &#8216;char&#8217;
/usr/include/librsvg-2/librsvg/rsvg.h:140: error: expected constructor, destructor, or type conversion before &#8216;char&#8217;
/usr/include/librsvg-2/librsvg/rsvg.h:142: error: ISO C++ forbids declaration of &#8216;guint8&#8217; with no type
/usr/include/librsvg-2/librsvg/rsvg.h:142: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:143: error: ISO C++ forbids declaration of &#8216;gchar&#8217; with no type
/usr/include/librsvg-2/librsvg/rsvg.h:143: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:162: error: typedef &#8216;RsvgSizeFunc&#8217; is initialized (use decltype instead)
/usr/include/librsvg-2/librsvg/rsvg.h:162: error: &#8216;gint&#8217; was not declared in this scope
/usr/include/librsvg-2/librsvg/rsvg.h:162: error: &#8216;width&#8217; was not declared in this scope
/usr/include/librsvg-2/librsvg/rsvg.h:162: error: &#8216;gint&#8217; was not declared in this scope
/usr/include/librsvg-2/librsvg/rsvg.h:162: error: &#8216;height&#8217; was not declared in this scope
/usr/include/librsvg-2/librsvg/rsvg.h:162: error: &#8216;gpointer&#8217; was not declared in this scope
/usr/include/librsvg-2/librsvg/rsvg.h:164: error: &#8216;RsvgSizeFunc&#8217; has not been declared
/usr/include/librsvg-2/librsvg/rsvg.h:165: error: &#8216;gpointer&#8217; has not been declared
/usr/include/librsvg-2/librsvg/rsvg.h:165: error: &#8216;GDestroyNotify&#8217; has not been declared
/usr/include/librsvg-2/librsvg/rsvg.h:169: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:170: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:172: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:174: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/librsvg-2/librsvg/rsvg.h:176: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
hello.cpp:3: error: expected constructor, destructor, or type conversion before &#8216;using&#8217;
hello.cpp: In function &#8216;int main()&#8217;:
hello.cpp:7: error: &#8216;cout&#8217; was not declared in this scope
hello.cpp:7: error: &#8216;endl&#8217; was not declared in this scope
```

It was now having trouble finding Gdk, so I also included that in the line:
```
$ g++ hello.cpp -I/usr/include/librsvg-2 -I/usr/include/gtk-2.0 -o test
In file included from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:31:18: error: glib.h: No such file or directory
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:33:25: error: glib-object.h: No such file or directory
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:35,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:35:21: error: gio/gio.h: No such file or directory
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:39,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-io.h:38:21: error: gmodule.h: No such file or directory
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:32,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-features.h:34: error: &#8216;guint&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-features.h:35: error: &#8216;guint&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-features.h:36: error: &#8216;guint&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:35,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:40: error: expected constructor, destructor, or type conversion before &#8216;typedef&#8217;
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:44: error: expected constructor, destructor, or type conversion before &#8216;;&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:63: error: typedef &#8216;GdkPixbufDestroyNotify&#8217; is initialized (use decltype instead)
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:63: error: &#8216;guchar&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:63: error: &#8216;pixels&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:63: error: &#8216;gpointer&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:81: error: &#8216;GQuark&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:85: error: &#8216;GType&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:98: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:100: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:108: error: &#8216;gboolean&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:132: error: &#8216;GError&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:136: error: &#8216;GError&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:140: error: &#8216;gboolean&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:141: error: &#8216;GError&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:143: error: ISO C++ forbids declaration of &#8216;guchar&#8217; with no type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:143: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:153: error: &#8216;gint&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:154: error: expected primary-expression before &#8216;const&#8217;
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:155: error: &#8216;gboolean&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:156: error: &#8216;GError&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:156: error: &#8216;error&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:156: error: initializer expression list treated as compound expression
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:160: error: &#8216;guint32&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:170: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:176: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:185: error: ISO C++ forbids declaration of &#8216;gboolean&#8217; with no type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:185: error: typedef &#8216;gboolean&#8217; is initialized (use decltype instead)
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:185: error: &#8216;GdkPixbufSaveFunc&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:190: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:197: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:207: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:214: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:222: error: &#8216;GInputStream&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:222: error: &#8216;stream&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:223: error: &#8216;GCancellable&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:223: error: &#8216;cancellable&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:224: error: &#8216;GError&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:224: error: &#8216;error&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:224: error: initializer expression list treated as compound expression
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:226: error: &#8216;GInputStream&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:226: error: &#8216;stream&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:227: error: &#8216;gint&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:228: error: &#8216;gint&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:229: error: &#8216;gboolean&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:230: error: &#8216;GCancellable&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:230: error: &#8216;cancellable&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:231: error: &#8216;GError&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:231: error: &#8216;error&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:231: error: initializer expression list treated as compound expression
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:233: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:241: error: &#8216;gboolean&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:242: error: &#8216;guchar&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:242: error: &#8216;guchar&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:242: error: &#8216;guchar&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:254: error: &#8216;gfloat&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:255: error: &#8216;gboolean&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:260: error: &#8216;G_CONST_RETURN&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-core.h:264: error: &#8216;G_END_DECLS&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:36,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:47: error: expected constructor, destructor, or type conversion before &#8216;;&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:66: error: &#8216;GdkInterpType&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:77: error: &#8216;GdkInterpType&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:89: error: &#8216;GdkInterpType&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:94: error: &#8216;guint32&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:95: error: &#8216;guint32&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:100: error: &#8216;GdkInterpType&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:105: error: &#8216;GdkInterpType&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:108: error: &#8216;guint32&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:109: error: &#8216;guint32&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:114: error: &#8216;gboolean&#8217; has not been declared
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-transform.h:116: error: &#8216;G_END_DECLS&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:37,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:52: error: &#8216;GType&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:58: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:62: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:63: error: variable or field &#8216;gdk_pixbuf_animation_unref&#8217; declared void
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:63: error: &#8216;GdkPixbufAnimation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:63: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:66: error: &#8216;GdkPixbufAnimation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:66: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:67: error: &#8216;GdkPixbufAnimation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:67: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:68: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:69: error: &#8216;GdkPixbufAnimation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:69: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:71: error: &#8216;GdkPixbufAnimation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:71: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:72: error: expected primary-expression before &#8216;const&#8217;
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:72: error: initializer expression list treated as compound expression
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:73: error: &#8216;GType&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:76: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:77: error: &#8216;gboolean&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-animation.h:149: error: &#8216;G_END_DECLS&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:38,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:46: error: &#8216;GType&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:47: error: &#8216;GType&#8217; does not name a type
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:49: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:52: error: variable or field &#8216;gdk_pixbuf_simple_anim_add_frame&#8217; declared void
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:52: error: &#8216;GdkPixbufSimpleAnim&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:52: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:53: error: expected primary-expression before &#8216;*&#8217; token
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:53: error: &#8216;pixbuf&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:54: error: variable or field &#8216;gdk_pixbuf_simple_anim_set_loop&#8217; declared void
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:54: error: &#8216;GdkPixbufSimpleAnim&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:54: error: &#8216;animation&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:55: error: &#8216;gboolean&#8217; was not declared in this scope
/usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-simple-anim.h:56: error: &#8216;gboolean&#8217; does not name a type
In file included from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf-io.h:36,
                 from /usr/include/gtk-2.0/gdk-pixbuf/gdk-pixbuf.h:39,
                 from /usr/include/librsvg-2/librsvg/rsvg.h:29,
                 from hello.cpp:2:
/usr/include/stdio.h:30: error: expected constructor, destructor, or type conversion before &#8216;extern&#8217;
```

Now it complains that it cannot find "glib.h", and it just goes on.  What is the right way to link to librsvg?

---

### Post by spjackson on 2010-09-15
If you installed librsvg2-dev from the repos, then pkg-config is your friend.
```

$ g++ hello.cpp -o test `pkg-config --cflags --libs librsvg-2.0`
```

---

### Post by dwhitney67 on 2010-09-15
> **spjackson said:**
> If you installed librsvg2-dev from the repos, then pkg-config is your friend.
```

$ g++ hello.cpp -o test `pkg-config --cflags --libs librsvg-2.0`
```

I don't recommend naming an executable as "test"; one with that name already exists in /usr/bin.  One may draw incorrect conclusions when running their app, unless they are smart enough to run it as "./test".

---

### Post by spjackson on 2010-09-15
> **dwhitney67 said:**
> I don't recommend naming an executable as "test"; one with that name already exists in /usr/bin.  One may draw incorrect conclusions when running their app, unless they are smart enough to run it as "./test".
As that was the original poster's choice, I didn't change it, since it has no bearing whatsoever on the problem presented. If one is a novice lacking understanding of the environment in which one is working, then your point is valid; otherwise there's no problem.

---

### Post by dodle on 2010-09-15
> **spjackson said:**
> If you installed librsvg2-dev from the repos, then pkg-config is your friend.
```

$ g++ hello.cpp -o test `pkg-config --cflags --libs librsvg-2.0`
```

Thank you very much.

---

