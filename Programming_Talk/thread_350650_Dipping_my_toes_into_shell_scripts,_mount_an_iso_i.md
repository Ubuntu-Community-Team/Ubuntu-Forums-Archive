---
title: "Dipping my toes into shell scripts, mount an iso in kde"
date: 2007-01-31
forum: Programming Talk
---

### Post by crysys on 2007-01-31
Ok my programming experience amounts to QBasic classes in HS and a semester of C++ in college where I figured out that I didn't like programming. :( 

I want to be able to easily mount and unmount an ISO image as a drive and I'm using KDE so I did some googling and started throwing together a simple mount script.  I believe I'm hung up in syntax and I just don't know what's going wrong, if someone could point me in the right direction, that would be awesome.  What I have:

```
#!/bin/sh
isofile=`kdialog --getopenfilename *.iso`
kdesu -u root -c 'mount $isofile /media/iso -t iso9660 -o loop'

```

But all I get from the terminal is mounts help output.  Now if I replace the kdesu line with an,
```
echo $isofile
```
it returns,
```
/home/me/myiso.iso
```
just fine.  Near as I can tell, mount never gets the variable because it's nested away inside kdesu.  But I'm guessing.  Any insight or recommendations for doing this without having to ask for root?  Oh, and I did modprobe loop.

---

### Post by lloyd_b on 2007-02-01
```
#!/bin/sh
isofile=`kdialog --getopenfilename *.iso`
kdesu -u root -c 'mount $isofile /media/iso -t iso9660 -o loop'
```

You're setting the value of 'isofile' to a command, not the result of the command.  Net result is that I think it's winding up trying to execute the following:
```
kdesu -u root -c 'mount kdialog --getopenfilename *.iso/media -t iso9660 -o loop'
```
Which is of course garbage as far as the mount command is concerned.

I'm not sure this is the *best* solution, but it should work. 
```
#!/bin/sh
echo -n "kdesu -u root -c '" > temp.script
kdialog --getopenfilename *.iso >> temp.script
echo -n "/media -t iso9660 -o loop'" >> temp.script
chmod 700 temp.script
temp.script
rm temp.script
```

What this does is build the "kdesu" command a piece at a time, into a file called "temp.script".  It then makes that script executable, runs it, and then deletes it.  What I'm not sure of is whether or not "kdialog" will stick a newline into the script (I don't run KDE, so I can't test it).  Try running this script without the "rm temp.script", then look at "temp.script" to see if it's generating the correct command.

Lloyd B.

---

### Post by crysys on 2007-02-01
The kdialog command is enclosed in back quotes which are supposed to execute the command.  It is passing the results of that command on and not just the command as evidenced when I replace the kdesu line with a simple echo.

But I tried your version out and it does indeed add a newline.  Then, while exploring why it does that and how I might prevent it I learned about the difference between back quote, single quote and double quote.  Especially that ' and " do not work the same.  So I changed to double quotes on the kdesu line and now it passes the variable correctly.

It works! :guitar: 

I'm still unsure why it works this way.  According to Linux Shell Scripting Tutorial:

> "Double Quotes" - Anything enclose in double quotes removed meaning of that characters (except \ and $).
'Single quotes' - Enclosed in single quotes remains unchanged.
`Back quote` - To execute command

I would think the double quotes would cause the problem I saw and not single quotes.  But perhaps I'm reading the definitions incorrectly(that double quote is stricter than single quote?). :confused: 

Anyway, thank you for the assist!

---

### Post by lloyd_b on 2007-02-01
> The kdialog command is enclosed in back quotes which are supposed to execute the command. It is passing the results of that command on and not just the command as evidenced when I replace the kdesu line with a simple echo.

Oops - missed that one.

> I would think the double quotes would cause the problem I saw and not single quotes. But perhaps I'm reading the definitions incorrectly(that double quote is stricter than single quote?).

As far as shell variables are concerned:
Enclosing a shell variable in double quotes ("$TEST") does NOT prevent it from being interpreted
Enclosing a shell variable in single quotes ('$TEST') DOES prevent it from being interpreted.

So:
```
#!/bin/sh
TEST="this is a test"
echo $TEST
echo "$TEST"
echo '$TEST'
```
produces
```
this is a test
this is a test
$TEST
```
(I just tested this to verify it...)

So as far as shell variables are concerned, double quotes is LESS literal than single quotes.  The tutorial is a bit misleading on that one.

At any rate, problem solved, and I learned something in the process. Cool :D 

Lloyd B.

---

### Post by LotsOfPhil on 2007-02-01
> **crysys said:**
> Ok my programming experience amounts to QBasic classes in HS and a semester of C++ in college where I figured out that I didn't like programming. :( 

I want to be able to easily mount and unmount an ISO image as a drive and I'm using KDE so I did some googling and started throwing together a simple mount script.  I believe I'm hung up in syntax and I just don't know what's going wrong, if someone could point me in the right direction, that would be awesome.  What I have:

```
#!/bin/sh
isofile=`kdialog --getopenfilename *.iso`
kdesu -u root -c 'mount $isofile /media/iso -t iso9660 -o loop'

```


All you need to do is switch your single quotes in the kdesu... line to double quotes. The problem is that you are outputting $isofile, not the value of isofile. Look at your check with echo. You say "echo $isofile" works. No quotes. If you do echo '$isofile' it won't work.

---

### Post by LotsOfPhil on 2007-02-01
P.S. I hope I am not restating what everyone else said. I am not sure that my brain is working.

---

