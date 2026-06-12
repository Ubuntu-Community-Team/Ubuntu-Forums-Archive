---
title: "substitution for Autohotkey - QT or GTK?"
date: 2015-09-28
forum: Programming Talk
---

### Post by simba4 on 2015-09-28
Hi there,

I am ~new to ubuntu but not new to computers.
Lately, I migrate from Windows to Ubuntu and I managing pretty well.

On Windows platform I used to script with a tool called _[Autohotkey]("http://www.autohotkey.com/")_.
Asking around for a substitute for the Ubuntu world, two names popped up: QT and GTK.

_[Reading  about the differences]("https://www.wikivs.com/wiki/GTK_vs_Qt")_, It seems that QT is the superior one, but that  is only my impression. For a more established opinion, I would like to  depend on your collective knowledge and experience.

I used to use  that _[Autohotkey]("http://www.autohotkey.com/")_ script language to control some stand alone  applications that lack some features or to automate some actions within  those applications.

For example, the attached picture shows  the screenshot of a stand_alone Windows trading application. I wrote a script to  perform an action on a specific combination of graph conditions (breach  or break).

I wonder if someone that is familiar with  that _[Autohotkey]("http://www.autohotkey.com/")_ can tell me which of the two (QT vs GTK) will be most  suitable for my purposes.


Thank you,


James

[IMG]http://www.broker.co.il/warehouse/userUploadFiles/Image/nigzarim7%282%29.jpg[/IMG]

---

### Post by TheFu on 2015-09-28
Qt and GTK are NOT what you think they are. They are cross-platform libraries for developers. Not very useful to end-users. There are bindings for many different languages, but mostly C/C++.

Don't use the GUI interface for things you want to remote control. Use the API or CLI interface - **expect** is the normal tool for that control on any Unix system.  You can also check out different testing tools - these provide inputs to programs and could be used for your needs. There are CLI and GUI versions of these. For example, if you want to control a website, that would use a different tool.

If you want to access 90% of the power in your Linux system, get away from the GUI and learn to write little scripts to automate things. Bash, Python, Ruby, Perl are the normal languages.

Also, you can visit "alternativeTo.net" to find GUI options.  (Teaching you to fish).
I suspect **autokey** is what you think you want. ;)

---

