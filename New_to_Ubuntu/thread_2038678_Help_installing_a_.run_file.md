---
title: "Help installing a .run file"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by rasimpson318 on 2012-08-07
I need help installing a .run file.  The particular file I'm trying to install is the Usenet Browser from Newshosting.com.  I downloaded it with Chrome and it is in my "Downloads" folder.  I selected to allow as executable and tried double clicking.  Nothing happened.  I then tried to run in terminal using the chmod comand and ./ command.  Still nothing.  I am out of ideas.  Any help would be greatly appreciated.

---

### Post by steeldriver on 2012-08-07
Unfortunately there's no one-size-fits-all answer - it depends what's in the .run file

Maybe if you post the exact commands you tried and the errors you got someone will be able to figure it out

---

### Post by afixane on 2012-08-07
Right Click the file, Select Properties, and go to "Permission" Tab, check the "Allow this file to run as program". Then double click it, and try to select "Open In terminal".

---

### Post by rasimpson318 on 2012-08-07
Steps I've already taken:

Downloaded from website.
Rightclick, select permisions and selected "Allow to run as executable"
Waited....nothing ever happened.
So...

Opened terminal
cd to folder
chmod +x filename.run
./filename.run
next line of terminal shows the cd path and nothing ever happened.

Also tried above running with sudo.

As always, any help is appreciated.

---

### Post by bogan on 2012-08-07
Hi!, r**asimpson318,**

Try, after cd to folder:```
 sudo sh <filemame>
```Alternatively, if that does not work either, and gives no error clues, try Right Click on the file, select 'Extract Here,' [ if that option is available], and see what you get, maybe a ReadMe file, if there is not one in the site you downloaded from.

If that's not valid, try ```
sudo sh <filename> --extract-only
``` Some .run files are self-extracting and offer that option, eg nvidia driver install .run files.

Chao!, **bogan.**

---

### Post by rasimpson318 on 2012-08-07
When typing in those commands I get the following error:

nh.run: 2: nh.run: Syntax error: end of file unexpected (expecting ")")

and when I right click, there is no option to extract.

---

### Post by steeldriver on 2012-08-07
It sounds like it is a script - try opening it in a text editor - or just

```
less nh.run
```so you can find out what kind of script it is - it may simply be that it's asking for an interpreter that you don't have on your system (such as csh)

The trouble with using 

```
sh *file*
``` on unknown shell scripts is (I think) that it forces interpretation by /bin/sh which is now symlinked to the dash interpreter - overriding the #! in the file itself - obviously that's fine if it's a dash script but if it's a bash or csh script it likely breaks things - for example:

```
#!/bin/bash
echo "This is a test."

for x in {a..f}; do echo $x; done
``````
$ ./test.sh
This is a test.
a
b
c
d
e
f
``````
$ sh ./test.sh 
This is a test.
{a..f}
```

---

### Post by rasimpson318 on 2012-08-07
When I run less nh.run it comes up with: 


"nh.run" may be a binary file.  See it anyway? 

then, when I say yes, it comes up with a bunch of zero's and such.

---

### Post by steeldriver on 2012-08-07
OK in that case I was wrong about it being a script - sorry

If it is a binary executable then either it will run or it won't (e.g. it may be compiled for the wrong architecture for your system) - there's not much we can do to 'fix' that bar making sure the executable permission is set (which you already did) - I suggest you contact tech support at newshosting.com

---

### Post by rasimpson318 on 2012-08-07
Ok, thanks for the help.  Since it's not going to be working, at least for the foreseeable future, do you have any recommendations for a NZB download client that supports pick and choose which files in the NZB to download, and that's free?

---

### Post by rasimpson318 on 2012-08-07
I just wanted to follow up for anyone else who was having this issue.  Apparently it was because I have the 64bit OS.  They advised my to install the 32bit libraries, and after doing so, everything worked perfectly.  Thanks again for all the help and support.

---

