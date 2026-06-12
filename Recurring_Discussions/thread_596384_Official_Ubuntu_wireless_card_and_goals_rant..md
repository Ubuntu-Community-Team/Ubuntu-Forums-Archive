---
title: "Official Ubuntu wireless card and goals rant."
date: 2007-10-29
forum: Recurring Discussions
---

### Post by Innomen on 2007-10-29
Since the sticky/wiki is worthless... I'd like to know what wireless pci card to buy.

Everyone looks so smart when it comes to posting links to...

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)
[http://www.Google.com](http://www.Google.com)
(or other threads)

... and everyone is so quick to say "Well if you're having trouble with that broad com card, just buy a 10$ card that Ubuntu will see".

I'd like the community to quit linking to other people's work when that work is not useful, if you guys can write a tutorial, then write an app, if its so easy and straight forward. If the tutorials are so good, then why cant they be batch files? Ignorance is not stupidity, and I'm tired of seeing people talked down to like not being born with Linux in the cradle is somehow a personal flaw. I have a decade of professional computer and tech support experience, I am not the problem here, and nor are most users.

This demand for continuous duplication of effort is unrealistic and elitist. Just because ***you*** had to walk to school and use a slide rule does not mean the rest of us should have to. Prior art is the foundation upon which all technology is built and this applies to Ubuntu. A Tutorial is not a solution, its a stop gap until a real solution is found. The community needs to acknowledge this. The standard defenses/apologies for why Linux is an unusable, impractical, specialist, piece of crap, do not apply here, as this is intended for normal users... "Linux for people." Remember? So don't tell us we should prefer CLI, don't tell us we should be comfortable with compiling our own ware. These are OPTIONS not requirements.

Transparency and ease of use should be primary goals. 

First, The install/upgrade process should be number 1. As no matter how cool the floaty cube desktop looks, if you can't install it what does it matter? The automatic recommended upgrade from fawn to gibbon irrevocably broke my system, and I'm not alone, I go mention this in the chat and I get 15 flavors of "thats what you get for upgrading so soon"... If its not ready, don't recommend it. Period. The installer is the first impression, it should be flawless.

Second, and here's where my problem was generated as a result of the first step being ignored... true support for networking hardware. We need an automated NDISwrapper equivalent, maybe even a repository of windows WIFI card drivers. Imagine it... "X unsupported card detected, installing NDISwrapper, downloading driver, configuring driver and card, installation complete."

Everything else should fall under these two in terms of priority. 

Again, a tutorial should not be seen as a final solution to a problem. A true solution is transparent.

Having said all that here is what I and many others would like.

A link (new egg/tiger direct/etc) to a PCI card that will work natively with Ubuntu and windows XP, with full support for WinXP, WEP, and whatever encryption Ubuntu prefers to use for under 15$. If you think there are too many choices that fall under that category then pick the cheapest.

In short I want a link to what should become the official Ubuntu wireless card... until such time as Ubuntu is grown up enough to support the majority of wireless cards out of the box. Windows users are happy with downloading drivers, Ubuntu took it upon itself to be totally automated with regard to hardware, I would never have demanded this, (hence the total lack of a GUI device manager), and given that choice of paths, this demand is not unreasonable.

And if I don't get this... If I get a link to a tutorial... If I get some smug insult about how I'm an insect mind because I don't speak c++ in my sleep... If I get a personal attack of ***any*** kind... Then I'm walking away from Ubuntu forever, as it will have finally proven itself to be just another Linux Distro, jam packed with elitists and complexity, totally devoid of practical value as a normal user windows alternative. And I will share this opinion to anyone whenever the subject of open source comes up, both professionally and personally. 

We are a society of specialists, everyone is ignorant about something, we should not be required to learn extraneous data, or duplicate effort. The computer itself was designed to protect humanity from tedious repetitive tasks. 

Thank you for your time.

---

### Post by wirelessmonkey on 2007-10-30
Welcome to the COMMUNITY forums....... Please be nice, not everybody is a super elite ultra professional.

While I don't like your tone, I'm happy to get you as close to your goal as I can.

Here's one! [http://www.newegg.com/Product/Product.aspx?Item=N82E16833320022](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320022)

$2 more expensive than you wanted, but ASUS has a native linux driver for it on their site.


Personally, I suggest the Netgear WG111 v2  USB wireless adapter.  It worked out of the box for me in Feisty, and in Gutsy was fully configurable from Network Manager (WPA, etc).

Best of Luck, and remember that Linux is NOT Windows.  Don't expect it to work the same.

---

### Post by SactoBob on 2007-10-30
I don't like your attitude much either.
But see [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

In that post I helped a guy who put the problem courteously.
It will explain why wireless problems exist (because manufacturer's won't release info) and what you can do to avoid the problem (get a wireless bridge)

---

### Post by brightspark on 2007-10-30
Hi,

   I am so pleased to read your post, as it highlights a fundamental problem for the take up of Ubuntu in the home market. I have struggled for the past 2 weeks trying to connect to the internet with a wireless card.   Installing new  software is fine with synaptic or the terminal.Success depends for the most part, on the internet and repositories.Home users expect a quick result if they are not  linux enthusiasts.  
Critics of my views, say it is the fault of the hardware not providing Linux drivers. linux is trying to compete in the home desktop market as an OS to upgrade to. It therefore should expect internet connectivety  issues.How can the ordinary Ubuntu user find help ? The local pc doctor would probably be unable to help,the user  then has  to search never ending  forums with the risk of failure? The problem is confined to external devices. if you don't need them, Ubuntu has all you need.
Part of my frustration is the fact I love Ubuntu, I want to use it. I don't want a dual boot machine.I hope  that is not too far off.

---

### Post by JoJerome on 2007-10-30
I too am a long-time Windows user with a networking degree under my belt and plenty of paychecks for techie services, and I too am pretty new to Linux, currently converting someone's laptop to Linux and ran into the won't-talk-wireless issue.

My experience here has been different from yours however. No one's talked down to me and most all of my questions have been answered. My only complaint of the tutorial I followed on this site...
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
...is that it would be nice if it started with showing us Linux newbies how to first scan for what we already had. Turned out my 2 week adventure with ndiswrapper was unnecessary. 7.10 found the wireless card just fine - it just needed 3 short lines of code to configure the networking. 

And if I understand you correctly, therein lies a core issue. "Why should we even need those 3 little lines of code?"

As I understand it - and someone feel free to correct me if I'm wrong - that little extra need for user manipulation is part of what makes Linux so secure in many ways. The fact that you *can't* have a generic program written to do major brain surgery on anyone's kernel with a simple, I-don't-want-to-know-the-details press of a button.

Also as I understand it, part of the problem lies in a world collectively geared towards Microsoft. Mac users once (and sometimes still do) had these same issues with components and programs that only play nice with Windows ... almost as if someone out there was planning it that way.

Me, I found the manual manipulation needed to get the wireless card working a very small price to pay and further inspiration for never having to give Micro$oft another dime of my money again. (See above re; 'almost as if someone out there was planning it that way'). But I can understand and accept that not everyone feels the same. For some, security issues, cluttered registries, expense, an endless array of "Are you sure you're not too dumb to perform this task?" pop-up-boxes and generic programs that sometimes kill your PC while performing automated brain-surgery are a small price to pay for having said programs be fully automated when they do work and not having to learn GIMP in place of Photoshop.

It's all a matter of which headache annoys you the least.:)

- Jo

---

### Post by JoJerome on 2007-10-30
As a P.S....

In this thread - [http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857) - kevdog, the author of a few of those tutorials, is looking for feedback on wireless issues. Presumably to make said tutorials that much brighter and better. 

- Jo

---

### Post by potentia on 2007-10-30
+1

I agree 100 % with the original poster.

---

### Post by kevdog on 2007-10-30
Hmm...You do know that no one hear posting in the forums is not receiving any money for their contribution??

Rather than complaining, why dont you take the initiative and make the wireless installer for the thousands of wireless devices out there and ones yet to be released.

Is it my job to provide you with an automated installer??  Or is it Ubuntu's??? Seriously the OS is free and manufacture's of wireless cards dont provide automated linux installers.  Even if there was an automated installer, what would you do when your wireless connection breaks after an upgrade or for no apparent reason?? Reinstall the card -- or troubleshoot??

No one claimed Linux was windows and some things require a little effort to get up and running.  That is kind of the way it is right now.  The trade off is that although its a rough introduction to the command line and linux, you actually LEARN SOMETHING that is going to help you in the future.  

Ive heard this rant from many people prior to you!! Stop complaining and contribute if you want to make a difference.  All I can do right now is make HOW-To's since this really isnt my job. Sorry all the people making the HOW-TO's are not programmers, rather people who have wasted many hours and wanted to pass their knowledge along.

Your complaints are total BS unless you are willing to make a difference!

---

### Post by UI-Freak on 2007-10-30
I agree with the OP as well. And hey, you learn absolutely nothing from working with Linux that will help you unless you are a computer wizard.

Wake up, lads, the world of tomorrow is automated. People do not want to re-enter 1985.

> 
Sorry all the people making the HOW-TO's are not programmers, rather people who have wasted many hours and wanted to pass their knowledge along.
EXACTLY! Wasted! How many people WASTE time and youth struggling with all these problems? How many won't find this knowledge? An OS user is not supposed to be part of a "community" to use an OS.

[IMG]http://mytsoftware.com/misc/linux2.jpg[/IMG]

---

### Post by aysiu on 2007-10-30
I don't know. I [asked for advice on what wireless card to get](http://ubuntuforums.org/showthread.php?t=302984), and I got good advice. The general consensus seemed to be Intel Pro Wireless 2200. I got it, and it's worked wonderfully with Ubuntu (no config file tweaking, no *ndiswrapper* crap).

Nobody talked down to me or just sent me a link.

---

### Post by kevdog on 2007-10-30
Dont complain unless you are willing to take action to change things. If you are not willing to take action, then go back to windows and have them change your mind for you!  If you dont want to be part of the ubuntu os community - Great I respect that -- but then don't waste your time here in the forums with the community complaining.  You cant have it both ways.  Im fairly certain rants expressed in this post are in no way going to influence the developers of future editions.  Im fairly certain they are aware of some of the OS limitations and are working to improve the situation.  Be a force for change and not one of complaint and a victim mentality.

---

### Post by adamorjames on 2007-10-30
> **kevdog said:**
> Dont complain unless you are willing to take action to change things. If you are not willing to take action, then go back to windows and have them change your mind for you!  If you dont want to be part of the ubuntu os community - Great I respect that -- but then don't waste your time here in the forums with the community complaining.  You cant have it both ways.  Im fairly certain rants expressed in this post are in no way going to influence the developers of future editions.  Im fairly certain they are aware of some of the OS limitations and are working to improve the situation.  Be a force for change and not one of complaint and a victim mentality.

:D I agree completely.
EDIT: To the thread starter... Linux is still growing a lot in many ways. You can voice yourself in a nice way, stay quiet or leave.

---

### Post by UI-Freak on 2007-10-30
Oh no, that is not how it works. Every manufacturer of any given product must LISTEN to his customers whatever kind of feedback they get. Feedback is always welcome, even if people can't or won't help.

And why? Think of all the people that didn't like Linux for reasons mentioned by the OP. His feedback is interesting. Any criticism is important. Linux has a long way to go and an insignificant user base. I am sure that the developers and the community has a lot to learn. It would be a shame to say that Linux is innovation driven. So far Linux and the software for Linux is struggling to catch up with Windows and OS X, yes even to get it working.

Try reading the OP once again. Perhaps it is aimed at you and perhaps YOU can learn something.

Put an ear to the ground and LISTEN now and then.

---

### Post by kevdog on 2007-10-31
The original poster is a total newbie.  How long do you think he tried using Ubuntu before he voiced his complaints?? How much effort do you think he put into his problems?  Did you learn how to use Windows in 30 minutes?

> Put an ear to the ground and LISTEN now and then.

Hmm, not sure if I quite understand the meaning of that saying but yea I will try to do that sometime.  Maybe it will muffle out all the complaining I'm only hearing from you!

> Try reading the OP once again. Perhaps it is aimed at you and perhaps YOU can learn something

Oh yea -- I forgot about that lesson -- complain without actually being part of the solution.  Just be the victim and complain.  I remember someone trying to teach me that lesson once, but I quickly forgot about it!

---

### Post by UI-Freak on 2007-10-31
I gave Linux 2 and OpenOffice 5 YEARS, reported TONS of bugs and feedback, and I still face big problems all the time, while OpenOffice is still where it was in 2002.

The solution is still not in sight. Upgrading Linux still smashes the previous finally working solution and people still recommend that I follow page long HOW TO's and compile software. I can act as a participating member or as a victim, but the result is the same. 

Does it matter that the OP is a "total newbie" ? What kind of users do you want to attract? Linux needs to be as user friendly as anything else, and the community must accept that the rest of the world will expect it from their OS.

---

### Post by JoJerome on 2007-10-31
kevdog - I for one wholeheartedly appreciate your how-tos and feel your time was not at all wasted. I see you putting up posts asking for feedback, which tells this newbie to the forums that you are not at all an elitist talking down to folks. I'm not sure who, if anyone, actually gets paid just to develop Linux.

All - I can appreciate the Original Poster's frustration (voted 'a little of both'). Especially as we've become so used to point-and-click-and-have-the-program-do-the-rest. Although I'm not a fan of the tone and the implication that the folks on this forum had better do something about Linux's flaws, "Or I'm never talking to you again! {Stick out lower lip, whip around dramatically and stomp into the next room to pout}"

- Jo

---

### Post by aysiu on 2007-10-31
> **Innomen said:**
> 

"Nobody talked down to me..."

Was this before or after you became forum staff? It doesn't matter. I've been afford equal amounts of respect and disrespect regardless of my staff status.

> Edit: Wow, thank you, for moving my thread to... a place for ideas, and I quote,  “that are not based on merit or logic.” 

I could not have devised a way for you to prove my point about being talked down too so splendidly. . And you have proved my point here as well. If people want to talk down to me, they will. They (you, in this case) don't care if I'm staff.

---

### Post by Innomen on 2007-10-31
"It doesn't matter. I've been afford equal amounts of respect and disrespect regardless of my staff status."

Neither of us actually believe that, but hey, say what you gotta to win. [URL="http://myspace-527.vo.llnwd.net/01321/72/51/1321511527_l.gif"]I understand how mods have to be when there is an audience.
[/URL]
"And you have proved my point here as well. If people want to talk down to me, they will. They (you, in this case) don't care if I'm staff."

So pointing out an abuse of power is talking down to you? 

Noted.

But you are right, I personally don't care. You've killed my goal already by burying my thread. 

I'll just count it as a moral victory. Your move as was unfair as simply editing my words, deleting my account or some other abuse. And before you quote at me, I don't care if your actions were or were not in violation of the rules you and your fellow mods made up, ethically your actions were underhanded.

However, I still don't have my link. Which means I still have cause to post in the networking forum, where this thread belongs. I suppose I could just post again, mentioning the same issues, would you move that one as well?

But it's ok, I understand. 

Curious, did you see what I said about draconian moderation? Seems particularly apt here don't you think?

---

### Post by UI-Freak on 2007-10-31
>  UI-Freak
Were you a in student government/journalism also? 

I met your type rarely but was always gratified as a result.How could you guess? I have worked in a government organization and  also with communication (in a similar org).

Let them stay in their dreamworld thinking that their OS (ideology to some) is "the best" - market shares tells another story. Save yourself.

---

### Post by adamorjames on 2007-10-31
To UI-Freak: I wouldn't say Linux is the best OS but I do think it is great for me and is becoming a bigger competitor to Windows and Mac as time goes on.

---

### Post by UI-Freak on 2007-10-31
> **adamorjames said:**
> To UI-Freak: I wouldn't say Linux is the best OS but I do think it is great for me and is becoming a bigger competitor to Windows and Mac as time goes on.

Indeed, but you are capable of seeing things in a more objective light than many others. I am glad that it is all you need. I can of course see that it is a free gift to many, but unfortunately not to a much bigger group.

---

### Post by Dimitriid on 2007-10-31
> **kevdog said:**
> Dont complain unless you are willing to take action to change things. If you are not willing to take action, then go back to windows and have them change your mind for you!  If you dont want to be part of the ubuntu os community - Great I respect that -- but then don't waste your time here in the forums with the community complaining.  You cant have it both ways.  Im fairly certain rants expressed in this post are in no way going to influence the developers of future editions.  Im fairly certain they are aware of some of the OS limitations and are working to improve the situation.  Be a force for change and not one of complaint and a victim mentality.

The level of commitment you demand is unrealistic for virtually all end users. As long as all  the essential decisions are made only by a handful of developers your opinion will matter little or not at all if you are not part of said group. 

And no, asking for "tips" and "ideas" is not really taking into consideration a meaningful opinion, and until then to many of us, some things will forever remain broken or have a ridiculously high potential to be broken, in the specific case of this thread, Network Manager.

So as long as it is the default tool when we know there is at least 1 tool more stable and reliable ( wicd ) my tips and ideas will be wasted on what its has been really faulty and unreliable piece of software.

If im not willing or able to spend the kind of time to be an active developer and have my voice count, I'll just find a distro that fits my need. The moment I am not able to do that is the moment I would stop using Linux altogether. But I am able to, and we will leave, and your appeals to basically beg and worship a few developers won't work, I refuse to be manipulated with such a guilt trip.

Ubuntu being popular doesn't equates to the best distro or a necessity to actively support it. In fact a few more releases like Gutsy that go backwards and break fundamental hardware functionality like Networking and it won't even be the top dog anymore. That is motivation enough for the developers to get things right, since for Canonical employees it means keeping their jobs.

---

### Post by luisjorge on 2007-10-31
I agree, Linux is not the best OS yet, and Ubuntu might not be the best distribution, but for the use I give it, it's the best option FOR ME. I have been using Windows for a looong time now, and yes, there are some installation aspects that are better thought out than in Ubuntu, but there are also many others that happen to be better in Ubuntu than in Windows.

I too upgraded from Feisty to Gutsy, and nothing worked. I simply put everything on my windows partition, did a clean install, and everything works flawlessly now. Yes, maybe I shouldn't have had to do that in the first place, but hey, no one ever has said that Ubuntu or any Linux distribution is already perfect, flawless and the best system you could have.
It also depends very much on each person. Some may like it, some may not. Some people may be more patient, others are not so.

I use Ubuntu because it works for me. Maybe, with time, Ubuntu or other Linux distros will become as easy to use (or even more) than Windows or Mac. And if that happens (which I'm sure it will), it will be thanks, in part, to the community. You might say we are not supposed to have this OS as a job. Well, it isn't. 
No one here has been forced to help other people or make tutorials, but that's the whole point of open source, I think. That's the difference between Linux and Windows. That every single person that uses the system or software, can make a difference. I'm pretty new to Linux myself, and obviously do not know anything at all about c++ or python or those things I don't really understand. I'm really grateful with people like kevdog that have spent time posting in this forum solutions (or as you might call them, temporary non-definitive solutions) that they themselves have found by playing with their own machines for quite some time. It is something that makes this community really a community. Sharing this information, and in fact, any useful information is the first step towards community.
Currently, I had to use CLI a couple of times in Feisty, but I haven't had to use it once in Gutsy. Maybe I got lucky, maybe it was the clean install. Maybe my specific hardware is well supported by Ubuntu, which is great. Feisty didn't work well at all with my graphics card, and a new release does perfectly. So I think is all a matter of time. Ubuntu is relatively new, and I remember having A LOT of problems with my hardware with earlier releases of Windows, even if my PC had the system pre-installed. I remember going through hours of searching the right drivers for my hardware, downloading, installing, realizing it didn't work, then doing all that again to get it finally up and running. I didn't have those problems with Windows XP, and the same thing has happened with Gutsy for me: no problems at all.
I also remember having certain piece of hardware that NEVER worked with XP, and did work with Ubuntu.

So there you are, maybe Ubuntu doesn't have the experience of Windows, but it certainly is advancing. And they are updating things that people want to update: people asked for a GUI Xorg configuration tool, people got it with Gutsy. 
And talking about new releases of systems smashing previously working configurations, I know quite some people that have had that same problem, with the new Windows Vista, and not with Gutsy.

And, Innomen, you are completely free to speak your mind and say what you feel. In fact, please, do! Still, I think there are certain ways in which you can still express what you feel without insulting other people's efforts, freedom of choice and tastes! If you really can't stand Ubuntu, then PLEASE don't use it. If you feel like testing it in some time, to see if it's better, welcome back. If you don't want to use it ever again, be my guest. And believe me, no one here feels threatened by you not using Ubuntu anymore, or by you telling your friends and clients that Ubuntu and Linux is rubbish. 
I'm sure you live in a free country. Ultimately, it's a free world. Do with your life and your computer whatever you like.

If you want to announce it, tell your parents or your friends, go out to the streets and shout it out loud. 
If you really want to help someone here, then post in this forum, and save your growling for some other place, or the Canonical phone number.

---

### Post by somersetsimon on 2007-11-01
> **wirelessmonkey said:**
> Welcome to the COMMUNITY forums....... Please be nice, not everybody is a super elite ultra professional.

While I don't like your tone, I'm happy to get you as close to your goal as I can.

Here's one! [http://www.newegg.com/Product/Product.aspx?Item=N82E16833320022](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320022)

$2 more expensive than you wanted, but ASUS has a native linux driver for it on their site.


Personally, I suggest the Netgear WG111 v2  USB wireless adapter.  It worked out of the box for me in Feisty, and in Gutsy was fully configurable from Network Manager (WPA, etc).

Best of Luck, and remember that Linux is NOT Windows.  Don't expect it to work the same.

Hi,
I also have a WG111v2 adapter. With Feisty it worked immediately, but with Gutsy I couldn't get it to work no matter how much I fiddled around with settings in Network Manager. At best it would start to work, but the network connection would be desperately slow. What was your process for getting it working?

PS I won't be able to test any new suggestions for a while - the power supply on my Linux box popped as I was about to revert to Feisty :-(

---

### Post by Innomen on 2007-11-01
Well, I did have a detailed reply here, but they deleted/moved it because apparently they can define stating your opinion, if it's critical of the forum's moderation, or Ubuntu itself, as 'rude' or 'disrespectful', and therefor move/delete the post.

They even gave me an "infraction" point. 

Ironically, in the post that was removed, I specifically mentioned just that sort of reaction.

But it's ok. As an American I've grown accustomed to this particular brand of 'free' speech, the kind where you can say whatever you like so long as everyone likes what you say.

So, to everyone who had things to say to/about me I'm sorry I cant respond and thank those who need it and rebut the rest. But hey, at least the latter group can stab away at me with impunity. The last word sure is fun isn't it.

Edit: They didn't delete it, they moved it to someplace called "The Jail", I'd link to it, but I'm sure they'd see that as an evasion, since clearly they don't want people to see what I said. It's Tremendously amusing to me that I discover my speech in 'jail' just after I comment on the unfree nature of speech on this forum lol.

---

### Post by matthew on 2007-11-01
I read your entire first post in this thread as well as the one in the jail about which you are complaining. I have one thing to say...

Please read the link in my signature titled "what's a troll." I think you will find the second post in the thread particularly interesting, especially the descriptions of The Old Warrior and The Sophist.

---

### Post by Innomen on 2007-11-02
I thank you for officially calling me names now, on top of the previous oppressions I've suffered, and instead of actually attacking my points. 

You want to make this about me, because if it was just about my ideas, my logical position, you would not stand a chance in a fair debate. Which is why I'm buried, censured and silenced. In a way your reaction is very flattering.

Your labels don't interest me. You and I both know the accuracy of them. 

It's simply a matter of perspective and position. You have a vested personal interest in Ubuntu being seen as the holy grail of assembled 1s and 0s, and in the community being a noble counter point to Microsoft's evil. 

Of course you'd attack me for pointing out the fact that this is simply not the case, for pointing out that you are all human, and subject to the corruption of power as surly as the rest of us, that you'll struggle to maintain your power base at the expense of others rather than innovate, the instant it becomes in your interest to do so. 

You and others basically tell me that I'm breaking rules yes? Which makes me a sort of criminal. Rules which you made up. 

Did you know it was once a crime in America for blacks to vote? My point being that just because a behavior is technically criminal, does not mean it's unethical. You call me names which carry negative connotations I simply have not earned.

My point is that while I may or may not be breaking the letter of your arbitrary rules, your rules in and of themselves are unjust. You have a captive audience here, if people want tech support they can afford, they have to give you personal information and speak as you wish them too, in short they have to give you power, and like all skilled power mongers you take the position that your power stems only from your altruistic desire to help humanity.

Make no mistake about that, it's a forum, all we CAN do here is speak therefor, any rules, any controls, are controls of speech. And this power invariably corrupts. I'm reminded of fox news for some reason.

Call me a 'troll' or 'sophist' for announcing this fact, and others of its character all you like. Bury my opinion and punish me when I fail to back down. Because while you may control this place, you do not control the reality of the matter, and we both know who is the more ethical and honest in this debate. 

Besides, I don't match your name calling anyway. The fundamental difference between what I am and what you called me is that I am not twisting my meaning to win, I actually just have an honest point which you and your ilk continuously find uncomfortable because I simply cannot be intimidated over a computer. 

Challenge: Try addressing the issues I've risen, rather than speaking about me as a person. Attack my work, not me. Don't call me names, don't abuse your power, don't take an attack on a piece of software, and a forum management architecture like I kicked your cat.

Put my thread back where it will be seen, where it belongs, where I might actually get a link to a card. Turn this back into a debate, instead of a police action.

You won't because I'd own you. Quite simply because I'm correct. It's astonishing how easy that makes a fair debate.

---

### Post by matthew on 2007-11-02
You're trolling. I'm not taking the bait. Trolling is against the [Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"). From Section I, item 4.> 4.   Forum Threads and Flaming:[LIST=1]
[*][LIST]
[*]Flaming and condescending messages: Flames are messages that personally attack, call people names, or otherwise harass another forum member (or any person). These, along with any generally condescending posts will be moved or removed at the moderators discretion.
[*]If the thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion), it will be locked or removed without notice. Individual flame-bait may be deleted or edited at the moderators' discretion. Any *[COLOR=DarkRed]users who continue to post in this manner or engage in other questionable practices, like trolling (posting in an attempt to engage people in arguments) may be subject to more serious sanctions[/COLOR]*.
[*]If the thread turns into an argument, it can be locked or removed without notice. Sometimes a moderator may split the thread or delete certain portions in order to keep the discussion going, but that is not always possible.[/LIST] [/LIST]Goodbye. I hope you find a community in which you are a better fit.

---

