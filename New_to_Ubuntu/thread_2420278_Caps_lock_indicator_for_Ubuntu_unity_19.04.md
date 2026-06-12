---
title: "Caps lock indicator for Ubuntu unity 19.04"
date: 2019-06-02
forum: New to Ubuntu
---

### Post by crip720 on 2019-06-02
Was wondering if anyone knows of a caps lock indicator for ubuntu unity desktop 19.04.  The one I was using before does not seem to be updated yet for 19.04([COLOR=#000000]tsbarnes/indicator-keylock), another one I found has not been updated for three years.  I know there are some extensions for the gnome desktop, but don't think they can work on unity.  Do I have to hope that tsbarmes will some day update or is there another indicator that will work?  Thank you.[/COLOR]

---

### Post by oldrocker99 on 2019-06-02
This is what I use:[https://askubuntu.com/questions/799437/lock-keys-panel-indicator-for-mate-desktop](https://askubuntu.com/questions/799437/lock-keys-panel-indicator-for-mate-desktop). It works beautifully.

---

### Post by crip720 on 2019-06-02
What Am I doing wrong? ```
 /opt> python lks-indicator/usr/bin/python: can't find '__main__' module in 'lks-indicator'
```  
did do sudo chmod on the second time, still getting this error.

---

### Post by mc4man on 2019-06-02
Maybe try the .deb, it's as old as the git you're getting but should still work. Link down the git page 
[https://github.com/SergKolo/lks-indicator](https://github.com/SergKolo/lks-indicator)

Install with apt and also install python-gi package.
Can be tested with command of lks-indicator  If working ok add it to startup applications

---

### Post by crip720 on 2019-06-02
Thanks seems to be working, big green circle if off, big red circle on.  All I need.

---

