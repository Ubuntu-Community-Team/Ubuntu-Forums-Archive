---
title: "A question"
date: 2008-01-29
forum: Programming Talk
---

### Post by rekahsoft on 2008-01-29
Hi all, i have been programming some lately and i came across a question...say i made a simple algorithm to encrypt a string...say just add 5 each char...say i did not know how the string was encrypted, and i did not have the source...how would i go about finding out what is done to the initial string that is unputed? i know it has something to do with watching how memory changes...can someone give a demostration?

---

### Post by popch on 2008-01-29
This part I could understand:
> **rekahsoft said:**
> Hi all, i have been programming some lately and i came across a question...say i made a simple algorithm to encrypt a string...say just add 5 each char...say i did not know how the string was encrypted, and i did not have the source...how would i go about finding out what is done to the initial string that is

while this one I did not:

> **rekahsoft said:**
> unputed? i know it has something to do with watching how memory changes...can someone give a demostration?

As far as I understood your question, there are two answers:
[LIST=1]
[*]you can add or subtract each number in {1..255} in turn from/to each character in the 'encrypted' text.
[*]you can tally the number of times each character occurs in the 'encrypted' text. For each language there is a quite unambiguous pattern of frequencies with which each character usually is encountered within a typical piece of text.[/LIST]

---

### Post by aks44 on 2008-01-29
Your question is very close to the reverse engineering topic, which BTW is illegal in most cases (if you can't get the source, the software is very likely to be protected by a license that forbids RE).

RE is a forbidden black art. Many people know it, but don't expect anyone to answer this kind of question. If you wanna go that way you'll have to learn by yourself.


Now *if* your problem is as simple as you describe, a simple probabilistic analysis will do the trick, without having to look at the algorithm (only the output data is needed). Each language has its own set of "most used letters" so this is quite easy to make sense of such basic string obfuscation (I wouldn't call that encryption).

---

### Post by rekahsoft on 2008-01-29
> **aks44 said:**
> Your question is very close to the reverse engineering topic, which BTW is illegal in most cases (if you can't get the source, the software is very likely to be protected by a license that forbids RE).

RE is a forbidden black art. Many people know it, but don't expect anyone to answer this kind of question. If you wanna go that way you'll have to learn by yourself.


Now *if* your problem is as simple as you describe, a simple probabilistic analysis will do the trick, without having to look at the algorithm (only the output data is needed). Each language has its own set of "most used letters" so this is quite easy to make sense of such basic string obfuscation (I wouldn't call that encryption).

lol i know it is loose..it was meant to be..and i know that just adding 5 to the value of the char (obviously wrapping at 255 back to 1)...i wrote the source..i am just wondering how i would go about figuring out (without the source) what was happening? is this possible? or is it agaist forum policy?

---

### Post by ZylGadis on 2008-01-29
> **aks44 said:**
> Your question is very close to the reverse engineering topic, which BTW is illegal in most cases (if you can't get the source, the software is very likely to be protected by a license that forbids RE).

RE is a forbidden black art. Many people know it, but don't expect anyone to answer this kind of question. If you wanna go that way you'll have to learn by yourself.

Decryption is definitely not a black art. What someone does with it afterward is not our concern. The same goes for reverse engineering. If I go with your reasoning, I should be forbidden to teach programming at a university because one of those I teach might turn out to be the next Kevin Mitnik.

OP, your problem is very easy, provided the input makes sense, and the matching is 1:1. If it is a random string obfuscated with a random key, it is impossible to "decrypt" it. If the input makes sense (i.e., it is a sentence in some language, or anything else you might know about it), however, you can apply statistical analysis to it. The longer the obfuscated text, the better your analysis will be. Typically you will try to find repeating patterns in the obfuscated string and match them to words/phrases from the language, until it starts making sense.

---

### Post by shawnhcorey on 2008-01-29
> **aks44 said:**
> Your question is very close to the reverse engineering topic, which BTW is illegal in most cases (if you can't get the source, the software is very likely to be protected by a license that forbids RE).

RE is a forbidden black art. Many people know it, but don't expect anyone to answer this kind of question. If you wanna go that way you'll have to learn by yourself.

Sorry, reverse engineering is neither forbidden nor illegal.  Nor does any license forbid it.  They state that doing so is a violation of the license; meaning you may be sued in civil court.  In many countries, some or all of the so-called licensing agreements are not enforcible.  Check with your lawyer.

Nor does patents prevent reverse engineering.  Patent law makes it illegal for you to incorporate a patent in a product, even if you give the product away for free.  What it specifically does not prevent is you reverse engineering it, thinking up improvements, and applying for your own patent on those improvements.  That was why patent law was created in the first place!  To encourage innovation!

---

### Post by LaRoza on 2008-01-29
> **shawnhcorey said:**
> Sorry, reverse engineering is neither forbidden nor illegal.  Nor does any license forbid it.  They state that doing so is a violation of the license; meaning you may be sued in civil court.  In many countries, some or all of the so-called licensing agreements are not enforcible.  Check with your lawyer.


It could be incorporated into the criminal code

[Dmitry Sklyarov[]("http://en.wikipedia.org/wiki/Dmitry_Sklyarov")

He was not not a citizen of the country he was arrested in, and a professional.

Discussing reverse engineering of your own code is allowed.

Looks for patterns and use your head.

Everything has a pattern, finding it is the key.

---

### Post by Wybiral on 2008-01-29
Unless you're talking about reversing the source to find the algorithm, you might be interested in [cryptography]("http://en.wikipedia.org/wiki/Cryptography")

It really depends on how much you know about the data. If the data is random, then breaking it will be REALLY hard. But if you can rely on patterns in the data, then you can use that to your advantage. For instance, in your case, you can look at it as a [substitution cipher]("http://en.wikipedia.org/wiki/Substitution_cipher"), and since English favors certain letters (such as E, T, S), you can use that to help fill in the gaps (ever try to solve one of those cryptograms in the newspaper?) If you know the data is English, you can find the most frequent letter and assume that it's an E (which is the most frequent letter in the English alphabet), and so on (trying different combinations in order of statistical frequency).

Knowing what type of data that's encrypted is very important. For instance, if you know that it's a LISP program's source code that's been encrypted, you can try substituting the more frequent symbols with "(" or ")" (since they have a high frequency distribution in LISP code).

---

### Post by shawnhcorey on 2008-01-29
> **LaRoza said:**
> It could be incorporated into the criminal code

[Dmitry Sklyarov]("http://en.wikipedia.org/wiki/Dmitry_Sklyarov")

He was not not a citizen of the country he was arrested in, and a professional.

Discussing reverse engineering of your own code is allowed.

He was arrested in the US, where the judges are elected, not appointed.  In other words, corporations can influence the decisions of judges by contributing to their campaigns.  You will also note that the charges were dropped.

Even in the US, there are laws that state that no government employee or elected representative can use their power for their own ends.  This is called influence peddling.

BTW, the only reason you need to reverse engineer your own code was because you were too lazy to document it properly when you wrote it.

---

### Post by LaRoza on 2008-01-29
> **shawnhcorey said:**
> He was arrested in the US, where the judges are elected, not appointed.  In other words, corporations can influence the decisions of judges by contributing to their campaigns.  You will also note that the charges were dropped.

Even in the US, there are laws that state that no government employee or elected representative can use their power for their own ends.  This is called influence peddling.

BTW, the only reason you need to reverse engineer your own code was because you were too lazy to document it properly when you wrote it.

No, I recently accidently deleted my source code for the System Restore program I am writing, and had to use the old byte code file that I dug out of the trash to get my code back.

Yes, I found it easier to reverse engineer byte code than to rewrite it. I got it back after a brief lesson on the byte code used, and a bit of luck.

(Still, the law was criminal in nature, not civil, and could be used again. I am waiting for them to try to arresst every dvdcss user...And not all judges are elected, some are appointed, it varies by jurisdiction)

---

### Post by CptPicard on 2008-01-29
Speaking of patterns, this reminds me of the seminar work I wrote in school over the Enigma cipher and how to break it. I've always been a bit of a history buff so "how to break Enigma with at most Colossus at your disposal" was a nice topic :)

It's a really fascinating example of a fairly strong cipher (for the time) that was totally screwed up by incompetent users. The Germans systematically reused codebooks without understanding that this gave a huge edge to the guys at Bletchley Park. 

Also, they could be goaded into sending predictable messages -- for example, the Royal Navy would set up mines somewhere and just wait for the U-boats to send/receive a message with the string *MINEN* in it. The U-boat weather report was also in a known format. You just took your own weather data, used that as plaintext and there you had the day's codes.

And of course, there was the unfortunate "Heil Hitler" as part of many messages...

---

### Post by Geekkit on 2008-01-29
> **aks44 said:**
> Your question is very close to the reverse engineering topic, which BTW is illegal in most cases (if you can't get the source, the software is very likely to be protected by a license that forbids RE).

RE is a forbidden black art. Many people know it, but don't expect anyone to answer this kind of question. If you wanna go that way you'll have to learn by yourself.

If this were true then AMD would never have survived as a business.

---

### Post by LaRoza on 2008-01-29
> **CptPicard said:**
> 
It's a really fascinating example of a fairly strong cipher (for the time) that was totally screwed up by incompetent users. The Germans systematically reused codebooks without understanding that this gave a huge edge to the guys at Bletchley Park. 

Also, they could be goaded into sending predictable messages -- for example, the Royal Navy would set up mines somewhere and just wait for the U-boats to send/receive a message with the string *MINEN* in it. The U-boat weather report was also in a known format. You just took your own weather data, used that as plaintext and there you had the day's codes.



Yes, they also used messages sent twice by accident and relied on the failure to use random keys by the operators.

---

### Post by LaRoza on 2008-01-29
> **Geekkit said:**
> If this were true then AMD would never have survived as a business.

Nor Compaq (and all IBM compatible computers after that)

However, they used a method that was legal.

(Have an independent group of people examine the product, and they write a specification, a lawyer reads the specifications to make sure no patents are violated, and the company uses this specification to make their product)

---

### Post by Geekkit on 2008-01-29
> **LaRoza said:**
> (Have an independent group of people examine the product, and they write a specification, a lawyer reads the specifications to make sure no patents are violated, and the company uses this specification to make their product)

And add a sprinkling of several millions dollars of venture capital and you have yourself a new hardware company. :)

Edit: I believe called clean room reverse engineering.

---

### Post by LaRoza on 2008-01-29
> **Geekkit said:**
> And add a sprinkling of several millions dollars of venture capital and you have yourself a new hardware company. :)

Without Compaq, we wouldn't have PC's as we know it.

They opened their standard so it could be cloned.

Even Apple seems to have caught on recently. :)

---

### Post by pmasiar on 2008-01-29
> **ZylGadis said:**
> Decryption is definitely not a black art. What someone does with it afterward is not our concern. The same goes for reverse engineering. If I go with your reasoning, I should be forbidden to teach programming at a university because one of those I teach might turn out to be the next Kevin Mitnik.

It is not as simple, and depends on jurisdiction. USA is screwed, [DMCA](http://en.wikipedia.org/wiki/Dmca) makes illegal to break even most moronic protection. All depends on how your case will be prosecuted.

---

### Post by pmasiar on 2008-01-29
> **CptPicard said:**
> Enigma cipher and how to break it. ...

It's a really fascinating example of a fairly strong cipher (for the time) that was totally screwed up by incompetent users. The Germans systematically reused codebooks without understanding that this gave a huge edge to the guys at Bletchley Park. 


It is fascinating history. Polish codebreakers broke [http://en.wikipedia.org/wiki/Enigma_machine](http://en.wikipedia.org/wiki/Enigma_machine) code, and told the principle to British. After war started in Poland, they escaped to Britain, but was not allowed to help breaking the code.

British never disclosed that they can read the code, they run elaborate cover, inventing spies etc. After war, they managed to sell Enigma machines to friendly regimes like Iran, so they were able to read their exchanges for couple more years.

---

### Post by pmasiar on 2008-01-29
> **Geekkit said:**
> If this were true then AMD would never have survived as a business.

In beginning of '80, Intel went into agreement with [http://en.wikipedia.org/wiki/Amd](http://en.wikipedia.org/wiki/Amd) to make AMD long-term "second source" of intel CPUs. Intel needed that, because market was afraid Intel will not be able to make technology work, and which one from competing architectures will win. Intel gave full manufacturing blueprints to AMD and AMD manufactured 100% Intel clones for IBM.

So until 1994, making clones clones was legal for AMD. See wikipedia for details. Of course it was all before DMCA.

---

### Post by pmasiar on 2008-01-29
> **LaRoza said:**
> Without Compaq, we wouldn't have PC's as we know it.

They opened their standard so it could be cloned.

IBM released open standard, with license to make compatible cards, because they have no other option: they were late to the PC market. That was last time when IBM used outside hardware and operating system. They paid once more MSFT to develop GUI for OS/2 but MSFT took money, learned about GUIs a little, but later reneged on the agreement, they were more interested in own Windows.

OS for IBM PC is another fascinating story. At that time, DR CP/M was leading OS for 8080 based computers, and they had CP/M86 for 8086. Legend says that Gary Kildall just bought new plane, took week of vacation to fly over Santa Cruz mountains and did not want to meet with IBM. IBM was in hurry, so they made deal with MSFT, which bought QDOS (Quick and Dirty OS, a clone of CP/M for 8086) and resold it to IBM. And rest is history...

---

