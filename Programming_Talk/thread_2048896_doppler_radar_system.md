---
title: "doppler radar system"
date: 2012-08-27
forum: Programming Talk
---

### Post by emmathompson on 2012-08-27
hi guys, I'm a python person & I'm looking at doing sth on the [SIZE=3]**doppler radar system**. [/SIZE]Anyone interested?

---

### Post by trent.josephsen on 2012-08-27
You do realize this is something like saying "I'm a microbiologist and I'm looking at doing something with a lathe", right? I mean, it's not only incredibly vague, it's not even in your field. How do you intend to relate programming to Doppler radar?

---

### Post by alexfish on 2012-08-28
You could use the printer port for the emit and return signals.

or if using usb , it may be possible program an interface to using libcssl

the interface needs to take into account for any discrepancies as regards timing issues

but not impossible.

regards

alexfish

---

### Post by emmathompson on 2012-08-28
python is robust, its actually in view of a larger system. something that'll need radar technology. & then, every now  & then a good microbiologist finds use of some kind of lathe

---

### Post by muteXe on 2012-08-28
Hiya,
What's 'sth'?

---

### Post by prismctg on 2012-08-28
> **muteXe said:**
> Hiya,
What's 'sth'?
  sth = something  :)

---

### Post by muteXe on 2012-08-28
ahhh right.  Thank you :)

OP: do you want to do something with a real system? or model a radar system?

---

### Post by trent.josephsen on 2012-08-28
> **emmathompson said:**
> python is robust, its actually in view of a larger system. something that'll need radar technology. & then, every now  & then a good microbiologist finds use of some kind of lathe

Biology is only part of a larger system, something that will need machined parts out of steel or aluminum.

See how vague that is?

---

### Post by emmathompson on 2012-08-28
The idea is a system that cross references every aircraft  that enters a country's airspace with a database of aircrafts flown by carriers in the country. Specific data like no. of hrs. since last maintenance, no. of hrs. to nxt maintenance, recommendation(s) of maintenance facility., etc. will be periodically uploaded by fliers. Failure to upload data on aircraft or use of an unregistered aircraft should attract some heavy fine. 

Does anyone see the feasibility & use of such a system?
thanks **prismctg**.

---

### Post by whatthefunk on 2012-08-28
what does this have to do with doppler radar?  Im sure that the US governemnt already has a strick system in place regarding aircraft maintenance...

---

### Post by emmathompson on 2012-08-28
> **whatthefunk said:**
> what does this have to do with doppler radar?  Im sure that the US governemnt already has a strick system in place regarding aircraft maintenance...

Doppler is one of the best around, I'd take  up any other suggestion. You're very correct, but the US govt. is nt the govt. of 2nd & 3rd world countries whose singular casualty in air crashes sometimes total several that occur in the US.

---

### Post by trent.josephsen on 2012-08-28
Doppler radar can tell you the velocity of an object if you know where it is. It won't tell you anything about the identity of an aircraft. It can't even tell the difference between an aircraft and a large bird. You may be thinking of the [system](http://en.wikipedia.org/wiki/Secondary_surveillance_radar) used in ATC that requests additional information from a transponder on the aircraft. I believe all aircraft that fly in the US are required to have a transponder, but I don't know if they're required to have it turned on all the time.

It is definitely feasible to monitor all air traffic entering and leaving a geographical area, and cross-reference them automatically against a database. Airports already do this. I don't know about the feasibility of controlling an entire country's airspace this way; I imagine it would be prohibitively expensive for most countries, and geography could cause some practical issues. (Fancy installing lots of heavy and expensive radar equipment in the Himalayas?) But this isn't really a programming question.

As for use, that's something you should ask someone in the industry. What problem or problems does this system purport to solve? Is there some less expensive way to enforce aircraft maintenance? Is it legal to surveil upon private pilots in this manner? Is the system at all practical if the pilot can just switch off his transponder and fly anonymously? These are all questions you're going to have to find answers to and none of them are programming-related. Find an air traffic controller or a pilot. If you're in the US, maybe you know someone in Civil Air Patrol. Or look online for forums frequented by such people.

The only programming-related aspects of this project that I can think of are implementation details composing at most 10% of the system you propose, and what language to use is probably the last thing you should be worrying about right now. Cart before the horse and all that.

[quote=Eric S. Raymond]Every good work of software starts by scratching a developer's personal itch.[/quote]
<hypothetical>What itch are you trying to scratch?</hypothetical>

---

### Post by muteXe on 2012-08-29
Still not sure what you want to do.
If you want to know how civil aviation authority does it (locates and tracks aircraft) you wanna google "ads-b"...

edit: also have a google for 'multilateration techniques'.

---

### Post by emmathompson on 2012-08-29
recently, there was an airplane crash in my country, at least 153 people(aboard & on the ground) died, there were whole families aboard that plane. One family was traveling to meet the head of the home, another was returning from a wedding, a man lost a his multi-million fish farm, ...the list goes on. Reports are pointing at poor condition of the aircraft, something people who flew that plane days before are corroborating. Some people  knew about the terrible state of that aircraft, they  either did nothing, didn't act early enough, or didn't act well enough to stop that plane from flying.

I didn't loose anyone on the plane, but do I have to before I do what I can?

I implore as many of u as maybe of help to this project to mail me at **tekunniyi@gmail.com**, anything, whatever u think might be of help. If there was a free or at least, cheaper, simpler system like the one I'm proposing here, 'maybe' those lives may have been **saved.** Who knows what may spring from this, it could benefit any of us, in ways we are yet to imagine, what's more? I think its going to be fun. 

thanks for scratching my itch ***trent***

---

### Post by muteXe on 2012-08-29
Pretty decent odds if you ask me.

---

### Post by Tony Flury on 2012-08-29
> **emmathompson said:**
> 
I implore as many of u as maybe of help to this project to mail me at **tekunniyi@gmail.com**, anything, whatever u think might be of help. If there was a free or at least, cheaper, simpler system like the one I'm proposing here, 'maybe' those lives may have been **saved.** Who knows what may spring from this, it could benefit any of us, in ways we are yet to imagine, what's more? I think its going to be fun. 


What project - you have not actually defined a project that needs to be developed, what it should do, why, and who for.  I might be wrong but i doubt anyone will say that they will help when you can't actually describe clearly what you want.

A project that saves lives is very laudible - but i am guessing that the software development bot of this is tiny, the bigger issue are things like - the physical infrastructure required to implement that actual system (servers etc), the physical radar installations that will be required, the physcal security required in terms of the installations and the equipment, the legal framework required in each jurisdiction to make these rules enforcable. I would imagine in every developing country which doesn't already have a overflight control system in place has other things to worry about (like feeding it's population), which are far higher on it's priority list.

---

### Post by emmathompson on 2012-08-29
> **Tony Flury said:**
> What project - you have not actually defined a project that needs to be developed, what it should do, why, and who for.  I might be wrong but i doubt anyone will say that they will help when you can't actually describe clearly what you want.

A project that saves lives is very laudible - but i am guessing that the software development bot of this is tiny, the bigger issue are things like - the physical infrastructure required to implement that actual system (servers etc), the physical radar installations that will be required, the physcal security required in terms of the installations and the equipment, the legal framework required in each jurisdiction to make these rules enforcable. I would imagine in every developing country which doesn't already have a overflight control system in place has other things to worry about (like feeding it's population), which are far higher on it's priority list.
I appreciate ur advice **tony, **believe me u've succesfully pointed out some things I've overlooked until now. I was hoping that this being a place for developers, I could get some insights & guidance, so far I don't think I'm disappointed.
On **trent**'s advice, I'm now looking at using the ADS-B (automatic dependent surveillance-Broadcast) instead of the doppler system earlier suggested. I understand actual coding is only a small part of this, but what could i do without the seasoned advice of you gurus? So pls. keep them coming, I appreciate it.

---

### Post by emmathompson on 2012-08-29
> **muteXe said:**
> Pretty decent odds if you ask me.
I'll bet those odds get worse if u're flying in or around Africa (no prejudice)

---

### Post by whatthefunk on 2012-08-29
This is not at all a computer program.  This is a government problem.  In "developed" nations, airlines dont do routine safety checks out of the kindness of their hearts, they do it because the government forces them to do it and has strick penalties for airlines which fail to comply.

---

### Post by Tony Flury on 2012-08-29
> **whatthefunk said:**
> This is not at all a computer program.  This is a government problem.  In "developed" nations, airlines dont do routine safety checks out of the kindness of their hearts, they do it because the government forces them to do it and has strick penalties for airlines which fail to comply.

+1 
This is exactly what i was refering to when i mentioned the legal/regulatory framework.

Just because an application exists that allows you to take aircraft transponder data and cross-reference it with maintenance records does not mean that suddenly goverments will start using it, and fine companies who don't comply with the regulations. The regulations themselves have to be written and argued about. all the other infrastructure needs to be bought and deployed. It is naive in the extreme to expect that the creation of a single computer program (however well written) will suddently persuade governments to invest in all the other costs of the system that I mentioned (and probably many others), and enact all the rules and regulations required or implied by the systems as a whole.

The reason that many developing world countries have a poor regulatory system for their aircraft is many fold -infrastructure (physical as well as the neccessary skilled people), relevant priorities (over say feeding the poor or educating children or eradicating diseases), and the wish to keep their airlines running at some level vs forcing them out of business (most of these small airlines run on a shoe string but do provide a vital commerical and economic service).
You will also need to take into account not just the cost of imposing the regulations themselves, but also the extra costs to the airlines of complying with the new regulations. Off all of these items my guess would be that the presence of a free computer database would be insignificant - and really not feature in the equation.

The radar hardware alone for any sizable country would probably cost into the billions of dollars if not more. All the other costs including enacting and enforcing the regulations woudl probably be many several more millions per year. A commerical application to provide the databse - maybe a few million if that - making that bit free does not do anything for that cost of the rest, and still puts it way out of reach for most developing countries.

Now if you can make a cheap open source radar installation - and find a way for countires to enforce their rules free of chanrge - then you have something worth talking about :-).

---

### Post by Tony Flury on 2012-08-29
emmathompson - if you really want to help save lives in the developing world, you might want to look at a diffierent problem where the solution does not require billions of dollars worth of very complex extra hardware.

Things that spring to mind are - in no particular order : 

Many developing countries have reasonably good modbile service - could we develop a distributed system working on simple smart phones that allowed remote access to medical records for travelling doctors ?

or maybe a smartphone/tablet diagnostic tool that allowed helath workers to intelligently search medial knowledge in a structure way to aid diagnosis.

or a simple system that allowed for easy tracking of disease out-breaks against demographic or geographic information.

or a routing algorithm that would help travelling health workers identify an optimal schedule.

or a distributed market/pricing system that allows farmers to link up with traders to get the best prices for their goods without having to travel 100s of miles to market and back 

any other ideas ?

---

### Post by emmathompson on 2012-08-29
> **Tony Flury said:**
> +1 
This is exactly what i was refering to when i mentioned the legal/regulatory framework.

Just because an application exists that allows you to take aircraft transponder data and cross-reference it with maintenance records does not mean that suddenly goverments will start using it, and fine companies who don't comply with the regulations. The regulations themselves have to be written and argued about. all the other infrastructure needs to be bought and deployed. It is naive in the extreme to expect that the creation of a single computer program (however well written) will suddently persuade governments to invest in all the other costs of the system that I mentioned (and probably many others), and enact all the rules and regulations required or implied by the systems as a whole.

The reason that many developing world countries have a poor regulatory system for their aircraft is many fold -infrastructure (physical as well as the neccessary skilled people), relevant priorities (over say feeding the poor or educating children or eradicating diseases), and the wish to keep their airlines running at some level vs forcing them out of business (most of these small airlines run on a shoe string but do provide a vital commerical and economic service).
You will also need to take into account not just the cost of imposing the regulations themselves, but also the extra costs to the airlines of complying with the new regulations. Off all of these items my guess would be that the presence of a free computer database would be insignificant - and really not feature in the equation.

The radar hardware alone for any sizable country would probably cost into the billions of dollars if not more. All the other costs including enacting and enforcing the regulations woudl probably be many several more millions per year. A commerical application to provide the databse - maybe a few million if that - making that bit free does not do anything for that cost of the rest, and still puts it way out of reach for most developing countries.

Now if you can make a cheap open source radar installation - and find a way for countires to enforce their rules free of chanrge - then you have something worth talking about :-).
Nigeria recently upped her radar system, & I know a handful of other African countries with functional radar coverage. Did you know that in installation alone, the cost of radars, especially SSR, far outweigh an average ADS-B system. Countries in Europe, e.g. Germany are already integrating ADS-B into their ATCs, & in the Americas, the US plans to make it mandatory for commercial airliners by 2014.
I wouldn't consider any country with US's category 1 FAA status as one with small airlines & to face it, these govt.s won't write the s/ware themselves, neither will they get the idea until someone puts it to them.

---

