---
title: "LIst all installed packages in size order"
date: 2007-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by app on 2007-11-01
The ugliest script in the world:

aptitude show '~n.*' | awk -f fix | grep 'State: installed' | sed 's/: /:/g' | sort -t: -n -k4 | more

Where "fix" is 

/^Package:/             {p = $0}
/^State:/               {s = $0}
/^Uncompressed Size:/   {print p " " s " " $0}

---

### Post by KIAaze on 2008-09-24
I was trying to find another one I used some time ago with dpkg and found this post instead.

Found it:
```
dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n
```

Others I found on the way:
```
dpkg-query --show --showformat='${Package;-50}\t${Installed-Size}\n' | sort -k 2 -n

```
```
dpkg-query --show --showformat='${Package;-50}\t${Installed-Size} ${Status}\n' | sort -k 2 -n |grep -v deinstall

```
source: [http://ubuntuforums.org/showthread.php?t=602270](http://ubuntuforums.org/showthread.php?t=602270)

In case somebody is looking for this too. ;)

And for those wanting a GUI: Just sort by installed size in Synaptic. ^^

edit:
Made a script allowing you to test all of those methods (also shows how to embed the awk script into the shellscript. ;) ).

**_list_installed_packages_by_size.sh_**:
```
#!/bin/bash
if [ $# -ne 1 ]
then
        echo "usage : $0 <0/1/2/3>"
        exit 0 
fi

if [ $1 -eq 0 ]
then
	aptitude show '~n.*' | awk '\
	/^Package:/ {p = $0};\
	/^State:/ {s = $0};\
	/^Uncompressed Size:/ {print p " " s " " $0};\
	' | grep 'State: installed' | sed 's/: /:/g' | sort -t: -n -k4 | more
fi

if [ $1 -eq 1 ]
then
	dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n
fi

if [ $1 -eq 2 ]
then
	dpkg-query --show --showformat='${Package;-50}\t${Installed-Size}\n' | sort -k 2 -n
fi

if [ $1 -eq 3 ]
then
	dpkg-query --show --showformat='${Package;-50}\t${Installed-Size} ${Status}\n' | sort -k 2 -n |grep -v deinstall
fi
```

---

### Post by KIAaze on 2010-04-09
Even better: wajig or dpigs! :)
cf: [http://www.commandlinefu.com/commands/view/3842/list-your-largest-installed-packages-on-debianubuntu](http://www.commandlinefu.com/commands/view/3842/list-your-largest-installed-packages-on-debianubuntu)

```
sudo apt-get install wajig
wajig large

```
```
sudo apt-get install debian-goodies
dpigs
```

---

