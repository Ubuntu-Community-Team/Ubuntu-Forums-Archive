---
title: "Bash scripting: Writing a file.."
date: 2005-07-13
forum: Programming Talk
---

### Post by audax321 on 2005-07-13
I'm writing a program to auto generate a thumbnail gallery for me in the format I need. But the problem is that I need to write the html file using the shell script. Can anyone tell me how to do this, I couldn't really find anything useful in Google.

I tried:

echo "THIS IS STUFF FOR THE FILE" > index.html

but, if I try to run this line another time, it overwrites anything that was written in the file on the previous run.


Thanks...  :)

---

### Post by jerome bettis on 2005-07-13
echo "THIS IS STUFF FOR THE FILE" > index.html
the single > just overwrites anything in there.

echo "THIS IS STUFF FOR THE FILE" >> index.html
the dual >> appends the stuff at the end.

you might want to take a look at python if your script is somewhat complicated.

---

### Post by audax321 on 2005-07-14
Nice, thanks... it shouldn't be too complicated. I just want to be able to select a bunch of pictures in Nautilus and run it to make the html file after converting using ImageMagick. A simple loop with some html output each run should do it.    :grin:

---

### Post by m87 on 2005-07-14
ahahah me too, I've done this 2 years ago! It seems everyone starts using BASH scripting and some time he comes to that problem :) By the way, my script is 2 years old and I am still using it :)

You should only use '>>' as when the file doesn't exist, '>>' (append) creates it as if it was '>'

marco

---

### Post by audax321 on 2005-07-15
Yeah, I didn't know how useful bash scripting was until I actually started using it. And that nautilus script folder has to be one of the most useful things in gnome :)

Now, I have another question. Some of the lines are extremely long, is there anyway to split a line up into a number of lines?

so instead of:

 echo -e "blah" >> crap.html && echo -e "woohoo" >> crap.html && echo -e "huh" >> crap.html

it could be:

echo -e "blah" >> crap.html && (some_escape_character)
echo -e "woohoo" >> crap.html && (some_escape_character)
echo -e "huh" >> crap.html

---

### Post by m87 on 2005-07-15
\n -> newline
\t -> tabulation
\r -> carriage return
\\ -> backslash

etc. etc. they are a lot

try

$ echo -e asd\nasd

marco

---

### Post by tomchuk on 2005-07-15
Also "echo -n" will echo something without the newline:
```

$ echo -n foo > test
$ echo bar >> test
$ cat test
foobar

```

---

### Post by binarylime on 2010-10-27
> **m87 said:**
> ahahah me too, I've done this 2 years ago! It seems everyone starts using BASH scripting and some time he comes to that problem :) By the way, my script is 2 years old and I am still using it :)

You should only use '>>' as when the file doesn't exist, '>>' (append) creates it as if it was '>'

marco

Kudos!  I found this post after having a "no brain-er" moment when using a Bash Script to configure Debian/Ubuntu network interfaces for noobs I work with.  The finished product left me scratching my head!

In short, I was using the ">" (open and write) instead of ">>" (open, append) to my interfaces file for EVERY echo statement:

echo "# This file describes the network interfaces available on your system" **>** /etc/network/interfaces
echo "# and how to activate them. For more information, see interfaces(5)." **>>** /etc/network/interfaces
echo " " **>>** /etc/network/interfaces
echo "# The loopback network interface" **>>** /etc/network/interfaces
echo "auto lo" **>>** /etc/network/interfaces
echo "iface lo inet loopback" **>>** /etc/network/interfaces
echo " " **>>** /etc/network/interfaces
echo "# The primary network interface" **>>** /etc/network/interfaces
echo "allow-hotplug $ETH" **>>** /etc/network/interfaces
echo "iface $ETH inet static" **>>** /etc/network/interfaces
echo "  address $IP" **>>** /etc/network/interfaces
echo "  netmask $NETMASK" **>>** /etc/network/interfaces
echo "  gateway $GATEWAY" **>>** /etc/network/interfaces


Thanks!!

---

### Post by PmDematagoda on 2010-10-27
Thread locked to prevent further necromancy.

---

