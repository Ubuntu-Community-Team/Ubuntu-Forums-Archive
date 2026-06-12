---
title: "[SOLVED] I got a probelm here"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by H!tMaN on 2008-06-06
Please I want to find out if that code correct or not:


 > printf("Enter device name:");
 system("read devname");        
 system("echo $devname");
 system("sudo mount -v $devname");

I think it seem to be correct but lets see the output:

> /dev/sda1

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/galileo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=galileo)
/dev/sdb on /media/JOYBEE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
Enter device name:

Can someone tell me why this block of doesn't work correctly?

---

### Post by Trail on 2008-06-06
Is this C/C++ ?

My guess is that the system() function does not expand $devname to the actual name of the device, but it remains as a literal "$devname". What does the 'echo' line print? You may want to substitute this with the value read. You could use regular C/C++ to read/write, create a string with the expanded device name and use this as a call to mount.

---

### Post by H!tMaN on 2008-06-06
Yes it's C

echo just leave a blank newline and please I need more explanation.

How to substitute them with basic C read write?
What that code mean?
Why the printed line appear after all although printf() is the first line of code??

```
banner -w 50 Trail
```

---

### Post by Trail on 2008-06-06
The "code" is my signature, and I should change it soon... Don't mind it.

Give this a look:

```

#include <stdio.h>
 
int main(void) {

  // Declare two string variables of length 50
  char devname[50];
  char command[50];

  // Print the message
  printf("Enter device name:\n");

  // Read the device name and store it into the variable 'devname'
  scanf("%s", devname);

  // Generate a string that contains the command we want to execute
  // '%s' is replace by the value of 'the variable devname'
  // The result is stored in the variable 'command'
  sprintf(command, "echo sudo mount -v %s", devname);

  // Execute the command
  system(command);
  return 0;
}

```

---

### Post by hyper_ch on 2008-06-06
entering a descriptive thread title helps to get support compared to a generic one like "noob here" or "help needed". The simple fact that you are on a support forum indicates already that with a chance of nearly 100% you open a thread to get some help.

---

### Post by H!tMaN on 2008-06-06
> **hyper_ch said:**
> entering a descriptive thread title helps to get support compared to a generic one like "noob here" or "help needed". The simple fact that you are on a support forum indicates already that with a chance of nearly 100% you open a thread to get some help.

I'm sorry but I really needed help and didn't think about the title.
Thanks ans sorry.

---

### Post by H!tMaN on 2008-06-06
> **Trail said:**
> The "code" is my signature, and I should change it soon... Don't mind it.

Give this a look:

```

#include <stdio.h>
 
int main(void) {

  // Declare two string variables of length 50
  char devname[50];
  char command[50];

  // Print the message
  printf("Enter device name:\n");

  // Read the device name and store it into the variable 'devname'
  scanf("%s", devname);

  // Generate a string that contains the command we want to execute
  // '%s' is replace by the value of 'the variable devname'
  // The result is stored in the variable 'command'
  sprintf(command, "echo sudo mount -v %s", devname);

  // Execute the command
  system(command);
  return 0;
}

```

I'll try this.

---

### Post by hyper_ch on 2008-06-06
> **H!tMaN said:**
> I'm sorry but I really needed help and didn't think about the title.
Thanks ans sorry.

The title is the first thing anybody else notices... if there's just a "need help" you might be wasting the time of others that are willing to help.

---

### Post by sayakb on 2008-06-06
I think the mods should put up a sticky on posting rules in ABT.

PS: hyper_ch has a scary pic.

---

### Post by H!tMaN on 2008-06-06
The echo message appear but the command doesn't execute. :(

---

### Post by Trail on 2008-06-06
Ah yeah, sorry :P

Change
```

ssprintf(command, "echo sudo mount -v %s", devname);

```

To:
```

sprintf(command, "sudo mount -v %s", devname);

```

I inserted "echo" on my machine to test, but I forgot to remove this before I posted it.

---

### Post by H!tMaN on 2008-06-06
Thanks it worked without echo :D
Thanks everyone

---

