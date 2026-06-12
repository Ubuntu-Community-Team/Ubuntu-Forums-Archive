---
title: "Which email client do you use?"
date: 2017-04-09
forum: New to Ubuntu
---

### Post by locam on 2017-04-09
I'm switching from OSX to Ubuntu. So far so good, I work mostly in the terminal and things are pretty similar.

However, I can't find a good email client.

Thunderbird has a lot of features but I find it slow and buggy. Geary is too simple but seems to work well.

I'm looking for a snappy email client that works with IMAP (Gmail, FastMail); supports GPG (signing and encryption/decryption); has a unified inbox (one inbox aggregating all inboxes in separate accounts).

Any recommendations?

---

### Post by Paddy Landau on 2017-04-09
I used to use Thunderbird, which I considered to be the best of its kind available (both Windows and Linux); this is a personal opinion, not an objective one. I didn't enjoy Evolution at all.

Thunderbird can get slow when you have very many emails (thousands including archived emails) or when the database grows large, so it's a good idea to regularly compact the database. The option from the menu is File > Compact Folders.

Several years ago, I started to use Google's Gmail browser-based interface instead. I quickly grew to love it. It's quite basic, yet fully functional, and fast. Accessible from smartphones and tablets, it has among the best spam filters available (probably because Google handles so many emails worldwide daily).

You have Gmail, so I recommend that you give it a try. Not much learning is needed — for example how to properly use its labels, and knowing which plugins ("Labs") suit you best. Gmail supports SMTP, POP3 and IMAP for other email providers, so it might work well for you.

It's quite easy to transfer your emails from Thunderbird to Gmail as long as you set it up right.

---

### Post by walts48 on 2017-04-09
Thunderbird for mail, feeds, newsgroups, calendaring and chat.

Though, Ubuntu is a little slow on keeping it updated.

---

### Post by RobGoss on 2017-04-09
I'm with** Paddy Landau**, I have been using Gmail for over 17-years and just love it. Gmail is so clean and simple to use you have to love it. The email service it self is pretty reliable I never had any issues what so ever. If you want to incorporate **Gmail** with let's say **Evolution,** email client it's not to hard getting things setup it took me a few minutes trying to configure it all once it was setup it also work well

I have Evolution email setup to see how other email clients work with Ubuntu and Linux, in general

---

### Post by howefield on 2017-04-09
Mutt will do what you want except for the unified inbox, if I understand your requirements correctly. I work around this by having gmail poll the other accounts (different providers) and then Mutt polls the gmail account. Might appeal given that you "*work mostly in the terminal*"

---

### Post by Paddy Landau on 2017-04-09
> **RobGoss said:**
> I have been using Gmail for over 17-years…
"Gmail was announced to the public by Google on 1 April 2004 … April Fool's Day" — [Wikipedia]("https://en.wikipedia.org/wiki/History_of_Gmail#Public_release")
You must have been working with its development from the start! :o

---

### Post by sevendogs on 2017-04-09
I am constantly switching email clients to find the "perfect one". Not a gmail user but Evolution works fine for me. I have used Sylpheed and Claws-Mail the longest, however they do not display html mail so you get raw text. Maybe that's not a bad thing...Claws-Mail has a ton of features and although I do not use any of the ones you describe, it's worth a look. Very light and fast. I do like Thunderbird but only use IMAP and it bugs me I have to have a "local folders" account I can't get rid of. Mildly OCD-ish, I know but it bugs me. I have tried nearly every email client known to man and it figures I have settled on the one with the heaviest GUI :rolleyes:

---

### Post by RobGoss on 2017-04-09
> **Paddy Landau said:**
> "Gmail was announced to the public by Google on 1 April 2004 … April Fool's Day" — [Wikipedia]("https://en.wikipedia.org/wiki/History_of_Gmail#Public_release")
You must have been working with its development from the start! :o

Hi Paddy Landau, yea it was some time ago it was my first email account and until today it's basically the only one I use

---

### Post by mastablasta on 2017-04-10
thunderbird is buggy? that's odd, since for some time now they are only (mostly) doing only bugfixes.

I use Thunderbird on Linux and Outlook 2013 on Windows.

since i mostly use gmail i would just use browser. the only hting that bothers me in gmail interface is that it is slow to load on my old PC and Quite often features of it would crash

---

### Post by zerubbabel on 2017-04-10
Claws does display incoming html-formatted emails with the Fancy plugin installed, but it does not compose html messages. I've used it for years and have tens of thousands of emails archived with no noticeable loss in performance.

---

### Post by locam on 2017-04-10
Good to know. I find it very slow, routinely using 100% CPU, sometimes getting confused about messages, showing them as blank with a 31/12/1969 sent date... Maybe I'll stick with it then if it's getting bug fixes. I thought the project wasn't maintained anymore but I'm glad to hear otherwise.

I tried mutt in the past and can't remember why I discontinued. Maybe because of HTML only emails? I'll give it another look.

> **mastablasta said:**
> thunderbird is buggy? that's odd, since for some time now they are only (mostly) doing only bugfixes.

I use Thunderbird on Linux and Outlook 2013 on Windows.

since i mostly use gmail i would just use browser. the only hting that bothers me in gmail interface is that it is slow to load on my old PC and Quite often features of it would crash

---

### Post by minecralex on 2017-04-10
I just use the integrated Gmail host in the browser.

---

### Post by howefield on 2017-04-11
> **locam said:**
> I tried mutt in the past and can't remember why I discontinued. Maybe because of HTML only emails? I'll give it another look.

You're correct, Mutt doesn't parse html by default but it can be set up to do so, I use w3m for the job. If that that doesn't do it then almost certainly the mail isn't worth reading ;)

---

### Post by mastablasta on 2017-04-11
> **locam said:**
> Good to know. I find it very slow, routinely using 100% CPU, sometimes getting confused about messages, showing them as blank with a 31/12/1969 sent date... Maybe I'll stick with it then if it's getting bug fixes. I thought the project wasn't maintained anymore but I'm glad to hear otherwise.



at the moment i am seeing this on Firefox, not on Thunderbird. but then again i don't use it as much.

Thunderbird developed a lot (what is not in official version is available in free add ons). so soem time ago they decided that rather than adding features, they owuld only do maintenance and bugfixes. ther eis only so much you can do in email client. 

at work Outlook was forced on me and i went with it since some 2003 version i believe. it was bad at first compared to TB but then later on it improved a lot. anyway i use 2013 now (soon to be replaced by 365). i could say they have something that is very usable now. however, it only Works on Windows. if you install MS Office to Linux then Outlook component will likely be the one that doesn't work and gives the suite some silver rating. on the other hand 365 Works in browser, so i is system agnostic. but then again not as fast as the loaded one and not so feature rich.

it really depends how many emails you have, what you do with them, what features are needed etc.

for example we are working a lot with USA via video conference calls and to be able to easilly schedule those, reserve rooms etc all from Outlook is of a big help to us.  

at home i do not need such features. not even a calendar anymore.

---

### Post by locam on 2017-04-11
mutt + w3m sound very promising, especially if it will let you render the email in a browser if all else fails.

I have several thousand emails in my archive, so that might be why TB is having a hard time. Still, I'd need a mail client that handles this well and TB doesn't seem to be it.

---

### Post by Paddy Landau on 2017-04-12
> **locam said:**
> I have several thousand emails in my archive, so that might be why TB is having a hard time. Still, I'd need a mail client that handles this well and TB doesn't seem to be it.
Thunderbird struggles with huge databases, unfortunately. As you want the terminal, you'll have to keep with mutt or w3m, otherwise I'd repeat my recommendation for Gmail, which easily handles huge numbers of emails.

---

### Post by kurt18947 on 2017-04-12
I've read where Mozilla is looking for a new home for Thunderbird. Some users would like to see The Document Foundation (LibreOffice) pick it up. Thunderbird uses the Gecko engine and Mozilla is working on a successor. Mozilla apparently isn't interested in fitting the new rendering engine into Thunderbird. Perhaps Mozilla feels that web mail is the future. Maybe so but not for me.

---

### Post by locam on 2017-04-12
Good point. Not all my accounts are hosted on gmail, and I'd rather not depend on google for my email client so I can move off them should I ever decide to do so.

> **Paddy Landau said:**
> Thunderbird struggles with huge databases, unfortunately. As you want the terminal, you'll have to keep with mutt or w3m, otherwise I'd repeat my recommendation for Gmail, which easily handles huge numbers of emails.

---

### Post by Paddy Landau on 2017-04-13
> **locam said:**
> … I'd rather not depend on google for my email client so I can move off them should I ever decide to do so.
The irony here is that I stay with Google partly because Google makes a point of making it easy to transfer all your data to somewhere else should you choose to leave :)

---

### Post by locam on 2017-04-14
It's not too bad with a mail client, you can drag and drop your emails from one account to the other and it will copy them over. Works with any IMAP provider :)

> **Paddy Landau said:**
> The irony here is that I stay with Google partly because Google makes a point of making it easy to transfer all your data to somewhere else should you choose to leave :)

---

### Post by bcbuch on 2017-04-14
I use Thunderbird imapping to my gmail and zoho accounts. Tried evolution for a bit, but it had some issues syncing to google calendar which Thunderbird doesn't have. I have mine and my wife's calendars synced so we can both keep up with what we have going on, and make changes from all of our devices. Currently testing a Ubuntu Gnome 17.04 modified a bit on my daily driver do to Gnome's ability to integrate Google into the desktop. After I get a few more things worked out after replacing Nautilus with Nemo I may try Evolution again. I like the looks of Evolution as a productivity option over Thunderbird's browser look.

---

