---
title: "Missing window header bar in UStudio11.10"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Noobuntu79 on 2012-03-08
Hello everyone.

I appear to be suffering from the same problem as the OP in this thread - [http://ubuntuforums.org/showthread.php?t=1877276](http://ubuntuforums.org/showthread.php?t=1877276) - I have no window header bar and therefore no min/max/close buttons.  However I am not having the same success in trying to remedy...

I tried 'compiz --replace' in a terminal, terminal told me I didn't have compiz and to try 'sudo apt-get install compiz-core' I tried this, terminal told me it couldn't locate package...

Any thoughts?

Cheers,

Steve

---

### Post by EzioAuditore on 2012-03-08
Have you tried metacity --replace ?

---

### Post by Noobuntu79 on 2012-03-08
Thanks for the reply...

Once again I'm getting the same terminal behaviour....
'metacity not installed.  you can install it by typing sudo apt-get install metacity'
'sudo apt-get install metacity'
'unable to locate package metacity'

At first I thought it might be a connectivity issue, and then I realised that I'm posting on here without any issue and so therefore it can't be that lol

---

### Post by EzioAuditore on 2012-03-08
Are you able to do 'sudo apt-get update' (w/o the quotes) ?

---

### Post by Noobuntu79 on 2012-03-08
Everything is all splendid again.....many thanks :)

---

### Post by EzioAuditore on 2012-03-09
well that's good.
Would be nice if you could post how you solved that as it'd be beneficial for others in case they run into same problem. :)

---

### Post by Noobuntu79 on 2012-03-10
Yes of course - I ran sudo apt-get update as you suggested then after it finished updating I ran sudo apt-get install metacity and metacity --replace...  Worked like a charm this time, not sure why it didn't run the first time but this brought back the header and buttons.
 
Thanks again

---

### Post by EzioAuditore on 2012-03-11
> **Noobuntu79 said:**
> Yes of course - I ran sudo apt-get update as you suggested then after it finished updating I ran sudo apt-get install metacity and metacity --replace...  Worked like a charm this time, not sure why it didn't run the first time but this brought back the header and buttons.
 
Thanks again

Your welcome. Glad i could help.

---

### Post by proEndreeper on 2012-05-31
This was very helpful, and I think this is caused by wine being opened or something.

---

