---
title: "kdevelop"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Zalorioresscon on 2008-04-29
So I'm clearly Noob when it comes to Linux, been using it for 3 days now but I want to make a successful transition from Windows. I am a CS Major in college looking for a good IDE for linux, and I heard about KDevelop.

i downloaded the KDevelop-3.5.1.tar.bz2. I don't understand how you guys do this, I can't figure out how to install the program onto my machine. 

So... How do i take this .tar.bz2 file and install the program that lies within it?

Thank you.

---

### Post by aheckler on 2008-04-29
What you need to do is called "compiling from source". Instructions can be found here: [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by martrn on 2008-04-29
> **Zalorioresscon said:**
> So I'm clearly Noob when it comes to Linux, been using it for 3 days now but I want to make a successful transition from Windows. I am a CS Major in college looking for a good IDE for linux, and I heard about KDevelop.

i downloaded the KDevelop-3.5.1.tar.bz2. I don't understand how you guys do this, I can't figure out how to install the program onto my machine. 

So... How do i take this .tar.bz2 file and install the program that lies within it?

Thank you.

you don't neet to compile kdevelop from source just
```

sudo apt-get install kdevelop
```

should install it.

To add using widgets instead of forms takes some getting used to
linux != windoze

---

### Post by aheckler on 2008-04-29
> **martrn said:**
> you don't neet to compile kdevelop just
```

sudo apt-get install kdevelop
```

should install it

Ahh yes, good idea. I just read that he'd downloaded the tar already so... yeah. My bad there.

---

### Post by Zalorioresscon on 2008-04-29
Okay so I got that figured out, now I am having a problem with the ./configure

i type ./configure and a whole lot of jargon scrolls the screen, and comes to:

"checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!"

does this mean the package i downloaded is incomplete?

---

### Post by aheckler on 2008-04-29
Yeah, just forget what I told you. It's way too complicated for what you're trying to do. Just go to Accessories > Terminal and type this:

```
sudo apt-get install kdevelop
```

That will install it.

---

### Post by Zalorioresscon on 2008-04-29
So what exactly determines when i can use commands like sudo apt-get install?

---

### Post by aheckler on 2008-04-29
If a program is in your enabled repositiories then you should always install with apt-get. ([Wikipedia on repositiories]("http://en.wikipedia.org/wiki/Linux_repository")) Depending on which repos you have enabled, that will determine which programs you'll be able to install with apt-get.

If one of your repos doesn't have a specific program, then your next method should be to go to the programs website and find a .deb file (the Linux version of an .exe file) and install it using that.

If all else fails, compiling from source is your last option.

---

### Post by Zalorioresscon on 2008-04-29
awesome, thank you so much. is anybody here familiar with KDevelop? i got it installed but already it's giving me hell to figure out how to compile C++ programs lol. giving me all kinds of makefile errors and such when i try to compile.

---

### Post by aheckler on 2008-04-29
Try asking over in the Developing and Programming Forum: [http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by martrn on 2008-04-29
Post a new thred at programming talk [http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39"), you find more programming topics and different languages and more response.  This is more of a bigginers forum (Absolute Beginner Talk Questions) Here.

---

