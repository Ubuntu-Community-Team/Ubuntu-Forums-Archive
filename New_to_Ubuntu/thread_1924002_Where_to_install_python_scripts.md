---
title: "Where to install python scripts?"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by arfdah on 2012-02-11
Where is the default place to save py scripts? I get a no file or directory error. Thank you.

Edit: Er, not install them, save them. Hurr

---

### Post by mcduck on 2012-02-11
> **arfdah said:**
> Where is the default place to save py scripts? I get a no file or directory error. Thank you.

Edit: Er, not install them, save them. Hurr

Where ever you want.

Depends on what the scripts are for, who do you wan to be able to access them and what you want to do with them.

What comes to the error, I assume that's when you are trying to execute one of the scripts? In that case make sure you've set the execute permission on the file, and are either running it from the same directory where the file is located, or are using the full path to the file.

---

### Post by cortman on 2012-02-11
If you want to be able to access them from anywhere in the shell, save them in /bin, where all the shell commands are stored.

---

### Post by savanna on 2012-02-11
If they're just for you, make a ~/bin directory and put them there (you may need to update your $PATH in ~/.bashrc).

---

### Post by markbl on 2012-02-12
> **savanna said:**
> If they're just for you, make a ~/bin directory and put them there (you may need to update your $PATH in ~/.bashrc).
This is the conventional approach for home made scripts etc.

---

### Post by mcduck on 2012-02-12
> **savanna said:**
> If they're just for you, make a ~/bin directory and put them there (you may need to update your $PATH in ~/.bashrc).

~/bin is automatically included in user's path if it exists. So you only need to log out and back again after creating the directory and it will work.

---

