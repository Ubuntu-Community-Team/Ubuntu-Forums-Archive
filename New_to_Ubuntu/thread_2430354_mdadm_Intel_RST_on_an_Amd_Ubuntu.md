---
title: "mdadm Intel RST on an Amd Ubuntu"
date: 2019-10-31
forum: New to Ubuntu
---

### Post by x5000scs on 2019-10-31
So I have attempted to pull data from a two former intel RST raid 0 drives. I tried using mdadm to attempt to mount them on my machine that is running ubuntu and an amd processor. Ubuntu is able to detect and identify the drives in question as can been seen on the disks panel as seen below.

[https://drive.google.com/drive/folders/162QSNDQRtcZvHMsBo5nbKhiRGcwcvrgq?usp=sharing](https://drive.google.com/drive/folders/162QSNDQRtcZvHMsBo5nbKhiRGcwcvrgq?usp=sharing)

On that basis I attempted to use mdadm to the best of my knowledge to attempt to mount the raid array.

sudo mdadm --assemble /dev/md0 /dev/sdf1 /dev/sde --force

mdadm: only give one device per ARRAY line: /dev/md/Main and SystemFS
mdadm: no recogniseable superblock on /dev/sdf1
mdadm: /dev/sdf1 has no superblock - assembly aborted

But the above happened and thus far I am not certain as to how I can work around this superblock problem. I am quite certain the raid array is fully functional, but there doesn't seem to be documentation on this subject that is useful in this context. What addtional commands would I need to issue to make this work so I can copy these drives data to something more stable?

---

