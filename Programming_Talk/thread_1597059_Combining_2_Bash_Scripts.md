---
title: "Combining 2 Bash Scripts"
date: 2010-10-14
forum: Programming Talk
---

### Post by bmathis on 2010-10-14
I have 2 pretty basic Bash scripts that do the same thing, but with minor differences depending on the specific version of Ubuntu. 

What I would like to do is combine the scripts and have them check which version of Ubuntu is running, then proceed to that specific set of commands before continuing with the rest of the script and exiting.

I was hoping that someone could point me in the right direction or a nice easy to understand tutorial. :-?

Thanks in Advance!

---

### Post by r-senior on 2010-10-15
You'll probably get the information you need from the lsb_release and/or uname commands:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

$ uname -a Linux wharfe 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

```

In both cases, you can use the --help option to see what's available.

Then it's a matter of extracting the information you need, assigning it to a variable and testing it. Awk will probably be your friend here. For example, if you are just interested in which Ubuntu codename is being used:

```

#!/bin/bash

version=$(lsb_release -c | awk '{print $2}')
echo "Version variable is $version"

case $version in
        maverick)
                echo "You are running 10.10 Maverick Meerkat"
                ;;
        lucid)
                echo "You are running 10.04 Lucid Lynx"
                ;;
        *)
                echo "You are running something else"
                ;;
esac

```

There might be neater ways to extract the information you need, but that would be my first idea.

---

### Post by bmathis on 2010-10-15
Thanks r-senior. That bit of code along with some more I found elsewhere worked perfectly. Mucho appreciato.

---

