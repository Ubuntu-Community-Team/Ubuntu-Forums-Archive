---
title: "How to check version of Ubuntu?"
date: 2011-07-24
forum: Programming Talk
---

### Post by leon.vitanos on 2011-07-24
In my program I do a specific thing with a specific command.
the thing is that Ubuntu 11.04 and former use another command than 11.10.
So, I assume that I have to make a check of the current ubuntu version running on the system and have the corresponding command to run.
What is the right way to do it through C++ (system calls are better to be avoided)?

Thanks in advance for any answers :)

---

### Post by slavik on 2011-07-24
cat /etc/lsb-release

---

### Post by hakermania on 2011-07-25
```
lsb_release -r
```

---

### Post by nvteighen on 2011-07-25
Are you sure there isn't a library you can use to get that functionality, so that you can avoid depending on how a command is named in each Ubuntu release?

---

### Post by Habitual on 2011-07-25
```
cat /etc/issue
```

Here's a function I found. It will require some additional entries. I am a basic shell scripter and my bash.fu is acquired from examples around the net.
But this can always serve as a "bad example". :)
YMMV.

```

os_check()
{
if [ "$(uname -s)" == 'FreeBSD' ]; then
  os='freebsd'
fi

os="";
grep -iq "centos" /etc/issue 
if [ $? = '0' ];then
os='centos'
fi

grep -iq  "debian" /etc/issue -i -q
if [ $? = '0' ];then
os='debian'
fi

grep -iq "suse" /etc/issue 
if [ $? = '0' ];then
os='SUSE'
fi
echo "OS is $os"
}


```

---

### Post by dwhitney67 on 2011-07-25
> **Bong.Da.City said:**
> In my program I do a specific thing with a specific command.
the thing is that Ubuntu 11.04 and former use another command than 11.10.

Could you enlighten us as to which command you are referring to?

---

