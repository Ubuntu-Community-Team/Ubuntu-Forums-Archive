---
title: "Questions about GPG"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by flurospar on 2012-04-03
I have been looking for solutions to sign and encrypt my mail, and came across GPG. Hence I installed Kleopatra and I was able to generate a RSA 4096-bit keys using [FONT=Courier New]gpg --gen-key[/FONT]. I set an expiration date of 2 years.

However, I face a few problems now:

1. Where do I store the revocation key or private key?

I am not thinking of storing it in physical media, since there are risks of losing the keys due to a earthquakes, volcanoes, or fires, or even someone stealing it. This just leaves me with the option of putting it on some cloud service, but then it becomes easy for everyone to snoop on my keys (Big Brother, the cloud service's employees, or hackers).

2. Since the date of expiration is two years from now, what do I do after 2 years?

Generate a new key? Make another key?

3. What if I happen to lose the revocation key or the private key?


Please help me out. This person lives in a country that passed email snooping laws without putting it for public debate, and I have no option but to encrypt and sign all my mail.

Many thanks in advance.

---

### Post by mastablasta on 2012-04-03
> **flurospar said:**
> I have been looking for solutions to sign and encrypt my mail, and came across GPG. Hence I installed Kleopatra and I was able to generate a RSA 4096-bit keys using [FONT=Courier New]gpg --gen-key[/FONT]. I set an expiration date of 2 years.
 
However, I face a few problems now:
 
1. Where do I store the revocation key or private key?
 
I am not thinking of storing it in physical media, since there are risks of losing the keys due to a earthquakes, volcanoes, or fires, or even someone stealing it. This just leaves me with the option of putting it on some cloud service, but then it becomes easy for everyone to snoop on my keys (Big Brother, the cloud service's employees, or hackers).
 
spider oak is a bit slow but encrypted cloud service. ;-)
 > 
2. Since the date of expiration is two years from now, what do I do after 2 years?
 
Generate a new key? Make another key?

yes i believe a new one is then generated 
 
> 
3. What if I happen to lose the revocation key or the private key?

what do you mean? you are locked out.
 
> 
Please help me out. This person lives in a country that passed email snooping laws without putting it for public debate, and I have no option but to encrypt and sign all my mail.
 
 
UK?
 
Sticking it to the man? :-)

---

### Post by flurospar on 2012-04-03
> **mastablasta said:**
> UK?

They are yet to pass it in UK, the country in question is [this]("http://news.oneindia.in/2012/02/22/yahoo-gmail-asked-to-route-mails-through-ind-servers.html").

Anyway, I have another question. Now that I have my keys:

1. How will other people encrypt mail for me to read?

2. How will others confirm my signature?

---

