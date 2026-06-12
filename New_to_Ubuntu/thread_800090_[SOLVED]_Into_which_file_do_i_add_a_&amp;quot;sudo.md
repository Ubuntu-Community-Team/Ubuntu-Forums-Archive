---
title: "[SOLVED] Into which file do i add a &amp;quot;sudo foo&amp;quot; command that I want to run every time"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by hanzj on 2008-05-19
Hello,
I want a sudo foo command [specifically, "sudo modprobe visor", which is for my old Palm OS pda] to run every time I log onto my computer.

I cannot simply add it to the "Sessions Preferences"/Startup Programs, because only non-sudo commands will work there.

Which file must I add sudo commands to?


Thanks.
[P.S. I've never been thanked here on this forums. Could someone thank me, for the fun of it? 8-)]

---

### Post by Majorix on 2008-05-19
/etc/rc.local

I don't think you need to add sudo infront, all of the commands in there already are launched in superuser mode.

---

### Post by hanzj on 2008-05-19
Should I have "exit 0" kept as the last line in that rc.local file?

[P.S. Wow. Someone actually thanked me! Thank you, N.N., for thanking me! 8-)]

---

### Post by Majorix on 2008-05-19
Nope it wasn't me who thanked you hehe.

And I am not sure about the "exit 0" line. It won't hurt the process, so you can keep it. Removing it *could* cause problems, so choose the safe way ;)

---

### Post by hanzj on 2008-05-19
Okay. I'll keep "exit 0". Does it matter whether "exit 0" is the last line in the file?

---

### Post by Majorix on 2008-05-19
That exit 0 command is most likely to notify the interpreter to exit the program, so make sure all your commands you add to be above that line.

---

### Post by hanzj on 2008-05-19
Case Solved!
Thanks to Majorix and N.N.
8-)

---

