---
title: "Checksum and move folder with conditions"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by octopus22 on 2011-10-01
Hi all!

I'm quite new to bash scripting and other stuff.

Have the following thing in mind:
a script that run by cron (i know how to use it!)
find all *.sfv files in folders at given path
check sfv file
moves **folder** with files checked to OK to another path

structure is 
/download
 /folder1/somefile.sfv
 /folder2/differentfile.sfv
 /folder3/otherfile.sfv

move OK folders to /checked
1 sfv file per folder

i understand, that's not so hard bash script, but it takes hours to understand pipeline, grep and other stuff.
i have pieces of puzzle, but can't take them together

---

### Post by papibe on 2011-10-01
First you need to install a program that do the checking:
```
$ sudo apt-get install cksfv
```
[Here]("https://ubuntuincident.wordpress.com/2011/02/11/verify-sfv-files/")'s some examples on how to use it.

You want to check every sfv files, so I would start finding them:
```
$ find start/ -iname '*.sfv'
```
That finds and prints all sfv files under the start/ directory.

Find can execute a command for every file that is found:
```
$ find start/ -iname '*.sfv' -exec cksfv -f '{}' \;
```

To execute more complex commands you can use a bash script, instead of a simple command:
```
$ find start/ -iname '*.sfv' -exec bash -c 'cksfv -f "$1"; echo $?' _ '{}' \;
```
To further research I recommend this [guide]("http://mywiki.wooledge.org/UsingFind") (suggested by bash expert extraordinaire sisco311).

I hope that point you in the right direction.

Regards.

---

### Post by octopus22 on 2011-10-02
Thank you for help!

> $ find start/ -iname '*.sfv' -exec bash -c 'cksfv -f "$1"; echo $?' _ '{}'\;
find: missing argument `-exec'

other commands work, but can't understand how to get back result of sfv check. digging it =)

---

### Post by papibe on 2011-10-02
Sorry, it should a space between the end:
```
...'{}'  \;
```

---

