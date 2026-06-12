---
title: "open with?"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by vrpatilisl on 2011-11-24
Hi everybody,
I am new in ubantu, I instaled 7zip from ubantu server. But it is not seen in 'openwith ' option. I want to add 7zip to open with list (by default it is not there). in other word i want to make 7z as my default rar/zip  handler. I am noob in terminal. So GUI guide wil be appreciated.
Thanxs

---

### Post by moody_mark on 2011-11-24
Hi, good to see another new user :-)

If you open up your file browser, Places --> Home, then navigate to the place where the file is, you can right click the file, select properties and select the open with tab, you should be able to select your 7zip application from there.

If you cant see your application in the list do this:

- Click add, you should see a new box with a longer list

If its still not there:

- Expand the "+" by Use Custom command and click browse
- You can search for 7zip, all applications are usually in /usr/bin. My 7z was in there.
- Click ok then you can select the application in the list.

I would though personally prefer to use the terminal, the sooner you get started using the terminal the better, you'll find it a very useful tool. Theres lots of guides around for using the terminal, if I find one, I'll post one for you.

---

### Post by vrpatilisl on 2011-11-24
hi
THANXS FOR REPLY AND NICE GUIDE.
you can also please tel me how to use terminal for the same.

---

### Post by 3rdalbum on 2011-11-24
> **vrpatilisl said:**
> Hi everybody,
I am new in ubantu, I instaled 7zip from ubantu server. But it is not seen in 'openwith ' option. I want to add 7zip to open with list (by default it is not there). in other word i want to make 7z as my default rar/zip  handler. I am noob in terminal. So GUI guide wil be appreciated.
Thanxs

On Ubuntu, 7zip is not a graphical program; instead you should use the regular File Roller (Archive Manager) program that comes with Ubuntu to open and deal with the 7z archives.

That's why 7zip doesn't appear as an option in the "Open With" menu; it's not a program that you can see on your screen, it's just a tool or "backend" that other programs can use.

---

