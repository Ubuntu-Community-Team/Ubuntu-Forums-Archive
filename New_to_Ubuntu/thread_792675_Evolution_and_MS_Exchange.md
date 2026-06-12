---
title: "Evolution and MS Exchange"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by pzs on 2008-05-13
Does anybody else use this combination? Do you find it to be total and utter sh*te? Mine has crashed 3 times in the last 10 minutes, either a hard crash or just losing connection with the Exchange backend process, which means it needs a restart. It usually crashes about 5 times a day.

It also often pauses for minutes at a time when opening new messages or moving messages between folders. Also, I hate the way it just hides junkmail by default, so if it thinks a message is junkmail you can't actually see it to say that it isn't.

I posted to the Evolution message board about the stability problems and poor performance and they told me to try the development version. This took a long while to get working and was exactly the same. I also got an earful for expressing impatience. Sigh.

---

### Post by SomethingCronic on 2008-05-13
I don't use it myself because of various reasons - I don't find it particularly stable either, however a couple of other guys use it at the office and thinks it's fine - if not better than Outlook.

I'm not a linux or Microsoft fanboy, but I do think Outlook is superior here - but then again it was built with Exchange in mind.

If you can open up imap ports on Exchange I would suggest using thunderbird or stick to OWA

EDIT
I just realised this is probably the most unhelpful post I ever given, sorry about that.

---

### Post by mankygitt on 2008-05-13
I use the Evolution/MS Exchange combination (when I have to) at my company.
I have noticed that Evolution has exactly the same sorts of limitations and performance problems that MS Outlook has. Therefore one must assume that much of this can be attributed to server-side functions or client-server transactions that cause client issues.

You can experiment with this if you wish by using Evolution as a POP client instead of a "Exchange" Client, which means you're downloading your email just like you to with your home ISP email account. This would tell you if it is server related.

I also use several other mail server platforms: MS Exchange is by far the poorest in features, stability, and quality. Maybe change companies: Choose one based on their choice of mail platform.

Email generally has contributed to a loss of productivity in corporate environments due to the inefficient and counter-productive way in which it is implemented. MS Exchange is one of the main platforms at the core of this. The cost to companies is ASTRONOMICAL.

You need to perhaps examine where Email really fits in what you need to do to be productive...

---

### Post by pzs on 2008-05-13
I can't control the Exchange server. Everybody in my office uses it for scheduling meetings so I need to use it too. Outlook and the web client work without crashing, so I think Evolution probably should too. 

Does anybody know what Evolution does when you press the "junk" button? The messages just disappear from the Evolution folder, but they're still there when I go to the web client. Along with it are all the non-spam messages that Evolution has tagged as Spam. Evolution has a "not-junk" button, but I can't see the point of it since I can't see messages that have been tagged as junk.

I have a "junk" folder, but it's empty.

---

### Post by fwre01 on 2008-05-30
The company i work for uses Exchange, my work colleagues and i would like to move to an open source environment (if we can sell it to the other ppl in the company) as i see it, exchange is performing 3 basic functions...

Email
Group based calendars 
Contacts database

The email part is this possible migration will (hopefully) be easy however, the other two parts perhaps not so easy, does anyone use any other open source apps that can replace the calendaring and contacts??

---

### Post by tytus on 2008-05-30
> **mankygitt said:**
> I use the Evolution/MS Exchange combination (when I have to) at my company.
I have noticed that Evolution has exactly the same sorts of limitations and performance problems that MS Outlook has. Therefore one must assume that much of this can be attributed to server-side functions or client-server transactions that cause client issues.


Not true at all. As much as I don't like MS, Evolution is much less stable than Outlook. Lets be hones about it.

> **mankygitt said:**
> 
You can experiment with this if you wish by using Evolution as a POP client instead of a "Exchange" Client, which means you're downloading your email just like you to with your home ISP email account. This would tell you if it is server related.


Most of people who I spoke to about Evolution are using it **only** because of calendaring. So POP is certainly not an alternative. And by the way if you don't care for calendaring IMAP would be much better option.

> **mankygitt said:**
> 
I also use several other mail server platforms: MS Exchange is by far the poorest in features, stability, and quality. Maybe change companies: Choose one based on their choice of mail platform.

Email generally has contributed to a loss of productivity in corporate environments due to the inefficient and counter-productive way in which it is implemented. MS Exchange is one of the main platforms at the core of this. The cost to companies is ASTRONOMICAL.

You need to perhaps examine where Email really fits in what you need to do to be productive...

I am sorry but this comments are totally frustrating. What are you talking about? The people using evolution exchange are using it because their companies are not giving them a choice. The talk about lost of productivity... I don't know even where to start. You may no like email but it is here to stay so let's stop taking about it's usefulness and just fix evolution so it WORKS!!!!

I am sorry if I get carried away.

---

### Post by ukripper on 2008-05-30
> **fwre01 said:**
> The company i work for uses Exchange, my work colleagues and i would like to move to an open source environment (if we can sell it to the other ppl in the company) as i see it, exchange is performing 3 basic functions...

Email
Group based calendars 
Contacts database

The email part is this possible migration will (hopefully) be easy however, the other two parts perhaps not so easy, does anyone use any other open source apps that can replace the calendaring and contacts??

you can do all of the above using citadel and there are many other alternatives. Citadel is fairly easy to configure and administer.

---

### Post by fwre01 on 2008-05-30
Ok, i shall take a look at Citadel. thanks

anybody else have any experience with trying to replace exchange with open source software?

---

### Post by pzs on 2008-06-02
> **tytus said:**
> I am sorry but this comments are totally frustrating. What are you talking about? The people using evolution exchange are using it because their companies are not giving them a choice. The talk about lost of productivity... I don't know even where to start. You may no like email but it is here to stay so let's stop taking about it's usefulness and just fix evolution so it WORKS!!!!

I am sorry if I get carried away.

I would like to give you a big hug for this comment, which I completely agree with.

The two applications I rely on most (and this is probably very common) are my Email client and my web browser. Under Ubuntu, Evolution, the default Email client, let's not beat about the bush here, *does not work*. 

I recently returned from a holiday and sorted my Email using Evolution. I set it to move 4 or 5 messages into a folder and then I literally went away and made a cup of tea and it hadn't finished by the time I got back. I put up with this every day, because it's the only way I can, as you say, use an Exchange aware calendar/Email system under Linux.

If we, as in the OSS community, want people to use Ubuntu, we should seriously be pouring an awful lot of effort into fixing Evolution or finding an alternative. I think effort on a *working* default Email client is worth 10 or 100 times more than work on pretty sounds or backgrounds or nice multi-media applications. Lots and lots and lots of businesses use Exchange servers and would leap at a drop-in replacement for Windows/Outlook. But Ubuntu is not it while it relies on Evolution.

The other thing I am sick of is when I express frustration like this on message boards I get told to "stop being so negative", "fix it myself" or "appreciate that it's free". Dude, you try not being frustrated when it takes you 10 minutes to move messages between folders. Stuff that worked really well in Pine 10 years ago simply does not work in Evolution. Yes, I know that there are fancy protocols underneath that are different - I don't care I just want it to f***ing work.

(calm down, calm down...)

---

