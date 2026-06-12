---
title: "Which folder for script that executes after computer resumes from hibernate/susp"
date: 2015-12-18
forum: Programming Talk
---

### Post by J_Me on 2015-12-18
I need to delete a plain text file(via a script) when the computer resumes from hibernate/suspend but I'm not sure where to put the script. Reading around the web it's been suggested to use one of these folders[br]1[/br] /lib/systemd/system-sleep/my-script[br]1[/br] /usr/lib/pm-utils/sleep.d/my-script[br]1[/br] [br]1[/br] But I don't want to mess things up so thought it best to ask here.[br]1[/br] [br]1[/br] The intended script to use[br]1[/br] --------------------------[br]1[/br] #!/bin/bash[br]1[/br] sleep 30[br]1[/br] rm /tmp/my-temp-file[br]1[/br] ----------------------------[br]1[/br] [br]1[/br] Also it's been mentioned to name the script something like 999zzzMYfile.sh so that it executes last, rather than doing this and potentially messing with the operating system can't I just put in a 'sleep 30' and have the script wait until things have settled.[br]1[/br] [br]1[/br] Thanks

---

### Post by ian-weisser on 2015-12-18
If you are really running 14.04, then you are using Upstart, not systemd.
Have you looked at the working examples in /usr/lib/pm-utils/sleep.d/ ?

Sleeping 30 seconds for the system to settle seems a bit kludgy. If you tell us what you are trying to do, we may be able to suggest another way.
If you pick an unfortunate filename, you might *prevent* the system from settling by blocking later tasks in the resume order.

---

