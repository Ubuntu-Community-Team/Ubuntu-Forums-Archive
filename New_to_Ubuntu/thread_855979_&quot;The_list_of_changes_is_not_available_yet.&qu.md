---
title: "&quot;The list of changes is not available yet.&quot;"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by ThreeTrees on 2008-07-11
O.K., so I've been seeing the downward pointing alert arrow Update Manager icon for a while now.  "You can install 173 updates."  Yay!  But I've been avoiding updating for over a month now.  This is because I noticed that certain updates stated "The list of changes is not available yet.  Please try again later."  So I decided to wait, even though admittedly I probably wouldn't understand the changes anyway.  But I just don't think it's a good idea to say O.K. to changing my system without even an attempt to say what the changes are for.  Unfortunately, I have underestimated the "later" in "try again later".  The following still say "not available yet" :

Important security updates

linux-generic
linux-restricted-modules-generic
nvidia-glx-new

Recommended updates

cpp
gcc
gij
libgcj-bc
libgcj-common
tzdata-java

Can someone explain why the list of changes for these are not forthcoming?  Is something wrong?  Thanks in advance for explaining!

---

### Post by SunnyRabbiera on 2008-07-11
sometimes its like that, its not really a big issue though it can be questionable.

---

### Post by Elfy on 2008-07-11
Have you reloaded your sources. As sunny says not really a big issue especially after a month - if there had been anything wrong there would have been howls of outrage on the forum.

I quite often have the same message on proposed updates but that's to be expected.

---

### Post by ThreeTrees on 2008-07-16
Thanks for the replies and sorry for taking so long to respond.  I guess I was being rhetorical when I asked if something is wrong.  Something **is** wrong.  Now I agree that the unexplained changes are probably not breaking anything, and in that sense it's not as big of a deal, but I do think it is wrong when the system asks to install stuff which it will not explain.

Just imagine talking to a manager at work about Ubuntu: "Well sometimes it will try to install stuff, but we won't know why or if we need the changes."

Or imagine taking to a Linux guru about a problem: "Well what changed on your system... you updated package so-and-so?  Why, what were the changes supposed to address?  What?!  You don't know!?  Whatanoob!!"

So sorry if I go on with this, but it just seems like bad form to have this happen.  I don't think it is a problem with my Ubuntu (Heron by the way) setup since the vast majority of changes **do** have descriptions.  I'm guessing (hoping) it is just some simple overlooked thing upstream from me.

P.S.  I'm not sure what "reloading sources" referred to in the previous post means.  Is it pressing the Check button on the Download Manager?  Or the "Reload" in Synaptic?

---

### Post by coffeecat on 2008-07-16
> **ThreeTrees said:**
> I'm guessing (hoping) it is just some simple overlooked thing upstream from me.

You could be right. You'd be doing Ubuntu a real service if you were to post a bug [here]("https://bugs.launchpad.net/ubuntu/"). Have a search around first, though. The devs just love it when the same bug is posted 999 times. :wink:

This forum is a useful place to air issues, but it doesn't get read by the devs (not much anyway), so bugs and problems really need to go on Launchpad.

**Edit:** Forgot to add: I think reloading sources was referring to pressing the reload button in Synaptic. That downloads all the latest package information from the repositories.

---

### Post by Elfy on 2008-07-16
> I think reloading sources was referring to pressing the reload button in Synaptic.Indeed that was what I was talking about :)

Although that said check in update manager would afaik do the same thing.

If there are still no descriptions - I would be wondering after this long, if you still have the same issue perhaps a screenshot of which updates don't have a description would be in order.

---

### Post by aelfwyne on 2008-07-17
Have noticed on ALL of today's updates as well.

Very bad form - the list of changes should be released SIMULTANEOUSLY to the patch. If you don't know what changes were made - perhaps the patch isn't ready to be released??? Lack of good documentation on changes is probably the #1 cause of Linux failures/bugs, etc.

It looks like it only tries once to download the changelog, and then doesn't bother looking again. Not certain on that...

As far as reporting bugs - until developers get off the high-horse of expecting all bug-reporting users to be developers too, I've given up on reporting bugs as have many. It is annoying to no end to report a bug that is CLEARLY a bug, give all the data to replicate said bug (especially if it is a very simple bug), have dozens of other people or hundreds all over the internet posting that they have the same problem, and have it closed because you didn't provide enough info. Yes, users should provide as much info as possible - but they are USERS not developers. 

As far as this particular item... it is either a bug or a human issue, I really don't know and I don't feel like figuring it out. But it is certainly not cool to release changes with absolutely NO documentation.

---

### Post by markbuntu on 2008-07-17
The failure to list changes in updates, especially security updates, is a little disturbing. I kind of expect that from Hardy proposed but they actually list changes a lot.

Someone who has reported this as a bug, give us the title and number and we can all jump on it. It is probably just one person being lazy or feeling harassed an underappreciated who feels it is not worth their time and effort over something so, to them, trivial. We need to let this person know that for us it is a vital and appreciated service. Perhaps, with their self esteem so lifted, they will become more diligent.

---

### Post by ThreeTrees on 2008-07-18
Yes, I just want to reiterate that I very much appreciate all the work that developers, maintainers, etc. do for Ubuntu / Linux / open source.  When you think about it, it is amazing how much is done.  So I hope we don't come across like ungrateful wretches :)  It's just that we (it sounds like at least a few other users agree with me!) think this problem is not as unimportant as it seems at first glance.

> 
If there are still no descriptions - I would be wondering after this long, if you still have the same issue perhaps a screenshot of which updates don't have a description would be in order.

I don't have a screenshot, but the changes that don't have a description are listed in my original post: 3 "important security updates" and 6 "recommended updates".  However, it sounds like user aelfwyne is saying just recently there are lots more (I haven't checked yet).

I don't know if this is a technical problem or a just a matter of someone forgetting something.  I have to believe that there is documentation somewhere, even if it isn't making it out to the Download Manager.  Even knowing where to look for developer notes could be a temporary measure...  Where do these changes get developed?  On launchpad? sourceforge?  For example, if I wanted to find out more about development work on gcc, where would I go to look?

---

### Post by Elfy on 2008-07-18
Well as we speak, or at least I do, I have 37 updates kicking around waiting for me to look.

I have 26 from proposed that all have descriptions.
I have 11 from other that are missong a description - however I can tell that they have come form the deluge repo so I don't need to worry too much about the provenance.


If however I only used prescribed repos and didn't add specific ones from elsewhere I would have none that had no description. It seems likely, but of course I can't be sure, that the updates you have waiting are proposed, backports and it is quite likely that they would not have descriptiosn - they don't know actually if they are going to be made mainstream yet.

Perhaps if you have such a problem with a lack of description you could post your sources list and we could see which may be causing the problem for you.

Personally I have a quick look at any updates I might have - disbale all the NOT security ones and then look at those when I have, I've only once been left high and dry by updates, other than intrepid :) , and that affected everyone who ran with nvidia it seemed.

You can set your software sources to only look for security updates if you so wish.



@Three Trees - if you actually still have updates with no description I would like to see them, if at leat to try and put your mind at rest.

Post the output you get from these - say no to the upgrade

```
cat /etc/apt/sources.list
sudo apt-get upgrade
```

---

### Post by Vivaldi Gloria on 2008-07-18
It should be impossible to put an update without also putting its description (for a software in the main repo). Canonical should make the technical changes in the update mechanism to that effect.

---

### Post by Elfy on 2008-07-18
> **Vivaldi Gloria said:**
> It should be impossible to put an update without also putting its description (for a software in the main repo). Canonical should make the technical changes in the update mechanism to that effect.

Totally agree - but I can't tell whether the lack of description is part and parcel of having backports and proposed enabled - which is what I'm trying to understand here :)

I don't think I've seen any main etc repos with no description myself.

It also appeared from some of the original hardy release problems that people where having those repos enabled - perhaps it's still happpening and these are the 'remnant' (no offense intended) - that would be a bigger problem I think ;)

---

### Post by Vivaldi Gloria on 2008-07-18
> **forestpixie said:**
> Totally agree - but I can't tell whether the lack of description is part and parcel of having backports and proposed enabled - which is what I'm trying to understand here :)

I don't have them enabled and I see updates without descriptions.

---

### Post by Elfy on 2008-07-18
> **Vivaldi Gloria said:**
> I don't have them enabled and I see updates without descriptions.

Eeeuh.. well I'd have to agree then - I can cope with a propsed or backports without a description, guess that would be expected. But wouldn't like a main/security eg. without I must sya - but I haven't had any without a description that didn't belong there.

SOmetimes they show up initially without and I leave them until a reload gives me one - but I've never waited longer than a day or two!

A month or more seems decidedly odd.

> But I've been avoiding updating for over a month now.OP a week ago.

---

### Post by Vivaldi Gloria on 2008-07-18
> **forestpixie said:**
> SOmetimes they show up initially without and I leave them until a reload gives me one - but I've never waited longer than a day or two!

Actually I've never waited longer than a day or two either. I'm not happy even with a couple of days. I want instant descriptions dammit.  ;)

> A month or more seems decidedly odd.

Agreed.

---

### Post by Elfy on 2008-07-18
I'd just like a look at the op's sources and if the upgrade hasn't been done the output to see what packages they are.

Wait and see I guess - personally I hate not being able to help properly :(

---

### Post by ThreeTrees on 2008-07-18
> **forestpixie said:**
> I'd just like a look at the op's sources and if the upgrade hasn't been done the output to see what packages they are.

Wait and see I guess - personally I hate not being able to help properly :(

What a nice pixie you are!:)

I don't think I have backports and proposed enabled.  Please see attached screenshot of Software Sources.

Also see attached cat of /etc/apt/sources.list .  Actually you don't have to bother with it; only five lines are uncommented, which are these below:

```
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

```

By the way, I also have been avoiding upgrading for over a month, but they may be wearing down my resistance soon!

@forestpixie: Maybe 'm misunderstanding, but I'm not sure why you keep asking for which packages don't have descriptions.  They are the same nine listed in the original post.  I just did the Update Manager "Check" again, and now there are 177 updates available, but no new ones without descriptions for me.  For your convenience, here they are again:

linux-generic
linux-restricted-modules-generic
nvidia-glx-new
cpp
gcc
gij
libgcj-bc
libgcj-common
tzdata-java

O.K., just for giggles, I'll attach an example screenshot of the Update Manager.

Finally, I did a little looking around launchpad for gcc documentation; I'm betting it's somewhere in there, but I don't have experience in navigating around there yet.

P.S.  @forestpixie: New Forest in England?

---

### Post by Elfy on 2008-07-22
Sorry - forgot they were at the beginning. Generally I will wait for a short while for a changelog to be forthcoming, but as I use proposed updates as well, quite often they are changelog less :) I would have had those updtaes long before you as I use the same nvidia package and they are alright here.

Further if I'm at all concerned about an update I will check the forum to see if there are problems regarding it - if I can't find anything - update it I do.

There is somewhere on the ubuntu.com site a security page which doies go through security changes but I can't find it, but if you go to launchpad you can find soem information - these are the launchpad and chnagelog ofr tzdata-java package

[http://packages.ubuntu.com/hardy-updates/tzdata-java](http://packages.ubuntu.com/hardy-updates/tzdata-java)
[http://changelogs.ubuntu.com/changelogs/pool/main/t/tzdata/tzdata_2008c-1ubuntu0.8.04/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/t/tzdata/tzdata_2008c-1ubuntu0.8.04/changelog)

Use the package search in the top right of the packages.ubuntu page to look for the others - in the links pane on the right you can see a changelog link.
Certainly the first three updates you have in the list would cause howls of outrage if there was still a problem - I would let the update run now and 

I can see from your sources you only have official repos enabled so you won't get problems from dodgy packages - unless of course everyone does.

@ThreeTrees - yes New Forest in England.

---

### Post by ThreeTrees on 2008-07-22
> **forestpixie said:**
> There is somewhere on the ubuntu.com site a security page which doies go through security changes but I can't find it, but if you go to launchpad you can find soem information - these are the launchpad and chnagelog ofr tzdata-java package

[http://packages.ubuntu.com/hardy-updates/tzdata-java](http://packages.ubuntu.com/hardy-updates/tzdata-java)
[http://changelogs.ubuntu.com/changelogs/pool/main/t/tzdata/tzdata_2008c-1ubuntu0.8.04/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/t/tzdata/tzdata_2008c-1ubuntu0.8.04/changelog)

Use the package search in the top right of the packages.ubuntu page to look for the others - in the links pane on the right you can see a changelog link.

Thanks for the reply.  I did manage to find that page before, but as a newbie, it kind of confused me...  First of all, in this example we are talking about tzdata-java, but the changelog says "tzdata".  I understand tzdata-java is an offshoot of tzdata, but I think it would be clearer if it had its own changelog (if it doesn't).  Secondly, the last change it mentions is in hardy-proposed, which as we know I have not enabled; where's the entry for this change in "regular" hardy?  Finally, what's with all the strange version "numbers": 2008c-1ubuntu0.8.04, 2008b-1ubuntu1, etc.?  I guess there's some rhyme or reason to it, but I haven't figured out the naming convention.  Maybe it sometimes confuses the Download Manager as well, and that's why the descriptions have gone missing??

I don't think anyone thought that there was anything seriously wrong with the changes themselves.  We just wondered what happened to the change descriptions.

---

### Post by Elfy on 2008-07-22
No idea why there was no change description - I've just installed a bunch of deluge updates without - they came from the deluge repo - I assume they won't do one either.

You can get to the tzdata page by clicking on tzdata near the top [ Source: tzdata  ]

I see that there are proposed updates - if you haven't got it enabled then you shouldn't have that change yet I assume.

No idea about the naming convention I'm afraid.

---

### Post by Elfy on 2008-07-23
There is an rss feed for changes

[http://feeds.ubuntu-nl.org/HardyChanges](http://feeds.ubuntu-nl.org/HardyChanges)

---

### Post by Vivaldi Gloria on 2008-07-23
> **forestpixie said:**
> There is an rss feed for changes

[http://feeds.ubuntu-nl.org/HardyChanges](http://feeds.ubuntu-nl.org/HardyChanges)

That's a good find forestpixie. Thanks. 

If you are looking for changes in a particular package then you can look at ubuntu package search:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

There is a link "Ubuntu Changelog" on the right for each package. But it may take a few days after the update for them to enter the changelog.

---

### Post by Elfy on 2008-07-23
I only found it because I saw one in the Intrepid forum for an intrepid one and just guessed :)

I pmm'd the op with the information then thought perhaps I should post it here as well for justin case.

---

