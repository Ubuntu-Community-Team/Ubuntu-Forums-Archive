---
title: "Grep madness: how to extract email addresses"
date: 2006-07-01
forum: Programming Talk
---

### Post by rosslaird on 2006-07-01
This is silly: I have spent so much time on this simple task, and have been so frustrated by it, that I have gone out and bought a book on how to program perl in order to find some way of figuring this out. But really, I shouldn't have to go so far (though I would like to know how to program in perl...).

Here's my "simple" challenge: I have a Sent folder of about 5000 emails on my hard drive. I have synced it with my remote imap folders using offlineimap. I want to extract the "to:" addresses in these sent messages so I can compare them with, and add them to, my newsletter subscriptions (I have an online newsletter). Then, I want to import the list into phplist and send a newsletter.

OK. I have found a script that fetches all the email addresses and places them in the little brother database for mutt. That's pretty good, but I don't want the addresses for all of my emails, just the sent ones.

I have tried navigating into the sent folder and using grep:

grep "^To: " * > emails.txt

But grep just seems to hang.

I have tried this with agrep also.

I am thinking of trying the following but I don't know exactly what it will do (I found it online):

perl -ne 'print $1 if m/^To: .*(\S+@\S+)/' < mboxfile

Maybe it's in my new book...
(I think what it does is search for lines with "To:" and print them to a file called mboxfile). I don't want to run it unless I know more about it.

But really, this should be a fairly simple exercise, no?

Feedback and suggestions welcome...

Ross

---

### Post by rosslaird on 2006-07-01
OK, small progress.

This,

grep -R 'To: ' *

when run in the main sent directory (i.e. above cur/tmp/new) causes grep to print out every line with "To" and "In-Reply-To:". It also shows the filename (of the message) which obviously I need to strip out, and I will need to exlcude the "In-Reply-To" lines as well. But progress is happening. Help still requested.

Ross

---

### Post by mlind on 2006-07-02
I thinkg your first idea looked okay
```

grep -h "^To:" * > test

```

If you have multiple To: matches on a one line, you might need sed or awk for the task.
With sed you can basicly do anything.

---

