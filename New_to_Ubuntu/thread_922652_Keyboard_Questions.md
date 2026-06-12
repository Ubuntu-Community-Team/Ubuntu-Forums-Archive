---
title: "Keyboard Questions"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-09-17
So I have just been noticing a few little things that reaaaaaaly make me angry about Linux, the first thing, being the lack of an at symbol and replacing it with quotation marks, secondly is the dissapearance ofmy question mark and its replacement, the É.


So, how do I get these back to normal. Or am I stuck forever not being able to sign into hotmail and without a necessary punctuation.

---

### Post by Titan8990 on 2008-09-17
System -> Preferences -> Keyboard -> Layout Tab

Select Generic -> US PC-104

You are currently using US-INTL.

---

### Post by marcordenis on 2008-09-17
Maybe your Keyboard Layout is wrong. Click on System -> Preferences -> Keyboard, then on the tab Layout. Depending on what country you are in (what country your keybaord comes from) the Layout will be different. There is a box where you can try it out to see if it works.
Hope this helps you.

---

### Post by Vendettaseve on 2008-09-17
I selected Canadian when I booted up, Wonder how that happend -.-

---

### Post by Vendettaseve on 2008-09-17
Ok I changed to USA Default keyboard layout and everything works good :D 


?????@@@@@??????@@@@


Success 

Thanks everyone

---

### Post by Titan8990 on 2008-09-17
During the installation it detects your keyboard layout by asking if you have certain keys on your keyboard. One that it asks you about is an accent mark that looks very much like a single quote '. 

Don't forget to mark your thread as solved.

---

### Post by billgoldberg on 2008-09-17
In the future it would be wise not to blame everyones favorite OS if you want help.

Most of the time the problem lays between the chair and keyboard.

--

Mark your thread as solved please.

---

### Post by Titan8990 on 2008-09-17
In the future you should give users in the Absolute Beginner Talk forums a break. It is not easy for people to take years of computer experience with Windows and throw it in the trash (where it should be).

---

### Post by billgoldberg on 2008-09-17
If you want another way to achieve this task.

Open up /etc/X11/xorg.conf with your favorite text editor. Let's presume it's gedit.

```
sudo gedit /etc/X11/xorg.conf
```

in the keyboard section of the textfile, in the bottom of the keyboard settings, put us between the "".

So it would be

> Option &#8220;XkbLayout&#8221; &#8220;us&#8221;

Save that.

--

Or you can use the terminal / alt+  f2 / fbrun/ "sessions"/ your startup file in fluxbox/ ... if you type this:

```
setxkbmap us
```

--
Just in case any non-gnome people stumble upon this thread.

---

### Post by billgoldberg on 2008-09-17
> **Titan8990 said:**
> In the future you should give users in the Absolute Beginner Talk forums a break. It is not easy for people to take years of computer experience with Windows and throw it in the trash (where it should be).

If you want help, be friendly. 

It's not because you are angry at your computer, that you need to take it out on volunteers who are trying to help you.

---

### Post by Titan8990 on 2008-09-17
I was in no way offended by the OP.

Maybe it is because I read this today: [http://ubuntuforums.org/showthread.php?t=922072](http://ubuntuforums.org/showthread.php?t=922072) 

or maybe it is because I have been volunteering to help people on forums long before I discovered Linux and have actually seen users get banned over things they have said to me.....

---

### Post by Vendettaseve on 2008-09-17
I did not mean to offend anyone by my original post, Im sorry if I have. 

Having said that, as ALOT of things are different with Linux, I simply assumed that this was a new thing and was relatively bothered because I rather like question marks.

Thanks for your help,

those who gave it.

---

### Post by Anzan on 2008-09-17
> **Vendettaseve said:**
> I selected Canadian when I booted up, Wonder how that happend -.-

I've made that mistake: it gives a Francophone layout.

---

