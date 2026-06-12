---
title: "Thunderbird freezes system.  Tried reinstall."
date: 2019-03-01
forum: New to Ubuntu
---

### Post by richard378 on 2019-03-01
Hi,
Ubuntu 18.04 LTS duel boot. My thunderbird email client freezes my system with just one Gmail account added. I want to add more accounts, but the one account freezes the whole system when updading folders. I tried to purge it and delete Home folder config files and reinstall. This did not help. My system totally freezes and is unusable when thunderbird is running. Please help. I want to use thunderbird.  This happens on multible machines.  Desktop and two laptops.

---

### Post by DuckHook on 2019-03-02
> **richard378 said:**
> …This happens on multible machines.  Desktop and two laptops.
Very strange. Did you use the same install media on all machines? If so, you may have a corrupted image.

[LIST]
[*]Try downloading a new ISO and running a LiveUSB session with your gmail account added to Tbird.
[*]Make sure your T-bird settings are correct, especially server/port settings.
Instructions here: [https://support.mozilla.org/en-US/kb/thunderbird-and-gmail](https://support.mozilla.org/en-US/kb/thunderbird-and-gmail)
and here: [https://support.mozilla.org/en-US/kb/manual-account-configuration](https://support.mozilla.org/en-US/kb/manual-account-configuration)
[*]Launch T-bird from the command line to see error messages generated.
[*]Anything unusual in your logs?
[/LIST]

---

### Post by walts48 on 2019-03-03
> **richard378 said:**
> 
  This happens on multible machines.  Desktop and two laptops.

Do you have the same extensions installed in Thunderbird on all machines?

Does the problem go away if you restart in safe mode?

[https://support.mozilla.org/en-US/kb/safe-mode-thunderbird](https://support.mozilla.org/en-US/kb/safe-mode-thunderbird)

---

### Post by richard378 on 2019-03-03
I did a purge thunderbird reinstall. Not OS reinstall. It still has the same freeze affect when I run in safe mode with addons disabled. It had a unity launcher addon which I removed. It does not seem to have a gnome intergration extension installed.

Get the following on the command line:

1551639249913 addons.xpi WARN Can't get modified time of /usr/lib/thunderbird/features/wetransfer@extensions.thunderbird.net
*** UTM:SVC TimerManager:registerTimer called after profile-before-change notification. Ignoring timer registration for id: telemetry_modules_ping

I checked my firewall. My UFW was blocking the ports causing the error. I fixed the ports and it is no longer having a problem that I can notice. Strange that the firewall was causing my system to freeze. 
S

---

### Post by ajgreeny on 2019-03-03
Try closing thunderbird, renaming the hidden ~/.thunderbird folder in your home, then restarting tunderbird; it could be a corrupt configuration causing the freeze.

All your saved old mail will still be in the old now renamed .thunderbird folder if you need it.

---

### Post by richard378 on 2019-03-05
I already did delete the configuration files in my home folder.  It was one of the first things I tried.  It is working now.

---

