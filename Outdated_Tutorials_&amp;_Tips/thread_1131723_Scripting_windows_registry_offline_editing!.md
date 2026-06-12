---
title: "Scripting windows registry offline editing!"
date: 2009-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by wileur on 2009-04-21
As an administrator of a network with a Linux LDAP/SMB server and windows clients I occasionally have the need to change a user's settings. One way is to have the logon scripts load a registry change which works fine, but what if you need to find out what settings a user has right away and can't wait for him to login? Or you want to update every user at once and know that it's done? Or any other reason for hacking the registry.

I've been searching for this for over a year and I'm posting it to save other people from gray or torn hair. I assume no responsibility for how you use this or for any damage this might do to your registry.

For this you will need the utility chntpw which is available from the repositories. More info on chntpw can be found at [http://home.eunet.no/pnordahl/ntpasswd/]("http://home.eunet.no/pnordahl/ntpasswd/")

chntpw is normally interactive but you can echo a string of commands to it. The following example shows which programs will run at login:
```

echo -e "cd Software\\Microsoft\\Windows\\CurrentVersion\\Run\nls\nq\n" | chntpw NTUSER.DAT

```

This will output the following:
```

chntpw version 0.99.3 040818, (c) Petter N Hagen
Hive's name (from header): <###REMOVED###\ntuser.dat>
ROOT KEY at offset: 0x001020 * Subkey indexing type is: 666c <lf>

File size 2007040 [1ea000] bytes, containing 292 pages (+ 1 headerpage)
Used for data: 19230/1975624 blocks/bytes, unused: 674/17976 blocks/bytes.
Simple registry editor. ? for help.

[1020] >
[1aabc8] (...)\Microsoft\Windows\CurrentVersion\Run> ls of node at offset 0x1aabcc
Node has 0 subkeys and 1 values
offs        size      type   value name                    [value if type DWORD]
[1aa5dc]     62  REG_SZ            <CTFMON.EXE>

[1aabc8] (...)\Microsoft\Windows\CurrentVersion\Run>
Hives that have changed:
 #  Name
None!

```

Let's break it down:
[LIST=1]
[*]**echo -e** tells echo to enable backslash commands. This makes it possible to send line breaks, \n
[*]**cd Software\\...\n** is the first command and tells chntpw to "change directory" (Move in the hive) to the key Run. Note the double backslashes which are required because echo now interprets them as special characters (See man echo). Also note the line break, \n, at the end. For some reason I had to break up some longer cd statements into two. Test your code before editing important stuff.
[*]**ls\n** lists the contents of the key.
[*]**q\n** exits chntpw
[*]**| chntpw** pipes the command string to chntpw
[*]**NTUSER.DAT** is the XP user registry file to work on. Usually located in your profile share on a domain or in C:\Documents and Settings\USERNAME on a local computer.
[/LIST]

You can also edit a value with "ed valuename\n". Enter the new value, "new value\n" and exit, "q\n". chntpw will ask if you want to save changes so a "y\n" needs to be written to.

The following code will change the value ctfmon.exe to c:\windows\foo.exe. JUST AN EXAMPLE, DO NOT RUN THIS!
```

echo -e "cd Software\\Microsoft\\Windows\\CurrentVersion\\Run\ned CTFMON.EXE\nc:\windows\foo.exe\nq\ny\n" | chntpw NTUSER.DAT

```

See the chntpw help for more commands.

This can easily be scripted in bash, PHP or whatever you prefer. Hope this makes your day as it did mine!

Wileur

---

### Post by jpeddicord on 2009-05-11
Approved. Thank you for your tutorial contribution, and sorry for the delay. :)

---

