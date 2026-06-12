---
title: "Unzip a .zip from downloads"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by shmparvez on 2012-03-29
I have another ubuntu dual boot on my laptop that is working. I transferred a .zip file that I created via email onto ubuntu. i downloaded it in downloads folder from firefox.

Now if I try to unzip it uby double clicking it, it throws error access denied.
If i try to unzip it by copy pasting some commands I found again it says access denied or folder does not exist etc.
Also when I ls, i see downloads folder. But I am not able to navigate into it using terminal.
THis is driving me crazy.
Can anyone help?

---

### Post by skatinjj on 2012-03-29
Access denied seems a little odd since it is in the Downloads folder in your home directory (I assume) never the less you can do try this:

```
sudo chown <name of file> <username>
```

---

### Post by oldos2er on 2012-03-29
> **shmparvez said:**
>  I am not able to navigate into it using terminal.

Linux is case-sensitive, so to change directory to your downloads folder in a terminal, enter ```
cd ~/Downloads
```

---

### Post by shmparvez on 2012-03-29
Wow that was the problem. This forum rocks. I did not realize that ubuntu is case sensitive.

---

