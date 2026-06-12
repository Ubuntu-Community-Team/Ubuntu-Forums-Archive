---
title: "no servers can be found"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by haplorrhine on 2013-07-19
My laptop's wifi is using the connection without problems.  The desktop computer, on the other hand, is unable to find any servers, despite being connected to the wired network through the AT&T modem.  No luck with firefox, update-manager, or software-center.  The latter two warned of untrusted packages, but, as I don't use the desktop computer, I don't know whether its "untrusted packages" problem is old or recent.
I got a terminal reading as I attempted to download chromium through the software center.

2013-07-19 18:49:43,357 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-07-19 18:49:43,361 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-07-19 18:49:43,415 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-07-19 18:49:43,838 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-07-19 18:49:43,998 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-07-19 18:49:44,007 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py:41: Warning: value "101.000000" of type `gdouble' is invalid or out of range for property `value' of type `gint'
  context.iteration()
/usr/lib/python2.7/dist-packages/gi/types.py:43: Warning: value "101.000000" of type `gdouble' is invalid or out of range for property `value' of type `gint'
  return info.invoke(*args, **kwargs)
2013-07-19 18:50:24,014 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 97}']'
2013-07-19 18:50:24,014 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:Unable to find the server at reviews.ubuntu.com
'
2013-07-19 18:50:31,096 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'SoftwareCenterAgentAPI', 'available_apps', '{"lang": "en", "series": "precise", "arch": "i386"}']'
2013-07-19 18:50:31,096 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:Unable to find the server at software-center.ubuntu.com
'
2013-07-19 18:50:31,097 - softwarecenter.db.update - WARNING - error: WARNING:__main__:Unable to find the server at software-center.ubuntu.com

2013-07-19 18:50:31,122 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 1
2013-07-19 18:50:31,644 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'SoftwareCenterAgentAPI', 'exhibits', '{"lang": "en", "series": "precise"}']'
2013-07-19 18:50:31,644 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:Unable to find the server at software-center.ubuntu.com
'

---

### Post by kc5hwb on 2013-07-19
It sounds like you don't have an internet connection.  You will see that "no servers" message in the Ubuntu Software Center or Update Manager when you aren't connected to the web.

Open a Terminal and run *ifconfig *and see if you have a valid IP address.

---

### Post by haplorrhine on 2013-07-20
I'm not getting a "no servers" anywhere.  I was looking at the  terminal's repeated statement of "WARNING:__main__:Unable to find the  server at..."

I don't know what an invalid IP address would be.   ifconfig's output was split into "eth0" (addresses: internet, Bcast, and  mask) and "lo" (internet and mask).




EDIT:  Someone else solved the problem. I'll ask them if they remember how they fixed the problem, then I'll post the solution (and mark the thread as SOLVED).

---

