---
title: "postinst script not working"
date: 2014-02-06
forum: Packaging and Compiling Programs
---

### Post by Jacobonbuntu on 2014-02-06
Dear people,
I feel kind of stupid, I am not at all into bash but this must be simple: I have a simple postinst script for my package that should run a script, located in /usr/share/qle2. When I try running the script "dry" it works fine. Packaged along with my deb file it doesn't. I tried giving the script other functionality (copying silly stuff) and it works fine. Where am I ging wrong?
```
#!/bin/bash
set -euf -o pipefail
python3 /usr/share/qle2/update_qledtfile.py
```
I need the script to edit the (possible) local desktop file. The application is also distributed by a ppa. I want to change the file layout of the application, and need to change the execute line in the (possibly present) local desktop file, to prevent mismatches.
(sorry for the long sentence ;))

---

### Post by Jacobonbuntu on 2014-02-06
OK, I probably get it... 
This is a huge blackout in my mind. The installer runs from root, the python script I am referring to edits a file in the current user's directory...

edit:
it turned out to be true, I changed the script to edit the desktopfiles of my application for all users it can find in /home and it works perfectly!

---

