---
title: "gambas error message with feisty fawn"
date: 2007-04-10
forum: Programming Talk
---

### Post by flulu on 2007-04-10
hello
i try to use gambas under feisty fawn and i receive error message :
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: #2: Cannot load class 'win1': Unable to load class file


anybody can help me ?

---

### Post by niijel on 2007-05-08
I hate to leave a good question unanswered, because others with the same problem will no doubt use a search engine to find it, then be disapointed :( 

I get the two X errors but they dont do any harm

Most common reason for the error 2 is that you are running an example and the example folder and its contents are read only. (/usr/share/gambas/examples)

I guess that having paths and permissions wrong will generate this also.

Anyone with specific info please add to thread :)

---

### Post by heen on 2007-05-29
As suggested by niijel 

```
sudo chmod -R o+w /usr/share/gambas/examples
```

solves problem.

---

### Post by msumurph on 2007-05-29
> **flulu said:**
> hello
i try to use gambas under feisty fawn and i receive error message :
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: #2: Cannot load class 'win1': Unable to load class file


anybody can help me ?

Actually, it seems that this is a KDE error message, not specific to Gambas.  A search for *[COLOR="Green"]BadDevice, invalid or uninitialized input device[/COLOR]* in the forums shows that this is a common problem with other applications as well.

This thread: [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=376313[/COLOR]]("http://ubuntuforums.org/showthread.php?t=376313") gives an explanation.  Personally, I use Gambas often and just ignore the message.  It does not effect my programs.

Take care!

---

