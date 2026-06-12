---
title: "password in terminal"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by cladder58 on 2012-11-05
i am running ubuntu 12.10 
i fancy putting mate on after i put the first line in terminal you got to put the password in but terminal will not let me type it

---

### Post by codemaniac on 2012-11-05
> **cladder58 said:**
> i am running ubuntu 12.10 
i fancy putting mate on after i put the first line in terminal you got to put the password in but terminal will not let me type it

Hi, 

Welcome to the forums :=)

It is not exactly clear from your post what are trying to convey!
I assume the when you type in your password nothing shows up right ?
If it is what happening to you then it is compeltely normal , as Unix is designed that way for securities sake.

However you can set up your sudoer environment so that passwords are shown as asterisks(*).
 refer the section "Enabling Visual Feedback when Typing Passwords" int the below link .

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by newb85 on 2012-11-05
You won't be given any visual feedback as you type the password, but it's still accepting the characters.  Simply type your password and hit enter.

---

### Post by Paari on 2012-11-05
It also ensures, you don't edit your password while typing... This is normal !

---

### Post by cladder58 on 2012-11-06
i could not type my password or anything

---

### Post by newb85 on 2012-11-06
Make sure you don't have CAPS LOCK on, and if your password contains numbers you enter with the number pad, make sure NUM LOCK is on.

If this seems too obvious, don't be offended.  I'm speaking from personal experience.

---

### Post by houseworkshy on 2012-11-06
As stated there is no visual feedback whilst entering passwords, not  even *'s. People looking over your shoulder won't even know how many  characters are in your password.  Otherwise it's normal entry, including  deleting after a mistake, sometimes one just *knows* it's been typed wrong.
That's  mostly been said above.  If you're not sure things are as they should  try "whoami" in the terminal.  Just a quick test to make sure you are  you and in the right account.
Welcome to the forums by the way, I  don't know if that means you are new to linux too, on the chance that  you are this is an excellent free guide which gives a good overview very  quickly.   [http://ubuntu-manual.org](http://ubuntu-manual.org)
As you are in the terminal  anyway it's worth knowing that the command line has a lot of built in  support.  To access them the main command are "info" and "man".  To know  how to use them try them on themselves first, "man info", "info man",  "man man", "info info".  
Because one can have many terminals open at the  same time, and copy and past between them, one useful practice is to  have one open for the manual pages and another in which one does things.  "q" exits the manuals and returns to the command line.  
"apropos" is  one very useful command when starting out; "man apropos" for details.   You could try "apropos password" and then "man" the results if something  does turn out not to be as it should be.  But it doesn't sound like you  have a problem based on what you've posted, and if you *don't* have a problem 'fixing' it could soon cause one.  So if all's well don't mess.  In fact if you are new to linux I'd recomend saving the command line for a bit later, it's a bit like running cmd in windows, good to know but perhaps not the very first thing to do.

If this is all lessons  on egg sucking for grandma then no offence intended,  I was only going  on your post count and am aware that new to a forum doesn't mean new to  linux.
Either way good luck and have fun.

---

### Post by newb85 on 2012-11-06
Can't believe I've never heard of apropos before now.

Thanks!

---

### Post by cladder58 on 2012-11-08
well i am back to the same problem.  i did manager to load mint on but i tried different web sites copying and paste then it worked i do not know why  i could put my password in .
i am now trying to load anti virus bitdefender on and when it comes to my password nothing happens 
i looked at the number lock etc did not work 
all what happens the  insert  thing flashes  al it dose carries on flashing 
i type the password and pressed return and nothing

---

