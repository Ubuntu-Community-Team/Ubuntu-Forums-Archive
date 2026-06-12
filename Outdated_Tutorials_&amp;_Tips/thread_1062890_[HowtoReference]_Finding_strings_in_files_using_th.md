---
title: "[Howto/Reference] Finding strings in files using the Command Line"
date: 2009-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Achetar on 2009-02-07
Okay, I decided to write a tutorial on how to find strings in files in the command line. This can be handy if your xorg.conf is broken on an OS that does not have a nice 'xfix' feature (alright, so you can run X -configure, but not everyone knows that).

The first thing I want to do is kill a method that has been spreading like wildfire (I myself helped spread it until someone showed me the right way to do it). Many people will tell you to do this to find a string in a file:
```

$ cat xorg.conf | grep Device

```However, there are two problems with this. 1st off, it doesn't give you line numbers. So when you find it, you still have no clue where it is, just that it is in there. You can add the -n option to cat to fix this:
```

$ cat -n xorg.conf | grep Device

```2nd, it wastes time. grep can already search inside files, there is no need to cat the file.
```

$ grep -n Device xorg.conf

```That command will do exactly the same thing as cat | grep, but without running two programs. Granted, this is a small difference in CPU time, but it can become noticable when searching through thousands of files.

grep can also search through multiple files with one command:
```

$ grep -n Device xorg.conf xorg.conf.old xorg.conf.200811071232

```That is something that cat cannot do.

You can also reverse grep's functionality by using the -v flag. So instead of printing lines that have a certain string, it will print all lines that DON'T have that string.
```

$ grep -n -v Device xorg.conf

```And you can make it case-insensitive:
```

$ grep -n -i device xorg.conf

```So....what if there is a space in your search string? Doing
```

$ grep -n Device "Card0" xorg.conf

```will NOT work. Two things need to be done to fix this. The first is to wrap the string in quotes. The second is to escape the quotes around Card0. Why? Otherwise the search won't work. It will be searching for Device in the files Card0 "" and xorg.conf. Backslashes are used to escape characters that we don't want bash interpreting.
```

$ grep -n "Device \"Card0\"" xorg.conf

```But what about if there is (as so often the case is) more than one space inbetween Device and Card0? Regex to the rescue! We can use the -e flag to add regex functionality to grep. Then we can use regex to find lines that contain any number of spaces in between Device and Card0. (Note that regex characters must also be escaped with backslashes)
```

$ grep -n -e "Device \+\"Card0\"" xorg.conf

```A full grep regex guide is in the grep manpage. The + operator searches for 1 or more of the preceding character. In this case the preceding character was a space, so it searched for 1 or more spaces.

Now, how about find and replace? Well, you could use nano's ^W ^R function, or you could use sed to automagically do it for you, without opening an editor!
```

$ sed -i s/Card0/nVidia GeForce 8800GT/ xorg.conf

```A word of warning: sed does not search for complete words, just strings, so if you have OtherCard0 and Card0, they will end up being OthernVidia GeForce 8800GT and nVidia GeForce 8800GT. 

Regex can be used in most sed versions without having to add the -r flag, but some require it, so in scripts and other portable things (such as tutorials) use the -r flag for regex
```

$ sed -i -r s/Card\./nVidia GeForce 8800GT/ xorg.conf

```WARNING: Do NOT run that previous command if you have more than one graphics card, it will change all identifiers to the same one, foobaring your xorg.conf.

Also note: In general, you can put two single dash flags together into one, like so:
```

$ sed -ir s/Card0/nVidia GeForce 8800GT/ xorg.conf

```
I kept them apart to make it easier to see what i had changed.

I hope this helps someone! If you have any questions or catch any errors please let me know!

---

