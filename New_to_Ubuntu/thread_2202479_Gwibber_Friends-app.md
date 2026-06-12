---
title: "Gwibber? Friends-app?"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by fluctuatinganomaly on 2014-01-29
This is another new thread for me, and I guess people will be getting annoyed with me fairly soon. I'll just dive straight into the question I have. Hopefuly, I'm not being completely stupid here.

Right, basicly, on install I'm pretty damn sure I read a thing (on the install slide things) that said you can intergrate social sites like facebook etc and recieve popups and notifications relating to the site that generated the notification. Now looking into this I have seen that some application called Gwibber was the original and that it has recently been replaced by the Friends App. I have also read that at the minute you can't really get it installed on 12.04 due to depency issues and the likes, I can't remember the exact details, but it was along the lines that updating all the packages would effectively change a "precise system" into a "raring system" (this personaly means nothing to me :p)

reading more, I also saw mention of empathy, but as far as I can tell this is merely a chat program that houses multiple accounts for multiple chat applications (MSN, Facebook chat, irc etc.) I read that pidgen is something along the same lines?

I remember reading on the Ubuntu homepage on desktop version, that there is a Dash Message Lens? When reading about Gwibber and the Friends app, there was mention of a "Lens" I'm assumping some app that incorporates the gwibber / friends app of some sort? (I'm really not all that up on things) 

I guess, my question is basicly, what do I need for this notification popup feature?

I tried installing the friends app with "sudo apt-get install friends-app" but it couldn't locate it, so I can only assume I don't have the repositry added for it? in which case, how do I find the repositry (how do you know whats reliable and legit and what is potentially harmful?)

I also tried using the Gwibber app, but apparently it isn't set up correctly for use with facebook? maybe I've just done this wrong or something?

I haev been googling to find information on each and whats being used, but theres alot that I don't quite understand yet and alot that just isn't particularly substantial at answering what I need to be looking for / using.

I hope I'm not being too much of a pain in the ass and that I'm also not creating a completely useless, stupid and pointless thread.

~Matt

---

### Post by newb85 on 2014-01-29
Precise and Raring are two releases of Ubuntu.  Raring is newer, but just reached the end of its life.   Precise is LTS, so it will be supported three more years. 

Gwibber was replaced in newer systems, but if you're on precise, there's probably no need to upwgrade. Just use Gwibber.

---

### Post by fluctuatinganomaly on 2014-01-29
I have tried to use gwibber, but I can't get it to authorise my facebook account, after selecting facebook in the drop down menu and clicking add, I enter my login details, click login, then click to save this browser (because of my facebook security settings) then it comes up with 

[LEFT][COLOR=#333333][FONT=lucida grande]**Error**[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]App Not Setup: The developers of this app have not set up this app properly for Facebook Login.[/FONT][/COLOR][/LEFT]

surely thats not right, as other people seem to have been able to do it. I have searched for the error, and have only come across other account issues, but nothing relevent to my particular issue?

Could it be something to do with my current facebook security settings, like wanting to save the "browser" I'm logging in with?

~Matt

---

### Post by newb85 on 2014-01-30
Now that you mention it, I think there is a security setting in Facebook about what apps are allowed to log in.   I don't engender how to get to it, but if you can't find it, I'd suggest googling it.

---

### Post by fluctuatinganomaly on 2014-02-01
I've been looking for the setting that allows apps, not sure if I found it or not, I changed stuff in my settings, which was the only stuff to do with remembering log ins, browsers and trusted devices etc, and it still doesnt work.
I was wondering maybe, that because it got updated to the friends app in 2013 (according to a facebook page / wiki entry of gwibber) to the friends app, that maybe somethings have changed with the way facebook accepts / recognises login and authentication and that maybe due to not being updated, the gwibber app just doesnt conform to these new standards any more? It seems like a fairly logical explination in my head, but maybe I'm just grasping at straws?

I did have a look on the facebook developers site for anything "gwibber" or "Gwibber" but came up with 0 results on each term.

Either way, despite endles googling and searching, I still havent managed to find anything thats directly related to my particular issue. Everything is about not authorising correctly, or unsure if authourised. Nothing about the app not being set up properly.

I think I'm just going to give up with this, as it seems like a fruitless effort. Thanks for all your help regarding the issue though :)

~Matt

---

### Post by newb85 on 2014-02-02
Upgrading from precise to saucy (raring is no longer supported) would be a headache.   You'd have to upgrade three times. If you wait until April, you can upgrade directly from Precise to Trusty, since they're both LTS releases.

---

### Post by lunalui on 2014-02-19
Hi there,
unfortunately gwibber has been having several problems for a long time, notably with facebook. Someone had found a way to circumvent the problem with facebook: it worked fine for some time but now it doesn't any longer (check this [link]("https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1088775")). What's worse is that now (since mid January) gwibber does not work with twitter either: it is impossible to authorize twitter. Here you can find a bug report: [https://bugzilla.redhat.com/show_bug.cgi?id=1048349](https://bugzilla.redhat.com/show_bug.cgi?id=1048349)
I'm definitely not happy about this, since there is no alternative to gwibber available for precise and nobody cares to fix its bugs (although precise is LTS). The feature doesn't seem to be worth the effort for the developpers, since it will be soon discarded for good. 
All I can say is that I'm really looking forward to 14.04 and hoping for the best.

---

### Post by newb85 on 2014-02-19
> **lunalui said:**
> 
I'm definitely not happy about this, since there is no alternative to gwibber available for precise and nobody cares to fix its bugs (although precise is LTS). The feature doesn't seem to be worth the effort for the developpers, since it will be soon discarded for good. 

April 2017 isn't exactly "soon".

---

### Post by lunalui on 2014-02-19
> **newb85 said:**
> April 2017 isn't exactly "soon".

yes, you're right! they are giving us just one more reason to upgrade from precise asap  ;)
In any case, the way gwibber problems have been dealt with is definitely not in line with the way ubuntu usually works, according to my experience.
And it's a pity that no effort was made to make friends available for precise.
I've been using ubuntu for ages (and some variety of linux for even longer) and been extremely satisfied up to the release of precise, which, to be honest has been a bit of a let down in different respects. This is just a personal opinion, though.

---

### Post by lucianloonstra on 2014-03-10
Dear all, 

I experienced the same problems with the Gwibber app, and every now and then searched for a fix. Apparently someone found it, and it worked for me!

You can find the fix here:

[URL="https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1286639"]https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1286639

[/URL]

---

### Post by lucianloonstra on 2014-03-10
> **lucianloonstra said:**
> Dear all, 

I experienced the same problems with the Gwibber app, and every now and then searched for a fix. Apparently someone found it, and it worked for me!

You can find the fix here:

[URL="https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1286639"]https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1286639

[/URL]

Sorry, I was a little too enthusiastic, I got to the twitter login  screen and was able to authorizr twitter, but unfortunately I didn't see  any messages yet.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Update: it did work actually. I'm using gwibber again for some months now, and it works perfectly.

---

### Post by lunalui on 2014-03-14
> **lucianloonstra said:**
> Dear all, 

I experienced the same problems with the Gwibber app, and every now and then searched for a fix. Apparently someone found it, and it worked for me!

You can find the fix here:

[URL="https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1286639"]https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1286639

[/URL]

thank you so much for this! the fix worked for me, too... I'm happy about this: I was about to give up on gwibber altogether

---

### Post by DaniPhii on 2014-06-29
I don't know if I'll install Gwibber in 14.04 as I'm getting used to webapps, but I get bored of them I'll install it again (if it works).

---

