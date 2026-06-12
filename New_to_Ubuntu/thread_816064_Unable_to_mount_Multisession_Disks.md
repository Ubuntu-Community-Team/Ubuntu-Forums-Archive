---
title: "Unable to mount Multisession Disks"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-02
I am unable to mount any multisession disk in my ubuntu 8.04.

whats the problem that i am having.

Is there any package that i can install to solve this

---

### Post by kpkeerthi on 2008-06-02
Pop in a multi-session disc, wait for a few seconds and post the output of
```
dmesg | tail
```Might give a clue as to what's going on.

---

### Post by rraj.be on 2008-06-02
This is the output

```
raj@raj-workstation:~$ dmesg | tail
[ 8134.039403] UDF-fs: Partition marked readonly; forcing readonly mount
[ 8134.073468] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '', timestamp 2004/07/22 04:39 (114a)
[ 8135.109059] cdrom: This disc doesn't have any tracks I recognize!
[11895.587650] UDF-fs: No VRS found
[11895.604890] ISO 9660 Extensions: Microsoft Joliet Level 3
[11895.663498] ISO 9660 Extensions: RRIP_1991A
[15315.313618] cdrom: This disc doesn't have any tracks I recognize!
[15319.023275] UDF-fs: Partition marked readonly; forcing readonly mount
[15319.059131] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '', timestamp 2004/07/22 04:39 (114a)
[15320.112120] cdrom: This disc doesn't have any tracks I recognize!
raj@raj-workstation:~$ dmesg | tail
[ 8134.039403] UDF-fs: Partition marked readonly; forcing readonly mount
[ 8134.073468] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '', timestamp 2004/07/22 04:39 (114a)
[ 8135.109059] cdrom: This disc doesn't have any tracks I recognize!
[11895.587650] UDF-fs: No VRS found
[11895.604890] ISO 9660 Extensions: Microsoft Joliet Level 3
[11895.663498] ISO 9660 Extensions: RRIP_1991A
[15315.313618] cdrom: This disc doesn't have any tracks I recognize!
[15319.023275] UDF-fs: Partition marked readonly; forcing readonly mount
[15319.059131] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '', timestamp 2004/07/22 04:39 (114a)
[15320.112120] cdrom: This disc doesn't have any tracks I recognize!
raj@raj-workstation:~$ 

```

---

### Post by rraj.be on 2008-06-02
any one there?

---

### Post by kpkeerthi on 2008-06-02
Thats strange. Did you create this disc with Windows? What happens when you mount it manually?

---

### Post by rraj.be on 2008-06-02
YUP.

I burnt that disk in windows.

but i havnt tried it to mount manually bcos i dont know how. to do that.

whats the command to manually mount

---

