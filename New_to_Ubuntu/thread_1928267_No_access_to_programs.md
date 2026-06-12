---
title: "No access to programs"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-02-19
My desktop has two Icons on it. IE 7 (PlayOnLinux) and LibreOffice. The bar across the top of my screen says File, Edit, View, Go, Bookmarks, Help.

I cant open a terminal or anything, how do I get to system tools, download manager, anything??

---

### Post by theducksfan2010 on 2012-02-19
Compiz Fusion works, but that is all, no terminal and no network config utility so I cant even get it online to google help on it.

---

### Post by Krytarik on 2012-02-19
Presuming that you are using Unity, try following this guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by sadaruwan12 on 2012-02-19
I think you're stuck in the show desktop function. Lets reset the unity and see if it works or not.

Press Ctrl + Alt + F1 then you'll go into a terminal from there log back in using your log in information.

Now enter the below command,

```

$ unity --reset

```

After the rest prosecc is finised entern this command to reboot,

```

$ sudo init 6

```

Please tell us what happened.

---

### Post by theducksfan2010 on 2012-02-20
I installed a fresh load of Ubuntu 11.10 and then enabled compiz fusion. After i did that I only have the bar across the top of my screen with File, Edit, View, Go , Bookmarks, Help.

I tired   sudo apt-get install gnome-session-fallback so I could go back to Gnome, but my terminal just sits there. The only thing my terminal has run is 

firefox

I have since figured out that when I try to go to 

su

it says:

su: Authentication failure

how do i fix my password for su, without a fresh install all over again, that took hours

---

### Post by wildmanne39 on 2012-02-20
Hi, here is a link to help fix your problem.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Did you use the wiki guide for installing compiz?
Thanks

---

### Post by theducksfan2010 on 2012-02-20
Compiz was already installed, I just checked the cube, wobbly windows etc and lost all access.

I have to have two terminals open to do this, one for firefox, the other too try to fix. But I do not have su, weird because I only used one password, is ther a default for it if I missed that one?

I cant run anything in the terminal except firefox, so the tutorial did not help. The commands did nothing.

---

### Post by wildmanne39 on 2012-02-20
Hi, yes but the guide is to tell you how to set up the cube and effects like wobbly windows.

Make sure you use the right section for your ubuntu version and you will have to reset unity and compiz first.

It is the second link in my signature.
Thanks

---

### Post by theducksfan2010 on 2012-02-20
Okay, installed it per your guide, then did the super key + a and typed ccsm, nothing. Also did alt + F2 and nothing

The compiz works, just nothing else does. I have wobbly windows, can turn my one workspace around and aroundbut cant get to system manager to make four workspaces via one, I cant find any programs or acces anything other than the file manager.

---

### Post by wildmanne39 on 2012-02-20
Hi, the launcher on the left side of the screen is gone and the top panel is gone is that right? if so use the link in my first post to reset unity and compiz and you may have to reinstall unity and compiz.
Thanks

---

### Post by uRock on 2012-02-20
Duplicate threads merged. Please do not create multiple threads on the same topic.

---

### Post by theducksfan2010 on 2012-02-20
guess I am having no luck - followed it and it didn't work. Maybe I just need to go back to what I know and am good with 11.04

---

### Post by theducksfan2010 on 2012-02-20
Hours of trying the ideas posted here, and still no fixes. I wiped my partition clean and did a fresh install. I found these later and wish I had found them before i did re-install

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

Something went wrong! How do I reset Unity or Compiz?


You can easily reset Unity or Compiz using the following commands (be careful when using these commands and only use them if you really have to!):

- to reset the Unity launcher icons:
unity --reset-icons

- to reset Unity:
unity --reset

- to reset Compiz:
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

**from:** [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by wildmanne39 on 2012-02-20
Hi, those are the same commands given in the links that Krytarik andd myself gave you, you must not have went far enough down the page.

I am glad you got it fixed.
Enjoy

---

### Post by theducksfan2010 on 2012-03-12
> **wildmanne39 said:**
> Hi, those are the same commands given in the links that Krytarik andd myself gave you, you must not have went far enough down the page.

I am glad you got it fixed.
Enjoy

Thanks for the help, still new to Linux all over again. So far its a love hate relationship, the hate mainly being on myself when I cant get it back up, lol.

---

### Post by wildmanne39 on 2012-03-13
Hi, your welcome!

---

### Post by wildmanne39 on 2012-03-13
Hi, I do not know about that 11.10 works good for me but not all people have the same experience.

12.04 comes out next month.

---

### Post by theducksfan2010 on 2012-03-13
> **wildmanne39 said:**
> Hi, I do not know about that 11.10 works good for me but not all people have the same experience.

12.04 comes out next month.

I have had success across many machine with Lubuntu 11.10 and mediocre with Ubunt 11.10 on 2. I am eagerly looking forward to changing over to 12.04 next month, across all machines. The Lubuntu 12.04 looks to be packing a lot of changes.

---

### Post by wildmanne39 on 2012-03-14
Hi, 12.04 will not be an LTS version because lubuntu us under heavy development so all versions of lubuntu will be having a lot of changes for the for see able future.

---

