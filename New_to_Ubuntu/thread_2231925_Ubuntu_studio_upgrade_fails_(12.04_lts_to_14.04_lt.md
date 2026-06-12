---
title: "Ubuntu studio upgrade fails (12.04 lts to 14.04 lts)"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by Bob S on 2014-06-28
Running a pcchips A13G w/ AMD X2 4400+ and 2 gb ddr2

First error says:
"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade."

Then:

"Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'"

Then:

"Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

Then:
"The following packages have unmet dependencies:
flightgear-data-aircrafts: flightgear-data-base: flightgear-data-models: "? 

I don't know what was installing flight gear to cause the dependancies in the first place so I don't know where to look or how to 'resolve' them. My Update Manager now has 3027 updates to be installed and is stuck because it can't install them? Please advise on what to do.
Thanks in advance

---

### Post by Bob S on 2014-06-28
Fixed! Removed filght gear flight simulator through Software Center. (Duh).

---

