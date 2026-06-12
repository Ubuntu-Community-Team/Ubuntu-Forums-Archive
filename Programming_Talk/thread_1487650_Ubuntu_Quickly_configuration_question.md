---
title: "Ubuntu Quickly configuration question"
date: 2010-05-19
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-05-19
What is the most efficient way of changing the editor from Gedit to say, Geany?

I have set py files to open with geany by default, but "quickly edit" results in the files opening with gedit instead". I dont see any reference to gedit in my quickly projects hidden files.

---

### Post by OgreProgrammer on 2010-05-23
I have found two ways to resolve this. 

The first one is to edit the /usr/share/quickly templates to use alternate software. This is less than ideal as an update to quickly could destroy my changes. It is the cleaner of the two however.

The second is to use quickly to duplicate and rename a template. This places a complete copy in my /home. I then edit to taste. While this is less exposed to disruption, it recreates a bunch of extra stuff. I also have to change my projects(one time each) to use the new template. Nevertheless, this is the option I have chosen.

---

