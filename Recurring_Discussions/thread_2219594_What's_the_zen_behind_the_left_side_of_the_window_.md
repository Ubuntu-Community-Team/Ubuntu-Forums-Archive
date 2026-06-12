---
title: "What's the zen behind the left side of the window titlebar?"
date: 2014-04-24
forum: Recurring Discussions
---

### Post by r_avital on 2014-04-24
I truly hope, even pray, that I'm not offending any delicate sensibilities by asking this question on this forum -- I tried to go directly to "recurring discussions" but the site won't let me start a thread there.

I'm trying hard to understand what the design consideration is, for forcibly imposing on users the placement of buttons, that has been practically universally accepted on the opposite side since the invention of modern GUIs.  Yes, yes, yes, there are other DEs around, nobody is forcing anything, I know, I'm familiar with that prevarication, but I'm trying to understand *this* DE, and the *conscious decision to invest time and effort in coding restrictions to already working and existing tools* (e.g. dconf-editor and several others) that always have allowed users to place window control buttons where they thought they belonged, on an OS that prides itself on being completely configurable by the end user.

This is not new, and too many Ubuntu users have been gritting their teeth with every new release since Lucid LTS (oh how I loved it) reconfiguring this to their liking, as it invariably flipped it on them.

The closest I've been able to find to an explanation, is this, from Mark Shuttleworth:
> Moving everything to the left opens up the space on the right nicely, and I would like to experiment in 10.10 with some innovative options
there
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/comments/110](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/comments/110)

That's nice.  Not to be facetious, but moving everything to the right opens up the space on the left just as nicely.  Kudos for experimenting with innovative options, but what reason is there for such options never to be on the left instead?

This is also very nice of Mr. Shuttleworth:
> ...I encourage folks who prefer that layout to use it, or to follow the instructions for setting the gconf preference manually. It's great that you can do that.

Encourage, that is, until the option is removed.

What could it be?  What is the UI wisdom or zen behind this?

Could it have anything to do with user instinct, due to the fact that we write from left to right?  I should hope not, given that there are close to a Billion people in the world using right-to-left languages that are supported in Ubuntu (at least as far as I'm able to glean from data in the CIA World Factbook), and I'm sure anyone as sensible as Mr. Shuttleworth would not want to offend them.  Certainly not when his programmers remove the ability to represent keyboard layouts by country flags, "because the Union Jack would not be appropriate in India, for instance," as has been stated in such fora as askubuntu and so on.

Why leave it open to speculation?  A clear explanation of the reason behind it, of why it is so critical as to get programmers to go out of their way to remove that flexibility, would be most welcome.

---

### Post by buzzingrobot on 2014-04-24
Well, the buttons have to be someplace.  It's pretty much a choice of one of two options. And, if memory serves, they are on the left in OS X, so it isn't really the case that putting them there violates decades of GUI rules.

Actually, there aren't rules about this sort of thing.  At least, no GUI Police hanging around to enforce someone's idea of rules.

Can't be that hard, after a bit of time, to use Unity's buttons.  Like visiting someplace where they "drive on the wrong side of the road", just really easier.  In hardly anytime, it's second nature.

The position of the buttons can be reversed using Unity Tweak Tool and, I'd bet, dconf editor. 

Actually, close, minimize and maximize buttons aren't really obligatory.  As long as there is a bar across the top of a window, clicking on the left third could minimize it, clicking on the middle third could maximize it, and clicking on the right third could close it.

---

### Post by r_avital on 2014-04-24
> **buzzingrobot said:**
> ... they are on the left in OS X, so it isn't really the case that putting them there violates decades of GUI rules.
Well, I never called it a "violation" -- only that it was universally accepted that they'd be on the right.  Okay, so universally minus one.  I remember DEC systems using early motif with buttons on the right.

> **buzzingrobot said:**
> At least, no GUI Police hanging around to enforce someone's idea of rules.
Well... If they go out of their way to disable the user's ability to reset them on the right, I think that's called enforcement.

> **buzzingrobot said:**
> The position of the buttons can be reversed using Unity Tweak Tool and, I'd bet, dconf editor. 
Have you tried it?  I have.  I made the same ":minimize,maximize,close" entry I've always made with every new release of Ubuntu, and this time, no reaction, they stay on the left.  There's a thread in launchpad about how they re-coded Unity to simply intercept that event and nullify it.  Sounds more and more like enforcement.  But if you find a way, I'd love to see it.  So would many others.

I've driven on the left side of the road.  The difference is, I don't own the road.  I'm supposed to own my computer.  And my screen.  And Canonical tells me I don't, not if I want to use their product.  Just like Apple and Microsoft.

---

### Post by llanitedave on 2014-04-25
> **r_avital said:**
>   I'm supposed to own my computer.  And my screen.  And Canonical tells me I don't, not if I want to use their product.  Just like Apple and Microsoft.

I get so tired of hearing this.  Unlike Apple and Microsoft, YOU ARE NOT PAYING for Canonical's product.  They offer it to you for free.  They don't owe you.  Not only that, but you also have available, FOR FREE, several other desktop environments that you can use if you don't like Unity, with access to the same applications and the ability to arrange your work area as you like.  There is no ownership dispute, and no arm-twisting, and no one is taking away your computer or your freedom.  They don't own you, but stop acting as if you own them.

Use it if you like it, use something else if you don't.  Sheesh.  Stop whining.

All that said, I know of no "universal" preference to put icons on the right side.  Windows has always done it on the left.  Apple started out putting them on the bottom.  Universally, tabbed windows arrange their tabs starting on the left, new ones are added to the right.

And if you really want to follow the Open Source ethos -- you have the source code.  I'm sure you can arrange it on the right if you put your mind to it.  Don't ask someone else to do it for you and then give it to you for free.

---

### Post by r_avital on 2014-04-25
> **llanitedave said:**
> Unlike Apple and Microsoft, YOU ARE NOT PAYING for Canonical's product.  They offer it to you for free.  They don't owe you.

Please show me, when did I say they owed me?  I'm past the hissing and moaning.  I was asking a question.  What is the design principle?  Is there a plan?  What is it?  And the reason I ask, is that it's strange to see them, again, deliberately investing coding time into, please pay attention to this, R-E-M-O-V-I-N-G the end-user's ability to set the option, using tools that already exist.  That warrants an honest, curious question.

Asking why, is not fighting.  You seem to be the one interested in a fight.
> **llanitedave said:**
> And if you really want to follow the Open Source ethos...
Sounds to me like you know something about the open-source ethos.  Would you agree that the open-source ethos includes the principle of allowing complete customization by the end-user?

Again, of course, they don't owe me.  If I can code, I can customize as I wish.  But again, you're missing the fact that they didn't have to put in any work to let me make the customization.  The tools already existed.  They deliberately added code to nullify existing code to remove the customization.  Call me a whiner if you wish, this is a fact you can't get around.  I am simply asking why.

Does "they give it you you free" equal "it's a good thing they provide an OS that angers some people" even if only a minority?  Does that make sense?

> **llanitedave said:**
> Not only that, but you also have available, FOR FREE, several other desktop environments that you can use if you don't like Unity, 
Hold on, fella.  I did not say in this thread that I didn't like Unity.  I have issues with it, true, especially with its bugs (or is dissatisfaction with bugs also verbotten when it's free?).  I like it enough.

> **llanitedave said:**
> 
All that said, I know of no "universal" preference to put icons on the right side.  

Then, respectfully, you don't know much.

> **llanitedave said:**
>   Don't ask someone else to do it for you and then give it to you for free.
One more time, brother, with feeling now, I never asked them to "do it for me"  -- they took the initiative and removed the E-X-I-S-T-I-N-G ability to customize that particular element.

Tired of hearing it?  Not nearly as tired as I am of repeating that particular point for fan-boys and shills who refuse to acknowledge it.  Now don't get me wrong, I will always defend your right to respond to any post, but if you're so tired of hearing it, you have the freedom to ignore my posts.  I recommend you do, because I will continue to raise that question, respectfully and politely, until I hear an answer that makes sense, or I'm banned.

Anyone else "gets so tired of hearing this" -- please exercise your freedom to resume cruising speed.

---

### Post by lisati on 2014-04-25
Doesn't worry me too much which side the icons appear on. Having said that, I'm more used to the left, which started back when I used Windows 98SE.

---

### Post by vasa1 on 2014-04-25
New bottle, old wine: [http://ubuntuforums.org/showthread.php?t=2210844](http://ubuntuforums.org/showthread.php?t=2210844)

---

### Post by 3rdalbum on 2014-04-25
Because in maximised windows, the buttons would look pretty stupid on the right of the indicators. You'd also be left with blank space there when the window wasn't maximised, or the indicators would move depending on the state of the window - either way would be terrible.

So the buttons go on the left, where there is space above the Launcher.

Why is the Launcher on the left instead of on the right? It's because you can control the mouse better, the closer it is to their center. Basically this means that, for right-handed people, your mousing is more precise when the cursor is on the left side of the screen. Hence, the Launcher goes on the left of the screen.

The Launcher doesn't go on the top or bottom because that would restrict precious vertical space on a widescreen monitor.

The truth is, virtually nobody changes the order of window buttons in Unity so they are on the right-hand side. The reason for this is that maximised windows will ALWAYS have their buttons on the left-side of the top panel regardless of the setting in dconf. This has always been the case in Unity.

I work in a place that has fleet cars. Some of them have their turn indicator switch on the right-hand side of the steering column, some have it on the left-hand side. The first or second time you might get it wrong and the windscreen wipers come on, but you adjust fast. I installed Ubuntu 14.04 today and found that the Back/Forward buttons in Nautilus have moved somewhat. The first couple of times my mouse went to the wrong spot, now it doesn't. Because I adapted.

Frankly, if you've been changing the order of window buttons to the right side every six months since 2010, you've been putting yourself through a lot of work to avoid adapting. The window button order is very trivial to get used to. Just stick with it. After a few hours you'll always go to the correct corner.

---

### Post by buzzingrobot on 2014-04-25
> **r_avital said:**
> 

Have you tried it?  I have.  I made the same ":minimize,maximize,close" entry I've always made with every new release of Ubuntu, and this time, no reaction, they stay on the left.  There's a thread in launchpad about how they re-coded Unity to simply intercept that event and nullify it.  Sounds more and more like enforcement.


Haven't tried in 14.04.  I'm don't really care which side they're on. It's not like it's a challenging situation.

Calling a design choice like this "enforcement" is inappropriate. Developers and designers get to make those choices, and users get to choose or reject the software they make. if window button placement is a sine qua non priority for a user, then that user ought to be willing to use an environment that accords with his or her priorities. 

The freedom in Linux is not about building in every possible configurable option in every program and supporting them in perpetuity. It's about code being free.

---

### Post by pfeiffep on 2014-04-25
> I've driven on the left side of the road. The difference is, I don't own the road. I'm supposed to own my computer. And my screen. And Canonical tells me I don't, not if I want to use their product. Just like Apple and Microsoft.
Somewhat accurate analogy except for those of us who use both Windows and Ubuntu. I like being able to customize my user interface for consistency ie having the control icons on the right.

---

### Post by buzzingrobot on 2014-04-25
> **pfeiffep said:**
> Somewhat accurate analogy except for those of us who use both Windows and Ubuntu. I like being able to customize my user interface for consistency ie having the control icons on the right.

When I used to run both Linux and OS X, it was, in fact, pleasant if both interfaces kept things more or less in the same place. 

Re: roads -- Roads are a public service. The choice of right or left must be uniform and enforced, otherwise we'd kill ourselves.  Software is a product, not a public service.  No one compels anyone to buy and use any of it. 

To be intentionally flippant, I don't order a margherita pizza and complain that someone is enforcing a no-anchovy rule.

---

### Post by r_avital on 2014-04-25
3rdalbum,

Thank you for the most pertinent and interesting answer so far.

> **3rdalbum said:**
> Because in maximised windows, the buttons would look pretty stupid on the right of the indicators. You'd also be left with blank space there when the window wasn't maximised, or the indicators would move depending on the state of the window - either way would be terrible.

Not trying to be difficult, I just don't follow.  If you take a look a the two images below:

Unmaxed: The window's min/max/close buttons on upper-right corner.  No blank space on panel, indicators are all where you'd expect them.

Maxed: The window's min/max/close buttons don't even show.

[IMG]https://db.tt/B7ljWuOD[/IMG]  [IMG]https://db.tt/gH4adMwH[/IMG]

In fact, I find the way Unity handles the maxed window very intelligent, merging the windows title-bar with the Unity panel. Sure, when maxed, there are min/max/close buttons on the right, but they're easy enough to ignore -- simply double-click on the panel, or drag down the maximized window to un-max it.  But again, I don't see what you mean.  This is in Raring.
> **3rdalbum said:**
> Why is the Launcher on the left instead of on the right?
I have no problem with the placement of the Launcher, and your explanation makes perfect sense to me -- for a right-handed person, as you noted.  My argument is that in a Linux system, it should be configurable, and I don't expect anyone to figure out for anyone else how to do it.  Let those who can code provide the hack.
> **3rdalbum said:**
> 
The Launcher doesn't go on the top or bottom because that would restrict precious vertical space on a widescreen monitor.
Obviously, true.  My monitor is rotated vertically, and I'm forever grateful for xrandr, which allows me to flip to landscape to watch videos, and back to portrait again when I'm working.  There, I can code that much, so I don't complain about workspace orientation.  God Bless Linux.
 > **3rdalbum said:**
> 
Frankly, if you've been changing the order of window buttons to the right side every six months since 2010, you've been putting yourself through a lot of work to avoid adapting.
Well, no, I haven't, but I read these forums and others often enough to have heard the same complaint from many users, over and over, with each new release.  I made the change once, in Lucid -- I love LTS releases -- and I've blissfully ignored Maverick, Natty, Oneiric, Precise, and Quantal, until well past Lucid's EOL.

Yes, it was always that way with Unity, as you say, but it was also the case that it was always configurable by the end-user, who is not interested in spending a lifetime studying and tweaking an operating system, but rather using an operating system, with a simple adjustment in, say, dconf-editor.

My question was, why was it so important that Canonical would, again, put in extra effort to nullify that adjustment (and in gconf/Unity-Tweak and all other tools that provided it).  I'm quite sure a lot of users would have been happier if they had invested that extra effort in more regression-testing to prevent legitimate functions from breaking after they've worked flawlessly -- e.g. built-in webcam on laptops and Atheros wi-fi no longer recognized in Trusty, lightdm ignoring directives in its configuration files, and other such stuff that was, again, working fine in Raring.

At any rate, thank you, this has been informative.

---

### Post by r_avital on 2014-04-25
> **buzzingrobot said:**
> 
To be intentionally flippant, I don't order a margherita pizza and complain that someone is enforcing a no-anchovy rule.

Of course not, that wouldn't make sense.  But if you did get the anchovies anyway, and you liked them, and years later, after you've been taking for granted that you'll always have them, or at least maybe, have to pay just a little extra for them, all of a sudden there's a Great Wall of China between you and the anchovies, and you're told it's up to you to drill through it to get them, and anyway, "no one is forcing you to have your pizza here, and no one is preventing you from drilling through that wall,"  What would your reaction be?  Because to use your fairly accurate analogy, that's what's happened here.  Not with comfort-food, but with software that people use, to be productive.

And to be clear, I'm past "reacting," I was asking a question in order to understand.

Thanks.

---

### Post by PondPuppy on 2014-04-25
+1 to 3rdalbum's explanation. 

It's a design decision. Making everything ultimately configurable, or making some desktop config items fixed, is another design decision. Mac has the buttons on the left. Fedora (Gnome desktop, default config) has a single X button on the right, no max or min button. Zorin has them on the right, like Windows. Manjaro (xcfe, default config) has all three buttons on the right, with a window-manager icon ("roll window up", etc) on the left. (Never noticed that one before.) 

I guess my point might be that every distro makes choices. And it's reasonable not to have every single choice configurable. From a coding standpoint, it's usually simpler to have a fixed interface. Fewer lines of code, fewer lines to debug, fewer chances of errors. Not an excuse for locking down user choice, but an explanation for why programmers in the real world sometimes balance configurability against complexity. Another explanation is interface complexity and user confusion, I guess.

Yadda, yadda -- sorry, this is more or less what others have written.

---

### Post by blitzd on 2014-04-25
I'd recommend Mint Linux, Cinnamon or MATE.

While there is the argument that you can switch DEs within Ubuntu, anything but the default always seems to be a subpar experience... Unless you're willing to put in some serious time troubleshooting and reconfiguring - the last time I tried to do that turned out to be about as productive as this thread is going, and it's linked above.

---

### Post by r_avital on 2014-04-25
> **PondPuppy said:**
> 
Yadda, yadda -- sorry, this is more or less what others have written.

Not at all, these are all valid points.  Reasonable people will disagree, but valid points.

Thanks.

---

### Post by sffvba[e0rt on 2014-04-25
*Thread moved to **Recurring Discussions**.*

---

### Post by r_avital on 2014-04-25
> **blitzd said:**
> I'd recommend Mint Linux, Cinnamon or MATE.
MATE is good, but it has its own bug issues, and therefore (in addition to other reasons), like you said, a bit subpar.  Truth is, the Unity Launcher is, or can be, very useful, and I'm still hesitating as to whether I want to stay with it or go MATE.

---

### Post by buzzingrobot on 2014-04-25
> **r_avital said:**
> But if you did get the anchovies anyway...

Wouldn't be a margherita pizza.  

> ... and you liked them, and years later, after you've been taking for granted that you'll always have them, or at least maybe, have to pay just a little extra for them, all of a sudden there's a Great Wall of China between you and the anchovies, and you're told it's up to you to drill through it to get them, and anyway, "no one is forcing you to have your pizza here, and no one is preventing you from drilling through that wall,"  What would your reaction be?  Because to use your fairly accurate analogy, that's what's happened here.  Not with comfort-food, but with software that people use, to be productive. 

I'd go somewhere else for my pizza.

People who make pizzas can make any kind of pizza they want.  They can change any recipe at any time.  Customers who don't like the changes can go elsewhere.  Ditto purveyors of software. If you are *selling* something, it is rational to pay attention to your customers, but there's no real obligation to do that.  Canonical also has no real obligation and isn't even selling software. How to accurately guage the whims and wishes of open source users has been, in any case, a near impossibility.

While it's fair and fine to like whatever we like, and no rules exist for this sort of thing, I have to admit I find it difficult to understand why issues like this have caused so much angst since Gnome 2 bit the dust 3 years ago. All the DE's are almost all the same: icons we click on, menus we scan.

---

### Post by r_avital on 2014-04-25
> **buzzingrobot said:**
> 
I'd go somewhere else for my pizza.


...wwwwellll... call me deranged then, but I'll venture that most people would be disappointed, and they'd say so.  Sure, it's easy to go somewhere else for pizza.  Is it just as easy to go to another distro, or even another DE matching the same distro, and have to get used to new bugs, and find new fixes and hacks to get around them, which will impact your productivity?  I don't sprinkle parmesan on my Ubuntu.  That analogy is a bit limited.  

Would you just as casually replace your car, if after your scheduled maintenance, you found out that the turn-signal and wipers controls were switched around and you had no way to switch them back? [Thank you 3rdalbum, for that much better analogy.]

Again, nobody asked Canonical to change it.  It was their initiative.  Instead of testing for the regressions/bugs I've listed a couple of posts ago, they invested time in removing something that was there.  And as I said, I was long past reacting and moaning about it, and I simply asked a legitimate question.  There's really nothing more to that. :)

I'm pretty sure this horse is dead.  At least until someone comes up with a hack to fix it (or break it, depending on one's religious convictions/political affiliation).

---

### Post by pfeiffep on 2014-04-26
> **blitzd said:**
> I'd recommend Mint Linux, Cinnamon or MATE.

While there is the argument that you can switch DEs within Ubuntu, anything but the default always seems to be a subpar experience... Unless you're willing to put in some serious time troubleshooting and reconfiguring - the last time I tried to do that turned out to be about as productive as this thread is going, and it's linked above.

My user experience was _greatly_ enhanced when I installed gnome flash back choosing metacity.

---

### Post by r_avital on 2014-04-26
3> **pfeiffep said:**
> My user experience was _greatly_ enhanced when I installed gnome flash back choosing metacity.

Same here, I tried it out when it was still called "gnome fallback" --but the trouble is, can you really count on it being available and maintained in the future, and for how long?  I hope I'm wrong, but I doubt it.

---

