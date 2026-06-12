---
title: "official documentation for 18.10 is all wrong for 18.04"
date: 2019-03-18
forum: New to Ubuntu
---

### Post by antitna on 2019-03-18
Hello,
I can't find official documentation for 18.04.  I don't know for sure but I think I am running Ubuntu Studio 18.04.  

I did find this: [https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en)
but this documentation is for 18.10, not 18.04.  The 18.1 documentation is all wrong for 18.04.  


[LIST]
[*]Open the [Activities]("https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en#activities") overview and       start typing Settings.


[*]Click on Settings.  <-- There is not Settings.  There is instead Settings Manager and Settings Editor, so I click on "Settings Manager"... Clicking on Settings Manager does not open Settings Manager, instead, clicking on Settings Manager opens Settings.  Ok then...


[*]Click on Privacy in the sidebar to open the panel.  <-- There is nothing that I can identify as a sidebar and there is nothing labeled as Privacy.  There is a search function... Search for Privacy gives no result. 


[*]Press on Screen Lock. <--can't find this (see above)


[*]If Automatic Screen Lock is on, you can change the value       in the Lock screen after blank for drop-down list. <--can't find this (see above)


[/LIST]



Can anyone help me find the 18.04 documentation?  Thanks!

---

### Post by Impavidus on 2019-03-18
The differences between 18.04 and 18.10 aren't very large, but your problem is that Ubuntu Studio uses the xfce user interface, while Ubuntu uses Gnome 3. Xubuntu also uses xfce, so you could try Xubuntu documentation instead.

---

### Post by #&amp;thj^% on 2019-03-18
One of many ways to tell what you are running is:
```
echo $DESKTOP_SESSION

```
Or:
```
lsb_release -a
```
or:
```
cat /etc/os-release
```
Docs found here:
Gnome Ubuntu Desktop Guide: [https://help.ubuntu.com/lts/ubuntu-help/index.html](https://help.ubuntu.com/lts/ubuntu-help/index.html)
Ubuntu Studio: [https://ubuntustudio.org/support/](https://ubuntustudio.org/support/)
Xubuntu: [https://docs.xubuntu.org/current/user/C/xubuntu-documentation-A4.pdf](https://docs.xubuntu.org/current/user/C/xubuntu-documentation-A4.pdf)
and here: [https://docs.xubuntu.org/1710/user/C/index.html](https://docs.xubuntu.org/1710/user/C/index.html)

---

### Post by deadflowr on 2019-03-18
As noted Ubuntu Studio should be running an xfce/xubuntu environment.
But that said, you could have just clicked the Official Documentation link at the top of the page to get to the main documentation page which has the documentation links for all currently supported releases, including 18.04.

---

