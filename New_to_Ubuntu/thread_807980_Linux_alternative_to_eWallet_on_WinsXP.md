---
title: "Linux alternative to eWallet on WinsXP?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Donalb on 2008-05-26
Hi all,
 Sorry if I'm asking this in the wrong forum (none of the others seemed right so....).
 Anyway, my biggest loss from XP is eWallet.
 I've tried
1; KeePass
2: Revelation
3: kWallet
4: pwManager

Revelation is the closest but still very restricted, not enough categories and can't be personalised
.
I'd like one password protected encrypted application that I can keep all my personal sensitive data in. Revelation only has a few categories. 
I'd like one where I can keep, by category:
Bank account (real world & online)
Credit cards
Debit Cards
Store/loyalty cards
Insurance (personal, house, car, medical, mortgage, etc) 
Personal Identity stuff (Social Security no, password,driving licence, swim club etc)
Product details, (serial numbers, descriptions, notes & photos of items)
Passwords (URLS, phone numbers, email accounts. notes etc)

Now that I've written all this down, I guess I've convinced myself to do  a spreadsheet, but I'd like an app. 
 Any thoughts?

Donal
ps Yes, I've emailed a list of suggestions to Revelations author.

---

### Post by quelx on 2008-05-26
I just fit my needs into revelation, it's not strict about the fields, so if needed an account number goes in the email field, a phone number in the notes field, I know what I'm looking at when I open the record, and just having it all wrapped up is what's important.  Try and be a little flexible and you may find it does nearly what you need with the exception of the labels not matching.  It does also give the options of folders which you can personalize and categorize types of accounts that way (though again the individual records may not make sense to someone else, the probably will make perfect sense to you)

EDIT: I just looked at the source and you can easuly customize the fields by editing **revelation-0.4.11/src/lib/entry.py** by changing the strings of the **self.name** variables i.e.

```
self.name		= _('Card number')
```

and rebuilding the app

---

### Post by Donalb on 2008-05-26
Cool answer. I had added the detail anyway, but it was too cluttered. I like the ability to edit the string, so I'll have a look at that.
Cheers!

---

### Post by Donalb on 2008-05-27
Or at least, I liked the idea until I thought about it and realised I have no idea how to do that...! I had a look and couldn't even find that file to edit.

Regards
Donal

---

