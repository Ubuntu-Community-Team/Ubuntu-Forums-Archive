---
title: "Need some simple scripting help -- samba relevant"
date: 2008-06-23
forum: Programming Talk
---

### Post by _UsUrPeR_ on 2008-06-23
Allow me to describe what I am attempting, and tell me the best way to go about doing it. For reference, I am a scripting newb, and the closest to scripting I have done so far consists of cron jobs and the like.

I am trying to create a script which will allow users to burn a cd from a directory which is automatically mounted off a samba drive.

Here's the simple code I have which is the general way I want it to work with a few caveats:

```
mount /home/remote/twindata
mkisofs -o cd.iso -R joliet-long /home/remote/twindata
cdrecord dev=/dev/sg0 -vvv --data -force -eject ./cd.iso
umount /home/remote/twindata
```

This works fine, but I wanted to get a little more fool-proof with it. for instance, what if a user quad-clicks the executing file by accident? If that happens, it will execute twice and freak out.

I am trying to figure out how I can use the return from
```
mount |grep -c twindata
```
in code to decide wether to mount.

This is kind of what I had figured so far... except for I'm sure I'm mangling the scripting language:
```
#!/bin/bash
a = |grep -c twindata

if [a == 0]
    mount /home/remote/twindata

mkisofs -o cd.iso -R joliet-long /home/remote/twindata
cdrecord dev=/dev/sg0 -vvv --data -force -eject ./cd.iso

```

Thanks in advance for any help!

Joel

---

### Post by apjone on 2008-06-23
at the beginning of the scrip 

```

if [ -e /tmp/twindata.run ];then
echo -e "Twindata CD gen is already running. If it is not then please run \n\n rm /tmp/twindata.run"
else
touch /tmp/twindata.run
fi

```

then at the end

```

rm /tmp/twindata.run

```

---

### Post by _UsUrPeR_ on 2008-06-23
Hey, thanks apjone!

I'll give that a shot tomorrow and report what's come of it.

---

### Post by _UsUrPeR_ on 2008-06-24
That worked great! I appreciate it.

---

