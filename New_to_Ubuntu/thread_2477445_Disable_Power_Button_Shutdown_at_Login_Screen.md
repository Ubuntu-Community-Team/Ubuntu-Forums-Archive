---
title: "Disable Power Button Shutdown at Login Screen"
date: 2022-07-25
forum: New to Ubuntu
---

### Post by stuartsparks on 2022-07-25
Hi All,

I'm hoping someone can help me resolve this.
We need to stop the physical power button from shutting down our Ubuntu 22.04 LTS desktop when it's at the login screen.
As the GUI settings to set Power Button Action = Nothing, only applies to the particular user that is logged on.

This is for a remote machine that we have no physical access to and has very limited outbound connectivity, so we cannot download a new application to it.

I've tried several online guides for editing various conf files, that mostly don't seem to exist on v22.04, as it seems the login screen process / account has changed over the years.
I thought I was getting somewhere when I changed the settings for - 
"gsettingsset org.gnome.settings-daemon.plugins.power power-button-action nothing"

But unfortunately this still doesn't have any effect at the logon screen

This surely must be an easily changeable setting as I would think Ubunu desktop is used in many operational environments where we don't want accidental shutdown.

Could anyone advise a known working resolution for this please?

Many Thanks in advance.

---

### Post by Irihapeti on 2022-07-25
*Post moved to **New to Ubuntu**, as it's a request for technical support.*

---

