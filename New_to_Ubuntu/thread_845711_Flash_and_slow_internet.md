---
title: "Flash and slow internet"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by natman on 2008-06-30
I am using FF 3 in kubuntu 64 bit. and i have the adobe non-free flash plugin. Youtube works, but when i go to the video it always takes about 20 for the video to start up ( its not downloading ) the whole browser just frezzes. Also when i open up a tab using flash, then a second, the flash will only ever work in one tab. Also after a while i need to restart FF to get the flash working. Here is the output from a firefox session loading youtube.
> ue 01 Jul 2008 02:04:55 GMT: VERBOSE (initDailyDilbert): enter methodTue 01 Jul
 2008 02:04:55 GMT: ERROR (initDailyDilbert): dailyDilbertLogger could not be in
itiatedTue 01 Jul 2008 02:04:55 GMT: DEBUG (initDailyDilbert): dailyDilbertLocal
izer initiatedTue 01 Jul 2008 02:04:55 GMT: VERBOSE (loadDailyDilbertPreferences
): enter methodTue 01 Jul 2008 02:04:55 GMT: VERBOSE (loadDailyDilbertPreference
s): leave methodTue 01 Jul 2008 02:04:55 GMT: DEBUG (initDailyDilbert): dailyDil
bertPreferences initiatedTue 01 Jul 2008 02:04:55 GMT: INFO (initDailyDilbert):
initDailyDilbert initiatedTue 01 Jul 2008 02:04:55 GMT: VERBOSE (initDailyDilber
t): leave methodLoadPlugin: failed to initialize shared library /home/natman/.re
alplayer/mozilla/nphelix.so [/home/natman/.realplayer/mozilla/nphelix.so: wrong
ELF class: ELFCLASS32]
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloa
ded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloade
d: ignored.
GCJ PLUGIN: thread 0x6228e0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x6228e0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x6228e0: NP_GetValue
GCJ PLUGIN: thread 0x6228e0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x6228e0: NP_GetValue return
GCJ PLUGIN: thread 0x6228e0: NP_GetValue
GCJ PLUGIN: thread 0x6228e0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x6228e0: NP_GetValue return
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object HTMLDocument])
## ##  mpc_extractStreamInternal2 0ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object HTMLDocument])
## ##  mpc_extractStreamInternal2 0ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms

ColorfulTabs Log: clrtabsInit
ColorfulTabs Log: setCtPref
ColorfulTabs Log: Pref Changed: satmax
ColorfulTabs Log: Pref Changed: satmin
ColorfulTabs Log: Pref Changed: lummax
ColorfulTabs Log: Pref Changed: lummin
colorfultabs log: clrprefs- 95 30 78 68

name: ColorfulTabs
version: 3.1
cl:     chkRestore
ColorfulTabs Log:
ColorfulTabs Log: user chose to color tabs with URl scheme
ColorfulTabs Log: initTabcontext true
                appending
ctlog:  context menu is set#  pageshow
## mpc_extractStreamOnDoc (chrome://browser/content/browser.xul)
## mpc_extractStreamInternal2 (undefined, [object XULDocument])
## ##  mpc_extractStreamInternal2 1ms
*** e = [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC
_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XP
C_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/utility
Overlay.js :: getShellService :: line 307"  data: no]

ColorfulTabs Log: location changed
Tab readonly?
cl:     setColor        hsl(102,60%,73%)
cl:     fadeAllTabs## mpc_isSideBarOpen()
## window.defaultStatus =
window.menubar =[object BarProp]
window.menubar.visible  =true
window.navigator  =[object Navigator]
window.scrollbars  =[object BarProp]
window.status  =
## mpc_canOpenSideBar()
## mpc_isSideBarOpen()
## window.defaultStatus =
window.menubar =[object BarProp]
window.menubar.visible  =true
window.navigator  =[object Navigator]
window.scrollbars  =[object BarProp]
window.status  =
## mpc_canOpenSideBar()
#  pageshow
## mpc_extractStreamOnDoc ([http://news.bbc.co.uk/nol/ifs_news/hi/front_page/tick](http://news.bbc.co.uk/nol/ifs_news/hi/front_page/tick)
er.stm)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
#  pageshow
## mpc_extractStreamOnDoc ([http://news.bbc.co.uk/](http://news.bbc.co.uk/))
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_buildContextMenu()
## mpc_extractStreamInternal ([http://news.bbc.co.uk/](http://news.bbc.co.uk/), [object XPCNativeWrapper [
object Window]])
## mpc_extractStreamInternal ([http://news.bbc.co.uk/](http://news.bbc.co.uk/), [object XPCNativeWrapper [
object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms

ColorfulTabs Log: location changed
Tab readonly?
cl:     setColor        hsl(174,60%,73%)
cl:     fadeAllTabs## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [obj
ect XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal ([http://ie.youtube.com/iyt](http://ie.youtube.com/iyt), [object XPCNativeWrappe
r [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
#  pageshow
## mpc_extractStreamOnDoc ([http://ie.youtube.com/index](http://ie.youtube.com/index))
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_buildContextMenu()

ColorfulTabs Log: location changed
Tab readonly?
cl:     setColor        hsl(174,60%,73%)
cl:     fadeAllTabsERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELO
AD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloade
d: ignored.

(npviewer.bin:15709): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengin
e.so: wrong ELF class: ELFCLASS64

(npviewer.bin:15709): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengin
e.so: wrong ELF class: ELFCLASS64
## mpc_extractStreamInternal ([http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k), [object
 XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://ie.youtube.com/version-check](http://ie.youtube.com/version-check)
.swf,[http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:](http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:)
//ie.youtube.com/watch?v=W53W_zOwG4k)
## mpc_IntermediateEmbedMediaFile([http://ie.youtube.com/version-check.swf](http://ie.youtube.com/version-check.swf))
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://s.ytimg.com/yt/swf/watch-vfl](http://s.ytimg.com/yt/swf/watch-vfl)
44017.swf,[http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f](http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f)
lash,[http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_IntermediateEmbedMediaFile([http://s.ytimg.com/yt/swf/watch-vfl44017.swf](http://s.ytimg.com/yt/swf/watch-vfl44017.swf))
## ##  mpc_extractStreamInternal2 4ms
## mpc_extractStreamInternal ([http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k), [object
 XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://ie.youtube.com/version-check](http://ie.youtube.com/version-check)
.swf,[http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:](http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:)
//ie.youtube.com/watch?v=W53W_zOwG4k)
## mpc_IntermediateEmbedMediaFile([http://ie.youtube.com/version-check.swf](http://ie.youtube.com/version-check.swf))
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://s.ytimg.com/yt/swf/watch-vfl](http://s.ytimg.com/yt/swf/watch-vfl)
44017.swf,[http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f](http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f)
lash,[http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_IntermediateEmbedMediaFile([http://s.ytimg.com/yt/swf/watch-vfl44017.swf](http://s.ytimg.com/yt/swf/watch-vfl44017.swf))
## ##  mpc_extractStreamInternal2 4ms
#  pageshow
## mpc_extractStreamOnDoc ([http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://ie.youtube.com/version-check](http://ie.youtube.com/version-check)
.swf,[http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:](http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:)
//ie.youtube.com/watch?v=W53W_zOwG4k)
## mpc_IntermediateEmbedMediaFile([http://ie.youtube.com/version-check.swf](http://ie.youtube.com/version-check.swf))
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://s.ytimg.com/yt/swf/watch-vfl](http://s.ytimg.com/yt/swf/watch-vfl)
44017.swf,[http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f](http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f)
lash,[http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_IntermediateEmbedMediaFile([http://s.ytimg.com/yt/swf/watch-vfl44017.swf](http://s.ytimg.com/yt/swf/watch-vfl44017.swf))
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal ([http://ie.youtube.com/index](http://ie.youtube.com/index), [object XPCNativeWrap
per [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://ie.youtube.com/version-check](http://ie.youtube.com/version-check)
.swf,[http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:](http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:)
//ie.youtube.com/watch?v=W53W_zOwG4k)
## mpc_IntermediateEmbedMediaFile([http://ie.youtube.com/version-check.swf](http://ie.youtube.com/version-check.swf))
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://s.ytimg.com/yt/swf/watch-vfl](http://s.ytimg.com/yt/swf/watch-vfl)
44017.swf,[http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f](http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f)
lash,[http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_IntermediateEmbedMediaFile([http://s.ytimg.com/yt/swf/watch-vfl44017.swf](http://s.ytimg.com/yt/swf/watch-vfl44017.swf))
## ##  mpc_extractStreamInternal2 3ms
## mpc_extractStreamInternal ([http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k), [object
 XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://ie.youtube.com/version-check](http://ie.youtube.com/version-check)
.swf,[http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:](http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:)
//ie.youtube.com/watch?v=W53W_zOwG4k)
## mpc_IntermediateEmbedMediaFile([http://ie.youtube.com/version-check.swf](http://ie.youtube.com/version-check.swf))
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://s.ytimg.com/yt/swf/watch-vfl](http://s.ytimg.com/yt/swf/watch-vfl)
44017.swf,[http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f](http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f)
lash,[http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_IntermediateEmbedMediaFile([http://s.ytimg.com/yt/swf/watch-vfl44017.swf](http://s.ytimg.com/yt/swf/watch-vfl44017.swf))
## ##  mpc_extractStreamInternal2 2ms
## mpc_extractStreamInternal (about:document-onload-blocker, [object XPCNativeWr
apper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://ie.youtube.com/version-check](http://ie.youtube.com/version-check)
.swf,[http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:](http://ie.youtube.com/version-check.swf,application/x-shockwave-flash,http:)
//ie.youtube.com/watch?v=W53W_zOwG4k)
## mpc_IntermediateEmbedMediaFile([http://ie.youtube.com/version-check.swf](http://ie.youtube.com/version-check.swf))
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])
   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu ([http://s.ytimg.com/yt/swf/watch-vfl](http://s.ytimg.com/yt/swf/watch-vfl)
44017.swf,[http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f](http://s.ytimg.com/yt/swf/watch-vfl44017.swf,application/x-shockwave-f)
lash,[http://ie.youtube.com/watch?v=W53W_zOwG4k](http://ie.youtube.com/watch?v=W53W_zOwG4k))
## mpc_IntermediateEmbedMediaFile([http://s.ytimg.com/yt/swf/watch-vfl44017.swf](http://s.ytimg.com/yt/swf/watch-vfl44017.swf))
## ##  mpc_extractStreamInternal2 2ms
## mpc_buildContextMenu()
## mpc_buildContextMenu()
## mpc_isSideBarOpen()
## window.defaultStatus =
window.menubar =[object BarProp]
window.menubar.visible  =true
window.navigator  =[object Navigator]
window.scrollbars  =[object BarProp]
window.status  =
## mpc_canOpenSideBar()

(npviewer.bin:15709): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attac                                                                                                   h_count > 0' failed

(npviewer.bin:15709): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET                                                                                                    (widget)' failed

(npviewer.bin:15709): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WID                                                                                                   GET (widget)' failed

(npviewer.bin:15709): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET                                                                                                    (widget)' failed

(npviewer.bin:15709): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WID                                                                                                   GET (widget)' failed

(npviewer.bin:15709): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WID                                                                                                   GET (widget)' failed
natman@natman-laptop:~$


---

### Post by ninjabob7 on 2008-07-01
Have you tried disabling IPv6? [Here's a guide to disable it system-wide.]("http://ubuntuforums.org/archive/index.php/t-87798.html") There's also an about:config tweak to disable it in firefox only. If you disable IPv6, it will probably help with the slowness at least.
Also, is Firefox 32-bits or 64-bits? You can tell by running
```
file /usr/lib/firefox-3.0/firefox
```
If it is 64-bit, I would recommend getting 32-bit Swiftfox. It will save you many headaches.

---

