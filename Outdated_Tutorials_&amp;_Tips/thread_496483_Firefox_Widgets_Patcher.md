---
title: "Firefox Widgets Patcher"
date: 2007-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by ElemonGW on 2007-07-09
INFORMATIONS OUT OF DATE! Until I update it, see [here]("http://elemongw.exofire.net/projects/linux/fwp") (still not proper, I need to update that as well but at least it is somewhat better than this) .

***About***
I present you a little script that will change your Firefox widgets to some which fit more with Ubuntu. To run it open the terminal and run
```
sudo sh /path/to/file/FirefoxWidgetPatcherinstall.sh
```

***Screenshots***
This is how Firefox Widgets will look after you have applied this patch:

**Text Fields**
[IMG]http://i168.photobucket.com/albums/u161/ElemonGW/Firefox%20Widgets%20Patcher/TextField.png[/IMG]

**Radio Buttons**
[IMG]http://i168.photobucket.com/albums/u161/ElemonGW/Firefox%20Widgets%20Patcher/RadioButton.png[/IMG]

**Drop Down Menus**
[IMG]http://i168.photobucket.com/albums/u161/ElemonGW/Firefox%20Widgets%20Patcher/DropDownMenu.png[/IMG]

**Checkboxes**
[IMG]http://i168.photobucket.com/albums/u161/ElemonGW/Firefox%20Widgets%20Patcher/CheckBox.png[/IMG]

**Buttons**
[IMG]http://i168.photobucket.com/albums/u161/ElemonGW/Firefox%20Widgets%20Patcher/Button.png[/IMG]

***Credits***
Osmo Salomaa for designing these widgets.

[Download Firefox Widgets Patcher Version 1.1]("http://elemongw.googlepages.com/FirefoxWidgetPatcherinstall_rev1.sh")

[center]***Downloads Archive***[/center]

[Download Firefox Widgets Patcher Version 1]("http://elemongw.googlepages.com/FirefoxWidgetPatcherinstall.sh")

[center]***Changelog***[/center]

**21-7-2007** Firefox Widgets Patcher Version 1.1
# Fixed a bug where some buttons were not correctly displayed.

**15-7-2007** Firefox Widgets Patcher Version 1
# First public release.


[Homepage]("http://elemongw.awardspace.com/?q=projects/linux/fwp")

---

### Post by ElemonGW on 2007-07-20
Never mind, I decided to update it.

---

### Post by coolglobal on 2007-07-22
Well done, I would like to commend you on an excellent patch.  The other patch was unsuccessful in my case.

---

### Post by Gausian on 2007-07-22
yeah, awesome job.  1 easy terminal command and ....... done.

---

### Post by andrek on 2007-07-22
Yet another Firefox Widgets Patcher?
Anyway, it doesn't work for me since I'm using Iceweasel ( script should has been adapted to few modifications of firefox, like Iceweasel or Swiftfox..).
The other script which was posted here does work with Iceweasel though.

---

### Post by ElemonGW on 2007-07-23
> **andrek said:**
> Yet another Firefox Widgets Patcher?
Anyway, it doesn't work for me since I'm using Iceweasel ( script should has been adapted to few modifications of firefox, like Iceweasel or Swiftfox..).
The other script which was posted here does work with Iceweasel though.

I guess that Iceweasel 's res folder is not locates @ /usr/lib/mozilla-firefox/res/ (where the script applies the patch by default). So, the only thing you have to do is open the script with the text editor you use and change all the references of that folder from /usr/lib/mozilla-firefox/res/ to the right folder for your case.

---

### Post by kostkon on 2007-07-23
Good work, ElemonGW!

---

### Post by crjackson on 2007-08-07
Once applied, does this patch do all the same changes the "Program" version is supposed to, or are some areas of modification not included?

In particular, I hate the way the google home page looks, and I'd love to see that thing fixed.

---

### Post by fatsheep on 2007-08-07
> **coolglobal said:**
> Well done, I would like to commend you on an excellent patch.  The other patch was unsuccessful in my case.
What do you mean by unsuccessful?  It didn't install?  It distorts your browser?  What?  Please report all bugs in the original topic.

> **ElemonGW said:**
> **About**
Because the other one didn't (completely) worked for me (and for others too). 


If you had problems then report them.  Please don't start over where I started months ago.  Look at my revisions, there have been significant improvements to the CSS in these widgets and the installation script has proved to be flawless.  

> Also, because the other one is a program, so it will have bugs.

The installation script that I have hasn't had any problems.  I have made superficial changes to it but the methods used have remained the same since the beginning of the Firefox Widgets back in February.  In that time I haven't received any complaints about the installation itself.  Infact, my installation script is a bash script just like your's.  Yes it's larger, can uninstall the widgets as well as install them, can install to many different browser paths (not just the default firefox one), and has a graphical frontend but it's still a bash script like your's.

However, that is besides the point.  The point is, I already have a reliable installation script with a GUI.  You have provided the original installation script which is actually the same one I rewrote to make mine.  We should be able to work together on perfecting the CSS.  The installation script is already done and it's just about flawless as I said.  If there are problems in the CSS then you should report them to me.  If you find a way to patch a bug, let me know.  However, **please do not reinvent the wheel** when much of the work you are probably about to embark on has already been done.  Start from where I am now and we can work together and perfect the widgets.

I don't mean to steal your thunder but I just don't see the point of starting another project.

---

### Post by ElemonGW on 2007-08-10
> **fatsheep said:**
> If you had problems then report them.
Hrm....
> Buttons and checkboxes are correctly changed. Drop down menus change as well but not correctly, as the button at the right remains the default and doesn't become the one with to arrows. Text fields are converted correctly too, but in some sites the default ones appear. Finally, no problem with radio buttons too. That's all :)
Reported it about a month ago.

> **fatsheep said:**
> Please don't start over where I started months ago.  Look at my revisions, there have been significant improvements to the CSS in these widgets and the installation script has proved to be flawless.
I don't say the opposite, but as I told before it didn't worked for me. You didn't replied to my report, so I decided to, being based on the original, create one for my own. Then, as I read that others had problem with yours too, I decided to share it with the community.


> **fatsheep said:**
> The installation script that I have hasn't had any problems.  I have made superficial changes to it but the methods used have remained the same since the beginning of the Firefox Widgets back in February.  In that time I haven't received any complaints about the installation itself.  Infact, my installation script is a bash script just like your's.  Yes it's larger, can uninstall the widgets as well as install them, can install to many different browser paths (not just the default firefox one), and has a graphical frontend but it's still a bash script like your's.

lol, I thought I have deleted that. It is something I am ashamed of telling ;) . I understood my mistake immediately, but it seems I forgot to remove it. Anyway, I now changed the first post, taking the one from my site which was up-to-date.
PS: To be honest, it is written in python so it is not completely a script, but anyway ;) .

---

### Post by walkerk on 2007-08-23
> **fatsheep said:**
> What do you mean by unsuccessful?  It didn't install?  It distorts your browser?  What?  Please report all bugs in the original topic.



If you had problems then report them.  Please don't start over where I started months ago.  Look at my revisions, there have been significant improvements to the CSS in these widgets and the installation script has proved to be flawless.  



The installation script that I have hasn't had any problems.  I have made superficial changes to it but the methods used have remained the same since the beginning of the Firefox Widgets back in February.  In that time I haven't received any complaints about the installation itself.  Infact, my installation script is a bash script just like your's.  Yes it's larger, can uninstall the widgets as well as install them, can install to many different browser paths (not just the default firefox one), and has a graphical frontend but it's still a bash script like your's.

However, that is besides the point.  The point is, I already have a reliable installation script with a GUI.  You have provided the original installation script which is actually the same one I rewrote to make mine.  We should be able to work together on perfecting the CSS.  The installation script is already done and it's just about flawless as I said.  If there are problems in the CSS then you should report them to me.  If you find a way to patch a bug, let me know.  However, **please do not reinvent the wheel** when much of the work you are probably about to embark on has already been done.  Start from where I am now and we can work together and perfect the widgets.

I don't mean to steal your thunder but I just don't see the point of starting another project.


I completely agree. Work with him too improve on his script where possible but don't try to take over the project. He's doing the leg work with the widgets and his scripts worked well for many users.. If you have issues PM him to report errors.. :/

---

### Post by ST.x on 2007-09-16
would this work with Swiftweasel 64bit?

---

### Post by ElemonGW on 2007-11-20
[Firefox Widgets Patcher Version 2 is Out!]("http://elemongw.exofire.net/blog/2007/11/20/firefox_widgets_patcher_version_2_is_out%21")

---

