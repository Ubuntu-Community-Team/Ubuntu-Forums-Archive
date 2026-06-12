---
title: "PHP5 and music playback"
date: 2006-01-23
forum: Programming Talk
---

### Post by matid on 2006-01-23
Hi, can anyone help me enabling php to play music on the server?
I tried:
```
<?php
system( '/usr/bin/play file.mp3' );
?>
```
But it doesn't work. It just displays nothing.
On the other hand, when I run this file with php cli it's playing ok.
I think it's all about permissions, but I added www-data to audio group and it's still not working.

Do you have any ideas?

---

### Post by rock freak on 2006-01-23
no idea if this will help but make sure it has read and excecute permissions i do belvie that if you got chmod 755 then the file name will set it so everyone and read and esxcute it but only the file owner can write to it. 

hope this helps not sure if it will

---

