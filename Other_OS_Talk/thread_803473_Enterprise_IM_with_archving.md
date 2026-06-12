---
title: "Enterprise IM with archving"
date: 2008-05-22
forum: Other OS Talk
---

### Post by abuthemagician on 2008-05-22
I am looking for a good Enterprise IM package that will let me archive user messages. I work for a Credit Union and we want to take email away from most of our users and replace it with IM so they can still communicate with their supervisors.

I have looked into Jabberd with Bandersnatch, but I couldn't get it to work on Ubuntu because of something stupid, but that is what i really want to use because of the admin features and the reporting / archiving features. 

Anyone have any recommendations?

---

### Post by Dr Small on 2008-05-22
Why would you want to take email away? That sounds ridiculous.

---

### Post by abuthemagician on 2008-05-22
I know it sounds mean, but people are really abusing it, and due to some of our requirements we have to use MS Exchange (which i happen to like so lets not discuss moving to another system). Also we want to upgrade to 2007, but the costs involved are more then we want to spend on the tellers just so they can talk to each other. If we give them Internal only IM, they can chat to their hearts content and not slow down the email server (hypothetically).

---

### Post by Dr Small on 2008-05-22
I have never successfully setup jabber either, but maybe if you start posting some of the errors and what the problem, a few people will join on the bandwagon and help you solve the problem.

Another form of communication would be IRC, but I'm not real sure if you would want IRC or not. You would need an IRC client like Gaim, Pidgin, IRSSI or Xchat.

---

### Post by Luke has no name on 2008-05-22
I know you said not to ask this, but if you're talking about an internal system for just the tellers, why not set up postfix email or something?

I'd have to try setting up Jabber on my server before I could help you on that... but XMPP is a great protocol.

---

### Post by abuthemagician on 2008-05-22
as far as IRC goes, we have some employees that are older and we had a hard enough time explaining the latest teller software, let alone try to explain IRC. Also, IM is point and click software for the client side, much like email is.

as far as a separate email server, we are going to give everyone IM, but limit who has access to email.

---

### Post by Dr Small on 2008-05-22
Instant Messenger (IM) is the protocol, the client is what could be considered 'point and click'. Anyhow, what client did you plan on using for your IM protocol? If it was Pidign or Gaim, then those clients will support IRC also, which still gives them the same atmosphere of 'point and click'.

---

### Post by ugm6hr on 2008-05-22
I have no idea whether this is the kind of thing you are looking for - it is a Bulletin Board system that has since developed into a complete Groupware system.

[http://www.citadel.org/doku.php/doku.php?id=start](http://www.citadel.org/doku.php/doku.php?id=start)

It does also allow email - presumably that can be restricted though.

---

### Post by abuthemagician on 2008-05-22
For the client it would be a windows based client as we are stuck with windows due to our core application requirements. We are looking into using Linux with an XMPP server, and want IM because it will give us presence (as long as people remember to put themselves in away mode) and it will also give us instant notification of messages. 

Citadel looks nice, but we want something that can be left open all day, and not have another application interfere with it. For instance if they click a link somewhere and it takes them away from the site to a new website.

---

### Post by Wizard of Aahz on 2008-05-23
Citadel does have IM ability - built in jabber server and yes. it archives. Some of the other functionality might be a little overkill, but no one has to keep open the citadel client. As I type this I'm also IMing other citadel users using Trillian.

---

### Post by LaRoza on 2008-05-23
> **abuthemagician said:**
> as far as IRC goes, we have some employees that are older and we had a hard enough time explaining the latest teller software, let alone try to explain IRC. Also, IM is point and click software for the client side, much like email is.

as far as a separate email server, we are going to give everyone IM, but limit who has access to email.

Some IRC clients are point and click. However, I use finch for IM and it is text based ;)

Don't judge protocols by the interface ;)

---

### Post by abuthemagician on 2009-02-04
we went with OpenFire on this in case anyone wondered.

---

### Post by pmicheal on 2009-02-04
Email is the best solution. Also setup & use your own mail server for maximum security. It's very secure you can share all of your secrets via email without any tension of lacking.

[Linux Archive]("http://www.linux-archive.org/")

---

### Post by abuthemagician on 2009-02-05
We already have an Exchange 2003 server. We were looking to offload some of the use by those who do not receive external emails to save on licensing if we go with 2007. It also takes away the load of general chit chat and gives us presence information.

---

### Post by alastair on 2009-02-09
> **abuthemagician said:**
> we went with OpenFire on this in case anyone wondered.

I'm looking to do something similar - install internal company IM. I'm currently testing Jabber via the jabberd2 packages. This was a bit more pain than expected (manual setup), plus a lot of learning (I've not done any IM before, even as a user). I also had to download and compile a "chat" plugin (muc-conference) manually. It all seems to work .. but seems a little adhoc. A concern is now be package maintenance and update.

I'll check ejabberd soon I think. Then perhaps Openfire. A GUI admin tool is atractive right now!

Alastair

---

### Post by abuthemagician on 2009-02-09
I would try openfire first. It has many plugins including RED5 which will give you a web based flash client as well as audio / video chat. The AV chat windows are kinda small at 320x2?? but I don't have an issue with that. Tried to get 640x480 out of the beast but don't know enough about the tools required to make it work.

Upgrading openfire is a cinch. Just download the .deb package and install do an upgrade. Done. Also it integrates with active directory, and you can use SSO if you take the time to set it up on the server.

Overall, no packages to compile (unless you want to) or dependencies to track down.

---

### Post by abuthemagician on 2009-02-09
also, we have ours running on a Dell Optiplex GX240 with a early 1.4ghz P4 processor and 1gb of ram. We have 75 users on it and it never goes down or does anything weird. I would think we could fit more than that on it but we don't have any more employees to test the theory.

---

### Post by HermanAB on 2009-02-09
Hmm, Citadel does it all: Email, calendars, IM, chat...

The Citadel back-end is BerkeleyDB and it can handle up to 256 TB of data.  You can literally replace dozens of Exchange servers with a single Citadel server.

See this:
[http://citadel.org](http://citadel.org)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

Cheers,

Herman

---

### Post by feign on 2009-02-09
I realize you got a solution, but wanted to give you some things to consider.

One thing to consider is some of your users may use IM to communicate with their children, etc.  I use IM at work strictly so my wife/kids can get a hold of me. I don't use it to communicate with co-workers as they would send stuff that should be routed through our request system, etc.  

Also I found that implementing changes like this best come from the top along with HR participation.

---

