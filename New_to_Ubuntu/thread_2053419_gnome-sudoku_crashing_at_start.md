---
title: "gnome-sudoku crashing at start"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by erichgamba on 2012-09-05
When I tried to run gnome-sudoku on kubuntu 12.04 it immediately crashed. I got the following message:

ERROR:root:Could not find any typelib for LaunchpadIntegration

and another one I don't remember.


The problem was solved by installing two missing dependencies:

python-gi-cairo

and

gir1.2-launchpad-integration-3.0

---

