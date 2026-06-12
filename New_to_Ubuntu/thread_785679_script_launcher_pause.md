---
title: "script launcher pause"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by alphaniner on 2008-05-07
Is there a command to put a 'pause' in a script?  I have a few scripts that just print something on the screen ie: ```
cat /proc/scsi/scsi
```
I made a launcher (type: application in terminal) on the desktop.  Of course when I run the launcher, a terminal window pops up and then disappears straightaway.  So what I need is a way to pause things until I press a key or something.  Is this possible?  Thanks.

---

### Post by spiderbatdad on 2008-05-07
i believe the 'read' command will cause the script to wait for input:
```
cat /proc/scsi/scsi
read
```
Then enter key will exit.

---

### Post by alphaniner on 2008-05-07
Nope, that didn't do it.  Still flashed in and out.  And I typed the script into the terminal, I got
```
Attached devices:
Host: scsi1 Channel: 00 Id: 02 Lun: 00
  Vendor: IBM      Model: ULTRIUM-TD1      Rev: 36U3
  Type:   Sequential-Access                ANSI  SCSI revision: 03
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: HDS724040KLSA80  Rev: KFAO
  Type:   Direct-Access                    ANSI  SCSI revision: 05
read: 3: arg count

```

---

### Post by Monicker on 2008-05-07
How about

```
cat /proc/scsi/scsi && read a
```

---

### Post by alphaniner on 2008-05-07
Woot! That worked.  Any chance you can give me a brief explanation why?  Or maybe a link?  Thanks.

---

### Post by Monicker on 2008-05-07
The read command is used to pass user input to the shell, but it requires an argument so that it knows to which variable it should assign the input.  You got the error previously because no variable name was given.  Basically the "read a" is waiting for you to enter something to be assigned to the variable "a".  Once you hit enter it has what it wants.  Since no more processing is actually being done, it just exits afterwards.

---

### Post by spiderbatdad on 2008-05-07
> **Monicker said:**
> The read command is used to pass user input to the shell, but it requires an argument so that it knows to which variable it should assign the input.  You got the error previously because no variable name was given.  Basically the "read a" is waiting for you to enter something to be assigned to the variable "a".  Once you hit enter it has what it wants.  Since no more processing is actually being done, it just exits afterwards.

Works fine for me as I posted it. No arg required. Shell waits for return key. Maybe because launcher forks the process of op?

---

### Post by Monicker on 2008-05-07
> **spiderbatdad said:**
> Works fine for me as I posted it. No arg required. Shell waits for return key. Maybe because launcher forks the process of op?

Could be.  I saw the same behavior as him when I launched via gui.  Now that I try it via terminal session, just "read" is sufficient.

---

