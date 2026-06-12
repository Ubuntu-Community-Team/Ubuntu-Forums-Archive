---
title: "[SOLVED] Firefox missing title bar"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by asgard_command on 2008-07-01
On occasion when opening a new page in Firefox it will shrink the window to about a quarter the size and loose the title bar. You also can't maximize from the menu or any other way. If I go back a page or close that tab the title bar reappears and I can resize the window.
Anybody know what causes this.
I run Ubuntu and Firefox 3 though I had the same problem with Firefox 2.

---

### Post by NT4usB on 2008-07-01
That sounds like a javaskript action.
Tools>Options> (Edit>Preferences)> Content flag. Click on Advanced next to Javaskript. Uncheck those boxes and see if it makes a difference.

---

### Post by Inxsible on 2008-07-01
> **asgard_command said:**
> On occasion when opening a new page in Firefox it will shrink the window to about a quarter the size and loose the title bar. You also can't maximize from the menu or any other way. If I go back a page or close that tab the title bar reappears and I can resize the window.
Anybody know what causes this.
I run Ubuntu and Firefox 3 though I had the same problem with Firefox 2.Does it happen only on a particular website or is it random ?

---

### Post by asgard_command on 2008-07-03
It doesn't happen often enough for me to have noticed any pattern. Most recently it was on my banking site but it did it all the time for that site so I think it is site specific rather than random.

---

### Post by asgard_command on 2008-07-03
Unchecking the options under advanced for java script had no effect but disabling java script all together worked. Not sure I want to have no java script but I guess if it's a site I have to get on at least I can now until I find a more complete solution.

---

### Post by silkstone on 2008-07-03
Similar report here...

[http://ubuntuforums.org/showthread.php?t=848446](http://ubuntuforums.org/showthread.php?t=848446)

Sounds like it's a bug caused by typing 'trans'.

---

### Post by asgard_command on 2008-07-04
Interesting set of circumstances that were causing this.
I realized the link on my bank site that was causing the problem was for a 'trans'fer so it seemed it was definitely linked to the setup I had of a terminal called 'trans' with various rules set for it in compiz.
Changing the terminal profile to something else and changing all the settings referring to a window titled 'trans' seems to have solved the problem.
Thanks for pointing me in the right direction.

---

