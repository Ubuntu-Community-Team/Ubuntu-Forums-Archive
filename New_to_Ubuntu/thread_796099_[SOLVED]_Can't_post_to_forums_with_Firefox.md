---
title: "[SOLVED] Can't post to forums with Firefox"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by dmub82 on 2008-05-16
Like the title says, Firefox under Hardy is now refusing to post messages to forums like this and others. I had to boot into Windows to post this.

I really have no more clues to give -- never happened before, haven't changed anything in Firefox that I can think of. Any ideas?

---

### Post by shifty_powers on 2008-05-16
assuming you're using firefox3beta5?

it is a beta after all, and can be prone to odd behaviour.

maybe try to uninstall3 and install ff2 or even opera.

```
sudo apt-get purge firefox-3.0
```

```
sudo apt-get install firefox-2
```

---

### Post by dmub82 on 2008-05-16
Yeah, I was just looking for something less drastic, I generally like the beta otherwise, and this just popped up out of nowhere. Hadn't had any issues with this before and I've been using the beta at the same sites for a while now.

eta: Oddly enough, this posted fine in Firefox. Maybe an only issue with longer posts or a comes-and-goes kind of thing?

---

### Post by shifty_powers on 2008-05-16
heh fair enough. what exactly happens when you try to post?

---

### Post by dmub82 on 2008-05-16
When it doesn't work (unlike now I guess), I click submit or preview and it's just "waiting for ubuntuforums.com" (etc.) for a minute or so until it times out.

---

### Post by shifty_powers on 2008-05-16
so it's working now?

when it doesn't work, try going to another borwser and submit from there.

will give us an idea whether it is something with firefox, or another cause...

---

### Post by dmub82 on 2008-05-16
> when it doesn't work, try going to another borwser and submit from there.

Long posts still not working in Ubuntu. I was able to create this thread and [another]("http://ubuntuforums.org/showthread.php?t=796098") in Windows, and was also able to post in another forum where I'd had problems in Ubuntu.

---

### Post by dmub82 on 2008-05-16
I had to split this reply in two because when I tried it all as one post it wouldn't go through. Size of post seems to be a factor. I don't have another browser installed in Ubuntu but everything seems fine in Windows. Think it's related to the browser, not the forums themselves.

---

### Post by NE Key on 2008-05-16
The implied invitation to us all is to try to duplicate your problem I am using Firefox  Beta on Hardy Heron and will no try a long post to see if I get the same symptoms. Not being prone to verbosity it be something of a challenge to generate enough gibberish to create a long post. The one you describe as having to split would seem to be of the order 7 lines.
How fast do you type - were you timed out for "pecking" at the keyboard too slowly ?
BTW do you have problems with Firefox crashing when changing videos at You Tube ? Hopefully that will be fixed in due course.
Is this post long enough ? Not being prone to verbosity it be something of a challenge to generate enough gibberish to create a long post. The one you describe as having to split would seem to be of the order 7 lines

---

### Post by omns on 2008-05-16
I've given up on the Hardy version of Firefox 3 and switched to the nightly build from mozilla. I'm having no issues with it

---

### Post by dmub82 on 2008-05-16
> **NE Key said:**
> [a long post]

Yeah when I'm having the problem this seems like it would be long enough to trigger it. And it wasn't an issue of how long it took to type, because after the first time I would copy a long post into a text document and just paste it into the box and hit submit a second later when I had to retry. {split}

---

### Post by dmub82 on 2008-05-16
{continued} Like I said this is one of those things that is really, really hard to nail down any specific conditions, and thus hard to fix. I was hoping maybe it was a known issue with a simple fix. Unless someone knowledgeable about the technical matters of how Firefox handles posting to a forum recognizes the issue, I doubt we're going to sniff this one out.

---

### Post by dmub82 on 2008-05-16
> **omns said:**
> I've given up on the Hardy version of Firefox 3 and switched to the nightly build from mozilla. I'm having no issues with it

Willing to try, if someone can link me a way to set that up so my preferences and extensions are preserved and I don't have multiple versions of FF all disorganized and conflicting.

---

### Post by dmub82 on 2008-05-17
Didn't try the nightlies but RC 1 isn't helping. Uninstalled, reinstalled, still doesn't work.

---

### Post by nowin4me on 2008-05-17
I will try it on Windows XP.
Hang on a secound.

---

### Post by nowin4me on 2008-05-17
I am testing the latest version of firefox on Windows XP to check if its Ubuntu or Firefox its self please DONT mark this as SPAM as I will reapeat myself a few times. Thank you for your copration.

I am testing the latest version of firefox on Windows XP to check if its Ubuntu or Firefox its self please DONT mark this as SPAM as I will reapeat myself a few times. Thank you for your copration.I am testing the latest version of firefox on Windows XP to check if its Ubuntu or Firefox its self please DONT mark this as SPAM as I will reapeat myself a few times. Thank you for your copration.I am testing the latest version of firefox on Windows XP to check if its Ubuntu or Firefox its self please DONT mark this as SPAM as I will reapeat myself a few times. Thank you for your copration.

---

### Post by nowin4me on 2008-05-17
I think it's a problem with Ubuntu if you have a look at my test up there you can clearly see that FireFox Beta  is working well.

So who's going to tell Ubuntu this problem?

---

### Post by dmub82 on 2008-05-17
Yeah I'm only experiencing the issue in Ubuntu; using FF3b5 in Windows I can post fine. Posting a bug report now.

Edit: Report is [here]("https://bugzilla.mozilla.org/show_bug.cgi?id=434214").

---

### Post by nowshining on 2008-05-17
did u have referring set to off in the configs? I had the same problem and after changing refcontrol to block by default and re-setting about:config referring option to the default fixed my issues. :)

u could of also went to FF2 or installed Swiftfox 2.x ([http://getswiftfox.com/br18.htm](http://getswiftfox.com/br18.htm)), etc...

---

### Post by dmub82 on 2008-05-17
Interesting, what's the name of the option you mean in about:config? I didn't see anything that looks like what you're talking about by searching or by browsing through my "user set" values. I'd be more confident if it wasn't for the fact that I can post short messages here but not long ones; that seems like a weird thing to implicate my referral settings so I'm kinda skeptical, but I'll give it a shot. {split}

---

### Post by dmub82 on 2008-05-17
{continued} I've gotten attached to a lot of the improvements in 3b5 so downgrading or switching to another browser is not an option I'd like to consider. I have to believe it's fixable since obviously most of the people who post here would have realized this if it was a fundamental fault in Firefox.

---

### Post by nowshining on 2008-05-17
all of ur settings/add-ons should be preserved when switching ver. of firefox, etc.. by the wey b = BETA.

---

### Post by dmub82 on 2008-05-18
Solved. It was... Firestarter. Not really sure how but stopping the firewall did the trick.

---

### Post by shifty_powers on 2008-05-18
well, tbh, especially if you have a modem/router with a built in firewall, then you don't need it anyway ;)

---

### Post by dmub82 on 2008-05-18
> **shifty_powers said:**
> well, tbh, especially if you have a modem/router with a built in firewall, then you don't need it anyway ;)

True.

---

### Post by shifty_powers on 2008-05-18
don't forget that firestart is not strictly a firewall anyways, it is just a configuration utility for iptables, which is part of the kernel iirc.

---

