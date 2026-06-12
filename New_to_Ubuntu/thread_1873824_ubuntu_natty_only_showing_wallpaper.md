---
title: "ubuntu natty only showing wallpaper"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by dock821 on 2011-11-02
I recently just upgraded to Natty 11.04 and after it installed it goes straight to keyring pass code. i put my password in and it only displays the wallpaper. i have looked through other forums and i got one forum which said to sudo apt-get remove compiz-core. i did that and now all i have is a wallpaper and a blck X as a cursor. any help will be greatly apprec.

---

### Post by ubume2 on 2011-11-02
Not an expert here.  I would go in on rescue mode, try reinstalling compiz-core, and see what happens.

sudo apt-get install [name of app]

If that doesn't work, Try reinstalling 11.04

---

### Post by dock821 on 2011-11-03
thank you for answering on my post greatly appreciated. i tried sudo apt-get install compiz-core again and it fixed my cursor but im still only getting the wallpaper. im using a netbook with no cd-rom drive and do not have a flash drive accessible at the moment. is there a way to reinstall 11.04 without it??

---

### Post by ubume2 on 2011-11-04
> **dock821 said:**
> I recently just upgraded to Natty 11.04 and after it installed it goes straight to keyring pass code. i put my password in and it only displays the wallpaper. i have looked through other forums and i got one forum which said to sudo apt-get remove compiz-core. i did that and now all i have is a wallpaper and a blck X as a cursor. any help will be greatly apprec.

Right out front, I would say start over with a fresh install.

I am posting because nobody else has posted yet.  I've used Ubuntu for 5 years, but really I am a newbie.  Just hoping that somebody who really knows what they are doing will pipe in here.

You said that you upgraded to 11.04.  After the upgrade you immediately started having problems?  I've tried upgrades a couple of times, and had poor results both times.

Do you get a login screen?  If you do, try changing from Ubuntu to Ubuntu Classic, and see if you get the normal desktop.

If you do, and it works, stick with Classic.

If you still have problems,  and have an unusuable system, I would do a fresh install.

11.04 is now pretty stable. If you don't like the unity desktop, you can stick with the "classic" Desktop.

P.S. This probably won't help, but you could try from a terminal
sudo apt-get update  ,
and then sudo apt-get upgrade, reboot and see what happens.

Good luck.

---

### Post by BillyBoa on 2011-11-04
I agree, if you confront such issues, it's very difficult to restore everything and you are going to continue to have problems in the future. Just consider a better installation.

---

### Post by dock821 on 2011-11-04
thank you all for ur post and help. every time i sudo apt-get update it says it fails. i will just try and reinstall ubuntu again. i just gotta find a external hard drive to load it from. thank you all again.

---

