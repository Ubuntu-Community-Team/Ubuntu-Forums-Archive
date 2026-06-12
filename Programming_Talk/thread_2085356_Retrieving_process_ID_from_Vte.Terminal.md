---
title: "Retrieving process ID from Vte.Terminal"
date: 2012-11-17
forum: Programming Talk
---

### Post by kiplingw on 2012-11-17
I am using Python 3 with GObject introspection to create a Vte.Terminal widget. Up to date and reliable documentation on this widget is scarce. If one uses the fork_command_full() method to create a child process in the aforementioned terminal widget, how does one then retrieve the child process ID? 

Version 0.26 of the Vte.Terminal documentation claims there is a 9th parameter to fork_command_full() method which is used to store the child's process ID, but my implementation claims there is no such parameter.

Any help appreciated.

---

