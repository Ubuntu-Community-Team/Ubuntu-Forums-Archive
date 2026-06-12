---
title: "Please try my new anagram game - Pynagram"
date: 2009-12-12
forum: Programming Talk
---

### Post by Umang on 2009-12-12
Hi Everyone,

I've made a simple anagram game called Pynagram. Please test it and post suggestions and bugs.

You can  download and install from my PPA. Added this to software sources and then install 'pynagram'.

```
deb [http://ppa.launchpad.net/umang/pynagram-ppa/ubuntu](http://ppa.launchpad.net/umang/pynagram-ppa/ubuntu) karmic main
    
    OR

ppa:umang/pynagram-ppa
```

Even if you have no specific comment, I would appreciate a post like "No bugs/suggestion. Nice/Boring/OK/Old/Interesting/etc".

Notice: I haven't been able to make a menu item as yet, so you will have to do an Alt+F2 and then type 'pynagram' to play after you install.

Pynagram's Launchpad page: [https://launchpad.net/pynagram](https://launchpad.net/pynagram)

Contributions are welcome. Here are a few things you can help with. These are very non-technical issues, you don't need to know how to code to help out here:
[LIST]
[*]The description needs to be improved. A more descriptive and accurate text would be great!
[*]The logo needs to be better. If you could make a new logo for Pynagram, I would be more than happy to include it.
[*]Help write a "How to install" file. I am going to upload one soon. If you are interested in writing the easiest INSTALL file, I would be glad to accept contributions here.
[/LIST]
If you can help out on the technical side, here are things that I don't know how to do. These involved Python, PyQt or packaging in general.

[LIST]
[*] Make the .deb package put a menu item (a .desktop file I believe). 
[*] Put the logo in a place from where I can set it as the main window's icon on all operating systems. If you know where and how I should do this (distutils? Separate for each installer/OS e.g Debian packaging?) please do let me know.
[*] Resize the window after every game to make the words fit. (LP495877 : [https://bugs.launchpad.net/pynagram/+bug/495877](https://bugs.launchpad.net/pynagram/+bug/495877)) I have no idea why this happens.
[/LIST]
Finally, if you think this is almost ready for the repos, say so and I will try to squeeze a bit of time to make Pynagram ready soon.

Thanks a lot!

PS: I hope this is in the correct forum

---

### Post by Umang on 2009-12-14
Bump.

Anyone?

---

### Post by nvteighen on 2009-12-14
I've played with it and read the code, well... honestly, very quickly. I like the shape it has: the code seems to be really well designed and the game works perfectly.

The issue is the one you mentioned of the window resizing itself. I'm almost an ignorant on how Qt works (I'm much more a GTK+ guy), but if you can use any fixed-length container widget instead of placing the guesses by columns, it would solve the issue.

The one objection I've got for your backend code is that I don't understand why the computer has to solve the anagram in order to give you the answer. Wouldn't be much easier to save the solution somewhere and just retrieve the solution when asked?

But great job!

---

### Post by Umang on 2009-12-14
Thanks for the comments. :)

I haven't really touched the backend for sometime, so I almost forgot how it works. But here's my reasoning: If I had to save each of the possibilities, then I would have to compile such a result for each of the possibilities for every wordlist I want to use.

I realized relatively early that someone might want to customize the wordlist. Now I don't think it would have been fun to compile a new set of results for a new worksheets. Also, I am considering support for multiple wordlists later and an option to add a custom wordlist. It appears to me that having the computer solve the anagram is the best way of going about it. If you have any suggestions on this, I would be glad to improve Pynagram.

I actually have the 0.1 series use PyGTK and not PyQt. (Seeing how horrible it looked on windows, after having to four run installers for different components of PyGTK, made me consider PyQt. Ironically, I am yet to test Pynagram on Windows!) In GTK I had it resize after every new game, which worked (more or less). Here, it doesn't do the resizing properly when I first request it (new game), but does so after the first time I hit enter. What confuses me is that it is the same line of code doing the resizing, it doesn't work the first time, but the second time only. (Duplicating the line doesn't help)

I'm considering making the width fixed and only the height variable, let's see how that works out. Still don't have too much free time, but I'll give that a shot also.

Thanks for your feedback! :)

---

### Post by nvteighen on 2009-12-14
> **Umang said:**
> Thanks for the comments. :)

I haven't really touched the backend for sometime, so I almost forgot how it works. But here's my reasoning: If I had to save each of the possibilities, then I would have to compile such a result for each of the possibilities for every wordlist I want to use.

I realized relatively early that someone might want to customize the wordlist. Now I don't think it would have been fun to compile a new set of results for a new worksheets. Also, I am considering support for multiple wordlists later and an option to add a custom wordlist. It appears to me that having the computer solve the anagram is the best way of going about it. If you have any suggestions on this, I would be glad to improve Pynagram.


Heck... I misunderstood the game's rules: I though you were to find just a single word by using all letters. No, now that I've played again, there is no other way to do it.

---

### Post by Umang on 2009-12-15
OK. I've found a horrible way to fix the resizing issue, but I'm going to keep it as a temporary solution, until I am able to understand what exactly is happening. If I get the resizing to happen after every timeout (1 second), there is hardly a noticable delay between a new game and the resize.

Pathetic, I know, but it's better than the previous situation...

---

