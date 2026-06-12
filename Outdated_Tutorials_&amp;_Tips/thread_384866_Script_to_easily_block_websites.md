---
title: "Script to easily block websites"
date: 2007-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by kevinlyfellow on 2007-03-15
I was working for the University of Maine not so long ago.  One of my jobs was to write an after school curriculum for science (for middle school students).  It was supposed to utilize technologies that these students may not have been exposed to (it was for a high poverty area).  So, I spent quite a bit of time looking at different resources on the internet, and I came across inappropriate advertisements frequently.  Recently studies have shown that most young people come across porn on the internet accidentally.  I figured that it just plain sucks that young people need to be exposed to certain material accidentally, but I also do not agree with out-right filtering.  Another thing I don't necessarily agree with is completely filtering out all ads altogether.  Web sites make revenue by advertising and I feel its important that if you like a site, you should give them a chance at making money through ads.  

So this has led me to make a script so that one can easily enter in an address to be blocked and it will be blocked system wide ever after.  Let me know what you think :-)

```

#!/bin/bash

## this program is a shell script to easily block designated sites using the hosts file.
## it assumes that you want your blocked sites to be at the bottom of the hosts file.

######################
# configurable definitions
hostsfile=/etc/hosts
redirect="127.0.0.1"
######################

## Some definitions that shouldn't be changed
user=`whoami`

if [ $user = "root" ]
then
another="Yes"
	while [ $another = "Yes" ]
	do
		site2bblocked=`zenity --entry \
			--title="Block Site" \
			--text="Enter site to be blocked.
DO NOT ENTER http:// !!!"`
		if [ $site2bblocked ]
		then
			another=`zenity --list \
				--title="Another site?" \
				--column="Would you like to enter another site?" "Yes" "No"`
		else
			another="No"
		fi

	echo "$redirect $site2bblocked" >> $hostsfile
	done
else
	zenity --info --text="You need to be root to run this"
fi

return 0

```

---

### Post by kalikiana on 2007-03-17
Personally I find it better to add lines to the hosts file manually. If I were to script every single task like this I'd easily end up with thousands of them. If you need it os often it may be a different thing.

---

### Post by kevinlyfellow on 2007-03-17
My thinking is that someone (a parent perhaps) is browsing the web and comes across an ad or website that is an in place where it is potentially viewed by young adults (or if you just don't dig raunch or for whatever billion reasons you may have to block some ads over others).  They can just add in the unwanted address into it and their done.  It is easy to block sites from the hosts file manually, but I figure this may prove valuable.

Plus I like playing with zenity :-)

---

### Post by mscir on 2008-03-12
[QUOTE=kevinlyfellow;2310532<snip>

Plus I like playing with zenity :-)[/QUOTE]

Would you mind showing us how you use zenity to edit the hosts file? I'm a first time Ubuntu user and I'd like to be able to manually edit the hosts file as I've been doing with windows. 

Thanks,
Mike

---

### Post by Princey on 2008-03-27
This doesn't use zenity, however, you can manually edit your hosts files this way.

Just open your terminal/konsole and type in > sudo gedit /etc/hosts and the rest is just as if you're on Windows. For the Kubuntu fans, substitute gedit with kedit or kate whichever you have installed.

---

### Post by LinuxLovingFalla on 2008-03-28
might be useful someday. thanx lol

---

### Post by sircalaj on 2010-02-14
I'm new to ubuntu's environment I had try editing the Hosts file to block websites but i cannot edit or save it because it is read only file. How to manually edit the HOSTS file? Any help is very much appreciated thanks in advance.

---

### Post by amsterdamharu on 2010-02-14
Control + F2 and type:
```
gksu gedit /etc/fstab
```

---

### Post by Princey on 2010-02-14
> **amsterdamharu said:**
> Control + F2 and type:
```
gksu gedit /etc/fstab
```

This is to edit your fstab file responsible for your discs mounted at boot. The command to manually edit your hosts file is:```
sudo gedit /etc/hosts
```
You can substitute kate for gedit if you're using KDE. That should bring up your hosts file for manual edit. Just be sure to follow the format > 127.0.0.1 IP address goes here

N.B. There's a space between 127.0.0.1 and the IP address

---

