---
title: "Ubuntu is giving me a pop up but can´t read it"
date: 2022-09-09
forum: New to Ubuntu
---

### Post by nicksboson on 2022-09-09
Hi all,

I'm new to this forum. I'm using Ubuntu for Special FX and CGI Software.

When I start Ubuntu I get a message but I can´t read the full message. And when I click it it dissapears.
Hot te read and fix it?
(see attachment)[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291015&stc=1[/IMG]

---

### Post by ajgreeny on 2022-09-09
Open up /var/log/syslog in your text-editor, (probably gedit if using Ubuntu) and search for the phrase "not running on one of the" and "this configuration is currently unsupported".
Ctrl+F is usually the keyboard keys needed for find in text.

Once found, assuming it is, look at the lines surrounding those phrases and you may get some more clues to what is going on and the full text of any error may point in the right direction..

Does the system still boot and run properly?

---

### Post by nicksboson on 2022-09-12
Found it, thanks!

---

### Post by ajgreeny on 2022-09-12
> **nicksboson said:**
> Found it, thanks!

Good to know, but what did it tell you and was it helpful?

---

### Post by mIk3_08 on 2022-09-12
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

