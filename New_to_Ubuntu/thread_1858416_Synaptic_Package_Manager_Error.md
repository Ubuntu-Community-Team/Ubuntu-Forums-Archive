---
title: "Synaptic Package Manager Error"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Gattslinc on 2011-10-12
Hi everyone,
I am new to Linux ubuntu 11.04 and experiencing a problem.Whenever i try to start Synaptic Package Manager, i get the erro below;


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How can i correct it?
And i need to install Lamp so that i can work with Joomla.
What is the best way to go about it?

Any kind of help will be greatly appreciated.

---

### Post by Immolatus on 2011-10-12
The error message has offered a solution:

'sudo dpkg --configure -a' to correct the problem. 

run this in a terminal without the quotes.

dpkg is a utility that installs-uninstalls programs. The "-a" option clears it's cache to get the error out of the way. This happens a lot if you have a slow network connection or if the server times out for some reason.

---

