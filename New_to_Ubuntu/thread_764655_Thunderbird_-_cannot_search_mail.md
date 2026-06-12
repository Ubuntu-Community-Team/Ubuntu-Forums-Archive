---
title: "Thunderbird - cannot search mail"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by MaximB on 2008-04-24
I have a Gmail account working with Thunderbird.
The problem is that I cannot search "words" in my emails, I am able to do so when I login to the "regular" "browser" Gmail, but not in Thunderbird.

---

### Post by munkyeetr on 2008-04-24
If I understand you correctly, you want to search for some text in the body of an email?

1) Open Thunderbird
2) **Edit** -> **Find** -> **Search Messages**
2a) or you can *right-click* on any of your email folders and choose **Search...** (*right-click* **Local Folders** to search them all)
3) In the Search Messages dialog, you want to change the default (Subject contains _) to Body contains _ and type in the search term you are looking for.

Thunderbird should then find any email you have that contains that text.

---

### Post by MaximB on 2008-04-24
Thanks
I just never changed to "body contains" ... never noticed that.

Now the problem is solved, thanks again.

---

### Post by brownknight on 2008-04-24
> **munkyeetr said:**
> If I understand you correctly, you want to search for some text in the body of an email?

1) Open Thunderbird
2) **Edit** -> **Find** -> **Search Messages**
2a) or you can *right-click* on any of your email folders and choose **Search...** (*right-click* **Local Folders** to search them all)
3) In the Search Messages dialog, you want to change the default (Subject contains _) to Body contains _ and type in the search term you are looking for.

Thunderbird should then find any email you have that contains that text.

The fastest way is to click the dropdown arrow on the seach box at the upper right corner (inbox view) and change it to "Entire Message". T

---

### Post by affinityvision on 2009-10-13
> **brownknight said:**
> The fastest way is to click the dropdown arrow on the seach box at the upper right corner (inbox view) and change it to "Entire Message". T
Okay, well this method works okay, but the "proper" search method fails miserably, there are loads of results in google about this; only one of those results got me here!

The search interface looks very good, pity it doesn't work!

---

### Post by affinityvision on 2009-10-13
I did a clean of dovecot files for my IMAP folder on the server and then got TB to download all the messages again whilst dovecot rebuilt it's files.

Now the search seems to be working.  Not sure where the fault is, but if TB relies on the IMAP server for searching, then that still sucks; if it doesn't, then TB needs a way to rebuild all it's own indexes without re-downloading all the messages again.

---

