---
title: "[SOLVED] PIDGIN (Possible Permissions Problem)"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Michael Cody on 2008-05-25
I have just setup my first Ubuntu 8.04 Hardy Heron machine an older T23 IBM laptop .. I am an experienced computer professional in the windows network/Cisco world, and everything is going fairly well except for Pidgin. This machine is for my youngest ... 

Anyway, when I click on Pidgin from the applications menu it flashes the add accounts screen, the panel icon flashes for a second too. Then it's gone. If I attempt to start Pidgin from the terminal I get the same thing. However if I launch it using "sudo" it comes up and runs fine. The accounts are setup to use General proxy settings inside pidgin.

The config is this:

IBM T23 laptop
SMCWUSB G 802.11g wireless using ndiswrapper and XP/2k drivers 
Linksys W54G wireless router -- running WPA Personal 
Dansguardian/Tinyproxy/Firehol  web filtering w/AOL.COM in the exceptions list

I have a couple of other issues with this machine, but no real show stoppers. Since it runs with "sudo" prefix I get the feeling this is a permissions problem. Below is the output w/o "sudo" prefix of a pidgin -d command - I didn't see anything obvous but then I admit I don't know exactly what to look for.... "Any help would be appreciated as I am getting up to speed with this stuff, it runs well so far except for this little items"

Dalton@Nmbr3SonT23:~$ pidgin -d
dalton@DaltonT23:~$ pidgin -d
(22:16:38) prefs: Reading /home/dalton/.purple/prefs.xml
(22:16:38) prefs: Finished reading /home/dalton/.purple/prefs.xml
(22:16:38) prefs: purple_prefs_get_string: /pidgin/browsers/command not a string pref
(22:16:38) dbus: okkk
(22:16:38) plugins: probing /usr/lib/pidgin/gRIM.so
(22:16:38) plugins: probing /usr/lib/pidgin/cap.so
(22:16:38) plugins: probing /usr/lib/pidgin/history.so
(22:16:38) plugins: probing /usr/lib/pidgin/sepandtab.so
(22:16:38) plugins: probing /usr/lib/pidgin/nautilus.so
(22:16:38) plugins: probing /usr/lib/pidgin/extplacement.so
(22:16:38) plugins: probing /usr/lib/pidgin/ticker.so
(22:16:38) plugins: probing /usr/lib/pidgin/convcolors.so
(22:16:38) plugins: probing /usr/lib/pidgin/guifications.so
(22:16:38) plugins: probing /usr/lib/pidgin/spellchk.so
(22:16:38) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(22:16:38) plugins: probing /usr/lib/pidgin/musictracker.so
(22:16:38) plugins: probing /usr/lib/pidgin/xchat-chats.so
(22:16:38) plugins: probing /usr/lib/pidgin/gestures.so
(22:16:38) plugins: probing /usr/lib/pidgin/markerline.so
(22:16:38) plugins: probing /usr/lib/pidgin/timestamp_format.so
(22:16:38) plugins: probing /usr/lib/pidgin/timestamp.so
(22:16:38) plugins: probing /usr/lib/pidgin/gevolution.so
(22:16:38) plugins: probing /usr/lib/pidgin/notify.so
(22:16:38) plugins: probing /usr/lib/pidgin/encrypt.so
(22:16:38) plugins: probing /usr/lib/pidgin/irssi.so
(22:16:38) plugins: probing /usr/lib/pidgin/pidgin-otr.so
(22:16:38) plugins: probing /usr/lib/pidgin/plonkers.so
(22:16:38) plugins: probing /usr/lib/pidgin/mystatusbox.so
(22:16:38) plugins: probing /usr/lib/pidgin/album.so
(22:16:38) plugins: probing /usr/lib/pidgin/iconaway.so
(22:16:38) plugins: probing /usr/lib/pidgin/blistops.so
(22:16:38) plugins: probing /usr/lib/pidgin/hideconv.so
(22:16:38) plugins: probing /usr/lib/pidgin/nicksaid.so
(22:16:38) plugins: probing /usr/lib/pidgin/xmppconsole.so
(22:16:38) plugins: probing /usr/lib/pidgin/difftopic.so
(22:16:38) plugins: probing /usr/lib/pidgin/lastseen.so
(22:16:38) plugins: probing /usr/lib/pidgin/pidginrc.so
(22:16:38) plugins: probing /usr/lib/pidgin/libextprefs.so
(22:16:38) plugins: probing /usr/lib/pidgin/pidgin-schedule.so
(22:16:38) plugins: probing /usr/lib/pidgin/musicmessaging.so
(22:16:38) plugins: probing /usr/lib/purple-2/dbus-example.so
(22:16:38) plugins: probing /usr/lib/purple-2/listhandler.so
(22:16:38) plugins: probing /usr/lib/purple-2/perl.so
(22:16:39) plugins: probing /usr/lib/purple-2/showoffline.so
(22:16:39) plugins: probing /usr/lib/purple-2/bash.so
(22:16:39) plugins: probing /usr/lib/purple-2/libaim.so
(22:16:39) plugins: probing /usr/lib/purple-2/buddynote.so
(22:16:39) plugins: probing /usr/lib/purple-2/ssl-nss.so
(22:16:39) plugins: probing /usr/lib/purple-2/irc-more.so
(22:16:39) plugins: probing /usr/lib/purple-2/idle.so
(22:16:39) plugins: probing /usr/lib/purple-2/flip.so
(22:16:39) plugins: probing /usr/lib/purple-2/autoaccept.so
(22:16:39) plugins: probing /usr/lib/purple-2/autoreply.so
(22:16:39) plugins: probing /usr/lib/purple-2/slashexec.so
(22:16:39) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(22:16:39) plugins: probing /usr/lib/purple-2/libmsn.so
(22:16:39) plugins: probing /usr/lib/purple-2/sslinfo.so
(22:16:39) plugins: probing /usr/lib/purple-2/libsametime.so
(22:16:39) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(22:16:39) plugins: probing /usr/lib/purple-2/libqq.so
(22:16:39) plugins: probing /usr/lib/purple-2/libbonjour.so
(22:16:39) plugins: probing /usr/lib/purple-2/libxmpp.so
(22:16:39) util: Reading file xmpp-caps.xml from directory /home/dalton/.purple
(22:16:39) util: File /home/dalton/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(22:16:39) plugins: probing /usr/lib/purple-2/libgg.so
(22:16:39) plugins: probing /usr/lib/purple-2/highlight.so
(22:16:39) plugins: probing /usr/lib/purple-2/joinpart.so
(22:16:39) plugins: probing /usr/lib/purple-2/ignore.so
(22:16:39) plugins: probing /usr/lib/purple-2/newline.so
(22:16:39) plugins: probing /usr/lib/purple-2/libsimple.so
(22:16:39) plugins: probing /usr/lib/purple-2/oldlogger.so
(22:16:39) plugins: probing /usr/lib/purple-2/log_reader.so
(22:16:39) plugins: probing /usr/lib/purple-2/ssl.so
(22:16:39) plugins: probing /usr/lib/purple-2/libicq.so
(22:16:39) plugins: probing /usr/lib/purple-2/eight_ball.so
(22:16:39) plugins: probing /usr/lib/purple-2/tcl.so
(22:16:39) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(22:16:39) plugins: probing /usr/lib/purple-2/libnovell.so
(22:16:39) plugins: probing /usr/lib/purple-2/statenotify.so
(22:16:39) plugins: probing /usr/lib/purple-2/autorejoin.so
(22:16:39) plugins: probing /usr/lib/purple-2/dice.so
(22:16:39) plugins: probing /usr/lib/purple-2/liboscar.so
(22:16:39) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:16:39) plugins: probing /usr/lib/purple-2/libjabber.so
(22:16:39) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(22:16:39) plugins: probing /usr/lib/purple-2/simfix.so
(22:16:39) plugins: probing /usr/lib/purple-2/psychic.so
(22:16:39) plugins: probing /usr/lib/purple-2/libyahoo.so
(22:16:39) plugins: probing /usr/lib/purple-2/libirc.so
(22:16:39) plugins: probing /usr/lib/purple-2/libzephyr.so
(22:16:39) plugins: probing /usr/lib/purple-2/libmyspace.so
(22:16:39) plugins: probing /usr/lib/purple-2/irchelper.so
(22:16:39) plugins: probing /usr/lib/purple-2/offlinemsg.so
(22:16:39) prefs: /purple/status/scores/offline changed, scheduling save.
(22:16:39) prefs: /purple/status/scores/available changed, scheduling save.
(22:16:39) prefs: /purple/status/scores/invisible changed, scheduling save.
(22:16:39) prefs: /purple/status/scores/away changed, scheduling save.
(22:16:39) prefs: /purple/status/scores/extended_away changed, scheduling save.
(22:16:39) prefs: /purple/status/scores/idle changed, scheduling save.
(22:16:39) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(22:16:39) util: Reading file accounts.xml from directory /home/dalton/.purple
(22:16:39) util: File /home/dalton/.purple/accounts.xml does not exist (this is not necessarily an error)
(22:16:39) util: Reading file status.xml from directory /home/dalton/.purple
(22:16:39) util: File /home/dalton/.purple/status.xml does not exist (this is not necessarily an error)
(22:16:39) certificate: CertificateVerifier x509, singleuse requested but not found.
(22:16:39) certificate: CertificateVerifier singleuse registered
(22:16:39) certificate: CertificatePool x509, ca requested but not found.
(22:16:39) certificate: CertificateScheme x509 requested but not found.
(22:16:39) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(22:16:39) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(22:16:39) certificate: CertificatePool ca registered
(22:16:39) certificate: CertificatePool x509, tls_peers requested but not found.
(22:16:39) certificate: CertificatePool tls_peers registered
(22:16:39) certificate: CertificateVerifier x509, tls_cached requested but not found.
(22:16:39) certificate: CertificateVerifier tls_cached registered
(22:16:39) prefs: /purple/logging/format changed, scheduling save.
(22:16:39) prefs: /purple/logging/format changed, scheduling save.
(22:16:39) prefs: /purple/proxy/type changed, scheduling save.
(22:16:39) prefs: /purple/proxy/host changed, scheduling save.
(22:16:39) prefs: /purple/proxy/port changed, scheduling save.
(22:16:39) prefs: /purple/proxy/username changed, scheduling save.
(22:16:39) prefs: /purple/proxy/password changed, scheduling save.
(22:16:39) certificate: CertificateScheme x509 requested but not found.
(22:16:39) certificate: CertificateScheme x509 registered
(22:16:39) stun: using server 
(22:16:39) sound: Initializing sound output drivers.
(22:16:39) prefs: /pidgin/conversations/placement changed, scheduling save.
(22:16:39) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(22:16:39) gtkblist: added visibility manager: 1
(22:16:39) prefs: /purple/savedstatus/default changed, scheduling save.
(22:16:39) docklet: created
(22:16:39) util: Reading file blist.xml from directory /home/dalton/.purple
(22:16:39) util: File /home/dalton/.purple/blist.xml does not exist (this is not necessarily an error)
(22:16:39) pounce: Error reading pounces: Failed to open file '/home/dalton/.purple/pounces.xml': No such file or directory
(22:16:39) ui_main: Failed to load the default window icon (scalablepx version)!
(22:16:39) Session Management: ICE initialized.
(22:16:39) Session Management: Connecting with no previous ID
(22:16:39) Session Management: Handling new ICE connection... 
(22:16:39) done.
(22:16:39) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000121176819900000058150105
(22:16:39) Session Management: Using pidgin as command
(22:16:40) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(22:16:40) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(22:16:40) util: requested to fetch ([http://192.168.1.1:5431/dyndev/uuid:001e-e56c-56c7000099dc](http://192.168.1.1:5431/dyndev/uuid:001e-e56c-56c7000099dc)), full=1, user_agent=((null)), http11=1
(22:16:40) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified.  Using Pidgin's proxy settings instead.
(22:16:40) dns: DNS query for '192.168.1.1' queued
(22:16:40) Session Management: Received first save_yourself
(22:16:40) Session Management: Received save_complete
(22:16:40) dns: Created new DNS child 23262, there are now 1 children.
(22:16:40) dns: Successfully sent DNS request to child 23262
(22:16:40) dns: Got response for '192.168.1.1'
(22:16:40) dnsquery: IP resolved for 192.168.1.1
(22:16:40) proxy: Attempting connection to 192.168.1.1
(22:16:40) proxy: Connecting to 192.168.1.1:5431 with no proxy
(22:16:40) proxy: Connection in progress
(22:16:40) docklet: embedded
(22:16:40) proxy: Connected to 192.168.1.1:5431.
(22:16:40) util: Request: 'GET /dyndev/uuid:001e-e56c-56c7000099dc HTTP/1.1
Connection: close
Host: 192.168.1.1:5431

'
(22:16:40) util: Response headers: 'HTTP/1.0 200 OK
SERVER: LINUX/2.4 UPnP/1.0 BRCM400/1.0
DATE: Sun, 25 May 2008 22:15:55 GMT
CONTENT-TYPE: application/octet-stream
Cache-Control: max-age=1
PRAGMA: no-cache
Connection: Close

'
(22:16:40) util: requested to fetch ([http://192.168.1.1:5431/uuid:001e-e56c-56c7020099dc/WANIPConnection:1](http://192.168.1.1:5431/uuid:001e-e56c-56c7020099dc/WANIPConnection:1)), full=0, user_agent=((null)), http11=1
(22:16:40) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified.  Using Pidgin's proxy settings instead.
(22:16:40) dns: DNS query for '192.168.1.1' queued
(22:16:40) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified.  Using Pidgin's proxy settings instead.
(22:16:40) dns: DNS query for '192.168.1.1' queued
(22:16:40) dns: Created new DNS child 23267, there are now 1 children.
(22:16:40) dns: Successfully sent DNS request to child 23267
(22:16:40) dns: Created new DNS child 23268, there are now 2 children.
(22:16:40) dns: Successfully sent DNS request to child 23268
(22:16:40) network: Entering nm_callback_func!
dns[23268] Error: getaddrinfo returned -2
(22:16:40) dns: Got response for 'UTF-8'
(22:16:40) dnsquery: Error resolving UTF-8:
Name or service not known
(22:16:40) proxy: Connection attempt failed: Error resolving UTF-8:
Name or service not known
(22:16:40) upnp: Local IP: 192.168.1.102
dns[23267] Error: getaddrinfo returned -2
(22:16:40) dns: Got response for ''
(22:16:40) dnsquery: Error resolving :
Name or service not known
(22:16:40) proxy: Connection attempt failed: Error resolving :
Name or service not known
*** glibc detected *** pidgin: malloc(): memory corruption (fast): 0x082ad908 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7652962]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb7653cad]
/lib/tls/i686/cmov/libc.so.6(realloc+0x1e6)[0xb7655836]
/usr/lib/libglib-2.0.so.0(g_realloc+0x35)[0xb77b2905]
/usr/lib/libglib-2.0.so.0[0xb77cc46c]
/usr/lib/libglib-2.0.so.0(g_string_sized_new+0x3d)[0xb77cd4ed]
/usr/lib/libglib-2.0.so.0[0xb77b0054]
/usr/lib/libglib-2.0.so.0(g_markup_parse_context_parse+0xd0e)[0xb77b17ae]
/usr/lib/libpango-1.0.so.0(pango_parse_markup+0x174)[0xb7a51814]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c58f40]
/usr/lib/libgtk-x11-2.0.so.0(gtk_label_set_markup+0x81)[0xb7c59871]
/usr/lib/libgtk-x11-2.0.so.0(gtk_tooltip_set_markup+0x52)[0xb7d49132]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d491da]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d496dd]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d49c81]
/usr/lib/libgdk-x11-2.0.so.0[0xb7ab581b]
/usr/lib/libglib-2.0.so.0[0xb77ab336]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x178)[0xb77aabf8]
/usr/lib/libglib-2.0.so.0[0xb77ade5e]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb77ae1e7]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c6c264]
pidgin(main+0xbbc)[0x80c70d5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb75fc450]
pidgin[0x806c821]
======= Memory map: ========
08048000-08115000 r-xp 00000000 08:01 1036217    /usr/bin/pidgin
08115000-08118000 rw-p 000cc000 08:01 1036217    /usr/bin/pidgin
08118000-0858d000 rw-p 08118000 00:00 0          [heap]
b4a00000-b4a21000 rw-p b4a00000 00:00 0 
b4a21000-b4b00000 ---p b4a21000 00:00 0 
b4b8a000-b4bea000 rw-s 00000000 00:09 5210124    /SYSV00000000 (deleted)
b4bea000-b4cee000 rw-p b4bea000 00:00 0 
b4cee000-b4d75000 r--p 00000000 08:01 157117     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4d75000-b4d8c000 r--s 00000000 08:01 181251     /var/lib/aspell/en_US-wo_accents-only.rws
b4d8c000-b5014000 r--s 00000000 08:01 181240     /var/lib/aspell/en-common.rws
b5014000-b5118000 rw-p b5014000 00:00 0 
b5118000-b511a000 r-xp 00000000 08:01 1090060    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b511a000-b511b000 rw-p 00001000 08:01 1090060    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b511b000-b51ac000 r--p 00000000 08:01 157116     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b51ac000-b51b2000 r--s 00000000 08:01 172327     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b51b2000-b51b5000 r--s 00000000 08:01 172344     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b51b5000-b51b6000 r--s 00000000 08:01 172343     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b51b6000-b51b7000 r--s 00000000 08:01 172342     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b51b7000-b51ba000 r--s 00000000 08:01 172341     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b51ba000-b51bd000 r--s 00000000 08:01 172340     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b51bd000-b51c0000 r--s 00000000 08:01 172339     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b51c0000-b51c8000 r--s 00000000 08:01 172338     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b51c8000-b51d0000 r--s 00000000 08:01 172337     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b51d0000-b51d1000 r--s 00000000 08:01 172336     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b51d1000-b51d4000 r--s 00000000 08:01 172335     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b51d4000-b51db000 r--s 00000000 08:01 172334     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b51db000-b51ea000 r-xp 00000000 08:01 1130622    /lib/libbz2.so.1.0.4
b51ea000-b51eb000 rw-p 0000f000 08:01 1130622    /lib/libbz2.so.1.0.4
b51eb000-b524a000 r-xp 00000000 08:01 1033094    /usr/lib/libgio-2.0.so.0.0.0
b524a000-b524c000 rw-p 0005e000 08:01 1033094    /usr/lib/libgio-2.0.so.0.0.0
b524c000-b527e000 r-xp 00000000 08:01 1036494    /usr/lib/libcroco-0.6.so.3.0.1
b527e000-b5281000 rw-p 00031000 08:01 1036494    /usr/lib/libcroco-0.6.so.3.0.1
b5281000-b52b1000 r-xp 00000000 08:01 1036497    /usr/lib/libgsf-1.so.114.0.7
b52b1000-b52b4000 rw-p 0002f000 08:01 1036497    /usr/lib/libgsf-1.so.114.0.7
b52b4000-b52b5000 rw-p b52b4000 00:00 0 
b52b5000-b52e5000 r-xp 00000000 08:01 1036499    /usr/lib/librsvg-2.so.2.22.2
b52e5000-b52e6000 rw-p 00030000 08:01 1036499    /usr/lib/librsvg-2.so.2.22.2
b52ea000-b52f0000 r--s 00000000 08:01 172326     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b52f0000-b52f2000 r--s 00000000 08:01 172520     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b52f2000-b52ff000 r--p 00000000 08:01 1060874    /usr/share/icons/Mist/icon-theme.cache
b52ff000-b5303000 r-xp 00000000 08:01 1093787    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5303000-b5304000 rw-Aborted

---

### Post by iaculallad on 2008-05-25
You could try this in the terminal:

> sudo mv /usr/local/lib/libpurple.la /tmp
sudo mv /usr/local/lib/libpurple.so.0.0.1 /tmp
sudo rm /usr/local/lib/libpurple.so.0
sudo ldconfig

then try accessing pidgin.

---

### Post by Michael Cody on 2008-05-25
I had found that particular set of info. I tried. The path layed out was not the same as my system. My system shows those files in /usr/lib/  and the file libpurple.la is not there. The other two are and I ran those commands as listed, it still didn't work. For fun I re-booted, still no joy. I am not sure of the differences in the file structure, but to date that fix didn't work. I even have completely uninstalled pidgin and reinstalled to no avail. 

I was wondering if the Dansguardian/Tinyproxy had something to do with it, but not sure where too look. That made sense to me, but I am not sure why there is no obvious error about not being able to connect. The section of the output made me wander in that direction:

(22:16:40) dns: DNS query for '192.168.1.1' queued
(22:16:40) Session Management: Received first save_yourself
(22:16:40) Session Management: Received save_complete
(22:16:40) dns: Created new DNS child 23262, there are now 1 children.
(22:16:40) dns: Successfully sent DNS request to child 23262
(22:16:40) dns: Got response for '192.168.1.1'
(22:16:40) dnsquery: IP resolved for 192.168.1.1
(22:16:40) proxy: Attempting connection to 192.168.1.1
(22:16:40) proxy: Connecting to 192.168.1.1:5431 with no proxy
(22:16:40) proxy: Connection in progress
(22:16:40) docklet: embedded
(22:16:40) proxy: Connected to 192.168.1.1:5431.
(22:16:40) util: Request: 'GET /dyndev/uuid:001e-e56c-56c7000099dc HTTP/1.1
Connection: close
Host: 192.168.1.1:5431

'
(22:16:40) util: Response headers: 'HTTP/1.0 200 OK
SERVER: LINUX/2.4 UPnP/1.0 BRCM400/1.0
DATE: Sun, 25 May 2008 22:15:55 GMT
CONTENT-TYPE: application/octet-stream
Cache-Control: max-age=1
PRAGMA: no-cache
Connection: Close

'
(22:16:40) util: requested to fetch ([http://192.168.1.1:5431/uuid:001e-e5...IPConnection:1]("http://192.168.1.1:5431/uuid:001e-e56c-56c7020099dc/WANIPConnection:1")), full=0, user_agent=((null)), http11=1
(22:16:40) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified. Using Pidgin's proxy settings instead.
(22:16:40) dns: DNS query for '192.168.1.1' queued
(22:16:40) proxy: Gnome proxy settings are set to 'manual' but no proxy server is specified. Using Pidgin's proxy settings instead.
(22:16:40) dns: DNS query for '192.168.1.1' queued
(22:16:40) dns: Created new DNS child 23267, there are now 1 children.
(22:16:40) dns: Successfully sent DNS request to child 23267
(22:16:40) dns: Created new DNS child 23268, there are now 2 children.
(22:16:40) dns: Successfully sent DNS request to child 23268
(22:16:40) network: Entering nm_callback_func!
dns[23268] Error: getaddrinfo returned -2
(22:16:40) dns: Got response for 'UTF-8'
(22:16:40) dnsquery: Error resolving UTF-8:
Name or service not known
(22:16:40) proxy: Connection attempt failed: Error resolving UTF-8:
Name or service not known
(22:16:40) upnp: Local IP: 192.168.1.102
dns[23267] Error: getaddrinfo returned -2
(22:16:40) dns: Got response for ''
(22:16:40) dnsquery: Error resolving :
Name or service not known
(22:16:40) proxy: Connection attempt failed: Error resolving :
Name or service not known

---

### Post by iaculallad on 2008-05-25
Just an option :) What about uninstalling pidgin then re-install it again using using the Synaptics?

---

### Post by Michael Cody on 2008-05-26
> **iaculallad said:**
> Just an option :) What about uninstalling pidgin then re-install it again using using the Synaptics?

Actually did that 2-3 times ... finally have it working! It was a proxy problem. When I installed Dansguardian/Tinyproxy/Firehol config it works fine but the system tries to use the Gnome settings when it starts. Well I config'd the settings in Pidgin, but not in Gnome. My screwup! When I configured the Gnome settings, viola no more problems. Makes the kid happy.  I've got a couple of other minor issues, but basically I am going good right now. I gave the boy a book on Ubuntu -- am not going to fix any other issues for him unless they are outside of the scope of a teachable moment. I spent an hour this morning making him find the problem I found in the debug output, didn't let him use the machine until he found the DNS/Proxy errors and asked me to explain how it all works. I've go to do some more security stuff so he can't add/change the Dansguardian lists (if he learns enough to bypass that well it's a good educational excersise, can't make it too easy). 

At least if he's on the machine for hours working on it, instead of watching anime .. he might actually be learning something!

Thanx for the input ....

---

