---
title: "Issues passing escape signals in expect"
date: 2012-04-05
forum: Programming Talk
---

### Post by floobit on 2012-04-05
I'm trying to navigate an ncurses-based text interface using expect.  I need to send escape sequences in order to do so.  I'm having trouble doing so.  I want to send an <F4> signal, which in xterm is <esc>[OS.  I have used od -c to verify this, and sure enough, if I type <ctrl>[ then O, then S from within the interface, I get the desired behavior.  Documentation I've read says that I can use send "\cX" to send the <ctrl>-X signal.  I've used this in the sample below:

```

#!/usr/bin/expect
spawn interface.ui
set timeout -1
expect "Welcome"
send "user\r"
set timeout -1
expect "user"
send "password\r"
set timeout -1
expect "Main Menu"
send "\c[OS"

```

Upon execution of this script, after the escape code is sent, all the characters are garbled when printed onto the screen:


&#9149;&#9149;&#9227;&#9532;± &#9228;&#9484;&#9146;&#9149;&#9226;-&#9225;&#9148;&#9618;&#9228;&#9488;&#9226;&#9500;
    &#9516;&#9252;&#9227;&#9484;&#9226; &#9226;&#9474;&#9226;&#9228;&#9508;&#9500;&#9227;&#9532;±
"&#9149;&#9226;&#9532;&#9229; "\&#9228;[OS"
&#9149;&#9226;&#9500; &#9500;&#9227;&#9492;&#9226;&#9146;&#9508;&#9500; -1
&#9226;&#9474;&#9147;&#9226;&#9228;&#9500; "M&#9618;&#9227;&#9532; M&#9226;&#9532;&#9508;"
&#9149;&#9226;&#9532;&#9229; "&#8804;\&#9148;"


&#9227;&#9532;&#9500;&#9226;&#9148;&#9618;&#9228;&#9500;

"
    (°&#9227;&#9484;&#9226; "./&#9500;&#9226;&#9149;&#9500;.&#9226;&#9474;" &#9484;&#9227;&#9532;&#9226; 25)
&#9229;&#9226;&#9524;2:[·/&#9225;&#9227;&#9532;]$


Thoughts?  I tried to write an expect sequence to write characters into od -c (to test whether the correct sequence is being sent), but expect won't write anything to the od -c line.

---

