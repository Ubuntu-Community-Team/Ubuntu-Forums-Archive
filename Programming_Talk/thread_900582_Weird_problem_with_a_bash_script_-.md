---
title: "Weird problem with a bash script -"
date: 2008-08-25
forum: Programming Talk
---

### Post by CRCarl on 2008-08-25
All - 
    I am having an odd issue with a bash script. I am building a string variable  that I want to eventually execute. If I echo the string then copy and paste it in term it runs fine, however when I exec the string it fails. Details below - 

The relevent part of the script - 

```

IFS=$'\n'
for line in $(cat "$file")
do
	usertime=$(echo "$line" | awk '{print $20}' | grep [0-9]$)
	systime=$(echo "$line" | awk '{print $21}' | grep [0-9]$)
	updateline=$(echo rrdtool update "$pathtorrd" "$EPOCHdate":"$usertime":"$systime" | grep [0-9]$)			
	echo $updateline    #for troubleshooting
	exec `$updateline`
	EPOCHdate=$(($EPOCHdate+300))
done

```

You will notice that I am echo'ing the string, then executing it. The output is - 
```

rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219662300:0:2
./dorado2.sh: line 30: rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219662300:0:2: No such file or directory

```

However if I copy and paste the results of the echo (first line above) it works just fine. Everything is running as me, all the paths are fully qualified, I dos2unix'ed the file, nothing helped. 

Ideas?

Thanks.

---

### Post by HalPomeranz on 2008-08-25
It looks to me like there are two problems with your code:

1) Your syntax using backticks means "execute the command in $updateline and substitute the output of that command as the arguments to exec".  This is clearly not what you want.

2) Calling exec causes your original shell script to be terminated and replaced with the program you're running via exec.  So your loop is actually going to terminate the instant the first exec call happens and only the first line of your input file is going to be processed.

Instead I think you want:

```

(exec $updateline)

```

The extra parens cause the exec to happen in a sub-shell so that your loop doesn't get terminated by the first exec call.

---

### Post by CRCarl on 2008-08-25
HAL - 
   Thanks for your help, but still no love. 

With the ``(backticks) the loop wasn't exiting, just that path error. With your suggestion substituted for my exec line the error has changed - It looks like it is prepending the string with the current path. I'm very confused. 

Note: I removed the echo lines - 
```
./folder2.sh: line 27: exec: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219651200:0:4: cannot execute: No such file or directory
./folder2.sh: line 27: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219651500:0:1: No such file or directory
./folder2.sh: line 27: exec: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219651500:0:1: cannot execute: No such file or directory
./folder2.sh: line 27: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219651800:0:1: No such file or directory
./folder2.sh: line 27: exec: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219651800:0:1: cannot execute: No such file or directory
./folder2.sh: line 27: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219652100:0:1: No such file or directory
./folder2.sh: line 27: exec: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219652100:0:1: cannot execute: No such file or directory
./folder2.sh: line 27: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219652400:1:3: No such file or directory
./folder2.sh: line 27: exec: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219652400:1:3: cannot execute: No such file or directory
./folder2.sh: line 27: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219652700:0:3: No such file or directory
./folder2.sh: line 27: exec: /home/user/Desktop/folder/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219652700:0:3: cannot execute: No such file or directory

```

---

### Post by HalPomeranz on 2008-08-25
What happens if you specify the correct absolute pathname to the rrdtool command when constructing your command-line (e.g. /usr/local/bin/rrdtool or whatever)?

---

### Post by dwhitney67 on 2008-08-25
> **CRCarl said:**
> All - 
    I am having an odd issue with a bash script. I am building a string variable  that I want to eventually execute. If I echo the string then copy and paste it in term it runs fine, however when I exec the string it fails. Details below - 

The relevent part of the script - 

```

IFS=$'\n'
for line in $(cat "$file")
do
	usertime=$(echo "$line" | awk '{print $20}' | grep [0-9]$)
	systime=$(echo "$line" | awk '{print $21}' | grep [0-9]$)
	updateline=$(echo rrdtool update "$pathtorrd" "$EPOCHdate":"$usertime":"$systime" | grep [0-9]$)			
	echo $updateline    #for troubleshooting
	exec `$updateline`
	EPOCHdate=$(($EPOCHdate+300))
done

``` 
...
What purpose does "| grep [0-9]$" serve?

I have no idea what 'rrdtool' is, but I presume it is an executable.  Therefore, why are you using exec?  It is not necessary.

I'm no bash expert, but I threw together these trivial programs to test what your attempting to do:

tester.sh:
```
#!/bin/sh

for file in `ls -1`
do
        cmd="sh /home/user/foo.sh 1:2:$file"
        $cmd
done
```
foo.sh:
```
#!/bin/sh

echo "I'm foo!"
echo arg is $1
exit 0
```

---

### Post by CRCarl on 2008-08-25
So integrating both of the suggestions above I'm still getting the "No such file or directory" error. If I copy and paste one of these lines in term it works fine.

```
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219659000:1:3: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219659300:1:3: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219659600:1:1: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219659900:0:2: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219660800:0:2: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219661100:1:3: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219661400:1:3: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219661700:0:2: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219662000:1:2: No such file or directory
./dorado2.sh: line 27: /usr/bin/rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219662300:1:2: No such file or directory

```

---

### Post by mssever on 2008-08-25
[LIST]
[*]When you echo $updateLine, is the result IDENTICAL to what you'd type at the command line?
[*]Don't use exec. You can use eval on a string, or just do ```
$updateLine
```
[/LIST]

---

### Post by dwhitney67 on 2008-08-25
What is rrdtool??

When you pass the 'update' option, does it require a hyphen (or double-hyphen) in front of it?

P.S.  If you have a man-page for 'rrdtool', please post the synopsis.

---

### Post by mssever on 2008-08-25
> **dwhitney67 said:**
> What is rrdtool??
```
~:$ rrdtool
The program 'rrdtool' is currently not installed.  You can install it by typing:
sudo apt-get install rrdtool
-bash: rrdtool: command not found
[Exit 127 ]
~:$ rapt show rrdtool
Package: rrdtool
Priority: extra
Section: utils
Installed-Size: 1136
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: David Martínez Moreno <ender@debian.org>
Architecture: i386
Version: 1.2.19-1ubuntu1
Depends: libc6 (>= 2.5-5), libpng12-0 (>= 1.2.13-4), librrd2 (>= 1.2.19-1ubuntu1), zlib1g (>= 1:1.2.1)
Suggests: librrds-perl
Filename: pool/main/r/rrdtool/rrdtool_1.2.19-1ubuntu1_i386.deb
Size: 522910
MD5sum: d0f01b89e283b656774b67adf36ec6ce
SHA1: 44108a3a19494b2393a540b00568b94b73a0ef21
SHA256: b510c8d98b03ed5a76f9d31271ac282124024dd3e2d9650efb0cbcdc1ba06e9d
Description: Time-series data storage and display system (programs)
 The Round Robin Database Tool (RRDtool) is a system to store and display
 time-series data (e.g. network bandwidth, machine-room temperature,
 server load average). It stores the data in Round Robin Databases (RRDs),
 a very compact way that will not expand over time. RRDtool processes the
 extracted data to enforce a certain data density, allowing for useful
 graphical representation of data values.
 .
 RRDtool is often used via various wrappers that can poll data from devices
 and feed data into RRDs, as well as provide a friendlier user interface and
 customized graphs.
 .
 This package contains command-line programs used to access and manipulate
 RRDs.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

~:$ 
```

---

### Post by dwhitney67 on 2008-08-25
> **dwhitney67 said:**
> What is rrdtool??

When you pass the 'update' option, does it require a hyphen (or double-hyphen) in front of it?

P.S.  If you have a man-page for 'rrdtool', please post the synopsis.
Nevermind.

OP, look at this web-page for the manpage for rrdtool's update feature.  Ensure that you are using the command properly.
[http://oss.oetiker.ch/rrdtool/doc/rrdupdate.en.html](http://oss.oetiker.ch/rrdtool/doc/rrdupdate.en.html)

---

### Post by ghostdog74 on 2008-08-25
> **dwhitney67 said:**
> 
```
#!/bin/sh

for file in `ls -1`
do
        cmd="sh /home/user/foo.sh 1:2:$file"
        $cmd
done
```
foo.sh:

take care of files with spaces. (useless use of ls)
Use shell expansion.
```

for file in * 
do
..
done

```

---

### Post by ghostdog74 on 2008-08-25
> **CRCarl said:**
> All - 
    I am having an odd issue with a bash script. I am building a string variable  that I want to eventually execute. If I echo the string then copy and paste it in term it runs fine, however when I exec the string it fails. Details below - 

The relevent part of the script - 

```

IFS=$'\n'
for line in $(cat "$file")
do
	usertime=$(echo "$line" | awk '{print $20}' | grep [0-9]$)
	systime=$(echo "$line" | awk '{print $21}' | grep [0-9]$)
	updateline=$(echo rrdtool update "$pathtorrd" "$EPOCHdate":"$usertime":"$systime" | grep [0-9]$)			
	echo $updateline    #for troubleshooting
	exec `$updateline`
	EPOCHdate=$(($EPOCHdate+300))
done

```

You will notice that I am echo'ing the string, then executing it. The output is - 
```

rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219662300:0:2
./dorado2.sh: line 30: rrdtool update /home/user/perfstat/hosts/acomputer1/cpu.acomputer1.rrd 1219662300:0:2: No such file or directory

```

However if I copy and paste the results of the echo (first line above) it works just fine. Everything is running as me, all the paths are fully qualified, I dos2unix'ed the file, nothing helped. 

Ideas?

Thanks.

exec is not necessary. Show your input file if possible. 
```

#!/bin/bash
pathtorrd=/somewhere
EPOCHdate="something"
awk -v pathtorrd="${pathtorrd}"  -v epochdate="${EPOCHdate}" '
$20 ~ /[0-9]$/{usertime=$20} 
$21 ~ /[0-9]$/ { systime = $21 }
{ 
    cmd = "rrdtool update " pathtorrd" "epochdate" "usertime":"systime 
    print cmd
    # system(cmd) #uncomment to use
}' file 

```

---

