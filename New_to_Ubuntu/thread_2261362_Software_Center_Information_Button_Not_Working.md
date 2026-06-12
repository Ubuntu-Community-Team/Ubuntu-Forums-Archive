---
title: "Software Center Information Button Not Working"
date: 2015-01-18
forum: New to Ubuntu
---

### Post by srJncLk on 2015-01-18
Hi all,
I am a bit new to ubuntu. I was using mint-cinnamon but my fairly old pc were having some speed issues. At first i started to use xfce and lxde on mint after that i decided to use a pure lxde distro.
I've installed Lubuntu 14.10 today and then started browsing applications from software center.
There was a problem.
Information button which is placed at the bottom of the window isn't working. I've checked many programs from different categories but all were the same.
Information button doesn't give me any information about listed programs, by the wat there is nothing wrong with installing/uninstalling any software.
I've searched forum, launchpad and google but couldn't find any issue like mine.
Can you use information button?

Thanks for your help.

---

### Post by Holger_Gehrke on 2015-01-18
Were you offline or on a **very **slow internet connection when this happened ? The 'Software Center' doesn't have all the information on your PC, it gets most of it from the net. The stuff it gets as 'Information' on a program is on the order of 1 MB including screenshot(s) in png-format. You can find the stuff it gets in '~/.cache/software-center' (unless that's changed since Ubuntu 12.04, which I am still using).

---

### Post by srJncLk on 2015-01-18
I am using 8mbit DSL connection and fully online all the time.
I checked .cache folder under my home directory but culdn't find software-center.

I am adding screenshots before and after clicking information button.
Please look at the category icon, it becomes like an help icon after clicking information.
But there is no infornation.

[ATTACH=CONFIG]259336[/ATTACH]
[ATTACH=CONFIG]259335[/ATTACH]

---

### Post by Holger_Gehrke on 2015-01-18
Hm, that looks a bit different from the software-center I know (and rarely ever use). Never mind the fact that I don't read Turkish ... In the old (Ubuntu 12.04) software-center, you click on a title in the list, than two buttons are added to the item in the list, one for getting more information and one for installing or uninstalling. If you click on the information button, A new page with detailed information is shown. (See attached screenshots)
[ATTACH=CONFIG]259341[/ATTACH][ATTACH=CONFIG]259340[/ATTACH][ATTACH=CONFIG]259339[/ATTACH]

And a small tip: when publishing screenshots on an international forum like this one, it can be a good idea to set programs to temporarily use non-localized messages. You can do this by starting the program from the command line and putting 'LC_ALL=C ' before the command, for example 'LC_ALL=C software-center' will give you the software-center in the original language.

---

### Post by srJncLk on 2015-01-18
Sorry for not changing my local language. Here the English screenshots.
[ATTACH=CONFIG]259342[/ATTACH][ATTACH=CONFIG]259343[/ATTACH]
Woow it worked. I think it is a language specific problem. I should submit a report for it.
But before opening this thread i changed my system language and it hadn't worked that time.
Now it works, strange.
Anyway, thanks for your help.

---

