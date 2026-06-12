---
title: "Problems with Shell Script from Lifehacker"
date: 2010-12-18
forum: Programming Talk
---

### Post by skytreader on 2010-12-18
I copy-pasted this script from [Lifehacker]("http://lifehacker.com/5711201/quickly-uninstall-old-linux-kernels-with-a-bash-script") to remove old kernels:

```
#/bin/bash
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r` > /tmp/kernelList
for I in `cat /tmp/kernelList`
do
aptitude remove $I
done
rm -f /tmp/kernelList
update-grub
```

I get the error:

```
'leanKernels.sh: line 4: syntax error near unexpected token `do
'leanKernels.sh: line 4: `do
```

I try move the do in line with the for and get

```
cleanKernels.sh: line 4: syntax error near unexpected token `aptitude'
'leanKernels.sh: line 4: `aptitude remove $I

```

No one in the Lifehacker comment thread seem to have this problem. Is there anything I'm missing? I run it with "sudo bash cleanKernels.sh" (no quotes, of course). I've even chmod-ed it (chmod 755).

Thanks for any help.

---

### Post by wojox on 2010-12-18
Change the first line to

```
#!/bin/bash
```

---

### Post by skytreader on 2010-12-18
> **wojox said:**
> Change the first line to

```
#!/bin/bash
```

Err...still no effect. Same problem with both do in line 4 and in line 3.

---

### Post by mobilediesel on 2010-12-18
> **skytreader said:**
> I copy-pasted this script from [Lifehacker]("http://lifehacker.com/5711201/quickly-uninstall-old-linux-kernels-with-a-bash-script") to remove old kernels:

```
#/bin/bash
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r` > /tmp/kernelList
for I in `cat /tmp/kernelList`
do
aptitude remove $I
done
rm -f /tmp/kernelList
update-grub
```

I get the error:

```
'leanKernels.sh: line 4: syntax error near unexpected token `do
'leanKernels.sh: line 4: `do
```

I try move the do in line with the for and get

```
cleanKernels.sh: line 4: syntax error near unexpected token `aptitude'
'leanKernels.sh: line 4: `aptitude remove $I

```

No one in the Lifehacker comment thread seem to have this problem. Is there anything I'm missing? I run it with "sudo bash cleanKernels.sh" (no quotes, of course). I've even chmod-ed it (chmod 755).

Thanks for any help.

It's a bit messy as posted on Lifehacker. Try this:
```
#!/bin/bash
ls /boot/vmlinuz* | sed -e "s@vmlinuz-@linux-image-@g" -e "/$(uname -r)/d" | \
while read I
do
aptitude remove $I
done
update-grub
```

---

### Post by wojox on 2010-12-19
I always used this script while using Debian or Ubuntu

[Ubucleaner 1.0]("http://opendesktop.org/content/show.php/Ubucleaner?content=71529")

---

### Post by skytreader on 2011-01-20
It's been quite a while since I last checked this thread but I didn't notice wojox's most recent reply last time. And just to say that wojox's link does everything (and a little more) of what I want.

Thank you!

---

