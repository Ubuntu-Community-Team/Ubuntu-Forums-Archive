---
title: "Ubuntu Support Network"
date: 2007-04-06
forum: Pennsylvania Team - US
---

### Post by tclark on 2007-04-06
The typical home/small office computer user, regardless of operating system, needs technical support from time to time.  Often, they can't get it, or they have to pay someone like Geek Squad <shudder />.

So here's my idea:  Let's make a list of people who are available to provide some basic tech support for Ubuntu, e. g., someone who will come to your home and help you set up a printer.  This help will be provided for free, but it should be limited to home, school, and perhaps very small office users.  For parties that really should be served by professional support, we could refer them to selected Ubuntu consultants.

Volunteers need to be polite, patient, and reasonably capable.  We will be ambassadors for Ubuntu, so it's critical that we make very good impressions everywhere we go.  And please, no bashing of other distros or operating systems.

What do you think?

---

### Post by lamalex on 2007-04-06
I'd be willing to help out but at the same time I'm a very busy person, I can't always guarantee my availability. I always give out my email/IM/cell phone to people when I give them a cd so they can contact me. Also I put  the URL of the forum and wiki on the paper I wrap my cds in. If someone organized this I would definately help when I could.

---

### Post by bfledderjohn on 2007-04-06
Tclark,

This is a good idea on so many levels.  One being the perceived lack of support with Linux.

This could help disburse the myth.  I can help people in person, however, I am less than helpful over the phone or via internet. :-(

---

### Post by lamalex on 2007-04-06
We could also set up VNC support, connect remotely to those who are comfortable with us doing so.

---

### Post by kejava on 2007-04-08
Iamalex,

I was thinking of just ssh but vnc would be good too.  I know ssh is very secure, I'm not sure about vnc.  Whatever one we choose, we'll have to come up with a way protecting that login information.  This is where it can get tricky.  What happens if one of our remote support volunteers is black hat but we don't know about it?

This is something that needs to be heavily discussed.  It's one thing for someone to allow us to install Linux on their PC.  Granting members of our group remote access to their PC is something different.  Especially if they have administrative privileges.

Don't get me wrong.  I think remote access is necessary.  We may just have to do it in such a way that limits team culpability if something goes wrong.  Here are some of my questions:
[LIST]
[*]Can we setup a support account on the remote PC that has just enough permissions to be helpful yet not harmful to the core system?
[*]How do we grant access to these remote PCs to specific team members?  My guess is that only some of us will be remote admins.
[*]How and where do we store this sensitive remote login information?
[/LIST]Perhaps all the tools for this are common and already in place.  I've never done anything like this with a large group.

---

### Post by kejava on 2007-04-08
> **tclark said:**
> For parties that really should be served by professional support, we could refer them to selected Ubuntu consultants.
Recommending professional consultants is definitely a good idea for targets like small businesses.  For businesses, we may want to limit our support to installs and presentations.  Beyond that, we could refer them to consultants like the ACE Technology Group.  I suppose that even some of our team members could be those consultants.  At the consultant would have general liability insurance, particularly errors and omissions.

---

### Post by tclark on 2007-04-08
My thinking is that we would focus on in-person help for a few reasons.  First, I hope that we'll be helping new users.  For them, setting up their machine to allow remote access is too much to ask.  Security is also an issue.  Do we want to introduce new users to Ubuntu by encouraging them to give remote root access to a stranger?

More importantly, in-person help is more effective.  It's a more effective way to solve problems, and it's a more effective way to demonstrate to people that using Ubuntu connects them to a community.  Finally, it's a strong marketing tool.  Imagine the word of mouth value when a frustrated proprietary OS user hears his neighbor talk about the person who came to her house last week to help get her online.

---

### Post by kejava on 2007-04-08
tclark, well put!  I agree that our focus should always be on in-person support.  I tried walking my brother through an installation over the phone a couple of years back, what a disaster!

I don't think we should rule out remote access completely.  I completely understand there are risks involved but there can be situations where remote access is the only solution for some of our team members.  What about our handicap team memebers, that can physically be at the client site?  What if the client is in a dangerous part of Philly?  For physical saftey reason you should always go as a 2 or more team members.  What if you can't get a group together?

These could be rare situations.  I'm sure there are other reaons for remote access that I haven't pointed out.  Maybe we should just put it on the back burner until we can figure out a way to do it *properly*.

---

### Post by jedijf on 2007-04-08
Hello all!

In person support is always better when available.

VNC can be initiated by the person requesting assistance.  Much better scenario then straight VNC which would require port forwarding on the person needing supports end.
It is a great scenario for a help desk and would prevent a "black" hat from having access to the
machine when not supposed to.  At least not as easliy.

The "help desk" sets up a listening server, and the person needing assistance connects to the help desk, which then can remotely manage their computer.

Via a dynamic dns service, like dyndns.org, the help desk ip could be migrated to a domain name that would point to differrent ip's depending on who was "on call" that day or evening.

Over the phone is too frustrating!!!

jedijf
jim fisher

---

### Post by kejava on 2007-04-08
Hi Jim!  Good to see active in the group.  (I know Jim from PACS).

Yes, I like this help desk idea with VNC or similar.  Do you think there's a package for managing/tracking these connections?  Sounds similar to what IT uses for their help desk support.  I guess the main thing is if a team member does decide to black hat on a client, we need a way of know who they are and what they did.

Integrating dyndns into this is perfect.  I use it to ssh into to my office PC all the time.  Perhaps we can get an Ubuntu specific domain reserved from dyndns.org.  Each client could have somthing like "client_nnn@pa-ubuntu-loco.org" where nnn is just a number assigned to the client when they enter the help desk service.

I bet there is already something out there for most of this.  If not, we may be able to code up something simple.  Either way, it's good we're at least discussing it.

---

### Post by lamalex on 2007-04-08
I can give a +1 recommendation to ACE Technology group ... I work there. For small businesses we're the perfect IT solution, affordable, always on call IT that know what we're doing. I can say will 100% assuredness that we'll support any businesses that need us. If needed I can mail out our business cards to any project leaders dealing with small businesses.

---

### Post by kejava on 2007-04-08
That's partly why I mentioned it ;-)  I remember reading about them a few years back and was very impressed.  Then I noticed it you signature and profile.  I might look into their services for future projects.

---

### Post by bfledderjohn on 2007-04-08
I like the idea of a list of Ubuntu capable consultants in Pennsylvania for the folks who need professional help.  I mean professional computer help :-)

How would be qualify the consultants?  Or would we simply maintain a list and say use at your own risk?

Would someone like help with the wiki for that list?

---

### Post by lamalex on 2007-04-08
done, [http://www.ubuntu.com/support/commercial/marketplace/northernamerica](http://www.ubuntu.com/support/commercial/marketplace/northernamerica)

---

### Post by kejava on 2007-04-08
Iamalex, good link.  What's strange though is that ACE Technology Group is either bad or the site is down.  Another oddity is that ACE is the ONLY Ubuntu Affiliate in PA.  You guys could be getting a lot of business pushed your way ;-)

---

### Post by lamalex on 2007-04-09
site fixed. We had a DNS issue. Should be propagating now, if you get a message that says Site moved, update your DNS, wait an hour and try again :\ sorry about that.

---

### Post by bfledderjohn on 2007-04-09
Check out what the Ohio Team is doing. Rather than reinventing the wheel, we may be able to duplicate or modify their program(s)?  I don't know, but they are very active and they got approved very quickly.  It may not be for us either, but I think that we need to know what the other teams are doing.

The rest of their wiki is very well done.
[URL="https://wiki.ubuntu.com/OhioTeam/NewUserTeam"]
https://wiki.ubuntu.com/OhioTeam/NewUserTeam[/URL]

---

### Post by ichilegend on 2007-04-09
> **kejava said:**
> I was thinking of just ssh but vnc would be good too.  I know ssh is very secure, I'm not sure about vnc.

Just to add my 2 cents, I do security for a living and VNC is tricky.  Only professional (pay) versions have any real security.  You can enhance the security of VNC though by requiring user interaction.  Gnome has built in a product called Vino with works with VNC to give the user a bit more control over the session.  Other than the logon, the session is unencrypted.  A better solution would be to set up an ssh tunnel for VNC, but that is slightly more difficult and bound to scare a few new users.  Giving the user the ability to turn the VNC session on and off at will with an easy to use graphical application would provide better security than simply leaving VNC active and can be accomplished in Gnome by using the "Remote Desktop" icon in the preferences menu.  Krfb does the same thing in KDE/Kubuntu located under the Internet menu.  I have used these VNC front ends before to help other Linux users in the past and they tend to like the fact that it warns them when I am trying to view their PC desktop.

For my vote, I prefer to assist people remotely while speaking with them on the phone, but then again I don't get paid for my assistance.  I guess if I was charging, I would go out on site - but that is off topic!

Cheers,

---

