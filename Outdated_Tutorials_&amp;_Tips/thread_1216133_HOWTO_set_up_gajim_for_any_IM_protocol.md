---
title: "HOWTO: set up gajim for any IM protocol"
date: 2009-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by loomsen on 2009-07-17
*edit*

This Post is not longer supported, please refer to [http://blog.loomsen.org/2010/11/jabberxmpp-transport-setup/](http://blog.loomsen.org/2010/11/jabberxmpp-transport-setup/) for an updated version and if you need help.

Hello again.

In this post I will try and introduce those of you who aren't aware of jabber (and it's possibilities) yet to this very handy open source protocol. 
Now, you might think, well, open source is nice, yes, but who the hell has a jabber account.

One powerful feature of jabber however is to manage transports. Basically, you connect to a jabber server and then link the server to your legacy accounts (like msn, yahoo, google talk, icq, irc...)
This means you'll decrease your network load, cause you only need to connect to one server instead of one connection for each protocol.

[For additional technical information on how it works hit him &#8594; \\:D/](http://en.wikipedia.org/wiki/Extensible_Messaging_and_Presence_Protocol)

Here's what this HOWTO will try and setup:
[[img]http://www.ubuntu-pics.de/thumb/19112/shot_58_dtq51d.png[/img]](http://www.ubuntu-pics.de/bild/19112/shot_58_dtq51d.png)

[COLOR="Orange"][SIZE="4"]INTRODUCTION, PROLOGUE, APERITIF[/SIZE][/COLOR]
You may choose whichever server you like, however, na-di.de offers a pretty nice amount of transports which should fit most users needs, so this howto will use na-di.de as an example.
This is my very own, subjectively colored opinion, of course it's up to you to choose another server if you want. You'll be pointed to a list of all available servers, their status and their offered transports below.
You may create as many accounts as you want and merge them if you want, maintaining users using metacontacts (merging a contacts different accounts to one main account, so you won't have multiple occurences of the same contact but different protocols)

[COLOR="SandyBrown"][SIZE="3"]WHY?[/SIZE][/COLOR]
OK, here's why I want it, and maybe why you would enjoy jabber as well.
As far as I'm concerned, I've tried any instant messenger app there is around, liked some of them, disliked others, however, none of the common apps really impressed me, or at least satisfied my needs. 
Until I stumbled upon gajim and got used to the transport stuff and how to set everything up. 
Basically, I have accounts at ICQ (most of my contacts), MSN (only 4 contacts) and jabber itself.
Thus I rarely used my MSN acc just because of one contact refusing to use ICQ ^^ But, as my MSN contacts are really good friends, this wasn't a sustainable situation.
Facing this issue jabber seemed like the best choice for me (distributing the whole connection issues, keep alives and such to the transport jabber server, and decreasing my ressource usage)
Also, I never liked pidgin for some reason, I don't even know why, but I really hate it and I'm glad to be rid of it.

===  Plot ends here  ===

Now, you need to decide which client you want to use. You may use pidgin as well if you like it.
However, as I mentioned, I choose gajim, which is nice, small, based on xmpp, highly extensible and configurable (through the advanced config manager)

So, here's 
[COLOR="Red"][SIZE="5"]STEP 1[/SIZE][/COLOR]

Set up gajim. (should be included in the official repos, but I'm no longer running ubuntu, so please let me know if this differs somehow)

```
sudo aptitude install gajim
```

[COLOR="Red"][SIZE="5"]STEP 2[/SIZE][/COLOR]
Get yourself a jabber account. Some servers offer account creation from within gajim, some don't. The server featured in this tutorial doesYou may visit 
[ME, klick ME](http://www.jabberes.org/servers/)
for an extensive overview of available servers and their offered transports.

K, time to start up your designated new instant messenger client.

[COLOR="Red"][SIZE="5"]STEP 3[/SIZE][/COLOR]

[SIZE="2"]Using na-di.de as I'd recommend:[/SIZE]
Launch gajim. Upon startup, you'll be asked to enter an account. Choose to create a new account, next enter na-di.de at the server prompt, and enter your desired login details. 
If you did everything right you should receive a welcome message. 

[COLOR="SeaGreen"]==============================[/COLOR]
[SIZE="2"]f you want to go with another server:[/SIZE]
Choose to create a new account, choose the server you'd like to use from the dropdown menu, for example jabber.ccc.de
Klick next and gajim will connect to your desired server and provide you with a simple mask to create a new account. Enter your desired username and your desired password, hit next and you'll be prompted that your account has been created successfully.
Pressing finish will ask for your password you just specified and connect to your jabber server and return a welcome message.
[COLOR="SeaGreen"]==============================[/COLOR]


Aight, preparation finished, now lets introduce our existing ICQ account to our jabber account.

[COLOR="Red"][SIZE="5"]STEP 4[/SIZE][/COLOR]
Transport setup

Now, rightclick your account in your contact list and choose discover services
Et voila, you'll see something similar to this:
[[img]http://www.ubuntu-pics.de/thumb/19105/shot_50_MwOHTF.png[/img]](http://www.ubuntu-pics.de/bild/19105/shot_50_MwOHTF.png)

Now, let's take my introduction above as a concrete example to get you going.
Mark ICQ and click Register, now enter your ICQ login details (your unique user ID and your password you use to login to your ICQ account)
When done the na-di.de server will use these credentials to login to an ICQ server and import your contact list and your groups.
Easy as that.
Same for MSN. Rightclick your account, discover services, mark MSN, hit Register and enter your details. And you're done. Any other offered transport should behave the same, except IRC, which may differ between different servers.

[SIZE="2"][COLOR="Red"]IRC:[/COLOR][/SIZE]
Choose any server which offers IRC transport from the server list, and register for the IRC transport exactly as you did for your ICQ account. 
Now you're ready to add any room you want to visit by 
Actions --> Join Group Chat --> using account <server offering IRC transport> --> Join new Group Chat
and make the upcoming form look sth like
[[img]http://www.ubuntu-pics.de/thumb/19109/shot_55_J7V6aD.png[/img]](http://www.ubuntu-pics.de/bild/19109/shot_55_J7V6aD.png)

#<YOUR_DESIRED_CHANNEL>@<IRC TRANSPORT SERVER TO USE>

A new Chat window will open showing your desired channel

Alright, now you're setup with anything you need to get rid of your old multiprotocol messengers and let your transport server do the work.
Once linked, you may login to your jabber account from everywhere enjoying your transports, so this is not limited to your PC.


[SIZE="3"][COLOR="Red"]APPENDIX A:
[/COLOR][/SIZE]
Removing accounts

So, you've tried a few servers creating accounts on each server. You may remove the accounts directly from the server from within gajim. Go to 
Edit --> Accounts
mark the account you wish to remove and click remove. You'll see a prompt asking you whether to remove the account from the local configuration or if you wish to wipe it off the server as well.
This will only work for servers offering account creation from within gajim.

[SIZE="3"][COLOR="Red"]APPENDIX B:
[/COLOR][/SIZE]
Facts, links, clients, servers, options, capabilities and so on may be found all over the internet. 
A good place to start should be 

[www.jabber.org](www.jabber.org)



Thats it, if you happen to find some major mistake in the steps described above please don't hesitate and let me know.
I hope you enjoied this HowTo, and that it's been easy and pleasant to follow. If enough users are interested in this I'll extend this HowTo and explain PGP encryption and some more of the huge variety of gajims capabilities and confguration options.
Thank you for your attention, 
enjoy.

---

### Post by loomsen on 2009-09-11
Hmm, although this obviously hardly bothers anyone (- I actually wonder why -) I decided to take another shot on explaining some further usage possibilities.

This second part deals with a Jabber contact, which acts as a dictionary, as well as registering with a server which offers remote storage with jabber.

The dictionary is fairly easy to set up, just adding a jabber contact and you're done.
The account you would want to add for a GER<->ENG dictionary is
[email]woerterbuch.info@swissjabber.org[/email]

Then you may send whichever word you want to translate to your new contact and instantly get something like:
[[img]http://www.ubuntu-pics.de/thumb/24432/shot_49_971A2g.png[/img]](http://www.ubuntu-pics.de/bild/24432/shot_49_971A2g.png)

For other dictionaries please search the web, there are a couple of dict transports out there.

Another neat thing is the possibility to store files remotely by registering with a server offering a file storage service, as the shot above shows: (you may simply add a new account registering through gajim, using jabbim.cz as server.

It provides some nice services, like a facebook beta transport, RSS reader, a smtp service, SMS services, TV services and so on (some of these services are only available in particular countries, at least with this server)
Here's another shot:
[[img]http://www.ubuntu-pics.de/thumb/24433/shot_50_0l9i17.png[/img]](http://www.ubuntu-pics.de/bild/24433/shot_50_0l9i17.png)

After registering with the storage service you'll get subscription requests by 3 new contacts, public.disk, private.disk and album.disk (suitable for photos) as you can see in the first image of this post.

The services offer some simple commands you may use, like mkdir, ls, rm, link (to get the link to a file)
Another impression:
[[img]http://www.ubuntu-pics.de/thumb/24434/shot_51_L09HLz.png[/img]](http://www.ubuntu-pics.de/bild/24434/shot_51_L09HLz.png)

While your files stored in public are accessible for everyone, those stored in private _are_ private.

As far as I'm concerned, I wouldn't want to be without my jabber account anymore, looking forward to a wide variety of services still to come.

Maybe this convinced some more of you to take a look into jabber, most of all because of the TOCs of the established IM services
[(a shocking short maybe found here)](http://www.ulm.ccc.de/~marcel/warum-jabber.htm)

Go jabber.

---

### Post by loomsen on 2009-12-29
updated

---

