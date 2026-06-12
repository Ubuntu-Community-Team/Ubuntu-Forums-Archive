---
title: "Why does vi say vim?"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by DarrenVortex on 2013-03-30
Hello,
So I just installed Ubuntu and i wanted to see if it already has VIM installed, so I ran vim and nothing happened. Then accidentally ran vi and was shocked when I saw the vim welcome screen in front of me. However, once I started using it, I figured that it was actually "vi" not "vim", due to arrow keys not being usable as expected in a regular text editor.
So I installed the actual VIM and I use it now and it's cool and all. No problem was really encountered here. However, I really wonder why "vi" still says "vim" at the welcome screen when it starts out. That was really misleading. If it had said "vi" instead of "vim" in the beginning, I wouldn't have to waste a precious 30 second to figure out that it wasn't really vim. Why is that?

---

### Post by mharv on 2013-03-30
Why would you want vim instead of vi anyways?

---

### Post by DarrenVortex on 2013-03-30
I don't. I was just wondering why "vi" says "vim" instead in the welcome screen.

---

### Post by bab1 on 2013-03-30
The default Ubuntu install comes with vim-tiny which is essentially vi.  You need to install vim to get all of the useful vim enhancements.

---

### Post by PaulW2U on 2013-03-30
The following output shows that vi is a symlink which points to whatever version of vim is installed.

```

paul@G620:~$ which vi
/usr/bin/vi
paul@G620:~$ vdir /usr/bin/vi
lrwxrwxrwx 1 root root 20 Mar 24 13:00 /usr/bin/vi -> /etc/alternatives/vi*
paul@G620:~$ vdir /etc/alternatives/vi
lrwxrwxrwx 1 root root 16 Mar 24 13:18 /etc/alternatives/vi -> /usr/bin/vim.gtk*

```

---

