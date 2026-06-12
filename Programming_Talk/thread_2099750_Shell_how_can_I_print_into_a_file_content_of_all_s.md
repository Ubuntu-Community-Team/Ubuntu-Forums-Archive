---
title: "Shell: how can I print into a file content of all subfolders of a folder?"
date: 2012-12-30
forum: Programming Talk
---

### Post by vincegata on 2012-12-30
Hello,

Right now my script looks like this (I have more subfolders actually):

```

echo "************************ Finance Papers ************************" > /home/ListOfPapers.txt	# Add header
txt -o /home/vince/Papers/Papers_Finance >> /home/ListOfPapers.txt					# Add list of papers in the folder.
echo >> /home/vince/Documents/ListOfPapers.txt								# Add empty line.

echo "************************ Math Papers ************************" >> /home/ListOfPapers.txt
txt -o /home/vince/Papers/Papers_Math >> /home/ListOfPapers.txt
echo >> /home/vince/Documents/ListOfPapers.txt

echo "************************ Programming Papers ************************" >> /home/ListOfPapers.txt
txt -o /home/vince/Papers/Papers_Prog >> /home/ListOfPapers.txt
echo >> /home/ListOfPapers.txt

```

With such script, when I add or delete subfolders in /home/vince/Papers/ folder I need to edit my script. 

How can I write a script so it will navigate each subfolder and print its contents (in the same format: header, list of files, space.)

Thanks in advance.

---

### Post by ehrt74 on 2012-12-30
Have you tried playing around with something like:

```

for i in `find . -type d`
do
echo $i
ls $i
done

```

---

### Post by vincegata on 2012-12-30
> **ehrt74 said:**
> Have you tried playing around with something like:

```

for i in `find . -type d`
do
echo $i
ls $i
done

```

It's good -- thank you!

The only thing is it cannot handle folders with spaces, such as
/Papers Numerical Analysis

Is it possible to fix it, o.w. I'll just rename the folders.

THX

---

### Post by HomelandSecurity on 2012-12-30
```

for i in `find . -type d` 
do 
echo "$i" ls "$i" 
done

```

what about the subfolders of a folder into the selcte folder? the you'll have to use find not ls!

---

### Post by Cheesemill on 2012-12-30
How about just using the tree command (you may need to install it first).

```
rob@arch:~$ tree ~/ISOs
[COLOR=MediumTurquoise]/home/rob/ISOs[/COLOR]
&#9500;&#9472;&#9472; haiku-r1alpha4.iso
&#9500;&#9472;&#9472; [COLOR=Blue]Linux[/COLOR]
&#9474;   &#9500;&#9472;&#9472; archlinux-2012.11.01-dual.iso
&#9474;   &#9500;&#9472;&#9472; archlinux-2012.12.01-dual.iso
&#9474;   &#9500;&#9472;&#9472; BT5R3-GNOME-64.iso
&#9474;   &#9500;&#9472;&#9472; [COLOR=Blue]CrunchBang[/COLOR]
&#9474;   &#9474;   &#9500;&#9472;&#9472; crunchbang-11-20120430-amd64.iso
&#9474;   &#9474;   &#9500;&#9472;&#9472; crunchbang-11-20120430-i386.iso
&#9474;   &#9474;   &#9492;&#9472;&#9472; crunchbang-11-20121015-amd64.iso
&#9474;   &#9500;&#9472;&#9472; debian-6.0.6-amd64-businesscard.iso
&#9474;   &#9500;&#9472;&#9472; debian-wheezy-DI-b3-amd64-netinst.iso
&#9474;   &#9500;&#9472;&#9472; linuxmint-14.1-cinnamon-dvd-64bit.iso
&#9474;   &#9492;&#9472;&#9472; [COLOR=Blue]Ubuntu[/COLOR]
&#9474;       &#9500;&#9472;&#9472; [COLOR=Blue]Precise[/COLOR]
&#9474;       &#9474;   &#9500;&#9472;&#9472; edubuntu-12.04.1-dvd-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kubuntu-12.04.1-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kubuntu-12.04.1-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kubuntu-12.04.1-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kubuntu-12.04.1-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.04-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.04-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.04-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.04-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04.1-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04.1-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04.1-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04.1-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04.1-server-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04.1-server-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04-business-desktop-remix-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04-business-desktop-remix-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04-cloud-live-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04-mini-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04-mini-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.04-mini-i386-nonpae.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntustudio-12.04.1-dvd-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; xubuntu-12.04.1-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; xubuntu-12.04.1-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; xubuntu-12.04.1-desktop-amd64.iso
&#9474;       &#9474;   &#9492;&#9472;&#9472; xubuntu-12.04.1-desktop-i386.iso
&#9474;       &#9500;&#9472;&#9472; [COLOR=Blue]Quantal[/COLOR]
&#9474;       &#9474;   &#9500;&#9472;&#9472; edubuntu-12.10-dvd-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kubuntu-12.10-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kubuntu-12.10-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.10-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.10-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.10-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lubuntu-12.10-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; mini.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.10-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.10-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.10-server-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-12.10-server-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntu-secure-remix-12.10-64bit.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntustudio-12.10-dvd-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; ubuntustudio-12.10-dvd-amd64.iso.zs-old
&#9474;       &#9474;   &#9500;&#9472;&#9472; xubuntu-12.10-desktop-amd64.iso
&#9474;       &#9474;   &#9492;&#9472;&#9472; xubuntu-12.10-desktop-i386.iso
&#9474;       &#9500;&#9472;&#9472; [COLOR=Blue]Raring[/COLOR]
&#9474;       &#9474;   &#9500;&#9472;&#9472; kraring-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kraring-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kraring-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; kraring-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lraring-alternate-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lraring-alternate-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lraring-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; lraring-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; mini.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; raring-desktop-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; raring-desktop-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; raring-server-amd64.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; raring-server-i386.iso
&#9474;       &#9474;   &#9500;&#9472;&#9472; xraring-desktop-amd64.iso
&#9474;       &#9474;   &#9492;&#9472;&#9472; xraring-desktop-i386.iso
&#9474;       &#9500;&#9472;&#9472; ubuntu-10.04.4-server-amd64.iso
&#9474;       &#9500;&#9472;&#9472; ubuntu-8.04-desktop-i386.iso
&#9474;       &#9492;&#9472;&#9472; warty-release-install-i386.iso
&#9500;&#9472;&#9472; [COLOR=Blue]Microsoft[/COLOR]
&#9474;   &#9492;&#9472;&#9472; WIN7_SP1 AIO_EN_DVD.ISO
&#9500;&#9472;&#9472; oi-dev-151a5-text-x86.iso
&#9492;&#9472;&#9472; sol-11_1-text-x86.iso
```


If you look at the man page there are loads of different options you can use, for example the -o option will output to a file instead of the screen.

---

### Post by ofnuts on 2012-12-30
> **ehrt74 said:**
> Have you tried playing around with something like: ```
 for i in `find . -type d` do echo $i ls $i done 
```  You can use the shorter (and less prone to parsing problems):     To print file path/names:  ```
  find . 
```      To print file information:  ```
  find . -ls 
```      To execute a command against each file:   ```
  # {} is replaced by the name of each file  # (no need to use quotes even if spaces are expected) find . -exec somecommand {} \; 
```

---

### Post by vincegata on 2012-12-30
Thank you for all responses!

---

### Post by vincegata on 2012-12-30
> **ofnuts said:**
> You can use the shorter (and less prone to parsing problems):     To print file path/names:  ```
  find . 
```      To print file information:  ```
  find . -ls 
```      To execute a command against each file:   ```
  # {} is replaced by the name of each file  # (no need to use quotes even if spaces are expected) find . -exec somecommand {} \; 
```

It does take care of spaces in folders, how do I insert name of folder and space?

Header (name of a folder)
List of files
Space

---

