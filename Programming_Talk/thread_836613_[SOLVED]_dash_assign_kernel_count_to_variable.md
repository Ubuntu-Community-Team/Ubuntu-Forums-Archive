---
title: "[SOLVED] dash: assign kernel count to variable"
date: 2008-06-21
forum: Programming Talk
---

### Post by x1a4 on 2008-06-21
Hi,

I'm making slight modifications to /sbin/update-grub.  I need the script to set different titles depending on the number of kernels installed.  Specifically, I don't want the grub menu to show the kernel version if there's only one kernel.  What's the best way to count kernels in /boot/ and assign the number to a variable?

Also, what's the dash syntax for the following: 
```

if ($kernel_count == 1) {
  echo -n "title      $title" >> $buffer
}
else if ($kernel_count > 1) {
  echo -n "title      $title, kernel $kernel_version" >> $buffer
}

```

Thank you.

---

### Post by x1a4 on 2008-10-29
Bump.

---

### Post by geirha on 2008-10-30
Several ways to count the kernels. A for loop
```
kernel_count=0
for kernel in /boot/vmlinuz-*; do
  kernel_count=`expr $kernel_count + 1`
done

```
Use a function:
```
num_kernels ()
{
  echo $#
}
kernel_count=`num_kernels /boot/vmlinuz-*`

```
Use set to reset the shells arguments to each kernel:
```
set -- /boot/vmlinuz-*
kernel_count=$#

```

conditional statements looks like this:
```

if [ "$kernel_count" = "1" ]; then
  echo one kernel
elif [ "$kernel_count" -gt "1" ]; then
  echo more than one kernel
else
  echo hm...
fi

```

---

