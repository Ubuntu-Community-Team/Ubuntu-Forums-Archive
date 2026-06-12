---
title: "Getting Console / Terminal Text With PID"
date: 2017-01-29
forum: Programming Talk
---

### Post by flashc5 on 2017-01-29
[COLOR=#333333]Hello,[/COLOR]

[COLOR=#333333]I have a linux pc that will run a console terminal (3rd party app) that I want to monitor the output of and alert me of certain conditions.[/COLOR]

[COLOR=#333333]Is there a way to get the output of the console/terminal with just the pid id? I read about stdout but that requires you to start the process which I cannot always do. How can I get the output of the window when all I have is the PID?[/COLOR]

[COLOR=#333333]Thanks in advance.[/COLOR]

---

### Post by Habitual on 2017-01-30
Is the 3rd party app "logging to file"?
You can lsof -p <pid_of_app> but that won't like let you see it's output.
lsof -p <pid> will show you what files the process has open.

More "in" More "out".... :)

---

