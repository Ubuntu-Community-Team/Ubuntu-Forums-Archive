---
title: "HOWTO: Apple iOS Backup Aqueduct Game Save With SSH (Jailbreak Only)"
date: 2010-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by bashologist on 2010-11-21
Couldn't find any info on backing up this game so I'm writing a tutorial.
For other games you could probably do the same basic thing but I havn't tested it.

Tested using Ubuntu and an iPad.

Install the ssh server on your iOS device then use your ssh client to access the device.
Make sure to change both your root password and your mobile passwords.
Replace x.x.x.x with your devices ip address.

Changing default passwords:
```

ssh root@x.x.x.x
passwd root
# enter new password here
passwd mobile
# enter new password here
exit

```
Safe passwordless login:
```

ssh-keygen
ssh-copy-id mobile@x.x.x.x
# enter your mobile password here

```
Make a backup:
```

mkdir "Aqueduct Backup/"
scp -rp "mobile@x.x.x.x:/private/var/mobile/Applications/*/Aqueduct.app/../Documents/" "Aqueduct Backup/"
# enter your mobile password here

```
Restore from backup:
```

scp -rp "Aqueduct Backup/Documents/" "mobile@x.x.x.x:/private/var/mobile/Applications/*/Aqueduct.app/../"
# enter your mobile password here

```

Looks like a lot of stuff just to backup some files but it's really just two commands to backup then one to restore once you got the ssh server setup.

---

