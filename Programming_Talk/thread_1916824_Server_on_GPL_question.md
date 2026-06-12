---
title: "Server on GPL question"
date: 2012-01-28
forum: Programming Talk
---

### Post by Pierrick584 on 2012-01-28
Lets say i base my server's work over an existing server in GPL, how does the GPL apply, i mean, the obligation to give source.

From my understanding, you need to give source to the end user, in the case of a server, I am the end user and people who comunicate to the server though a client doesnt actualy have to see the server's source, right? or am i wrong.

Dont take me as an *** who doesnt respect GPL, i plan to build a game, and i might base my work off an existing server on GPL, yet many things in the server code must not be public.

---

### Post by SeijiSensei on 2012-01-28
I don't think that's kosher under the GPL, but I'm neither an expert nor an attorney.  I'd start by reading the relevant sections from the [GPL FAQ]("http://www.gnu.org/licenses/gpl-faq.html").  If you remain unsure, you'll need to consult an attorney that specializes in software law and understands the GPL.

It sounds like either (a) you want to modify GPL code but not release the modifications; or, maybe, (b) you want to link from GPL-code to closed-source binaries.  I know that (a) is almost certainly a [violation]("http://www.gnu.org/licenses/gpl-faq.html#GPLRequireSourcePostedPublic") *if you distribute the modified software to others*.  If you don't distribute the software, and just use it on you own server(s), you aren't violating the terms of the GPL.  (Remember, the GPL is concerned with distributing software to third-parties.) Option (b) is more complicated.  It might be akin to using closed-source video drivers with the GPL Linux kernel, but you'd need to talk to real experts if that's the approach you're looking to take.  Again if you don't distribute your modified software, you won't be violating the GPL.

---

### Post by trent.josephsen on 2012-01-28
I think that would be OK as long as the server is used in house by you alone; the derivative work definition would apply, but if you're not distributing the work itself you would not be under any obligation to provide the source.  However, if you sell or distribute it **at all**, you would then be under such an obligation.

Regarding the client-server relationship... well, if your server (or at least the parts that make the client-server interface demonstrably unique) isn't licensed under the GPL, then all you're doing is making a GPLed client to a closed-source protocol, which automatically grants you ethical superiority. :)

HOWEVER, this is the kind of thing you should absolutely ask a lawyer rather than posting in an online forum.  Also note that no interpretation of the GPL really matters except the interpretation of the court that settles your lawsuit.

---

### Post by Pierrick584 on 2012-01-28
Thanks both of you for the answers, yeah the thing is realy about running the servers for my personal use (well, servers giving service to many people but, i aint distributing the server binary)

And realy, its not about not putting the server as GPL, technicaly i dont care that my server is in GPL, but i were just wondering at some point if using the service provided by the server count as server beign distributed.

Example: I am a nowhere logging on a game server with a perfectly legal proprietary game client, but the actual game server is in GPL, does using the service provided by the software give right to the source code?

You guys pretty much made it clear, i think, i guess it does not apply to service provided, but plain binary distributed, my game's server binary will not be distributed, and if it does, i dont mind it beign fully GPL with source, its just more customisation to the users, if i end up to distribute server, its so people can customise it anyway.

Thanks!

---

### Post by Bachstelze on 2012-01-29
I don't see any problem with it. The GPL only requires you to distribute the source if you distribute the software in another form, like a binary. If you are just making a server, you are definitely not redistributing the software in any way, so ou don't have to release your source.

---

### Post by Barrucadu on 2012-01-29
You don't have to give the source to users of your server, unless you also provide them with the binaries. In fact, this is exactly why the AGPL exists - which does stipulate that users of a server are entitled to the source.

---

