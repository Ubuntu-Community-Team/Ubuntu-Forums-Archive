---
title: "set rightclick context menu to my keyboard's &quot;multi_key&quot;"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by kiwi_kirsch on 2014-04-17
i am an absolute beginner with ubuntu. yes, i confess to have been one of those win'xp idiots until the end of its support a week ago. a friend got me to try out xubuntu. and i LOVE it.

as i am very much into keyboard usage, i am partially fighting, partially succeeding with setting up my xubuntu keyboard settings to what i need. i do own a logitech keyboard named k270 with a terribly useful "multi_key" for context menues. which won't show up on my xubuntu 13.10 with a hell of consistency.

i already ixquicked this matter for days, but did not find anything *helpful to me* - due to little experience with xubuntu's insides so far. i am a bit of a nerd, i'm afraid, but still too unexperienced with my new system's terminal command syntax and anatomy altogether.

HOW ON EARTH can i tell this key to pop up EXACTLY what a right mouse click would show me?!

can someone maybe spell me the command for that settings/keyboard/shortcuts thing where i at least figured the name of that guy, being "multi_key"?

this is the key i am talking about: [IMG]http://i.imgur.com/KHmSQ3W.jpg[/IMG]

i tried xkeycaps which doesn't even show any response to this key if pressed (but to ANY other key, though) and i failed to feel safe or patient enough to try understanding any of those loooooooong manuals otherwise.. :(

heeelp.. i need somebody.. 

;)

---

### Post by amanchesterman on 2014-04-17
This isn't a complete answer to your question but it may help to establish that the key is actually working.
On my Xubuntu default install on a Dell laptop, the 'multi key' as you call it (actually the 'menu' key I think) works perfectly: it calls up the context menu on the desktop.
If you click on (main menu) > Settings Manager > Keyboard > Application Shortcuts tab it lists existing keyboard shortcuts and allows you to add more. Click on 'add', choose a simple command (e.g. 'firefox' to launch Firefox) and then press the menu key to assign that action to it. If it works, you can then delete that shortcut: at least you will have established that the menu key is working OK.

---

### Post by whitesmith on 2014-04-17
This may help you. [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
This tutorial was originally posted by a forum member whose handle I can't instantly recall.

---

### Post by kiwi_kirsch on 2014-04-17
thank you so much, both!!! happy about every response =)))

the key *does* actually work, and that settings/keyboard/shortcut-thing is actually exactly where i figured that my system feels like calling that key "multi_key" =) it is placed right hand of "space", the (i think what you refer to?) "menu key" -showing the windows logo and being recognized as Super_L- has already been successfully set to open the main menu, meanwhile i had to change other shortcuts containg super_L as my main menu always popped up even if i meant to open the terminal win "Super_L + T" only =D blabla. sorry. ahem. anyway: it is working, and it provides my system with its "multi_key" identity, yet i have no clue how to "exo-open blabla" or "xfce4-blabla" or "whatever" that key so that it'd finally open a proper right click context menu. if i remember right, it has never owned that function, not even before i began adjusting (and deleting) shortcuts i'd use or i would only use by accident ;D

that mouse link seems to provide me with a very useful path where my so-much-wanted command might be hidden! yay! thank you so much! i'll have look into that. i'll post feedback as soon as i have results. i'm afraid i'll try it now although it's almost 2am and i've had a very long and hard day.. cross your fingers, please =D

[grammar edit]

---

### Post by kiwi_kirsch on 2014-04-17
hmm. decided to listen to my pillow, first. thank you! =)

---

### Post by kiwi_kirsch on 2014-04-18
having had another pretty computerless day, i am now sitting in bed with my "small dell" (netbook) on my lap and figured the seemingly EXACT SAME key on my netbook, same print, same position on keyboard between "alt gr" and "strg" [latter is "ctrl" on english speaking keyboards]. it does EXACTLY what i wish my abovementioned Multi_Key of my "big dell" would do!! trying to trace the difference between both keys, i soon figued this one's indeed called "Menu" like amanchesterman had mentioned, which i had mistaken as "the key for the menu", being super_L. why the ***k do keyboards have to be THIS ***k*** different??!

Question: is there a chance to teach my logitech k270 to spit out "Menu" instead of "Multi_key" if pressed?

Otherwise: is there a way to teach my "big dell"s xubuntu to translate that "Multi_key" into "Menu" if pressed?

i can very well imagine i'm the threehundred-seventy-ninth idiot asking that, i am serioulsy sorry if so :(

[COLOR=#800080]edit: i think i finally found my own answer, and the best part of it: it's in my own mother tongue, which is helpful as i am new to ubuntu =D
[http://wiki.ubuntuusers.de/Xmodmap](http://wiki.ubuntuusers.de/Xmodmap)[/COLOR]

---

### Post by kiwi_kirsch on 2014-04-21
i got it &#8211; half.

i finally got a rightclick menu by editing the xmodmap:

keycode 135 = Menu Menu Menu Menu

i now get a context menu - *to where the mouse is pointing!!* one might say "yes, of course, isn't that what you said?" erm, and yes it seems it actually IS.. but.. but..

isn't thee a chance to get a context menu  FOR THE THING THE FOCUS IS ON? e.g. the jpg i just chose in my filemanager (Thunar) using keyboard instead of mouse, which i would now like to "open with.. gimp" or "open with.. flickr uploader" or whatever.

i had no clue there's a reason to doubt that the *right click on my mouse* will pop up a menu where the *mouse* is and a **keyboard menu key** would pop up a menu where i chose the **focus** to be, using **arrow keys**.

is there a chance?

[IMG]http://smilies.kiwikirsch.de/worf.gif[/IMG]

---

