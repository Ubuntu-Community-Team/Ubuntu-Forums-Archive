---
title: "No functions can be imported from apt module (Python)"
date: 2010-01-26
forum: Programming Talk
---

### Post by Jekshadow on 2010-01-26
I am trying to use python-apt, and it seems like there are no functions available when I import any of the apt modules (apt_pkg, aptsources, apt, etc.). 

Anybody know what is going on?

---

### Post by Can+~ on 2010-01-26
Mine works, what exactly are you trying to do? (And with what version of python).

---

### Post by Jekshadow on 2010-01-26
> **Can+~ said:**
> Mine works, what exactly are you trying to do? (And with what version of python).

Right now, I am just trying to get it to work, and I'm using Python 2.6.

Here is an example of what happens:
```

>>> import apt_pkg
>>> apt_pkg.init_config()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'init_config'

```

---

### Post by Can+~ on 2010-01-26
[PHP]>>> dir(apt_pkg)
['Base64Encode', 'CheckDep', 'CheckDomainList', 'Config', 'CurStateConfigFiles', 'CurStateHalfConfigured', 'CurStateHalfInstalled', 'CurStateInstalled', 'CurStateNotInstalled', 'CurStateUnPacked', 'Date', 'DeQuoteString', 'DepConflicts', 'DepDepends', 'DepObsoletes', 'DepPreDepends', 'DepRecommends', 'DepReplaces', 'DepSuggests', 'GetAcquire', 'GetCache', 'GetCdrom', 'GetDepCache', 'GetLock', 'GetPackageManager', 'GetPkgAcqFile', 'GetPkgActionGroup', 'GetPkgProblemResolver', 'GetPkgRecords', 'GetPkgSourceList', 'GetPkgSrcRecords', 'InitConfig', 'InitSystem', 'InstStateHold', 'InstStateHoldReInstReq', 'InstStateOk', 'InstStateReInstReq', 'LibVersion', 'ParseCommandLine', 'ParseDepends', 'ParseSection', 'ParseSrcDepends', 'ParseTagFile', 'PkgSystemLock', 'PkgSystemUnLock', 'PriExtra', 'PriImportant', 'PriOptional', 'PriRequired', 'PriStandard', 'QuoteString', 'ReadConfigDir', 'ReadConfigFile', 'ReadConfigFileISC', 'RewritePackageOrder', 'RewriteSection', 'RewriteSourceOrder', 'SelStateDeInstall', 'SelStateHold', 'SelStateInstall', 'SelStatePurge', 'SelStateUnknown', 'SizeToStr', 'StrToTime', 'StringToBool', 'Time', 'TimeRFC1123', 'TimeToStr', 'URItoFileName', 'UpstreamVersion', 'Version', 'VersionCompare', '__doc__', '__file__', '__name__', '__package__', 'init', 'md5sum', 'newConfiguration', 'sha1sum', 'sha256sum'][/PHP]

Seems that they prefer the CamelCase instead of underscores.

[PHP]apt_pkg.InitConfig()[/PHP]

---

### Post by Jekshadow on 2010-01-26
> **Can+~ said:**
> [PHP]>>> dir(apt_pkg)
['Base64Encode', 'CheckDep', 'CheckDomainList', 'Config', 'CurStateConfigFiles', 'CurStateHalfConfigured', 'CurStateHalfInstalled', 'CurStateInstalled', 'CurStateNotInstalled', 'CurStateUnPacked', 'Date', 'DeQuoteString', 'DepConflicts', 'DepDepends', 'DepObsoletes', 'DepPreDepends', 'DepRecommends', 'DepReplaces', 'DepSuggests', 'GetAcquire', 'GetCache', 'GetCdrom', 'GetDepCache', 'GetLock', 'GetPackageManager', 'GetPkgAcqFile', 'GetPkgActionGroup', 'GetPkgProblemResolver', 'GetPkgRecords', 'GetPkgSourceList', 'GetPkgSrcRecords', 'InitConfig', 'InitSystem', 'InstStateHold', 'InstStateHoldReInstReq', 'InstStateOk', 'InstStateReInstReq', 'LibVersion', 'ParseCommandLine', 'ParseDepends', 'ParseSection', 'ParseSrcDepends', 'ParseTagFile', 'PkgSystemLock', 'PkgSystemUnLock', 'PriExtra', 'PriImportant', 'PriOptional', 'PriRequired', 'PriStandard', 'QuoteString', 'ReadConfigDir', 'ReadConfigFile', 'ReadConfigFileISC', 'RewritePackageOrder', 'RewriteSection', 'RewriteSourceOrder', 'SelStateDeInstall', 'SelStateHold', 'SelStateInstall', 'SelStatePurge', 'SelStateUnknown', 'SizeToStr', 'StrToTime', 'StringToBool', 'Time', 'TimeRFC1123', 'TimeToStr', 'URItoFileName', 'UpstreamVersion', 'Version', 'VersionCompare', '__doc__', '__file__', '__name__', '__package__', 'init', 'md5sum', 'newConfiguration', 'sha1sum', 'sha256sum'][/PHP]

Seems that they prefer the CamelCase instead of underscores.

[PHP]apt_pkg.InitConfig()[/PHP]

Ah, thanks, I had just been looking at [http://apt.alioth.debian.org/python-apt-doc/](http://apt.alioth.debian.org/python-apt-doc/) as a guide, and it showed underscores.

---

