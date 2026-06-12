---
title: "[hardy] And the best Javascript editor is..."
date: 2008-07-20
forum: Programming Talk
---

### Post by iamah on 2008-07-20
UPDATE: Geany is the one I'm using now, function browser seems to work fine.

Wine & Notepad++ 3.9 !!! :guitar:

[http://sourceforge.net/project/showfiles.php?group_id=95717&package_id=102072](http://sourceforge.net/project/showfiles.php?group_id=95717&package_id=102072)

Seriously, I've been looking for a decent Javascript editor for ages, with function navigation and usable auto-complete.

Javascript function navigation seems to be completely ignored in Linux, I even tried once to do one for Gedit, but I couldnd't.

Notepad++ 3.9 installs smoothly via Wine in Ubuntu Hardy(I've unchecked the %APP...% option)... new version 5.0 gave me an error, something about the planets not being aligned... 

Anyway, this is the best editor I've found for Javascript and possible some other languages... Just remember to activate plugin -> function list, and right click there to sort by name, or whatever...

Hope this is useful for someone who have similar problem...

cheers:KS


PS: For Greasemonkey development in Firefox i did this: 
1. type "about:config" in address bar
2. search for "greasemonkey.editor", change it to "/usr/bin/notepadpp" 
3. open a teminal and "sudo gedit /usr/bin/notepadpp"
4. paste this and save(change "Program Files" if needed)
```
#!/bin/bash
wine "C:\Program Files\Notepad++\notepad++.exe" $1
```
5. close gedit and "sudo chmod +x /usr/bin/notepadpp"

PS2: I must say I've run in some problems with file reloads, things related to Wine I guess, since this program never had those problemns in native environment.

---

### Post by hanniph on 2008-07-20
Nice. I will give it a try someday, but for now I'm satisfied with Komodo Edit. :)

---

### Post by iamah on 2008-07-20
I went there at Komodo site, but they ask some kind of registration... is it some kind of Eclipse based IDE?

I could get what I wanted with Eclipse, but I find it somewhat cumbersome for small tasks...  for that, those small old school windows editors have a nice balance between features, size and usability, IMO...

---

### Post by hanniph on 2008-07-20
That registration part is optional. You can leave all blanks empty and skip to download section. 

Komodo edit has both function navigation and auto-complete function. It's simplified and free version of Komodo IDE. And um, I've never tried Eclipse 8-)

---

### Post by ankursethi on 2008-07-20
What about Vim or Emacs?

Trust me, they're not that hard. You could pick one and learn the basics in a day or two, then you keep learning new stuff as you work with it.

I use Emacs and know just 5 or 10 keystrokes by heart. For the rest, I have a cheat sheet. Same goes for Vim.

---

### Post by iamah on 2008-07-20
I'll definitely try Komodo, and possibily give it a shot at Vim and Emacs... :)
Thanks

---

### Post by iamah on 2008-07-28
Komodo looks really nice, but I couldn't get code browser tab... I'm thinking is a pro feature... if so, my quest continues:popcorn:

---

### Post by ceclauson on 2008-07-28
Eclipse is annoying at the beginning, but once you get used to it it's pretty handy.

---

### Post by iamah on 2008-08-03
I'm excited about Vim, because of this feature:
[http://www.oreillynet.com/mac/blog/2006/07/more_vim_save_time_with_macros_1.html](http://www.oreillynet.com/mac/blog/2006/07/more_vim_save_time_with_macros_1.html)

before learning that I really didn't get the point of vim... but macros are just the start...

---

### Post by catchmeifyoutry on 2008-08-04
> **iamah said:**
> I'm excited about Vim, because of this feature:
[http://www.oreillynet.com/mac/blog/2006/07/more_vim_save_time_with_macros_1.html](http://www.oreillynet.com/mac/blog/2006/07/more_vim_save_time_with_macros_1.html)

before learning that I really didn't get the point of vim... but macros are just the start...

Welcome new Vim user, may the force be with you.
Don't forget to type "vimtutor" in the terminal to learn some basic skills.
The added benefit of vim is that if you can access your server via terminal you can directly edit the javascript (or html, php, css, etc.) without downloading/uploading.

---

### Post by gimakel on 2008-08-28
I always use [1st JavaScript Editor]("http://www.yaldex.com/JSFactory_Pro.htm")

---

### Post by LaRoza on 2008-08-28
> **gimakel said:**
> I always use 
That is a commercial products. Looks like spam.

Also, it is Windows only. You'll note this is not only a Linux site, but a community that almost universally values free software. That editor has no special features we can't get for free, and the site is very poorly designed. 

Please don't spam our forum. Yes, this is a public notice (not a usual one for spammers) because that pisses me off too much.

---

### Post by jespdj on 2008-08-28
[NetBeans](http://www.netbeans.org/) has very good support for JavaScript.

---

### Post by tinny on 2008-09-03
> **jespdj said:**
> [NetBeans](http://www.netbeans.org/) has very good support for JavaScript.

+1

Just been doing some JavaScript dev with NetBean's... NICE!

---

