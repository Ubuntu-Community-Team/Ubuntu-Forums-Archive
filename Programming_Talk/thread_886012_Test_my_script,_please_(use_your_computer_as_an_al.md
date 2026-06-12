---
title: "Test my script, please (use your computer as an alarm)"
date: 2008-08-10
forum: Programming Talk
---

### Post by ConMan318 on 2008-08-10
I have written a script, and I would like to know if it runs in other Linux distros, as I have tried to make it portable but cannot test if works on other distros on my own.  I would also like to know if there are any errors in the script, so it would be great if people could try to cause it to screw up :).

I made a thread about this a while ago but I have since added a whole lot of new things: mostly being the user-editable settings that are read from/written to a hidden settings file through a simple user interface.

Feel free to ask any questions about the script here and please report any errors you may get.  Also feel free to critique the source code.



To run the script, simply save the attached file, navigate to where it is located and run
```

tar -zxf alarmScript.tar.gz && rm alarmScript.tar.gz
chmod 755 alarm

```
which will extract it, delete the tarball, and make the file executable.  Then run it with
```

./alarm

```

After testing it, if you wish to remove it, just run
```

rm /path/to/alarm ~/.alarmSettings

```
where path/to/alarm is replaced with wherever you extracted the file.

Thanks in advance.

---

