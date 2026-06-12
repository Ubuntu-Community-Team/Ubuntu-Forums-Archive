---
title: "Alternate web browser"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Miljet on 2008-11-29
I am running 8.04 on a Toshiba Satellite P205-S6237.

I am tired of trying to get java applets working right in Firefox 3 and am looking for a different web browser. I tried Opera but can't get it to recognize the Sun java6 plugin. Any suggestions?

---

### Post by linuxguymarshall on 2008-11-29
Epiphany, seamonkey, or get firefox to work

---

### Post by Xiong Chiamiov on 2008-11-29
Opera is a fantastic browser.  Kazehakase, Ephiphany and Galeon are popular Gecko-based browsers that are as lightweight as Gecko can be, and of course there are the text-based browsers (elinks and w3m seem to be 2 of the more popular ones).  You can even use IE6 through Wine if you like (ies4linux), which works surprisingly well.

I have a feeling your Java issues are not related to your browser but to having the proper packages installed, and switching won't help.

---

### Post by zvacet on 2008-11-29
[Here]("http://www.opera.com/support/kb/view/459/")

---

### Post by the.phantom on 2008-11-29
might be easier to find what is wrong with firefox?

what happens when you type 

> about:config
in the url spot of firefox?
does it show sunjava? or any other java?

when you installed sunjava you selected the plug in too?

and in firefox
edit/preferences/content   youi have java and java script enabled?

---

### Post by mmb1 on 2008-11-29
I personally recommend kazehakase, as it is light and very functional.

However epiphany or even konqueror if you don't mind installing a few dependencies are both solid choices. 

Best of Luck!

---

### Post by Miljet on 2008-11-29
Thanks for all the quick replies. Don't get me wrong - I love Firefox. That said, I have been trying for four weeks to get java based game applets to work right. 
I have checked about:plugins and the correct plugin is listed.
```
     File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07 
```

Sometimes the games load and run correctly (maybe 10% of the time). Otherwise, I get wildly varying results. Sometimes the applet will load and then show a "game applet death" message, sometimes it just hangs at the "game applet loading" point, sometimes the screen changes to an "application programming error" screen, and sometimes the game applet window just closes.

I asked for help from the game site and after two weeks of "try this, try that", they finally admitted that they don't support Linux. I have posted here a couple of weeks ago and got no suggestions.

Also I have tried disabling all other plugins except java with no improvement. Also tried removing all extensions - no help. I would love to get Firefox working, but don't know what wlse to try.

---

### Post by Xiong Chiamiov on 2008-11-29
Which Java plugin did you install?  If it's one of the open-source Javas, that might be what's causing the problem.

---

### Post by Miljet on 2008-11-29
Sun Java(TM) Plug-in 1.6.0_07

I have sun-java6-bin, sun-java6-fonts, sun-java6-jre, and sun-java6-plugin all installed.

Guess I should have mentioned that the reason I suspect Firefox is that these games worked great under Firefox 2. As soon as I upgraded to Firefox 3, the problems started.

---

### Post by sstusick on 2008-11-29
In addition to Firefox, I use Epiphany and Galeon. Both are great.

---

### Post by Zzl1xndd on 2008-11-29
+1 to Epiphany.

---

### Post by Miljet on 2008-11-29
zvacet, thanks for the link for Opera. But I guess I'm just stupid. I followed the tutorial to the letter but as soon as I try to start a game, It shows a pop-up window that says "No java plugin."

---

### Post by Miljet on 2008-11-29
Well, I installed Epiphany and tried that. I am getting the exact same results as Firefox. So, I guess that exonerates Firefox 3.

Trouble is, now I am fresh out of ideas of what the problem might be.

---

### Post by the.phantom on 2008-11-29
I AM NOT A EXPERT

but how did you install sunjava and the plugin  ( from applications/add/remove) or did you do it with some other way?
in the add remove there are two to install one is java and the other is the plugin ?

if you installed it another way have you uninstalled that way and tried add/remove?

i am out of ideas as a lightweight sorry !

---

### Post by eternalnewbee on 2008-11-29
Nobody's mentioned **Swiftweasel**.

---

### Post by bruce89 on 2008-11-29
> **Miljet said:**
> Well, I installed Epiphany and tried that. I am getting the exact same results as Firefox. So, I guess that exonerates Firefox 3.

That is because they both (currently) use the same Web browser engine.

> **eternalnewbee said:**
> Nobody's mentioned **Swiftweasel**.

It is also a Gecko one, so that won't make any difference.

---

### Post by Miljet on 2008-11-29
I used apt-get to install all 4 (-bin,-fonts,-jre, and -plugin). I just prefer the command line for installing/removing programs.

I guess the next thing is to try different versions of Sun-java, but there aren't too many choices in the repositories.

---

### Post by Miljet on 2008-11-29
>  That is because they both (currently) use the same Web browser engine. 

So maybe back to trying to get Opera working.

---

### Post by Miljet on 2008-11-29
Opera is a no-go too. Every time a game tries to load, the entire browser just closes.

---

### Post by Xiong Chiamiov on 2008-11-29
> **eternalnewbee said:**
> Nobody's mentioned **Swiftweasel**.

> **bruce89 said:**
> 
It is also a Gecko one, so that won't make any difference.

More than that, it **is** Firefox, merely with non-free images removed and compiled with different gcc options.

OP:
I'd suggest creating a new thread, as this is no longer about an Alternate web browser, but rather about getting a Java plugin to work in Opera.

---

### Post by Unanimated on 2008-11-29
Do you have Ubuntu Restricted Extras installed? That put Java on my computer just fine.

---

### Post by bruce89 on 2008-11-29
> **Unanimated said:**
> Do you have Ubuntu Restricted Extras installed? That put Java on my computer just fine.

That is a metapackage which depends on what the OP has installed.

I have no issues with OpenJDK (icedtea6-plugin).

---

### Post by jamesstansell on 2008-11-30
> **Miljet said:**
> Sun Java(TM) Plug-in 1.6.0_07

I have sun-java6-bin, sun-java6-fonts, sun-java6-jre, and sun-java6-plugin all installed.

Guess I should have mentioned that the reason I suspect Firefox is that these games worked great under Firefox 2. As soon as I upgraded to Firefox 3, the problems started.

several thoughts:

What game is it?  Making sure there is a bug report for it would help.

Several people report success running java applets with konqueror; one day I'll have to try that myself. :)

Java 6u7 is the latest version packaged for hardy, but intrepid has 6u10 packages.  You should be able to download and install them to see if the update helps.

Also with 6u10 is a new browser plugin, which could also make a difference.  It takes a few manual steps to get it configured, but might be worth exploring.

---

### Post by Miljet on 2008-11-30
OK, I am starting a new thread with a more appropriate title. I have about convinced myself that the problems are not caused by Firefox. I have tried several other browsers and the problems persist.

Thanks for all the replies.

---

