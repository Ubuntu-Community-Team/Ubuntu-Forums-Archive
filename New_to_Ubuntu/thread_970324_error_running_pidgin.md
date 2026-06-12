---
title: "error running pidgin ??"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by sazan on 2008-11-04
i was running pidgin without any problem moments before.. then i closed it and tried it running.. this is wat i get 

```


libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files




```


and this when i run " pidgin -d"

```


(14:38:43) prefs: Reading /home/sagrawal/.purple/prefs.xml
(14:38:43) prefs: Finished reading /home/sagrawal/.purple/prefs.xml
(14:38:43) dbus: okkk
(14:38:43) plugins: probing /usr/lib/pidgin/notify.so
(14:38:43) plugins: probing /usr/lib/pidgin/gevolution.so
(14:38:43) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(14:38:43) plugins: probing /usr/lib/pidgin/history.so
(14:38:43) plugins: probing /usr/lib/pidgin/convcolors.so
(14:38:43) plugins: probing /usr/lib/pidgin/timestamp.so
(14:38:43) plugins: probing /usr/lib/pidgin/markerline.so
(14:38:43) plugins: probing /usr/lib/pidgin/timestamp_format.so
(14:38:43) plugins: probing /usr/lib/pidgin/iconaway.so
(14:38:43) plugins: probing /usr/lib/pidgin/xmppconsole.so
(14:38:43) plugins: probing /usr/lib/pidgin/extplacement.so
(14:38:43) plugins: probing /usr/lib/pidgin/ticker.so
(14:38:43) plugins: probing /usr/lib/pidgin/spellchk.so
(14:38:43) plugins: probing /usr/lib/pidgin/gestures.so
(14:38:43) plugins: probing /usr/lib/pidgin/musicmessaging.so
(14:38:43) plugins: probing /usr/lib/pidgin/pidginrc.so
(14:38:43) plugins: probing /usr/lib/purple-2/dbus-example.so
(14:38:43) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(14:38:43) plugins: probing /usr/lib/purple-2/libmsn.so
(14:38:43) plugins: probing /usr/lib/purple-2/libsimple.so
(14:38:43) plugins: probing /usr/lib/purple-2/ssl-nss.so
(14:38:43) plugins: probing /usr/lib/purple-2/libzephyr.so
(14:38:43) plugins: probing /usr/lib/purple-2/libbonjour.so
(14:38:43) plugins: probing /usr/lib/purple-2/libsametime.so
(14:38:44) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(14:38:44) plugins: probing /usr/lib/purple-2/idle.so
(14:38:44) plugins: probing /usr/lib/purple-2/libirc.so
(14:38:44) plugins: probing /usr/lib/purple-2/libqq.so
(14:38:44) plugins: probing /usr/lib/purple-2/statenotify.so
(14:38:44) plugins: probing /usr/lib/purple-2/buddynote.so
(14:38:44) plugins: probing /usr/lib/purple-2/libnovell.so
(14:38:44) plugins: probing /usr/lib/purple-2/libyahoo.so
(14:38:44) plugins: probing /usr/lib/purple-2/log_reader.so
(14:38:44) plugins: probing /usr/lib/purple-2/psychic.so
(14:38:44) plugins: probing /usr/lib/purple-2/liboscar.so
(14:38:44) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:38:44) plugins: probing /usr/lib/purple-2/libxmpp.so
(14:38:44) util: Reading file xmpp-caps.xml from directory /home/sagrawal/.purple
(14:38:44) util: File /home/sagrawal/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(14:38:44) plugins: probing /usr/lib/purple-2/joinpart.so
(14:38:44) plugins: probing /usr/lib/purple-2/ssl.so
(14:38:44) plugins: probing /usr/lib/purple-2/newline.so
(14:38:44) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(14:38:44) plugins: probing /usr/lib/purple-2/libmyspace.so
(14:38:44) plugins: probing /usr/lib/purple-2/autoaccept.so
(14:38:44) plugins: probing /usr/lib/purple-2/libicq.so
(14:38:44) plugins: probing /usr/lib/purple-2/libgg.so
(14:38:44) plugins: probing /usr/lib/purple-2/libjabber.so
(14:38:44) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:38:44) plugins: probing /usr/lib/purple-2/libaim.so
(14:38:44) plugins: probing /usr/lib/purple-2/offlinemsg.so
(14:38:44) prefs: /purple/status/scores/offline changed, scheduling save.
(14:38:44) prefs: /purple/status/scores/available changed, scheduling save.
(14:38:44) prefs: /purple/status/scores/invisible changed, scheduling save.
(14:38:44) prefs: /purple/status/scores/away changed, scheduling save.
(14:38:44) prefs: /purple/status/scores/extended_away changed, scheduling save.
(14:38:44) prefs: /purple/status/scores/idle changed, scheduling save.
(14:38:44) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(14:38:44) util: Reading file accounts.xml from directory /home/sagrawal/.purple
(14:38:44) util: Reading file status.xml from directory /home/sagrawal/.purple
(14:38:44) certificate: CertificateVerifier x509, singleuse requested but not found.
(14:38:44) certificate: CertificateVerifier singleuse registered
(14:38:44) certificate: CertificatePool x509, ca requested but not found.
(14:38:44) certificate: CertificateScheme x509 requested but not found.
(14:38:44) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(14:38:44) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(14:38:44) certificate: CertificatePool ca registered
(14:38:44) certificate: CertificatePool x509, tls_peers requested but not found.
(14:38:44) certificate: CertificatePool tls_peers registered
(14:38:44) certificate: CertificateVerifier x509, tls_cached requested but not found.
(14:38:44) certificate: CertificateVerifier tls_cached registered
(14:38:44) prefs: /purple/logging/format changed, scheduling save.
(14:38:44) prefs: /purple/logging/format changed, scheduling save.
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
(14:38:44) prefs: /purple/proxy/type changed, scheduling save.
(14:38:44) prefs: /purple/proxy/host changed, scheduling save.
(14:38:44) prefs: /purple/proxy/port changed, scheduling save.
(14:38:44) prefs: /purple/proxy/username changed, scheduling save.
(14:38:44) prefs: /purple/proxy/password changed, scheduling save.
(14:38:44) certificate: CertificateScheme x509 requested but not found.
(14:38:44) certificate: CertificateScheme x509 registered
(14:38:44) stun: using server 
(14:38:44) sound: Initializing sound output drivers.
(14:38:44) prefs: /pidgin/conversations/placement changed, scheduling save.
(14:38:44) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(14:38:44) gtkblist: added visibility manager: 1
(14:38:44) docklet: created
(14:38:44) main: exiting because another libpurple client is already running
(14:38:44) blist: Attempted to save buddy list before it was read!
(14:38:44) certificate: CertificateScheme x509 unregistered
(14:38:44) certificate: CertificateVerifier tls_cached unregistered
(14:38:44) certificate: CertificateVerifier singleuse unregistered
(14:38:44) certificate: CertificatePool tls_peers unregistered
(14:38:44) certificate: CertificatePool ca unregistered
(14:38:44) util: Writing file accounts.xml to directory /home/sagrawal/.purple
(14:38:44) util: Writing file /home/sagrawal/.purple/accounts.xml
(14:38:44) util: Writing file prefs.xml to directory /home/sagrawal/.purple
(14:38:44) util: Writing file /home/sagrawal/.purple/prefs.xml
(14:38:45) main: Unloading all plugins
(14:38:45) plugins: Unloading plugin MSN
(14:38:45) plugins: Unloading plugin SIMPLE
(14:38:45) plugins: Unloading plugin NSS
(14:38:45) certificate: CertificateScheme x509 unregistered
(14:38:45) plugins: Unloading plugin Zephyr
(14:38:45) plugins: Unloading plugin Bonjour
(14:38:45) plugins: Unloading plugin Sametime
(14:38:45) plugins: Unloading plugin IRC
(14:38:45) plugins: Unloading plugin QQ
(14:38:45) plugins: Unloading plugin GroupWise
(14:38:45) plugins: Unloading plugin Yahoo
(14:38:45) plugins: Unloading plugin XMPP
(14:38:45) plugins: Unloading plugin SSL
(14:38:45) plugins: Unloading plugin SILC
(14:38:45) plugins: Unloading plugin MySpaceIM
(14:38:45) plugins: Unloading plugin ICQ
(14:38:45) plugins: Unloading plugin Gadu-Gadu
(14:38:45) plugins: Unloading plugin AIM
(14:38:45) accels: accel changed, scheduling save.
(14:38:45) accels: accel changed, scheduling save.
(14:38:45) accels: accel changed, scheduling save.
(14:38:45) accels: accel changed, scheduling save.
(14:38:45) accels: accel changed, scheduling save.
(14:38:45) accels: accel changed, scheduling save.
(14:38:45) gtkblist: removed visibility manager: 0
(14:38:45) docklet: destroyed
(14:38:45) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed



```


What is the problem ??

---

### Post by sazan on 2008-11-04
strange but after doing logoff .. it started working fine now.. but cudnt understand the problem

---

