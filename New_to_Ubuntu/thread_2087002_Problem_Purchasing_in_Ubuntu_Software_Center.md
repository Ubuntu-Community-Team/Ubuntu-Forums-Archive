---
title: "Problem Purchasing in Ubuntu Software Center"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by fictionalhippo on 2012-11-22
Hello, I just recently installed Ubuntu and i am still learning. Everything is running great so far as expected, but i am unable to make a purchase in the software center. Whenever i click buy the terms and agreements will not load making it to where i cannot click accept. Is there anything i can do to possibly fix this?

---

### Post by fictionalhippo on 2012-11-23
Hello, I just recently installed Ubuntu and i am still learning. Everything is running great so far as expected, but i am unable to make a purchase in the software center. Whenever i click buy the terms and agreements will not load making it to where i cannot click accept. Is there anything i can do to possibly fix this?

---

### Post by cariboo on 2012-11-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by xannaxprozaxx on 2013-02-14
I have the same problem. Here is what software center gives me if ran from the shell:

On Launch:
```

Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 8: reading configurations from ~/.fonts.conf.d is deprecated.
2013-02-15 03:08:18,608 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-02-15 03:08:18,620 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-02-15 03:08:18,860 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2013-02-15 03:08:19,233 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-02-15 03:08:19,241 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-02-15 03:08:19,241 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-02-15 03:08:19,326 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-02-15 03:08:19,331 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-02-15 03:08:20,568 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-02-15 03:08:20,568 - root - ERROR - Could not find any typelib for Gst

```

A second later:
```

2013-02-15 03:08:30,200 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2013-02-15 03:08:31,140 - softwarecenter.db.update - INFO - 'SCAApplicationParser'.make_doc: skipping region restricted app u"Bulleti d'esquerra de Calonge i Sant Antoni " (region not whitelisted)
2013-02-15 03:08:31,764 - softwarecenter.db.update - INFO - 'SCAApplicationParser'.make_doc: skipping region restricted app u'Comentarios Web' (region not whitelisted)
2013-02-15 03:08:33,145 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-02-15 03:08:33,145 - softwarecenter.db.database - INFO - reopen() database
2013-02-15 03:08:33,145 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

```

Then, when clicking on a non-free app
```

2013-02-15 03:09:45,186 - softwarecenter.db.pkginfo_impl.aptcache - ERROR - simulate failed
None

```

Note that this message does NOT appear if I click on a free software.

---

