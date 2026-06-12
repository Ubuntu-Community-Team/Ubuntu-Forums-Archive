---
title: "wxPython Bundling"
date: 2008-11-19
forum: Programming Talk
---

### Post by themusicwave on 2008-11-19
One of my very minor work tasks is converting old Dos batch files to something new.  For this I have been using Python.  For the GUI when needed, I have been using TKinter, however I really want to give wxWidgets a try.  It looks much more promising.

My only worry is that I need to redistribute these files to users/colleagues who aren't always great with installing things.  I don't want them to have to install Python, then wxWidgets...

I've got the python install covered, by sending the /quiet flag to the MSI installer.  However, with wxPython's installer this trick does not work.

I know it is possible to bundle wxWdigets with an application, because PostgreSQL's PG Admin III program uses it.

How would I go about bundling wxPython with a Python application so they don't need to use the installer?

I have my own installer that I wrote, ironically in Python to install the application.  I used py2exe to compile it to an exe so it can install Python.  I'd like to add the ability to install wxWidgets to it as well.

Any Ideas?

---

