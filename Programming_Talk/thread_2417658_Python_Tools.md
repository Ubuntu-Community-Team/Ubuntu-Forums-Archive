---
title: "Python Tools"
date: 2019-04-25
forum: Programming Talk
---

### Post by radu19842 on 2019-04-25
Good evening , wen i was using windows i had all the aplications/ide's,etc. for writing a complete job, or better said developing a game/application from zero to finish , but now as i am on xubuntu 18.04 i started to enjoy it more by the day and in the meanwhile i want to know , from you my friends witch have experience developing in python , witch are (all) the best tools to develop , program , a game or an application in python under xubuntu cause i'm kinda in a foggy state lol ! :D A list with all i need for python under xubuntu cause i am never going back on that damn windows again.A good evening to all of you ! ):P
Thank you ! :)

---

### Post by Crafty Kisses on 2019-04-25
This should get you started: [https://docs.python-guide.org/starting/install3/linux/](https://docs.python-guide.org/starting/install3/linux/)

If you're missing any dependencies while you're building via "import" it will tell you, and you can pip it usually.

---

### Post by oldfred on 2019-04-25
See:
[https://wiki.python.org/moin/GuiProgramming](https://wiki.python.org/moin/GuiProgramming)

I dabble in python and use Geany, but have to change settings to use spaces, not tabs.
I have used glade for gtk, but now use qt5 designer for qt.

---

### Post by freemedia2018 on 2019-04-25
I just use leafpad. But that's only for code that is fewer than 2000 loc.

Geany would be the next best thing-- it lets you do find and replace on every open tab at once (how cool is that?)

---

### Post by ambidextrous2 on 2019-04-25
Visual Studio Code is free and available for all platforms.

---

### Post by radu19842 on 2019-04-25
Good morning , thank you all for your advices , helps me allot ! All the best ! :)

---

### Post by freemedia2018 on 2019-04-26
> **ambidextrous2 said:**
> Visual Studio Code is free and available for all platforms.

Be sure to [disable telemetry so it doesn't spy on you]("https://www.reddit.com/r/privacy/comments/80d8wu/just_realised_that_visual_studio_code_sends/").

---

### Post by radu19842 on 2019-04-29
Thank you all , since i have started using xubuntu i learned lots of new stuff . Still i want to ask you (if you do not mind) giving me a list if you will , witch contains only the best and stable applications for python that are aimed at :
- Software development
- GUI develompent
It's just that is a bit confusing for me as a beginner in ubuntu and i hope you understand ! :)
Thank you so much and have a nice day ! ;)

[B]Later Edit

[/B]I have just installed trough terminal the folowing :

> [COLOR=#22292F][FONT=Menlo]sudo apt update[/FONT][/COLOR][COLOR=#22292F][FONT=Menlo]
[/FONT][/COLOR]> [SIZE=1]sudo[/SIZE][COLOR=#22292F][FONT=Menlo] apt install software-properties-common[/FONT][/COLOR]
Then 
> [COLOR=#22292F][FONT=Menlo]sudo add-apt-repository ppa:deadsnakes/ppa[/FONT][/COLOR]
After that
> [COLOR=#22292F][FONT=Menlo]sudo apt install python3.7[/FONT][/COLOR]
Then i checked version
> [COLOR=#22292F][FONT=Menlo]python3.7 --version[/FONT][/COLOR]
Output
> [COLOR=#22292F][FONT=Menlo]Python 3.7.3[/FONT][/COLOR]
Next 
> [COLOR=#22292F][FONT=Menlo]sudo apt update[/FONT][/COLOR]
Then
> [COLOR=#22292F][FONT=Menlo]sudo apt install python3-pip[/FONT][/COLOR]
After that
> [COLOR=#22292F][FONT=Menlo]pip3 --version[/FONT][/COLOR]
Output
> pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)
And now what to do , i am not sure i installed pip correctly for python 3.7.3 , now what to install , kinda stuck here :( ? Oh and the above applications request still stands cause i really need them ! :( 
Thank's again to all !

---

