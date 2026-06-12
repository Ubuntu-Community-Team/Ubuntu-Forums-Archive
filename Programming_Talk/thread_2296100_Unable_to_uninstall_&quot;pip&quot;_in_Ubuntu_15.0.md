---
title: "Unable to uninstall &quot;pip&quot; in Ubuntu 15.04"
date: 2015-09-23
forum: Programming Talk
---

### Post by arjun13 on 2015-09-23
Hello,

I am using Ubuntu 15.04 [3.19.0-28-generic #30-Ubuntu] and have 2 flavours of Python viz., 2.7.9 and 3.4.3. I had installed "pip" using "apt-get install pip" and it got installed. Now I want to remove it and I am using the commands:

"apt-get remove pip" OR "apt-get purge pip". Both of these commands are giving me the output:
E: Unable to locate package pip

But when I use "whereis pip", I get the output:
pip: /usr/bin/pip /usr/share/man/man1/pip.1.gz

And, when I use "find / -iname "pip"", I get the output:
/usr/bin/pip
/usr/lib/python2.7/dist-packages/pip

Why is apt-get unable to remove it. And does this now mean that I will have to remove it using "rm" command manually for each of the files listed above?

Thanks!

---

### Post by arjun13 on 2015-09-23
I got the solution to this by using the following command:
"sudo apt-get purge --auto-remove python-pip"

---

