---
title: "gparted"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by asmolinski on 2014-01-30
I am having trouble installing gparted. From the terminal I type in sudo apt-get install gparted
When I enter the command this is what I get.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gparted : Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

I am not sure what to do.

---

### Post by sudodus on 2014-01-30
The simple solution is to ***use gparted when booted from a live CD/DVD/USB drive***. Gparted actually comes with the Ubuntu install iso files and is available 'out of the box'. Normally you should run it from another device anyway, so it is usually not included in the basic installed systems.

-o-

I have installed gparted into installed systems of Ubuntu 12.04 LTS and into Lubuntu 13.10. Maybe it helps if you run the following commands and then try to install it again

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

and watch for error outputs and warnings. If they seem to finish well, try again with

```
sudo apt-get install gparted
```

---

### Post by Bashing-om on 2014-01-30
asmolinski; Hello,

This:
> 
some required packages have not yet been created
or been moved out of Incoming.

advisory says there "may" be an easy solution, maybe:
Try terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` where the "dist-upgrade" uses apt-get's smart mode to try and resolve dependencies to update installed packages.

If you still error out, provide the complete outputs of the above commands, and we will see where to go from there.

[INDENT][INDENT][INDENT]checks and balances,
[INDENT][INDENT][INDENT]it's all in the process
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

