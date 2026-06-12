---
title: "HOWTO: Nicer Firefox Form Widgets"
date: 2005-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by majikstreet on 2005-10-29
I did not write this howto, I simply made sure it worked for breezy.

[http://ubuntuforums.org/showthread.php?t=44110&highlight=firefox+widgets](http://ubuntuforums.org/showthread.php?t=44110&highlight=firefox+widgets)

good luck,
majikstreet

[color=green][b]PLEASE READ:
If you are using firefox 1.5 installed any way, please see the post directly below me ([http://ubuntuforums.org/showpost.php?p=520822&postcount=2](http://ubuntuforums.org/showpost.php?p=520822&postcount=2)) for instructions. These fix an issue with some buttons being a very light text on a beige button! - majikstreet
[/b][/color]
thanks, majikstreet

---

### Post by ow50 on 2005-11-25
I made made my own version of the firefox/xulrunner forms. It resembles quite closely the ones linked to in the first post of this thread. I modified the radio- and checkbutton images.

The forms package is at
[http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz](http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz).

Read the "INSTALL" file in the package.

Screenshot:
[[IMG]http://img498.imageshack.us/img498/418/kuvakaappausgoogletarkennettuh.th.png[/IMG]](http://img498.imageshack.us/my.php?image=kuvakaappausgoogletarkennettuh.png)

Other form widgets that apparently work:
[Winterfox](http://clear.com.ua/en/projects/firefox/winterfox)
[PrettyWidgets (OS X)](http://emps.l-c-n.com/articles/94/)

---

### Post by majikstreet on 2005-12-04
outdated.

---

### Post by royg1234 on 2005-12-11
there's a slightly annoying side effect on some sites where buttons have white text on beige-ish buttons.  See screenshots:

[INDENT]
bad:
[INDENT][http://www.geocities.com/roygullem/widget_facebook.png](http://www.geocities.com/roygullem/widget_facebook.png)
[http://www.geocities.com/roygullem/widget_npr.png](http://www.geocities.com/roygullem/widget_npr.png)[/INDENT]
good:
[INDENT][http://www.geocities.com/roygullem/widget_facebook_epiphany.png](http://www.geocities.com/roygullem/widget_facebook_epiphany.png)
[http://www.geocities.com/roygullem/widget_npr_epiphany.png](http://www.geocities.com/roygullem/widget_npr_epiphany.png)[/INDENT]
[/INDENT]

---

### Post by benplaut on 2005-12-11
[QUOTE=royg1234]there's a slightly annoying side effect on some sites where buttons have white text on beige-ish buttons.  See screenshots:

[INDENT]
bad:
[INDENT][http://www.geocities.com/roygullem/widget_facebook.png](http://www.geocities.com/roygullem/widget_facebook.png)
[http://www.geocities.com/roygullem/widget_npr.png](http://www.geocities.com/roygullem/widget_npr.png)[/INDENT]
good:
[INDENT][http://www.geocities.com/roygullem/widget_facebook_epiphany.png](http://www.geocities.com/roygullem/widget_facebook_epiphany.png)
[http://www.geocities.com/roygullem/widget_npr_epiphany.png](http://www.geocities.com/roygullem/widget_npr_epiphany.png)[/INDENT]
[/INDENT][/QUOTE]

yeah, i confirm that...

---

### Post by ow50 on 2005-12-12
Thanks for the feedback. The button text issue is fixed. I also made some other minor adjustments. There's now a changelog in the package if you're interested in the details.

---

### Post by royg1234 on 2005-12-14
[QUOTE=ow50]Thanks for the feedback. The button text issue is fixed. I also made some other minor adjustments. There's now a changelog in the package if you're interested in the details.[/QUOTE]

Thanks!  You're a champion.

---

### Post by benplaut on 2005-12-14
[QUOTE=ow50]Thanks for the feedback. The button text issue is fixed. I also made some other minor adjustments. There's now a changelog in the package if you're interested in the details.[/QUOTE]

i uninstalled using instructions above, then reinstalled... still broken :(

<<edit>>
scratch that, it works!

---

### Post by ow50 on 2005-12-14
I updated the package. No new content, but different installation. For better future compatibility, the custom stuff is now to be appended to the existing Firefox's forms.css. This way I don't need to keep up with whatever changes the Firefox devs choose to make to the official forms.css.

I updated the second post. Maybe majikstreet can update the third post as well.

---

### Post by zachtib on 2005-12-19
this didn't work for me (the intructions for ff1.5 from wiki) The form buttons still look the same

---

### Post by ow50 on 2005-12-19
[QUOTE=zachtib]this didn't work for me (the intructions for ff1.5 from wiki) The form buttons still look the same[/QUOTE]
Perhaps you used majikstreet's outdated instructions (third post). If so, uninstall according to the third post and then reinstall according to the second post. I added wiki-compatible instructions to the second post.

---

### Post by benplaut on 2005-12-19
found something broken: use the search-within-page tool (press /), and look at the text box. happens for some other boxes, too

---

### Post by zachtib on 2005-12-19
[QUOTE=ow50]Perhaps you used majikstreet's outdated instructions (third post). If so, uninstall according to the third post and then reinstall according to the second post. I added wiki-compatible instructions to the second post.[/QUOTE]

a-ha works great now, thanks

---

### Post by zachtib on 2005-12-19
[QUOTE=benplaut]found something broken: use the search-within-page tool (press /), and look at the text box. happens for some other boxes, too[/QUOTE]
ive noticed this too

---

### Post by majikstreet on 2005-12-19
Sorry guys! I hadn't noticed that this thread was updated... I need to subscribe to it :)

Anyway, I updated my post, and I have updated it on my computer.. I don't remember any of the websites with the white on beige buttons.. But, I can say that I have seen them too...

majikstreet

---

### Post by ow50 on 2005-12-19
Updated.

[QUOTE=benplaut]found something broken: use the search-within-page tool (press /), and look at the text box. happens for some other boxes, too[/QUOTE]
Madness! Being an Epiphany user myself I had no idea of the bizarre widgetry practised by Firefox. I thought the forms.css file affected only how web pages are displayed. Either way, it was an easy fix. I assume the "some other boxes" meant text entries; those should all be fixed now.

---

### Post by majikstreet on 2005-12-19
o_O so that's why the stumble upon box is messed up... will update my computer :)

---

### Post by veloct on 2005-12-19
I installed it and it was fine until I looked at the properties for the bookmarks, text box was too small to see text so I uninstalled.  Otherwise it was nice.

---

### Post by ow50 on 2005-12-19
[QUOTE=veloct]I installed it and it was fine until I looked at the properties for the bookmarks, text box was too small to see text so I uninstalled.  Otherwise it was nice.[/QUOTE]
This is exactly what should be fixed now; see two posts up. Or is the text still small somewhere?

---

### Post by veloct on 2005-12-19
[QUOTE=ow50]This is exactly what should be fixed now; see two posts up. Or is the text still small somewhere?[/QUOTE]

Nope that was it, reinstalled it and it's working nicely. Thanks, great job.

---

### Post by benplaut on 2005-12-20
i needed to uninstall using majik's directions, but they're gone... how do i get rid of the old one?

:(

---

### Post by ow50 on 2005-12-20
[QUOTE=benplaut]i needed to uninstall using majik's directions, but they're gone... how do i get rid of the old one?[/QUOTE]
Actually the uninstall instructions haven't changed, so the second post uninstall instructions work. It's just a matter of restoring from the backup and removing the form widget directory. I was mistaken about that in a previous post.

---

### Post by Juippisi on 2005-12-20
[QUOTE=ow50]**For Firefox 1.5 users:**

I made made my own version of the firefox forms for Firefox 1.5. It resembles quite closely the ones linked to in the first post of this thread. I modified the radio- and checkbutton images.

The forms package is at
[http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz](http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz).

**Installation instructions for wiki readers who used the tarball from mozilla.org**
(Works with [http://wiki.ubuntu.com/FirefoxNewVersion](http://wiki.ubuntu.com/FirefoxNewVersion))

Installation:
```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /opt/firefox/res/forms.css /opt/firefox/res/forms.css.bak
cat firefox-form-widgets-ots/res/forms-extra.css | sudo tee --append /opt/firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets-ots/res/form-widgets /opt/firefox/res
rm -rf firefox-form-widgets-ots
```

Uninstallation:
```
sudo rm -rf /opt/firefox/res/form-widgets
sudo cp /opt/firefox/res/forms.css.bak /opt/firefox/res/forms.css
```

**Installation instructions for Dapper users and those who backported their firefox from Dapper**

Installation:
```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
cat firefox-form-widgets-ots/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets-ots/res/form-widgets /usr/lib/mozilla-firefox/res
rm -rf firefox-form-widgets-ots
```

Uninstallation:
```
sudo rm -rf /usr/lib/mozilla-firefox/res/form-widgets
sudo cp /usr/lib/mozilla-firefox/res/forms.css.bak /usr/lib/mozilla-firefox/res/forms.css
```

Screenshot:
[[IMG]http://img498.imageshack.us/img498/418/kuvakaappausgoogletarkennettuh.th.png[/IMG]](http://img498.imageshack.us/my.php?image=kuvakaappausgoogletarkennettuh.png)

Other form widgets that apparently work with Firefox 1.5:
[Winterfox](http://clear.com.ua/en/projects/firefox/winterfox)
[PrettyWidgets (OS X)](http://emps.l-c-n.com/articles/94/)[/QUOTE]

And doesn't Firefox 1.5 seek a style from your GTK-theme to use in forms and other buttons? Ok, Gnome uses Metacity, but you can change your GTK-style by editing ~/.gtkrc and ~/.gtkrc-2.0 files. 
Also that "Widgets-from-themes" is possible, as you mentioned.

---

### Post by ow50 on 2005-12-20
[QUOTE=Juippisi]And doesn't Firefox 1.5 seek a style from your GTK-theme to use in forms and other buttons?[/QUOTE]
Not that I know. It would be good if it did.

[QUOTE=Juippisi]Ok, Gnome uses Metacity, but you can change your GTK-style by editing ~/.gtkrc and ~/.gtkrc-2.0 files.[/QUOTE]
Metacity is a window manager. I don't see what a window manager would have to do with web page form widgets. Changing the GTK theme via whatever has no effect on web page form widgets.

[QUOTE=Juippisi]Also that "Widgets-from-themes" is possible, as you mentioned.[/QUOTE]
I don't know what you're referring to.

It appears either you're confusing application widgets with web page form widgets or alternatively you know some superior way to get native widgets on web pages that you're not telling us.

---

### Post by majikstreet on 2005-12-23
here's a little issue I found: if you don't remove the .tar.gz file, the newer files will be named whatever.tar.gz.1 etc... so DELETE the tar.gz file after the installation :)

---

### Post by Adrenal on 2005-12-30
Hi, I'm seem to be having a problem with these widgets. Basically, my gnome-theme is a dark one, grey backgrounds, white text(easy on the eyes).
However, this widgets transform all text boxes to white, while retaining the inherent colour of the system font.
Ergo, when posting on forums, such as this one, I am writing white text on a white background.
Is there anyway to make the text default to black, or change the colour of a text box?

---

### Post by kaamos on 2005-12-30
[QUOTE=ow50]**For Firefox 1.5 users:**

I made made my own version of the firefox forms for Firefox 1.5. It resembles quite closely the ones linked to in the first post of this thread. I modified the radio- and checkbutton images.[/QUOTE]

Works like a charm! Thanks.

---

### Post by ow50 on 2005-12-30
[QUOTE=Adrenal]Hi, I'm seem to be having a problem with these widgets. Basically, my gnome-theme is a dark one, grey backgrounds, white text(easy on the eyes).
However, this widgets transform all text boxes to white, while retaining the inherent colour of the system font.
Ergo, when posting on forums, such as this one, I am writing white text on a white background.
Is there anyway to make the text default to black, or change the colour of a text box?[/QUOTE]
I tried a random dark theme from GNOME-Look.org and got white text on black background in all text boxes.

The code in the forms-extra.css file does not define text box colors, only borders, margins and paddings. Here's the relevant code
```
/* Text inputs */

input[type=text],
input[type=password],
input:not([type]),
textarea {
  border:1px solid ThreeDShadow;
  margin: 2px;
  padding: 3px 3px;
}
```

So if there's a problem, it could be in Firefox itself (Firefox's forms.css file).

---

### Post by ember on 2006-02-18
I like these pretty much, yet I had to uninstall them, because some buttons got very weird, for example the login-button on [http://www.gothic-chat.de]("http://www.gothic-chat.de") got grey instead of the dark-blue look it normally has. 
And e.g. on the page of my bank ([https://bankingportal.sparkasse-karlsruhe.de/banking/?BLZ=66050101]("https://bankingportal.sparkasse-karlsruhe.de/banking/?BLZ=66050101")), the login-boxes moved to a place underneath the text instead of their standard right placing.

---

### Post by ow50 on 2006-02-18
> **ember]I like these pretty much, yet I had to uninstall them, because some buttons got very weird, for example the login-button on [http://www.gothic-chat.de]("http://www.gothic-chat.de") got grey instead of the dark-blue look it normally has.[/QUOTE]
This could easily be fixed by removing some "!important" statements, but I find that some some sites have such hideous looking widgets that it's better to force them all to a standard look. However, for those that might like it, replace the res/forms-extra.css in the tarball  with
```
/* Text inputs */

input[type=text],
input[type=password],
input:not([type]),
textarea {
  border:1px solid ThreeDShadow said:**
> ,
input[type="submit"],
input[type="reset"],
button,
select{
  color: ButtonText;
  background-color: Window;
  background: Window url("form-widgets/button.png") repeat-x bottom right;
  border: 2px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-right-colors: ThreeDShadow Window;
  -moz-border-bottom-colors: ThreeDShadow Window;
  -moz-border-left-colors: ThreeDShadow ThreeDHighlight;
  margin: 2px;
  padding: 0px 1px;
  -moz-border-radius: 1px;
}

input[type="button"]:hover,
input[type="submit"]:hover,
input[type="reset"]:hover,
button:hover {
}

/* Radio buttons */

input[type="radio"] {
  width: 13px !important;
  background-image: url("form-widgets/radio.png") !important;
  -moz-border-radius: 0 !important;
  border: none !important;
  background-color: inherit !important;
}

input[type="radio"]:focus:not([class]):not([id]):not([style]) {
  border:none !important;
}

input[type="radio"]:focus {
  border:none !important;
}

input[type="radio"]:active:focus {
  border:none !important;
}

input[type="radio"]:checked {
  background-image: url("form-widgets/radio-checked.png") !important;
}

input[type="radio"][disabled],
input[type="radio"][disabled]:hover {
  border: none !important;
}

*::-moz-radio {
  border: none !important;
  background-color: transparent !important;
}

/* Checkboxes */

input[type="checkbox"] {
  width: 12px !important;
  height: 12px !important;
  border-width: 0 !important;
  background-image: url("form-widgets/checkbox.png") !important;
  background-color: -moz-Field !important;
}

input[type="checkbox"]:checked {
  background-image: url("form-widgets/checkbox-checked.png") !important;
}

/* Dropdowns  */

select,
select:not([size]),
select[size="0"],
select[size="1"] {
  color: ButtonText;
  background-color: Window;
  background: Window url("form-widgets/button.png") repeat-x bottom right;
  border: 2px solid ThreeDShadow;
  -moz-border-top-colors: ThreeDShadow ThreeDHighlight;
  -moz-border-right-colors: ThreeDShadow Window;
  -moz-border-bottom-colors: ThreeDShadow Window;
  -moz-border-left-colors: ThreeDShadow ThreeDHighlight;
  margin: 2px;
  padding: 0px 1px;
  -moz-border-radius: 1px;
}

select > input[type="button"]{
  width: 6px !important;
  border: none !important;
  background: transparent url("form-widgets/droparrow.png") no-repeat center center !important;
}

select > input[type="button"]:focus {
}

```

[QUOTE=ember]And e.g. on the page of my bank ([https://bankingportal.sparkasse-karlsruhe.de/banking/?BLZ=66050101]("https://bankingportal.sparkasse-karlsruhe.de/banking/?BLZ=66050101")), the login-boxes moved to a place underneath the text instead of their standard right placing.
The text input margins and paddings are not forced with "!important" so fixing this would uglify much else.

---

### Post by majikstreet on 2006-02-19
oh yeah, for some reasons certain boxes, like people had complained before, still look wierd even after re installing the package.. hmm

---

### Post by Uuranor on 2006-05-01
[QUOTE=ow50]**For Firefox 1.5 users:**
**Installation instructions for Dapper users and those who backported their firefox from Dapper**

Installation:
```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
cat firefox-form-widgets-ots/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets-ots/res/form-widgets /usr/lib/mozilla-firefox/res
rm -rf firefox-form-widgets-ots
```

Uninstallation:
```
sudo rm -rf /usr/lib/mozilla-firefox/res/form-widgets
sudo cp /usr/lib/mozilla-firefox/res/forms.css.bak /usr/lib/mozilla-firefox/res/forms.css
```
[/QUOTE]

It is great :D
Thanks a lot, ow50.

Btw, something is changed in Dapper.
So, to make it working in Ubuntu 6.06 you need to change in your guide /usr/lib/mozilla-firefox with /usr/lib/firefox :)
At least in mine Dapper :p

---

### Post by dilidon on 2006-07-20
Hi,
I used either this thread or that found [here]("http://www.ubuntuforums.org/showthread.php?t=175394&highlight=firefox+widgets") to polish my Firefox/Swiftfox. All was sort of fine. Thanks a million!

However, on some sites there seems to be a problem with displaying the text  inside the form boxes. See the attached screenshots from [www.postimees.ee](www.postimees.ee) and [www.hanza.net](www.hanza.net)

I guess these forms are also slightly different than the one of, say, google.com so the problem might have nothing to do with this post, but its worth a try - I'm willing to remove the post in case this is the wrong place. It is hard to desribe, but text gets sort of pushed downwards and there is some empty space above the letters - hence, only half of every word typed is visible, which in some cases makes it difficult to operate some sites. I can't tell if it was like that also before getting the nicer widgets in place, but I would doubt that, as I didn't have that problem in Windows and I never noticed it before in Linux either. Wouldn't wanna go removing the imporvements right away for the purposes of finding out as well...
Any clues?

---

### Post by dilidon on 2006-07-27
Anyone?
Or should I perhaps repost this little problem elswhere? (Just wanted to avoid cross-posting so far and this issue seemed possibly connected to the howto...). Thanks for any pointers.

---

### Post by KillerKiwi on 2006-08-03
Heres a tweak for the radio buttons (stops them repeating if the css height/width has been set)

```
/* Radio buttons */

input[type="radio"] {
  width: 13px !important;
  background-image: url("form-widgets/radio.png") !important;
  background-repeat: no-repeat;
  background-position: middle center;
  -moz-border-radius: 0 !important;
  border: none !important;
  background-color: inherit !important;
}
```

---

### Post by PingunZ on 2006-08-19
Err, what about Edgy users with Bon Echo ?

---

### Post by PingunZ on 2006-08-21
Found out this works on edgy too :)
just do : ```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /opt/firefox/res/forms.css /opt/firefox/res/forms.css.bak
cat firefox-form-widgets-ots/res/forms-extra.css | sudo tee --append /opt/firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets-ots/res/form-widgets /opt/firefox/res
rm -rf firefox-form-widgets-ots
```

---

