---
title: "Mutt and multiple addresses"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by h8uthemost on 2011-09-15
Does anyone know of a _simple_ way to make Mutt show my multiple Gmail addresses? I emphasize simple because the only solutions I've found to do this is to install multiple scripts or other things. And surely there has to be an easier way. 

All I'm wanting to do is input my addresses into my .muttrc and be good to go. Which I have done that, but Mutt won't show all my addy's. So I'm putting something wrong into the config file.

Anyone use Mutt and multiple Gmail addys? Any help will be appreciated.

Thanks.

---

### Post by gmargo on 2011-09-15
I suspect you are looking for the "alternates" command, used to specify a list of email addresses by which you are known.  See /usr/share/doc/mutt/manual.txt.gz for more info.

Example from my .muttrc:
```

 alternates "gmargo@example1\.net|gmargo@fish\.example2\.net|gmargo@example3\.com"

```

---

### Post by h8uthemost on 2011-09-15
What exactly does that command do though? I put it in my .muttrc(changing to my emails), but see no change in Mutt. 

I'm trying to get two email boxes(well there's four but I'm trying to get just two working right now) to show in Mutt, and then be able to select whatever one I want to look in. Is that possible? Something similar to how Cone is. 

I have it showing two email addresses right now, but the messages from both appear all as one. I want to be able to choose between each other.

Anyways, I looked through the manual and found the Alternative Addresses section . And it just told me a code like the one you posted, but I'm still unclear of what it actually does.

Would a macros be something that I should be using? Something like binding the two emails to the 1 and 2 keys?

---

### Post by Seq on 2011-09-16
> **h8uthemost said:**
> What exactly does that command do though? I put it in my .muttrc(changing to my emails), but see no change in Mutt. 

Usually in message indexes, Mutt displays who a message was from. When it detects it was from you, it shows 'To' instead. This allows it to detect you as multiple addresses.

> **h8uthemost said:**
> I'm trying to get two email boxes(well there's four but I'm trying to get just two working right now) to show in Mutt, and then be able to select whatever one I want to look in. Is that possible? Something similar to how Cone is. 

I have it showing two email addresses right now, but the messages from both appear all as one. I want to be able to choose between each other.

Anyways, I looked through the manual and found the Alternative Addresses section . And it just told me a code like the one you posted, but I'm still unclear of what it actually does.

Would a macros be something that I should be using? Something like binding the two emails to the 1 and 2 keys?

I'm assuming you're using IMAP. I have not used Mutt's imap support before. 

However, the first link in google for [mutt switch between accounts]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=mutt+switch+between+accounts") actually seems like a [useful tutorial to switch between mutt accounts]("http://wiki.mutt.org/?action=browse&diff=1&id=UserStory/GmailMultiIMAP"). There are a few items specific to gmail (labels, trash, and record) but can be ignored if you're not configuring gmail addresses.

Personally, I use offlineimap, and would have both accounts download to their own directories, populate a .mailboxes file with the full list, and use the folder-hook stuff from above to set my 'from', smtp, etc.

---

### Post by h8uthemost on 2011-09-16
Thanks seq. I've actually came across that tutorial before and have my accounts set up like it shows. But...it doesn't show away to switch between the two accounts, unless I'm being blind. It has two macros configs on there, but that's just to mark your emails. I'm trying to figure out how to set a macros to switch between two accounts.

Eh...maybe Mutt is more work than it's worth. I've tried a few other console-based clients and none really measured up to a gui one. And I was just wanting to see if Mutt was any better. But so far I can't even get it to do the one thing that other console-based clients did right, and that's show to all my emails in a neat tree view.

Ah well, guess I'll stick with the gui ones.

Actually, I'll post my config incase someone happens across this thread that has figured out how to get Mutt set up the way I want it and will know what I need to put in my .muttrc:

```
# Account 1
account-hook imaps://myemail@imap.gmail.com 'set imap_user=myemail@gmail.com imap_pass="mypass"'
folder-hook 'imaps://myemail@imap.gmail.com' 'set folder=imaps://myemail@imap.gmail.com/'

# Account 2
account-hook imaps://myemail@imap.gmail.com 'set imap_user=myemail@.com imap_pass="mypass"'
folder-hook 'imaps://myemail@imap.gmail.com' 'set folder=imaps://myemail@imap.gmail.com'

set folder="imaps://myemail@imap.gmail.com"
set spoolfile="+INBOX"

set folder="imaps://myemail@imap.gmail.com"
set spoolfile="+INBOX"
```

---

### Post by h8uthemost on 2011-09-16
Actually I did figure out how to finally switch between the inboxes with that above code. With the above when Mutt starts nothing is on the screen. But if I hit c then Shift+? and Enter I'll go to my home directory. Then...if I hit the Tab button, my two email accounts pop up. They appear like this:

imaps://myemail@imap.gmail.com
imaps://myemail@imap.gmail.com

Then I just choose one to go to the inbox. Which is great, but two things I don't like about it. There's entirely too many key strokes to get to the screen that lists those two emails, and there's isn't a number with however many new unread emails.

Anyone know of a way that I can fix those two things?

---

### Post by Seq on 2011-09-16
> **h8uthemost said:**
> Actually I did figure out how to finally switch between the inboxes with that above code. With the above when Mutt starts nothing is on the screen. But if I hit c then Shift+? and Enter I'll go to my home directory. Then...if I hit the Tab button, my two email accounts pop up. They appear like this:

imaps://myemail@imap.gmail.com
imaps://myemail@imap.gmail.com

Then I just choose one to go to the inbox. Which is great, but two things I don't like about it. There's entirely too many key strokes to get to the screen that lists those two emails, 

I use 'y' to switch between my mailboxes, but I can't recall if that was a bind or default. It gives me a nice list from whatever was in my .mailboxes file.

> **h8uthemost said:**
> and there's isn't a number with however many new unread emails.

Anyone know of a way that I can fix those two things?

I didn't even bother with mutt's IMAP support, and went the offlineimap route. I can post my configs if you would like.

The advantage of the offlineimap approach:

[LIST]
[*]You have a maildir store that is there even if mutt isn't running (or if you want to try out another mail client).
[*]It is available offline
[*]It is available instantly. You never need to wait for a message or attachment to download as you don't even see the message appear until it is already on your disk.
[*]Mutt's mailboxes list tells you what boxes have new mail (note: not unread, just new), but not how many.
[/LIST]

Downsides are the disk footprint of having all messages locally (which you would have with a client that caches anyway), and "yet-another-thing". But I felt the benefits worth it.

A fellow by the name of Brad started a notification indicator for maildirs. He and I have both updated it to work in Ubuntu's messaging menu, have clean popups, etc. This way you can have offlineimap pull in mail every five minutes or so and get a graphical notice about waiting messages, even if mutt isn't running.

[https://launchpad.net/~chrisirwin/+archive/maildir-indicator](https://launchpad.net/~chrisirwin/+archive/maildir-indicator)

---

