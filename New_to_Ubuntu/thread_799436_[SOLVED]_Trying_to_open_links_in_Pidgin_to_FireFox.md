---
title: "[SOLVED] Trying to open links in Pidgin to FireFox"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-05-19
I have Firefox and Pidgin installed, but when someone sends me a link in pidgin I can't click on it and open it in Firefox. This is what my preferred applications menu looks like, use to have Firefox listed, but no more.

---

### Post by sdennie on 2008-05-19
I'm not sure why firefox isn't showing in preferred applications but, you can just add a custom command that is:

```

firefox "%s"

```

Or, to open it in a new firefox tab:

```

firefox -new-tab "%s"

```

---

### Post by ImThatNerd on 2008-05-19
I put those commands in terminal and this is what I got:

```
ryan@ryan-desktop:~$ firefox -new-tab "%s"
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
ryan@ryan-desktop:~$ 

```

I have 8.04. I got rid of 3.0 since it was horrible and reinstalled firefox 2.

---

### Post by sdennie on 2008-05-19
In that case, I think just replace "firefox" with "firefox-2".

---

### Post by Deeta on 2008-05-19
@deinstalled FF3: Ahh yeah that makes then. Firefox 2 has a different command in 8.04 than in 7.10 and earlier.

Thus if you type 'firefox' ubuntu thinks you want to run Firefox3.

If you follow Vor's instructions and use (I think it was firefox-2 or firefox2) instead of 'firefox' it should work.

---

### Post by ImThatNerd on 2008-05-21
Alright well when I put firefox-2 and click a link in pidgin firefox opens with my homepage, which is google.com. It does not take me to the link that was listed on pidgin.

---

### Post by sdennie on 2008-05-21
It sounds like you forgot the "%s" in the custom browser command.

---

### Post by ImThatNerd on 2008-05-21
> **vor said:**
> It sounds like you forgot the "%s" in the custom browser command.

Gee that fixed it. :p thanks.

---

