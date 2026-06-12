---
title: "A couple of login screen questions"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by Danja91 on 2012-06-19
I'm setting up an ubuntu system for my grandparents so that they can read the news and look up information for crossword puzzles in Wikipedia. I have Ubuntu 12.04 installed on a Dell Dimension 4600 (old, I know). The OS is working well for me so far, but I'd like to help my grandparents out a little bit. Since they are completely unfamiliar with computers, I'd like to at least streamline the login process. I have two things I would like to do:

1: Set the login screen language to Russian. This is the major hickup point; when they click on their user name, a "log in" button appears. I would like for it to say "log in" in Russian so that they know what to click on.

2: I have their profile pictures set to their faces, but I can't figure out how to get the picture to show up on the login screen, as is standard for Windows installations.

Could anyone help me one either of the tasks?

---

### Post by anewguy on 2012-06-19
What language did you select when you installed?

Also - if they are going to use this for purely online work, we can tell you how to make the browset auto-start on login.

Dave ;)

---

### Post by Danja91 on 2012-06-19
> **anewguy said:**
> What language did you select when you installed?

Also - if they are going to use this for purely online work, we can tell you how to make the browset auto-start on login.

Dave ;)

I selected English because it's a lot easier for me to read English than Russian. Is it too late to change it?

Autostarting the browser would be great!

---

### Post by anewguy on 2012-06-19
I think there is a by-user setting, but that would not change the login screen.  For that you need to change the system default language.  If you are using the default desktop with 12.04 - i.e., the Unity interface - just slide to the left to bring up the Unity menu, go to the very top entry (Unity dash) - it will bring up a screen with installed/used applications, and also a search area at the top.  Type "language" in the search box and it should pop up Language Support.  Here is where you can set the language.  It's possible you may need to download some sort of Russian language support - I'd have to check into that - before you would be able to select it there.

Obviously, if you don't know Russian, you'll want to set everything up using English and when everything is where you want it THEN change to Russian (you might even want to set up an English-language user id so that even though the login screen would be in Russian, you could login and have the language default to English for you.  I'd have to check on how you do that as well.)

As far as auto-starting the browser:

- just edit the .profile file for each user and add the following line:

firefox &u


You may need to do some searching for the Russian language support - I'll be looking for that as well.  Post back with any questions and in the mean time I'll search for the Russian language support (hopefully it's just a package in the package manager).

Dave ;)

---

### Post by anewguy on 2012-06-19
OK, I checked in the package manager and there is a Russian translation package.  There are actually several - some for certain software (like LibreOffice), etc..  There is also a couple for Cyrillic (sp?) language support - it came up when I did a search using "Russian" in the package manager's search entry.  There may be another piece of the puzzle, and I honestly don't know how that works:  you would probably need to change the keyboard some how to be able to input "Russian" characters.  I'm sure there is probably some simple way to do that, but I don't know it.

Dave ;)

---

### Post by Danja91 on 2012-06-19
Thank you! I already had the Russian packs installed because I had set my grandparents' user accounts to Russian instead of English. All I had to do was change the system default language and the login language was as I wanted.

Any ideas on how to get profile pictures to display on the login screen?

---

### Post by anewguy on 2012-06-20
Geez, I forgot all about that!  Let me do some checking around and see what I can find, if anything.

Dave ;)

---

### Post by anewguy on 2012-06-20
I think [this]("http://ubuntuforums.org/showthread.php?p=11889678") thread covers what you need to do - read the entire thread first so you can see where the post was made pointing out things for 12.04.  It also looks like these pictures would need to be converted to icon images of 96x96, if I'm reading it correctly.  Worth experimenting with!

Let me know how that goes - I'm curious!

Dave ;)

---

### Post by Danja91 on 2012-06-20
> **anewguy said:**
> I think [this]("http://ubuntuforums.org/showthread.php?p=11889678") thread covers what you need to do - read the entire thread first so you can see where the post was made pointing out things for 12.04.  It also looks like these pictures would need to be converted to icon images of 96x96, if I'm reading it correctly.  Worth experimenting with!

Let me know how that goes - I'm curious!

Dave ;)

Thanks Dave. If I'm interpreting that thread correctly, the command line solutions were equivalent to clicking on the user account picture in the users menu and replacing the blank placeholder with the desired image. If so, I have already done this. While this will show you the profile picture if you attempt to log out or switch profiles during a session, it does not have any effect on the main login screen. I believe that I would actually have to edit the login screen in some way to achieve what I want, but I don't have enough experience to do so.

---

### Post by anewguy on 2012-06-22
Yeh, it does look that way.  I don't have clue how to do what you want - sorry.

---

### Post by vidtek on 2012-06-22
Just a thought-

If a web browser is all you need why not use it in kiosk mode?

I saw a how-to somewhere.......

Tony.

---

