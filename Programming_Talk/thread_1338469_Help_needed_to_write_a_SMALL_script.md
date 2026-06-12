---
title: "Help needed to write a SMALL script"
date: 2009-11-26
forum: Programming Talk
---

### Post by emigrant on 2009-11-26
hi all ;)
i would be very greateful if anybody can help me to get a script which should be able to
[COLOR=Red]switch off 'extra' visual effects on switchuser/logoff and switch on 'extra' visual effects back on switchuser/logins[/COLOR].

this is desperately because, in my machine, at a time one user only is able to have enabled 'extra' visual effects. :(

hope you understand...
thank you very much for your ideas/suggestions/helps as i have not written system related scripts before...

:popcorn:

---

### Post by mo.reina on 2009-11-26
you'll have to add the script name to /etc/gdm/PostSession/Default.  this is the script that runs everytime you logout of gnome.

the command you're looking for is ```
metacity --replace &
``` to turn off compiz and ```
compiz --replace &
``` to turn it back on.  

however, i think compiz turns on automatically on login, no?

anyway just put the metacity command in the script i mentioned above and it should turn off compiz on logout everytime.

if compiz doesn't turn on automatically on login, add the compiz command in this script

/etc/gdm/PostLogin/Default

you might have to create the post login default script, but there is usually an example script labelled Default.sample

---

### Post by emigrant on 2009-11-26
hi, thank you very much for the help :) 
but i don't have installed compiz, and i think i wouldnt since im contended with the default animation in the 'extra' desktop effects. 
this is because, anyway i can't activate compiz in 2 accounts at the same time.
any suggestions... ? :(

thank you very much.

---

### Post by emigrant on 2009-11-26
oh sorry for my above post. i didn't know that compiz is installed by default.
the script worked and thank you very much :)
but to get it worked i have to login/logout.
where should i add the script to '[COLOR=Red]switch user[/COLOR]' as well.
one more thing, although now i get the extra visual effects in all accounts, i don't get that 'wobly' effect in other accounts except my default one.

---

### Post by emigrant on 2009-11-26
](*,) sorrry for the damn hurry.
actually the wobly is working now as a charm \\:D/.
now the only remaining thing is to add the script to the switch user session.

thank you very much =;

---

### Post by emigrant on 2009-11-27
hi mo.reina,
with this script running, i get a new problem,
i can't change themes in the sense, the window border won't change but only the window appearance color. :(
if i disable this script, everything works fine. i posted a seperate thread regarding this here (before knowing the this script is related with that):
[http://ubuntuforums.org/showthread.php?p=8393803#post8393803](http://ubuntuforums.org/showthread.php?p=8393803#post8393803)


any suggestions...?
thank you very much :pop corn:

---

### Post by mo.reina on 2009-11-28
try installing the fusion icon and emerald theme manager.  see if you can switch themes with emerald

---

### Post by emigrant on 2009-11-28
no still the problem persists... :(

---

### Post by Penguin Guy on 2009-11-28
Copy and paste the following commands into the terminal and press Enter:
```

echo "compiz --replace &" >> ~/.profile
echo "metacity --replace &" >> ~/.bash_logout

```
Your computer should now enable cool visual effects at logon and disable them at logout.

---

### Post by emigrant on 2009-11-29
> **Penguin Guy said:**
> Copy and paste the following commands into the terminal and press Enter:
```

echo "compiz --replace &" >> ~/.profile
echo "metacity --replace &" >> ~/.bash_logout

```Your computer should now enable cool visual effects at logon and disable them at logout.

still the window border won't change. only the body color :(

---

