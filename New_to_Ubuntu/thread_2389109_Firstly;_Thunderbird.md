---
title: "Firstly; Thunderbird"
date: 2018-04-11
forum: New to Ubuntu
---

### Post by desukane on 2018-04-11
I'm not a new user, just an old one severely out of date. I'm assuredly not liking Gmail; is there a better email service? One that is very secure. I've read that Thunderbird is slow and cumbersome; anything better? I'm considering dropping Gmail for something more and more secure. I'm not liking what Gmail and Facebook and others are doing with information, maybe this forum. It's all hackneyed accuses. Anything better?

---

### Post by #&amp;thj^% on 2018-04-11
I'm kind of liking Zoho Mail, but have not had it long about 4 months now.
They Claim:"Secure, fast, ad-free email for business. Free for up to 25 users. Plans start at $2 /month"
I'm using the free version and no compaints so far.
Here is a good list of providers:[https://www.technorms.com/14035/10-free-email-service-providers](https://www.technorms.com/14035/10-free-email-service-providers)
As far as thunderbird goes, I just use Seamonkey a close cousin to thunderbird: [https://www.seamonkey-project.org/](https://www.seamonkey-project.org/)
[B]EDIT Please Read TheFu's post below mine.
Very wise and respected user here in UF[/B]

---

### Post by TheFu on 2018-04-11
Warning - lots of opinions below....

Nothing will be as secure as running your own email server, but doing it is a non-trivial effort. Securing an email server is non-trivial. Maintaining an email server so that it doesn't get on spam blocklists is also something to consider.  I've been running my own email server over 25 yrs now.  In the beginning, it was fairly simple. SMTP is an easy protocol.  It is all the anti-spam stuff that has made email harder.

ProtonMail has been considered reputable email provider the last few years.  I only use it for testing and never with a thick client. That sort of access might require a paid account.  IDK.  

Free email providers that you've heard about have the same problems as gmail, IMHO.  They are providing a service for free, which means you and your data is the product being sold.

The best answer could depend on your location in the world.  For example, if you are in the USA, then specifically choosing a non-USA company,, with systems ex-USA might be important to you. Especially with the CLOUD Act (recent law) that mandates corporate data stored overseas by companies based in the USA be provided to the USgovt. Physical location doesn't matter.

And ... really ... no email is secure.  The protocol leaks metadata all over the place, so even if you only use gpg encrypted messages, the TO/FROM/SUBJECT and servers involved will all be known by any node between both clients.  Turns out that the actual words inside the encryption aren't really sufficient security.

If you want real secure messages between people who actually trust each other, something like RetroShare is where I'd start.

I use thunderbird.  Haven't found any alternatives that do what I need, like enterprise calendaring which can connect to a CalDAV server or 10.  On Android, I use K-9 Mail, but I don't consider any smartphone or tablet secure.

---

### Post by SlidingHorn on 2018-04-11
If you're looking for a provider, there are a couple out there that offer end-to-end encryption between users (you'd have to encrypt externally if you were sending to a user on another service) that I personally like:

- [ProtonMail]("https://protonmail.com")
- [TutaNota]("https://tutanota.com")

However, due to the nature of them having an end-to-end encryption on their platform, they don't allow for IMAP access through Thunderbird or other applications.

In terms of clients for other services, I usually suggest Thunderbird or Claws-Mail, as both have plugins available to allow GPG/PGP integration.

---

