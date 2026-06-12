---
title: "How To: Legacy ATI TV out on boot"
date: 2010-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Thelasko on 2010-01-19
Users of legacy ATI cards with S-video out can either use GATOS or atitvout to use this feature.  The following are instructions for using atitvout.  I use this to make my MythTV box display to the TV on boot.

**This method does make changes to system files and is not recommended for users new to Ubuntu.**

[LIST=1]
[*]Install atitvout ```
sudo apt-get install atitvout
```

[*]Open the terminal and determine which commands work with your card.  For my card I use: ```
sudo atitvout -f t
```

[*]Use your favorite text editor to create a script containing the command you used to get tv out to function correctly.  Note that all scripts start with "#!/bin/bash" followed by the commands you wish to run.  Therefore my script is:  ```
#!/bin/bash
sudo atitvout -f t
``` Then save the script.

[*]Make the script executable by right clicking>properties>permissions>make executable. or you can use chmod.  (**Please test this script before continuing!**)

[*]Using a super user privileges (sudo) copy the script into the etc/init.d directory.  Make sure it is still executable.

[*]Use the following command to make this script execute upon boot:  ```
update-rc.d *scriptname* defaults
```
[/LIST]

Please let me know if I have omitted anything or if you need help.

---

