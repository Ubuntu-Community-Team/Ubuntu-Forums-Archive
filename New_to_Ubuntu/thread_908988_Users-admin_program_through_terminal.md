---
title: "Users-admin program through terminal?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by b-war3 on 2008-09-03
Hello everyone,

i have a problem. I did something very stupid (i not telling what) and now i would like to know how you can give someone admin rights trough the terminal. Does somebody know how to do that? Please, i need the answer very much!

---

### Post by tuxulin on 2008-09-03
before you get an answer you must first tell what you did LOL

the commands are
adduser or gksu users-admin then add the new user to the adm group 
then check /etc/group by using nano.

if you have forgotten your first user password (the installed user) then a different aproach is needed. just let us know

Tuxulin

---

### Post by b-war3 on 2008-09-03
Well, what i did, adn please, dont laugh,
i opened the program users-admin, clicked on myself, then properties, and the priveleges, and  then disabled every box that was visible in that screen. I know, it&#347; verry verry stupid. But what i'm  going to do now is add a ne user to the admin list and give myself admin priveleges through that new account. so, problem solved :lolflag:
[EDIT] ok, now i added a new user called rubbens, and i made a password. but when i want to log in, it says "the administrator has disabled your account." then a black screen, and then the login screen again. what did i do wrong?
[EDIT] nvm, problem solved now!

---

### Post by tuxulin on 2008-09-03
good to know all is good :)
just remember Murphy's law "If anything can go wrong, it will"

Tuxulin

---

