---
title: "HOWTO: Use Jabber With Transport Services"
date: 2008-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by NovaAesa on 2008-01-05
**[SIZE="4"]NovaAesa's Jabber Guide[/SIZE]**

**Reasons to use Jabber**
1)   Jabber is based on the open protocol XMPP (eXtensible Messaging and Presense Protocol). Open protocols are always good in my eyes. As GNU/Linux users we should be supporting open protocols.
2)   The Jabber network can't be 'down' like other instant messaging networks. I'll get to the reason behind this a bit later.
3)   You can still connect to existing contacts that use non-jabber protocols (such as MSN and AIM) without having to use a multi-protocol application. So compatibility isn't an issue.

**How Jabber works**
Jabber works in much the same way that email works. There are hundreds of Jabber servers through which a client programme can connect. Each person who uses Jabber has their own account with one of many Jabber services. When a message is sent, the message goes from that persons computer to their nominated Jabber server. This server then sends the message to the recipient's nominated Jabber server. Assuming that permissions are correct ie. the second person hasn't blocked the first person, the message will be sent from the second server to the recipient. This is the reason that the Jabber 'network' is never down. Everyone is using different servers, so if one server goes down then only the contacts connecting to that certain server can't connect. This is better than say the situation with MSN where if the server goes down then nobody can connect.

**Picking a Client**
There are many different Jabber clients out there available for use. Two of the main single protocol clients available are Gajim and Psi. If you use GNOME, Gajim runs well because it uses the GTK+ toolkit. I've used both Psi and Gajim and would recommend the latter.

**Setting Up an Account**
Before you set up an account, you have to decide which server you want to use. It's probably a good idea to choose a server that is geographically close to you. For example, I used jabber.org.au because the server is located in Australia. A list of Jabber servers can be found here: [http://www.jabber.org/user/publicservers.shtml](http://www.jabber.org/user/publicservers.shtml). There are two different ways to register for the service.
1)   You must go to their website and sign up for an account there.
2)   Use a Jabber client and simply sign in using the desired account name.
Different servers use different methods, so just give one a try!

**Connecting to MSN/ICQ/AIM/etc contacts**
Many of the complaints I have heard about Jabber (from both GNU/Linux and non-GNU/Linux users) are based on the idea that no one else uses Jabber. Many of my non-Linux friends prefer to use MSN because everyone else is using it. However, there is a way of using Jabber to connect to these contacts albeit indirectly. This is done through a 'transport' service, also known as a 'gateway'. Some servers will support these but others won't. The following instructions are for using Gajim, but a similar method can be used for using Psi (although the names may change slightly).
1)   Once you have logged into your jabber account, click on Actions -> Discover Services.
2)   Type in the address of the server you have your account with and click Go. For example my server is jabber.org.au, which will result in finding a transport for ICQ and one for Yahoo!.
3)   If you don't find the transport services you want, try looking under another jabber server. I really wanted an MSN transport because most of my contacts use MSN, so I looked under other servers. I eventually found that jabber.meta.net.nz had an MSN transport.
4)   Once you find the service you want, highlight it and click Register. You will then have to enter information about that service, such as the address you have  for that service (in my case novaaesa<at>hotmail<dot>com) and a password.
5)   A new entry under Transports should now appear in your Gajim main page. Contacts using the protocol you connected to using the transport will also appear on the main page.

**Closing**
So now people out there really have no excuse not to be using Jabber rather than any nasty propietary IM services. As a community that embrases free software, we should really all be using Jabber for our IM needs!

BTW if you're new to Jabber and are looking for someone to chat to I'm online most of the time. My JID (Jabber ID) is [email]novaaesa@jabber.org.au[/email]

---

### Post by -grubby on 2008-01-06
Nice guide. This would've helped me when i first started using jabber

---

### Post by mrgnash on 2008-07-10
Great guide, thanks. Adding contacts from other networks doesn't appear to work if you're using a Google Talk account, though :(

---

### Post by drubin on 2008-07-27
Just keeping this jabber thread alive!!!

I work with jabber every day. :) :)
Great tutorial if only more people used it and it was back on these forums as a available contact method.

---

### Post by KIAaze on 2008-08-02
I have a few questions concerning jabber:

1) Are the MSN&co passwords you enter for each of your non-jabber accounts stored on your own PC or on the servers providing the transport services? i.e: How safe is it to use such transport services?

2) Is it possible to have so-called meetings between people using different non-jaber protocols? For example so that if you are talking with a person using MSN and another using AOL, those two people could talk together without having Jabber.

---

### Post by drubin on 2008-08-02
> **KIAaze said:**
> I have a few questions concerning jabber:

1) Are the MSN&co passwords you enter for each of your non-jabber accounts stored on your own PC or on the servers providing the transport services? i.e: How safe is it to use such transport services?

2) Is it possible to have so-called meetings between people using different non-jaber protocols? For example so that if you are talking with a person using MSN and another using AOL, those two people could talk together without having Jabber.

1) passwords are stored on the servers... So It would be just as safe if not safer then using a windows live messagner (your password is stored on your own pc if "remember me" is checked)

**EDIT:** If you are using a "reliable" server every thing should be A ok, ie  jabber.org. (or your own one)

2)No it is not, Sorry but jabber only allows for a centerlised place for your accounts. YOU could be your jabber account to some one that was on MSN, but you would not be able to hold a conference between different IM  protocols.

---

### Post by KIAaze on 2008-08-02
Thanks.
Also: Are there any jabber servers which allow automatic password recovery?

Because I already tried jabber some time ago using jabber.org, but forgot my password and it seems the only way of recovering it is sending lots of info to the admin.

I just had a look at a few other servers and it seems to be the same everywhere.
Is it because automatic password recovery is dangerous or because it's complicated to install such a system?

---

### Post by drubin on 2008-08-02
> **KIAaze said:**
> Thanks.
Also: Are there any jabber servers which allow automatic password recovery?
....
Is it because automatic password recovery is dangerous or because it's complicated to install such a system?

The reason is because when you set up a Jabber account on their servers they do not ask for any IDENTIFIABLE information ie email address/mobile number.

So how would they send you the details? Could I just email them asking for your password. Others do ask for this information and would have recovery functionality. Not 100% sure of which ones though, I run private jabber servers..

---

### Post by KIAaze on 2008-08-02
Ah..., ok.
Then the e-mail address I had was just for an account on the website. (I can't even figure out how I got an account there, but I could request a new password [here]("http://www.jabber.org/user/password") and it worked, but not for jabber IM)

But I did find a jabber server with automatic password recovery:
[https://web.swissjabber.ch/index.php/Hauptseite](https://web.swissjabber.ch/index.php/Hauptseite)
:)

I'll still try mailing the jabber.org admin to see if I can get a new password.

---

### Post by drubin on 2008-08-02
> **KIAaze said:**
> Ah..., ok.
Then the e-mail address I had was just for an account on the website. (I can't even figure out how I got an account there, but I could request a new password [here]("http://www.jabber.org/user/password") and it worked, but not for jabber IM)

But I did find a jabber server with automatic password recovery:
[https://web.swissjabber.ch/index.php/Hauptseite](https://web.swissjabber.ch/index.php/Hauptseite)
:)

I'll still try mailing the jabber.org admin to see if I can get a new password.


That would be the account to login to their website not sure if that is also for the IM system.

Never heard of it, I would try and go with the WELL known ones if you are worried about security.

I have heard that emailing the jabber.org admin's  seems to work pretty well, just have to have the correct information.  Good luck

---

### Post by KIAaze on 2008-08-02
It's on the jabber.org IM services list and after reading their [policy for accepting servers]("http://www.jabber.org/submission-guide/im-service/policy") on that list, I think it's reasonably safe.

Still one more question ^^':
What nicknames will users of MSN&co see?
The jabber nickname/address or the MSN/AOL/... nicknames?
Are there jabber clients allowing separate nicknames for each service?

Best info I found was this: [http://forum.psi-im.org/thread/3865](http://forum.psi-im.org/thread/3865)
It suggests that there's only one nickname possible. :(

---

### Post by drubin on 2008-08-03
Some clients support changing your msn nickname. May i suggest Pigdin or PSI for jabber client.

Pigdin might be a lot more user friendly then PSI although psi is still one of the mots comprehensive jabber clients around.

If you are using Pigdin and would like to chat to your msn/AOL contact i would suggest setting up the msn/AOL accounts in Pigdin as it would be a better option then proxying through a jabber server. (Very useful if you need it or blocked by fire walls).


Pigdin support multiple account of any number of IM protocols. (Pigdin comes standard with the ubuntu install)

---

### Post by KIAaze on 2008-08-03
That's what I already do. I use MSN over pidgin.
I think I'll keep it that way since I don't feel comfortable with another server storing my MSN credentials (even if it's only for IM).
I'll just use jabber as a secondary IM account in pidgin.

---

### Post by NCarlson on 2008-10-12
> **drubin said:**
> Some clients support changing your msn nickname. May i suggest Pigdin or PSI for jabber client.

Pidgin rocks.  It DOES support Jabber. I stress this because of the newbie I am and couldn't find "jabber" in adding a contact, because the list had changed from "jabber" to "xmpp".  It's a more correct name for the protocol, I guess.

---

### Post by durand on 2008-10-13
Very nice guide. Unfortunately, jabber.org doesn't support any transports so I'm gonna stick to using multiprotocols. I really like jabber but I'm not entirely sure why it doesn't support many smileys as part of the default protocol..

---

### Post by drubin on 2008-10-14
> **durand said:**
> Very nice guide. Unfortunately, jabber.org doesn't support any transports so I'm gonna stick to using multiprotocols. I really like jabber but I'm not entirely sure why it doesn't support many smileys as part of the default protocol..

That would be because smilies are kinda anoying to say the lease. You can configure you client to display any number of smilies you would like :)

---

### Post by durand on 2008-10-14
Yeah...but I love having to show off the awesome pidgin smileys [IMG]http://durand.zephyrhosting.net/dump/smileys/smile-big.png[/IMG]

---

### Post by drubin on 2008-10-14
> **durand said:**
> Yeah...but I love having to show off the awesome pidgin smileys [IMG]http://durand.zephyrhosting.net/dump/smileys/smile-big.png[/IMG]

/me :frown: because his :-({|= teacher said  [-X when he found him 	:guitar:ing in the :popcorn: :ZlolflagZ: 
):P time to ](*,)

This is why I cant stand emotions... 

ps translated that is
/me Frowns because his music teacher said no when he found him playing guitar in the movie LOL.
I am sad because it is time to hit the road.

You have included 9 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Had to remove one.
> Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

---

### Post by KIAaze on 2008-10-15
> **durand said:**
> Yeah...but I love having to show off the awesome pidgin smileys [IMG]http://durand.zephyrhosting.net/dump/smileys/smile-big.png[/IMG]

I think smileys get translated into what the other's client currently has installed.
i.e. If you send ":)", MSN users won't see the same smiley as Pidgin users.
And worse: if you send a smiley the other doesn't have, he'll just see the ASCII code.

But maybe I'm wrong. I'm not such a big MSN user. I just remember people sometimes sending me some weird emoticons which just didn't get displayed and therefore most of the time didn't make any sense.

---

### Post by durand on 2009-01-25
> **KIAaze said:**
> I think smileys get translated into what the other's client currently has installed.
i.e. If you send ":)", MSN users won't see the same smiley as Pidgin users.
And worse: if you send a smiley the other doesn't have, he'll just see the ASCII code.

But maybe I'm wrong. I'm not such a big MSN user. I just remember people sometimes sending me some weird emoticons which just didn't get displayed and therefore most of the time didn't make any sense.

Oops, very late reply. That's why I like using custom smileys instead of the default ones. With pidgin, you can set your own images as smileys and when you use them, the image gets sent rather than just the ascii. Actually, since my last post, jabber has gained support for custom smileys but I'm not sure which clients support it. I know that pidgin does, but not sure about others.

---

### Post by durand on 2009-01-25
Could someone recommend a good msn transport server that supports buddy icons? My friends can see mine but I can't see theirs when I use msn.gajim.org as the transport.

Thanks

---

