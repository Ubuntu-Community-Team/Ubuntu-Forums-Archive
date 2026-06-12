---
title: "Broken Pipe message?"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by NotSure23 on 2012-10-01
Is this an issue?  This message has been appearing when my comp is shutting down. Computer seems to run great though. Sorry for blurry image. 

[[IMG]http://imageshack.us/a/img846/857/img20121001192053.jpg[/IMG]]("http://imageshack.us/photo/my-images/846/img20121001192053.jpg/")

---

### Post by Wim Sturkenboom on 2012-10-02
Not an issue. This happens when a server-type application goes down and a connected client is (still) trying to communicate.

It probably happens because the graphical environment (X) is stopped.

---

### Post by NotSure23 on 2012-10-02
ok cool thanks

---

### Post by moodle on 2012-10-10
> **Wim Sturkenboom said:**
> Not an issue. This happens when a server-type application goes down and a connected client is (still) trying to communicate.

It probably happens because the graphical environment (X) is stopped.

This is a HUGE issue for me, as it happens when my computer is starting up. What can I do about it?

---

### Post by MG&amp;TL on 2012-10-10
> **moodle said:**
> This is a HUGE issue for me, as it happens when my computer is starting up. What can I do about it?

Does anything not work as it should?

---

### Post by GeForce 9500GT on 2012-10-10
I came across this solution on the Linux Mint forum which appaerantly works:

[LIST=1]
[*]Boot into recovery mode
[*]Repair broken packages
[*]Hit the continue boot button
[*]Log in to the desktop
[*]Reboot
[*]Log in normally
[/LIST]The topic title is:
> could not write bytes: Broken pipe <-- message at shutdown

---

