---
title: "[SOLVED] Bash: How to determine if package installed"
date: 2008-10-20
forum: Programming Talk
---

### Post by lavinog on 2008-10-20
I am writing a shell script that I will use on multiple computers. It uses some programs that are not installed by default (notify-send, prism..etc)
I have a function that has a list of the binaries needed and checks their existance in /usr/bin. For the ones that don't exist I have a case statement that I manually set to output the required package for each missing binary.
I would like to change this behavior to only check that the required packages are installed and report the ones that are still needed

Is there a preferred way of doing this or a way to get a list of packages installed on a system without super user privileges?

---

### Post by geirha on 2008-10-20
You could use: ```
aptitude search '~i ^packagename$'
# For example
aptitude search '~i ^zenity$'

```

It will print a line if the package is installed, and nothing otherwise.

---

### Post by unutbu on 2008-10-20
You could also generate a list of all the installed packages this way:
```

dpkg --get-selections | awk '/\Winstall/{print $1}'

``` or
```

COLUMNS=250 dpkg --list | awk '/^ii/{print $2}'
```

Then you could grep against this list.

---

### Post by lavinog on 2008-10-20
Thank you both for you timely response
both ideas will work for me.

---

### Post by JupiterV2 on 2008-10-20
pkg-config could be another program that may help you.

However, this and the above solutions assume the user has the above programs. You should make sure you have a fall-back method if one or all of them are missing.

Also, be aware that programs can be installed to /usr, /usr/local or even /opt. Each distribution uses a different method and not every system or distribution adheres to the FHS (Filesystem Hierarchy Standard).

There is, likely, no fool-proof way to check if a package is installed or not.

---

### Post by ghostdog74 on 2008-10-20
it depends on what platform or distro your multiple computers are. I reckon they are all the same. If they are all the same and you can use commands such as dpkg or aptitude, by all means. however if they are different, a simple find to find those commands should suffice.

---

### Post by gramound on 2011-09-29
On Ubuntu, I prefer dpkg-query, because I can use the exit status in a script:
```
if dpkg-query -W packagename; then ...; fi
```

---

### Post by ofnuts on 2011-10-01
> **gramound said:**
> On Ubuntu, I prefer dpkg-query, because I can use the exit status in a script:
```
if dpkg-query -W packagename; then ...; fi
```A completely different soluton is to provide a .deb to install the scripts,  and let the package manager install the prereqs if needed.

---

### Post by ubudog on 2011-11-29
Back to sleep thread.

---

