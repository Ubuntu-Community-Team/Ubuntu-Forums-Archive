---
title: "Mail default?"
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by EgoGratis on 2011-07-26
If i understand correctly right now Thunderbird is default mail client in Ubuntu 11.10? Will it stay default in Ubuntu 11.10 and will Evolution be on the installation CD too? I found [one bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/757976") today. How likely is this getting fixed in Ubuntu 11.10?

---

### Post by sgage on 2011-07-26
> **EgoGratis said:**
> If i understand correctly right now Thunderbird is default mail client in Ubuntu 11.10? Will it stay default in Ubuntu 11.10 and will Evolution be on the installation CD too? I found [one bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus-sendto/+bug/757976") today. How likely is this getting fixed in Ubuntu 11.10?

Yes, Thunderbird will be the default email client - as far as I know it's a done deal. Evolution does not seem to be on the current daily iso, and I kind of doubt that it will be in the end. But it will certainly be available in the repos.

---

### Post by EgoGratis on 2011-07-26
I see! TB by default in Ubuntu 11.10 and no Evolution on CD.

---

### Post by sgage on 2011-07-26
> **EgoGratis said:**
> I see! TB by default in Ubuntu 11.10 and no Evolution on CD.

Well, who knows how it will end up, but that's how it looks. Evolution certainly in the repos, though.

---

### Post by IanW on 2011-07-27
Now all we need is an Exchange plugin for TB.

---

### Post by kaldor on 2011-07-27
I haven't used Thunderbird since around 2.0. It was a buggy, slow, POS for me, so I started using Evolution.

Since Ubuntu is switching to TB, I was a bit worried at first. But, after hearing some good things about TB 5 I installed the stable PPA on a production machine and I couldn't be happier. This is a fast, stable, modern client and I love it.

Bugs in Thunderbird are better reported Upstream (in my opinion).

---

### Post by EgoGratis on 2011-07-27
Will TB get more Ubuntu developer time if it will be default? I can find some bugs and problems with integration that were not solved for years. Will this be any different when TB will be default or Ubuntu developers will focus just on Unity integration? Will integration between GNOME and other software be developed that was not touched for years?

Exchange support AFAIK can't just be implemented without some kind of agreement with Microsoft? So i doubt TB will have it any time soon. But i am more interested to get an answer for my first question. One thing is making it default another thing is developing support beyond Unity and Ubuntu One integration that is a problem for years!

---

### Post by castrojo on 2011-07-27
> **EgoGratis said:**
> Will TB get more Ubuntu developer time if it will be default? I can find some bugs and problems with integration that were not solved for years. Will this be any different when TB will be default or Ubuntu developers will focus just on Unity integration?

Mozilla has Mike Conley working on Ubuntu integration, he blogs about it here: [http://mikeconley.ca/blog/](http://mikeconley.ca/blog/)

Chris Coulson has also being integration work. What I recommend is to revisit the bugs that you've had in the past and see if they still affect Tbird in Oneiric.

---

### Post by EgoGratis on 2011-07-27
Thank you for your answer and hard work on Unity and in other areas. Yes I am testing integration in OO between TB and Unity and it is very good i must say and i know it is not done yet. In first post i made an example with just one bug that is in Ubuntu for many versions now and i think it is not directly connected to Unity integration. I guess i was wondering if bugs of this type will be addressed sooner when TB will became default. But OK i know you probably can't give me strait answer i was just wondering and i will just wait and see. Thanks again for your work on Unity and Ubuntu.

---

### Post by castrojo on 2011-07-27
Yeah it's tough to tell that, I suspect if this brings in a bunch more users that provide _good solid testing_ that it would enable them to fix more bugs.

If you want to collect a list of dumb integration bugs like this nautilus one and then post a summary on the ubuntu-desktop mailing list that would be really useful, it will at least get people looking at the bugs users care about.

---

### Post by EgoGratis on 2011-07-27
OK i will keep an eye on this kind of bugs and if i find them i will try to pass the information on to the people, that can make a difference (mailing list). 

I must say generally speaking TB integration is progressing very well and this is why i opened this thread when i saw the bug that was there for so long time to still be there. It would just be a shame to have this kind of bug or similar one in Ubuntu when so much effort is being made to integrate TB in Ubuntu. Thanks again!

---

### Post by chrisccoulson on 2011-07-27
I've just uploaded a version of nautilus-sendto which fixes the problem you mentioned

---

### Post by EgoGratis on 2011-07-28
I tested fixed nautilus-sendto multiple times now and in many scenarios and it works all the times! Seeing this bug fixed in Ubuntu 11.10 is like thinking everything is possible now and i mean everything. 

Not only great Unity integration is developed for Thunderbird but quality desktop environment integration in all areas too. You just can't imagine how many TB users will notice this fixed and how many new users won't have to make workarounds to get this working and how many administrators in corporate environments will not have to manually work on this issue from now on. I don't have other words but to say thank you Jorge and Chris.

---

### Post by Roo79x on 2011-07-29
if thunderbird does get the green light to be the default mail client (which I hope it does) I would like to see 2 features added if possible.

1> now that thunderbird work like a dream with the messaging menu, a command or the ability to start thunderbird minimized at login would be very helpful.
say something like adding thunderbird -minimized to the startup applications.

2> this one I think would be alot harder but I'd like to be able to start thunderbird showing the calendar {you would need lightning installed of course} I do remember seeing something once before I'll go googling to see if I can find it again.

---

### Post by sgage on 2011-07-29
> **Roo79x said:**
> if thunderbird does get the green light to be the default mail client (which I hope it does) I would like to see 2 features added if possible.

1> now that thunderbird work like a dream with the messaging menu, a command or the ability to start thunderbird minimized at login would be very helpful.
say something like adding thunderbird -minimized to the startup applications.

2> this one I think would be alot harder but I'd like to be able to start thunderbird showing the calendar {you would need lightning installed of course} I do remember seeing something once before I'll go googling to see if I can find it again.

I have a tab with the calendar (lightning) running all the time. When I start TB, it has the Inbox tab and the Calendar tab all ready to go.

I like your idea #1, though it isn't that hard to just hit the launcher. The way I have it set up, after logging in I just go click, click, click right on down the line and open all my apps.

---

