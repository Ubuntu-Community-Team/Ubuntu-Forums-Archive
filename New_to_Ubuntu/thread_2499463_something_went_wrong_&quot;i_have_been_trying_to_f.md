---
title: "something went wrong &quot;i have been trying to find the answer for few days now, anyone?"
date: 2024-07-28
forum: New to Ubuntu
---

### Post by MeanGuy on 2024-07-28
i've install the same ubuntu studio on my desktop and it worked fine, i was trying a lot of fixes, from using the grub menu when you first boot, to actually resizing the boot partition and making it 2gb
since that was the initial problem i faced on my desktop when upgrading .
i can't format the laptop cuz its not mine. but im encouraging my cousin to work with linux and explore.
i copied a part from the log where i think its relevant , 
im trying to dualboot, i turned off the safe boot, protection, created a linux partition from windows and grub, but everytime i get the same error.

my boot partition is /dev/nvme0n1p1
and the root should be in /dev/nvme0n1p7

```

device              Start        End    Sectors   Size Type
/dev/nvme0n1p1       2048    4196351    4194304     2G EFI System
/dev/nvme0n1p2    4196352    4229119      32768    16M Microsoft reserved
/dev/nvme0n1p3    4229120 1056186367 1051957248 501.6G Microsoft basic data
/dev/nvme0n1p4 1957306368 1959100415    1794048   876M Windows recovery environment
/dev/nvme0n1p5 1959104512 1999998975   40894464  19.5G Microsoft basic data
/dev/nvme0n1p6 1999998976 2000408575     409600   200M Windows recovery environment
/dev/nvme0n1p7 1056186368 1957306367  901120000 429.7G Linux filesystem

```

i thought im too old for this lol, but ive been trying to understand whats wrong for the past 5 days. any help would be appreciated.

 ```
22]:        

22]:         Skipped removing 3 old UEFI entries.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         UEFI entry 'Windows Boot Manager' might no longer exist and should be removed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         UEFI entry 'ubuntu' might no longer exist and should be removed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         UEFI entry 'ubuntu' might no longer exist and should be removed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         installing grub to target=/target devices=['/dev/nvme0n1p1'] [replace_defaults=False]
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It's not, using normal behavior
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg', '--print-architecture'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Using grub install command: /usr/lib/grub/grub-multi-install
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Grub install cmds:
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         [['efibootmgr', '-v'], ['dpkg-reconfigure', 'grub-efi-amd64'], ['update-grub'], ['/usr/lib/grub/grub-multi-install'], ['efibootmgr', '-v']]
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/dev', '/target/dev'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/proc', '/target/proc'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/run', '/target/run'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/sys', '/target/sys'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/sys/firmware/efi/efivars', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/target/usr/bin/true', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'efibootmgr', '-v'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'dpkg-reconfigure', 'grub-efi-amd64'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'update-grub'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', '/usr/lib/grub/grub-multi-install'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['udevadm', 'settle'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         TIMED subp(['udevadm', 'settle']): 0.002
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/sys'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/sys'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/run'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/run'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/proc'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/proc'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/dev'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/dev'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         finish: cmd-install/stage-curthooks/builtin/cmd-curthooks/install-grub: FAIL: installing grub to target devices
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         finish: cmd-install/stage-curthooks/builtin/cmd-curthooks/configuring-bootloader: FAIL: configuring target system bootloader
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         finish: cmd-install/stage-curthooks/builtin/cmd-curthooks: FAIL: curtin command curthooks
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Traceback (most recent call last):
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/main.py", line 202, in main
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             ret = args.func(args)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/curthooks.py", line 2234, in curthooks
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             builtin_curthooks(cfg, target, state)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/curthooks.py", line 2189, in builtin_curthooks
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             setup_grub(cfg, target, osfamily=osfamily,
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/curthooks.py", line 852, in setup_grub
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             install_grub(instdevs, target, uefi=uefi_bootable, grubcfg=grubcfg)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/install_grub.py", line 451, in install_grub
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             in_chroot.subp(cmd, env=env, capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/util.py", line 843, in subp
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             return subp(*args, **kwargs)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/util.py", line 323, in subp
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             return _subp(*args, **kwargs)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/util.py", line 172, in _subp
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             raise ProcessExecutionError(stdout=out, stderr=err,
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         curtin.util.ProcessExecutionError: Unexpected error while running command.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Command: ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', '/usr/lib/grub/grub-multi-install']
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Exit code: 1
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Reason: -
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stdout: ''
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stderr: perl: warning: Setting locale failed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Please check that your locale settings:
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANGUAGE = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LC_ALL = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANG = "en_US.UTF-8"
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                     are supported and installed on your system.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Falling back to the standard locale ("C").
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_CTYPE to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_ALL to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing grub to /boot/efi.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing for x86_64-efi platform.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: Cannot set EFI variable Boot0005.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: efivarfs_set_variable: writing to fd 9 failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: error: failed to register the EFI boot entry: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 
Jul 28 18:55:04 ubuntu-studio subiquity_log.[10522]:         Unexpected error while running command.
Jul 28 18:55:04 ubuntu-studio subiquity_log.59355935[10522]:         Command: ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', '/usr/lib/grub/grub-multi-install']
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Exit code: 1
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Reason: -
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stdout: ''
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stderr: perl: warning: Setting locale failed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Please check that your locale settings:
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANGUAGE = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LC_ALL = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANG = "en_US.UTF-8"
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                     are supported and installed on your system.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Falling back to the standard locale ("C").
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_CTYPE to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_ALL to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing grub to /boot/efi.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing for x86_64-efi platform.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: Cannot set EFI variable Boot0005.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: efivarfs_set_variable: writing to fd 9 failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: error: failed to register the EFI boot entry: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         {'current': '0009', 'timeout': '1 seconds', 'order': '0004,0005,0007,0008,0009'}
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         {'current': '0009', 'timeout': '1 seconds', 'order': '0004,0005,0007,0008,0009'}
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]: Stderr: ''
Jul 28 18:55:05 ubuntu-studio subiquity_event.5935[5935]:   curtin command install
 Skipped removing 3 old UEFI entries.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         UEFI entry 'Windows Boot Manager' might no longer exist and should be removed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         UEFI entry 'ubuntu' might no longer exist and should be removed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         UEFI entry 'ubuntu' might no longer exist and should be removed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         installing grub to target=/target devices=['/dev/nvme0n1p1'] [replace_defaults=False]
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It's not, using normal behavior
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'dpkg', '--print-architecture'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Using grub install command: /usr/lib/grub/grub-multi-install
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Grub install cmds:
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         [['efibootmgr', '-v'], ['dpkg-reconfigure', 'grub-efi-amd64'], ['update-grub'], ['/usr/lib/grub/grub-multi-install'], ['efibootmgr', '-v']]
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/dev', '/target/dev'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/proc', '/target/proc'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/run', '/target/run'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/sys', '/target/sys'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/sys/firmware/efi/efivars', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--bind', '/target/usr/bin/true', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'efibootmgr', '-v'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'dpkg-reconfigure', 'grub-efi-amd64'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', 'update-grub'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Checking if target_proc (/target/proc) is a mount
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         It is, so unshare will use --mount-proc=/target/proc
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', '/usr/lib/grub/grub-multi-install'] with allowed return codes [0] (capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['udevadm', 'settle'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         TIMED subp(['udevadm', 'settle']): 0.002
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/usr/bin/ischroot'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/sys/firmware/efi/efivars'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/sys'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/sys'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/run'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/run'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/proc'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/proc'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['mount', '--make-private', '/target/dev'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Running command ['umount', '/target/dev'] with allowed return codes [0] (capture=False)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         finish: cmd-install/stage-curthooks/builtin/cmd-curthooks/install-grub: FAIL: installing grub to target devices
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         finish: cmd-install/stage-curthooks/builtin/cmd-curthooks/configuring-bootloader: FAIL: configuring target system bootloader
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         finish: cmd-install/stage-curthooks/builtin/cmd-curthooks: FAIL: curtin command curthooks
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Traceback (most recent call last):
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/main.py", line 202, in main
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             ret = args.func(args)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/curthooks.py", line 2234, in curthooks
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             builtin_curthooks(cfg, target, state)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/curthooks.py", line 2189, in builtin_curthooks
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             setup_grub(cfg, target, osfamily=osfamily,
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/curthooks.py", line 852, in setup_grub
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             install_grub(instdevs, target, uefi=uefi_bootable, grubcfg=grubcfg)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/commands/install_grub.py", line 451, in install_grub
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             in_chroot.subp(cmd, env=env, capture=True)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/util.py", line 843, in subp
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             return subp(*args, **kwargs)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/util.py", line 323, in subp
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             return _subp(*args, **kwargs)
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:           File "/snap/ubuntu-desktop-bootstrap/237/lib/python3.10/site-packages/curtin/util.py", line 172, in _subp
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:             raise ProcessExecutionError(stdout=out, stderr=err,
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         curtin.util.ProcessExecutionError: Unexpected error while running command.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Command: ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', '/usr/lib/grub/grub-multi-install']
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Exit code: 1
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Reason: -
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stdout: ''
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stderr: perl: warning: Setting locale failed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Please check that your locale settings:
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANGUAGE = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LC_ALL = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANG = "en_US.UTF-8"
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                     are supported and installed on your system.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Falling back to the standard locale ("C").
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_CTYPE to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_ALL to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing grub to /boot/efi.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing for x86_64-efi platform.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: Cannot set EFI variable Boot0005.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: efivarfs_set_variable: writing to fd 9 failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: error: failed to register the EFI boot entry: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 
Jul 28 18:55:04 ubuntu-studio subiquity_log.[10522]:         Unexpected error while running command.
Jul 28 18:55:04 ubuntu-studio subiquity_log.59355935[10522]:         Command: ['unshare', '--fork', '--pid', '--mount-proc=/target/proc', '--', 'chroot', '/target', '/usr/lib/grub/grub-multi-install']
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Exit code: 1
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Reason: -
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stdout: ''
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         Stderr: perl: warning: Setting locale failed.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Please check that your locale settings:
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANGUAGE = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LC_ALL = (unset),
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                         LANG = "en_US.UTF-8"
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                     are supported and installed on your system.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 perl: warning: Falling back to the standard locale ("C").
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_CTYPE to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_MESSAGES to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 locale: Cannot set LC_ALL to default locale: No such file or directory
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing grub to /boot/efi.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 Installing for x86_64-efi platform.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: Cannot set EFI variable Boot0005.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: efivarfs_set_variable: writing to fd 9 failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 grub-install: error: failed to register the EFI boot entry: Invalid argument.
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:                 
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         {'current': '0009', 'timeout': '1 seconds', 'order': '0004,0005,0007,0008,0009'}
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         {'current': '0009', 'timeout': '1 seconds', 'order': '0004,0005,0007,0008,0009'}
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]:         
Jul 28 18:55:04 ubuntu-studio subiquity_log.5935[10522]: Stderr: ''
Jul 28 18:55:05 ubuntu-studio subiquity_event.5935[5935]:   curtin command install
```

---

### Post by yancek on 2024-07-28
EFI partitions (the first partition on the drive you reference) are generally 500MB or less and unless you have a number of different operating systems install, that should be more than enough room.

> created a linux partition from windows and grub 

Clarify that.  Windows doesn't understand and can't create and format a LInux filesystem partition and you can't create a partition with Grub as Grub is just a bootloader.

> but everytime i get the same error. 

Is the error you get 'Something went wrong'?

If you cannot boot the installed Ubuntu, use the DVD or USB that you used to install Ubuntu and boot it up, then open a terminal and mount the first partition on the SSD (/dev/nvme0n1p1)  and check to see if there is an 'ubuntu' directory there with efi boot files.  Next mount partition 7 where you say Ubuntu is installed and navigate to the /etc/fstab file on that partition and check to see if there is an entry for /dev/nvme0n1p1 as the /boot/efi directory.

If you can't do this task, go to the boot repair site and download it using the 2nd option on that site.  Use your DVD/USB with Ubuntu on it and select the Create BootInfo Summary option there and post the link you get here.  This will provide details which should allow someone to suggest a solution.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by MeanGuy on 2024-07-29
> **yancek said:**
> EFI partitions (the first partition on the drive you reference) are generally 500MB or less and unless you have a number of different operating systems install, that should be more than enough room.



Clarify that.  Windows doesn't understand and can't create and format a LInux filesystem partition and you can't create a partition with Grub as Grub is just a bootloader.



Is the error you get 'Something went wrong'?

If you cannot boot the installed Ubuntu, use the DVD or USB that you used to install Ubuntu and boot it up, then open a terminal and mount the first partition on the SSD (/dev/nvme0n1p1)  and check to see if there is an 'ubuntu' directory there with efi boot files.  Next mount partition 7 where you say Ubuntu is installed and navigate to the /etc/fstab file on that partition and check to see if there is an entry for /dev/nvme0n1p1 as the /boot/efi directory.

If you can't do this task, go to the boot repair site and download it using the 2nd option on that site.  Use your DVD/USB with Ubuntu on it and select the Create BootInfo Summary option there and post the link you get here.  This will provide details which should allow someone to suggest a solution.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

thank you for taking the time to read and reply to my question, i didn't sleep for couple of days so i apologize if i wasn't clear. i mean i created an empty partition with windows without assigning the file system. and i created another one in another attempt using gparted 
i can't boot the install ubuntu , the last time i used linux was 20 years ago :D maybe i lost it and probably got confused with the naming and stuff. but i appreciate you guiding me to the right direction to fix it. 
i booted up with the live usb, mounted the boot partition and the linux partition , and i installed the boot-repair , i tried it before in the past few days cuz it was suggested and it wasnt able to fix the issue, i didn't create a report cuz i didn't know who to give it to.

and yes, everytime i do a fresh installation i always end up with "something went wrong" while using the installer, i was thinking about editing the installer to install ubuntu without installing grub but couldn't figure out cuz i didn't know how to add -b option for ubiquity

thank you again for trying to help. and i apologize for having rusty skills "its been over 20 years" :D

```

ubuntu-studio@ubuntu-studio:~$ sudo mount /dev/nvme0n1p1 /mnt
ubuntu-studio@ubuntu-studio:~$ sudo nano /mnt/
EFI/                       FX516PE.BIN                System Volume Information/ 
ubuntu-studio@ubuntu-studio:~$ ls /mnt/EFI/
Boot  Microsoft  ubuntu
ubuntu-studio@ubuntu-studio:~$ ls /mnt/EFI/Boot/
bkpbootx64.efi  bootx64.efi  fbx64.efi  mmx64.efi
ubuntu-studio@ubuntu-studio:~$ ls /mnt/EFI/ubuntu/
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

```

mounted /dev/nvme0n1p7 "which is the linux partition on media and here's whats in the /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during curtin installation
/dev/disk/by-uuid/7d512f20-442c-4289-b0c6-a4b96bd252b2 / ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/dev/disk/by-uuid/CAC3-6A51 /boot/efi vfat defaults 0 1
/swap.img       none    swap    sw      0       0


```

and here's the report from boot-repair
[https://paste.ubuntu.com/p/Vc5jvZzsdF/](https://paste.ubuntu.com/p/Vc5jvZzsdF/)

---

### Post by MeanGuy on 2024-07-29
we never had ai back in the days, but i pasted the log and asked why this is happening ,
maybe this will help also

Based on the log, there are a few potential causes for the boot issue that prompted the need for running Boot Repair:

1. Missing or corrupted GRUB installation:
The log shows that the grub-efi installation on nvme0n1p7 (the partition where Ubuntu is installed) was missing or corrupted. This could be due to various reasons like a failed update, disk errors, or manual changes to the boot configuration.

2. EFI variables issue:
There are multiple warnings about EFI variables not being set or accessible on this system:

```
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
EFI variables are not supported on this system.
```

This indicates an issue with the system's ability to manage EFI boot entries, which is crucial for a proper GRUB setup on UEFI systems.

3. Module loading issue:
The log shows an error when trying to load the efivars kernel module:

```
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-31-lowlatency
```

This module is required for GRUB to interact with the EFI firmware and manage boot entries.

4. Locked NVRAM:
The final recommendation mentions "Locked-NVram detected." This suggests that the system's NVRAM (Non-Volatile RAM), which stores EFI variables and boot settings, is locked or inaccessible, preventing Boot Repair from properly configuring the boot process.

The root cause could be a combination of these issues, potentially stemming from a hardware, firmware, or software compatibility problem with the specific system configuration. It's also possible that a previous update, misconfiguration, or corruption in the boot process led to this state.

Without more context about recent system changes or hardware information, it's difficult to pinpoint the exact cause. However, the log indicates that the primary issues revolve around the EFI boot management and the GRUB installation on the Ubuntu partition.

and the first step it suggested was resetting the nvram to default

For an ASUS TUF Dash F15 laptop, here are the steps to reset the UEFI settings and unlock the NVRAM:

    Power off the laptop completely.

    Press and hold the F9 key on your keyboard, then press the Power button to turn on the laptop. Keep holding the F9 key until the UEFI firmware setup utility opens.

    In the UEFI firmware setup utility, navigate to the "Exit" menu.

    Look for an option called "Load Setup Defaults" or something similar. This option may reset the UEFI settings to their default values.

    Select the "Load Setup Defaults" option and confirm the action when prompted.

    After the settings are reset, look for an option to save the changes and exit the UEFI firmware setup utility. This may be an option like "Save Changes and Reset" or "Save & Exit."

    Select the appropriate option to save the changes and exit the UEFI firmware setup utility.

    The laptop should now reboot with the default UEFI settings, which should unlock the NVRAM.


what are your ideas? should i go and do it? since i don't wanna mess up my cousin's laptop

---

### Post by yancek on 2024-07-29
>  Locked-NVram detected.

That's a serious problem with no specific solution.  There are quite a number of threads here on the forums about this problem and some have a solution for a specific case.  You might try a search on the forums to see if any suggestions apply to this computer.  I don't see anything else in the boot repair output and whether to try the suggestion of setting the nvram to default is something to be decided by your cousin.

Nothing really significant in boot repair other than the locked nvram.  I did notice that  line 348 of boot repair suggests selecting the " (nvme0n1p1/efi/****/grub****.efi" entry while line 125 shows the Ubuntu entry in efibootmgr as "\EFI\UBUNTU\SHIMX64.EFI)0000424".  The shim file is generally used when the install is with Secure Boot on.  I don't know that this would solve the issue as the locked nvram appears to be the problem so search the forums and online for the specific computer you are using.

---

### Post by MeanGuy on 2024-07-29
thanks for the reply, i doubled checked the secure boot in windows, its off, 
at least i got a pointer where the problem is from.
i'll look around , since there isn't any options in asus bios but thanks for the help. i'll keep looking and before i do anything i'll ask him for permission :D

---

### Post by Shibblet on 2024-07-29
One of the issues with dual booting and sharing a hard drive, is that Windows utilizes the /efi/boot partition.  So, if you are going to do it that way, install Windows first, then Ubuntu.  And they both have to use the /efi/boot drive.

If you have a separate drive, you can make an /efi/boot partition on that drive during install, and install Ubuntu without worrying about the Windows Boot Partition.

---

