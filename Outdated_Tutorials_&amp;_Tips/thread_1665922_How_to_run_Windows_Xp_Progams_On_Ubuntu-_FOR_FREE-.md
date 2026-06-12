---
title: "How to run Windows Xp Progams On Ubuntu- FOR FREE-  BEGGINERS"
date: 2011-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Bazzi313 on 2011-01-13
[COLOR=Black]Wine is a program that lets you run some Windows software on other operating systems.  With  Wine, you can install and run these applications just like you would in  Windows.[/COLOR]
  [COLOR=Black]
[/COLOR]
[COLOR=Black]* We Must Add wine the wineHQ PPQ [/COLOR]repository:
  Open the Software Sources menu by going to **Applications->Ubuntu Software  Center**, then selecting **Edit->Software Sources**. Choose the **Other  Software** tab and click **Add**.
Then, **copy and paste the line below**.
  [I]**ppa:ubuntu-wine/ppa**

[/I]**Installing Wine:**

  Once you have added the WineHQ PPA Repository, you are ready to install.
  *To get the most recent Wine 1.3 beta,  [click this link to install the wine1.3 package]("apt://wine1.3").*
 *To install the older, stable Wine 1.2 version,  [click this link to install the wine1.2 package]("apt://wine1.2").*
[COLOR=SeaGreen]( *If links don't work you can simply go to the ubuntu software centre ( Applications>Ubuntu Software Centre) and search for wine and install it from there)*[/COLOR]


**Alternative Command Line Instructions for Installing Wine:**

  It is also possible to add the Wine PPA and install via the terminal. This may be useful on Kubuntu, Xubuntu, and other Ubuntu derivatives.
  ***sudo add-apt-repository ppa:ubuntu-wine/ppa***
  Then update APT's package information by running '**sudo apt-get  update**'. You can now install Wine by typing '**sudo apt-get  install wine1.3**'.
  If you'd like to browse the PPA manually, you can [visit its Launchpad page]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa").




[SIZE=4]**How to use.**[/SIZE]

*After installing Wine You Download a program like you would for xp
*Then Go to the directory you have saved the installer in by default it is in downloads folder ( Home/downloads ), and right click it and select, open with wine/wine application etc.
[U][B]  IN-CASE IT DOES NOT WORK.
[/B][/U]If it dosnt work simply right click the file go to Permissions tab and then click allow executing, and it should work, this is also how to bypass and execute exe files :).

Credit: To WineHQ.com

COMMENT ON RESULTS HOPE I HELPED.

---

### Post by Bazzi313 on 2011-01-17
Hmm, No Comments i want to know if its working for people i know this is cheap but meh P:

---

### Post by judrbug on 2011-07-17
Thank you this really helped! :) Finally something I can completely follow.

---

### Post by geazzy on 2011-07-18
nice tutorial :)

---

