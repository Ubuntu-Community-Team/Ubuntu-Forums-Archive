---
title: "sudo issues"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Doormat on 2008-04-22
I can no longer sudo when it asks for my password I input it and nothing happens, when I type su and then try to put in my password it has an authentication error. What do I do?

---

### Post by Joeb454 on 2008-04-22
When you enter your password for sudo it will never show any input, this is normal :)

Just enter your password (making sure you type it correctly of course ;)) and hit enter. That's it :)

---

### Post by thiebaude on 2008-04-22
After you type in your password, do you press enter?

---

### Post by Wazoot on 2008-04-22
yup just hit enter when your done typing your password and it should take it!
I was in your position once lol. Took me forever to figure it out =]

~Waz00t

---

### Post by Doormat on 2008-04-22
if I type sudo fdisk -l it will ask for my password, I enter it and hit enter and nothing happens then I tried to su and then use fdisk but I could not su (see above). I know this is the correct password is there any way to reset my password perhaps?

---

### Post by Joeb454 on 2008-04-22
Hmm, sounds a bit odd.

What happens if you do ```
sudo aptitude update
``` Does it do anything then?
Just for the record - that will basically check to see if there are any system updates :)

---

### Post by Doormat on 2008-04-22
nothing happens

---

### Post by Doormat on 2008-04-22
issue solved: booted into recovery mode and:
adduser username admin

booted normally and sudo works

---

