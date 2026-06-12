---
title: "Evolution's way or the highway (still) ..."
date: 2008-04-25
forum: Recurring Discussions
---

### Post by gwilson on 2008-04-25
Please educate me, if I'm ignorant.

Is it possible that the Gnome developers of Evolution are secret admirers of Microsoft?

I haven't used Evolution for years now because I don't like the fact that it is designed to ignore other major software programs such as Thunderbird. It seems that Evolution is designed to put all of your email and contact info into it's own preferred format and is intentionally designed to lock you in by not providing a means to export your data. I decided to give evolution a test run, and it can't even import my Thunderbird contacts and existing emails directly.

Why the Gnome developers design in this exclusiveness is beyond me, and seems to be not compatible with the spirit of Linux. It has much more in common with the sort of things Microsoft does to lock you into a single system by designing in barriers to interaction with other competing formats.

---

### Post by ShadowGray on 2008-04-25
I use thunder bird, and that's the end of that.

---

### Post by smoker on 2008-04-25
one of the first things i do with a new install is remove evolution and replace it with thunderbird.

---

### Post by urukrama on 2008-04-25
I've recently started using Evolution for my work-related email. I tried it a few years ago, and didn't like it, but decided to give it another (longer) chance this time. I think I'll stick with it. Kmail is pretty powerful too, except that I can't find a way to automatically filter all my unread email.

You can import/export mail in Evolution, though it is not as simple as in Thunderbird perhaps. A simple Google search gives me this:

[LIST][How to Import Evolution mail into Thunderbird]("http://fedoranews.org/mediawiki/index.php/How_to_import_Evolution_mail_into_Thunderbird")
[/LIST]
[LIST]
[Import Thunderbird Email into Evolution]("http://www.debianadmin.com/import-thunderbird-email-into-evolution.html")[/LIST]

Kmail behaves in a similar way in regards to this, by the way, though you can easily import addresses and contact details into Kaddressbook.

---

### Post by Mr. Picklesworth on 2008-04-25
Of course Evolution isn't working under the same format as Thunderbird. Thunderbird is strictly an email program (and not aiming straight at this operating system), while Evolution is a complex beast plugging in to the Evolution Data Server, which handles *a lot* of data in an open-ended way.

Besides that, since when has vcard been an exclusive format?

Furthermore, email programs have never been standardized in the way they store data. Evolution is actually a pretty good attempt, since it is built into GNOME; PIM suites like Pimlico choose to work with it and get automatic desktop integration. There are similar niceties going with KDE.
It isn't desktop-neutral yet, but at least we don't have every program using a different underlying system, which used to happen. (Oh, wait, there's Thunderbird...).

Windows Vista does something neat here, too. It has contacts in their own easily visible directory in the user's home folder (named "Contacts"). It has a nice list of the user's contacts, with previews. They can be opened up easily, revealing further information ready to be modified. The bonus there is being able to back up and send contacts by hand without converting them to another format; they are already easily moved as is.

---

### Post by Mateo on 2008-04-25
eh, if you've ever talked to the evolution developers you'd know that they are pretty hard headed.  It's treated like a small-time project with the developers only creating an application the way they want.  Which is fine, but strange for such a big project.  For example, they refuse to create a tray icon because they say the notification area is not a system tray and that apps that use it for a tray are abusing gnome specs.  Whether this is true or not, it just goes to show that useability takes a backseat to rigidity in the eyes of evolution devs.

I really wish someone capable would fork it.

---

### Post by rickyjones on 2008-04-25
> **Mateo said:**
> eh, if you've ever talked to the evolution developers you'd know that they are pretty hard headed.  It's treated like a small-time project with the developers only creating an application the way they want.  Which is fine, but strange for such a big project.  For example, they refuse to create a tray icon because they say the notification area is not a system tray and that apps that use it for a tray are abusing gnome specs.  Whether this is true or not, it just goes to show that useability takes a backseat to rigidity in the eyes of evolution devs.

I really wish someone capable would fork it.

I filed a bug report because I wanted Evolution to insert the signature where I put the cursor, much like Outlook. Last time I checked the behavior was to insert the signature at the top, which if you typed a long email meant you had to spend time reformatting it and moving the signature around.

Long story short the bug report was closed because the developer who looked at it did not think it was a worthy idea to implement.

-Richard

---

### Post by Mr. Picklesworth on 2008-04-25
> **Mateo said:**
> For example, they refuse to create a tray icon because they say the notification area is not a system tray and that apps that use it for a tray are abusing gnome specs.  Whether this is true or not, it just goes to show that useability takes a backseat to rigidity in the eyes of evolution devs.

Yes, that is true:
[http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)
More specifically, [this](http://library.gnome.org/devel/hig-book/stable/desktop-notification-area.html.en).

Putting permanent icons in the notification area ("iconifying an application") is neither sane, nor consistent, nor usability-inclined. There are many ways to push applications out of the way already, two of which are pushing them to other workspaces and minimizing them. Evolution appears in the notification area if, and only if, it has something to notify the user about. Otherwise, the purpose of that applet is completely dilluted and it becomes loaded with useless information.

---

### Post by p_quarles on 2008-04-25
Moved to Recurring Discussions.

---

### Post by ShadowGray on 2008-04-25
Long story short... Evolution should just stop being implemented.

Why is Evolution implemented instead of Thunderbird?

---

### Post by smartboyathome on 2008-04-26
> **ShadowGray said:**
> Long story short... Evolution should just stop being implemented.

Why is Evolution implemented instead of Thunderbird?

Because it is made to be more of a all-in-one office app like Outlook, not just an email client like thunderbird.

---

### Post by macogw on 2008-04-26
> **rickyjones said:**
> I filed a bug report because I wanted Evolution to insert the signature where I put the cursor, much like Outlook. Last time I checked the behavior was to insert the signature at the top, which if you typed a long email meant you had to spend time reformatting it and moving the signature around.

Long story short the bug report was closed because the developer who looked at it did not think it was a worthy idea to implement.

-Richard

My sig always appears at the end...I think there's a setting for it though.

I just don't like that it's monolithic.  E-D-S is well-documented though, so interacting with it in other ways is possible.

---

### Post by tact on 2008-04-26
> **ShadowGray said:**
> Long story short... Evolution should just stop being implemented.

Why is Evolution implemented instead of Thunderbird?

Does Thunderbird have all the functionality to link into a corporate exchange server like evolution?

Serious question.
I need to work in an environment that is dominated by exchange server and MSOutlook and I have to be able to accept/create meeting invitations that can be transparently be exchanged with MSOutlook users.

So far only Evolution does the job as far as I can see.  

Cheers

---

### Post by gwilson on 2008-04-26
All of the points in defense of Evolution may be valid, but valid questions remain. Why do the developers treat Thunderbird (yes, it's an email-only program) as a competitor to be stamped out? Why don't they include Thunderbird in their built-in email function? It would be an obvious plus for the program, and it would be simple to implement, if they are so clever. Treating Thunderbird as if it doesn't even exist is the height of arrogance. Sure there are work arounds if you are a geek (like me), but why is that necessary?

Oh, well. I guess the answer is obvious and has been discussed ad nauseum or else this wouldn't have been "moderated" to Recurring Discussions (which also betrays the official Ubuntu intention to sweep such discussion under the rug and thus suppress it).

---

### Post by p_quarles on 2008-04-26
> **gwilson said:**
> All of the points in defense of Evolution may be valid, but valid questions remain. Why do the developers treat Thunderbird (yes, it's an email-only program) as a competitor to be stamped out? Why don't they include Thunderbird in their built-in email function? It would be an obvious plus for the program, and it would be simple to implement, if they are so clever. Treating Thunderbird as if it doesn't even exist is the height of arrogance. Sure there are work arounds if you are a geek (like me), but why is that necessary?

Oh, well. I guess the answer is obvious and has been discussed ad nauseum or else this wouldn't have been "moderated" to Recurring Discussions (which also betrays the official Ubuntu intention to sweep such discussion under the rug and thus suppress it).
What are you talking about? The developers do not "treat Thunderbird as though it doesn't exist." I don't know how you could reach that conclusion, but if you have some sort of evidence for that claim, please do point it out. I suppose that you could say that anything not included on the live disk is being "ignored." I doubt, though, that the MOTU developers would appreciate having their efforts characterized that way. 

The thread was moved to Recurring Discussions because it fits the bill. If we wanted to censor anyone, we would simply delete the post.

---

### Post by Mr. Picklesworth on 2008-04-26
Well, the fact is, Thunderbird is not built for GNOME, or really any Linux desktop. It is a one-size-fits-all program, typical with Mozilla. Not really suited as a default choice, but a nice option.
For that matter, it fits quite poorly in GNOME. The work spent getting Thunderbird to work in a manner consistent with this environment (essentially requiring a fork) would be better spent producing a working email client from the ground up. For example, Modest is coming along quite well.
As an example of how much trouble that would be, such work has been going into Firefox for ages, and Firefox 3 is the first time it has looked almost native. Even so, beyond looks, it still feels distinctly different in a way that would make anyone concerned about learnability tremble. There is a lot of work to be done yet on that one, let alone Thunderbird.

As for the Evolution shell, I for one agree it feels messy. The really frightening part is it's not actually as monolithic as it appears; Mail, Calendar, Contacts and Memos are all seperate components, but some lunatic decided it would make sense to have them all appear in the same window. The end result is horrifying from a usability perspective. Actually, looking at the thing and the lack of discussion regarding its interface, I am inclined to believe that the usability people gave up on sight.

Still, at least it uses GTK, and thus follows the majority of UI conventions. And it feels just like home for any MS Outlook users.

---

### Post by gwilson on 2008-04-26
Well, aren't we defensive!  What's an MOTU developer?  Do you understand that my crticism is directed at the Evolution developers, not the Ubuntu staff? I don't have a problem with Thunderbird not being included on the live CD, especially since I don't use the live CD. If Evolution offers to import email from several programs, including the basically defunct Netscape, why doesn't it offer to import mail from Thunderbird which is heavily utilized by Ubuntu users? It's a simple question you are obviously ignoring in your defense of Evolution.

I thought the Cafe was a place where we can discuss the topics we choose to rather freely. There's quite a bit there that isn't even realted to Ubuntu. When you bury the topic in a subforum where responses don't show up as new posts, you are certainly suppressing discussion of what should not be such a threatening subject. Why not be honest about this?

---

### Post by hartl_vienna on 2008-04-26
I like Evolution. The only thing I really miss is a reliable sync solution with mobile devices according to the functionality of ActivSync.

---

### Post by gwilson on 2008-04-26
> **Mr. Picklesworth said:**
> Well, the fact is, Thunderbird is not built for GNOME, or really any Linux desktop. It is a one-size-fits-all program, typical with Mozilla. Not really suited as a default choice, but a nice option.

I'm not concerned with the cosmetics. Thunderbird looks fine to me, even if it isn't sufficiently Gnomish for others.   :-)

I'm not advocating that Thunderbird be the default choice or that Evolution be replaced. Evolution is an impressive program and a plausible replacement for Outlook, but I never used Outlook, either. They are both bloatware if all you want is an email program.

So what's with Vancouver? My son is currently up there visiting his fiance whom he met at a swing dance convention in Sweden. I help the Rover Car Club of Canada (based in Vancouver) with their website. Today, I ordered a musical instrument that could only be purchased from a music store on Hastings Street in Vancouver. I'd emigrate if you people weren't so dead set against Americans moving north!  ;-)

---

### Post by p_quarles on 2008-04-26
> **gwilson said:**
> Well, aren't we defensive!
No?

> What's an MOTU developer?
MOTU == "master of the universe." These are the volunteer package maintainers (including several forum members) who populate the universe repository.

> Do you understand that my crticism is directed at the Evolution developers, not the Ubuntu staff?
I wasn't really concerned about the target of the criticism so much as the inflammatory and counterproductive method in which it was expressed. 

> I don't have a problem with Thunderbird not being included on the live CD, especially since I don't use the live CD. If Evolution offers to import email from several programs, including the basically defunct Netscape, why doesn't it offer to import mail from Thunderbird which is heavily utilized by Ubuntu users? It's a simple question you are obviously ignoring in your defense of Evolution.
Both Thunderbird and Evolution will work just fine with the good old mbox format. The fact that Evolution supports Netscape mail, but not Thunderbird's default format, suggests that the developers have left in legacy support without adding new support, not that they want to pretend that other mail clients don't exist. After all, if someone is happy with Thunderbird, why should Evolution go out of its way to convince people to switch to something they don't need? 

By the way, I'm a KDE user, so I find it slightly ridiculous that I'm being accused of GNOME partisanship here. 

> I thought the Cafe was a place where we can discuss the topics we choose to rather freely. There's quite a bit there that isn't even realted to Ubuntu. When you bury the topic in a subforum where responses don't show up as new posts, you are certainly suppressing discussion of what should not be such a threatening subject. Why not be honest about this?
The Recurring Discussions section is here for a reason. It's here because people feel the need, for whatever reason, to continually bring up these "my favorite app is better than your favorite app for the following arbitrary reasons" topics. This is one of them. Not everyone likes to rehash these topics, but for those who do, this sub-forum exists.

Please don't accuse me of being dishonest, nor invent conspiracies.

---

### Post by gwilson on 2008-04-26
I raised a valid topic and even asked to be educated in my opening sentence. What I got was an extremely defensive reaction from a couple of Ubuntu forum staff and the immediate relegation of our discussion (which several of us were enjoying and also trading knowledgw and insights) to a dead subforum. Here's what I said:

"It seems that Evolution is designed to put all of your email and contact info into it's own preferred format and is intentionally designed to lock you in by not providing a means to export your data. I decided to give evolution a test run, and it can't even import my Thunderbird contacts and existing emails directly."

That hardly seems "inflammatory or counterproductive" to me. You guys really jumped the gun on this one, in my opinion. Apparently, any thread that discusses the strengths and weaknesses of Evolution must be immediately squashed. 

You state that this thread was not relegated to a dead end subforum in order to supress it when your own words make it clear that this was precisely what was done. If the dishonest shoe fits, you might as well wear it.

I still don't understand why crticism of Evolution is such a red flag issue to you guys. Hair-trigger stuff. 

I would also comment that the Red-Letter Forum Staff should not be so quick to jump into a discussion amongst the little people and bully them around. It really doesn't look good on you.

---

### Post by mrgnash on 2008-04-26
> **Mr. Picklesworth said:**
> Yes, that is true:
[http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)
More specifically, [this](http://library.gnome.org/devel/hig-book/stable/desktop-notification-area.html.en).

Putting permanent icons in the notification area ("iconifying an application") is neither sane, nor consistent, nor usability-inclined. There are many ways to push applications out of the way already, two of which are pushing them to other workspaces and minimizing them. Evolution appears in the notification area if, and only if, it has something to notify the user about. Otherwise, the purpose of that applet is completely dilluted and it becomes loaded with useless information.

Correct. Gnome developers typically don't care about winning popularity contests through pandering, or making things more like Windows. If users don't like that approach, then there's always KDE.

> Oh, well. I guess the answer is obvious and has been discussed ad nauseum or else this wouldn't have been "moderated" to Recurring Discussions (which also betrays the official Ubuntu intention to sweep such discussion under the rug and thus suppress it).

This is pure nonsense, by the way. Discussions moved to recurring discussions are exactly that: recurring discussions.

---

### Post by p_quarles on 2008-04-26
[quote=gwilson]Is it possible that the Gnome developers of Evolution are secret admirers of Microsoft?[/quote]
That's not a discussion of the strengths and weaknesses of Evolution, it's just flamebait. 

As for your assertion that this is a "dead-end subforum" . . . well, you must be new here. ;)

---

### Post by gwilson on 2008-04-26
> **p_quarles said:**
> That's not a discussion of the strengths and weaknesses of Evolution, it's just flamebait. 

As for your assertion that this is a "dead-end subforum" . . . well, you must be new here. ;)


Designing software with built-in barriers to the exchange of information with other programs that might be considered competition when the tools to allow said exchange could easily have been included is somewhat Microsoft-esque! Wouldn't you agree? Besides, allowing new users to easily import their data from another major program with fewer features would make Evolution a stronger, more attractive application. It has nothing to do with stealing users from another program or sinking to Thunderbird's level.

Do messages posted to to the Recurring Discussions Forum appear in the New Postings search at the top of the forum? From what I can see, they do not. Therefore, they are hidden from most of the frequent visitors to the Ubuntu Forums even though they are active. In this way, the discussion is conveniently repressed and hidden from casual view, and moderators like you can claim that no censorship has occurred. This is patently obvious, and claims that this is not the case only serve to make the moderators look silly and, yes, dishonest. So, why not just admit that relegating any subject to this forum effectively suppresses the thread? Surely, your Vulcan half can see the logic in this...

---

### Post by rajeev1204 on 2008-04-26
> **p_quarles said:**
> That's not a discussion of the strengths and weaknesses of Evolution, it's just flamebait. 

As for your assertion that this is a "dead-end subforum" . . . well, you must be new here. ;)

hi

I think except the microsoft reference , the rest of the statements are pretty polite.Just my point of view.


regards

rajeev

---

### Post by p_quarles on 2008-04-26
> **gwilson said:**
> Designing software with built-in barriers to the exchange of information with other programs that might be considered competition when the tools to allow said exchange could easily have been included is somewhat Microsoft-esque! Wouldn't you agree?
I don't see how making Evolution *less* inviting for Thunderbird users is related to competition with Thunderbird. If they wanted to compete with Thunderbird, they would make it easy to switch. 

> Do messages posted to to the Recurring Discussions Forum appear in the New Postings search at the top of the forum?
No, they don't, but they are not otherwise hidden in any way. The "new posts" search is primarily intended for support questions anyway.

---

### Post by gwilson on 2008-04-26
> **rajeev1204 said:**
> hi

I think except the microsoft reference , the rest of the statements are pretty polite.Just my point of view.


regards

rajeev


At least until the thread was moderated into the trash bin. If you notice, the same person who decided that the thread should be repressed also took sides in the discussion. There's a current thread called "Firefox 3 beta 5 - disappointment, it's a cpu hog!" that is full of people claiming their browser is the best, but that thread has 75 postings and has not been moderated to the dead threads forum.

---

### Post by rajeev1204 on 2008-04-26
> **gwilson said:**
> At least until the thread was moderated into the trash bin. If you notice, the same person who decided that the thread should be repressed also took sides in the discussion. There's a current thread called "Firefox 3 beta 5 - disappointment, it's a cpu hog!" that is full of people claiming their browser is the best, but that thread has 75 postings and has not been moderated to the dead threads forum.

No comments. :)

---

### Post by p_quarles on 2008-04-26
Sigh.

I'm sorry you don't like the fact that this thread belongs in this section. I moved it according to forum policy, which was not made by me. As I said, I don't use Evolution, nor am I particularly fond of it. All the same, this topic falls clearly under the list of those that get moved to this sub-forum. It was neither "put in the trash bin," locked, nor removed. It was placed in an area that is easy to find for those interested in rehashing these questions, and that is easy to avoid for those sick of them. 

Now, if you have any further questions about this policy please post them in the Resolution Center so that this thread can return to its topic.

---

### Post by gwilson on 2008-04-26
> **p_quarles said:**
> I don't see how making Evolution *less* inviting for Thunderbird users is related to competition with Thunderbird. If they wanted to compete with Thunderbird, they would make it easy to switch. 


No, they don't, but they are not otherwise hidden in any way. The "new posts" search is primarily intended for support questions anyway.

Regarding Evolution, the original question asked was why the developers of Evolution chose not to include Thunderbird data files among those that could be imported. I think we all agree that it would have improved the program and made it more useful. It's the obvious absence of this raises questions about the developers thought process.

You're a real politician, p_quarles. It's not much of a debate when you ignore most of the points the other party makes. Why can't you simply admit that you changed the location of this thread in order to suppress discussion of the topic? "Not otherwise hidden" makes it clear that the postings are, in fact, hidden to some extent. That's progress. You'll feel better if you just let it all out. Hey, we're in the dead letter box, here. No one will ever know. 

Moderators have to make a lot of important decisions, and sometimes there is a lapse in judgment and worthwhile discussions are squelched. Moderators are only human, or is that another point you're not willing to concede?

---

### Post by 23meg on 2008-04-26
> **Mateo said:**
> For example, they refuse to create a tray icon because they say the notification area is not a system tray and that apps that use it for a tray are abusing gnome specs.  Whether this is true or not, it just goes to show that useability takes a backseat to rigidity in the eyes of evolution devs.

I really wish someone capable would fork it.

This is what plugin architectures are good for; Evolution has one. If you don't agree with the maintainer on a possible feature, write a plugin that implements the functionality you want, or get/pay someone to write it instead of hopelessly trying to persuade the maintainer. This is how FOSS works: if you expect to be able to persuade others to agree with you 99% of the time and do nothing yourself, you're doomed to be all talk. Forking for such purposes would be ridiculous. It seems many people who have superficially read about or witnessed one or two of the significant forking stories of the past (Beryl/Compiz, the X saga, etc.) are under the illusion that forking is something people resort to at will, without paying much thought or listening to each other's rationales and engaging in proper diplomacy with the forked project. 

Forking is a last resort, and if it's being resorted to prematurely (I'll refrain from citing a recent hot example for the sake of preventing a flame war), there's definitely some ignorance or shortage of social skills involved. Patches, (d)VCS, plugins, undisclosed modifications, you name it; there are many socially and technically compatible ways to disagree with others, yet keep in line with them. Of course, these aren't the easy way out, and are of no interest to people who live in a fantasy world under the illusion that there's a single fixed, homogeneous group of people called "the developers" that everything is to be expected from.

Related reading: [Homesteading the Noosphere]("http://www.firstmonday.org/issues/issue3_10/raymond/")

---

### Post by rajeev1204 on 2008-04-26
Lets stick to the topic wilson. 

See, 23 meg just added his comment. :)

---

### Post by gwilson on 2008-04-26
> **p_quarles said:**
> Sigh.

Now, if you have any further questions about this policy please post them in the Resolution Center so that this thread can return to its topic.

That's fine by me. Just read back and remember that YOU were the one who changed the topic:

"The thread was moved to Recurring Discussions because it fits the bill. If we wanted to censor anyone, we would simply delete the post."

You should have stayed on topic yourself after weighing in.

---

### Post by 23meg on 2008-04-26
[QUOTE=gwilson]Why don't they include Thunderbird in their built-in email function? It would be an obvious plus for the program, and it would be simple to implement, if they are so clever.[/QUOTE]

If they are so clever as to what? Disagree with you? How do you know it would be simple to implement? Do you know about the inner workings of Evolution? May there be a structural problem preventing this? Maybe there are bugs that need to be fixed before it happens, and/or code that has to be rewritten? Maybe simply nobody who works on Evolution has the time or willingness to do it, and they're just waiting for a prospective contributor to come along and implement it (that happens often for many features in many projects), and they'll happily accept it if that happens?

[QUOTE=gwilson]
Regarding Evolution, the original question asked was why the developers of Evolution chose not to include Thunderbird data files among those that could be imported.[/QUOTE]

Did you ask them why not? Did anyone? Someone probably did in the past; did you do a search in forums / mailing lists / the web to find out before speculating? If not, especially given your loaded question at the very beginning, your speculation is aimed at mudslinging rather than being a genuine question

---

### Post by gwilson on 2008-04-26
> **rajeev1204 said:**
> Lets stick to the topic wilson. 

See, 23 meg just added his comment. :)

You're yanking my chain, Rajeev!  ;-)

---

### Post by bapoumba on 2008-04-26
Thread closed for Staff evaluation.

---

