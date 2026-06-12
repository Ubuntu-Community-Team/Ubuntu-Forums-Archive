---
title: "How To Create An Irc Account"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-04-30
How do i create an IRC account...  i am just a beginner :)
so please gimme clear steps](*,):-o

---

### Post by marufaberlin on 2008-04-30
[http://www.ubuntuforums.org/showthread.php?t=376907](http://www.ubuntuforums.org/showthread.php?t=376907)

---

### Post by omns on 2008-04-30
This will help as well :)

[http://freenode.net/faq.shtml](http://freenode.net/faq.shtml)

---

### Post by master5o1 on 2008-04-30
They are different for each IRC server.

So if you join the server that #ubuntu (and derivitives) are located on, you will not have the same account for the server that bucket chat is on


(bucket = [http://jonanin.no-ip.org/bucket/](http://jonanin.no-ip.org/bucket/) example purpose only)

---

### Post by avacado on 2009-11-20
Can these steps be added to the documentation to make it newby friendly?

For example, one surfs to [http://freenode.net/faq.shtml#nicksetup](http://freenode.net/faq.shtml#nicksetup) where one finds the instruction

[COLOR=Magenta]Register your IRC nick:           [/COLOR][INDENT]             [COLOR=Magenta][B]/msg nickserv register <your-password> <your-email>
[/B][/COLOR]
[/INDENT]**...what on earth does that mean ?**
I managed to register a nickname account with jabber and chat in jabber.conference.net but I am stumped about how to create an IRC account that will connect with the ubuntu support channel.
honestly what does "/msg" mean?

I have tried empathy/edit/accounts/add/irc and I recieve a NICKSERV message that my choice of nickname is not registered.
Well obviously ! but how do I register?

---

### Post by Soul-Sing on 2009-11-20
Which irc client are you going to use? prob. xchat is a good client to begin with.
Serveroption: choose freenode.
channels: #ubuntu,#ubuntu-beginners,#ubuntu-beginners-help,etc.
then register.
/msg nickserv register <your-password> <your-email>

---

### Post by avacado on 2009-11-20
EMPATHY is standard with Karmic.
I am so close, I can smell success, I even got a message from NICKSERV to say I need to reegister, I just need someone to tell me what '/mesg' means.

---

### Post by avacado on 2009-11-20
I just found the conversation window for nickserv which opens when you try to join the room by adding acount details for IRC and select freenode from the drop menu.
I have sent an instant message by typing in the bottom line where the cursor is flashing and pressing 'enter' and recieved this reply

nickname registered password email from nickserv
solved - I am in !

---

### Post by Soul-Sing on 2009-11-20
welldone!:p

---

### Post by avacado on 2009-11-20
Start empathy using either 
Applications/internet/empathyIMclient
OR
click on the envelope symbol in the top right hand corner of the screen

The contact list window will appear
To create an account click Edit/accounts/Add/IRC/Create/Freenode
fill in some details of an account username and password you would like and click connect or apply.

Wait a couple minutes and a window will appear from the freenode server auto administrator called Nickserv. If you lose this window you can get it back by clicking the envelope again. this will tell you that the nickname is not registered, don't panic - type a reply in the line below this window with the format 
REGISTER <your password> <email address> and follow the instructions from Nickserve to verify the nickname.
further information on [http://freenode.net/faq.shtml#nicksetup](http://freenode.net/faq.shtml#nicksetup)

Now you have a nickname, all you need to do is enter a room to start conversation.
Bring up the contact list again .
click room/join and change the account to your new nickname in the droplist and enter #ubuntu and press enter.
with any luck you will be in the support room.
the process will be similar for other IM carriers and other rooms.

For example, my local ubuntu team is on IRC.FREENODE.NET:6667 
I am not sure how to 'point' my IM client toward that server...always learning !

---

### Post by dbram32 on 2010-02-05
Thanks Avacado and others - worked like a charm!

---

### Post by andrew.46 on 2010-02-05
Hi dbram,

> **dbram32 said:**
> Thanks Avacado and others - worked like a charm!

Another little nickserv snippet is the syntax to get a neat summary of your settings:

```
/msg nickserv info
```

or indeed to see *all* nickserv options:

```
/msg nickserv help
```

All the best,

Andrew

---

### Post by rstewart on 2010-06-23
> **avacado said:**
> reply in the line below this window with the format 
REGISTER <your password> <email address> and follow the  instructions from Nickserve to verify the nickname.

Just for other Empathy newbies: the email said to send the following command on IRC:
/msg NickServ VERIFY REGISTER <user nickname> <identification code> 
"/msg NickServ" starts a private conversation with NickServ
But if you still have the chat conversation window with NickServ hanging around, you already have this conversation going.

So when you get the e-mail, go the window from NickServ, and paste something like  
"VERIFY REGISTER myUserNickname randomIdentificationCodeYxnoasdEC"
piece of your email in the chat line. No "/msg NickServ"

---

