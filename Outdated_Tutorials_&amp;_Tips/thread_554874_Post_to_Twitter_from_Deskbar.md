---
title: "Post to Twitter from Deskbar"
date: 2007-09-19
forum: Outdated Tutorials &amp; Tips
---

### Post by reda_ea on 2007-09-19
[SIZE="5"]**EDIT**
 I think this doesn't work anymore, because deskbar changed completely. Besides, deskbar regressed so much I'm not using it anymore, so someone else will have to rewrite this...
**/EDIT**[/SIZE]

Hi all

Just decided to try out [twitter]("http://twitter.com/reda_ea"), the only problem was that I couldn't find a good tool to use it from ubuntu.
the only good way I found is this
[http://philwilson.org/blog/2007/03/post-to-twitter-from-ubuntu-deskbar.html](http://philwilson.org/blog/2007/03/post-to-twitter-from-ubuntu-deskbar.html)
however, this requires you to compile certain libs installing their dependencies and everything

So I decided to write my own, based on the same idea but using the standard http methods, thus requiring no further installation

**EDIT**
use the attached *install.sh* script instead, download it in the same folder as the archive and run it
$ bash install.sh
give your username/password and you're done
**/EDIT**

you just need to extract the attached archive in
/home/*YOU*/.gnome2/deskbar-applet/handlers
and open the file and replace the username/password with your own

lots of things are still to be fixed, but it works

Enjoy

---

### Post by drsaamah on 2007-09-20
so after the files are extracted to the folder and the TWITTER_USERNAME and TWITTER_PASSWORD are replaced in the python code... what do we do then?

---

### Post by reda_ea on 2007-09-20
just type something in deskbar and you'll see an entry for twitter
select it and that's all

you may need to restart your deskbar OR remove the compiled .pyc
rm ~/.gnome2/deskbar-applet/handlers/deskbar-http-twitter.pyc
if you put the file in the folder before changing the code

this is still a test version, I'll be working more on this to improve it as I get more feedback about it

**EDIT**

[SIZE="3"]OR[/SIZE]

remove everything and use the installer script I just added : )

---

### Post by fedalmor on 2007-10-06
There's nothing to do: **it cause the Deskbar to crash** and automatically deselect two Compiz-Fusion plugins on the window decorator (to move windows)... exactly as the *"first"* non-HTTP version of deskbar-twitter... :(

But it could be 'cuz I use the **SVN version of python-twitter**...? :P Anyway, this happens on Feisty... because **Gutsy doesn't recognize it** as a deskbar handler... :(

---

### Post by Xtopher_Robin on 2007-11-02
Hmm.  Not working for me.  I tried the manual install as well as the install.sh file you created.  When I run the install file, it says installation complete, but I get nothing from my deskbar.  For the record, the python-twitter that you referenced never worked for me either.  And yes, I tried restarting the computer in leu of restarting deskbar (I couldn't figure out how to just restart it).  Any ideas?  I'd LOVE to twitter from the deskbar!

EDIT:
I thought I figured it out since you have to use the "modules-2.20-compatible" folder instead of the "handlers" folder, but I'm still getting nothing.  It's odd; non of the extensions for deskbar that I've installed will work, so it's not isolated to this one...

---

