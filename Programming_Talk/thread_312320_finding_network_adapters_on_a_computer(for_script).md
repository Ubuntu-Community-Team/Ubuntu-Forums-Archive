---
title: "finding network adapters on a computer(for script)"
date: 2006-12-04
forum: Programming Talk
---

### Post by vtechstu on 2006-12-04
I'm trying to write a script for something.  At some point in it, I need to create a list of all the network adapters on current computer.  Since the results of ifconfig aren't one line each, doing | awk '{print $1}' returns all of the adapters, plus some junk info( a good bit). 

I'm just learning how to use regular expressions, so this is where I need the help.  I need to narrow the results down to something that starts with a lowercase a-z, ends with a 0-9, and a string which is no longer then 8 characters.  

Could someone good with expression please help me out? I'm sure it's simple but i'm not having much luck making sense of these books I have!


Chase

---

### Post by lloyd_b on 2006-12-04
Alternate method:

 ```
ifconfig | cut -d ' ' -f1 | grep -e [0-9:a-z:A-Z]
```

The "cut" command will eliminate everything except the interface names (eth0, lo, ath1, etc), but will leave a bunch of blank lines.  The grep command takes care of the blank lines....

Lloyd B.

---

### Post by vtechstu on 2006-12-04
> **lloyd_b said:**
> Alternate method:

 ```
ifconfig | cut -d ' ' -f1 | grep -e [0-9:a-z:A-Z]
```

The "cut" command will eliminate everything except the interface names (eth0, lo, ath1, etc), but will leave a bunch of blank lines.  The grep command takes care of the blank lines....

Lloyd B.

You my friend are awesome! It works great for some of the computers, others not.  If you have the time, could you please explain to me how that works( which each part does, except the grep part). 

```
 [twinkie 7] /sbin/ifconfig -a | cut -d ' ' -f1
lo0:
        inet
bge0:
        inet
bge1:
        inet
 [twinkie 8] /sbin/ifconfig -a | cut -d ' ' -f1 | grep -e [0-9:a-z:A-Z]
grep: No match.

```

So you see, for the other servers, without the grep, the three adapters, plus 'inet' are returned, but the grep part doesn't clear the rest.  i tried egrep and stayed the same.  Any ideas?

Chase

---

### Post by lloyd_b on 2006-12-04
> You my friend are awesome! It works great for some of the computers, others not. If you have the time, could you please explain to me how that works( which each part does, except the grep part).

1. ifconfig - (I'm assuming you already know what this does)

2. cut - cut is designed to "cut" specific columns from a text display.  In this case, the "-d ' '" tells it that the columns are separated by spaces, and the "-f1" tells it that we only want the first field.  Net result - it returns everything before the first space character in each line.  Lines with a space character in the first position will return a blank line.

3. grep -e [0-9:a-z:A-Z] - the "-e" option tells it to use and extended regex for the match (same as running "egrep [0-9:a-z:A-Z]").  The [0-9:a-z:A-Z] regex matches lines that have any alphanumeric characters, i.e. any non-blank lines.

> So you see, for the other servers, without the grep, the three adapters, plus 'inet' are returned, but the grep part doesn't clear the rest. i tried egrep and stayed the same. Any ideas?

The problem is that those other servers have the results of "ifconfig" returned in a different format.  It would be pretty trivial to come up with an equivalent command for them if I knew the format, but developing a script that will work correctly with either format is a little bit trickier...

That alternate format seems to put a colon after the interface.  We could use that to key another cut command:

```
ifconfig | cut -d ' ' -f1 | cut -d ':' -f1 | grep -e [0-9:a-z:A-Z]
```

Since there won't be any colons in the "first" format, in that case the "cut" command will return the entire line.  For the second format, it should clean out those "   inet" lines (provided that the leading spaces are in fact spaces, and not a tab character!).

If it turns out that those ARE tabs (and not spaces):

```
ifconfig | tr '\t' ' ' | cut -d ' ' -f1 | cut -d ':' -f1 | grep -e [0-9:a-z:A-Z]
```

The "tr" command translates one character into another.  In this case, it translates all tab characters (the '\t') to space characters (the ' ').  You'll probably still want the "cut -d ':' -f1" part, though, as it will get rid of the colons, making the output the same for both types of machine.

Note: Don't be surprised if you encounter machines with yet another format for the "ifconfig" output - there's nothing standardized about such formats, so each Unix variant (and possibly different versions of the same variant) may have a different format.

I was looking at your message - it looks like those other machines don't support extended regex in their version of "grep" (another thing that isn't standard from one Unix to the next).  If they have the "egrep" command (which is the same thing), then you can try: 

```
ifconfig | tr '\t' ' ' | cut -d ' ' -f1 | cut -d ':' -f1 | egrep [0-9:a-z:A-Z]
```

Note: if "egrep" isn't available, try "rgrep" - it should work in this case.

Lloyd B.

---

### Post by vtechstu on 2006-12-05
Thank you for the explanation of everything. I was able to use what you gave me to do many other things.  For a while the command would not work, the grep part, but found it being caused by a lack of quotes around [0-9:a-z:A-Z].  doing help fixed and works great for all the servers I've tried it on so far.  Thanks again.

chase

---

### Post by Wim Sturkenboom on 2006-12-06
You can use ```
cat /proc/net/dev
```to find the interfaces. I wrote a little bandwidth monitor around it.

---

### Post by lloyd_b on 2006-12-06
The problem is that "/proc" is pretty much a Linux specific trick (AFAIK).  If you're working in a mixed environment (Linux, AIX, BSD, Solaris) then you'd need a separate solution for each vendor.

AFAIK, "ifconfig" serves the same purpose on pretty much every Unix variant, though the format of it's output does vary from vendor to vendor.

I wouldn't rely on that parsing script as a "universal" solution, but it's closer to one than using the "/proc" method.

Lloyd B.

---

