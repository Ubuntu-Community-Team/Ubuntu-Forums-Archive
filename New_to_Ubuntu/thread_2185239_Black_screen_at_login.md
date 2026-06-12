---
title: "Black screen at login"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by fatharraxman on 2013-11-01
[TABLE]
[TR]
[TD="class: votecell"]     

              [/TD]
              [TD="class: postcell"]                I have installed Ubuntu 13.10 and it was a little bet heavy  on my 1 gb ram mini notebook, so I went on to cinnamon and installed  gnome classic as well, I observed that I could not log in to defalt  unity desck top, when I write my password on that scerrn it blinck and a  black screen comes on as if it will enter me into it then it return  back to log in screen again without any understanding as if the system  is mad of me using cinnamon. any help please?
      

[/TD]
[/TR]
[/TABLE]

---

### Post by protoss96 on 2013-11-02
If the prompt is asking you for username and password just login, then run this command:
```
startx
```
Are you seeing something graphical?

---

### Post by fantab on 2013-11-02
For 1Gb RAM all, Unity, Cinnamon and Gnome-Classic, will be heavy. Try Xubuntu or Lubuntu.

---

### Post by deadflowr on 2013-11-02
Are you using the cinnamon-stable ppa by chance.
If so, it is a known issue that the version in the ppa causes problems with unity(breakage).
[http://askubuntu.com/questions/361392/does-cinnamon-2-0-really-break-your-13-10-desktop](http://askubuntu.com/questions/361392/does-cinnamon-2-0-really-break-your-13-10-desktop)

I don't know if a bug report is out on this, but you can go to launchpad to find out.

---

### Post by fatharraxman on 2013-11-08
solved by:
[http://askubuntu.com/questions/361392/does-cinnamon-2-0-really-break-your-13-10-desktop](http://askubuntu.com/questions/361392/does-cinnamon-2-0-really-break-your-13-10-desktop)
and:
[http://askubuntu.com/questions/360772/unity-isnt-starting-on-13-10-with-cinnamon-2-0-installed](http://askubuntu.com/questions/360772/unity-isnt-starting-on-13-10-with-cinnamon-2-0-installed)
and:
[http://askubuntu.com/questions/360772/unity-isnt-starting-on-13-10-with-cinnamon-2-0-installed](http://askubuntu.com/questions/360772/unity-isnt-starting-on-13-10-with-cinnamon-2-0-installed)

Thank you

---

