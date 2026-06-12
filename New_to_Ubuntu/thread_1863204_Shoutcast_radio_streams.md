---
title: "Shoutcast radio streams"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by fractalman on 2011-10-17
Does anybody know if there is a fix for the banshee-radio fetcher plugin to get it to receive shoutcast streams?   mines only recieving xiph streams at the mo,  ive tried everything a good hunt on google has thrown up but still no luck.  im on 11.10

---

### Post by wesleybishop on 2011-10-17
check this out. [http://banshee.fm/download/extensions/](http://banshee.fm/download/extensions/)

---

### Post by fractalman on 2011-10-18
Thanks Wesleybishop, i have already tried installing the radio-fetcher plugin but i can only get xiph radio stations with it, ive tried the medibuntu repos too but i cant get shoutcast streams through banshee/streamtuner/audacious or radiotray.  if i log onto the shoutcast website  i can stream a few through the pop out player in my browser so obviously i can receive the streams.  

 I'm guessing i must have a missing package so does anybody know if there are any extra packages i might have missed?

have shoutcast changed anything at their end recently that prevents open source from receiving their streams? 

Any ideas will be much appreciated

thanks

---

### Post by fractalman on 2011-10-18
Well ive still had no luck, if i try using the shoutcast/xiph plugin i can only get xiph stations, if i go on the shoutcast site i can stream a handful of sites in the pop  out player.

if i try by entering the url manually in banshee it wont connect and i get the following output when run from a terminlal


```
phi@COLIN:~$ banshee
[Info  20:55:04.984] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Info  20:55:08.032] Updating web proxy from GConf
[Info  20:55:08.116] All services are started 2.803025
[Info  20:55:09.430] nereid Client Started
[Info  20:55:09.562] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Warn  20:55:59.277] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0

** (Banshee:3010): WARNING **: _wapi_connect: error looking up socket handle 0x1a
[Warn  20:56:13.754]  - Colifm (on Colifm) <00:00:00> [<unknown>] - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Playlists.Formats.PlaylistParser.Parse (Hyena.SafeUri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUri (System.String uri) [0x00000] in <filename unknown>:0 
[Warn  20:56:43.765]  - Colifm (on Colifm) <00:00:00> [<unknown>] - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Playlists.Formats.PlaylistParser.Parse (Hyena.SafeUri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUri (System.String uri) [0x00000] in <filename unknown>:0 
[Warn  20:57:13.514]  - Colifm (on Colifm) <00:00:00> [<unknown>] - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Playlists.Formats.PlaylistParser.Parse (Hyena.SafeUri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUri (System.String uri) [0x00000] in <filename unknown>:0 
[Warn  20:57:39.631]  - Colifm (on Colifm) <00:00:00> [<unknown>] - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] in <filename unknown>:0 
  at Banshee.Playlists.Formats.PlaylistParser.Parse (Hyena.SafeUri uri) [0x00000] in <filename unknown>:0 
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUri (System.String uri) [0x00000] in <filename unknown>:0 
*** glibc detected *** banshee: double free or corruption (!prev): 0x0a425e10 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6b961)[0x19d961]
/lib/i386-linux-gnu/libc.so.6(+0x6d28b)[0x19f28b]
/lib/i386-linux-gnu/libc.so.6(cfree+0x6d)[0x1a241d]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x36)[0xb3ec86]
/usr/lib/libgdk-x11-2.0.so.0(+0x2b65f)[0xcd065f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_union+0xa4)[0xcd0ef4]
/usr/lib/libgdk-x11-2.0.so.0(+0x3574c)[0xcda74c]
/usr/lib/libgdk-x11-2.0.so.0(+0x35a02)[0xcdaa02]
/usr/lib/libgtk-x11-2.0.so.0(+0x26b03b)[0x177d03b]
/usr/lib/libgtk-x11-2.0.so.0(+0x27131f)[0x178331f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_resize+0x7b)[0x17833bb]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x88)[0x901088]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xacc7)[0x8e2cc7]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x192)[0x8e4372]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x1e7b6)[0x8f67b6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x7a9)[0x8ffb29]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x32)[0x8ffcc2]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_remove+0xf1)[0x15bad71]
/usr/lib/libgtk-x11-2.0.so.0(+0x2732fd)[0x17852fd]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_run_dispose+0x7f)[0x8e7bff]
/usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e)[0x1673e7e]
/usr/lib/libgtk-x11-2.0.so.0(+0x21664c)[0x172864c]
/usr/lib/libgtk-x11-2.0.so.0(+0x217202)[0x1729202]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__PARAM+0x88)[0x900e48]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xacc7)[0x8e2cc7]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x192)[0x8e4372]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x1e7b6)[0x8f67b6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x7a9)[0x8ffb29]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x32)[0x8ffcc2]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xe0e1)[0x8e60e1]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xd3ef)[0x8e53ef]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_notify+0x549)[0x8e8379]
/usr/lib/libgtk-x11-2.0.so.0(gtk_tool_button_set_stock_id+0xb3)[0x17298f3]
/usr/lib/libgtk-x11-2.0.so.0(+0x626d6)[0x15746d6]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__PARAM+0x88)[0x900e48]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x192)[0x8e4372]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x1f048)[0x8f7048]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x7a9)[0x8ffb29]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x32)[0x8ffcc2]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xe0e1)[0x8e60e1]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xd3ef)[0x8e53ef]
/usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_set_property+0x831)[0x8ec3d1]
[0x132465d]
[0x132456f]
[0x1326947]
[0x2520fcf]
[0x2520a3f]
[0x2520918]
[0x24889d0]
[0x6a2fa19]
[0x5b436ab]
[0x5b43644]
[0x5b48697]
[0x5b4822e]
[0x5b48089]
[0x6fb0bf]
banshee[0x8062bc8]
banshee(mono_runtime_invoke+0x3e)[0x8192eee]
banshee(mono_runtime_invoke_array+0x2a0)[0x81967a0]
banshee[0x8198d1e]
banshee[0x81c3ff3]
banshee[0x81c4b67]
banshee[0x81c3da4]
======= Memory map: ========
00010000-000ed000 rwxp 00000000 00:00 0 
00110000-00117000 r-xp 00000000 08:41 1835910    /lib/i386-linux-gnu/librt-2.13.so
00117000-00118000 r-xp 00006000 08:41 1835910    /lib/i386-linux-gnu/librt-2.13.so
00118000-00119000 rwxp 00007000 08:41 1835910    /lib/i386-linux-gnu/librt-2.13.so
00119000-0012e000 r-xp 00000000 08:41 1835906    /lib/i386-linux-gnu/libpthread-2.13.so
0012e000-0012f000 r-xp 00015000 08:41 1835906    /lib/i386-linux-gnu/libpthread-2.13.so
0012f000-00130000 rwxp 00016000 08:41 1835906    /lib/i386-linux-gnu/libpthread-2.13.so
00130000-00132000 rwxp 00000000 00:00 0 
00132000-0028c000 r-xp 00000000 08:41 1835841    /lib/i386-linux-gnu/libc-2.13.so
0028c000-0028d000 ---p 0015a000 08:41 1835841    /lib/i386-linux-gnu/libc-2.13.so
0028d000-0028f000 r-xp 0015a000 08:41 1835841    /lib/i386-linux-gnu/libc-2.13.so
0028f000-00290000 rwxp 0015c000 08:41 1835841    /lib/i386-linux-gnu/libc-2.13.so
00290000-00293000 rwxp 00000000 00:00 0 
00293000-002d0000 r-xp 00000000 08:41 1835903    /lib/i386-linux-gnu/libpcre.so.3.12.1
002d0000-002d1000 r-xp 0003c000 08:41 1835903    /lib/i386-linux-gnu/libpcre.so.3.12.1
002d1000-002d2000 rwxp 0003d000 08:41 1835903    /lib/i386-linux-gnu/libpcre.so.3.12.1
002d2000-002d3000 rwxp 00000000 00:00 0 
002d3000-002d4000 rwxs 00000000 00:10 24580      /dev/shm/mono.3010
002d4000-002d8000 r-xp 00000000 08:41 4467846    /usr/lib/banshee/Banshee.exe
002d8000-002d9000 r-xp 00000000 08:41 674116     /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
002d9000-002e3000 r-xp 00000000 08:41 1835887    /lib/i386-linux-gnu/libnss_files-2.13.so
002e3000-002e4000 r-xp 00009000 08:41 1835887    /lib/i386-linux-gnu/libnss_files-2.13.so
002e4000-002e5000 rwxp 0000a000 08:41 1835887    /lib/i386-linux-gnu/libnss_files-2.13.so
002e5000-002f7000 r-xp 00000000 08:41 1874       /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll
002f7000-002f8000 r-xp 00000000 08:41 665884     /usr/share/locale-langpack/en_GB/LC_MESSAGES/atk10.mo
002f8000-002f9000 r-xp 00000000 00:00 0          [vdso]
002f9000-004f9000 r-xp 00000000 08:41 4464338    /usr/lib/locale/locale-archive
004f9000-00529000 r-xp 00000000 08:41 4464472    /usr/lib/banshee/Hyena.dll
00529000-00556000 r-xp 00000000 08:41 1868       /usr/lib/mono/gac/Mono.Posix/2.0.0.0__0738eb9f132ed756/Mono.Posix.dll
00556000-00558000 r-xp 00000000 08:41 4463281    /usr/lib/i386-linux-gnu/gconv/UTF-16.so
00558000-00559000 r-xp 00001000 08:41 4463281    /usr/lib/i386-linux-gnu/gconv/UTF-16.so
00559000-0055a000 rwxp 00002000 08:41 4463281    /usr/lib/i386-linux-gnu/gconv/UTF-16.so
0055a000-0055c000 r-xp 00000000 08:41 4462888    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
0055c000-0055d000 r-xp 00002000 08:41 4462888    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
0055d000-0055e000 rwxp 00003000 08:41 4462888    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.2800.6
0055e000-00567000 r-xp 00000000 08:41 1835891    /lib/i386-linux-gnu/libnss_nis-2.13.so
00567000-00568000 r-xp 00008000 08:41 1835891    /lib/i386-linux-gnu/libnss_nis-2.13.so
00568000-00569000 rwxp 00009000 08:41 1835891    /lib/i386-linux-gnu/libnss_nis-2.13.so
00569000-005ed000 r-xp 00000000 08:41 4465150    /usr/lib/banshee/Banshee.Services.dll
005ed000-00604000 r-xp 00000000 08:41 4460086    /usr/lib/libMonoPosixHelper.so
00604000-00605000 r-xp 00016000 08:41 4460086    /usr/lib/libMonoPosixHelper.so
00605000-00606000 rwxp 00017000 08:41 4460086    /usr/lib/libMonoPosixHelper.so
00606000-00608000 r-xp 00000000 08:41 4462839    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
00608000-00609000 r-xp 00001000 08:41 4462839    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
00609000-0060a000 rwxp 00002000 08:41 4462839    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
0060a000-0060c000 r-xp 00000000 08:41 665932     /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
0060c000-0060d000 r-xs 00000000 08:41 138721     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
0060d000-0062d000 rwxp 00000000 00:00 0 
0062d000-00635000 r-xp 00000000 08:41 4462843    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00635000-00636000 r-xp 00007000 08:41 4462843    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00636000-00637000 rwxp 00008000 08:41 4462843    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
00637000-00638000 r-xp 00000000 00:00 0 
00638000-0064b000 r-xp 00000000 08:41 1835924    /lib/i386-linux-gnu/libz.so.1.2.3.4
0064b000-0064c000 r-xp 00012000 08:41 1835924    /lib/i386-linux-gnu/libz.so.1.2.3.4
0064c000-0064d000 rwxp 00013000 08:41 1835924    /lib/i386-linux-gnu/libz.so.1.2.3.4
0064d000-006a9000 r-xp 00000000 08:41 4465154    /usr/lib/banshee/Banshee.ThickClient.dll
006a9000-006aa000 r-xs 00000000 08:41 140981     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
006aa000-006c0000 r-xp 00000000 08:41 1927       /usr/lib/mono/gac/glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll
006c0000-006d0000 rwxp 00000000 00:00 0 
006d0000-006d3000 r-xp 00000000 08:41 4461530    /usr/lib/cli/glib-sharp-2.0/libglibsharpglue-2.so
006d3000-006d4000 r-xp 00002000 08:41 4461530    /usr/lib/cli/glib-sharp-2.0/libglibsharpglue-2.so
006d4000-006d5000 rwxp 00003000 08:41 4461530    /usr/lib/cli/glib-sharp-2.0/libglibsharpglue-2.so
006d5000-006d7000 r-xp 00000000 08:41 4460087    /usr/lib/libMonoSupportW.so
006d7000-006d8000 r-xp 00001000 08:41 4460087    /usr/lib/libMonoSupportW.so
006d8000-006d9000 rwxp 00002000 08:41 4460087    /usr/lib/libMonoSupportW.so
006d9000-006dd000 r-xp 00000000 08:41 665984     /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
006dd000-006e1000 r-xp 00000000 08:41 1913       /usr/lib/mono/gac/gconf-sharp/2.24.0.0__35e10195dab3c99f/gconf-sharp.dll
006e1000-006eb000 r-xp 00000000 08:41 4462932    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
006eb000-006ec000 r-xp 00009000 08:41 4462932    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
006ec000-006ed000 rwxp 0000a000 08:41 4462932    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2800.4
006ed000-006f3000 r-xp 00000000 08:41 4462841    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
006f3000-006f4000 r-xp 00005000 08:41 4462841    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
006f4000-006f5000 rwxp 00006000 08:41 4462841    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
006f5000-006f9000 r-xp 00000000 08:41 4462833    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
006f9000-006fa000 r-xp 00003000 08:41 4462833    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
006fa000-006fb000 rwxp 00004000 08:41 4462833    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
006fb000-0070b000 rwxp 00000000 00:00 0 
0070b000-00738000 r-xp 00000000 08:41 1910       /usr/lib/mono/gac/atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll
00738000-0073a000 r-xp 00000000 08:41 4462967    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
0073a000-0073b000 r-xp 00001000 08:41 4462967    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
0073b000-0073c000 rwxp 00002000 08:41 4462967    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
0073c000-00742000 r-xp 00000000 08:41 4462963    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00742000-00743000 r-xp 00005000 08:41 4462963    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00743000-00744000 rwxp 00006000 08:41 4462963    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
00744000-00746000 r-xp 00000000 08:41 1876       /usr/lib/mono/gac/NDesk.DBus.GLib/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.GLib.dll
00746000-00759000 r-xp 00000000 08:41 1835881    /lib/i386-linux-gnu/libnsl-2.13.so
00759000-0075a000 r-xp 00012000 08:41 1835881    /lib/i386-linux-gnu/libnsl-2.13.so
0075a000-0075b000 rwxp 00013000 08:41 1835881    /lib/i386-linux-gnu/libnsl-2.13.so
0075b000-0075d000 rwxp 00000000 00:00 0 
0075d000-00778000 r-xp 00000000 08:41 4460343    /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
00778000-00779000 r-xp 0001a000 08:41 4460343    /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
00779000-0077a000 rwxp 0001b000 08:41 4460343    /usr/lib/libgdk_pixbuf-2.0.so.0.2300.3
0077a000-0077c000 r-xp 00000000 08:41 4462821    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
0077c000-0077d000 r-xp 00001000 08:41 4462821    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
0077d000-0077e000 rwxp 00002000 08:41 4462821    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
0077e000-007a2000 r-xp 00000000 08:41 1835878    /lib/i386-linux-gnu/libm-2.13.so
007a2000-007a3000 r-xp 00023000 08:41 1835878    /lib/i386-linux-gnu/libm-2.13.so
007a3000-007a4000 rwxp 00024000 08:41 1835878    /lib/i386-linux-gnu/libm-2.13.so
007a4000-007d2000 r-xp 00000000 08:41 1852       /usr/lib/mono/gac/Mono.Addins/0.4.0.0__0738eb9f132ed756/Mono.Addins.dll
007d2000-0080c000 r-xp 00000000 08:41 1918       /usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll
0080c000-0081d000 r-xp 00000000 08:41 1835908    /lib/i386-linux-gnu/libresolv-2.13.so
0081d000-0081e000 r-xp 00010000 08:41 1835908    /lib/i386-linux-gnu/libresolv-2.13.so
0081e000-0081f000 rwxp 00011000 08:41 1835908    /lib/i386-linux-gnu/libresolv-2.13.so
0081f000-00821000 rwxp 00000000 00:00 0 
00821000-00825000 r-xp 00000000 08:41 4462829    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00825000-00826000 r-xp 00003000 08:41 4462829    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00826000-00827000 rwxp 00004000 08:41 4462829    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00827000-0082b000 r-xp 00000000 08:41 4462746    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0082b000-0082c000 r-xp 00003000 08:41 4462746    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0082c000-0082d000 rwxp 00004000 08:41 4462746    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0082d000-0082e000 r-xs 00000000 08:41 140971     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
0082e000-0083e000 rwxp 00000000 00:00 0 
0083e000-00858000 r-xp 00000000 08:41 4465147    /usr/lib/banshee/Banshee.Core.dll
00858000-00860000 r-xp 00000000 08:41 4462825    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00860000-00861000 r-xp 00007000 08:41 4462825    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00861000-00862000 rwxp 00008000 08:41 4462825    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00862000-00864000 rwxp 00000000 00:00 0 
00864000-008a2000 r-xp 00000000 08:41 4462930    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
008a2000-008a3000 r-xp 0003e000 08:41 4462930    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
008a3000-008a4000 rwxp 0003f000 08:41 4462930    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2800.4
008a4000-008d1000 r-xp 00000000 08:41 4462877    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
008d1000-008d2000 r-xp 0002c000 08:41 4462877    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
008d2000-008d3000 rwxp 0002d000 08:41 4462877    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
008d3000-008d6000 r-xp 00000000 08:41 4462902    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
008d6000-008d7000 r-xp 00003000 08:41 4462902    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
008d7000-008d8000 rwxp 00004000 08:41 4462902    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.2800.6
008d8000-0091d000 r-xp 00000000 08:41 4462896    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
0091d000-0091e000 r-xp 00044000 08:41 4462896    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
0091e000-0091f000 rwxp 00045000 08:41 4462896    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.2800.6
0091f000-00938000 r-xp 00000000 08:41 1835912    /lib/i386-linux-gnu/libselinux.so.1Stacktrace:

  at (wrapper managed-to-native) GLib.Object.g_object_set_property (intptr,intptr,GLib.Value&) <0x00004>
  at (wrapper managed-to-native) GLib.Object.g_object_set_property (intptr,intptr,GLib.Value&) <0x00004>
  at GLib.Object.SetProperty (string,GLib.Value) <0x0003e>
  at Gtk.Action.set_StockId (string) <0x00066>
  at Banshee.Gui.PlaybackActions.ShowPlay () <0x00046>
  at Banshee.Gui.PlaybackActions.OnPlayerStateChange (Banshee.MediaEngine.PlayerEventStateChangeArgs) <0x000ee>
  at Banshee.Gui.PlaybackActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs) <0x0010f>
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs) <0x00167>
  at Banshee.MediaEngine.PlayerEngineService.EndSynthesizeContacting (Banshee.Collection.TrackInfo,bool) <0x00058>
  at Banshee.Streaming.RadioTrackInfo.set_PlaybackError (Banshee.Streaming.StreamPlaybackError) <0x00022>
  at Banshee.Streaming.RadioTrackInfo.SavePlaybackError (Banshee.Streaming.StreamPlaybackError) <0x0001b>
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUri (string) <0x0038e>
  at Banshee.Streaming.RadioTrackInfo.LoadStreamUris () <0x000fd>
  at Banshee.Streaming.RadioTrackInfo.<Play>m__51 (object) <0x00018>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0x00046>

Native stacktrace:

    banshee() [0x80dbc5b]
    [0x2f840c]
    /lib/i386-linux-gnu/libc.so.6(abort+0x17e) [0x16034e]
    /lib/i386-linux-gnu/libc.so.6(+0x61577) [0x193577]
    /lib/i386-linux-gnu/libc.so.6(+0x6b961) [0x19d961]
    /lib/i386-linux-gnu/libc.so.6(+0x6d28b) [0x19f28b]
    /lib/i386-linux-gnu/libc.so.6(cfree+0x6d) [0x1a241d]
    /lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x36) [0xb3ec86]
    /usr/lib/libgdk-x11-2.0.so.0(+0x2b65f) [0xcd065f]
    /usr/lib/libgdk-x11-2.0.so.0(gdk_region_union+0xa4) [0xcd0ef4]
    /usr/lib/libgdk-x11-2.0.so.0(+0x3574c) [0xcda74c]
    /usr/lib/libgdk-x11-2.0.so.0(+0x35a02) [0xcdaa02]
    /usr/lib/libgtk-x11-2.0.so.0(+0x26b03b) [0x177d03b]
    /usr/lib/libgtk-x11-2.0.so.0(+0x27131f) [0x178331f]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_resize+0x7b) [0x17833bb]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__OBJECT+0x88) [0x901088]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xacc7) [0x8e2cc7]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x192) [0x8e4372]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x1e7b6) [0x8f67b6]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x7a9) [0x8ffb29]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x32) [0x8ffcc2]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_remove+0xf1) [0x15bad71]
    /usr/lib/libgtk-x11-2.0.so.0(+0x2732fd) [0x17852fd]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_run_dispose+0x7f) [0x8e7bff]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_object_destroy+0x7e) [0x1673e7e]
    /usr/lib/libgtk-x11-2.0.so.0(+0x21664c) [0x172864c]
    /usr/lib/libgtk-x11-2.0.so.0(+0x217202) [0x1729202]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__PARAM+0x88) [0x900e48]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xacc7) [0x8e2cc7]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x192) [0x8e4372]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x1e7b6) [0x8f67b6]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x7a9) [0x8ffb29]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x32) [0x8ffcc2]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xe0e1) [0x8e60e1]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xd3ef) [0x8e53ef]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_notify+0x549) [0x8e8379]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_tool_button_set_stock_id+0xb3) [0x17298f3]
    /usr/lib/libgtk-x11-2.0.so.0(+0x626d6) [0x15746d6]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_cclosure_marshal_VOID__PARAM+0x88) [0x900e48]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_closure_invoke+0x192) [0x8e4372]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0x1f048) [0x8f7048]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit_valist+0x7a9) [0x8ffb29]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_signal_emit+0x32) [0x8ffcc2]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xe0e1) [0x8e60e1]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(+0xd3ef) [0x8e53ef]
    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0(g_object_set_property+0x831) [0x8ec3d1]
    [0x132465d]
    [0x132456f]
    [0x1326947]
    [0x2520fcf]
    [0x2520a3f]
    [0x2520918]
    [0x24889d0]
    [0x6a2fa19]
    [0x5b436ab]
    [0x5b43644]
    [0x5b48697]
    [0x5b4822e]
    [0x5b48089]
    [0x6fb0bf]
    banshee() [0x8062bc8]
    banshee(mono_runtime_invoke+0x3e) [0x8192eee]
    banshee(mono_runtime_invoke_array+0x2a0) [0x81967a0]
    banshee() [0x8198d1e]
    banshee() [0x81c3ff3]
    banshee() [0x81c4b67]
    banshee() [0x81c3da4]
    banshee() [0x81f669a]
    banshee() [0x8211c12]
    /lib/i386-linux-gnu/libpthread.so.0(+0x5e99) [0x11ee99]
    /lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0x20273e]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
phi@COLIN:~$ 



```

i tried a few times and on the last one banshee just stopped and shut itself down.

---

