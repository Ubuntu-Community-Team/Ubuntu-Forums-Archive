---
title: "Keeps asking for the password"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by tehforum on 2008-06-19
Hello, I am new here. (Ubuntu 7.10 Gutsy Gibbon)

I have gone through the laborious process of installing *finally* installing Unrar, after having to find the repo in the Tools > Administration > Software Resources.

Now, I followed all the commands, and it's installed.

Now it says to do 

```

unrar e filename.rar

```

That doesn't work, just say No file found etc

So, I found another thread on this forum [here]("http://ubuntuforums.org/showthread.php?t=271867"), and at the last post, it says to right on the file, and press Extract here.

I did so, and I thought everything was all dandy, when it accepted my password (to confirm the operation), but then it keeps going on a loop.

Accept password, extract files, the extracted folder automatically deletes, and it happens again, and again.

I was hoping if you could shed some light here.

Thank you, Ubuntu community.

---

### Post by nothingspecial on 2008-06-20
You only have to do it once. Have a look in the folder you are extracting the files to and they should be sitting right there.

---

### Post by alexandremrj on 2008-06-20
Hello,

when you select the extract here menu it should never ask you the admin password. What it may ask is the rar password, that means that someone password-protected that rar file. If that happens it will try to extract and then ask the password and if that password is wrong then it will delete what he already extracted and try again (asking the password - the file one, not your system password).

---

