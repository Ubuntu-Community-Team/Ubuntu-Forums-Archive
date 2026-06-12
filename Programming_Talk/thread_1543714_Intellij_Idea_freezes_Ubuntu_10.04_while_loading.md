---
title: "Intellij Idea freezes Ubuntu 10.04 while loading"
date: 2010-08-01
forum: Programming Talk
---

### Post by angelinux on 2010-08-01
Hi all,

I'm having a strange behaviour on a Ubuntu box in which i have migrated to Lucid.

The well known Intellij Idea does not starts, it freezes the whole box.

In another box I have no trouble but I can't find any difference. Only difference is that the first box has many years and it was migrated between three-four releases of ubuntu (at least) while the working one is born with Lucid.

[LIST]
[*]The Java VM is updated (sun one, but open jdk has the same effect)
[*]The issue does not seem to be related to the VM that definitively works with all other applications
[*]The issue does not seem to be related to the specific Idea version, I tested on three of them, having the same behaviour
[*]I tried to remove and reinstall the VM, all configuration data for the application, no changes at all
[/LIST]

The ENTIRE MACHINE freezes after few seconds launching the idea startup script, with no error message, no warning, nothing at all.

Do someone experimented the same behaviour??

Angelo

---

### Post by angelinux on 2010-08-06
I finally found that launching idea with the nosplash option, the issue does not appear, so I kept this as a workaround.

Maybe some graphical libraries have troubles;)

---

