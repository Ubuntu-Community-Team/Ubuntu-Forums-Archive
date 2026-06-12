---
title: "keyboard layout for two different users"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by olly_ontario on 2008-06-25
Hello!
Have just started using Ubuntu (Hardy Heron) a week ago.
Now I have a computer with 2 users, that is me and my father.
I use the Dvorak layout whereas my father uses the regular QWERTY layout. Is there anyway where I can configure Ubuntu so that both of us can use the computer without any inconvenience.
At the moment since the default layout is Dvorak my dad is not able to use it.
Please suggest!
Regards,
Olly

---

### Post by p_quarles on 2008-06-25
Yeah, and it should be easy, assuming you and your father have your own individual user accounts on this computer.

---

### Post by rockerphil on 2008-06-25
like mentioned before it should be pretty easy if you've got seperate accounts. if not here's how to add an account for your dad to use. just open up a terminal and type this 

sudo adduser <username>

it'll ask you for your sudo password (it won't show up as you type it, this is normal)

then just have your dad set his own password and things of the like. once that's done your dad will be able to log in under his own user name and be able to cofigure the keyboard layout for his account, and not affect the keyboard layout for your account. hope this info helps


ps. remember to replace <username> with the user name your dad is going to use to log in

---

### Post by olly_ontario on 2008-06-26
Thanks for your replies! However the main problem comes during the username/password entry. Becase the defauld keyboard layout is set to dvorak while my dad type in querty so how can he can his username and login?!
Any Ideas?!
Thanks!!

---

### Post by p_quarles on 2008-06-27
Under the administrative menu in the top bar, there is a section called smoething like "Users and Groups." That submenu will give you the option of creating a new user, which can then keep all of its own settings without changing yours.

---

### Post by mcduck on 2008-06-27
If you can tolerate the idea of logging in with nirmal layout and using DVORAK _after_ that, I'd recommnd setting the default layout to QWERTY, and then your own account's layout to DVORAK..

Actually I don't think there's any other way, the login screen doesn't have a keyboard layout selection (and it would be pretty annoying for your dad to need to change the layout every time he logs in..).

---

