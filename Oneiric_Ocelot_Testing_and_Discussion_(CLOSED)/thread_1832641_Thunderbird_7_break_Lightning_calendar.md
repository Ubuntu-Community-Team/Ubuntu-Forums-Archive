---
title: "Thunderbird 7 break Lightning calendar"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pressureman on 2011-08-25
For any of you who depend on the Lightning calendar extension for Thunderbird, be warned that the Thunderbird 7 package that was recently uploaded to the repos is not compatible with Lightning 1.0b5.

Bug report is here [https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/833508](https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/833508)

So far I haven't been able to find a historical nightly release of Lightning that actually works, and the latest nightly releases require an even later release of Thunderbird, version 9.0a (note to Thunderbird packager: that is not a hint to upload version 9).

---

### Post by pressureman on 2011-08-25
Ok, after hacking the install.rdf of Lightning 1.0b5 so that it would install in Thunderbird 7, it still appears buggy, which leads me to believe that the bugs are with Thunderbird 7, not Lightning itself. As an example, the timezone drop-down list in the Lightning preferences is empty, as is the "start day of week".

Contrary to the naming of the Thunderbird 7.0 package, it is not version 7.0 beta 1. It is build1 *candidate* of 7.0b1... in other words, still an alpha. In my experience, it's historically been a bad idea to run an alpha of Thunderbird. Even a beta is like playing Russian roulette with your mailbox.

So for now, I have reverted to Thunderbird 6.0, and have apt-pinned it, before we get Thunderbird 8.0 or 9.0 uploaded to the repos. I may do the same with Firefox yet, as I've already found some strange incompatibilities in that too.

---

### Post by SevenMachines on 2011-08-25
You might want to try 'Add-on Compatibility Reporter' for thunderbird, theres a similar one for firefox too, when testing. It allows you to enable your addons for incompatible versions of thunderbird/firefox. They, of course, might not work, but often its fine.

[EDIT] Sorry, I was thinking of an answer to a completely different question! Ignore me :)

---

### Post by chrisccoulson on 2011-08-25
No, editing the install.rdf or installing the addon compatibility reporter is not ever going to make Lightning work. It has a binary component which needs rebuilding against the latest Thunderbird as a minimum.

Reporting bugs to say that Lightning isn't working straight after a Thunderbird upload is generally unnecessary. I'm already well aware that it (and enigmail) won't work until I've rebuilt them, and it's already part of my standard checklist with a Thunderbird upload. I don't really need reminding ;)

---

### Post by pressureman on 2011-08-25
I didn't mean this as a reminder. It was meant as a warning to anybody who doesn't want to lose calendar functionality, to wait a bit until the Lightning package is updated.

If you can update Lightning to work with Thunderbird 7, that would be impressive, since I tried numerous nightly builds from ftp.mozilla.org, which were (according to the install.rdf) compatible as far as Thunderbird 9.0a, and they all had problems.

And hacking the install.rdf is what got me through several incompatibility problems in the Thunderbird 3.0/3.1 series, when x64 builds of Lightning were very infrequent.

---

### Post by tareko on 2011-09-06
Actually, even the nightly build doesn't work.

Here is [the nightly build]("http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/nightly/"). Here is [discussion of it]("http://forums.mozillazine.org/viewtopic.php?f=46&t=2247929"). Here are two [related]("https://bugzilla.mozilla.org/show_bug.cgi?id=680099") [bugs]("https://bugzilla.mozilla.org/show_bug.cgi?id=401779").

tarek : )

---

### Post by tareko on 2011-09-06
To further clarify, it appears the Ubuntu package fixes this problem. See [Bug #833508]("https://bugs.launchpad.net/ubuntu/+source/lightning-extension/+bug/833508").

tarek : )

---

### Post by JonM33 on 2011-09-06
I sort of gave up on Thunderbird after Mozilla went all crazy release cycle. Pity because I really liked it and the Lightning add-on.

---

### Post by pressureman on 2011-09-06
Yeah, the current packages in Oneiric seem to be working ok. We seem to have hit a stable milestone. Hope it lasts...

---

### Post by BrokenKingpin on 2011-09-06
It seems every time I go to use Lightning with Thunderbird the versions are incompatible... it is quite frustrating. Why can't they update the two products at the same time?!?

---

### Post by pressureman on 2011-09-06
> **BrokenKingpin said:**
> It seems every time I go to use Lightning with Thunderbird the versions are incompatible... it is quite frustrating. Why can't they update the two products at the same time?!?

Because Lightning seems to be in a perpetual beta.... I remember work starting on it sometime back around 2004, and they're still only at 1.0 beta5. I think that even beats some of Google's beta phases.

---

### Post by dmoconnell on 2011-09-07
> **BrokenKingpin said:**
> It seems every time I go to use Lightning with Thunderbird the versions are incompatible... it is quite frustrating.[COLOR=Red]* Why can't they update the two products at the same time?!?*[/COLOR]

That would be the smart thing to do, and why would they do that :D It seems like everyone (save for Microsoft) is doing the rapid release cycle thing. which is dam annoying for this very reason.

---

### Post by cariboo on 2011-09-07
I guess you didn't read all of post [#4]("http://ubuntuforums.org/showpost.php?p=11185229&postcount=4"), chris is going to rebuild the binaries, just give him some time. Keep in mind that the devs are in bug fixing mode, so everything should be reasonably stable by release time.

---

