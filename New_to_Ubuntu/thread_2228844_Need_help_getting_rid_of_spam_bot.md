---
title: "Need help getting rid of spam bot"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by rjmiller on 2014-06-09
I think my computer has recently been infected with a spam bot: I've been seeing posts in my spam file offering cut rate medications but the e-mail address is mine. I was uncertain how to get rid of it so I tried wiping the disc and reinstalling the OS. This worked for a while but the spam posts came back. I wiped the drive and reinstalled the OS again then upgraded to 13.10 but the spam posts have returned. Obviously I'm not doing something right; can anyone tell me how to get rid of the spam posts that have my address?

---

### Post by lisati on 2014-06-09
There's a good chance that it's not your fault and that there's no spambot on your machine. I regularly receive emails claiming to be sent from my email address but in reality were sent by spammers using someone else's machine who tried to divert attention from their real identity.

---

### Post by Vladlenin5000 on 2014-06-09
> **lisati said:**
> There's a good chance that it's not your fault and that there's no spambot on your machine. I regularly receive emails claiming to be sent from my email address but in reality were sent by spammers using someone else's machine who tried to divert attention from their real identity.

I agree 100%.

---

### Post by LastDino on 2014-06-09
You should consider stripping that mail address of everything, including contacts and all, if possible get a different one all  together. I've had this issue with one of my play addresses  2 years ago and  I reset the password using the backup mail address I had given while making the compromised one, then went with the stripping process. I'm assuming when you say ''mail address is yours'' you mean it is used to send those spam mails.

---

### Post by Vladlenin5000 on 2014-06-09
> **LastDino said:**
> (...) it is used to send those spam mails.
... or just spoofed. It can be any virus or similar in any (Windows) machine that has that email address in any of its address books. It doesn't need access to the real email account to send a spoofed one. Actually, that rarely happens.

---

### Post by LastDino on 2014-06-09
> **Vladlenin5000 said:**
> ... or just spoofed. It can be any virus or similar in any (Windows) machine that has that email address in any of its address books. It doesn't need access to the real email account to send a spoofed one. Actually, that rarely happens.

That was not what it was in my case, my password was also changed and I was not able to access it at all.

---

### Post by Vladlenin5000 on 2014-06-09
Correct. You had you account hacked. Probably not the case here.

---

### Post by lisati on 2014-06-10
An analysis of the offending spam's "received" headers might provide some clues as to whether it's a compromised machine or account. In theory, they're meant to provide a chain of custody for the message, and although the method's not 100% foolproof, examining them can often provide useful information about a message's origin.

---

### Post by LastDino on 2014-06-10
> **Vladlenin5000 said:**
> Correct. You had you account hacked. Probably not the case here.
Yeah, lets hope its only spoofing :p
> **lisati said:**
> An analysis of the offending spam's "received" headers might provide some clues as to whether it's a compromised machine or account. In theory, they're meant to provide a chain of custody for the message, and although the method's not 100% foolproof, examining them can often provide useful information about a message's origin.

+1 to this.

---

### Post by Habitual on 2014-06-10
have 2 accounts. One you use for 'public' activity and will be 'published' on the 'net.
And one you **never** publish on the 'net. Ever.

---

### Post by SeijiSensei on 2014-06-10
Revealing the "source" of an email and examining the headers as lisati suggests should be your first approach to suspicious messages.  In Thunderbird you can use View > Message Source for this task.  Otherwise browse the web for pointers on viewing message headers in other email clients.

My email filters are generally suspicious of any outside messages with my address as the From since the only legitimate origin of such messages is my own mail server.

---

### Post by rjmiller on 2014-06-17
It would appear that the problem was not with my machine after all. My dental insurance site appears to have been a phishing site. Haven't seen a spam post with my address on it since I canceled the policy. They did an extremely good job of imitating a dental insurance site though; had me completely fooled for a long time.

---

