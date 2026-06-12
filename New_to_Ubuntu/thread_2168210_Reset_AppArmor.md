---
title: "Reset AppArmor"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by ConcreteDonkey on 2013-08-16
After trying to configure AppArmor it seems I may have made a few mistakes during configuration, as such I'm wondering if there's a command that I can run that will completely reset all AppArmor profiles to their default, exactly the way they came during installation?

---

### Post by meilin on 2013-08-17
[COLOR=#333333][FONT=Ubuntu]*AppArmor*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] profiles are simple text files located in [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/apparmor.d/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]. The files are named after the full path to the executable they profile replacing the "/" with ".". For example [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/apparmor.d/bin.ping[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] is the AppArmor profile for the [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/bin/ping[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] command.  Read this [ubuntu documents]("https://help.ubuntu.com/13.04/serverguide/apparmor.html")[/FONT][/COLOR]

---

### Post by ConcreteDonkey on 2013-08-17
So I should just do:

sudo apt-get purge apparmor-profiles
sudo apt-get install apparmor-profiles

And it will be back to normal?

---

### Post by pasqoo on 2014-04-11
I booted up an old ubuntu installation (12.04) and noticed some apparmor warnings during the boot.
I too would like to reset the configuration of this software, to be sure it's working with the default settings (which should be good enough for this system) and then maybe do my editing if I'd like to.
Do those two commands do the job?

Thanks

---

