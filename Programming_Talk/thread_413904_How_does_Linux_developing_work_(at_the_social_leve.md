---
title: "How does Linux developing work (at the social level)?"
date: 2007-04-19
forum: Programming Talk
---

### Post by username132 on 2007-04-19
I was wondering about the levels of interaction involved in producing a Linux release? Take openSUSE for example - that one's done with Novell, so do they have paid developers that are ultra clever and have oversight and voluntary ones with certain responsibilities? Take the serialmonkey ([http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)) developers - they're not working for any particular distro, I don't think, so how does the interaction work between them and Ubuntu? I feel the need for a big diagram with lots of arrows. I imagine the story is different from different distros.

---

### Post by justin whitaker on 2007-04-19
I always envisioned them getting together in a big room, and throwing coffee beans at the new guys with bad ideas. The guy with the most beans is made the jr. kernel developer, or jr. marketing wonk, depending on who needs a coffee lackey at the time. :)

---

### Post by username132 on 2007-04-19
> **justin whitaker said:**
> I always envisioned them getting together in a big room, and throwing coffee beans at the new guys with bad ideas. The guy with the most beans is made the jr. kernel developer, or jr. marketing wonk, depending on who needs a coffee lackey at the time. :)

I think you've had enough... *tries to withdraw Justin's skinny soy caramel ubuntu*

---

### Post by Zuph on 2007-04-19
It really depends on the developer.  Some are more community driven, while others user more paid programmers.

---

### Post by lawentzel on 2007-04-19
Actually I've looked at a couple of games on Linux to see who all made them and so forth, and what I see, is one person works on what he does best.  Say networking, or graphics engine or objects.  Who decides who is best at that?  Maybe a portfolio of work they have done.  Or in some cases a desperate programmer willing to accept any sort of help he can get.  Just my two cents for what it is worth.

---

### Post by pmasiar on 2007-04-19
Lots of different skills beyond code hackers. You need someone to create pretty graphics, translate at least your own distro programs (like installer), people to triage bugs and assign priorities, people to administer servers/FTP/compile farms, people managing community (forum moderators etc), people contacting rich sponsors asking for financial support, people writing articles/PR/blogs, and "cat herders" - project managers managing all those people. And I certainly forgot some important skills - this is just an idea.

---

### Post by markitect on 2007-04-19
I'll comment on the kernel, but it applies pretty universally, programmers, whether paid or just want a new feature or to fix a bug, see a problem or a way to improve things, and make some changes.  Once they have the changes how they like them they send them out on the kernel mailing list as a patch.  Now its sent out to all the hardcore kernel people as well as anyone else that is subscribed and they start emailing back and forth any comments on it.  At some point (the developer hopes) one of the big guys (there are three separate main kernel branches with lead maintainers and a few other people who have the authority) decides its a good piece of code that will improve things and puts it in the kernel.  After some amount of changes the maintainer decides to do a release and all the people that make distros wait for these.  Now all the distro maintainers see the new kernel and configure it for their distro and send it out as an update. Everyone gets it and somebody sees something else they want to change and the process starts all over again.

The exception to this is the maintainers and that handful of other people can just plop new code in.

And often distro maintainers see a patch that the kernel tree hasn't accepted and decide they like it enough to include it in their distro.

So basically the development has a tree structure.  Most changes move towards the root, and when they gain acceptance they move down towards leafs under the node that has accepted it.

That said some estimates say most kernel work is by paid developers (for redhat, suse, etc) other by freelance people.  But almost everyone has one specialty be it drivers or filesystem, etc.

---

### Post by wmcbrine on 2007-04-20
Interaction between the developers of individual packages and Ubuntu? In many cases (including my own), there is none. I maintain a program... a Debian maintainer takes my new releases and makes Debian packages of them... and then Ubuntu grabs everything from the Debian repositories every so often. This is how the majority of packages get in. Of course some groups, like the Gnome team, may work much more closely with the Ubuntu people.

---

