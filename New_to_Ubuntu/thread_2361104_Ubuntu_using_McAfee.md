---
title: "Ubuntu using McAfee"
date: 2017-05-12
forum: New to Ubuntu
---

### Post by pkxlive on 2017-05-12
I am using McAfee on my Ubuntu machine to test for future roll out. I need help to locate where the DAT. file data is located to have that query for version and build. The command (/opt/NAI/LinuxShield/engine/dat) has the DAT files. It does not display in clear text. The command Verify current DAT version: (/opt/NAI/LinuxShield/bin/nails --version). How can I get this data read without running this command? This query will happen over multiple endpoints at every 6 hours.

---

### Post by TheFu on 2017-05-12
Welcome to the forums.

I'd use 'find' or 'locate' to find or locate files on a machine.
[https://www.tecmint.com/35-practical-examples-of-linux-find-command/](https://www.tecmint.com/35-practical-examples-of-linux-find-command/) has some 'find' examples. Don't forget to review the manpage. All is revealed inside manpages.  If you are responsible for admin or automation of Unix/Linux systems, then you'll need to get used to those.

Locate pre-builds an index, but is limited to 1 trick - finding files that were on the machine when the index was created.  Don't remember how often that happens, daily or weekly.  It is configurable. /etc/updatedb.conf (I think).

If you want to update more than a few systems every few hours, I'd use a devops tool.  That is what those things are designed to handle. They are all free (F/LOSS, not freeware) and most places only use the F/LOSS versions.

I don't know anyone using McAfee on Linux.  That "verify" command might not be just reading a file.  It is a command. You might be able to simplify what it does, but I wouldn't bother.  Running the same command on 1 or 50,000 systems isn't a big deal.  Just setup ssh with key-based authentication.  That's the 1st step in almost all Linux admin process - ssh.

Based on the question, I'm guessing you are new to Linux scripting?

Thanks lisati for fixing the font.

---

### Post by SeijiSensei on 2017-05-13
> **pkxlive said:**
> It does not display in clear text.
Of course it doesn't display in clear text.  First, the file is more compact as a binary and, more importantly from McAfee's point-of-view, having it be a binary lets them keep their virus definitions and methods a secret from their competition.  I can't imagine any method where you can peruse the DAT files in clear text.

---

### Post by milkness on 2017-05-13
LibreOffice can sometimes piece together characters believe it or not in DAT files, has helped me a lot. - Just putting it out there.

---

### Post by lisati on 2017-05-13
I'd be inclined to use the "locate" command, as has already been suggested, if I'm trying to locate a particular file. 

On the other hand, if I'm curious about the contents of a binary file, depending on what I'm doing at the time, the ["strings" command]("http://www.tutorialspoint.com/unix_commands/strings.htm") is sometimes of help.

---

