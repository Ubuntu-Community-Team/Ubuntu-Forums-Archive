---
title: "Loop through mail addresses in an evolution folder"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-09-12
Hi!

Question: I need to reply to all e-mails that I filtered in a separate directory in Evolution e-mail client.

How can I reply to all senders of all emails in this folder?
I see no default function, maybe there is, or else how can I loop through all mails in a evolution email folder?

---

### Post by WitchCraft on 2008-09-13
O.K., so far I did this:

cd ~/.evolution/mail/local
grep "From: " ./filteredmails | sed '/X-MailScanner-From: /d;s/>//' | sed -re 's/.+<//' | sed 's/From: //' |  sed '$!N; /^\(.*\)\n\1$/!P; D' | sed '/no-reply@students/d;s/$/;/' | sed ':a;N;$!ba;s/\n//g'

Which gives me a list of all e-mail addresses in this folder.
Unfortunately, if I moved some mails out of this folder, the addresses keep appearing when using grep / sed on this file for the directory.

Why? How can I find out which have been moved out, to drop them from the sed list?

---

### Post by WitchCraft on 2008-09-17
bump.

---

### Post by WitchCraft on 2008-10-06
bump.

---

