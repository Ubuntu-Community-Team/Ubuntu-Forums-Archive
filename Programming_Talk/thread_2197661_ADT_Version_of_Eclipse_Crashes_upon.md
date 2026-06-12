---
title: "ADT Version of Eclipse Crashes upon"
date: 2014-01-04
forum: Programming Talk
---

### Post by jspike397 on 2014-01-04
Hello,

I hope that I have placed this in the correct forum, and moderators are free to move this thread if there is a more appropriate location for it.  

I have been trying to use the Android SDK for the past week or so.  However, I am having a issue, with Eclipse crashing unexpected.   It happens every time I view the predictions/correction area that is created by creating a "." in eclipse or netbeans.  I use this a lot to correct spelling of methods and such, so I would really like this to work.  Here is the terminal output of the application: 
 ```

(joshn@joshn-Vaio: ~)$ /home/joshn/Linux/adt-bundle-linux-x86_64-20130729/eclipse/eclipse     
No bp log location saved, using default.
[000:000] Cpu: 20.2.0, x2, 1750Mhz, 11582MB
[000:000] Computer model: Not available
[000:000] Browser XEmbed support present: 1
[000:001] Browser toolkit is Gtk2.
[000:001] Using Gtk2 toolkit
[000:090] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:090] No bp log location saved, using default.
[000:091] Cpu: 20.2.0, x2, 1750Mhz, 11582MB
[000:092] Computer model: Not available
[000:092] Browser XEmbed support present: 1
[000:092] Browser toolkit is Gtk2.
[000:093] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Cpu: 20.2.0, x2, 1750Mhz, 11582MB
[000:001] Computer model: Not available
[PIPELIGHT:LIN:unknown] attached to process.
[PIPELIGHT:LIN:unknown] checking environment variable PIPELIGHT_SILVERLIGHT5_1_CONFIG.
[PIPELIGHT:LIN:unknown] searching for config file pipelight-silverlight5.1.
[PIPELIGHT:LIN:unknown] trying to load config file from '/home/joshn/.config/pipelight-silverlight5.1'.
[PIPELIGHT:LIN:unknown] trying to load config file from '/etc/pipelight-silverlight5.1'.
[PIPELIGHT:LIN:unknown] trying to load config file from '/usr/share/pipelight/pipelight-silverlight5.1'.
[PIPELIGHT:LIN:silverlight5.1] sandbox not found / not installed!
[PIPELIGHT:LIN:silverlight5.1] basicplugin.c:438:checkSilverlightGraphicDriver(): GPU driver check - Your driver is not in the whitelist, hardware acceleration disabled.
[PIPELIGHT:LIN:silverlight5.1] using wine prefix directory /home/joshn/.wine-pipelight/.
[PIPELIGHT:LIN:silverlight5.1] checking plugin installation - this might take some time.
[install-dependency] wine-silverlight5.1-installer is already installed in '/home/joshn/.wine-pipelight/'.
[install-dependency] wine-mpg2splt-installer is already installed in '/home/joshn/.wine-pipelight/'.
[install-dependency] wine-wininet-installer is already installed in '/home/joshn/.wine-pipelight/'.
[PIPELIGHT:WIN:silverlight5.1] windowless mode       is off.
[PIPELIGHT:WIN:silverlight5.1] embedded mode         is on.
[PIPELIGHT:WIN:silverlight5.1] unity hacks           is off.
[PIPELIGHT:WIN:silverlight5.1] window class hook     is on.
[PIPELIGHT:WIN:silverlight5.1] render toplevelwindow is off.
[PIPELIGHT:WIN:silverlight5.1] replaced API function CreateWindowExA.
[PIPELIGHT:WIN:silverlight5.1] replaced API function CreateWindowExW.
[PIPELIGHT:WIN:silverlight5.1] replaced API function TrackPopupMenuEx.
[PIPELIGHT:WIN:silverlight5.1] replaced API function TrackPopupMenu.
fixme:advapi:RegisterTraceGuidsW (0x2b1f87, 0x350118, {aa087e0e-0b35-4e28-8f3a-440c3f51eef1}, 1, 0x66f5f8, (null), (null), 0x350118): stub
[PIPELIGHT:WIN:silverlight5.1] init successful!
[PIPELIGHT:LIN:silverlight5.1] using thread asynccall event handling.
[001:887] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[001:887] No bp log location saved, using default.
[001:889] Cpu: 20.2.0, x2, 1750Mhz, 11582MB
[001:889] Computer model: Not available
(joshn@joshn-Vaio: ~)$ fixme:advapi:UnregisterTraceGuids 0: stub


(joshn@joshn-Vaio: ~)$ 



```

Also, if someone knows why there is pipelight logs in the output of eclipse, I would be very interested.  

Thank you in advance for your help.

---

### Post by jspike397 on 2014-02-05
I solved it.  The answer was on stackoverflow, at [http://stackoverflow.com/questions/16383992/why-does-my-eclipse-indigo-crash-on-ubuntu-13-04-with-oracle-jdk-64bit](http://stackoverflow.com/questions/16383992/why-does-my-eclipse-indigo-crash-on-ubuntu-13-04-with-oracle-jdk-64bit).

---

