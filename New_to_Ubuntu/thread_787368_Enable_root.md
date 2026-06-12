---
title: "Enable root"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Nikunj93 on 2008-05-08
how can we login into root account?
i have only my accounts password neither did i see any option of root during installation

---

### Post by RequinB4 on 2008-05-08
Please read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2008-05-08
Ubuntu uses sudo. The proper way to obtain a root shell is to either boot to recovery mode or use :

```
sudo -i
```

To all: On these forums, please teach new users how to use sudo properly. Yes there are times when setting a root password is needed, but it is rare.

---

### Post by Nikunj93 on 2008-05-09
well i wanted to get only root privileges
so i asked
if root privilages can be gained through sudo then whats the need 
I dont need it thanks!

---

### Post by Nikunj93 on 2008-05-09
i needed one info
well its offtopic
but
like in windows when i cliked on the scroller present in the mouse i could scroll the page with moving the mouse and did not require scrolling
but is that option there in UBUNTU?

---

### Post by dmub82 on 2008-05-09
> **Nikunj93 said:**
> i needed one info
well its offtopic
but
like in windows when i cliked on the scroller present in the mouse i could scroll the page with moving the mouse and did not require scrolling
but is that option there in UBUNTU?

In what application? If you're talking about Firefox, type ```
about:config
``` in the address bar. You'll get a little warning, just click yes; you'll see a page with a bunch of settings. In the search bar at the top of that page, search and find the setting ```
general.autoScroll
```Double click that line to change the value to "true". That should do it.

---

### Post by Nikunj93 on 2008-05-09
hey thanks it worked
now im a trouble but
:(
whenever i minimize something instead of going to the panel it just termintates
this happens with firefox and pidgin and every other application
what to do??

---

### Post by Nikunj93 on 2008-05-09
any one here?

---

### Post by hyper_ch on 2008-05-09
> **bodhi.zazen said:**
> Yes there are times when setting a root password is needed, but it is rare.
The only case I can think of right now is for using SWAT... besides that I do not know any reason to enable root.

---

### Post by Nikunj93 on 2008-05-09
??

---

### Post by Nikunj93 on 2008-05-09
what is this man
no one is helping
i can minimze anythin!!

---

### Post by Nikunj93 on 2008-05-09
i would like to u all information that
when ever i open any application i cant see it on the panel also
so when i minize its absent

---

### Post by Nikunj93 on 2008-05-09
:(
anyone plz help
no one is replying why?

---

### Post by Delever on 2008-05-09
You probably lost Window List from your panel. Right-click bottom panel, then "Add to panel...", and then "Window List". After that you can move window list left or right. I hope this is it?

(P.S. ussually no one replies when no one knows the answer)

---

### Post by Bölvaður on 2008-05-09
Window Selector is also fun.

---

### Post by Nikunj93 on 2008-05-09
ok i selected window list now its all ok
but its right alined
what ever i add to the panel is right aligned
while i want it left aligned 
how to do it?

---

### Post by bodhi.zazen on 2008-05-09
> **hyper_ch said:**
> The only case I can think of right now is for using SWAT... besides that I do not know any reason to enable root.

You need to set a root password for many web gui tools. Another example is CUPS.

---

### Post by 10Digits on 2008-05-09
If your panel is right aligned then right click on it and go to properties on the context menu. Then change the alignment to whatever:) catches your fancy.

---

### Post by raypsi on 2008-05-09
Oh yes I remember how I got to root well sort of. Just like they were saying above, go to applications > accessories > terminal. This will pull up a command line terminal/window. 

Now I had to run dpgk with some other sub commands added. This was all because I couldn't update. Until I ran this command from root. So instead of update I went to upgrade to hardy heron.

Whale hail I couldn't get sudo to work until I found out why.

sudo dpkg is what I used, it ran the dpgk command from root

usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
I saw the above when I typed sudo and hit enter I dropped the -u and just ran it 'sudo dpgk'

It took a long time to download hardy heron at 56kbps into a 8mbps pipe.

You might be able to run root from a gui or desktop but you still have to use sudo to get there.

---

