---
title: "Help me spread the word."
date: 2011-02-06
forum: Programming Talk
---

### Post by cgroza on 2011-02-06
Hello, I recently developed a text editor in python and wxPython and I would like to make it available for everyone. I put it on source forge and softpedia took it and posted on their site. So far I have 45 download and I would like to know how does a developer attract more attention?

I have a deb for it and maybe someone could give me a tutorial on how can I get it in the Ubuntu repositories.
I worked hard on it and I don't want it to be just some forgotten chunk of code somewhere. Thanks.
Source Forge link: [http://sourceforge.net/projects/gecrit/](http://sourceforge.net/projects/gecrit/)
Softpedia link: [http://mac.softpedia.com/get/Word-Processing/gEcrit.shtml](http://mac.softpedia.com/get/Word-Processing/gEcrit.shtml)

Note: The Softpedia screenshots are out of date. The editor changed its looks since then.

Thank you.

---

### Post by SevenMachines on 2011-02-06
Look at the REVU process for getting something into ubuntu
[https://wiki.ubuntu.com/MOTU/Packages/REVU](https://wiki.ubuntu.com/MOTU/Packages/REVU)
other stuff to read,
[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

---

### Post by diesch on 2011-02-06
[http://sourceforge.net/projects/gecrit/](http://sourceforge.net/projects/gecrit/) points to [http://gecrit.sourceforge.net/](http://gecrit.sourceforge.net/) but that URL doesn't contain anything useful about your program. If you want to attract attention you have to provide information about your editor's features, why it is better than the existing ones, how it looks like, what's its current state of development, ...

[http://freshmeat.net/](http://freshmeat.net/) is a good place to announce new projects and releases. For Python programs [http://pypi.python.org/pypi](http://pypi.python.org/pypi) is useful, too.

---

### Post by cgroza on 2011-02-06
> **diesch said:**
> [http://sourceforge.net/projects/gecrit/](http://sourceforge.net/projects/gecrit/) points to [http://gecrit.sourceforge.net/](http://gecrit.sourceforge.net/) but that URL doesn't contain anything useful about your program. If you want to attract attention you have to provide information about your editor's features, why it is better than the existing ones, how it looks like, what's its current state of development, ...

[http://freshmeat.net/](http://freshmeat.net/) is a good place to announce new projects and releases. For Python programs [http://pypi.python.org/pypi](http://pypi.python.org/pypi) is useful, too.

Yes, I was thinking about that. I will do this as soon as I have some spare time.

---

### Post by JOHNNYG713 on 2011-02-06
Looks promising ! I have found some issues, I had to force install to 64 bit ! Does this set a launcher in the menu ? If so where ! started it with gecrit in terminal, and I have line numbers activated, and cant see them, I have tried several different themes, And I had to force Quit the application.

---

### Post by cgroza on 2011-02-06
> **JOHNNYG713 said:**
> Looks promising ! I have found some issues, I had to force install to 64 bit ! Does this set a launcher in the menu ? If so where ! started it with gecrit in terminal, and I have line numbers activated, and cant see them, I have tried several different themes, And I had to force Quit the application.
Glad you tried it. As you noticed it says BETA:p. You should download it from sourceforge because softpedia updates it later. While you are encountering difficulties, does the terminal show error messages?
And no, it does not put any launchers in the menus, but it will soon. The thing is still young and bugs are normal. I use Maverick with the default theme and everything looks fine. Thank you for support. I appreciate it.

P.S: If you have some programming skills, are you interested to join me? :D

---

### Post by cgroza on 2011-02-06
Also, I have tried different themes here now and everything looks OK. And when you say that you were forced to quit the application you mean it froze?

---

### Post by Hur Dur on 2011-02-06
Two Questions:

1.) Is it lightweight? As in, few dependencies, and light on system resources? I'm looking for a replacement for Abiword.

2.) Is it possible to get this working on Arch Linux? I don't mind compiling from source.

---

### Post by cgroza on 2011-02-06
> **Hur Dur said:**
> Two Questions:

1.) Is it lightweight? As in, few dependencies, and light on system resources? I'm looking for a replacement for Abiword.

2.) Is it possible to get this working on Arch Linux? I don't mind compiling from source.

It depends on the wxPython libraries.
It runs pretty fast on my system.
And yes, it should run on arch linux, just make sure python can find the wxPython libs.
I do not know if it could replace Abiword, that depends on what you need.

Also, this project is beta, so problems may appear.

---

### Post by wmcbrine on 2011-02-06
Bear in mind that you're in a very crowded space -- there are fifty million editors out there, and most people who'll want one already have a favorite.

---

### Post by cgroza on 2011-02-06
> **wmcbrine said:**
> Bear in mind that you're in a very crowded space -- there are fifty million editors out there, and most people who'll want one already have a favorite.

You are right, thats why I should think of something special. Thank you for your support. I am open for suggestions.

---

### Post by cgroza on 2011-02-06
Added some screen shots on source forge: 
[https://sourceforge.net/project/screenshots.php?group_id=387510&ssid=144029](https://sourceforge.net/project/screenshots.php?group_id=387510&ssid=144029)

---

### Post by nvteighen on 2011-02-06
There's a big issue here: you haven't commited the code to the SVN repository so that eventually someone could contribute to the code.

(I'm not familiar with Sourceforge, so I can't help with the exact procedure to do this. Sorry)

---

### Post by cgroza on 2011-02-06
> **nvteighen said:**
> There's a big issue here: you haven't commited the code to the SVN repository so that eventually someone could contribute to the code.

(I'm not familiar with Sourceforge, so I can't help with the exact procedure to do this. Sorry)
I am not familiar either, but I will read some documentation. If anyone wants to contribute with code I would be happy.

---

### Post by cgroza on 2011-02-06
I have a SVN link:

[https://gecrit.svn.sourceforge.net/svnroot/gecrit](https://gecrit.svn.sourceforge.net/svnroot/gecrit)

If someone is interested I only need their username to give them permission on sourceforge.

---

### Post by cgroza on 2011-02-06
I uploaded the source in the SVN repository.

---

### Post by Hur Dur on 2011-02-06
I just gave it a try. I rather like it. The only problem I have with it is that when you press "Run This Program". a terminal comes up for a split-second and then disappears. Of course, this is a minor complaint, because you can always go to view - OS Shell, and chmod/run it from there. Also, you misspelled Python in the view tab. Again, a minor complaint. When you press Ctrl+F to find something, you can not exit out of it by clicking the X. You have to click cancel. On the other hand, there are a lot of useful features, like line numbering, syntax highlighting, and my favorite, the Python and OS shells. As for dependencies, it's pretty light. The only dependency problem I ran into was Python-wxWidgets. Compared to Abiword, which had an upwards of 10 dependencies I needed to install. The interface is easy to use, but it stays out of your way. I never find myself trying to look for a certain button. Unfortunately, it is not extremely light on resources, but it is not too heavy either. A lot of my complaints are just minor things, that are common in most beta programs. Overall, you've done a good job so far.

I've only tried it on Debian, I will try it on Arch later.

---

### Post by cgroza on 2011-02-06
> **Hur Dur said:**
> I just gave it a try. I rather like it. The only problem I have with it is that when you press "Run This Program". a terminal comes up for a split-second and then disappears. Of course, this is a minor complaint, because you can always go to view - OS Shell, and chmod/run it from there. Also, you misspelled Python in the view tab. Again, a minor complaint. When you press Ctrl+F to find something, you can not exit out of it by clicking the X. You have to click cancel. On the other hand, there are a lot of useful features, like line numbering, syntax highlighting, and my favorite, the Python and OS shells. As for dependencies, it's pretty light. The only dependency problem I ran into was Python-wxWidgets. Compared to Abiword, which had an upwards of 10 dependencies I needed to install. The interface is easy to use, but it stays out of your way. I never find myself trying to look for a certain button. Unfortunately, it is not extremely light on resources, but it is not too heavy either. A lot of my complaints are just minor things, that are common in most beta programs. Overall, you've done a good job so far.

I've only tried it on Debian, I will try it on Arch later.

Glad you like it. Thanks for the reports, I appreciate it. I will correct the spelling errors and will bind some events on those X buttons. The  Run button is still a dummy button, and if it works it is a bug :D. The changes will be available in the next release.

---

### Post by worksofcraft on 2011-02-07
I wanted to try it but it says:
```

Error: Wrong architecture 'i386'

```
How I get for 64-bit Ubuntu?

---

### Post by slavik on 2011-02-07
how does your text editor compare to others?

---

### Post by cgroza on 2011-02-07
> **worksofcraft said:**
> I wanted to try it but it says:
```

Error: Wrong architecture 'i386'

```How I get for 64-bit Ubuntu?

You need to force architecture.

---

### Post by cgroza on 2011-02-07
> **slavik said:**
> how does your text editor compare to others?

I am trying to focus on simplicity and clean menus. Trying to allow things with the minimum of possible clicks.

---

### Post by worksofcraft on 2011-02-07
> **cgroza said:**
> You need to force architecture.

... all the install options are grayed out in the .deb package installer :(

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182953&stc=1&d=1297113527[/IMG]

---

### Post by cgroza on 2011-02-07
> **worksofcraft said:**
> ... all the install options are grayed out in the .deb package installer :sad:



Please put the deb file in you home folder an then run this command:
```
dpkg -i --force-architecture deb_name_here
```

Thank you.

NOTE: This deb dodes not create a menu entry(still need to figure it  out). You can launch the program by pressing ALT+F2 and typing " gecrit "  and hitting enter.

---

### Post by cgroza on 2011-02-07
Triple post, sorry

---

### Post by cgroza on 2011-02-07
Triple post, sorry.

---

### Post by worksofcraft on 2011-02-07
> **cgroza said:**
> Please put the deb file in you home folder an then run this command:
```
dpkg -i --force-architecture deb_name_here
```

Thank you.

NOTE: This deb dodes not create a menu entry(still need to figure it  out). You can launch the program by pressing ALT+F2 and typing " gecrit "  and hitting enter.

Thanks... it works very nicely now and looks really pro :)

I like the indentation guides. I mostly want to edit C++ source code so I'm going to be experimenting with that.

I haven't explored any of gecrit's features yet but it would be cool if it has code folding and color coding and a facility to submit the source to a compiler and then take me straight to the error message and so on... but basic text editing is all I really need :)

---

### Post by cgroza on 2011-02-07
> **worksofcraft said:**
> Thanks... it works very nicely now and looks really pro :)

I like the indentation guides. I mostly want to edit C++ source code so I'm going to be experimenting with that.

I haven't explored any of gecrit's features yet but it would be cool if it has code folding and color coding and a facility to submit the source to a compiler and then take me straight to the error message and so on... but basic text editing is all I really need :)
Right now it only useful for python. This week I will try to code some file recognition and using that, pick a lexer(busy because of school, only 6 hours to do all my stuff). Thank you for trying it. I really appreciate it.

---

### Post by Pithikos on 2011-02-07
Well you could give it some cool features that can't be found on other editors.. for example live editing from pastebin.com, wiki syntax support, advanced search&replace(which usually only can be done via terminal). Just some ideas that would really make me excited about a new editor ;-)

---

### Post by cgroza on 2011-02-07
> **Pithikos said:**
> Well you could give it some cool features that can't be found on other editors.. for example live editing from pastebin.com, wiki syntax support, advanced search&replace(which usually only can be done via terminal). Just some ideas that would really make me excited about a new editor ;-)

Yes, these are good ideas, especially the pastebin.com. I will keep this in mine. Thank you for the ideas.

---

### Post by worksofcraft on 2011-02-07
> **cgroza said:**
> Yes, these are good ideas, especially the pastebin.com. I will keep this in mine. Thank you for the ideas.

I had a go at editing Python source code with gecrit and I think it is much better than anything else I've used and shall be using it exclusively for writing Python code from now on :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182978&stc=1&d=1297126347[/IMG]

What I really like is the clean intuitive user interface that isn't cluttered with unintelligible features.

Instead of trying to pack more into one product, I wonder if it could work as an imported "base class" for more specialized editors... so like you could have a gamut of customized editors for different languages and purposes without turning it all into one super heavy weight project?

---

### Post by cgroza on 2011-02-07
> **worksofcraft said:**
> I had a go at editing Python source code with gecrit and I think it is much better than anything else I've used and shall be using it exclusively for writing Python code from now on :)

What I really like is the clean intuitive user interface that isn't cluttered with unintelligible features.

Instead of trying to pack more into one product, I wonder if it could work as an imported "base class" for more specialized editors... so like you could have a gamut of customized editors for different languages and purposes without turning it all into one super heavy weight project?

Glad you like it, now i feel like I made something useful. This is still a beta so you should keep some backup somewhere just in case. I work alone on this and many bugs may be hidden. And the idea of using this as a base is not bad, in fact I should do this on the long run.

Thank you.

---

### Post by cgroza on 2011-02-07
I got some pastebin class that I can use in gecrit. Hope this feature will be out this week.

---

### Post by cgroza on 2011-02-08
I added support for [www.pastebin.com](www.pastebin.com) snippet submit. It collects some data from the user and then uploads the current document. Link to the latest deb:
[https://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download](https://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download)

---

### Post by cgroza on 2011-02-08
By tomorrow, I will get a syntax check feature. Wish me luck.

---

### Post by worksofcraft on 2011-02-08
> **cgroza said:**
> By tomorrow, I will get a syntax check feature. Wish me luck.

:shock:

I wish you luck...

oh and remember to split off a base class editor before it all becomes too complicated and intertwined ;)

---

### Post by cgroza on 2011-02-09
> **worksofcraft said:**
> :shock:

I wish you luck...

oh and remember to split off a base class editor before it all becomes too complicated and intertwined ;)

I think is still simple, I will put a feature or 2, and then put in in the "freezer".:D

---

### Post by cgroza on 2011-02-09
Ok, I got the check syntax function working. I am still working on it because sometimes it says there is no error. I believe it has something to do with the file saving. I uploaded it on sourceforge.
[https://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download](https://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download)

---

### Post by cgroza on 2011-02-10
Ok, I tested a bit on a longer time, and the memory consumption is rising very fast from 17.6MB to 20.9MB after opening a few tabs and pressing all possible buttons, and it seems to be steady like this. These values are plus the python interpreter memory itself.[http://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download](http://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download)

---

### Post by worksofcraft on 2011-02-10
> **cgroza said:**
> Ok, I tested a bit on a longer time, and the memory consumption is rising very fast from 17.6MB to 20.9MB after opening a few tabs and pressing all possible buttons, and it seems to be steady like this. These values are plus the python interpreter memory itself.[http://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download](http://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download)

I shouldn't worry about it. Python does have a good garbage collector... I heard it doesn't do garbage collection until it actually has to and so perhaps it simply hasn't seen any need to do that yet.. I mean why collect garbage when there are still gigabytes of unused space... right ?!

Is there any reason you suspect memory usage could become a problem ?

---

### Post by cgroza on 2011-02-11
> **worksofcraft said:**
> I shouldn't worry about it. Python does have a good garbage collector... I heard it doesn't do garbage collection until it actually has to and so perhaps it simply hasn't seen any need to do that yet.. I mean why collect garbage when there are still gigabytes of unused space... right ?!

Is there any reason you suspect memory usage could become a problem ?

So far no, but who knows what could arrive in the future. In the first days, I was worried about the memory increasing abruptly at each new action. I realized that it was probably python importing modules. drPython presents the same behavior. Thank you. Now I will put my head on working some new ideas. :D

---

### Post by cgroza on 2011-02-11
Just fixed some bugs in the way the editor is taking the file paths. The change will be available tomorrow.

---

### Post by cgroza on 2011-02-12
Fixed a bug in the Shell Emulators resizing when activated in full screen mode(they would not take all the space). 
Source Forge link:[https://sourceforge.net/projects/gecrit/files/gEcrit.zip/download](https://sourceforge.net/projects/gecrit/files/gEcrit.zip/download)
SoftPedia link: [http://mac.softpedia.com/get/Word-Processing/gEcrit.shtml](http://mac.softpedia.com/get/Word-Processing/gEcrit.shtml)

---

### Post by cgroza on 2011-02-13
OK, I got mass line  Indentation and Dedentation working. Now I will start working on some Autocompletion.
Wish me luck.
Available on sourceforge: [https://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download](https://sourceforge.net/projects/gecrit/files/gecrit_1.7.0.deb/download)

Thanks.

---

### Post by cgroza on 2011-02-14
Autocompletition is now function. Right now, it is activated on pressing Ctrl+Space, but this will change. Sometimes it fails to find the right word because I use diff_lib to get the best match. Well, I think it is decent. Available at:[https://sourceforge.net/projects/gecrit/files/gEcrit.zip/download](https://sourceforge.net/projects/gecrit/files/gEcrit.zip/download)

---

### Post by cgroza on 2011-02-16
Fixed a bug that caused the gEcrit to consume all the CPU cycles when running the terminal emulators.
Available at: [https://sourceforge.net/projects/gecrit/files/gecrit_1.8.0.deb/download](https://sourceforge.net/projects/gecrit/files/gecrit_1.8.0.deb/download)

---

### Post by cgroza on 2011-03-06
Posting after a few releases, a few new features were added!
[http://sourceforge.net/projects/gecrit/files/](http://sourceforge.net/projects/gecrit/files/)

---

### Post by cgroza on 2011-03-13
Just releases 18.5:
[http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
New features added and bugfixes.

---

### Post by cgroza on 2011-03-20
Just released 1.8.7:
[http://freshmeat.net/projects/gecrit](http://freshmeat.net/projects/gecrit)
New features added.

---

