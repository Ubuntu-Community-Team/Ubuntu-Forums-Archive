---
title: "[SOLVED] pidgin does not work"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by nir2000 on 2008-07-27
I started pidgin once and after I filled up the correct details and logged out it won't start again.If I click the pidgin icon the small clock like footprint turns and turns and at the end pidgin won't start, please help.
Thank you in advance 
Nir

---

### Post by Ryadt on 2008-07-27
Can you try starting it through the terminal```
pidgin
```

---

### Post by braddcadd on 2008-07-27
Start it from the terminal and see if there are any text messages given.  The debug option may help.  In a terminal, type the following:

```
pidgin -d
```

---

### Post by gjoellee on 2008-07-27
if you are using pidgin for MSN you can use amsn instead...and by the way it looks more like msn to....
> sudo apt-get install amsn

---

### Post by nir2000 on 2008-07-27
I have tried pidgin in the terminal and nothing happens

---

### Post by rockstarrem on 2008-07-27
Try:

> 
sudo apt-get remove pidgin
sudo apt-get install pidgin


---

### Post by nbayiha on 2008-07-27
i have the same problem , here. Pidgin is not working at all. On a clean hardy instalation.

---

### Post by nir2000 on 2008-07-27
Thanks to everybody for your trying to help me.  I have also tried &#8220;pidgin -d&#8221; and it wrote many lines which I didn't manage to see. Do you have any other ideas.
I will be grateful 

Nir

---

### Post by llama320 on 2008-07-27
> **nir2000 said:**
> Thanks to everybody for your trying to help me.  I have also tried “pidgin -d” and it wrote many lines which I didn't manage to see. Do you have any other ideas.
I will be grateful 

Nir

To catch those messages, type this in terminal
```
 pidgin -d > ~/Desktop/pidgin_output.txt
```

then copy and paste the text in "pidgin_output.txt" to this forum so we can look at it

Good Luck

---

### Post by nir2000 on 2008-07-27
Yhanks again for every one. uninstalling and installing pidgin didn't help.
any way thank you
Nir

---

### Post by nir2000 on 2008-07-27
(20:44:26) prefs: Reading /home/nirbh/.purple/prefs.xml
(20:44:26) prefs: Finished reading /home/nirbh/.purple/prefs.xml
(20:44:26) prefs: purple_prefs_get_string: /pidgin/browsers/command not a string pref
(20:44:26) dbus: okkk
(20:44:26) plugins: probing /usr/lib/pidgin/convcolors.so
(20:44:26) plugins: probing /usr/lib/pidgin/iconaway.so
(20:44:26) plugins: probing /usr/lib/pidgin/nautilus.so
(20:44:26) plugins: probing /usr/lib/pidgin/notify.so
(20:44:26) plugins: probing /usr/lib/pidgin/spellchk.so
(20:44:26) plugins: probing /usr/lib/pidgin/markerline.so
(20:44:26) plugins: probing /usr/lib/pidgin/timestamp_format.so
(20:44:26) plugins: probing /usr/lib/pidgin/gestures.so
(20:44:26) plugins: probing /usr/lib/pidgin/cap.so
(20:44:26) plugins: probing /usr/lib/pidgin/gevolution.so
(20:44:26) plugins: probing /usr/lib/pidgin/musicmessaging.so
(20:44:26) plugins: probing /usr/lib/pidgin/extplacement.so
(20:44:26) plugins: probing /usr/lib/pidgin/pidginrc.so
(20:44:26) plugins: probing /usr/lib/pidgin/xmppconsole.so
(20:44:26) plugins: probing /usr/lib/pidgin/history.so
(20:44:26) plugins: probing /usr/lib/pidgin/timestamp.so
(20:44:26) plugins: probing /usr/lib/pidgin/ticker.so
(20:44:26) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(20:44:26) plugins: probing /usr/lib/purple-2/libaim.so
(20:44:26) plugins: probing /usr/lib/purple-2/buddynote.so
(20:44:26) plugins: probing /usr/lib/purple-2/libyahoo.so
(20:44:26) plugins: probing /usr/lib/purple-2/perl.so
(20:44:26) plugins: probing /usr/lib/purple-2/offlinemsg.so
(20:44:26) plugins: probing /usr/lib/purple-2/dbus-example.so
(20:44:26) plugins: probing /usr/lib/purple-2/libirc.so
(20:44:26) plugins: probing /usr/lib/purple-2/libqq.so
(20:44:26) plugins: probing /usr/lib/purple-2/joinpart.so
(20:44:26) plugins: probing /usr/lib/purple-2/libsimple.so
(20:44:26) plugins: probing /usr/lib/purple-2/newline.so
(20:44:26) plugins: probing /usr/lib/purple-2/psychic.so
(20:44:26) plugins: probing /usr/lib/purple-2/libsametime.so
(20:44:26) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(20:44:26) plugins: probing /usr/lib/purple-2/libmsn.so
(20:44:26) plugins: probing /usr/lib/purple-2/autoaccept.so
(20:44:26) plugins: probing /usr/lib/purple-2/ssl-nss.so
(20:44:26) plugins: probing /usr/lib/purple-2/ssl.so
(20:44:26) plugins: probing /usr/lib/purple-2/libbonjour.so
(20:44:26) plugins: probing /usr/lib/purple-2/libnovell.so
(20:44:26) plugins: probing /usr/lib/purple-2/libxmpp.so
(20:44:26) util: Reading file xmpp-caps.xml from directory /home/nirbh/.purple
(20:44:26) util: File /home/nirbh/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(20:44:26) plugins: probing /usr/lib/purple-2/statenotify.so
(20:44:26) plugins: probing /usr/lib/purple-2/libmyspace.so
(20:44:26) plugins: probing /usr/lib/purple-2/libgg.so
(20:44:26) plugins: probing /usr/lib/purple-2/libzephyr.so
(20:44:26) plugins: probing /usr/lib/purple-2/liboscar.so
(20:44:26) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(20:44:26) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(20:44:26) plugins: probing /usr/lib/purple-2/tcl.so
(20:44:26) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(20:44:26) plugins: probing /usr/lib/purple-2/libjabber.so
(20:44:26) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(20:44:26) plugins: probing /usr/lib/purple-2/idle.so
(20:44:26) plugins: probing /usr/lib/purple-2/libicq.so
(20:44:26) plugins: probing /usr/lib/purple-2/log_reader.so
(20:44:26) prefs: /purple/status/scores/offline changed, scheduling save.
(20:44:26) prefs: /purple/status/scores/available changed, scheduling save.
(20:44:26) prefs: /purple/status/scores/invisible changed, scheduling save.
(20:44:26) prefs: /purple/status/scores/away changed, scheduling save.
(20:44:26) prefs: /purple/status/scores/extended_away changed, scheduling save.
(20:44:26) prefs: /purple/status/scores/idle changed, scheduling save.
(20:44:26) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(20:44:26) util: Reading file accounts.xml from directory /home/nirbh/.purple
(20:44:26) util: Reading file status.xml from directory /home/nirbh/.purple
(20:44:26) certificate: CertificateVerifier x509, singleuse requested but not found.
(20:44:26) certificate: CertificateVerifier singleuse registered
(20:44:26) certificate: CertificatePool x509, ca requested but not found.
(20:44:26) certificate: CertificateScheme x509 requested but not found.
(20:44:26) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(20:44:26) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(20:44:26) certificate: CertificatePool ca registered
(20:44:26) certificate: CertificatePool x509, tls_peers requested but not found.
(20:44:26) certificate: CertificatePool tls_peers registered
(20:44:26) certificate: CertificateVerifier x509, tls_cached requested but not found.
(20:44:26) certificate: CertificateVerifier tls_cached registered
(20:44:26) prefs: /purple/logging/format changed, scheduling save.
(20:44:26) prefs: /purple/logging/format changed, scheduling save.
(20:44:26) prefs: /purple/proxy/type changed, scheduling save.
(20:44:26) prefs: /purple/proxy/host changed, scheduling save.
(20:44:26) prefs: /purple/proxy/port changed, scheduling save.
(20:44:26) prefs: /purple/proxy/username changed, scheduling save.
(20:44:26) prefs: /purple/proxy/password changed, scheduling save.
(20:44:26) certificate: CertificateScheme x509 requested but not found.
(20:44:26) certificate: CertificateScheme x509 registered
(20:44:26) stun: using server 
(20:44:26) sound: Initializing sound output drivers.
(20:44:26) prefs: /pidgin/conversations/placement changed, scheduling save.
(20:44:26) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(20:44:26) gtkblist: added visibility manager: 1
(20:44:26) docklet: created
(20:44:26) main: exiting because another libpurple client is already running
(20:44:26) blist: Attempted to save buddy list before it was read!
(20:44:26) certificate: CertificateScheme x509 unregistered
(20:44:26) certificate: CertificateVerifier tls_cached unregistered
(20:44:26) certificate: CertificateVerifier singleuse unregistered
(20:44:26) certificate: CertificatePool tls_peers unregistered
(20:44:26) certificate: CertificatePool ca unregistered
(20:44:26) util: Writing file accounts.xml to directory /home/nirbh/.purple
(20:44:26) util: Writing file /home/nirbh/.purple/accounts.xml
(20:44:26) util: Writing file prefs.xml to directory /home/nirbh/.purple
(20:44:26) util: Writing file /home/nirbh/.purple/prefs.xml
(20:44:26) main: Unloading all plugins
(20:44:26) plugins: Unloading plugin AIM
(20:44:26) plugins: Unloading plugin Yahoo
(20:44:26) plugins: Unloading plugin Perl Plugin Loader
(20:44:26) plugins: Unloading plugin IRC
(20:44:26) plugins: Unloading plugin QQ
(20:44:26) plugins: Unloading plugin SIMPLE
(20:44:26) plugins: Unloading plugin Sametime
(20:44:26) plugins: Unloading plugin MSN
(20:44:26) plugins: Unloading plugin NSS
(20:44:26) certificate: CertificateScheme x509 unregistered
(20:44:26) plugins: Unloading plugin SSL
(20:44:26) plugins: Unloading plugin Bonjour
(20:44:26) plugins: Unloading plugin GroupWise
(20:44:26) plugins: Unloading plugin XMPP
(20:44:26) plugins: Unloading plugin MySpaceIM
(20:44:26) plugins: Unloading plugin Gadu-Gadu
(20:44:26) plugins: Unloading plugin Zephyr
(20:44:26) plugins: Unloading plugin ICQ
(20:44:26) gtkblist: removed visibility manager: 0
(20:44:26) docklet: destroyed
(20:44:26) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed

---

### Post by nbayiha on 2008-07-30
Please i need help right here , pidgin is not working , actually my main problem is that i can't use Gadu Gadu who is a Polish instant messaging , and after a clean installation , i can't connect with my gadu gadu. 
I tried kopete, and i still got the same problem , nothing is working , I installed gyachi (for Yahoo), and i can chat with Yahoo, but using kopete i can connect to yahoo neither to gadu.

Please Help needed. 

Resuming the problem .... Just gyachi is working , with other program like kopete or pidgin i can't connect to gadu neither to yahoo .:confused:

Edit : i fixed the problem, what i did was first uninstall  firestarter (i just thought that may be the problem), and then i configure Gadu proxy . Anyway i think the problem was with firestarter.

---

### Post by rhenium3 on 2008-07-31
I have reinstalled pidgin numerous times and it is still not working... It will act like it is starting, the little circle rolling and a program window "starting pidgin" and then nothing.... this just started today, yesterday it worked fine :(

any help? I tried doing  pidgin -d > ~/Desktop/pidgin_output.txt but I got no output at all :(

---ok, nevermind, I did sudo apt-get update and it seems to be working....

---

### Post by nbayiha on 2008-09-01
Why not installing something else instead. If you want to use Gadu Gadu for instance you can install , Kadu 
[http://www.kadu.net/w/Pobierz:Ubuntu](http://www.kadu.net/w/Pobierz:Ubuntu)

and for the rest you can always use kopete or amsn and gyache for yahoo.

---

### Post by erudite on 2008-09-01
@rhenium3 you could always try the latest version of Pidgin...uninstall using terminal or your package manager...

The go to [http://www.getdeb.com/]("http://www.getdeb.com/") and type pidgin download all the .deb files and install then you have the latest version.  Hope this helps.

Typical...i used getdeb last night and there is a new version already.

---

### Post by keith.eckstein on 2008-09-01
On a clean install of Hardy Heron, my Pidgin didn't work - it would try to load and then hang.  My Yahoo IM Address is something like [email]Kecksteinxxxx@yahoo.co.uk[/email] - I had set Pidgin up to use a Yahoo IM account.  

I then changed it it an MSN account (using my Yahoo IM address), in Pidgin; Manage Accounts and everything worked fine.

Not really sure why???  but it might be worth trying that - I am on 2Mb/s broadband and it looked like Pidgin was hanging - if the OP is on dial-up the effect will be far worse.

Like others here - I could suggest AMSN but I still prefer Pidgin and welcome the lack of support for webcams - for webcam stuff, I tend to use Y!Live which I find very good.

All the best

Keith

---

### Post by erudite on 2008-09-01
Pidgin always hangs because you have to use http method of connection because windows only want you using windows live.  HTTP method seems really dodgy and sometimes messages don't get through.

---

