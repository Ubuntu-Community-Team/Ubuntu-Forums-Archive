---
title: "Thunderbird SMTP"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by brdokoky on 2008-06-13
I'm new to Ubuntu 8.04. I would like to ask you, that I've got a problem with sending emails with large attaching files   as is 14 MB.Downloading emails is working well , but when I send large email that after around 30 percents it stops ,but when I send just small text email is O.k.I tried to use an other client such as Evolution , in that is still the same problem. As well I tried to use wine following thunderbird and I got same problem. I found out that the problem maybe from second computer with windows xp connected to ethernet ,because if is shut down that I can send any emails - 20 MB without Problem.
Can you help me please ?

---

### Post by hyper_ch on 2008-06-13
Most email server refuse to take emails larger than 10 MB.... due to the encoding there can be up to 30% overhead of the original file. So you need to split it up into smaller ones.

---

### Post by acidsolution on 2008-06-13
which email server you are using?
 because most of the mail server restricts the attachment of 10 MB

---

### Post by brdokoky on 2008-06-13
But the problem is that I can send 20 MB email when is the second computer down and when is second computer running I can not send any attachments only at that time I can send just plain text.

---

### Post by brdokoky on 2008-06-13
Gmail

---

### Post by hyper_ch on 2008-06-13
and whom do you send it two? there's (mostly) two mail servers in the process. The sending one (has to accept the file size) and the receiving one (has also to accept the file size)

---

### Post by brdokoky on 2008-06-13
Yes , I know that. I send from gmail to gmail. As well I tried to use an other email server such as GMX. I tried to send from GMX to GMX and it's still the same problem. I've checked internet connection, that seems to be O.K. As well I tried to use uploading on rapidshare- it works well. Uploading via torrent works well.

---

### Post by brdokoky on 2008-06-15
I found out that the problem can be skype running on the second computer. When I tried to run the second computer without skype that I could send any mails. Now just to solve conflicting skype from windows xp to Ubuntu thunderbird.

---

### Post by brdokoky on 2008-06-20
You can set this as solved. I just disabled Qos in my router . Now all is working perfect. Thanks

---

