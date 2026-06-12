---
title: "Eclectus in Ubuntu 11.04"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2012-02-10
I recently updated my ubuntu 10.04 netbook remix to ubuntu 11.04 through ubuntu 10.10. ubuntu 11.04 uses python 2.7 where as eclectus depends on python 2.6. so i tried to install electus from source code when i tried to invoke eclectus from terminal i got the following on the terminal but the program did not start


> sudarshan@sudarshan-laptop:~$ eclectus
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
Writing to db: sqlite:////home/sudarshan/.kde/share/apps/eclectus/dictionaries.db
Attached db: cjklib, sqlite:////usr/local/lib/python2.7/dist-packages/libeclectus/libeclectus.db, sqlite:////usr/local/share/eclectus/cmn-caen-tan/cmn-caen-tan.db, sqlite:////usr/local/share/eclectus/chi-balm-hsk1/chi-balm-hsk1.db
Traceback (most recent call last):
  File "/usr/local/lib/python2.7/dist-packages/eclectusqt/renderthread.py", line 334, in run
    classInstance = entryClassObject(*args, **param)
  File "/usr/local/lib/python2.7/dist-packages/libeclectus/characterinfo.py", line 199, in __init__
    self.db = DatabaseConnector.getDBConnector(configuration)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/util.py", line 702, in new_func
    return func(*args, **kwargs)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/dbconnector.py", line 142, in getDBConnector
    return getDBConnector(configuration, projectName)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/dbconnector.py", line 84, in getDBConnector
    _dbconnectInst = DatabaseConnector(databaseSettings)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/dbconnector.py", line 219, in __init__
    for url in self._findAttachableDatabases(attach, searchPaths):
  File "/usr/local/lib/python2.7/dist-packages/cjklib/dbconnector.py", line 251, in _findAttachableDatabases
    configuration = getDefaultConfiguration(name)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/dbconnector.py", line 105, in getDefaultConfiguration
    configuration = getConfigSettings('Connection', projectName)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/util.py", line 81, in getConfigSettings
    libdir = locateProjectFile(projectName, projectName)
  File "/usr/local/lib/python2.7/dist-packages/cjklib/util.py", line 56, in locateProjectFile
    return resource_filename(Requirement.parse(projectName), relPath)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 869, in resource_filename
    self, resource_name
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1148, in get_resource_filename
    return self._fn(self.module_path, resource_name)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1226, in _fn
    return os.path.join(base, *resource_name.split('/'))
  File "/usr/lib/python2.7/posixpath.py", line 68, in join
    elif path == '' or path.endswith('/'):
AttributeError: 'NoneType' object has no attribute 'endswith'


---

### Post by rrashkin on 2012-02-10
That doesn't sound right to me.  Python 2.7 should be compatible with everything written for Python 2.6.

From the message, I suspect you're referring to an erroneous path.

---

### Post by 1991sudarshan on 2012-02-10
> **rrashkin said:**
> That doesn't sound right to me.  Python 2.7 should be compatible with everything written for Python 2.6.

From the message, I suspect you're referring to an erroneous path.

Do I have to recompile from the source code to rectify the erroneous path?

---

