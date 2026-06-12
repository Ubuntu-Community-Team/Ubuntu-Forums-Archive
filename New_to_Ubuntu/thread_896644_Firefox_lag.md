---
title: "Firefox lag"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by pzs on 2008-08-21
I'm running Firefox 3.0.1 on Hardy. I find that after a day of use, Firefox starts acquires painful lag. I type in the search box and the letters take several seconds to appear. Opening a new window just took about 10 seconds and this window was locked out while I was doing it.

This is particularly galling because this is a quad core Xeon machine with 8GB of memory connected to a University connection. It should be *fast*. 

Restarting or killing Firefox -9 doesn't help. Neither does logging out and logging back in. A machine restart may help but... seriously. A restart should not be necessary to get Firefox to work.

---

### Post by Het Irv on 2008-08-21
Perhaps Firefox was corrupted on the install?

If you go into your /home folder and make a backup of your .mozilla folder, you can safely reinstall firefox without loseing your add-ons or bookmarks, just remember to replace the .mozilla folder after reinstalling.

---

### Post by pzs on 2008-09-24
I tried a reinstall, which made no difference. However, it got a lot worse with the latest update.

I finally fixed the problem by deleting my whole .mozilla directory and reimporting my bookmarks. I've lost some of my saved passwords and so on, but at least now it doesn't take a minute to redraw the window...

---

### Post by billgoldberg on 2008-09-24
> **pzs said:**
> I tried a reinstall, which made no difference. However, it got a lot worse with the latest update.

I finally fixed the problem by deleting my whole .mozilla directory and reimporting my bookmarks. I've lost some of my saved passwords and so on, but at least now it doesn't take a minute to redraw the window...

I find that firefox is quite laggy when I haven't installed my graphics card driver.

Is your installed? Maybe try the newest version using Envy or something.

Or try another browser.

Chromium is available for linux (runs an some sort of Wine version, I think Codeweaver, could be wrong).

Then there is Epiphany (the official gnome browser). That one has a plugins package in the repos with adblocker and some other add ons.

You could also use Opera (closed source!).

Opera and Chromium don't have ad blocker, but a good /etc/hosts list is just as good.

---

### Post by reginak on 2008-09-24
Absolute Beginner here....

With the latest update I lost google and I also can't get anywhere using the address box. Apparently my bookmarks still work, since I was able to get here. When I try to type in the google box, I get this:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:(ja,searchbar-history,null,[xpconnect wrapped nsIAutoCompleteObserver])

So I thought, I'll do what you suggested, backup my .mozilla folder and re-install. But I can't find a .mozilla folder in my home folder! Throughout my file system there are 8 or 9 folders called "mozilla" or "Mozilla" or "Mozilla Firefox". Should I back up the one under users>*username*>appdata>local ?

Thanks so much

---

### Post by pzs on 2008-09-25
To see your .mozilla files, do View->Show hidden files (or Ctrl-H). That should show you all the files and directories that start with a "." so you can make a backup.

---

### Post by reginak on 2008-09-25
Oh! Aha! Thank you!

(told you I was an Absolute Beginner! LOL)

---

