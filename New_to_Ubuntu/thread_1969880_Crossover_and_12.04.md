---
title: "Crossover and 12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-04-30
I use FL studio and run it in cross over. It works fine on my mac and it worked fine on 11.10. I did a fresh install of 12.04 and now it is freezing up at the end of the installation. here is the debug log. Please help. I am extremely dependant on this program.



***```
** Mon Apr 30 16:49:56 2012
Starting: '/opt/cxoffice/bin/cxbottle' '--bottle' 'flstudio_10' '--create' '--template' 'winxp' '--install'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
5675: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5675: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Running '/opt/cxoffice/share/crossover/bottle_templates/winxp/setup' '--create'


***** Mon Apr 30 16:49:56 2012
Starting: '/opt/cxoffice/share/crossover/bottle_templates/winxp/setup' '--create'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
CXRWConfig->new(/opt/cxoffice/share/crossover/bottle_data/cxbottle.conf)
system encoding='UTF-8'
CXRWConfig->write(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
Running '/opt/cxoffice/bin/wine' '--wl-app' 'rundll32.exe' '--no-quotes' '--scope' 'private' '--winver' 'winxp' '--dll' 'advpack=b;atl=b;oleaut32=b;rpcrt4=b;shdocvw=b;*iexplore.exe=b' 'setupapi.dll,InstallHinfSection' 'DefaultInstall' '128' '/opt/cxoffice/share/crossover/bottle_data/crossover.inf'


***** Mon Apr 30 16:49:57 2012
Starting: '/opt/cxoffice/bin/wine' '--wl-app' 'rundll32.exe' '--no-quotes' '--scope' 'private' '--winver' 'winxp' '--dll' 'advpack=b;atl=b;oleaut32=b;rpcrt4=b;shdocvw=b;*iexplore.exe=b' 'setupapi.dll,InstallHinfSection' 'DefaultInstall' '128' '/opt/cxoffice/share/crossover/bottle_data/crossover.inf'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
Product version=11.0.3.26035
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
Mode = 'private'
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
Environment:
  CX_ROOT = "/opt/cxoffice"
  CX_BOTTLE = "flstudio_10"
  WINEPREFIX = "/home/dylan/.cxoffice/flstudio_10"
  CX_WINDOWS_VERSION = "winxp"
  PATH = "/opt/cxoffice/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/opt/cxoffice/lib"
  WINEDLLPATH = "/opt/cxoffice/lib/wine"
  WINEDLLOVERRIDES = "advpack=b;atl=b;oleaut32=b;rpcrt4=b;shdocvw=b;*iexplore.exe=b"
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/opt/cxoffice/bin/wineloader"
  WINESERVER = "/opt/cxoffice/bin/wineserver"
  WINEDEBUG = "+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/dylan/.cxoffice/desktopdata/com.codeweavers.unknown.5270.log.fifo"
  CX_DEBUGMSG = "+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = "/home/dylan/.cxoffice/usage.log"
  DISPLAY = ":0"
Command:
/opt/cxoffice/bin/wineloader winewrapper.exe --no-quotes --run -- /opt/cxoffice/lib/wine/rundll32.exe.so setupapi.dll,InstallHinfSection DefaultInstall 128 /opt/cxoffice/share/crossover/bottle_data/crossover.inf

** Mon Apr 30 16:49:57 2012
Starting '/opt/cxoffice/bin/wineloader' 'winewrapper.exe' '--no-quotes' '--run' '--'
'/opt/cxoffice/lib/wine/rundll32.exe.so' 'setupapi.dll,InstallHinfSection' 'DefaultInstall' '128' '/opt/cxoffice/share/crossover/bottle_data/crossover.inf'

err:module:load_builtin_dll failed to load .so lib for builtin L"winemp3.acm": libmpg123.so.0: cannot open shared object file: No such file or directory
-> rc=0  (took 4.08893990516663 seconds)
Piping into "/opt/cxoffice/bin/wine" --scope private --wl-app regedit.exe -


***** Mon Apr 30 16:50:01 2012
Starting: '/opt/cxoffice/bin/wine' '--scope' 'private' '--wl-app' 'regedit.exe' '-'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
Product version=11.0.3.26035
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
Mode = 'private'
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
Environment:
  CX_ROOT = "/opt/cxoffice"
  CX_BOTTLE = "flstudio_10"
  WINEPREFIX = "/home/dylan/.cxoffice/flstudio_10"
  CX_WINDOWS_VERSION = <undefined>
  PATH = "/opt/cxoffice/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/opt/cxoffice/lib"
  WINEDLLPATH = "/opt/cxoffice/lib/wine"
  WINEDLLOVERRIDES = <undefined>
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/opt/cxoffice/bin/wineloader"
  WINESERVER = "/opt/cxoffice/bin/wineserver"
  WINEDEBUG = "+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/dylan/.cxoffice/desktopdata/com.codeweavers.unknown.5270.log.fifo"
  CX_DEBUGMSG = "+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = "/home/dylan/.cxoffice/usage.log"
  DISPLAY = ":0"
Command:
/opt/cxoffice/bin/wineloader winewrapper.exe --run -- /opt/cxoffice/lib/wine/regedit.exe.so -

** Mon Apr 30 16:50:01 2012
Starting '/opt/cxoffice/bin/wineloader' 'winewrapper.exe' '--run' '--'
'/opt/cxoffice/lib/wine/regedit.exe.so' '-'

-> rc=0  (took 0.347716093063354 seconds)
-> rc=0  (took 4.48870182037354 seconds)
5675: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5675: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5675: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
5675: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
Running '/opt/cxoffice/bin/cxmenu' '--install' '--scope' 'private'


***** Mon Apr 30 16:50:01 2012
Starting: '/opt/cxoffice/bin/cxmenu' '--install' '--scope' 'private'

-> rc=0  (took 0.0538399219512939 seconds)
Running '/opt/cxoffice/bin/cxassoc' '--install' '--scope' 'private'


***** Mon Apr 30 16:50:01 2012
Starting: '/opt/cxoffice/bin/cxassoc' '--install' '--scope' 'private'

-> rc=0  (took 0.072490930557251 seconds)
Running '/opt/cxoffice/bin/cxnsplugin' '--install' '--scope' 'private'


***** Mon Apr 30 16:50:01 2012
Starting: '/opt/cxoffice/bin/cxnsplugin' '--install' '--scope' 'private'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
5730: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5730: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
5730: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5730: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5730: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
5730: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
5730: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5730: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXRWConfig->new(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
CXRWConfig->write(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
5730: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Template plugin library for architecture 'PrivateLinuxNSPluginDirs': '/opt/cxoffice/lib/nsplugin-linux.so'
'/home/dylan/.cxoffice/flstudio_10/cxnsplugin.conf' not modified -> no need to save
-> rc=0  (took 0.0661218166351318 seconds)


***** Mon Apr 30 16:50:01 2012
Starting: '/opt/cxoffice/bin/cxassoc' '--bottle' 'flstudio_10' '--sync'



***** Mon Apr 30 16:50:01 2012
Starting: '/opt/cxoffice/bin/wine' '--no-convert' '--wl-app' 'assocscan.exe' '--scan' '--icon-dir' '/home/dylan/.cxoffice/flstudio_10/windata/Associations'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
Product version=11.0.3.26035
5735: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5735: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
Mode = 'private'
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
Environment:
  CX_ROOT = "/opt/cxoffice"
  CX_BOTTLE = "flstudio_10"
  WINEPREFIX = "/home/dylan/.cxoffice/flstudio_10"
  CX_WINDOWS_VERSION = <undefined>
  PATH = "/opt/cxoffice/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/opt/cxoffice/lib"
  WINEDLLPATH = "/opt/cxoffice/lib/wine"
  WINEDLLOVERRIDES = <undefined>
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/opt/cxoffice/bin/wineloader"
  WINESERVER = "/opt/cxoffice/bin/wineserver"
  WINEDEBUG = "+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/dylan/.cxoffice/desktopdata/com.codeweavers.unknown.5270.log.fifo"
  CX_DEBUGMSG = "+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = "/home/dylan/.cxoffice/usage.log"
  DISPLAY = ":0"
5735: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Command:
/opt/cxoffice/bin/wineloader winewrapper.exe --no-convert --run -- /opt/cxoffice/lib/wine/assocscan.exe.so --scan --icon-dir /home/dylan/.cxoffice/flstudio_10/windata/Associations

** Mon Apr 30 16:50:01 2012
Starting '/opt/cxoffice/bin/wineloader' 'winewrapper.exe' '--no-convert' '--run' '--'
'/opt/cxoffice/lib/wine/assocscan.exe.so' '--scan' '--icon-dir' '/home/dylan/.cxoffice/flstudio_10/windata/Associations'



***** Mon Apr 30 16:50:02 2012
Starting: '/opt/cxoffice/bin/wine' '--bottle' 'flstudio_10' '--untrusted' '--wait-children' '--no-convert' '--' 'Y:\Downloads\flstudio_10.0.9c.exe'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
Product version=11.0.3.26035
5745: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5745: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
Mode = 'private'
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
Environment:
  CX_ROOT = "/opt/cxoffice"
  CX_BOTTLE = "flstudio_10"
  WINEPREFIX = "/home/dylan/.cxoffice/flstudio_10"
  CX_WINDOWS_VERSION = <undefined>
  PATH = "/opt/cxoffice/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/opt/cxoffice/lib"
  WINEDLLPATH = "/opt/cxoffice/lib/wine"
  WINEDLLOVERRIDES = <undefined>
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/opt/cxoffice/bin/wineloader"
  WINESERVER = "/opt/cxoffice/bin/wineserver"
  WINEDEBUG = "+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/dylan/.cxoffice/desktopdata/com.codeweavers.unknown.5270.log.fifo"
  CX_DEBUGMSG = "+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = "/home/dylan/.cxoffice/usage.log"
  DISPLAY = ":0"
5745: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Command:
/opt/cxoffice/bin/wineloader winewrapper.exe --wait-children --no-convert --run -- Y:\Downloads\flstudio_10.0.9c.exe

** Mon Apr 30 16:50:02 2012
Starting '/opt/cxoffice/bin/wineloader' 'winewrapper.exe' '--wait-children' '--no-convert' '--run' '--'
'Y:\Downloads\flstudio_10.0.9c.exe'

fixme:process:GetLogicalProcessorInformation ((nil),0x33f7f4): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Image-Line\\Shared" 1 4 (nil) (nil) 0x140520 (nil)
fixme:process:GetLogicalProcessorInformation ((nil),0x33f7fc): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33f7fc): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33f7fc): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33f7fc): stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:vbscript:p****_script parser failed on parsing L"\r\n    case HKEY_CLASSES_ROOT\r\n        key = \"HKEY_CLASSES_ROOT\"\r\n    Case HKEY_CURRENT_USER\r\n        key = \"HKEY_CURRENT_USER\"\r\n    Case HKEY_LOCAL_MACHINE\r\n        key = \"HKEY_LOCAL_MACHINE\"\r\n    Case HKEY_USERS\r\n        key = \"HKEY_USERS\"\r\n    Case HKEY_CURRENT_CONFIG\r\n "...
fixme:vbscript:p****_script parser failed on parsing L"\r\n    case HKEY_CLASSES_ROOT\r\n        key = \"HKEY_CLASSES_ROOT\"\r\n    Case HKEY_CURRENT_USER\r\n        key = \"HKEY_CURRENT_USER\"\r\n    Case HKEY_LOCAL_MACHINE\r\n        key = \"HKEY_LOCAL_MACHINE\"\r\n    Case HKEY_USERS\r\n        key = \"HKEY_USERS\"\r\n    Case HKEY_CURRENT_CONFIG\r\n "...
fixme:shell:SHAutoComplete stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33e3b4): stub
fixme:shell:SHAutoComplete stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33e580): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33e580): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x33e3b4): stub
fixme:process:GetLogicalProcessorInformation ((nil),0x134e55c): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Image-Line\\FL Studio 10" 1 4 (nil) (nil) 0x15e1f8 (nil)
fixme:process:GetLogicalProcessorInformation ((nil),0x134e55c): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Outsim\\SynthMaker" 1 4 (nil) (nil) 0x1f5fb70 (nil)
err:module:load_builtin_dll failed to load .so lib for builtin L"winemp3.acm": libmpg123.so.0: cannot open shared object file: No such file or directory
err:seh:setup_exception_record stack overflow 832 bytes in thread 0012 eip b75d2a27 esp 00240ff0 stack 0x240000-0x241000-0x340000
err:seh:setup_exception_record stack overflow 832 bytes in thread 0013 eip b75dfa27 esp 01250ff0 stack 0x1250000-0x1251000-0x1350000


***** Mon Apr 30 16:54:46 2012
Starting: '/opt/cxoffice/bin/wine' '--bottle' 'flstudio_10' '--wait-children' '--wl-app' 'reboot.exe'

CXConfig->read(/opt/cxoffice/etc/cxoffice.conf)
CXConfig->read(/home/dylan/.cxoffice/cxoffice.conf)
Product version=11.0.3.26035
5789: Grabbing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
5789: Got the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
CXConfig->read(/home/dylan/.cxoffice/flstudio_10/cxbottle.conf)
Mode = 'private'
Bottle environment variables:
 PULSE_LATENCY_MSEC -> 20
Environment:
  CX_ROOT = "/opt/cxoffice"
  CX_BOTTLE = "flstudio_10"
  WINEPREFIX = "/home/dylan/.cxoffice/flstudio_10"
  CX_WINDOWS_VERSION = <undefined>
  PATH = "/opt/cxoffice/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
  LD_LIBRARY_PATH = "/opt/cxoffice/lib"
  WINEDLLPATH = "/opt/cxoffice/lib/wine"
  WINEDLLOVERRIDES = <undefined>
  LD_PRELOAD = ""
  LD_ASSUME_KERNEL = <undefined>
  WINELOADER = "/opt/cxoffice/bin/wineloader"
  WINESERVER = "/opt/cxoffice/bin/wineserver"
  WINEDEBUG = "+cxreboot,-cxassoc,-cxmenu"
  CX_LOG = "/home/dylan/.cxoffice/desktopdata/com.codeweavers.unknown.5270.log.fifo"
  CX_DEBUGMSG = "+cxreboot,-cxassoc,-cxmenu"
  CX_WINE_USAGE_LOGFILE = "/home/dylan/.cxoffice/usage.log"
  DISPLAY = ":0"
5789: Releasing the '/tmp/.wine-1000/bottle-801-f00169.lock' lock
Command:
/opt/cxoffice/bin/wineloader winewrapper.exe --wait-children --run -- /opt/cxoffice/lib/wine/reboot.exe.so

** Mon Apr 30 16:54:46 2012
Starting '/opt/cxoffice/bin/wineloader' 'winewrapper.exe' '--wait-children' '--run' '--'
'/opt/cxoffice/lib/wine/reboot.exe.so'

trace:cxreboot:Process_WininitIni Processing Wininit.ini file
trace:cxreboot:Process_WininitIni renaming wininit.ini file
trace:cxreboot:Process_PendingFileRenameOperations Deleting L"\\??\\C:\\users\\crossover\\Temp\\nsm2ffc.tmp\\OpenCandy_Why_Is_This_Here.txt"
err:cxreboot:Process_PendingFileRenameOperations Failed to delete L"\\??\\C:\\users\\crossover\\Temp\\nsm2ffc.tmp\\OpenCandy_Why_Is_This_Here.txt"
trace:cxreboot:Process_PendingFileRenameOperations Deleting L"\\??\\C:\\users\\crossover\\Temp\\nsm2ffc.tmp\\OCSetupHlp.dll"
```

---

### Post by Enigmapond on 2012-04-30
You could just save yourself the head trauma and just install the Ubuntustudio-audio apps. I use them on a daily basis and really, in my opinion are much better than FL. I use them professionally with only positive things. The LADSPA plugins, (Like VST), are exceptional and are really on par now with Waves VST's. I use to say I was totally dependant on Cubase and Adobe Audition but not anymore. If you do it make sure you update the KXStudio PPA's listed in this forum for bleeding edge things and it's very well managed.

---

### Post by TheMTtakeover on 2012-04-30
> **Enigmapond said:**
> You could just save yourself the head trauma and just install the Ubuntustudio-audio apps. I use them on a daily basis and really, in my opinion are much better than FL. I use them professionally with only positive things. The LADSPA plugins, (Like VST), are exceptional and are really on par now with Waves VST's. I use to say I was totally dependant on Cubase and Adobe Audition but not anymore. If you do it make sure you update the KXStudio PPA's listed in this forum for bleeding edge things and it's very well managed.

Thanks, but I'd rather stick with FL. I enjoy using it with people and don't feel like bringing a new item to the table. If it help anyone that same thing happens using wine. (i know crossover is wine) but running and crossover and running in wine end up in the same result

---

### Post by Cheesemill on 2012-04-30
I was going to say why don't you ask the Crossover people, you do pay for support after all.

I'm guessing you're Dylan on their forums though :)

---

### Post by TheMTtakeover on 2012-04-30
Haha, Indeed I am. I posted there and thought well the Ubuntu forums has a larger user base I'll see if they know anything. It's not a big deal to switch back to 11.10 but I worry about when support for that is up if this will still be an issue or not.

---

### Post by TheMTtakeover on 2012-04-30
Sorry to bump this but does anyone think if I install it on 11.10 and then upgrade to 12.04 it will work properly?

---

### Post by tp0x45 on 2012-05-13
On 64-bit Ubuntu 12.04, I needed to add libjpeg62 prior to CrossOver installation. In terminal:
sudo apt-get install libjpeg62

Then I ran:
sudo dpkg -i ia32-crossover_11.0.3-1_amd64.deb

with the package I downloaded from CodeWeavers website.

Now CrossOver installation went through and I got the CrossOver icons in Applications.

I hope this helps.

---

