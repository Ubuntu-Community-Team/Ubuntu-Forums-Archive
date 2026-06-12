---
title: "Java - Get current cursor style"
date: 2011-01-07
forum: Programming Talk
---

### Post by PaulM1985 on 2011-01-07
Hi

I am working on a Java program which is designed to show the screen of another computer.  I am able to get a screen shot using the java.awt.Robot class, but I am wondering how I get the cursor to be displayed.

As an alternative, if I could get the cursor style on the other computer, I could set this to be the cursor style on the client.

Any ideas?

Paul

---

### Post by t1497f35 on 2011-01-07
> **PaulM1985 said:**
> Hi

I am working on a Java program which is designed to show the screen of another computer.  I am able to get a screen shot using the java.awt.Robot class, but I am wondering how I get the cursor to be displayed.

As an alternative, if I could get the cursor style on the other computer, I could set this to be the cursor style on the client.

Any ideas?

Paul
It's unclear to me whether you want the user to interact with the cursor or just get the cursor to be painted upon the screenshot, or set user's cursor and move it according to the cursor from the remote computer. or something else..
Anyway, you have to tools to get the cursor type:
java.awt.Cursor.getType()
and to get its coords relative to the screen:
java.awt.MouseInfo.getPointerInfo().getLocation()
That would be enough for me to work my way out.

---

### Post by PaulM1985 on 2011-01-07
The user on the client machine can control the mouse of the other computer.  I can replicate the moves by sending the scaled mouse positions on the panel of the client to the other computer and using the Robot to move the mouse.  However, the mouse may not be over a Java component on the other computer, for example it could be over a web link in a web browser and so give it a different cursor type.  Is there any way I can get this image?

Also, getType() returns the type for "this" cursor.  How do I get "this" cursor from the client machine?

Paul

---

### Post by t1497f35 on 2011-01-07
You can't use a lowest common denominator solution like Java for such a task without using platform specific code, by which I mean - it's doable, but it doesn't yield you the flexibility you're asking for - for instance you can't get the cursor type outside the JFrame (you can only get the cursor location) without workaround/platform specific code but, as a (lame/stopgap) solution, you can keep always drawing a "default" cursor instead if the user is OK with that.

---

