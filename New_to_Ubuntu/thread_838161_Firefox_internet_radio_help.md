---
title: "Firefox internet radio help"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by natman on 2008-06-23
Hi i have Realplayer installed and works fine, all i want to be able to do is play the following :
> [http://www.rte.ie/radio/liveplayer_av.html?1,null,200,http://dynamic.rte.ie/av/live/radio/radio1.smil](http://www.rte.ie/radio/liveplayer_av.html?1,null,200,http://dynamic.rte.ie/av/live/radio/radio1.smil)
I get an error message "could not find approiate hxplay or real in system path.."
What do i do?

---

### Post by y-lee on 2008-06-23
It  plays fine for me using the Mplayer plugin. So lets try insalling the Mplayer plugin, installing the restricted codecs  and  installing the Real Video codecs from the Medibuntu repo.

 **First part: real video codecs**
[LIST=1]
[*]Close Firefox
[*]Remove the plugins you will no longer be using:
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc
```
[*]Install mplayer plugin:
```
sudo apt-get install mozilla-mplayer
```
[*]Now let's make sure ubuntu-restricted-extras  are installed. Open Synaptics package manager, go to Settings > Repositories, and ensure that the lines that contain "(universe)" and "(multiverse)" are checked; if have to check them, ensure that after closing the settings window, you click on "Reload" in Synaptics main window)
```
sudo apt-get install ubuntu-restricted-extras
```[/LIST][B]
     Second part: real video codecs
[/B]     For this, we will use the medibuntu repository. We will add to the repo list, and then import their keys. *I am assuming you are using Hardy here if you are not let us know as this will not work right in earlier releases of ubuntu.*[LIST=1]
[*]Edit /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list
```
[*]Append the following lines to it:
```
## Medibuntu - Ubuntu 8.04 "hardy"
deb  http://packages.medibuntu.org/ hardy free non-free
```
[*]Import medibuntu's key and update the local package list
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
[*]Now install the codec we need:
```
sudo apt-get install non-free-codecs
```[/LIST]

Now hopefully it works :)

---

### Post by natman on 2008-06-27
( sorry about the late reply )
I did as above and it gave no errors, but still nothing when i use the link, firefox stalls and if i click "play in real play" all i get is an mplayer downlaod still nothing.

---

### Post by y-lee on 2008-06-27
Ah don't worry about the late reply. I had hoped that would do the trick but life is not always simple :confused:

Hmm start firefox in a terminal 

```
firefox
```

and go to that site and try to play the media and post any errors you get in the terminal here. If you get no errors tell me that too.

Note it may be an error other than firefox pulse audio or something like that I truthfully don't know. I am good with firefox errors but other errors I may or may not know anything about.

Good luck.

---

### Post by jp_coll2003 on 2008-06-27
this link should work. I had the same trouble with my bbc radio streaming. did not want to use realplayer and I also have 64 hardy. When you have followed the instructions and all is installed go to synaptic and dont forget to click on the firefox mplayer extension. Maybe that is all you had to do without my link as I found out much to my relief. But hey, if in doubt, do it all.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by natman on 2008-06-28
Okay "y-lee" here is the terminal output ( sorry about the extensions :) )
[HTML]natman@natman-laptop:~$ firefox
Sat 28 Jun 2008 12:56:29 GMT: VERBOSE (initDailyDilbert): enter methodSat 28 Jun
 2008 12:56:29 GMT: ERROR (initDailyDilbert): dailyDilbertLogger could not be in
itiatedSat 28 Jun 2008 12:56:29 GMT: DEBUG (initDailyDilbert): dailyDilbertLocal
izer initiatedSat 28 Jun 2008 12:56:29 GMT: VERBOSE (loadDailyDilbertPreferences
): enter methodSat 28 Jun 2008 12:56:29 GMT: VERBOSE (loadDailyDilbertPreference
s): leave methodSat 28 Jun 2008 12:56:29 GMT: DEBUG (initDailyDilbert): dailyDil
bertPreferences initiatedSat 28 Jun 2008 12:56:29 GMT: INFO (initDailyDilbert):
initDailyDilbert initiatedSat 28 Jun 2008 12:56:29 GMT: VERBOSE (initDailyDilber
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
## ##  mpc_extractStreamInternal2 1ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms

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
## mpc_extractStreamOnDoc (http://news.bbc.co.uk/nol/ifs_news/hi/front_page/tick
er.stm)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
#  pageshow
## mpc_extractStreamOnDoc (http://news.bbc.co.uk/)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_buildContextMenu()
## mpc_buildContextMenu()
## mpc_buildContextMenu()
## mpc_buildContextMenu()
## mpc_extractStreamInternal (http://news.bbc.co.uk/, [object XPCNativeWrapper [
object Window]])
## mpc_extractStreamInternal (http://news.bbc.co.uk/, [object XPCNativeWrapper [
object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_buildContextMenu()
## mpc_buildContextMenu()
## mpc_buildContextMenu()

ColorfulTabs Log: location changed
Tab readonly?
cl:     setColor        hsl(138,60%,73%)
cl:     fadeAllTabs## mpc_extractStreamInternal (http://www.rte.ie/radio/livepla
yer_av.html?1,null,200,http://dynamic.rte.ie/av/live/radio/radio1.smil, [object
XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD
ocument]])
## ##  mpc_extractStreamInternal2 2ms
#  pageshow
## mpc_extractStreamOnDoc (http://www.rte.ie/radio/liveplayer_av.html?1,null,200                                                                                                   ,http://dynamic.rte.ie/av/live/radio/radio1.smil)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD                                                                                                   ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_extractStreamInternal (http://www.rte.ie/radio/liveplayer_av.html?1,null,                                                                                                   200,http://dynamic.rte.ie/av/live/radio/radio1.smil, [object XPCNativeWrapper [o                                                                                                   bject Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLD                                                                                                   ocument]])
## ##  mpc_extractStreamInternal2 0ms
## mpc_buildContextMenu()
## mpc_isSideBarOpen()
## window.defaultStatus =
window.menubar =[object BarProp]
window.menubar.visible  =true
window.navigator  =[object Navigator]
window.scrollbars  =[object BarProp]
window.status  =
## mpc_canOpenSideBar()
natman@natman-laptop:~$

[/HTML]
I also tried the other suggested solution and nothing, now when i click the radio link it tells me i need to install real ( im using it right now to listen stand alone )

---

### Post by Oddvar on 2009-11-25
This worked for me and my Ubuntu 9.10. First instruction from y-lee  
Every version of Ubuntu have problem with internet radio and my favourite channel Beatlesarama.com. Takes many hours of investigation and  Google

---

