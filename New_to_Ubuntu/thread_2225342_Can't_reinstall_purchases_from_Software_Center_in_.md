---
title: "Can't reinstall purchases from Software Center in 14.04"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-05-21
Hi Guys,

When I try to reisntall purchases from the Software Center is seems that nothing happens.
I think the problem is with the software center login.  I am not given the oppertunity to login.

When I run the Software Center from the terminal and then attempt to restore purchases I get this:

```

$ software-center
2014-05-21 08:26:51,017 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
2014-05-21 08:26:51,188 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-05-21 08:26:51,488 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2014-05-21 08:26:52,065 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-05-21 08:26:52,068 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2014-05-21 08:26:52,076 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2014-05-21 08:26:52,076 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2014-05-21 08:26:52,202 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2014-05-21 08:26:52,893 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2014-05-21 08:26:52,893 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 62 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
/usr/bin/software-center:184: Warning: Source ID 107 was not found when attempting to remove it
  Gtk.main()
2014-05-21 08:26:59,081 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
2014-05-21 08:27:04,261 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 228 was not found when attempting to remove it
  GLib.source_remove(self._timeout)
2014-05-21 08:27:19,213 - softwarecenter.backend.login_impl.login_sso - ERROR - _on_credentials_error for Ubuntu One: dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'GUINotAvailableError'), dbus.String(u'message'): dbus.String(u'Can not find a GUI to present to the user (tried with "(\'ubuntu-sso-login-qt\', \'ubuntu-sso-login-qt\')"). Aborting.')}, signature=dbus.Signature('ss')) ()
2014-05-21 08:27:19,214 - softwarecenter.backend.login_impl.login_sso - ERROR - _on_credentials_error for Ubuntu One: dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'GUINotAvailableError'), dbus.String(u'message'): dbus.String(u'Can not find a GUI to present to the user (tried with "(\'ubuntu-sso-login-qt\', \'ubuntu-sso-login-qt\')"). Aborting.')}, signature=dbus.Signature('ss')) ()
2014-05-21 08:27:19,214 - softwarecenter.backend.login_impl.login_sso - ERROR - _on_credentials_error for Ubuntu One: dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'GUINotAvailableError'), dbus.String(u'message'): dbus.String(u'Can not find a GUI to present to the user (tried with "(\'ubuntu-sso-login-qt\', \'ubuntu-sso-login-qt\')"). Aborting.')}, signature=dbus.Signature('ss')) ()
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py:404: Warning: Source ID 289 was not found when attempting to remove it
  GLib.source_remove(self._timeout)


```

I would really appreciate any help I can get.  I found one post that mentioned going to passwords and keys in the dash, but this machine is running Xubuntu and I could not find anything related to passwords and keys in the settings manager.

---

### Post by GrouchyGaijin on 2014-05-21
I figured it out.  I installed ubuntu-sso-client-qt  and was able to login to the Software Center and install my previous purchases.

---

### Post by d-evan on 2014-07-02
Thanks!  First nstalling ubuntu-sso-client-qt from the software center worked for me too.

---

