---
title: "How to claim owner?"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by zman7411 on 2011-12-28
I was wondering how would you claim owner on Ubuntu 11.10 because it will not let me modify any of my files or access any of my files. And it won't let me change permissions because it says I am not the owner. What can you do?

---

### Post by CharlesA on 2011-12-28
What files are you trying to change?

If they are outside your home directory, you'd need to use sudo to modify them, but chances are that they are fine as they are.

---

### Post by zman7411 on 2011-12-28
Accually I am trying to replace a file, not modify, sorry for the confusion.

---

### Post by CharlesA on 2011-12-28
Which file?

---

### Post by The Cog on 2011-12-28
> **CharlesA said:**
> Which file?

This is important. You should not be taking ownership of files outside of your home directory. This can break the system so badly that you need to reinstall before you can log in again.

You can use sudo to edit files outside of your home when you are doing system maintenance. See
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zman7411 on 2011-12-28
> **CharlesA said:**
> Which file? 
It was a batch file from a video game I downloaded off of the internet.

---

### Post by CharlesA on 2011-12-28
> **zman7411 said:**
> It was a batch file from a video game I downloaded off of the internet.
You are going to have to be more specific than that.

Which game?
What is the name of the file?
Where are you trying to put it?

---

