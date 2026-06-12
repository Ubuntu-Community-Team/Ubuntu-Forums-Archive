---
title: "how to open a file using terminal?"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by chahat on 2012-05-25
I want to open the following file-

/var/lib/NetworkManager/NetworkManager.state

How do i do that? When i typed this in the dash home,it gave no results?
Can i use terminal for this purpose?
I use 12.04.

---

### Post by SPK201 on 2012-05-25
Either use nano, a terminal editor:

```
sudo nano /var/lib/NetworkManager/NetworkManager.state
```or

```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by lisati on 2012-05-25
Using the terminal (a.k.a. "command line") to "open" a file usually requires you to know which program you want to use to process the file.

If you want to display the contents of a file using the terminal, you can do something like this:
```
sudo cat /var/lib/NetworkManager/NetworkManager.state
```
If it's a big file, you can do this:
```
sudo cat /var/lib/NetworkManager/NetworkManager.state | less
```

Edit: SPK201's way should work too.

---

### Post by Lord Burghley on 2012-05-25
> **chahat said:**
> I want to open the following file-

/var/lib/NetworkManager/NetworkManager.state

How do i do that? When i typed this in the dash home,it gave no results?
Can i use terminal for this purpose?
I use 12.04.

Certainly. Open your terminal, copy and paste the following...

```
cd /var/lib/NetworkManager
```

This will move you to the NetworkManager directory. Now enter...

```
less NetworkManager.state
```

This will open the file and let you view it. Hope this helps. :) Remember to be careful when you're working in the terminal if you're unfamiliar with it!

---

