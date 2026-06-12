---
title: "can someone explain how this is possible"
date: 2014-03-16
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2014-03-16
i almost managed to find what i was looking for, but it can only be found when searching both the etc and usr folders in that order
cat reads evreything as a plain text file right?
```
chad@M4A79XTD-EVO:~$ cat -n /tmp/ddwrt/old/{etc,usr}/*/*|grep '@import' -A5 -B5
cat: /tmp/ddwrt/old/etc/freeradius/certs: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/modules: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/sites-available: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/sites-enabled: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/sql: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/extra: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/file_types: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/malware: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/protocols: Is a directory
cat: /tmp/ddwrt/old/etc/openser/dbtext: Is a directory
cat: /tmp/ddwrt/old/etc/privoxy/templates: Is a directory
cat: /tmp/ddwrt/old/etc/terminfo/l: Is a directory
cat: /tmp/ddwrt/old/etc/terminfo/v: Is a directory
cat: /tmp/ddwrt/old/etc/terminfo/x: Is a directory
cat: /tmp/ddwrt/old/usr/etc/mc: Is a directory
cat: /tmp/ddwrt/old/usr/etc/tor: Is a directory
cat: /tmp/ddwrt/old/usr/lib/asterisk: Is a directory
cat: /tmp/ddwrt/old/usr/lib/daq: Is a directory
cat: /tmp/ddwrt/old/usr/libexec/nocat: Is a directory
cat: /tmp/ddwrt/old/usr/lib/firmware: Is a directory
cat: /tmp/ddwrt/old/usr/lib/lighttpd: Is a directory
cat: /tmp/ddwrt/old/usr/lib/mc: Is a directory
cat: /tmp/ddwrt/old/usr/lib/openser: Is a directory
cat: /tmp/ddwrt/old/usr/lib/snort_dynamicengine: Is a directory
cat: /tmp/ddwrt/old/usr/lib/snort_dynamicpreprocessor: Is a directory
cat: /tmp/ddwrt/old/usr/lib/squid: Is a directory
303035    fieldset legend {
303036    margin-left:-9px;
303037    margin-bottom:8px;
303038    padding:0 .09em;
303039    }
303040    Wireless_Advanced.asprouter_stylebluecyanyellowgreenorangered@import url(../common.css);
303041    #menuSub,
303042    #menuMainList li span,
303043    #help h2 {
303044    background:#%03x;
303045    color:#%03x;
cat: /tmp/ddwrt/old/usr/share/freeradius: Is a directory
cat: /tmp/ddwrt/old/usr/share/locale: Is a directory
cat: /tmp/ddwrt/old/usr/share/mc: Is a directory
cat: /tmp/ddwrt/old/usr/share/tor: Is a directory
cat: /tmp/ddwrt/old/usr/share/transmission: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/cron.d: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/ddns: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/etc: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/mnt: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/nvram: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/oet: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/root: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/var: Is a directory
cat: /tmp/ddwrt/old/usr/tmp/www: Is a directory
cat: /tmp/ddwrt/old/usr/var/cache: Is a directory
cat: /tmp/ddwrt/old/usr/var/logs: Is a directory
cat: /tmp/ddwrt/old/usr/var/run: Is a directory
chad@M4A79XTD-EVO:~$ cat -n /tmp/ddwrt/old/etc/*/*|grep '@import' -A5 -B5
cat: /tmp/ddwrt/old/etc/freeradius/certs: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/modules: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/sites-available: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/sites-enabled: Is a directory
cat: /tmp/ddwrt/old/etc/freeradius/sql: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/extra: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/file_types: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/malware: Is a directory
cat: /tmp/ddwrt/old/etc/l7-protocols/protocols: Is a directory
cat: /tmp/ddwrt/old/etc/openser/dbtext: Is a directory
cat: /tmp/ddwrt/old/etc/privoxy/templates: Is a directory
cat: /tmp/ddwrt/old/etc/terminfo/l: Is a directory
cat: /tmp/ddwrt/old/etc/terminfo/v: Is a directory
cat: /tmp/ddwrt/old/etc/terminfo/x: Is a directory
chad@M4A79XTD-EVO:~$ cat -n /tmp/ddwrt/old/usr/*/*|grep '@import' -A5 -B5
cat: /tmp/ddwrt/old/usr/etc/mc: Is a directory
cat: /tmp/ddwrt/old/usr/etc/tor: Is a directory
cat: /tmp/ddwrt/old/usr/lib/asterisk: Is a directory
cat: /tmp/ddwrt/old/usr/lib/daq: Is a directory
cat: /tmp/ddwrt/old/usr/libexec/nocat: Is a directory
cat: /tmp/ddwrt/old/usr/lib/firmware: Is a directory
cat: /tmp/ddwrt/old/usr/lib/lighttpd: Is a directory
cat: /tmp/ddwrt/old/usr/lib/mc: Is a directory
cat: /tmp/ddwrt/old/usr/lib/openser: Is a directory
cat: /tmp/ddwrt/old/usr/lib/snort_dynamicengine: Is a directory
cat: /tmp/ddwrt/old/usr/lib/snort_dynamicpreprocessor: Is a directory
cat: /tmp/ddwrt/old/usr/lib/squid: Is a directory
Binary file (standard input) matches
chad@M4A79XTD-EVO:~$ cat -n /tmp/ddwrt/old/{usr,etc}/*/*|grep '@import' -A5 -B5
cat: /tmp/ddwrt/old/usr/etc/mc: Is a directory
cat: /tmp/ddwrt/old/usr/etc/tor: Is a directory
cat: /tmp/ddwrt/old/usr/lib/asterisk: Is a directory
cat: /tmp/ddwrt/old/usr/lib/daq: Is a directory
cat: /tmp/ddwrt/old/usr/libexec/nocat: Is a directory
cat: /tmp/ddwrt/old/usr/lib/firmware: Is a directory
cat: /tmp/ddwrt/old/usr/lib/lighttpd: Is a directory
cat: /tmp/ddwrt/old/usr/lib/mc: Is a directory
cat: /tmp/ddwrt/old/usr/lib/openser: Is a directory
cat: /tmp/ddwrt/old/usr/lib/snort_dynamicengine: Is a directory
cat: /tmp/ddwrt/old/usr/lib/snort_dynamicpreprocessor: Is a directory
cat: /tmp/ddwrt/old/usr/lib/squid: Is a directory
Binary file (standard input) matches
```

---

### Post by Vaphell on 2014-03-16
your glob matches and passes some dirs to cat and you get messages on stderr. If you used 2>/dev/null you'd get rid of them
What do you need that cat for in the first place? Can't you just use the glob with grep directly?

---

### Post by pqwoerituytrueiwoq on 2014-03-16
i was trying to find what ever file contains the text i found no idea where it is or what it is called

---

### Post by Vaphell on 2014-03-16
either way try to get rid of cat and use that glob directly with grep. If it makes sense you might also go recursive with -r on /tmp/ddwrt/old/{usr,etc}

---

### Post by pqwoerituytrueiwoq on 2014-03-16
like this i assume, did not know you use grep without pipeing text into it
```
~$ grep '@import' -A5 -B5 -r /tmp/ddwrt/old/{usr,etc}
Binary file /tmp/ddwrt/old/usr/sbin/httpd matches
--
/tmp/ddwrt/old/etc/www-    background:url(/images/bin_bt.gif) center no-repeat;
/tmp/ddwrt/old/etc/www-    cursor:pointer;
/tmp/ddwrt/old/etc/www-}
/tmp/ddwrt/old/etc/www-input.spaceradio {
/tmp/ddwrt/old/etc/www-    margin-right:.4em;
/tmp/ddwrt/old/etc/www:}@import url(layout.css);
/tmp/ddwrt/old/etc/www:@import url(colors.css);
/tmp/ddwrt/old/etc/www-/* Colors */
/tmp/ddwrt/old/etc/www-body {
/tmp/ddwrt/old/etc/www-    background-color:        #CCC;
/tmp/ddwrt/old/etc/www-}
/tmp/ddwrt/old/etc/www-
--
/tmp/ddwrt/old/etc/www-}
/tmp/ddwrt/old/etc/www-
/tmp/ddwrt/old/etc/www-#menuMain ul#menuSubList li:last-child * {
/tmp/ddwrt/old/etc/www-    border:                none; 
/tmp/ddwrt/old/etc/www-    /*border-right:        0px dotted;*/
/tmp/ddwrt/old/etc/www:}@import url(layout.css);
/tmp/ddwrt/old/etc/www:@import url(look.css);
/tmp/ddwrt/old/etc/www:@import url(colors.css);
/tmp/ddwrt/old/etc/www-.overlay_ddwrt {
/tmp/ddwrt/old/etc/www-    background-color: #dddddd;
/tmp/ddwrt/old/etc/www-    filter:alpha(opacity=60);
/tmp/ddwrt/old/etc/www-    opacity: 0.6;
/tmp/ddwrt/old/etc/www-}
```

---

