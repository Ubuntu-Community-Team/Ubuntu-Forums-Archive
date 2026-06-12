---
title: "TWEAK: Nicer Firefox form widgets"
date: 2005-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by FrzzMan on 2005-06-24
Well, I follow [this guide](http://ubuntuforums.org/showthread.php?t=22034) and decided to tweak it a lil bit, so the credit should goes to ubuntu-geek rather than me.

This tweak enhance the button look (shrink it a bit), replace the missing "ring" of checked radio option, and fix the text-cut-off problem (describe [here](http://ubuntuforums.org/showpost.php?p=204963&postcount=14))

Step-by-step howto:

1. Download attached file to your Desktop
2. Open the CLI (Applications > System Tools > Terminal)
3. [cd /usr/lib/mozilla-firefox/]
4. [tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz .]
5. Delete the file if you want

Have fun...

PS: This tweak is safe, just in case you want to uninstall the tweak, back up the /usr/lib/mozilla-firefox/res/ directory somewhere and cp it back as needed.

EDIT: Nothing is change, you don't have to re-download the package.

---

### Post by Lunde on 2005-06-24
[QUOTE=FrzzMan]Well, I follow [this guide](http://ubuntuforums.org/showthread.php?t=22034) and decided to tweak it a lil bit, so the credit should goes to ubuntu-geek rather than me.

This tweak enhance the button look (shrink it a bit), replace the missing "ring" of checked radio option, and fix the text-cut-off problem (describe [here](http://ubuntuforums.org/showpost.php?p=204963&postcount=14)

Step-by-step howto:

1. Download attached file to your Desktop
2. Open the CLI (Applications > System Tools > Terminal)
3. [cd /usr/lib/mozilla-firefox/]
4. [tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz .]
5. Delete the file if you want

Have fun...

PS: This tweak is safe, just in case you want to uninstall the tweak, back up the /usr/lib/mozilla-firefox/res/ directory somewhere and cp it back as needed.[/QUOTE]
 May we see a screenshot?

---

### Post by JettCRX on 2005-06-24
[QUOTE=Lunde]May we see a screenshot?[/QUOTE]
 Yeah... preferrably before AND after.  :)

---

### Post by wylfing on 2005-06-24
I haven't looked at this file, but in general Firefox is highly customizable with regard to its on-screen widgets. Under /usr/lib/mozilla-firefox/res are bits that go into rendering stuff on screen. This file probably just replaces/adds a few and includes a platform-forms.css file to describe their usage. You can easily edit platform-forms.css to your liking if you grok CSS.

Here's a link to another "forms enhancer" for Firefox:
[http://www.gnome-look.org/content/show.php?content=21812](http://www.gnome-look.org/content/show.php?content=21812)

---

### Post by N'Jal on 2005-06-24
Here's a screen shot, i can say it's an excelent tweak.

---

### Post by moment on 2005-06-24
Nice! Here it is. compare it with yours.

---

### Post by sexycatsinhats on 2005-06-24
**Before and After attached**

---

### Post by ChaKy on 2005-06-24
It doesn't work on Deer Park Alpha 1. :-(

---

### Post by Lunde on 2005-06-25
NICE! Thanks.

It's like getting rims on your car..

---

### Post by RastaMahata on 2005-06-25
This tweak works in google, but I still see ugly forms in the forums :(

---

### Post by tzutolin on 2005-06-25
Thanks FrzzMan!
It works perfectly  :smile:

---

### Post by NeoChaosX on 2005-06-25
[QUOTE=RastaMahata]This tweak works in google, but I still see ugly forms in the forums :([/QUOTE]
That's because the forums (at least the buttons, anyway - everything else is fine) don't use the default widgets, but rather the ones in the server software.

---

### Post by tzutolin on 2005-06-25
[QUOTE=NeoChaosX]That's because the forums (at least the buttons, anyway - everything else is fine) don't use the default widgets, but rather the ones in the server software.[/QUOTE]
 So is it possible to solve this problem?

---

### Post by NeoChaosX on 2005-06-25
Yeah, bug ubuntu-geek to change the appearance of the buttons in the forum software.  :-P

---

### Post by manicka on 2005-06-25
Very nice tweak... Thankyou :D

---

### Post by FrzzMan on 2005-06-25
Happy to see you like it :)

I don't have Deer Park here so can't test it, can you give me a screenshot?

---

### Post by ChaKy on 2005-06-25
[QUOTE=FrzzMan]Happy to see you like it :)

I don't have Deer Park here so can't test it, can you give me a screenshot?[/QUOTE]

Well, here is the screenshot:

[img]http://public.globalnet.hr/~ncakelic/slike/google-forms.jpg[/img]

It was working fine on 1.0.4, but not on Deer Park. If you take a look at this thread
[http://forums.mozillazine.org/viewtopic.php?t=235391](http://forums.mozillazine.org/viewtopic.php?t=235391), someone has said that it is not working on Trunk builds.

---

### Post by i3dmaster on 2005-06-25
Nice enhancement, thanks!!

---

### Post by KillerKiwi on 2005-06-27
Nice very nice, this should be standerd the ugly form controls make me want to cry

---

### Post by Caboto on 2005-06-27
Looks indeed very nice. But I've got one further question. Where is the Background-color of a Select field with more than 1 option set? I've tried different things, but can't seem to find it.

On some sites, the background-color is set with css as select {} instead with an id, class or style tag and thus the select field is not readable (e.g. when the select field gets an white font color from the website, but no real background color -> white font on bright grey background).

I can find the place, where droparrow.png is set and can turn it off, but a change to the background-color doesn't change anything.  I would just like to have it transparent or in the site style. A possibility would be too, that the font color is always set to black. 
Any idea? :???:

---

### Post by bigcletus on 2005-06-28
[QUOTE=FrzzMan]
4. [tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz .]
.[/QUOTE]

I get this:  tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz .
tar: .: Not found in archive
tar: Error exit delayed from previous errors

Any idea why?

---

### Post by dissident on 2005-06-28
[QUOTE=bigcletus]I get this:  tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz .
tar: .: Not found in archive
tar: Error exit delayed from previous errors

Any idea why?[/QUOTE]
Try leaving out the period at the end.  ;-)

---

### Post by Arthemys on 2005-06-28
Flawless! Nice.

---

### Post by i3dmaster on 2005-07-01
This is really much nicer than the default one. Thanks for sharing!

---

### Post by FrzzMan on 2005-07-01
I haven't figured out why this didn't work with Deer Park Alpha 1, so I'm sorry I can't help you out...

Btw... thanks for your "thanks" :D

---

### Post by bored2k on 2005-07-01
Cute ^_^ !

---

### Post by idn on 2005-09-10
Is there a way to get this to work for epiphany?

^ Ok just realised it works in epiphany as well, just checked it out on google, it didnt work in these forums :)

Nice hack :)

---

### Post by LaSSarD on 2005-09-11
Nice, thanks :D

---

### Post by dudus on 2005-10-18
this works fine for some buttons but not for other ones. Don't know why. And some buttons resize when mouseover.

---

### Post by Albaraha on 2005-10-18
Thanks guy.

---

### Post by hornett on 2005-11-18
Works a treat in 1.07 but has anybody managed to get this working under Firefox 1.5? 

Seems like it ignores the forms-2.css file.

---

### Post by ow50 on 2005-11-25
**For Firefox 1.5 users:**

I made made my own version of the firefox forms for Firefox 1.5. It resembles quite closely the ones posted in the first post of this thread. I modified the radio- and checkbutton images. The forms.css I made based on Firefox 1.5 RC3's forms.css and Winterfox 0.4's forms.css.

The forms package is at
[http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz](http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz).

Below is installation instructions for Dapper users and those who backported their firefox from Dapper. If you used an installer from mozilla.org, the paths will be different.

Installation:
```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
sudo cp -r firefox-form-widgets-ots/res/* /usr/lib/mozilla-firefox/res
rm -rf firefox-form-widgets-ots
```

Uninstallation:
```
sudo rm -rf /usr/lib/mozilla-firefox/res/form-widgets
sudo cp /usr/lib/mozilla-firefox/res/forms.css.bak /usr/lib/mozilla-firefox/res/forms.css
```
If you didn't backup, you can unistall by removing the whole /usr/lib/mozilla-firefox/res directory and  reinstalling the firefox package.

Screenshot:
[[IMG]http://img498.imageshack.us/img498/418/kuvakaappausgoogletarkennettuh.th.png[/IMG]](http://img498.imageshack.us/my.php?image=kuvakaappausgoogletarkennettuh.png)

Edit:
Oops. This a Hoary forum. Continue at
[http://www.ubuntuforums.org/showthread.php?t=83855](http://www.ubuntuforums.org/showthread.php?t=83855)

---

### Post by mc_bizon on 2005-12-03
i love it!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Healey on 2005-12-05
Hi
I thought I would like to try this out but had the following problem after Typing "tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz":

res/
res/forms-2.css
tar: res/forms-2.css: Cannot open: Permission denied
res/button-bg-active.png
tar: res/button-bg-active.png: Cannot open: Permission denied
res/checkbox.png
tar: res/checkbox.png: Cannot open: Permission denied
res/checkbox_checked.png
tar: res/checkbox_checked.png: Cannot open: Permission denied
res/radio.png
tar: res/radio.png: Cannot open: Permission denied
res/button-bg.png
tar: res/button-bg.png: Cannot open: Permission denied
res/radio_checked.png
tar: res/radio_checked.png: Cannot open: Permission denied
res/droparrow.png
tar: res/droparrow.png: Cannot open: Permission denied
res/platform-forms.css
tar: res/platform-forms.css: Cannot open: File exists
tar: res: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

What am I doing wrong ??

I am using Firefox 1.0.7

Ubuntu 5.10

And I am very new at this stuff - Sorry !!

Thanks in advance

Healey

---

### Post by mcrosmar on 2005-12-20
[quote=Healey]Hi
I thought I would like to try this out but had the following problem after Typing "tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz":

res/
res/forms-2.css
tar: res/forms-2.css: Cannot open: Permission denied
res/button-bg-active.png
tar: res/button-bg-active.png: Cannot open: Permission denied
res/checkbox.png
tar: res/checkbox.png: Cannot open: Permission denied
res/checkbox_checked.png
tar: res/checkbox_checked.png: Cannot open: Permission denied
res/radio.png
tar: res/radio.png: Cannot open: Permission denied
res/button-bg.png
tar: res/button-bg.png: Cannot open: Permission denied
res/radio_checked.png
tar: res/radio_checked.png: Cannot open: Permission denied
res/droparrow.png
tar: res/droparrow.png: Cannot open: Permission denied
res/platform-forms.css
tar: res/platform-forms.css: Cannot open: File exists
tar: res: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

What am I doing wrong ??

I am using Firefox 1.0.7

Ubuntu 5.10

And I am very new at this stuff - Sorry !!

Thanks in advance

Healey[/quote] 
You have to type **sudo tar xvzf ~/Desktop/firefox-form-widgets-fixed.tar.gz** 
Give the password of the user that you have logged in.

---

### Post by Healey on 2005-12-20
Hi
Thanks for your reply

It worked very well !!

Your answer has helped me understand a few other things also !

Thanks again

Healey

---

### Post by adam.tropics on 2005-12-22
All great but when using the 'find' or 'add bookmark' (and probably others I haven't found yet), the text box isn't large enough for the height of the text within it. Not sure if i have messed the fonts up or something, but all the parts of say, google advanced search are fine, it seems to be just the widgets within firefox itself. Any ideas anyone?
Btw, other than that, it's a massive improvement on the general look of the thing. Makes you wonder why it comes with such crap widgets in the first place? I guess as long as they are not worrying about that, they have more time to worry about security, which is all good....anyway, thanks if anyone can help.

---

### Post by Adrenal on 2005-12-30
Hi, I'm seem to be having a problem with these widgets. Basically, my gnome-theme is a dark one, grey backgrounds, white text(easy on the eyes).
However, this widgets transform all text boxes to white, while retaining the inherent colour of the system font.
Ergo, when posting on forums, such as this one, I am writing white text on a white background.
Is there anyway to make the text default to black, or change the colour of a text box?

---

### Post by scratched on 2006-05-13
[QUOTE=ow50]
Installation:
```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
sudo cp -r firefox-form-widgets-ots/res/* /usr/lib/mozilla-firefox/res
rm -rf firefox-form-widgets-ots
```[/QUOTE]

I tried the tweak using these exact instructions from ow50 since I'm using ff1.5, and nothing changed. Any ideas as to what I need to do or what I did wrong?

EDIT: oops, I made the same mistake as ow50 but didn't notice right away... this is the hoary forum... oops:neutral: .

These new widgets look amazing:)

---

### Post by hikaricore on 2006-09-16
> **Adrenal said:**
> Hi, I'm seem to be having a problem with these widgets. Basically, my gnome-theme is a dark one, grey backgrounds, white text(easy on the eyes).
However, this widgets transform all text boxes to white, while retaining the inherent colour of the system font.
Ergo, when posting on forums, such as this one, I am writing white text on a white background.
Is there anyway to make the text default to black, or change the colour of a text box?

for you and anyone else having issues with textbox font colors being unreadable i've got a lazy fix.

from console do

gksudo gedit /usr/lib/mozilla-firefox/res/forms.css

> 
--replace lines 84-85--

```

background-color: -moz-Field;
color: -moz-FieldText;
```

with:
```

/*  background-color: -moz-Field; */
/*  color: -moz-FieldText; */

```


next

> 
--replace lines 105-106--

```

background-color: -moz-Field;
color: -moz-FieldText;

```

with

```

/*  background-color: -moz-Field; */
/*  color: -moz-FieldText; */

```


finally
> 
---replace lines 198-199---
```

background-color: inherit;
color: inherit;

```

with

```

/*  background-color: inherit; */
/*  color: inherit; */

```


save, then close+restart or if it's not open, start firefox.

this should fix almost all of it.

let me know if i missed any :)

also make sure your text fonts are set to system colors or some other readable color for sites without much color coding :)

--aaron

---

### Post by mucha on 2006-10-29
I don't think I get this working with Firefox 2.0. In firefox 1.5 it worked perfect. Anyone else with the same problem?

---

### Post by rado_london on 2006-10-29
> **mucha said:**
> I don't think I get this working with Firefox 2.0. In firefox 1.5 it worked perfect. Anyone else with the same problem?

It doesnt work in 2.0 for me. Any idea what to do in order to get this working?

---

### Post by ThrobbingBrain66 on 2006-10-29
i think these are the instructions i used...

[http://www.ubuntuforums.org/showthread.php?t=250688&highlight=widgets](http://www.ubuntuforums.org/showthread.php?t=250688&highlight=widgets)

---

### Post by rado_london on 2006-10-29
> **ThrobbingBrain66 said:**
> i think these are the instructions i used...

[http://www.ubuntuforums.org/showthread.php?t=250688&highlight=widgets](http://www.ubuntuforums.org/showthread.php?t=250688&highlight=widgets)

Works fine in 2.0. Thanks 
Just to mention download the file from [www.riborest.eu/data/firefox-form-widgets-ots.tar.gz](www.riborest.eu/data/firefox-form-widgets-ots.tar.gz) because the original link ain't working!

Thanks again!

---

### Post by kjempe on 2006-11-22
For different widgets try these:

[http://www.ubuntuforums.org/showthread.php?p=1792821#post1792821]("http://www.ubuntuforums.org/showthread.php?p=1792821#post1792821")

---

