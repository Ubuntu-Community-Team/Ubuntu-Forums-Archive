---
title: "My first shell script, need a little help"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by someitalian123 on 2012-01-20
I'm trying to make a shell script to blacklist these four modules. I got it working like this


echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00lib"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00pci"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist rt2800lib"  >>  /etc/modprobe.d/blacklist.conf

but how can I make it so if the module is already blacklisted it won't add the line to my /etc/modprobe.d/blacklist.conf file?

---

### Post by CoffeeRain on 2012-01-20
I know it's possible and easy in Python, but as this is your first bash script, you may want to stick to bash for now. Is there anything like re in bash?

---

### Post by WthIteh on 2012-01-20
> **someitalian123 said:**
> but how can I make it so if the module is already blacklisted it won't add the line to my /etc/modprobe.d/blacklist.conf file?
You could **grep** the file and check its result with an **if** rule.
Something like this:
```
if grep 'something to search for' /etc/modprobe.d/blacklist.conf > /dev/null; then echo already exist; else echo add it now; fi
```

---

### Post by someitalian123 on 2012-01-20
> **WthIteh said:**
> You could **grep** the file and check its result with an **if** rule.
Something like this:
```
if grep 'something to search for' /etc/modprobe.d/blacklist.conf > /dev/null; then echo already exist; else echo add it now; fi
```

That did the job, Thank you.

---

### Post by CharlesA on 2012-01-20
> **WthIteh said:**
> You could **grep** the file and check its result with an **if** rule.
Something like this:
```
if grep 'something to search for' /etc/modprobe.d/blacklist.conf > /dev/null; then echo already exist; else echo add it now; fi
```

You could write it like this as well:

```
if [[ -z $(grep rt2800pci /etc/modprobe.d/blacklist.conf) ]]; then
echo "rt2800pci" >> /etc/modprobe.d/blackflist.conf; else
echo "rt2800pci is already blacklisted"
fi
```

Add an if statement for each module you want to blacklist and go from there.

See here as well: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---

