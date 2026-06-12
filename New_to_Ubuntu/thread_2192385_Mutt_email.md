---
title: "Mutt email"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by Toni_Vines on 2013-12-07
I wonder if someone could help me with mutt email please? I've installed it and I can open it in the terminal. I've gone through the configuration process for gmail and all seems ok but when I run mutt I get the blue bar across the top of the terminal showing the letters for commands. I enter the email addy I'm sending to and hit 'enter' - all ok. Then I enter subject and hit enter and I loose the blue bar and just have a terminal window. I can write my message there but I've lost the commands so can't save or send the email! 
Any ideas please?
Thanking you,
Toni.

---

### Post by howefield on 2013-12-07
Screenshot it and post it here ?

What are you using for your editor in muttrc ?

---

### Post by Toni_Vines on 2013-12-07
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
<t-toni-OptiPlex-GX260-1000-8887-10369338571965904093" 0L, 0C 0,0-1         All
This is what I get after entering the subject. I've been using gedit on the muttrc file.
Thank you for your help,
All the best,
Toni.

---

### Post by howefield on 2013-12-07
Change your .muttrc file to use nano.

You'll get keyboard shortcuts along the bottom of the terminal, nice and easy :-)

---

### Post by Toni_Vines on 2013-12-07
I'm sorry, I don't understand you. I really am a newbie so sorry if I seem thick. I have no idea what I'm supposed to do and what is meant to happen! 
All the best,
Toni.

---

### Post by howefield on 2013-12-07
Go to your home folder and press Ctrl+H keys to show hidden files. Scroll down to the .muttrc file and open it, in the "Composing Mail" section change the "set editor" option to nano and save the file.

---

### Post by andrew.46 on 2013-12-07
Hmmmm..... there is a wiki page that goes through this process in great detail, but only for POP3 access not IMAP:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

Would this make life easier?

---

### Post by Toni_Vines on 2013-12-07
OK, I'm close to giving up now. I've done as advised and opened the .muttrc file and believe it or not it's already got the "set editor" option to "nano". What now please? 
Toni.

---

### Post by Toni_Vines on 2013-12-07
Hi andrew.46, I've looked at the page you suggest but although it has a very large amount of info on it, it tells me nothing of how to use the said info. For instance it has some very lengthy code with 'johnsmith' type sections that obviously need to be changed. Unfortunately if I try to paste it into Vim and then attempt to change anything it won't let me!!!!!!

---

### Post by Toni_Vines on 2013-12-07
q:Quit  d:Del  u:Undel  s:Save  m:Mail  r:Reply  g:Group  ?:Help










































---Mutt: (no mailbox) [Msgs:0]---(threads/date)-------------------------(all)---
/var/mail/toni: No such file or directory (errno = 2)
Take a look at this please. You will see along the bottom a line that includes "No such file or directory (errno = 2) Could this be something to do with my problems?

---

### Post by Toni_Vines on 2013-12-08
I take it I've exhausted the knowledge on mutt! Lol! Never mind, it was worth a try.
Cheers anyway.

---

### Post by howefield on 2013-12-08
It's been so long since I set mutt up, all I do with a new machine is install mutt and abook, untar my settings backup (abook folder, muttrc and .sig) to ~/ and I'm done.

Don't know if it helps but here is my muttrc, all you have to do is replace the ***'s with your details, (line 38 the first asterisks are your email usernames and the second your password. You could rename your muttrc or save it elsewhere and try using this one.

The main site I used to get up and running was this one : [http://www.linuxjournal.com/magazine/power-your-e-mail-mutt?page=0,0](http://www.linuxjournal.com/magazine/power-your-e-mail-mutt?page=0,0)

```
# Local folder
set mbox_type=Maildir
set folder=~/Mail

# IMAP Settings
set realname="**** ******"                    
set from="**** ****** <*******@ubuntu.com>" 
set imap_user=******@gmail.com
set imap_pass=******              
set folder=imaps://imap.gmail.com                
set spoolfile=imaps://imap.gmail.com/INBOX       
set record=imaps://imap.gmail.com/Sent            
set postponed=imaps://imap.gmail.com/Drafts        
mailboxes =INBOX # check for new email here                                 
set header_cache=~/.mutt_cache     

# Reading Mail
set timeout=10  
set mail_check=300
set sort=threads
set sort_aux=date
set move=no     
set mark_old=no
ignore * # ignore all headers except for ...
unignore Date: From: To: CC: Bcc: Subject:
hdr_order Subject: Date: From: To: CC: Bcc:
set index_format="%{%b %d} %-15.15L [%Z] %s" # custom index format

# Composing Mail
set editor="nano"     
set markers=no     
set signature=~/.sig  
set include=yes     
set forward_format="Fwd: %s"                

# Sending Mail
set copy=yes      
set smtp_url="smtps://******@gmail.com:******@smtp.gmail.com/" 

# Pretty Colors
color status white blue
color index green  default ~N  # new
color index red default ~D  # deleted
color index brightmagenta default ~T  # tagged
color index brightyellow default ~F  # flagged
color header green default "^Subject:"
color header yellow default "^Date:"
color header yellow default "^To:"
color header yellow default "^Cc:"
color header yellow default "^Bcc:"
color header yellow default "^From:"
color header red default "^X-.*:"

# View Special Formats
# set mailcap_path=~/.mailcap
# auto_view text/html # auto-render html inline mutt

# Use abook with Mutt
# set query_command="abook --mutt-query '%s'"
# macro index a     "|abook --add-email\n" 'add sender to abook'
# macro pager a     "|abook --add-email\n" 'add sender to abook'
```

---

