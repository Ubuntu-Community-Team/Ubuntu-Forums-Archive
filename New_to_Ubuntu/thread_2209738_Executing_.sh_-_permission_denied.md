---
title: "Executing .sh - permission denied"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by scoobyd on 2014-03-07
Hi,

I've been trying to execute run.sh but keep getting "permission denied" even after I've made it executable by entering "chmod +x run.sh"

This is what I entered and what Terminal churned out:
[I]
username@Tosh-Ubuntu:~$ cd Desktop/linux
username@Tosh-Ubuntu:~/Desktop/linux$ chmod +x run.sh
username@Tosh-Ubuntu:~/Desktop/linux$ ./run.sh
./run.sh: line 2: ./adb: Permission denied

./run.sh: line 7: ./adb: Permission denied[/I]

Help??

TIA.

---

### Post by Lars Noodén on 2014-03-07
What filesystem are you using there?

```
mount | grep /dev
```

---

### Post by raja.genupula on 2014-03-07
I think its Android Debugging script. For that If i remembered properly from #XDA , he must run it as a root user with sudo

---

### Post by Lars Noodén on 2014-03-07
> **raja.genupula said:**
> I think its Android Debugging script. For that If i remembered properly from #XDA , he must run it as a root user with sudo

Yes, now I see the error messages.  

What are the first few lines of the script?

```

head -n 8 run.sh

```

You probably want to take a look through the whole thing really before running it as root, just to be sure.

---

### Post by Impavidus on 2014-03-07
run.sh is running, but it calls adb.sh, which doesn't run. You may have to give execute permission to adb.sh

---

### Post by raja.genupula on 2014-03-07
Yes , its better to have a look before running something

---

### Post by nunecas123 on 2014-03-07
Why don't you use sudo?
```
sudo *./run.sh
```*

---

### Post by scoobyd on 2014-03-07
> **Lars Noodén said:**
> What filesystem are you using there?

```
mount | grep /dev
```


username@Tosh-Ubuntu:~$ mount | grep /dev
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sda7 on /boot type ext4 (rw)
/dev/sda9 on /home type ext4 (rw)
/dev/sda2 on /boot/efi type vfat (rw)
/dev/sda5 on /media/username/Loopie type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/username/61D3-9E5B type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

---

### Post by scoobyd on 2014-03-07
> **Lars Noodén said:**
> Yes, now I see the error messages.  

What are the first few lines of the script?

```

head -n 8 run.sh

```

You probably want to take a look through the whole thing really before running it as root, just to be sure.

username@Tosh-Ubuntu:~/Desktop/linux$ head -n 8 run.sh
BASE=$(dirname $0)
pkg=$($BASE/adb shell pm path com.koushikdutta.backup)
# apparently pm path appends a carriage return which screws
# up the class name in dalvikvm invocation
pkg=$(echo $pkg | cut -d : -f 2 | sed s/\\r//g)
echo $pkg
$BASE/adb shell << EOF
CLASSPATH=$pkg app_process /system/bin com.koushikdutta.shellproxy.ShellRunner2 $@ &

---

### Post by scoobyd on 2014-03-07
> **Impavidus said:**
> run.sh is running, but it calls adb.sh, which doesn't run. You may have to give execute permission to adb.sh

I gave adb excute permission but now end up with this:


*username@Tosh-Ubuntu:~/Desktop/linux$ ./run.sh*
*./run.sh: line 2: ./adb: No such file or directory*

*./run.sh: line 7: ./adb: No such file or directory*

---

### Post by Impavidus on 2014-03-08
Peculiar... What's in there exactly?```
ls -l run.sh adb.sh
```

---

### Post by scoobyd on 2014-03-08
> **Impavidus said:**
> Peculiar... What's in there exactly?```
ls -l run.sh adb.sh
```


username@Tosh-Ubuntu:~$ ls -l run.sh adb.sh
ls: cannot access run.sh: No such file or directory
ls: cannot access adb.sh: No such file or directory
username@Tosh-Ubuntu:~$ cd Desktop/linux
username@Tosh-Ubuntu:~/Desktop/linux$ ls -l run.sh adb.sh
ls: cannot access adb.sh: No such file or directory
-rwxrwxrwx 1 username username 351 Jan 31  2013 run.sh



I wanted to run Helium: [http://www.clockworkmod.com/carbon](http://www.clockworkmod.com/carbon)

---

