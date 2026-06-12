---
title: "HOWTO: replace the firefox throbber with a rotating firefox logo"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by bruenig on 2006-07-11
EDIT: January 7, 2007
It has been brought to my attention that there has now been an extension made for this. It is probably easier to use that instead of this and so here is the [link](http://burntelectrons.org/moz/spinfox/spinfox-0.7.1.xpi).

Nevertheless, if you still wish to do it manually, I will leave up the original HOWTO.

Works on 1.5 and 2.0. Also works in swiftfox.

I stumbled upon [this website](http://burntelectrons.org/moz/spinfox/) where some guy created and explained how to replace the throbber icon, that little circle in the top right of the browser that becomes active when loading pages and other times, with this firefox rotating around a globe. I thought it looked pretty cool so I figured I would try to do it in Linux. It took much longer than I thought it would because of seemingly redundant directories and code that didn't work but nevertheless, I got it to work and figured I would put together this little HOWTO.

Note: I will use all exact paths in this tutorial. If you want to use relative paths, go ahead.

First thing you must do is determine your random firefox default directory name. Replace USERNAME with your own.
```
ls /home/USERNAME/.mozilla/firefox
```
That should give you an output which includes a directory named with 8 random alphanumeric characters followed by a .default (********.default). Use that in the following commands.

Now you must navigate to the directory where all the action will be taking place.
```
cd /home/USERNAME/.mozilla/firefox/********.default/chrome
```
Now download the new gifs for the throbber with wget.
```
wget http://burntelectrons.org/moz/spinfox/static16.gif http://burntelectrons.org/moz/spinfox/static20.gif http://burntelectrons.org/moz/spinfox/static24.gif http://burntelectrons.org/moz/spinfox/throbber16.gif http://burntelectrons.org/moz/spinfox/throbber20.gif http://burntelectrons.org/moz/spinfox/throbber24.gif
```
Now you must configure the userChrome.css file. If you are like me, you don't have one so will be creating a userChrome.css file. Either way the command is the same.
```
gedit /home/USERNAME/.mozilla/firefox/********.default/chrome/userChrome.css
```
If you created this file (i.e. it is blank) copy the following into the file
```
/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/* This changes the throbber
 */
   #navigator-throbber { list-style-image: url("static24.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber24.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 24px !important; min-height: 24px !important; }

   #navigator-throbber { list-style-image: url("static20.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber20.gif") !important; opacity: 1 !important }
   #navigator-throbber { min-width: 20px !important; min-height: 20px !important; }

   #navigator-throbber { list-style-image: url("static16.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber16.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 16px !important; min-height: 16px !important; }
```

If you have configured it before, just copy the last part of the code.
```
/* This changes the throbber
 */
   #navigator-throbber { list-style-image: url("static24.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber24.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 24px !important; min-height: 24px !important; }

   #navigator-throbber { list-style-image: url("static20.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber20.gif") !important; opacity: 1 !important }
   #navigator-throbber { min-width: 20px !important; min-height: 20px !important; }

   #navigator-throbber { list-style-image: url("static16.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber16.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 16px !important; min-height: 16px !important; }
```

Save the file and restart firefox.

---

### Post by FLeiXiuS on 2006-07-11
I think this adds a bit of flare.  I liked the improvements.  Nice directed how-to, will publish!  Thanks!

---

### Post by skull_leader on 2006-07-11
It worked here... man, that is so cool. :)

---

### Post by reacocard on 2006-07-11
works, and is awesome!

---

### Post by xolot1 on 2006-07-11
very nice.

to make this a bit easier, i put together i quick bash script. its attached.

directions:
1. Download tarball **To Desktop**
2. Extract tarball
```
tar xf /home/$USER/Desktop/throbber.tar.gz
```
3. Change the file permissions to allow execution
```
sudo chmod +x /home/$USER/Desktop/replacefirefoxlogo
```
4. Run script
```
/home/$USER/Desktop/./replacefirefoxlogo
```
5. Restart Firefox




*note*
it changes the default profile only.


its a very simple script, so if you want to inspect it, you should have no problem.

**edit:**
updated script to correct download directory

**edit 2:**
script now includes the ubuntu throbber. run the script and it will give you a choice.

---

### Post by dspivey on 2006-07-11
that is very cool.  thanks!

---

### Post by Janux on 2006-07-11
Really nice, thanks!
It would be really great if someone made a Ubuntu icon with the logo rotating, thought.

---

### Post by xolot1 on 2006-07-11
its still summer vacation for me, maybe ill edit the icons tomorrow...  great thinking.

---

### Post by Nathan Otis on 2006-07-11
Xolot,

I copied and pasted code just as you said, but my throbber was replaced with ...

nothing.
:( 

What'd I do wrong?
n.

---

### Post by xolot1 on 2006-07-11
so i did some quick GIMPing, and came up with these "throbbing" ubuntu logos.
theyre not such high quality right now - but its a draft.
theyre attached below.

if youve already replaced the throbber to the firefox one, you merely have to replace static16.gif, static20.gif, static24.gif, throbber16.gif, throbber20.gif, throbber24.gif in your /home/$USER/.mozilla/firefox/xxxxxxxx.default/chrome directory with the attached images (of the same name).


should you want to switch them back, just redownload the images from the first post, and again replace the images.

---

### Post by adam.tropics on 2006-07-12
Just to point out that firstly this will also affect swiftfox (same profile directory), which is nice, and that secondly can simply be adapted to cover thunderbird as well.

---

### Post by manicka on 2006-07-12
I've added this tweak to the Ubuntu Document Storage Facility

[http://doc.gwos.org/index.php/FirefoxThrobber](http://doc.gwos.org/index.php/FirefoxThrobber)

---

### Post by adam.tropics on 2006-07-19
Well, if you're gonna use an Ubuntu logo throbber, you may as well change the throbber link to reflect the new graphic.

In firefox go to about:config

In the Filter box, type browser.throbber.url

Select the listing and then right click > modify. Change the value of the URL in the text field.

---

### Post by Stirfry on 2006-07-19
Thanks I thought this lookied prety cool so I tried it. everything went fine with out a hitch. awsome thanks.

---

### Post by matthew on 2006-07-19
Very cool. This is the sort of thing I love--silly, useless fun that lets you set yourself apart. Thank you!

---

### Post by glotz on 2006-10-18
Check out [http://kb.mozillazine.org/Customizing_throbber](http://kb.mozillazine.org/Customizing_throbber)

Note the link to RenegadeX work.

---

### Post by jpyanowski on 2006-11-12
> **bruenig said:**
> Works on 1.5 and 2.0. Also works in swiftfox.

I stumbled upon [this website](http://burntelectrons.org/moz/spinfox/) where some guy created and explained how to replace the throbber icon, that little circle in the top right of the browser that becomes active when loading pages and other times, with this firefox rotating around a globe. I thought it looked pretty cool so I figured I would try to do it in Linux. It took much longer than I thought it would because of seemingly redundant directories and code that didn't work but nevertheless, I got it to work and figured I would put together this little HOWTO.

Note: I will use all exact paths in this tutorial. If you want to use relative paths, go ahead.

First thing you must do is determine your random firefox default directory name. Replace USERNAME with your own.
```
ls /home/USERNAME/.mozilla/firefox
```
That should give you an output which includes a directory named with 8 random alphanumeric characters followed by a .default (********.default). Use that in the following commands.

Now you must navigate to the directory where all the action will be taking place.
```
cd /home/USERNAME/.mozilla/firefox/********.default/chrome
```
Now download the new gifs for the throbber with wget.
```
wget http://burntelectrons.org/moz/spinfox/static16.gif http://burntelectrons.org/moz/spinfox/static20.gif http://burntelectrons.org/moz/spinfox/static24.gif http://burntelectrons.org/moz/spinfox/throbber16.gif http://burntelectrons.org/moz/spinfox/throbber20.gif http://burntelectrons.org/moz/spinfox/throbber24.gif
```
Now you must configure the userChrome.css file. If you are like me, you don't have one so will be creating a userChrome.css file. Either way the command is the same.
```
gedit /home/USERNAME/.mozilla/firefox/********.default/chrome/userChrome.css
```
If you created this file (i.e. it is blank) copy the following into the file
```
/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/* This changes the throbber
 */
   #navigator-throbber { list-style-image: url("static24.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber24.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 24px !important; min-height: 24px !important; }

   #navigator-throbber { list-style-image: url("static20.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber20.gif") !important; opacity: 1 !important }
   #navigator-throbber { min-width: 20px !important; min-height: 20px !important; }

   #navigator-throbber { list-style-image: url("static16.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber16.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 16px !important; min-height: 16px !important; }
```

If you have configured it before, just copy the last part of the code.
```
/* This changes the throbber
 */
   #navigator-throbber { list-style-image: url("static24.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber24.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 24px !important; min-height: 24px !important; }

   #navigator-throbber { list-style-image: url("static20.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber20.gif") !important; opacity: 1 !important }
   #navigator-throbber { min-width: 20px !important; min-height: 20px !important; }

   #navigator-throbber { list-style-image: url("static16.gif") !important; }
   #navigator-throbber[busy="true"] { list-style-image: url("throbber16.gif") !important; opacity: 1 !important}
   #navigator-throbber { min-width: 16px !important; min-height: 16px !important; }
```

Save the file and restart firefox.

I have only one thing to say: SWEET!!!!!!! \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by stonymouse on 2006-11-20
These things appeal to me :-D Thank you for a V cool little tweak, without too much work!

Jenny

---

### Post by DC@DR on 2006-11-20
Works like a charm. BIG thanks :)

---

### Post by hikaricore on 2006-12-19
Much better than the original :)  I always had a hard time telling it the damn thing was moving or not :P

Can't wait to see high quality ubuntu logos for this hehe

---

### Post by jpyanowski on 2006-12-29
SWEEET. Your instructions were easy to follow and copy and the result is nice to look at, but that was the purpose of this HOW TO, wasn't it???? ;)

---

### Post by george_apan on 2006-12-30
Very nice! Thank you! :)

---

### Post by smartbei on 2007-01-06
This has been released in XPI (extension) form on the website mentioned in the first post. Probably easier to get it from there.

---

### Post by bruenig on 2007-01-07
> **smartbei said:**
> This has been released in XPI (extension) form on the website mentioned in the first post. Probably easier to get it from there.

Yeah this does look obsolete now.

---

