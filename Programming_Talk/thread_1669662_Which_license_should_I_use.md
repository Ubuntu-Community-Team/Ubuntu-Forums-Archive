---
title: "Which license should I use?"
date: 2011-01-18
forum: Programming Talk
---

### Post by Nerdcore Steve on 2011-01-18
I admit that when I try to read through all the legal junk on the gnu website I have trouble motivating myself to search through it all to find the information I really want.

I want to license my project as completely open source, I don't want a license like Java's or Android's, which is apparently only partially open source. I want my code to be freely available to anyone to use, modify, distribute that code so long as they return the favor with any modifications or additions they make.

So, which one is that?

---

### Post by worksofcraft on 2011-01-18
> **Nerdcore Steve said:**
> I admit that when I try to read through all the legal junk on the gnu website I have trouble motivating myself to search through it all to find the information I really want.

I want to license my project as completely open source, I don't want a license like Java's or Android's, which is apparently only partially open source. I want my code to be freely available to anyone to use, modify, distribute that code so long as they return the favor with any modifications or additions they make.

So, which one is that?

That would be the lesser public license, but I want to warn you that it is **not a good idea** because you will give away all rights to ever get anything from it and big cash rich companies can steal all your ideas hide them inside their products add their own with restrictive licenses and get even richer... IMO it undermines and devalues the worth of computer programming!

I recommend you use the Gnu General Public License V3. The main difference is that your software is only free to students and other people who contribute theirs in the same way. You can then have other licensing agreements that might include some royalties for you should it get used in profitable commercial applications.

---

### Post by Ravenshade on 2011-01-18
Or if you're not capitalist and don't mind anyone else using your work for any reason. Simply release it into the public domain. That way, everyone can use the work and no one can put claim to it aka charge royalties off it, since it is in the public domain. They can make modifications and charge money based on those modifications, but then, that's not your work. 

You simply have to explicitly state that the code or program belongs to the Public Domain.

---

### Post by ssam on 2011-01-18
> **Nerdcore Steve said:**
> I admit that when I try to read through all the legal junk on the gnu website I have trouble motivating myself to search through it all to find the information I really want.

I want to license my project as completely open source, I don't want a license like Java's or Android's, which is apparently only partially open source. I want my code to be freely available to anyone to use, modify, distribute that code **so long as they return the favor with any modifications or additions they make**.

So, which one is that?

that means you want a 'copyleft' licence like GPL, and not like BSD or MIT.

LGPL is to allow a closed source program to link to your library, or for allowing closed source plugins to a program. from what you said it does not seems that you want this.

i recommend that you stick to one of the main licences, eg GPL, LGPL, BSD or one of the creative commons (more for are than software).

also remember that you will be the copyright holder, so you can change the licence at any time, but you can't revoke rights you have already given.

---

### Post by nvteighen on 2011-01-18
I wonder what you mean with "returning the favor". To me that sounds like you want to allow the publishing of a modified version if and only if those modifications are sent back to you.

I don't know of any license doing that.

Free Software, according to the FSF, works in a completely different way: you give full permission to anyone to redistribute (gratis or for a fee) and to publish modified versions of your program as long as the licensee also gives the same permissions he was granted. The idea is that the same piece of code remains Free no matter in which hands it lands. This is how the GPL basically works; then, the GPL states different mechanisms in order to make this ideal be true.

Open Source, according to the FSF, or what people generally call "non-copyleft Free licenses" give full permission to redistribute (gratis or for a fee) and to publish modified versions, with no further requirements than attribution. This is how MIT- and BSD-style licenses work: the licensee can do anything with your code as long as he states that that code isn't his... he can even relicense it or not show the source code either. The LGPL can be considered to be in this group too, but some details in it make it more an intermediate between this and the full-fledged GPL.

Under my interpretation, what you want sounds more like a "gatekept open source model". This means: even though you're not stating it this way, you're effectively acting as a gatekeeper on what modified versions can be published and which not. Even though you won't be "approving" modifications, you want to get the modifications people do to your work. This means that nobody will be allowed to publish his modified version until and unless they send it back to you... but then, they have to prove somehow that you got that modified code... so, in practice, you'll have to reply to the licensee giving him confirmation that you received the modified code and you were informed, in accordance to the license's terms. In my opinion, this renders the whole license not too different to how copyright works by default.

Of course, if this is what you want, your local copyright law probably allows you to do it, so you're free to do it. But I wouldn't call it "Free Software" or "completely Open Source".

But, again, I'm not sure on what you actually meant by "returning the favor" and this post is based on my interpretation. So, please, if I'm reading your post wrong, don't hesitate in clarifying this.

P.S.: I'm not a lawyer, but have some basic legal training.

---

### Post by Nerdcore Steve on 2011-01-19
Sorry if I wasn't clear.

"you give full permission to anyone to redistribute (gratis or for a fee) and to publish modified versions of your program as long as the licensee also gives the same permissions he was granted."

That's what I want. I want something similar to the Creative Commons BY-SA license. I want people to share, I don't care to receive anyone's modifications to my code so long as they share those modifications with the same license. 

I was worried about licensing my program in such a way that I would "give away all rights to ever get anything from it and big cash rich companies can steal all your ideas hide them inside their products add their own with restrictive licenses and get even richer"

I don't want that.

I seem to remember that Linus Torvalds had an objection to Gnu General Public License V3 for that reason.

---

### Post by worksofcraft on 2011-01-19
[QUOTE=Nerdcore Steve;10377074
I seem to remember that Linus Torvalds had an objection to Gnu General Public License V3 for that reason.[/QUOTE]

Article [Why you shouldn't use the Lesser GPL...]("http://www.gnu.org/philosophy/why-not-lgpl.html") suggests that would be only the **lesser** GPL and the full version is doesn't have that problem.

---

### Post by ssam on 2011-01-19
the share-alike in CC-BY-SA is a copyleft clause, so you want GPL.

---

### Post by Nerdcore Steve on 2011-01-19
Ok, I'll use GPL v3. Thanks for the clarification. :D

---

