---
title: "Thunderbird From problem"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-04-29
Currently running a freshly installed Ubuntu Hardy Heron 64. When i setup Thunderbird (version 2.0.0.12 (20080227) i first setup a gmail account. Then my work mail. I found out that all mail from me looks to be From the gmail account/address. Both accounts seemed to be from the same gmail account. My work mail is not gmail. And i would like it to not show as From the gmail account. How can i do this??

I deleted the gmail account. Making my work mail default. But it still shows the gmail adress as sender of all mail. Anyone know how i can make this right?

It also seems that when minimized it doesn't check for new mail. In addition i have to scroll down manually to find new mail if i get a confirmation that i have new mail. Which is strange.

And is it POP or IMAP who physically downloads all mail. Which one leaves it on the server and don't download it?

And I'm asking here since MozillaZine seems to be asleep. The forums here are so incredibly fast...

---

### Post by pedro_orange on 2008-04-29
You setup on the gmail website if you want it to remove emails after downloading to Thunderbird etc. It doesnt matter on the Protocol POP3/IMAP.

I guess what you need to do is within your Thunderbird settings; point your email client to send from your work email.

I think you actually tell Thunderbird how often to check for new emails. Perhaps it's only setup to check on start up?

---

### Post by peakshysteria on 2008-04-29
Hmmm, when i send mail it says it's connecting to smtp.gmail.com for some strange reason. How can i change this. Can't see no option for changing that??

---

### Post by monkeymoo on 2008-04-29
You go to Edit -> Account Settings -> Outgoing Server (SMTP) -> Add 
And then input the details of the outgoing server you want to use. 

Then you go to the account settings for the account you want to use this new outgoing server (just click the name not the "Server settings") and select the name of the newly added server in the outgoing server box.

---

