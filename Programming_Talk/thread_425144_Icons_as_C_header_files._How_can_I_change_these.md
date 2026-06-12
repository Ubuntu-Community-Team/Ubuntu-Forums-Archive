---
title: "Icons as C header files. How can I change these?"
date: 2007-04-27
forum: Programming Talk
---

### Post by Laterix on 2007-04-27
I just love [sylpheed]("http://sylpheed.sraoss.jp/en/") e-mail client, but the icons are butt ugly! So I want to change these icons. I downloaded the source package from the website and found out that icons are in */src/icons* as xpm, png and h files. I can change the xpm-files and changes are applied after I compile the program.

If I change .png files these changes won't have any effect. Old icons are still used. It seems that there is a header file for each png file. For example **stock_inbox.png** and **stock_inbox.h**. So the application probably uses only those headers.

Now, my question is: **How can I create a C-header file from PNG or is this even possible?** I really want to change these icons. Hopefully someone can help me with this.

Here is the content of** stock_inbox.h**
```

/* GdkPixbuf RGBA C-Source image dump 1-byte-run-length-encoded */

#ifdef __SUNPRO_C
#pragma align 4 (stock_inbox)
#endif
#ifdef __GNUC__
static const guint8 stock_inbox[] __attribute__ ((__aligned__ (4))) = 
#else
static const guint8 stock_inbox[] = 
#endif
{ ""
  /* Pixbuf magic (0x47646b50) */
  "GdkP"
  /* length: header (24) + pixel_data (703) */
  "\0\0\2\327"
  /* pixdata_type (0x2010002) */
  "\2\1\0\2"
  /* rowstride (64) */
  "\0\0\0@"
  /* width (16) */
  "\0\0\0\20"
  /* height (16) */
  "\0\0\0\20"
  /* pixel_data: */
  "\206\0\0\0\0\1\0\0\0.\202\0\0\0\377\1\0\0\0\23\212\0\0\0\0\7\0\0\0.\0"
  "\0\0\377\245\236\222\377\335\333\326\377\366\366\365\377\0\0\0\377\0"
  "\0\0\23\207\0\0\0\0\12\0\0\0.\0\0\0\377\252\244\231\377\343\341\336\377"
  "\204|m\377+)$\377\256\250\235\377\364\363\362\377\0\0\0\377\0\0\0\23"
  "\204\0\0\0\0\5\0\0\0.960\377\267\262\250\377\343\341\336\377\316\312"
  "\303\377\202\15\14\12\377\6)'\"\377qk^\377\331\327\322\377\364\363\362"
  "\377\0\0\0\377\0\0\0\23\203\0\0\0\0\16\0\0\0\377\372\372\371\377\310"
  "\304\275\377\0\0\0\377\12\12\11\377\30\26\23\377FA9\377xqc\377\204|m"
  "\377\220\210y\377\341\336\332\377\364\363\362\377\0\0\0\377\0\0\0\23"
  "\202\0\0\0\0\21\0\0\0\377\377\377\377\377\345\343\340\377FA9\377HC;\377"
  "c]R\377xqc\377\207\177p\377\224\214}\377\234\225\207\377\236\230\213"
  "\377\341\336\332\377\364\363\362\377\0\0\0\377\0\0\0\23\0\0\0\0\0\0\0"
  "\377\202\377\377\377\377\15\345\343\340\377(&!\377c]R\377zse\377\217"
  "\207x\377\235\226\210\377\240\232\215\377\241\233\216\377\244\235\221"
  "\377\331\327\322\377\366\365\364\377\0\0\0\377\0\0\0\23\211\0\0\0\377"
  "\6\212\204z\377\245\236\222\377\250\241\225\377\252\244\231\377\341\336"
  "\332\377\362\361\357\377\202\0\0\0\377\207\377\377\377\377\13\0\0\0\377"
  "qlc\377\210\203{\377\257\251\236\377\261\254\241\377\304\300\271\377"
  "\331\327\322\377hhh\377\0\0\0\377\377\377\377\377\357\357\357\377\204"
  "Ki\203\377\10\314\314\314\377\0\0\0\377hd\\\377\212\205|\377\272\266"
  "\254\377\323\321\314\377\210\205\201\377WRH\377\202\0\0\0\377\1\377\377"
  "\377\377\202\357\357\357\377\203Ki\203\377\6\314\314\314\377\0\0\0\377"
  "d_V\377\270\265\256\377\223\220\213\377XUN\377\202\0\0\0\377\4\0\0\0"
  "4\0\0\0\377\377\377\377\377\357\357\357\377\204Ki\203\377\4\314\314\314"
  "\377\0\0\0\377urk\377^ZT\377\202\0\0\0\377\1\0\0\0C\202\0\0\0\0\2\0\0"
  "\0\377\377\377\377\377\203Ki\203\377\3\357\357\357\377Ki\203\377\314"
  "\314\314\377\203\0\0\0\377\1\0\0\0C\204\0\0\0\0\4\0\0\0\377\377\377\377"
  "\377\357\357\357\377Ki\203\377\203\357\357\357\377\3\314\314\314\377"
  "\0\0\0\377\0\0\0N\206\0\0\0\0\2\0\0\0\377\377\377\377\377\206\314\314"
  "\314\377\1\30\30\30\377\207\0\0\0\0\202\0\0\0\377\1\11\11\11\377\206"
  "\0\0\0\377\207\0\0\0\0"};

```

---

### Post by WW on 2007-04-27
The program [gdk-pixbuf-csource]("http://developer.gnome.org/doc/API/2.0/gdk-pixbuf/gdk-pixbuf-csource.html") does this.  Something like this should work:
```

$ gdk-pixbuf-csource myicon.png > myicon.h

```
Take a look at the [gdk-pixbuf web page]("http://developer.gnome.org/doc/API/2.0/gdk-pixbuf/index.html") for more information.

---

### Post by Laterix on 2007-04-27
> **WW said:**
> The program [gdk-pixbuf-csource]("http://developer.gnome.org/doc/API/2.0/gdk-pixbuf/gdk-pixbuf-csource.html") does this.  Something like this should work:
```

$ gdk-pixbuf-csource myicon.png > myicon.h

```
Take a look at the [gdk-pixbuf web page]("http://developer.gnome.org/doc/API/2.0/gdk-pixbuf/index.html") for more information.
Thanks for the tip! This looks exactly what I was looking for.

---

### Post by Laterix on 2007-04-27
I got it to work. Thanks again.

I used commands like this to create those header files.
```

gdk-pixbuf-csource --build-list stock_mail-forward stock_mail-forward.png > stock_mail-forward.h

```
Sadly, I had to modify some of the headers after generation. For example in **stock_mail-forward.h** I had to change all **stock_mail-forward** to **stock_mail_forward**.

Just in case that someone else is interested to change these icons.

Here is a [**screenshot**]("http://users.utu.fi/ljtaim/pics/sylpheed.png") of what I achieved. I find it much more beautiful than the [**original look**]("http://sylpheed.sraoss.jp/images/sylpheed2-mainwindow.png").

---

### Post by patiobarbecue on 2012-12-04
> **Laterix said:**
> 

```

/* GdkPixbuf RGBA C-Source image dump 1-byte-run-length-encoded */

#ifdef __SUNPRO_C
#pragma align 4 (stock_inbox)
#endif
#ifdef __GNUC__
static const guint8 stock_inbox[] __attribute__ ((__aligned__ (4))) = 
#else
static const guint8 stock_inbox[] = 
#endif
{ ""
  /* Pixbuf magic (0x47646b50) */
  "GdkP"
  /* length: header (24) + pixel_data (703) */
  "\0\0\2\327"
  /* pixdata_type (0x2010002) */
  "\2\1\0\2"
  /* rowstride (64) */
  "\0\0\0@"
  /* width (16) */
  "\0\0\0\20"
  /* height (16) */
  "\0\0\0\20"
  /* pixel_data: */
  "\206\0\0\0\0\1\0\0\0.\202\0\0\0\377\1\0\0\0\23\212\0\0\0\0\7\0\0\0.\0"
  "\0\0\377\245\236\222\377\335\333\326\377\366\366\365\377\0\0\0\377\0"
  "\0\0\23\207\0\0\0\0\12\0\0\0.\0\0\0\377\252\244\231\377\343\341\336\377"
  "\204|m\377+)$\377\256\250\235\377\364\363\362\377\0\0\0\377\0\0\0\23"
  "\204\0\0\0\0\5\0\0\0.960\377\267\262\250\377\343\341\336\377\316\312"
  "\303\377\202\15\14\12\377\6)'\"\377qk^\377\331\327\322\377\364\363\362"
  "\377\0\0\0\377\0\0\0\23\203\0\0\0\0\16\0\0\0\377\372\372\371\377\310"
  "\304\275\377\0\0\0\377\12\12\11\377\30\26\23\377FA9\377xqc\377\204|m"
  "\377\220\210y\377\341\336\332\377\364\363\362\377\0\0\0\377\0\0\0\23"
  "\202\0\0\0\0\21\0\0\0\377\377\377\377\377\345\343\340\377FA9\377HC;\377"
  "c]R\377xqc\377\207\177p\377\224\214}\377\234\225\207\377\236\230\213"
  "\377\341\336\332\377\364\363\362\377\0\0\0\377\0\0\0\23\0\0\0\0\0\0\0"
  "\377\202\377\377\377\377\15\345\343\340\377(&!\377c]R\377zse\377\217"
  "\207x\377\235\226\210\377\240\232\215\377\241\233\216\377\244\235\221"
  "\377\331\327\322\377\366\365\364\377\0\0\0\377\0\0\0\23\211\0\0\0\377"
  "\6\212\204z\377\245\236\222\377\250\241\225\377\252\244\231\377\341\336"
  "\332\377\362\361\357\377\202\0\0\0\377\207\377\377\377\377\13\0\0\0\377"
  "qlc\377\210\203{\377\257\251\236\377\261\254\241\377\304\300\271\377"
  "\331\327\322\377hhh\377\0\0\0\377\377\377\377\377\357\357\357\377\204"
  "Ki\203\377\10\314\314\314\377\0\0\0\377hd\\\377\212\205|\377\272\266"
  "\254\377\323\321\314\377\210\205\201\377WRH\377\202\0\0\0\377\1\377\377"
  "\377\377\202\357\357\357\377\203Ki\203\377\6\314\314\314\377\0\0\0\377"
  "d_V\377\270\265\256\377\223\220\213\377XUN\377\202\0\0\0\377\4\0\0\0"
  "4\0\0\0\377\377\377\377\377\357\357\357\377\204Ki\203\377\4\314\314\314"
  "\377\0\0\0\377urk\377^ZT\377\202\0\0\0\377\1\0\0\0C\202\0\0\0\0\2\0\0"
  "\0\377\377\377\377\377\203Ki\203\377\3\357\357\357\377Ki\203\377\314"
  "\314\314\377\203\0\0\0\377\1\0\0\0C\204\0\0\0\0\4\0\0\0\377\377\377\377"
  "\377\357\357\357\377Ki\203\377\203\357\357\357\377\3\314\314\314\377"
  "\0\0\0\377\0\0\0N\206\0\0\0\0\2\0\0\0\377\377\377\377\377\206\314\314"
  "\314\377\1\30\30\30\377\207\0\0\0\0\202\0\0\0\377\1\11\11\11\377\206"
  "\0\0\0\377\207\0\0\0\0"};

```

The code throws me into wildness: how to understand the type of this C array? First of all, it is typed guint8, why not char * stock_inbox[] = {,,,}; furthermore, don't we need commas between initilizing items? I copied (chage guint8 to int) the array into a hello-world C code, and it cannot compile. The error is:

error: wide character array initialized from non-wide string

Can anybody explain to me how it works?

```

#include <stdio.h>

#ifdef __SUNPRO_C
#pragma align 4 (sym_alpha)
#endif
#ifdef __GNUC__
static const int sym_alpha[] __attribute__ ((__aligned__ (4))) = 
#else
static const int sym_alpha[] = 
#endif
{ ""
  /* Pixbuf magic (0x47646b50) */
  "GdkP"
  /* length: header (24) + pixel_data (451) */
  "\0\0\1\333"
  /* pixdata_type (0x2010002) */
  "\2\1\0\2"
  /* rowstride (152) */
  "\0\0\0\230"
  /* width (38) */
  "\0\0\0&"
  /* height (38) */
  "\0\0\0&"
  /* pixel_data: */
  "\377\0\0\0\0\377\0\0\0\0\377\0\0\0\0\377\0\0\0\0\250\0\0\0\0\6\0\0\0"
  "U\0\0\0\220\0\0\0\204\0\0\0\250\0\0\0o\0\0\0\2\236\0\0\0\0\4\0\0\0\6"
  "\0\0\0\227\0\0\0\300\0\0\0\12\202\0\0\0\0\2\0\0\0\300\0\0\0t\202\0\0"
  "\0\0\1\0\0\0h\233\0\0\0\0\3\0\0\0\217\0\0\0\327\0\0\0\13\203\0\0\0\0"
  "\5\0\0\0a\0\0\0\364\0\0\0\7\0\0\0\6\0\0\0\224\232\0\0\0\0\3\0\0\0""5"
  "\0\0\0\375\0\0\0p\204\0\0\0\0\5\0\0\0J\0\0\0\377\0\0\0)\0\0\0Q\0\0\0"
  "8\232\0\0\0\0\3\0\0\0\235\0\0\0\373\0\0\0\25\204\0\0\0\0\4\0\0\0""4\0"
  "\0\0\377\0\0\0O\0\0\0|\233\0\0\0\0\2\0\0\0\324\0\0\0\326\205\0\0\0\0"
  "\4\0\0\0%\0\0\0\377\0\0\0\271\0\0\0\37\233\0\0\0\0\2\0\0\0\362\0\0\0"
  "\257\205\0\0\0\0\3\0\0\0\36\0\0\0\377\0\0\0\220\234\0\0\0\0\2\0\0\0\305"
  "\0\0\0\264\205\0\0\0\0\3\0\0\0@\0\0\0\377\0\0\0W\234\0\0\0\0\3\0\0\0"
  "P\0\0\0\363\0\0\0\13\202\0\0\0\0\7\0\0\0\14\0\0\0\177\0\0\0l\0\0\0\325"
  "\0\0\0r\0\0\0\11\0\0\0[\233\0\0\0\0\13\0\0\0Y\0\0\0\273\0\0\0\207\0\0"
  "\0v\0\0\0w\0\0\0\30\0\0\0\0\0\0\0>\0\0\0\275\0\0\0u\0\0\0!\377\0\0\0"
  "\0\377\0\0\0\0\377\0\0\0\0\377\0\0\0\0\245\0\0\0\0"};



int main(){

  printf("Hello: %d\n",stock_inbox[0]);

}


```

---

### Post by trent.josephsen on 2012-12-04
1) Don't change stuff if you don't understand what it already does.
2) What do you mean, commas between initializing items? There's only one initializer, where would you put commas?
3) This is an old thread, if you have questions about C you should start a new one.

---

