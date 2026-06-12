---
title: "Creating a bogus script to override another script"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by adhanali on 2008-10-06
Hello,
I came across a post to fix the ticking sound my harddrive makes [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement). I was able to follow all the directions except the last one

> Create a bogus /etc/pm/power.d/laptop-tools script to override /usr/lib/pm-utils/power.d/laptop-tools

Unfortunately, I have no clue what that means. Do I create a blank file named /etc/pm/power.d/laptop-tools or is there something else I need to do?

Any help would be much appreciated,
Ali

---

### Post by lukjad on 2008-10-10
Which version of Ubuntu are you using? If it is Intrepid I think there is a specific subforum for beta-testers. As far as I see, this step is only for Intrepid.

---

### Post by adhanali on 2008-10-10
Hi,
I am using Hardy Heron (8.04). The wiki page linked in my original post is specifically for fixing disk-idling in Hardy Heron (8.04). The page does mention though which fixes will be done by default in Intrepid Ibex (8.10). 

The complete instructions are
> To correct disk-idleing in Ubuntu 8.04 you need to adjust the following:
    * Enable CONTROL_HD_POWERMGMT=1 in /etc/laptop-mode/laptop-mode.conf          
    * ENABLE_LAPTOP_MODE=true in /etc/default/acpi-support So that laptop-mode-tools can control the harddisk power management settings.          
    * Delete or #comment the four $HDPARM blocks (for...done) in /etc/acpi/power.sh and change the two $LAPTOP_MODE start/stop lines to "$LAPTOP_MODE auto"          
    * Create a bogus /etc/pm/power.d/laptop-tools script to override /usr/lib/pm-utils/power.d/laptop-tools.
          
With the above changes hardy (ubuntu 8.04) will set the hdparm -B value to 254 when booting and thus override inadequately aggressive hardware defaults that cause load cycling.

I can follow the first 3 parts, the last instruction about creating the bogus script though is a little too cryptic for me.

---

### Post by bodhi.zazen on 2008-10-10
I guess a bogus script = a script that does nothing.

```
gksu /etc/pm/power.d/laptop-tools
```

Put 2 lines in the 'script"

> #!/bin/bash

Exit 0

---

