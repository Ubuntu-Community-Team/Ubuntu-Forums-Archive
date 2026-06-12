---
title: "Help Spotify does not work"
date: 2017-11-27
forum: New to Ubuntu
---

### Post by mthstvrs on 2017-11-27
Hello,

I just recently bought a computer and I'm a new Ubuntu 16.04 user.
I was installing all my programs and Spotify does not open. It is installed. The icon is there. However, when I click on it, it just keeps blinking and then disappears.
It does not open, I've searched eveywhere, don't know what to to.
Any help would be my appreciated

Thanks.

---

### Post by Perfect Storm on 2017-11-27
Try run it through the terminal, it may give a clue:

```
spotify
```

Or 
```
spotify --show-console
```

will give more output.

---

### Post by mthstvrs on 2017-11-27
it does not work
I tried figuring out how to insert print screen of the image here - don't know how
ubuntu is very hard

---

### Post by howefield on 2017-11-27
> **mthstvrs said:**
> it does not work
I tried figuring out how to insert print screen of the image here - don't know how
ubuntu is very hard

If it is an image of terminal output, then select the text in the terminal and copy/paste it back here between [noparse]```

```[/noparse] tags.

---

### Post by monkeybrain20122 on 2017-11-28
How did you install it? Works here.

---

### Post by littlefoot505 on 2017-12-01
You may want to try uninstalling Spotify and then reinstalling it.

---

### Post by shintaomonk on 2017-12-07
```
sudo apt remove spotify && apt install spotify
```

---

### Post by cariboo on 2017-12-07
> **shintaomonk said:**
> ```
sudo apt remove spotify && apt install spotify
```

sudo apt remove only removes the packages. To completely remove a package and it's configuration files use:

```
sudo apt purge <package_name>
```

---

