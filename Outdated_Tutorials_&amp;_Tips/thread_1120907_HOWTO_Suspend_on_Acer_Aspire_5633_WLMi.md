---
title: "HOWTO: Suspend on Acer Aspire 5633 WLMi"
date: 2009-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by LucaTNT on 2009-04-09
Here is a little howto on getting suspend/hibernate to work on the Acer Aspire 5633 WLMi laptop.

The first thing is to open /etc/default/acpi-support with your favorite editor (of course with sudo) and make sure ACPI_SLEEP and ACPI_HIBERNATE are set to TRUE, while POST_VIDEO and SAVE_VBE_STATE must be set to FALSE.

Then we have to create a script that turns DPMS off and on again, otherwise the screen would stay off, though the rest of the system has correctly resumed.
Create the file /etc/pm/sleep.d/99-dpms-off-on.sh with your favorite editor and put the following lines in it:
```
#!/bin/sh

/usr/lib/pm-utils/functions

sleep 1
case "$1" in
        thaw|resume)
                vbetool dpms off
                vbetool dpms on
                ;;
        *)
                ;;
esac

```
Make the script executable:
```
sudo chmod +x /etc/pm/sleep.d/99-dpms-off-on.sh
```
That's it!

Suspend and hibernate should now work.
If you want to hibernate, make sure your swap partition is big at least as your RAM.

---

