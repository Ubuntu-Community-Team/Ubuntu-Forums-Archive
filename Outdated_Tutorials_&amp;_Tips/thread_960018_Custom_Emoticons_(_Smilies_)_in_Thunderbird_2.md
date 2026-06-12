---
title: "Custom Emoticons ( Smilies ) in Thunderbird 2"
date: 2008-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by baracuda68 on 2008-10-27
[SIZE=2]OK
Here is a HOWTO for adding Custom Animated Emoticons ( like "Incredimail") to your Email compositions,while using Thunderbird 2.0.x, that works well for me...

Most know that there are stock set of emoticons with TB2, provided that you have Edit>Account Settings>Composition & Addressing-"Compose Messages in HTML Format" enabled. But these are kind of plain and bland.

With a couple of extensions,you can also add custom smilies to your compositions.

You first must install MR Tech Toolkit (formerly Local Install) 6.0.1 at[https://addons.mozilla.org/en-US/thunderbird/addon/421](https://addons.mozilla.org/en-US/thunderbird/addon/421) for compatibility of the next extension.

Next you want to install Smilie Inserter 0.7.0 located at [https://addons.mozilla.org/en-US/thunderbird/addon/769](https://addons.mozilla.org/en-US/thunderbird/addon/769) or at [http://files.pegia.se/aofiohdf/smilie_inserter-0.7.0-tb.xpi](http://files.pegia.se/aofiohdf/smilie_inserter-0.7.0-tb.xpi).[IMG]https://addons.mozilla.org/en-US/firefox/images/p/993/943948800[/IMG]

Next is to find a database of smilies. I use [http://www.kde-look.org/](http://www.kde-look.org/) and select "Emoticon Themes" on the left side.
Download and unzip to a folder of choice, then select the folder with Smiley Inserter and voila! Custom animated smilies to _*annoy your friends and family*_. Like these> :KS:popcorn::guitar::lolflag:](*,)

Hope you enjoy Please comment.[/SIZE]

---

### Post by baracuda68 on 2008-11-01
*Bump* for the hell of it:)

---

### Post by jfl on 2009-08-23
Thanks !!!
Good info, worked the firdt time !!!

---

### Post by baracuda68 on 2009-08-23
Glad to hear.jfl, Glad you're happy!!

:guitar:

---

### Post by WinRiddance on 2011-01-24
When I tried to install the smilie inserter add-on I get an error that it is not
compatible with Thunderbird 3.1.7 .  Is there a smilie inserter that I can use?

Regards...

---

### Post by baracuda68 on 2011-01-24
> **WinRiddance said:**
> When I tried to install the smilie inserter add-on I get an error that it is not
compatible with Thunderbird 3.1.7 .  Is there a smilie inserter that I can use?

Regards...
[SIZE=2]Hi, WinRid... 
Since the author didn't make a version of Smiley Inserter for Thunderbird,beyond V.1.5.0,
You need to disable extension compatibility checking in TBird.[/SIZE]

 [SIZE=2]You can install the Mr Tech Toolkit extension from the link above, to disable checking,

 _Or_ if you are the type to tweak TBird's version of "about:config", you can go to Edit/Preferences/Advanced section/General tab, and press the "Config Editor" button. In the search field you can put "*extensions.checkCompatibility*" (Yes,_without_ the quotes). If anything shows up below that, you can click them to false.
If nothing shows up you can add it.[/SIZE]

[SIZE=2]Right-Click on a blank area of the page and select "New" in the menu  and select the data type as "Boolean" (Boolean is a "true" or "false"  type statement for those that don?t know), type the preference name as "*extensions.checkCompatibility*" and click ok. Another screen will popup with a select option of "True" or "False", Select "False" in this screen.
Others to add are "extensions.checkCompatibility.3.1" & "local_install.extensions.checkCompatibility" ,set all to false.[/SIZE]

[SIZE=2]After Smiley Inserter is installed, you will see a note saying "Not compatible with Thunderbird 3.1.7" in the extension list, but the add on is installed, and the preferences work fine! Then follow the instructions above to add the database, and voilà'!  Enjoy![/SIZE]

---

