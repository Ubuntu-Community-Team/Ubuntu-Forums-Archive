---
title: "error returned in broken packages repair"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by archp2009 on 2014-02-16
When I go edit repair broken packages in  synapic package manager I get this error:  ```
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23758 package 'genisoimage':
 newline in field name `'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23758 package 'genisoimage':
 newline in field name `'
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23758 package 'genisoimage':
 newline in field name `'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23758 package 'genisoimage':
 newline in field name `'
```
What should I try next?

---

### Post by wildmanne39 on 2014-02-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by plucky on 2014-02-17
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 23758 package 'genisoimage':
 newline in field name `'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

Open a terminal and ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-broken
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

The first line renames the "status" file to status-broken"
The second line copies the file "status-old" and creates the file "status", hopefully from a file that isn't broken.

Then run ```
sudo apt-get update && sudo apt-get upgrade
``` and see if you get any errors.

Good Luck

---

