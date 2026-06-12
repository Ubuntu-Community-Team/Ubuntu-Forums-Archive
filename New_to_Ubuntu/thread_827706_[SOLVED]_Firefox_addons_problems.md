---
title: "[SOLVED] Firefox addons problems"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-13
I'm getting an error message on every ff addon I try adding on. Where can I find some help with this?

---

### Post by kesman on 2008-06-13
Well, you could tell what version of ubuntu and Firefox you are running, and also the error message you get when you try to install.

---

### Post by niceguy123 on 2008-06-13
I'm running Hardy 8.04 and have now installed both FF3 and FF2, same problem on both. 

```
Firefox could not install the file at

http://addons.mozilla.org/....

because: Unexpected installation error
Reveiw the Error Console log for more details.
-203
```

---

### Post by SunnyRabbiera on 2008-06-13
it might be related to that addon.
you may want to back up your important stuff like bookmarks or cookies if you wish and remove the mozilla profiles folder.

---

### Post by JudgeFudge on 2008-06-13
I had a similar problem. I uninstalled firefox (both 2 and 3 and remembering to export my bookmarks first) then  did a  rm -Rf .mozilla/firefox/

Then reinstalled firefox and reinstalled the add ons.

Kind of drastic but it worked when nothing else would.

---

### Post by acidsolution on 2008-06-13
go to 
```

/home/user/.mozilla/firefox/ke218j8e.default  
```

and delete the file 
extension.cache
extension.ini
extension.rdf

close firefox before deleting this file 
and than restart the firefox 
this must solve your problem 
it takes sumtimes for firefox to restart because it creates this file automatically

---

### Post by niceguy123 on 2008-06-13
> **acidsolution said:**
> go to 
```

/home/user/.mozilla/firefox/ke218j8e.default  
```

and delete the file 
extension.cache
extension.ini
extension.rdf

close firefox before deleting this file 
and than restart the firefox 
this must solve your problem 
it takes sumtimes for firefox to restart because it creates this file automatically

Did I do something wrong?


```
bash: /home/user/.mozilla/firefox/ke218j8e.default: No such file or directory

```

---

### Post by kesman on 2008-06-13
of course replace user with your username =D
and the directory name can differ, but it ends in .default , so you'll easily find it.

---

### Post by Bubba64 on 2008-06-13
A lot of add ons can be added from individual sites rather than Mozilla, if the problem is compatibility. If you install nightly tester tools this will force packages to work.
[https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools](https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools)
Also just installing nightly tester tools has helped others with just getting the add ons that were not ready for the FF 3 browser fro Mozilla.

---

### Post by niceguy123 on 2008-06-13
> **acidsolution said:**
> go to 
```

/home/user/.mozilla/firefox/ke218j8e.default  
```

and delete the file 
extension.cache
extension.ini
extension.rdf

close firefox before deleting this file 
and than restart the firefox 
this must solve your problem 
it takes sumtimes for firefox to restart because it creates this file automatically

That worked great - THANKS.

---

