---
title: "Can't mount ddf_raid partition"
date: 2017-10-30
forum: New to Ubuntu
---

### Post by rantree on 2017-10-30
I have just upgraded my ubuntu version I am having trouble to mount a ddf raid partition sdb, sdc and sdd

@iH8QG6:~$ sudo blkid -c /dev/null -o list
device                                                          fs_type          label            mount point                                                          UUID
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                                                   ext4                                 /                                                                                900e551c-72ff-4d52-acf4-10e03a71923e
/dev/sda5                                                                   swap                                 [SWAP]                                                                           558651ce-0555-4f47-9f54-590cab76965a
/dev/sdb                                                                    ddf_raid_member                      (in use)                                                                        |ggT&#65533;C|ggTkgT&#65533;ngT&#65533;&#65533;&#65533;&#65533;
/dev/sdc                                                                    ddf_raid_member                      (in use)                                                                        |ggT&#65533;C|ggTkgT&#65533;ngT&#65533;&#65533;&#65533;&#65533;
/dev/sdd                                                                    ddf_raid_member                      (in use)                                                                        |ggT&#65533;C|ggTkgT&#65533;ngT&#65533;&#65533;&#65533;&#65533;
/dev/sde1                                                                   ext4              Processed_data     /Processed_data                                                                  15948201-6d19-4159-b8d7-49f07bc26e71

---

