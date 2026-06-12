---
title: "unity dash"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-13
hi its my third thread today 
i am maintaining separate threads to each one . 
 we all know about unity dash , i am attaching that picture also . there how can i made some modifications . i mean if we open dash , its giving as media apps internet apps like this. now what i wanna do is replace them with the applications what i want .
thanks in advance .

---

### Post by mc4man on 2011-09-13
Browse the web, Check email, and Listen to music will all show whatever you pick from available choices in System Settings > System Info > Default Applications, (Web, Mail, Music

I don't believe View Photos can be changed without a source edit or  some unadvised binary diversion/rename, or removing shotwell which will then pick from a preset top down list

---

### Post by raja.genupula on 2011-09-14
actually i am not using them (up  side items), for any application i want i am searching them in the dash it self and using . so i wanna replace them with any other application i am gonna use mostly . 

thanks in advance

---

### Post by lucazade on 2011-09-14
cannot be changed.. yep, are pretty useless also for me.

---

### Post by raja.genupula on 2011-09-14
so guys i am  thinking to close this and mark as solved , what you gonna suggest ?
keep this like this or end ?

---

### Post by mc4man on 2011-09-14
> **lucazade said:**
> cannot be changed.. yep, are pretty useless also for me.

You can alter this to some extent in the src, - PlacesHomeView.cpp

As is the only favorite that can be expanded to 'non-traditional' choices without much consequence is 'Listen to Music' - it is the default for  audio/x-vorbis+ogg= and choices available in System Info.. can be expanded by adding to  audio/x-vorbis+ogg= in the Added Associations section in ~/.local/share/applications/mimeapps.list

---

### Post by raja.genupula on 2011-09-14
hey 
is that only way for changing  those things ?

---

### Post by lucazade on 2011-09-14
> **mc4man said:**
> You can alter this to some extent in the src, - PlacesHomeView.cpp

As is the only favorite that can be expanded to 'non-traditional' choices without much consequence is 'Listen to Music' - it is the default for  audio/x-vorbis+ogg= and choices available in System Info.. can be expanded by adding to  audio/x-vorbis+ogg= in the Added Associations section in ~/.local/share/applications/mimeapps.list

good to know.. I can live with it at the moment, I hope anyway it will be revamped in future unity iterations.

---

### Post by raja.genupula on 2011-09-14
so i think  i am done with this. 
thanks to all for spending your time . 
i am closing this .

---

