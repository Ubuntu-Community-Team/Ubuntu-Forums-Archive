---
title: "Update via command line errors modifiy tempfiles.d what does this mean?"
date: 2019-03-08
forum: New to Ubuntu
---

### Post by richard378 on 2019-03-08
I have the following errors updating Ubuntu 18.10. I was runing 18.04 LTS duel boot but it failed to boot up and I learned it was having ACPI errors because the kernel was not updated enough. Ubuntu 18.10 seems to work so far after the other install quit on me. In my rush to install I did the initial update on the command line. sudo apt update && sudo apt upgrade and got the following message which has affected boot logs with similar messages.

```
Setting up systemd (239-7ubuntu10.8) ...
[/usr/lib/tmpfiles.d/speech-dispatcher.conf:1] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher &#8594; /run/speech-dispatcher; please update the tmpfiles.d/ drop-in file accordingly.
[/usr/lib/tmpfiles.d/speech-dispatcher.conf:2] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/.cache &#8594; /run/speech-dispatcher/.cache; please update the tmpfiles.d/ drop-in file accordingly.
[/usr/lib/tmpfiles.d/speech-dispatcher.conf:3] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/.speech-dispatcher &#8594; /run/speech-dispatcher/.speech-dispatcher; please update the tmpfiles.d/ drop-in file accordingly.
[/usr/lib/tmpfiles.d/speech-dispatcher.conf:4] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/.cache/speech-dispatcher &#8594; /run/speech-dispatcher/.cache/speech-dispatcher; please update the tmpfiles.d/ drop-in file accordingly.
[/usr/lib/tmpfiles.d/speech-dispatcher.conf:5] Line references path below legacy directory /var/run/, updating /var/run/speech-dispatcher/log &#8594; /run/speech-dispatcher/log; please update the tmpfiles.d/ drop-in file accordingly.
[/usr/lib/tmpfiles.d/spice-vdagentd.conf:2] Line references path below legacy directory /var/run/, updating /var/run/spice-vdagentd &#8594; /run/spice-vdagentd; please update the tmpfiles.d/ drop-in file accordingly.
Setting up openssl (1.1.1-1ubuntu2.1) ...

```

Update:
Never mind I figured it out.  I simply delted /var from the tmpfile.d files.  This removed the boot log notations.

---

