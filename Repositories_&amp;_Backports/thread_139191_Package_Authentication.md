---
title: "Package Authentication"
date: 2006-03-03
forum: Repositories &amp; Backports
---

### Post by MikeMcKay on 2006-03-03
A month or so ago I upgraded from Hoary to Breezy and afterwards had periodic problems with packages for update being flagged as not authenticated.  I use Synaptic for all package administration.

The repositories I used for Hoary were gb.archive.ubuntu.com.  To do the upgrade I simply changed all references in sources.list from Hoary to Breezy so I continued to use this URL for Breezy package maintenance.

Finally, following some hints and a hunch, I changed all the repositories to archive.ubuntu.com did a reload and the problem went away.

I had naively assumed that all packages would be signed once before distribution to the various mirror sites and so the signing would be the same regardless of which repositories I used.  Clearly this is not the case.

Can anyone explain, or point me to an explanation, of how package signing is administered and how it varies between the mirror sites so that I can avoid similar SNAFUs in future ?

---

### Post by Xian on 2006-03-03
Basically, if what you outlined is in fact the case then it is a bug and should be reported as such. There really is no good explanation as it a dramatic error that needs to be resolved.

---

### Post by 5-HT on 2006-03-04
While I am not knowledgable about package signing for the various mirrors, I have come across a quick fix for this issue in these forums apart from switching mirrors (sorry I'm not sure who originally found this out, but all the credit goes to you).

i. Backup your sources list to something like /etc/apt/sources.list.backup
ii. Create an empty file for the new /etc/apt/sources.list
iii. Update the package list
iv. Revert back to the backup sources list
v. Update the package list

And hopefully the signing errors should go away.

So maybe it is the fact that you changed your sources and updated the package list in the process of switching mirrors, apart from the actual change of mirrors that was resposible?

Because of this, it seems as if maybe the problem lies not with the servers, but rather seems to be something to do with apt's own records on the localhost?

I very well could be, am probably am,  completely ignorant of what's going on here, but this evidence seems to support such a conclusion.

---

### Post by MikeMcKay on 2006-03-04
Thanks for the contributions.

Xian, I've submitted bug report No. 33696.  I've included a reference to this thread so any submissions here should be easily found by whoever ends up working on the bug.  

5-HT, I'd never have found that in a million years . . .  I think that's a valuable bug characterisation.  You'll see from the previous paragraph that it ought to be seen by whoever (eventually . . .) works on the bug.

Keep your contributions coming!

---

### Post by 5-HT on 2006-03-04
Oh sorry, I'm not trying to insinuate that this is not a bug, sorry if it came across like that.
No matter if it is something to do with the mirrors, or just apt itself (which seems less likey now that I think about it), there is no doubt something going on (and I've seen more than a few posts about signing errors).

I just thought that what I posted may have some relevance (could have none at all though).

Hope that it gets worked out. 
Would you mind posting back when you've heard from whomever looks at the bug report, I'm curious to see what may be going on?

---

### Post by MikeMcKay on 2006-03-04
5-HT,

No worries; I didn't read your reply to mean that there wasn't a bug.

You've given more info about the how the bug behaves and also another workaround for anyone who needs it. Thanks.

---

