---
title: "Thunderbird problem - fetches mail, but won't send mail for 1 out of 3 accounts"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by blackbird34 on 2012-12-19
Hi everyone

For a few weeks now Thunderbird has been refusing to send email via my Gmail account. I currently have one university email account and one Yahoo account that both send and receive mail perfectly, but with my (main) Gmail account I can't send anything...
So I thought it must be a network problem. The problem is that I would prefer not just deleting and re-adding the GMail account as I have been starring and tagging and generally searching around 2 years' worth of email I have stored from it.
Could anyone guide me through resetting the server settings to default ports, and generally resetting the smtp so that Thunderbird can send mail properly again? Like give screenshots of a settings pane on a working setup or explain me through it?

Thanks!

PS I'm on Thunderbird 17 now but this problem has been going for a couple of versions now...


EDIT: been looking around, found [this thread]("http://ubuntuforums.org/showthread.php?t=1642398&highlight=email+connection+problems").  Turns out that when I went to Thunderbird Menu > Preferences > Account Settings > Outgoing Server (SMTP) and reset smtp.googlemail.com to smtp.gmail.com and SSL/TLS to STARTTLS, it worked and sent a test mail (albeit slowly).
Any idea why it's so slow? And also, what is the difference between STARTTLS and SSL/TLS? Is it less secure?

---

