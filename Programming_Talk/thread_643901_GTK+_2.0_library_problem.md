---
title: "GTK+ 2.0 library problem"
date: 2007-12-18
forum: Programming Talk
---

### Post by dubemasterd88 on 2007-12-18
I installed GTK+ 2.0, and have all the development headers and everything.  I try to compile a simple program (just diplaying a single window), and it will not work.  I compile as follows:

gcc 'pkg-config --cflags -libs gtk+-2.0' main.c

and I get a ridiculous amount of errors, all coming from the gtk header files:

/usr/include/gtk/gtktextbuffer.h:272: error: expected declaration specifiers before ‘GtkTextMark’
/usr/include/gtk/gtktextbuffer.h:275: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:277: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:284: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:288: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:292: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:296: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:300: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:308: error: expected declaration specifiers before ‘GtkTextTag’
/usr/include/gtk/gtktextbuffer.h:316: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:320: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:324: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:327: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:330: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:332: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:334: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:337: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:341: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:354: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:355: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:358: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:360: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:362: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:365: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:368: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:370: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:375: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:378: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:383: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:384: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:386: error: expected declaration specifiers before ‘GtkTargetList’
/usr/include/gtk/gtktextbuffer.h:387: error: expected declaration specifiers before ‘GtkTargetList’
/usr/include/gtk/gtktextbuffer.h:390: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:392: error: expected declaration specifiers before ‘GtkTextBTree’
/usr/include/gtk/gtktextbuffer.h:394: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:398: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbuffer.h:401: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:175,
                 from main.c:1:
/usr/include/gtk/gtktextbufferrichtext.h:35: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:44: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:49: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:52: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:57: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:60: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:62: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:65: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:68: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:71: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:73: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:76: error: expected declaration specifiers before ‘guint8’
/usr/include/gtk/gtktextbufferrichtext.h:82: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextbufferrichtext.h:90: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:176,
                 from main.c:1:
/usr/include/gtk/gtktextview.h:53: error: expected declaration specifiers before ‘GtkTextWindowType’
/usr/include/gtk/gtktextview.h:57: error: storage class specified for parameter ‘GtkTextView’
/usr/include/gtk/gtktextview.h:58: error: storage class specified for parameter ‘GtkTextViewClass’
/usr/include/gtk/gtktextview.h:61: error: storage class specified for parameter ‘GtkTextWindow’
/usr/include/gtk/gtktextview.h:62: error: storage class specified for parameter ‘GtkTextPendingScroll’
/usr/include/gtk/gtktextview.h:66: error: expected specifier-qualifier-list before ‘GtkContainer’
/usr/include/gtk/gtktextview.h:155: error: expected specifier-qualifier-list before ‘GtkContainerClass’
/usr/include/gtk/gtktextview.h:215: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktextview.h:217: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:218: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:220: error: expected declaration specifiers before ‘GtkTextBuffer’
/usr/include/gtk/gtktextview.h:221: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:227: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:233: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:235: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:237: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:239: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:241: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:243: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:245: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:248: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:252: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:257: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:262: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:267: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:273: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:280: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:282: error: expected declaration specifiers before ‘GtkTextWindowType’
/usr/include/gtk/gtktextview.h:285: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:288: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:291: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:293: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:295: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:297: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:299: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:301: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:306: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:310: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:317: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:325: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:327: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:328: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:330: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:331: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:333: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:334: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:336: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:337: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:339: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:340: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:342: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:343: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:345: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:346: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:348: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:349: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:351: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:352: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:354: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:355: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:357: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktextview.h:358: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktextview.h:360: error: expected declaration specifiers before ‘PangoTabArray’
/usr/include/gtk/gtktextview.h:363: error: expected declaration specifiers before ‘GtkTextAttributes’
/usr/include/gtk/gtktextview.h:365: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:177,
                 from main.c:1:
/usr/include/gtk/gtktipsquery.h:52: error: storage class specified for parameter ‘GtkTipsQueryClass’
/usr/include/gtk/gtktipsquery.h:58: error: expected specifier-qualifier-list before ‘GtkLabel’
/usr/include/gtk/gtktipsquery.h:73: error: expected specifier-qualifier-list before ‘GtkLabelClass’
/usr/include/gtk/gtktipsquery.h:96: error: expected declaration specifiers before ‘GtkType’
/usr/include/gtk/gtktipsquery.h:98: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktipsquery.h:99: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktipsquery.h:100: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktipsquery.h:102: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktipsquery.h:106: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:181,
                 from main.c:1:
/usr/include/gtk/gtktoolbar.h:67: error: expected declaration specifiers before ‘GtkToolbarChildType’
/usr/include/gtk/gtktoolbar.h:69: error: storage class specified for parameter ‘GtkToolbarChild’
/usr/include/gtk/gtktoolbar.h:73: error: expected specifier-qualifier-list before ‘GtkToolbarChildType’
/usr/include/gtk/gtktoolbar.h:85: error: storage class specified for parameter ‘GtkToolbarSpaceStyle’
/usr/include/gtk/gtktoolbar.h:87: error: storage class specified for parameter ‘GtkToolbar’
/usr/include/gtk/gtktoolbar.h:88: error: storage class specified for parameter ‘GtkToolbarClass’
/usr/include/gtk/gtktoolbar.h:89: error: storage class specified for parameter ‘GtkToolbarPrivate’
/usr/include/gtk/gtktoolbar.h:93: error: expected specifier-qualifier-list before ‘GtkContainer’
/usr/include/gtk/gtktoolbar.h:121: error: expected specifier-qualifier-list before ‘GtkContainerClass’
/usr/include/gtk/gtktoolbar.h:139: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktoolbar.h:141: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:144: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktoolbar.h:146: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktoolbar.h:147: error: expected declaration specifiers before ‘GtkToolItem’
/usr/include/gtk/gtktoolbar.h:149: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:150: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:152: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:153: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:155: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:156: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:158: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:159: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:161: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:162: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:163: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:164: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktoolbar.h:167: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:172: error: expected declaration specifiers before ‘gchar’
/usr/include/gtk/gtktoolbar.h:174: error: expected declaration specifiers or ‘...’ before ‘GtkToolbar’
/usr/include/gtk/gtktoolbar.h:176: error: expected declaration specifiers or ‘...’ before ‘GtkAllocation’
/usr/include/gtk/gtktoolbar.h:177: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktoolbar.h:178: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:181: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:183: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:187: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:194: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:201: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:211: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:220: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:221: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:222: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:224: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:227: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:237: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:247: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:259: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:263: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:267: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktoolbar.h:276: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:187,
                 from main.c:1:
/usr/include/gtk/gtktreednd.h:34: error: storage class specified for parameter ‘GtkTreeDragSourceIface’
/usr/include/gtk/gtktreednd.h:38: error: expected specifier-qualifier-list before ‘GTypeInterface’
/usr/include/gtk/gtktreednd.h:53: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktreednd.h:56: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:60: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:66: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:75: error: storage class specified for parameter ‘GtkTreeDragDest’
/usr/include/gtk/gtktreednd.h:76: error: storage class specified for parameter ‘GtkTreeDragDestIface’
/usr/include/gtk/gtktreednd.h:80: error: expected specifier-qualifier-list before ‘GTypeInterface’
/usr/include/gtk/gtktreednd.h:93: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktreednd.h:98: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:104: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:112: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:115: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreednd.h:119: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:191,
                 from main.c:1:
/usr/include/gtk/gtktreemodelsort.h:36: error: storage class specified for parameter ‘GtkTreeModelSortClass’
/usr/include/gtk/gtktreemodelsort.h:40: error: expected specifier-qualifier-list before ‘GObject’
/usr/include/gtk/gtktreemodelsort.h:69: error: expected specifier-qualifier-list before ‘GObjectClass’
/usr/include/gtk/gtktreemodelsort.h:79: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktreemodelsort.h:80: error: expected declaration specifiers before ‘GtkTreeModel’
/usr/include/gtk/gtktreemodelsort.h:82: error: expected declaration specifiers before ‘GtkTreeModel’
/usr/include/gtk/gtktreemodelsort.h:83: error: expected declaration specifiers before ‘GtkTreePath’
/usr/include/gtk/gtktreemodelsort.h:85: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreemodelsort.h:88: error: expected declaration specifiers before ‘GtkTreePath’
/usr/include/gtk/gtktreemodelsort.h:90: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreemodelsort.h:93: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreemodelsort.h:94: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreemodelsort.h:95: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreemodelsort.h:99: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:192,
                 from main.c:1:
/usr/include/gtk/gtktreeselection.h:42: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:49: error: expected specifier-qualifier-list before ‘GObject’
/usr/include/gtk/gtktreeselection.h:62: error: expected specifier-qualifier-list before ‘GObjectClass’
/usr/include/gtk/gtktreeselection.h:74: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktreeselection.h:76: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:78: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:79: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:83: error: expected declaration specifiers before ‘gpointer’
/usr/include/gtk/gtktreeselection.h:84: error: expected declaration specifiers before ‘GtkTreeView’
/usr/include/gtk/gtktreeselection.h:88: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:91: error: expected declaration specifiers before ‘GList’
/usr/include/gtk/gtktreeselection.h:93: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktreeselection.h:94: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:97: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:99: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:101: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:103: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:105: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:107: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:109: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:110: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:111: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:114: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreeselection.h:119: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:193,
                 from main.c:1:
/usr/include/gtk/gtktreestore.h:28: error: expected declaration specifiers before ‘G_BEGIN_DECLS’
/usr/include/gtk/gtktreestore.h:39: error: storage class specified for parameter ‘GtkTreeStoreClass’
/usr/include/gtk/gtktreestore.h:43: error: expected specifier-qualifier-list before ‘GObject’
/usr/include/gtk/gtktreestore.h:61: error: expected specifier-qualifier-list before ‘GObjectClass’
/usr/include/gtk/gtktreestore.h:71: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtktreestore.h:72: error: expected declaration specifiers before ‘GtkTreeStore’
/usr/include/gtk/gtktreestore.h:74: error: expected declaration specifiers before ‘GtkTreeStore’
/usr/include/gtk/gtktreestore.h:76: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:82: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:86: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:89: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:94: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:97: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:99: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:103: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:107: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:111: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:116: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:123: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:126: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:129: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:132: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtktreestore.h:134: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:135: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:137: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:140: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:143: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:146: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtktreestore.h:151: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:197,
                 from main.c:1:
/usr/include/gtk/gtkuimanager.h:51: error: storage class specified for parameter ‘GtkUIManagerClass’
/usr/include/gtk/gtkuimanager.h:52: error: storage class specified for parameter ‘GtkUIManagerPrivate’
/usr/include/gtk/gtkuimanager.h:56: error: expected specifier-qualifier-list before ‘GObject’
/usr/include/gtk/gtkuimanager.h:64: error: expected specifier-qualifier-list before ‘GObjectClass’
/usr/include/gtk/gtkuimanager.h:103: error: storage class specified for parameter ‘GtkUIManagerItemType’
/usr/include/gtk/gtkuimanager.h:110: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkuimanager.h:111: error: expected declaration specifiers before ‘GtkUIManager’
/usr/include/gtk/gtkuimanager.h:112: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:114: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:115: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:118: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:120: error: expected declaration specifiers before ‘GList’
/usr/include/gtk/gtkuimanager.h:121: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:122: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:124: error: expected declaration specifiers before ‘GSList’
/usr/include/gtk/gtkuimanager.h:126: error: expected declaration specifiers before ‘GtkAction’
/usr/include/gtk/gtkuimanager.h:128: error: expected declaration specifiers before ‘guint’
/usr/include/gtk/gtkuimanager.h:132: error: expected declaration specifiers before ‘guint’
/usr/include/gtk/gtkuimanager.h:135: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:142: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:144: error: expected declaration specifiers before ‘gchar’
/usr/include/gtk/gtkuimanager.h:145: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkuimanager.h:146: error: expected declaration specifiers before ‘guint’
/usr/include/gtk/gtkuimanager.h:148: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:198,
                 from main.c:1:
/usr/include/gtk/gtkvbbox.h:46: error: storage class specified for parameter ‘GtkVButtonBoxClass’
/usr/include/gtk/gtkvbbox.h:50: error: expected specifier-qualifier-list before ‘GtkButtonBox’
/usr/include/gtk/gtkvbbox.h:55: error: expected specifier-qualifier-list before ‘GtkButtonBoxClass’
/usr/include/gtk/gtkvbbox.h:59: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkvbbox.h:65: error: expected declaration specifiers before ‘gint’
/usr/include/gtk/gtkvbbox.h:66: error: expected ‘)’ before ‘spacing’
/usr/include/gtk/gtkvbbox.h:73: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:202,
                 from main.c:1:
/usr/include/gtk/gtkvolumebutton.h:45: error: storage class specified for parameter ‘GtkVolumeButtonClass’
/usr/include/gtk/gtkvolumebutton.h:49: error: expected specifier-qualifier-list before ‘GtkScaleButtonClass’
/usr/include/gtk/gtkvolumebutton.h:58: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkvolumebutton.h:61: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:203,
                 from main.c:1:
/usr/include/gtk/gtkvpaned.h:45: error: storage class specified for parameter ‘GtkVPanedClass’
/usr/include/gtk/gtkvpaned.h:49: error: expected specifier-qualifier-list before ‘GtkPaned’
/usr/include/gtk/gtkvpaned.h:54: error: expected specifier-qualifier-list before ‘GtkPanedClass’
/usr/include/gtk/gtkvpaned.h:57: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkvpaned.h:61: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:204,
                 from main.c:1:
/usr/include/gtk/gtkvruler.h:57: error: storage class specified for parameter ‘GtkVRulerClass’
/usr/include/gtk/gtkvruler.h:61: error: expected specifier-qualifier-list before ‘GtkRuler’
/usr/include/gtk/gtkvruler.h:66: error: expected specifier-qualifier-list before ‘GtkRulerClass’
/usr/include/gtk/gtkvruler.h:70: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkvruler.h:74: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:205,
                 from main.c:1:
/usr/include/gtk/gtkvscale.h:47: error: storage class specified for parameter ‘GtkVScaleClass’
/usr/include/gtk/gtkvscale.h:51: error: expected specifier-qualifier-list before ‘GtkScale’
/usr/include/gtk/gtkvscale.h:56: error: expected specifier-qualifier-list before ‘GtkScaleClass’
/usr/include/gtk/gtkvscale.h:60: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkvscale.h:61: error: expected ‘)’ before ‘*’ token
/usr/include/gtk/gtkvscale.h:62: error: expected ‘)’ before ‘min’
/usr/include/gtk/gtkvscale.h:67: error: expected declaration specifiers before ‘G_END_DECLS’
In file included from /usr/include/gtk/gtk.h:207,
                 from main.c:1:
/usr/include/gtk/gtkvseparator.h:47: error: storage class specified for parameter ‘GtkVSeparatorClass’
/usr/include/gtk/gtkvseparator.h:51: error: expected specifier-qualifier-list before ‘GtkSeparator’
/usr/include/gtk/gtkvseparator.h:56: error: expected specifier-qualifier-list before ‘GtkSeparatorClass’
/usr/include/gtk/gtkvseparator.h:60: error: expected declaration specifiers before ‘GType’
/usr/include/gtk/gtkvseparator.h:64: error: expected declaration specifiers before ‘G_END_DECLS’


Can someone please help????

---

### Post by jespdj on 2007-12-19
> gcc 'pkg-config --cflags -libs gtk+-2.0' main.c
Note that the quotes should not be normal, straight quotes, but backticks. The key for that is on the top left of your keyboard, together with the tilde (~). Also, it should be "--libs" with two dashes, not with one dash. So:
```
gcc `pkg-config --cflags --libs gtk+-2.0` main.c
```

---

### Post by Vox754 on 2007-12-19
> **jespdj said:**
> Note that the quotes should not be normal, straight quotes, but backticks. **The key for that is on the top left of your keyboard, together with the tilde (~).**

This is bad advice since not everybody uses the same keyboard.

> **dubemasterd88 said:**
> 
and I get a ridiculous amount of errors, all coming from the gtk header files:
...

Man! Do you really think it is necessary to post all those errors?

[Readability of your post.](http://ubuntuforums.org/showthread.php?t=641693)

[Gtk+ headers?](http://ubuntuforums.org/showthread.php?t=567049)

---

### Post by jespdj on 2007-12-19
> **Vox754 said:**
> This is bad advice since not everybody uses the same keyboard.
Well, that's where backticks are on most keyboards. If it's not there on his keyboard, I trust that he's smart enough to find where the backticks are on his keyboard...

---

### Post by Vox754 on 2007-12-19
> **jespdj said:**
> Well, that's where backticks are **on most keyboards**.
Again, generalizations are bad.
But hey
> **Wikipedia]
[Keyboard Layout](http://en.wikipedia.org/wiki/Keyboard_layout#Dutch_.28Netherlands.29)
The Dutch keyboard layout is barely used said:**
> 
Interesting.

[QUOTE=jespdj;3981548]
If it's not there on his keyboard, **I trust that he's smart enough** to find where the backticks are on his keyboard...

Agreed!

By the way, the use of backticks (backquotes, [grave accents](http://en.wikipedia.org/wiki/Grave_accent)) is a way of [command substitution in bash.](http://tldp.org/LDP/abs/html/commandsub.html)
```

textfile_listing=`ls *.txt`
# Variable contains names of all *.txt files in current working directory.
echo $textfile_listing

textfile_listing2=$(ls *.txt)   # The alternative form of command substitution.
echo $textfile_listing2
# Same result.

```

---

