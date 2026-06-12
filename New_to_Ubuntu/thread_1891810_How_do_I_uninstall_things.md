---
title: "How do I uninstall things :/"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by Drowz0r on 2011-12-06
Seems a really dull question but how do I uninstall something?

I don't want to run terminal commands for everything. I've just attempted an install of DC universe through wine (and it won't work - like most games it seems) but now it's on my box and I can't seem to uninstall it. The installed used an exe through wine but the uninstaller didn't remove everything. Additionally the Software Centre can't see it but it's listed under my applications under the ubuntu search thing (the top left thing, also opens with the windows key)

---

### Post by BC59 on 2011-12-06
If you like to uninstall an Ubuntu application, the easiest way is through Ubuntu Software Center-->remove. For applications you installed independently of the Software Center, you have to ask how.

About Wine (microsoft) applications, you can use the Uninstall Wine Software application. If it's not working, because the uninstallers  are windows programs as well and don't work perfectly, then you have to improvise.

I personally delete the hidden ~/.wine folder in ~/Home directory and wine creates a fresh one without the program installed of course.

---

### Post by jjex22 on 2011-12-06
I know you said you didn't want terminal commands, but the best way I know is 

```

wine uninstaller

```

for removing wine programs, of course the software centre is good for removing linux packages - always remember the distinction between programs under wine and linux packages :) personally I prefer the terminal as I find it quicker, but that's just me!

Edit you don't need to delete the wine folder - navigate inside it and delete the program from the program files folder if wine uninstaller doesn't work. Also synaptic, aptittude, software centre are all for removing linux packages - which would be wine, not the programs it runs.

---

### Post by bluexrider on 2011-12-06
I would use synaptic, it get all the dependencies too

---

