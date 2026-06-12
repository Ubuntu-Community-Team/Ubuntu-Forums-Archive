---
title: "boot efi error"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by boregard on 2012-07-24
hello, while poking around in disk utility trying to solve another problem i am having with misaligned partitions i found this error, mount point: mounted at /boot/efi. it was underligned and in red so clicked on it to see what it was and found this. not sure if this is related to other problem i have so i am posting it here. i did some googling and found something simular but it wasnt about grubx64.efi.  ```
Archive:  /boot/efi/EFI/ubuntu/grubx64.efi
[/boot/efi/EFI/ubuntu/grubx64.efi]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /boot/efi/EFI/ubuntu/grubx64.efi may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /boot/efi/EFI/ubuntu/grubx64.efi or
          /boot/efi/EFI/ubuntu/grubx64.efi.zip, and cannot find /boot/efi/EFI/ubuntu/grubx64.efi.ZIP, period.
```

---

### Post by oldfred on 2012-07-24
It looks like you tried to open it as a zip file, but it really is an executable to load grub in efi systems. I do not think that is an issue.

If you have that on your system not the liveCD then you are in UEFI boot mode?

---

