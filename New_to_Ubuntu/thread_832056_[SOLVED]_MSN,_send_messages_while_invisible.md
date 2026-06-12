---
title: "[SOLVED] MSN, send messages while invisible?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by BlackDragonBE on 2008-06-17
Hi everyone,

This isn't really an absolute beginners question, but I don't know where else to post this:

I used WinXP and moved to Ubuntu about a year ago, I don't regret it at all, but some things are different of course, up until now however I found a good replacement for everything except Visual Studio which I use virtualbox for and Windows Live Messenger (using vb too).

Anyway, it's worth it to boot up virtualbox to do some programming but not for WLM in my opinion. All the linux-based messengers are fine, but I haven't found one that has my favorite feature of WLM, talking to people while remaining invisible..
I know I could just block all other people every time, but come on that's a bit of overkill, no?

What I want to know is: Is there a messenger that I can use (with wine even?) that allows me to talk while I remain invisible?

Thanks,
BlackDragonBE

---

### Post by ChildOfMana on 2008-06-17
Try aMSN

I use this myself but not to send messages while appearing logged-out.

It's in the feature list though so might be worth a go.

---

### Post by MasterSander on 2008-06-17
Yeah I use amsn as well with MSN Live Messenger skin, it's not exactly the same but it's one of the best out there. Mercury messenger is also very nice but slow.

And it supports invisible messages.

---

### Post by BlackDragonBE on 2008-06-17
I already use aMSN, it's quite good, but I can't send invisible messages with it like you said.
EDIT: It's really the sending while invisible feature I need, I know about aMSN, pidgin, mercury and others but none that has this specific feature.
EDIT2:Wow someone else from Belgium, hehe.

---

### Post by MasterSander on 2008-06-17
I believe I can. You do mean being offline and sending messages? (Launching aMSN now)

EDIT: I can.

---

### Post by ChildOfMana on 2008-06-17
Yeah I just tried it and I can too.

Are you getting any error messages?

---

### Post by BlackDragonBE on 2008-06-17
Whoa, you sure?!
Last time I tried it failed..
I'll give it a try, I'll be right back.
EDIT: Nope, he (my bro in the same chamber with a laptop) doesn't receive anything, and I get this:

[18:50:32] Er was een probleem bij het bezorgen van de volgende boodschap:
hallow

It's Dutch, the translation:
[18:50:32] There was a problem with sending the following message:
hallow

---

### Post by MasterSander on 2008-06-17
Yeah I did get that error message as well but I though it was because my mate had been idle too long. I'll try again.

---

### Post by ChildOfMana on 2008-06-17
Can't help I'm afraid.

I don't get any error messages and I can quite happily hold a conversation with a friend whilst appearing offline.

Sorry.

---

### Post by MasterSander on 2008-06-17
It seems you're right, because aMSN first tries to ping the msn server to open a conversation, but it won't do that because you're offline.I'm gonna try looking at the preferences to see if I can change something.

---

### Post by MasterSander on 2008-06-17
ChildOfMana, what amsn version do you use?

---

### Post by MasterSander on 2008-06-17
Just installed the last version of aMSN but still not working. Can't send offline messages.

---

### Post by ChildOfMana on 2008-06-17
Version 0.97

---

### Post by ChildOfMana on 2008-06-17
Just had a good look through my aMSN options and I can't see anything I've got enabled/disabled that might explain why I can send messages while invisible and you can't.

Have you opened port 6891?

I can't see this making any difference at all but it's the best I can come up with, sorry.

---

### Post by BlackDragonBE on 2008-06-17
That's weird.. I'm also using 0.97 but I can't.
There just has to be something that can enable this!

---

### Post by BlackDragonBE on 2008-06-17
> **ChildOfMana said:**
> Just had a good look through my aMSN options and I can't see anything I've got enabled/disabled that might explain why I can send messages while invisible and you can't.

Have you opened port 6891?

I can't see this making any difference at all but it's the best I can come up with, sorry.

When you're in a chat session while invisible, does it say "You're not online" at the bottom?

---

### Post by ChildOfMana on 2008-06-17
Yeah, pretty much. To be exact it says;

> You still are/appear offline!

Are you talking to people who are also using aMSN, or are they on an alternative client too?

Everyone on my friends list uses WLM (as far as I know).

Perhaps it might have something to do with different versions of WLM? Or even the settings of the person you're talking to? I'm just guessing now though tbh.

---

### Post by BlackDragonBE on 2008-06-17
All my friends use WLM, except maybe 2 who use Mac OSX.
I dunno about those settings, I guess only if they disable offline messages, but it works when I use WLM, so it should work with aMSN too, right?

---

### Post by ChildOfMana on 2008-06-17
> it works when I use WLM, so it should work with aMSN too, right?

Yeah, it should. Strange that it doesn't.

Are you logging in as invisible, or changing your status to invisible *after* you've logged in?

---

### Post by BlackDragonBE on 2008-06-17
I log in invisible.

EDIT: Never mind this, it's something totally different: 
{
Do you have anything at aMsn -> Account -> Preferences -> Advanced -> TLS ?
Just a thought, I really have no idea.
}

---

### Post by ChildOfMana on 2008-06-17
No, it's blank.

The only thing I can think of that we're doing differently is that (as I don't normally use the 'appear offline' functionality) I'm changing my status to 'appear offline' after I've already logged in.

I can't test it logging in as invisible at the moment as all my friends have gone offline, so no one to message :(

Try logging in as 'online' and then changing your status, see if that makes a difference.

I can't see why it would but to be honest this one's got me completely stumped - might be worth clutching at a straw or two eh?

---

### Post by BlackDragonBE on 2008-06-17
Nope I tried logging in as online, then changing to invisible but I still get that blasted error message.
I really have no clue what it could be that's different except for the language..
You might have other settings, but I can't find an option to send invsible messages anywhere.

---

### Post by ChildOfMana on 2008-06-17
I can't see any settings to do with it either - it just seems to work for me.

I'll wait until another of my friends logs in and I'll try a few things to see if I can come up with anything - I wouldn't hold out much hope though as I really haven't got a clue what it could be.

Sorry I can't help any more than that.

---

### Post by BlackDragonBE on 2008-06-18
Bump :)

---

### Post by Joeb454 on 2008-06-18
I'm going to be really lazy, jump in on the 3rd page and say this:

What MSN client are you using?

---

### Post by Tom--d on 2008-06-18
emesene!
use emesene.

It does offline messeages!

[www.emesene.org](www.emesene.org)

Also, in the repos! :D

```
sudo apt-get install emesene
```

---

### Post by BlackDragonBE on 2008-06-18
> **Tom--d said:**
> emesene!
use emesene.

It does offline messeages!

[www.emesene.org](www.emesene.org)

Also, in the repos! :D

```
sudo apt-get install emesene
```

Are you 100% sure about this?
Btw, I use aMSN for the lazy guy. :p
EDIT:
THANKS!!! It really works!! :D

---

### Post by Tom--d on 2008-06-19
Sure it does.
Why would I recommend something but doesnt work xD

No problem btw :)

---

