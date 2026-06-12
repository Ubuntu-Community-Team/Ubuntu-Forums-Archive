---
title: "_winreg in Python"
date: 2010-11-10
forum: Programming Talk
---

### Post by 7raTEYdCql on 2010-11-10
I'm trying to fetch values from a windows registry, using _winreg module in python.

This is function, which fetches a registry value:

```

def get_registry_value(sub_key, value_name):
	registry = _winreg.ConnectRegistry(None, _winreg.HKEY_LOCAL_MACHINE)
	key = _winreg.OpenKey(registry, sub_key)
	
	value = _winreg.QueryValueEx(key, value_name)

	_winreg.CloseKey(key)
	_winreg.CloseKey(registry)

	return value

```

Now when I pass, subkey = SOFTWARE\Microsoft\Internet Explorer\UnattendBackup\TrustedSites and value = 'TrustedSites' to the given function it returns a null string.

I checked for other key_value pairs it was returning proper values.

Any exceptions to what the length of the value can be? Cause, this is a string containing all TrustedSites on IE. Every other case on which I've tested this function, it has been relatively short string.

Any other forum on which I can ask this doubt, where it would be more appropriate?

---

### Post by 7raTEYdCql on 2010-11-10
This was executed on Windows Storage Server 2008 R2

---

### Post by Tony Flury on 2010-11-10
Is there a chance that that value is actually a list of values - and not one big string ?

Do you need to used EnumKey or EnumValue on your open key to get all the sub values ? 

Try calling QueryInfoKey in your open key and see if there are any subkeys 

[http://docs.python.org/library/_winreg.html](http://docs.python.org/library/_winreg.html)

---

### Post by 7raTEYdCql on 2010-11-19
Thank you so much Tony, that was indeed of good help.

---

