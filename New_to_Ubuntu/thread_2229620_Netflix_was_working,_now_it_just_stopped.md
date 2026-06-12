---
title: "Netflix was working, now it just stopped"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by Ben_Cook on 2014-06-14
So, after many questions on here I was able to get netflix working.  I hadn't used it for a couple of weeks, and when I went on, it wouldn't play video anymore.  Is this because of the html5 update thing for netflix?  I have the restricted extras package and silverlight is working.  I don't really know where to go from here

---

### Post by SeijiSensei on 2014-06-14
I just checked to see if Netflix still works for me using pipelight and had no problems, Ben.  Have you updated recently?  I've seen new versions of wine-compholio and pipelight appear over the past few days.  I'm using the most recent release of Flash for Linux as well; that appeared yesterday as I recall.

---

### Post by Ben_Cook on 2014-06-14
Ah..no I haven't.  I am just about to head out to work (on a beautiful sunny Saturday :( ).  But I will update when I get home this evening.  As you know, I know very little about linux, so can I get the update through the terminal.  Something like sudo apt get-update?  Or am I way off base haha?

---

### Post by SeijiSensei on 2014-06-14
```

sudo apt-get update
sudo apt-get upgrade

```
The first command checks all your active repositories to determine if they have updated lists of packages.  The lists are then downloaded as needed and compiled to create the database of packages stored in /var/lib/apt.  The second command does the actual update, downloading and installing any new packages.

You can do all this with a GUI package manager, too, but I prefer the detailed reporting I get from the command prompt.

Sometimes you will see packages that are "held back."  Usually these are new operating system kernels.  In most cases you want to install these as well, so when you see held packages, you can cancel the upgrade and use "sudo apt-get dist-upgrade" instead.  You'll need to reboot whenever you update the kernel, and if you have proprietary graphics drivers or programs like VirtualBox that require custom kernel modules, you'll need to have installed the **dkms** package so the upgrades can compile and install new kernel modules.

---

### Post by monkeybrain20122 on 2014-06-14
How does it not work? Does silverlight work at all, or is it just netflix? Go to [http://www.iis.net/media/experiencesmoothstreaming1080p](http://www.iis.net/media/experiencesmoothstreaming1080p) to test if silverlight works.

If you have an AMD card it may be because pipelight now enables hardware acceleration by default [https://answers.launchpad.net/pipelight/+question/250132](https://answers.launchpad.net/pipelight/+question/250132)

---

### Post by Ben_Cook on 2014-06-14
I did the update, but still nothing.  I tried the silverlight test and I again get nothing.  Netflix worked last time I used it.  I just don't understand.  All I really want to do is watch the world cup, which is live streaming (legally!).  I restarted the computer after installing the updates

---

### Post by monkeybrain20122 on 2014-06-14
You did not answer my question. Do you have an AMD card?

---

### Post by yancek on 2014-06-14
Which browser are you using?  You generally need to use User Agent Switcher software to identify as a windows browser.

---

### Post by monkeybrain20122 on 2014-06-14
> **yancek said:**
> Which browser are you using?  You generally need to use User Agent Switcher software to identify as a windows browser.
Yeah that is a good point. It doesn't work on Chrome/Chromium any more because google has pulled the plug on all NPAPI plugins.

---

### Post by Ben_Cook on 2014-06-14
Sorry - not AMD, it's Intel.  And I'm using firefox with a user agent switcher.  About two weeks (or less) ago I could stream everything fine, but now I just get a blank screen

---

### Post by monkeybrain20122 on 2014-06-14
Well in that case may be just start afresh.
Close Firefox
In the terminal
```
sudo pipelight-plugin --disable silverlight
```
(use 'sudo' only if you enabled silverlight with sudo, otherwise leave it out)
Then open the file manager at your home directory, press ctrl+h or choose 'show hidden files' from menu, find the hidden folder .wine-pipelight, delete it.
Then in the terminal
```
pipelight-plugin --enable silverlight
```
Open Firefox, let the silverlight installer does its thing and try again.

---

### Post by Ben_Cook on 2014-06-14
OK, so I was about to say I will try reinstalling firefox in the morning when I decided to check if everything was ok.  Somehow, I no longer have a user agent switcher.  I know it was there before but it seems to have disappeared.  I put one on but I don't remember what to put in for a user agent string.  Could this be my problem?

---

### Post by Ben_Cook on 2014-06-15
Tried to disable/enable silverlight, but it said command not found.....so I guess it's not on there after all.  But it WAS on there, same as the UA switcher.  It seems everything has disappeared, so I will start anew and put silverlight back on. :mad:

---

### Post by Ben_Cook on 2014-06-15
Ok, I have silverlight working, my UA string is - "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:18.0) Gecko/20100101 Firefox/18.0".  Still getting that dreadful minimum requirements screen for netflix.  But, it seems like the other video sites are working now.  I still have no idea what happened to silverlight in the first place, but it's back on there now

---

### Post by yancek on 2014-06-15
I installed wine-pipelight on a friend's computer a week ago.  I tested it at several silverlight test sites including the microsoft silverlight site and they all worked.  I don't have a subscription to netflix so could not actually test that.  I spoke with him earlier today and he indicates that he still gets positive results from the silverlight test site but going to netflix gives him the same page you refer to about minimum requirements.

If we come up with any positive results, we'll post here.

---

### Post by monkeybrain20122 on 2014-06-15
> **Ben_Cook said:**
> Ok, I have silverlight working, my UA string is - "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:18.0) Gecko/20100101 Firefox/18.0".  Still getting that dreadful minimum requirements screen for netflix.  But, it seems like the other video sites are working now.  I still have no idea what happened to silverlight in the first place, but it's back on there now

Which UA switcher do you use? Use the user agent overrider and set it to Windows/Firefox 26 should work.[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)

---

### Post by trag on 2014-06-15
I have had some weirdness with netflix as well. do the usual update/upgrade via terminal then sudo these two instructions next. sudo pipelight-plugin --enable silverlight


sudo pipelight-plugin --enable widevine.

good luck
tragic

---

### Post by monkeybrain20122 on 2014-06-16
> **trag said:**
> I have had some weirdness with netflix as well. do the usual update/upgrade via terminal then sudo these two instructions next. sudo pipelight-plugin --enable silverlight


sudo pipelight-plugin --enable widevine.

good luck
tragic

You don't need sudo.widevine has nothing to do with netfix.

---

### Post by Ben_Cook on 2014-06-16
[**[COLOR=#000000]@[/COLOR]**[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1843403") 				 				 					 						 	[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403")  - changing the user agent overrider did the trick, I couldn't remember  what I had last time.  Anyway, it works.  Again, thank you for your help  everybody. Without you, monkeybrain20122 and seijisensei, I don't think I could use linux so thank you.  Best community ever!

---

