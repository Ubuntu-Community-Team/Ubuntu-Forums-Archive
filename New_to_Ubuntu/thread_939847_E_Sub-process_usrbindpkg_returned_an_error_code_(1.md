---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) problems"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Zatarg on 2008-10-06
I installed GHC6 and emacs, but when trying to compile an .hs file I got an error that it could not import an appropriate OpenGL module. From what i can tell, this should be a standard module and should not be missing. So I tried uninstalling it all and im having some problems with the package 

libghc6-cairo-dev

running sudo apt-get remove ghc6
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  haddock
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  ghc6 libghc6-cairo-dev libghc6-glib-dev libghc6-mtl-dev
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 136MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153419 files and directories currently installed.)
Removing libghc6-cairo-dev ...
ghc-pkg: cannot find package cairo-0.9.12.1
dpkg: error processing libghc6-cairo-dev (--remove):
 subprocess pre-removal script returned error exit status 1
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/cairo-0.9.12.1/cairo.package.conf" ... done.
WARNING: unversioned dependencies are deprecated, and will NOT be accepted by GHC 6.10: base
ghc-pkg: dependency mtl-1.1.0.0 doesn't exist (use --force to override)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing libghc6-mtl-dev ...
Saving old package config file... done.
Writing new package config file... done.
Removing libghc6-glib-dev ...
Saving old package config file... done.
Writing new package config file... done.
Removing ghc6 ...
Errors were encountered while processing:
 libghc6-cairo-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

running sudo apt-get -f install 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  haddock
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libghc6-cairo-dev (0.9.12.1-1ubuntu2) ...
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/cairo-0.9.12.1/cairo.package.conf" ... done.
WARNING: unversioned dependencies are deprecated, and will NOT be accepted by GHC 6.10: base
ghc-pkg: dependency mtl-1.1.0.0 doesn't exist (use --force to override)
dpkg: error processing libghc6-cairo-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libghc6-cairo-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

