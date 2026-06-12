---
title: "programming editor for PHP?"
date: 2012-05-02
forum: Programming Talk
---

### Post by anon0 on 2012-05-02
Hi all, can anyone recommend a good editor for writing PHP code? I work from a Windows machine and save the file to the Ubuntu server.

---

### Post by codemaniac on 2012-05-03
There is no need to code the php script in windows and push it into your ubuntu server .Instead all you can do is just ssh to your Ubuntu server and script there in vim .Still if you wan to code in windows environment i can suggest you **notepad++** .

---

### Post by trivialpackets on 2012-05-03
Agreed, ssh to server and vim works well, but if you want to try it, I'm also quite partial to sublime text 2, as it's cross platform and I just love the environment.

---

### Post by anon0 on 2012-05-03
> **codemaniac said:**
> There is no need to code the php script in windows and push it into your ubuntu server .Instead all you can do is just ssh to your Ubuntu server and script there in vim .Still if you wan to code in windows environment i can suggest you **notepad++** .

Thanks. I see that vim isn't able to collapse functions like notepad++ can, unless I'm missing it in vim.

---

### Post by cgroza on 2012-05-03
> **anon0 said:**
> Thanks. I see that vim isn't able to collapse functions like notepad++ can, unless I'm missing it in vim.
Pretty sure it can, it may need to be set up though. Look for a plugin someplace. Have you considered editing your files over ftp? I remember doing this once.

---

### Post by anon0 on 2012-05-03
> **cgroza said:**
> Pretty sure it can, it may need to be set up though. Look for a plugin someplace. Have you considered editing your files over ftp? I remember doing this once.

Thanks. For now, I've enabled Samba share on the directory so I can just open it with any Windows editor, work with it and save as needed. Pretty simple for my needs.

---

### Post by LemursDontExist on 2012-05-03
You might check out [Bluefish]("http://bluefish.openoffice.nl/index.html").  For web development it's pretty good.

---

### Post by rg4w on 2012-05-03
+1 for Bluefish.  I started using it a few weeks ago based on the recommendations from so many in this forum, and so far it seems a very competent tool.

---

### Post by codemaniac on 2012-05-04
> **anon0 said:**
> Thanks. I see that vim isn't able to collapse functions like notepad++ can, unless I'm missing it in vim.

The functionality you're referring to is called "folding" (see :help usr_28).

[http://vim.wikia.com/wiki/Folding](http://vim.wikia.com/wiki/Folding)

---

