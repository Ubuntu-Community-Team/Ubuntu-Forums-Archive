---
title: "[SOLVED] gksu kills my theme"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2008-05-12
I was just wondering... Since i installed hardy (fresh install) when i open a program (with GUI) and using gksu (like sysnaptic, gdm manager, clamav front end, nautilus, etc) they all lose the my current system theme and use some ugly aMSN like theme. Im not in my home so i will post some screens later.

This is something known? Bug? its doesn't botter me that much, but i was just wondering why...


thx in advance for the answers ^^

---

### Post by PeterJS on 2008-05-12
Presumably the theme you're running is stored in /home/user/.themes, making them available only to your account. While the applications have permission to read /home/user/.themes they have no reason to look there for themes (because they aren't running as your user, so /home/user/ isn't their home directory), instead they will look in /root/.themes and /usr/share/themes. So your choices are: install the theme system wide by moving it to /usr/share/themes, or symlink your personal theme directory to the root account's personal theme directory with:
```

sudo ln -s ~/.themes/ /root/.themes

```

---

### Post by Ryuki_NdranC on 2008-05-12
> **PeterJS said:**
> Presumably the theme you're running is stored in /home/user/.themes, making them available only to your account. While the applications have permission to read /home/user/.themes they have no reason to look there for themes (because they aren't running as your user, so /home/user/ isn't their home directory), instead they will look in /root/.themes and /usr/share/themes. So your choices are: install the theme system wide by moving it to /usr/share/themes, or symlink your personal theme directory to the root account's personal theme directory with:
```

sudo ln -s ~/.themes/ /root/.themes

```

Hmmm i figured that much :). But i never worked with symlinks before. I gonna look it to them when i get home, but in your opinion what should be the more appropriate solution? im thinking maybe just copy my theme directory? I think i reed somewhere that symlinks may cause problems with unexpected behavior. 

Is that true?

BTW thx for the fast answer :)

---

### Post by PeterJS on 2008-05-12
> **Ryuki_NdranC said:**
> Hmmm i figured that much :). But i never worked with symlinks before. I gonna look it to them when i get home, but in your opinion what should be the more appropriate solution? im thinking maybe just copy my theme directory? I think i reed somewhere that symlinks may cause problems with unexpected behavior. 

Is that true?

BTW thx for the fast answer :)

Symlinks between partitions can get a bit funky if one end of the link is mounted but the other end isn't. But if you stay within a partition the symlink will behave just like it is the target file/directory.

I've got mine set up with symlinks, if you only have one administrative account on the machine that should be fine, a little sloppy but won't cause any problems. If you have multiple administrative accounts, it would probably be worth moving the themes to /usr/share/themes/.

---

### Post by Ryuki_NdranC on 2008-05-12
Then I'm gonna move it. I just have one administrative account, but it fells more right if i just move it. Anyway thanks a lot for your answers, it help a lot in my ultimate goal of learning all i can about how linux does what it does :)

---

