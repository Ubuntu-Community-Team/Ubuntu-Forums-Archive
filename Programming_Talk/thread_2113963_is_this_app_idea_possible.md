---
title: "is this app idea possible?"
date: 2013-02-08
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-02-08
Hi

I'm a University student. The varsity allocates about 3gigs of data per month for each student. My friends normally finish their data before the end of the month and hassle me for mine.

The thing is --- we each have passwords. The problem I have is that they want me to give them my password. You might think --- it's not a big deal since you can change it.

The problem however is that I cannot recycle my passwords as with the university password system -- you cannot change your password to a previous one for security reasons.

I've been meaning to build an app that can create a temp. password for my account.
Is this possible and how would one go about doing it?


Regards

---

### Post by r-senior on 2013-02-08
You should already have a password generator called apg that generates strong passwords:

```
$ apg

Please enter some random data (only first 16 are significant)
(eg. your old password):>
Felbyet2 (Felb-yet-TWO)
OthOmmuIpOs8 (Oth-Om-mu-Ip-Os-EIGHT)
ojDaffyab8 (oj-Daff-yab-EIGHT)
yedguAjnot8 (yed-gu-Aj-not-EIGHT)
ErfLckFam8 (Erf-Lck-Fam-EIGHT)
madBirb4 (mad-Birb-FOUR)

```

---

### Post by 3v3rgr33n on 2013-02-09
I don't want to just generate passwords.

I want to generate TEMPORARY passwords for a specific account!

---

### Post by SuperCamel on 2013-02-09
> **3v3rgr33n said:**
> I don't want to just generate passwords.

I want to generate TEMPORARY passwords for a specific account!

How will passwords be set? Will the password expire and change after a period of time? You say you can't recycle passwords so the password can't be reset to what it was originally, right?

---

### Post by 3v3rgr33n on 2013-02-09
> **SuperCamel said:**
> How will passwords be set? Will the password expire and change after a period of time? You say you can't recycle passwords so the password can't be reset to what it was originally, right?

1. Will the password expire and change after a period of time?

Yes!

2. You say you can't recycle passwords so the password can't be reset to what it was originally, right?
 
Yes It can't. Is it not possible to create an additional password --- then one would have the original password and a temp. one

3. How will passwords be set?

I don't know the specifics yet. That's what I'm tryng to figure out

4. Will the password expire and change after a period of time?

Yes.

---

### Post by trent.josephsen on 2013-02-09
That's a pretty reasonable set of requirements. Assuming you have a secure PC that can run this program on a schedule, or whenever you want it to run, it shouldn't be too difficult to work out the specifics.

I imagine your university has a Web page that you go to in a browser to change your password. Ideally, all you need to do is look at the source of that page and see where and how it sends the data, then create a program that does the same thing the browser does, but automatically. You'll almost certainly want to use HTTPS, which does make it a little more complicated, but not too much. You'll need some background in HTML and a basic understanding of HTTP(S), plus whatever language you decide to use.

Perl is my go-to language for... well, most things, really, so I'd probably look into doing it with the WWW::Mechanize module (which I've never used before, so I could be going down the wrong track entirely, but it's a place to start).

One thing you could do is use your "old" password as a base password, and add one or two characters to it to create a new, "unique" but still easily remembered password. Like if your current password is foobar2700, you could have your app generate passwords like foobar2700_aQ and foobar2700_3p. You could even have it text the new ending (aQ or 3p or whatever) to your phone whenever it changes, so you can always know the password without ever divulging the whole thing. (That last depends on your cell carrier.) That saves you the trouble of remembering a whole new password every time it gets "reset".

---

### Post by Cheesemill on 2013-02-09
Also bear in mind that it is probably against your University's network terms and conditions to let anyone else use your account.

If it is then I wouldn't even think about trying this out as the repercussions could be serious.

The first thing you should do is check with IT support at your University, they may suggest a simple solution such as actually transferring your balance to a different account.

As to your original question if you can't currently reuse an old password then there is no way of getting round this on your end. You would be able to write a program that changed your password to a temporary one for a certain amount of time before changing it again, but you still wouldn't be able to change your password back to one that had already been used.

---

### Post by KdotJ on 2013-02-09
Maybe your friends should just be more careful with their data? 

I agree with Cheesemill that this is probably against your University's rules and not worth the trouble.

---

### Post by Habitual on 2013-02-09
Easy answer, keep your password.

---

### Post by 3v3rgr33n on 2013-02-09
> **Cheesemill said:**
> Also bear in mind that it is probably against your University's network terms and conditions to let anyone else use your account.

If it is then I wouldn't even think about trying this out as the repercussions could be serious.

The first thing you should do is check with IT support at your University, they may suggest a simple solution such as actually transferring your balance to a different account.

As to your original question if you can't currently reuse an old password then there is no way of getting round this on your end. You would be able to write a program that changed your password to a temporary one for a certain amount of time before changing it again, but you still wouldn't be able to change your password back to one that had already been used.

I contacted the IT people regarding this matter. I'm waiting for their response.

Are you sayin' there's no way of creating an additional password to an account?
I don't want to write a script that will basically change my password and change it back after a period of time.

 I want to create an additional temporary password as that will not require me to know the temp. password to access my account during the period where the temp. password is valid.

---

### Post by KdotJ on 2013-02-09
So basically you want two passwords to for the same account. Just say to your IT guys "My friends want to use my data allowance, can you grant secondary access to my account please?" .. and see what they say. Maybe they will just sort that out easily for you.

Just out of interest, why can't they use your normal password that you use?

---

### Post by 3v3rgr33n on 2013-02-09
> **KdotJ said:**
> 
Just out of interest, why can't they use your normal password that you use?

'Coz they'll do all sorts of wicked stuff like check my results if they know my password.
The university has this central password system so you basically use one password for almost every service they have.

> **KdotJ said:**
> So basically you want two passwords to for the  same account. Just say to your IT guys "My friends want to use my data  allowance, can you grant secondary access to my account please?" .. and  see what they say. Maybe they will just sort that out easily for you.

Even if they say OK --- I don't want my friends to access my account whenever they feel like it.

---

### Post by KdotJ on 2013-02-09
Ok I'm a little confused....

If the one password is used to access all systems... then won't this "temporary" password also have the same privileges? Are you trying to get a password set up that is *only* used for the data?

---

### Post by 3v3rgr33n on 2013-02-09
It doesn't matter if it can access all the systems as long as it's temporary.
If it's only applicable for the data --- that would be better but that's not my primary concern.

I just want the password to be temporary --- that's the first concern.

---

### Post by KdotJ on 2013-02-09
Ah right. Maybe I'm just really dense, but I don't see the difference between if it's temporary or not... it only takes a second for them to look at your results and know them. 

Unfortunately I can't help you, but I think the best thing to do is wait until your IT guys get back to you as they may have a better solution. Good luck!

---

### Post by 3v3rgr33n on 2013-02-09
> **KdotJ said:**
> Ah right. Maybe I'm just really dense, but I don't see the difference between if it's temporary or not... it only takes a second for them to look at your results and know them.

I don't want them to check my results before me at the end of the year. They can't do that without knowing my password. They'll only need a temp. password during the year hence I don't have to worry.

---

### Post by KdotJ on 2013-02-09
So give them your current password... then just change it before results time

---

### Post by 3v3rgr33n on 2013-02-09
> **KdotJ said:**
> So give them your current password... then just change it before results time

LOL What would be the point of havin' a password then?

I don't want them to access my account when they feel like it. I think you're forgettin' that if I do that --- they can use my data whenever they want to.

---

### Post by KdotJ on 2013-02-09
> **3v3rgr33n said:**
> I don't want them to access my account when they feel like it. I think you're forgettin' that if I do that --- they can use my data whenever they want to.

Ok, I'm following you now. So you would like to be able to give them access for say 3 hours on demand?

Let the IT guys sort it out, or get new friends who you trust and who would respect the fact you're giving them your data allowance.


> **3v3rgr33n said:**
> LOL What would be the point of havin' a password then?

Exactly, maybe you need to think about that as well.  You have a password for your account as it's yours, it's private. 



I guess the only legitimate way to get around it, is just change the password every time they want to use your data, then change it to something new when they're done.

---

### Post by 3v3rgr33n on 2013-02-09
> **KdotJ said:**
> 
I guess the only legitimate way to get around it, is just change the password every time they want to use your data, then change it to something new when they're done.

Darn it!

I was really hoping to have to make an app. I'm juiced out of ideas --- I need a project to work on.

---

### Post by 3v3rgr33n on 2013-02-11
I will not be doin' the app. It is against the policies of the university.
Thanks to everyone who replied.

---

