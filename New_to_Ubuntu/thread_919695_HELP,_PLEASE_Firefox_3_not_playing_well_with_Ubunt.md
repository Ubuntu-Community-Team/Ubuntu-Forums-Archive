---
title: "HELP, PLEASE: Firefox 3 not playing well with Ubuntu?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-14
I've been having serious issues regarding sound and media, and I think I may have tracked down the real issue. It seems that if Firefox 3 is open at the same time I try to play any sort of media, nothing works correctly. Both just a moment ago locked up, and the Firefox process froze. I was unable to restart Ubuntu, and ended up having to pull the plug and pop the battery.

I really, really need to get this all sorted out. Please help.

---

### Post by k33bz on 2008-09-14
> **Grimhound said:**
> I've been having serious issues regarding sound and media, and I think I may have tracked down the real issue. It seems that if Firefox 3 is open at the same time I try to play any sort of media, nothing works correctly. Both just a moment ago locked up, and the Firefox process froze. I was unable to restart Ubuntu, and ended up having to pull the plug and pop the battery.

I really, really need to get this all sorted out. Please help.

Firefox 3 is still very unstable. It has however improved quite a bit "version 3 that is". It was alot more unstable than it is now. 

You can downgrade Firefox 3 to Firefox 2 in the synaptic manager.

---

### Post by Grimhound on 2008-09-14
I installed a libpatch off of Synaptic, so at least it crashes now instead of freezing. >_>

---

### Post by k33bz on 2008-09-14
You can eliminate both crashing and freezing by forcing Firefox to version 2.


open your synaptic manager. Search "firefox"
unistall all firefox-3 related installations, and install firefox-2

---

### Post by TheUbGuy on 2008-09-14
Hmmm ... I'm running Firefox 3.0.1 and have not had any issues. I can listen to MP3 or streams in Rhythym Box with absolutely no problem. I'm on the current 64-bit version of Ubuntu.

---

### Post by arpanaut on 2008-09-14
this How To fixed all my firefox, sound, and flash issues...

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Hope it works for you!

or try the main guide linked in that post if you aren't wanting to add experimental repositories.

---

### Post by kansasnoob on 2008-09-14
I followed the appropriate steps (there are 64 bit and i386 specific steps) in the following guide and my Firefox/Sound/Flash problems went away:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Now, it's been a while and I'm not sure what version of Flash that'll update you to, so just type about:PLUGINS into the URL box and see what it shows when you've completed all steps of the guide. If it shows anything older than Shockwave Flash 10.0.0 d569, then just remove any previous versions of flash by:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

And then you can install the Flash 10 RC here:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

It's a .deb so it's easy to install.

---

### Post by carolinason on 2008-10-05
i'm going to try the downgrade route, iow bump

---

### Post by kansasnoob on 2008-10-05
> **carolinason said:**
> i'm going to try the downgrade route, iow bump

Try what you want but the link posted by me and Arpanaut is a very good "fix" for pulse audio problems.

Then, as I said, if you still have flash/firefox crashing problems you can follow the steps I outlined to install Flash 10 RC.

---

### Post by carolinason on 2008-10-05
can't downgrade to ff2. dependancy issue and i don't want to force. tried epiphany, but it won't even let me log into ubuntu forums. :confused:

---

### Post by nolazabal on 2009-03-10
sorry i tried all i can now and nothing works, sorry ubuntu but i'm putting windows back on, see ya in a few years when this OS gets decent.

---

### Post by crjackson on 2009-03-10
> **nolazabal said:**
> sorry i tried all i can now and nothing works, sorry ubuntu but i'm putting windows back on, see ya in a few years when this OS gets decent.

Yeah, can't say I blame you. With all the requests for help you've posted and what not. It seems you have no choice.  BTW, Firefox is not Ubuntu. There are many browsers you can use if you don't like firefox.

---

### Post by Crafty Kisses on 2009-03-10
What are your system specs? I've also heard trying Opera is sometimes faster.

---

### Post by Tews on 2009-03-10
First .. *If* this is a request for help, how about help us help you.  Start off with a description that says something about your problem ... we are not mind readers.

Second ... Let us know what what you have done already to correct the problem ... that way we wont waste time suggesting something that you have already tried.

Third .... let us know what your system specs are ... what version of Ubuntu you are using ....

The members of the community are here to help but dont expect too much if you cant supply more information than you have.  I wish you luck with what ever system you decide on..

---

### Post by nolazabal on 2009-03-10
i just i'm trying to get away from all the crap in windows and gives a try but cant take it anymore for the last three days i've been dealing with with this problem, i have an old computer HP Pavilion using firefox 3. i was running XP in it with no problems just my son got it infected with virus but.

btw i know firefox is not ubuntu but i read places some say you have to talk to adobe, other that is the OS other that is the youtube itself, i cant deal with all of this sorry i just want a simple thing to work. 

let me tell you i dont like the idea of going back to windows since this looks very good and super fast, way faster that when i had windows but before i start punching and kicking my computer i have to change

> **Tews said:**
> First .. *If* this is a request for help, how about help us help you.  Start off with a description that says something about your problem ... we are not mind readers.

Second ... Let us know what what you have done already to correct the problem ... that way we wont waste time suggesting something that you have already tried.

Third .... let us know what your system specs are ... what version of Ubuntu you are using ....

The members of the community are here to help but dont expect too much if you cant supply more information than you have.  I wish you luck with what ever system you decide on..


is just specially in youtube firefox crashes, all the time. i most of read about a hundred different solutions about this, maybe i said this wrong, sry is just my frustration talking  


sry guys

---

### Post by kansasnoob on 2009-03-10
> **nolazabal said:**
> i just i'm trying to get away from all the crap in windows and gives a try but cant take it anymore for the last three days i've been dealing with with this problem, i have an old computer HP Pavilion using firefox 3. i was running XP in it with no problems just my son got it infected with virus but.

btw i know firefox is not ubuntu but i read places some say you have to talk to adobe, other that is the OS other that is the youtube itself, i cant deal with all of this sorry i just want a simple thing to work. 

let me tell you i dont like the idea of going back to windows since this looks very good and super fast, way faster that when i had windows but before i start punching and kicking my computer i have to change

sry guys

Well, I don't know what the problem is.

Give me a few minutes to review your previous posts!

You know, this was a very old thread you revived, so nothing from fall 2008 is any longer pertinent!

---

### Post by kansasnoob on 2009-03-10
Sorry, all I find is these two posts:

[http://ubuntuforums.org/search.php?searchid=56599722](http://ubuntuforums.org/search.php?searchid=56599722)

Maybe I'm missing something. Can you point to prvious posts that haven't been answered?

Or maybe start a new post being specific about your problems?

I'm pretty good at working thru Firefox probs.

---

### Post by nolazabal on 2009-03-10
> **kansasnoob said:**
> Well, I don't know what the problem is.

Give me a few minutes to review your previous posts!

You know, this was a very old thread you revived, so nothing from fall 2008 is any longer pertinent!

the problem is when firefox will crash when running flash in places like youtube after a few videos the browser will simply crash

> Sorry, all I find is these two posts:

[http://ubuntuforums.org/search.php?searchid=56599722](http://ubuntuforums.org/search.php?searchid=56599722)

Maybe I'm missing something. Can you point to prvious posts that haven't been answered?

Or maybe start a new post being specific about your problems?

I'm pretty good at working thru Firefox probs.

sry i never said i posted before, ive just read many other post about the same issue i have a tried all the suggested fixes and no luck.

PS: ty for trying to help, like i said before is just my frustration talking after not able to do such a simple task

---

### Post by kansasnoob on 2009-03-10
Well, it would be best to start a new thread in the future! It's also helpful to know what version of Ubuntu and Firefox you're using.

But please, in Firefox, go to Help > About. That should tell you what version of Ubuntu and Firefox you're running unless you've installed Firefox using something other than the repos.

You can also find out what version of Ubuntu you're running by going to terminal and running:

```
cat /etc/issue
```

Anyway one of the most generic steps is to install "ubuntu-restricted-extras" either by going to System > Administration > Synaptic Package Manager and clicking on Search, then finding and installing it or go to Terminal and:

```
sudo apt-get install ubuntu-restricted-extras
```

For new Ubuntu users I suggest getting used to Synaptic. You'll learn more that way! So go to synaptic as described above, then click on Search, then type "flash" without the quotation marks.

Scroll through that and make sure neither "gnash" or "swfdec-gnome" or "swf-mozilla" are installed. If they are mark them for "complete removal". Towards the bottom of the list you'll see "ubuntu-restricted-extras", you want to mark that for installation! then click on "apply"!

Now, back in Firefox, go to Tools > Add-ons > Get Add-ons and search for and install Flashblock 1.5.8. That will replace all flash objects by a button you'll need to click to display the object. If you don't like it you can always disable it and then decide whether you like it or not.

---

