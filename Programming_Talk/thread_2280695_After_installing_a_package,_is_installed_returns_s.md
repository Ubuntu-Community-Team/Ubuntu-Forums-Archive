---
title: "After installing a package, is_installed returns still False, in python apt"
date: 2015-06-01
forum: Programming Talk
---

### Post by wisdom2 on 2015-06-01
By using python apt, i can install packages. Before and after  installing the package, i updated the cache. However, before and after  installing the package, is_installed returns the same, in other words,  it gives wrong result.

  After installing the package, i need to check whether the package is installed or not. Here is my code :

```

    import apt.cache

    def cache_update():
        cache = apt.cache.Cache()    
        cache.update()
        pkg = cache["p7zip-full"]
        print pkg.is_installed  # prints false

        if pkg.is_installed:
           print "it is already installed. Invalid request! "
           pkg.mark_delete()
        else:
           print "it is not installed.Now you are installing..."
           pkg.mark_install()

        cache.commit()


        print "DONE."
        cache.update()  
        print pkg.is_installed # prints false.



    if __name__ == '__main__':
        cache_update()

```

thanks in advance.

---

### Post by corti-nico on 2015-06-01
> **wisdom2 said:**
> By using python apt, i can install packages. Before and after  installing the package, i updated the cache. However, before and after  installing the package, is_installed returns the same, in other words,  it gives wrong result.

  After installing the package, i need to check whether the package is installed or not. Here is my code :

```

    import apt.cache

    def cache_update():
        cache = apt.cache.Cache()    
        cache.update()
        pkg = cache["p7zip-full"]
        print pkg.is_installed  # prints false

        if pkg.is_installed:
           print "it is already installed. Invalid request! "
           pkg.mark_delete()
        else:
           print "it is not installed.Now you are installing..."
           pkg.mark_install()

        cache.commit()


        print "DONE."
        cache.update()  
        print pkg.is_installed # prints false.



    if __name__ == '__main__':
        cache_update()

```

thanks in advance.

You should reload a Cache object. I don't know exact implementation details of python apt library, but I think that when you instantiate a new Cache object you get a python dictionary, that you can use to read information about packages. These informations are not synced in real time with real package system (for instance if you start your script, the another user install a package, if your object is 'old' you can get a wrong answer).

> 
Dictionary-like package cache.
The APT cache file contains a hash table mapping names of binary packages to their metadata. A Cache object is the in-core representation of the same. It provides access to APTs idea of the list of available packages.


Anyway try a solution like this:
```

#!/usr/bin/python
import apt.cache 

def cache_update():
  cache = apt.cache.Cache()    
  cache.update()
  pkg = cache["p7zip-full"]
  print pkg.is_installed  # prints false

  if pkg.is_installed:
     print "it is already installed. Invalid request! "
     pkg.mark_delete()
  else:
     print "it is not installed.Now you are installing..."
     pkg.mark_install()

  cache.commit()


  print "DONE."
  cache.update()
  cache = apt.cache.Cache()  
  pkg = cache["p7zip-full"] 
  print pkg.is_installed # prints false.



if __name__ == '__main__':
  cache_update()

```

---

