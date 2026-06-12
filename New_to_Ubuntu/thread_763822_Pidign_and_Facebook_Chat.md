---
title: "Pidign and Facebook Chat"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-04-23
using Pidgin, the skype plugin, and a bit of time, I have been able to put gmail, yahoo, msn, and skype all in one pidgin window. Now facebook has released a chat. I find this useful because facebook is pretty much the only place where ALL my friends have an account. Unlike msn, etc. where I have to add their addresses individually with facebook I already have it there. I'm not a huge facebook user but I would like the ability of being able to chat with my friends, especially those who aren't on msn, etc. So any thoughts on putting the facebook chat as a plugin for pidgin? It only came out, and I don't have any idea of what to do, but I'd like to try.

---

### Post by Oldsoldier2003 on 2008-04-23
> **abhiroopb said:**
> using Pidgin, the skype plugin, and a bit of time, I have been able to put gmail, yahoo, msn, and skype all in one pidgin window. Now facebook has released a chat. I find this useful because facebook is pretty much the only place where ALL my friends have an account. Unlike msn, etc. where I have to add their addresses individually with facebook I already have it there. I'm not a huge facebook user but I would like the ability of being able to chat with my friends, especially those who aren't on msn, etc. So any thoughts on putting the facebook chat as a plugin for pidgin? It only came out, and I don't have any idea of what to do, but I'd like to try.

thats really more a pidgin thing than a Ubuntu thing :) You could wander over to the [Pidgin website]("http://www.pidgin.im/") and see if you can find anything on writing plugins, or see if there is any indication anyone has started a plugin.

---

### Post by abhiroopb on 2008-04-23
Yes I did look there, but couldn't really find a place to post my issues, if you know a link would be appreaciated.

---

### Post by computertreker on 2008-04-23
The way I understood it is that as of now the Facebook chat is exclusively a web app. Meaning that pidgin won't be able to communicate with it. However, there is a plan to support Jabber which will allow Pidgin (and many other IM clients) to communicate with Facebook chat.

---

### Post by abhiroopb on 2008-04-23
I was thinking of something along the lines of how gmail chat is supported in pidgin (which uses jabber of course).

---

### Post by Daniel591992 on 2008-04-23
So it will be possible one day? That'd be incredibly useful!

---

### Post by SOULRiDER on 2008-04-23
> **computertreker said:**
> However, there is a plan to support Jabber which will allow Pidgin (and many other IM clients) to communicate with Facebook chat.

Pidgin DOES support Jabber already.

---

### Post by rouge568 on 2008-04-23
> **SOULRiDER said:**
> Pidgin DOES support Jabber already.
I think he was talking about the facebook chat.

---

### Post by topgun98 on 2008-04-27
Here, here!

Two questions:
1) Is anyone, in addition to me, me willing to throw in some cash to get this coded?
2) Is anyone here willing to code such a plugin for cash?

---

### Post by PhoenixP3K on 2008-04-28
Well... The Facebook chat was released only a few weeks ago. Right now it's like a web-app running on their servers meaning it's not like there is a communication protocol we can use to tap into it. For MSN or AIM, the work involves to replicate what the original applications have to do. In the case of the Facebook chat I think the best outcome is if they truly port it to have Jabber support this way Pidgin and many other IM programs will be able to support it.

I will agree that Facebook is a place I have the most contacts consolidated. But since I'm using Pidgin people I know on different IM networks are already accessible via one interface.

As for getting in touch with the Pidgin people they seem to have an IRC channel #pidgin on irc.freenode.net
This link talks about their community features: [http://developer.pidgin.im/wiki/PidginCommunity](http://developer.pidgin.im/wiki/PidginCommunity)

---

### Post by topgun98 on 2008-04-28
> **PhoenixP3K said:**
> Right now it's like a web-app running on their servers meaning it's not like there is a communication protocol we can use to tap into it. 

Insanity!  Just because it uses AJAX instead of a proprietary protocol, it can't be used?  I strongly disagree.  In fact, I bet it would be many times easier reverse-engineering AJAX versus some closed binary protocol.

> **PhoenixP3K said:**
> For MSN or AIM, the work involves to replicate what the original applications have to do. In the case of the Facebook chat I think the best outcome is if they truly port it to have Jabber support this way Pidgin and many other IM programs will be able to support it.

Of course that would be ideal.  But we have no control over it.  They may decide to do it... they may not.  In the meantime, no connectivity for pidgin users.

> **PhoenixP3K said:**
> I will agree that Facebook is a place I have the most contacts consolidated.

Exactly!  Facebook is the place where *everyone* is available on one network, at least for me.  Pidgin integration would be the best thing since IM.

If a few of us throw a couple bucks on it, we could easily hire a coder to whip up a plugin... I can do the reverse-engineering, but I haven't messed with the libpurple codebase before.

Who's in?

---

### Post by abhiroopb on 2008-04-28
I personally have no coding experience, so it won't be so easy for me to provide help. What has pidgin doen exactly to integrate gmail? Because gmail chat at least LOOKs the same as the facebook chat.

---

### Post by xdevnull on 2008-04-28
There's no project files yet, but there is a site...
[http://sourceforge.net/projects/pidginfbchat/](http://sourceforge.net/projects/pidginfbchat/)

---

### Post by Vadi on 2008-04-29
This isn't technically feasible right now, as I understand. Everybody, on all paltforms, has to use the web-based version of the facebook chat.

---

### Post by topgun98 on 2008-04-29
Care to explain why it's not feasible?

---

### Post by Vadi on 2008-04-29
""Facebook chat" does not seem to have an associated IM protocol, and until it does, we can't implement it" (from the #pidgin notice)

Sounds simple enough. Home-brewn web chat, no standard procotol, nor any documentation.

You know, it does help if you actually do some research to the project that this is related to, eh? I doubt even one Pidgin developer will see this thread on these forums.

---

### Post by atomkarinca on 2008-04-29
> **topgun98 said:**
> Care to explain why it's not feasible?

Because there's no documentation.

It seems they already are looking to implement the jabber protocol, you can read it [here]("http://www.facebook.com/group.php?gid=11586172524").

---

### Post by topgun98 on 2008-04-29
> **Vadi said:**
> ""Facebook chat" does not seem to have an associated IM protocol, and until it does, we can't implement it" (from the #pidgin notice)

Sounds simple enough. Home-brewn web chat, no standard procotol, nor any documentation.

You know, it does help if you actually do some research to the project that this is related to, eh? I doubt even one Pidgin developer will see this thread on these forums.

Yeah, because AIM was an open IM protocol with tons of documentation when gaim was created, right? :rolleyes:

Just because it's AJAX over HTTP via port 80 doesn't mean you couldn't write a plugin for it.

And no, you don't need documentation in order to write a plugin for a protocol... it just makes it much easier.

---

### Post by Vadi on 2008-04-29
Go ahead and do it then! Nobody's stopping ya.

---

### Post by topgun98 on 2008-04-29
> **Vadi said:**
> Go ahead and do it then! Nobody's stopping ya.

Way to read the thread.  If you take a gander, you'll notice I already stated that I'm not familiar with the libpurple codebase, and that I'm more interested in joining with others who would like to hire a coder, since there seems to be a great deal of interest here and elsewhere.

---

### Post by Vadi on 2008-04-29
Good point, but I doubt facebook chat will compare to aim, especially given that facebook is working on a solution of their own already.

It's not like linux users are missing out on anything o.O

---

### Post by topgun98 on 2008-04-29
> **Vadi said:**
> Good point, but I doubt facebook chat will compare to aim, especially given that facebook is working on a solution of their own already.

It's not like linux users are missing out on anything o.O

Well, we don't know for sure that they're working on anything at all.

It would be worth $10 now to be able to integrate my Facebook friends with the rest of my buddy list.

---

### Post by bapoumba on 2008-04-29
I've removed 6 off-topic posts from this thread.

---

### Post by Vadi on 2008-04-29
Hm there'll need to be a lot of the $10's for anyone to be seriously interested, unless they use facebook themselves and have the ability to do it.

I mean, look at voice & video ([click]("http://cofundos.org/project.php?id=89")), it's at 10 Bids (&#8364;400).

---

### Post by hanzomon4 on 2008-04-29
I already can use facebook im with adium and adium uses libpurple right? I'm not booted into OS X right now but I believe it's through jabber that I'm able to connect to facebookIM

---

### Post by tj111 on 2008-04-29
The only method I could think of would be to implement some sort of web rendering engine (like Webkit), hide it, and parse the IM-section contents constantly for changes and stuff.  Think of it like the ultimate Greasemonkey script, but doing nothing but eating up resources and using regular expressions for parsing text/html and using javascript as an interface.  That's the only method I can think of for "reverse engineering" it, and I don't see it as being feasable (major resource hog, it'll turn Pidgin into Trillian).  

There are rumors that FB will integrate it with Jabber in the future, so I think your best bet for now would be to keep complaining to facebook until they add support, not pay someone to develop a plugin for it.

---

### Post by hanzomon4 on 2008-04-29
Wait that's social IM I'm using

---

### Post by abhiroopb on 2008-04-29
> **hanzomon4 said:**
> I already can use facebook im with adium and adium uses libpurple right? I'm not booted into OS X right now but I believe it's through jabber that I'm able to connect to facebookIM

So you've done it already? How? What settings have you used?

---

### Post by atomkarinca on 2008-04-29
Apparently you *can* add your facebook account through Jabber. All you gotta do is to add social.im application to your facebook account. Once you've added the application, it gives you the instructions.

---

### Post by abhiroopb on 2008-04-29
Tried social.im it basically works, but you have to invite each of your friends (18 at a time). Which seems like a real pain, so I haven't really bothered. But any thoughts on i?

---

### Post by bilal.17 on 2008-04-29
social.im is really crappy cuz as previously mention you have to re invite all over your friends..

---

### Post by abhiroopb on 2008-04-29
I think this has something to do with the fact that facebook does not allow spamming, so you can't just invita everyone in one go. even then I wouldn't like to invite everyone in one go, I'd be labelled a stalker!!!

---

### Post by abhiroopb on 2008-05-01
[http://lifehacker.com/386331/digsby-integrates-facebook-chat](http://lifehacker.com/386331/digsby-integrates-facebook-chat)

This looks really promising, wonder how they did it, wish it would come to linux, I'm happy with pidgin, but they seem to be working very hard!

---

### Post by whitenoise on 2008-05-03
I have been using Digsby for Windows for several months now.  They have indeed added Facebook chat/friend online status to their app some two weeks ago, and it works like a charm.

So there's got to be a way to do this, as I don't believe they are affiliated with Facebook.  (Facebook APIs?)

---

### Post by Mad_Gouki on 2008-05-07
I found this, but I can't figure out what folder it goes in to make the .so file

---

### Post by cudjoe on 2008-05-09
Guyz,

There are stuff online :
[http://www.neaveru.com/wordpress/index.php/pidgin-facebook-plugin/](http://www.neaveru.com/wordpress/index.php/pidgin-facebook-plugin/)
[http://fr.rpmfind.net/linux/rpm2html/search.php?query=pidgin-facebook](http://fr.rpmfind.net/linux/rpm2html/search.php?query=pidgin-facebook)

Looks like it's just missing a debian packager !

---

### Post by atomkarinca on 2008-05-09
> **cudjoe said:**
> Guyz,

There are stuff online :
[http://www.neaveru.com/wordpress/index.php/pidgin-facebook-plugin/](http://www.neaveru.com/wordpress/index.php/pidgin-facebook-plugin/)
[http://fr.rpmfind.net/linux/rpm2html/search.php?query=pidgin-facebook](http://fr.rpmfind.net/linux/rpm2html/search.php?query=pidgin-facebook)

Looks like it's just missing a debian packager !

It's not what we're looking for. This is straight from the site:

> [COLOR="Red"]**IMPORTANT: This plugin has nothing to do with facebook chat. This was created before facebook came out with facebook chat. If you are looking for a way to integrate facebook chat into pidgin, this is not the place to look. Sorry.**[/COLOR]

---

### Post by abhiroopb on 2008-05-09
Thanks...almost used alien!

---

### Post by BigBrownChunx on 2008-05-15
Sorry to reopen an old thread, but I've been working on Facebook chat for Pidgin for the last week or so, and have got buddy lists downloading and messages sending [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

---

### Post by atomkarinca on 2008-05-15
> **BigBrownChunx said:**
> Sorry to reopen an old thread, but I've been working on Facebook chat for Pidgin for the last week or so, and have got buddy lists downloading and messages sending [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

Great job. It seems to be working.

---

### Post by abhiroopb on 2008-05-15
Seems alright, just keeps signing in/out for some reason. (using linux). It signs a bunch of people in and a bunch of people out, dunno why. Haven't tested the chat that thoroughly yet.

---

### Post by abhiroopb on 2008-05-15
PS: Great work! Please post updates here

---

### Post by inportb on 2008-05-15
> **BigBrownChunx said:**
> Sorry to reopen an old thread, but I've been working on Facebook chat for Pidgin for the last week or so, and have got buddy lists downloading and messages sending [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

Whoa, that's awesome. I'll be installing and testing.
Thanks for the great work.

---

### Post by abhiroopb on 2008-05-15
Thanks a lot for this...

An error I am getting...it seems to log everyone out (or just me) and logs everyone back in, and then I notice a slight increase in the number of people online/offline.

---

### Post by inportb on 2008-05-15
Hm, interesting... it's crashed Pidgin once, but other than that, it looks good...

---

### Post by Kinst on 2008-05-15
How do you install it for newbies like me? I just put the libfacebookchat.so file in /usr/lib/pidgin/ but I guess now I don't know what I'm supposed to be doing.

---

### Post by abhiroopb on 2008-05-15
copy the .so file to /home/<user>/.purple/plugins (it'll be hidden so you'll have to show all folders.

---

### Post by Kinst on 2008-05-15
Cool! Thanks for the plugin, it works really well :)

---

### Post by macaholic on 2008-05-17
> **abhiroopb said:**
> copy the .so file to /home/<user>/.purple/plugins (it'll be hidden so you'll have to show all folders.
I don't have the plugins directory, and if I make it, it doesn't work.

---

### Post by abhiroopb on 2008-05-17
which version of pidgin do you have?

In any case I don't recommend you use it just yet, as it is HIGHLY unstable (keeps crashing pidgin, friends can't see me online). Still its a wonderful effort, but will wait until it becomes a bit more stable.

---

### Post by macaholic on 2008-05-17
2.4.1, I had to install it from the source since the package in Intrepid has an unsatisfiable dependency (perl 5.8).

---

### Post by abhiroopb on 2008-05-17
hmmm you may need the purple plugin pack. See the pidgin website about that.

---

### Post by macaholic on 2008-05-17
I think I have them installed already for some reason, because I have a bunch of plugins That I am using and work, but I'll install it anyway.

---

### Post by abhiroopb on 2008-05-17
i have 2.4.0 (which I got from the repo) and I can't remember exactly how I installed the plugins.

---

### Post by macaholic on 2008-05-17
Well I installed the plugin pack, theres more plugins now, but still no facebook plugin listed.

---

### Post by abhiroopb on 2008-05-17
wait wait you're doing it wrong I think.

Copy the facebook plugin to purple/plugins. Then Add a new account and you should see facebook in the list.

---

### Post by macaholic on 2008-05-17
Well I thought of that already, but it doesn't show up there either, and one other thing, even after I installed the plugin pack, there was still no plugins folder in .purple. Is this unusual? Should I try again to make a directory and put the plugin in there?

---

### Post by macaholic on 2008-05-20
Anyone else have any ideas?
EDIT: Theres a 64-bit version now, tryign that.
EDIT2: 64 bit version works, and there is a new version overall, so check it out.

---

### Post by mbeierl on 2008-05-21
Awesome!  The 64-bit version works for me on Hardy.  I even have it hooked up with the Festival plugin to "announce" my contacts as the come online.

Now, what's the coolest thing I can do with Linux that I can't with Windows?!?

---

### Post by abhiroopb on 2008-05-21
Still has errors for me... :(

---

### Post by aphelionos on 2008-05-26
I get to the point where i can add a facebook acount to Pidgin. But when i do so i get no contacts to show, and i get no error messages or notificatio that i can't login. Any details on what login info to write in which field of the plugin?

any ideas?

---

### Post by abhiroopb on 2008-05-26
screen name: the full e-mail address you use for facebook
password; your facebook pw.

---

### Post by niceguy123 on 2008-05-26
> **abhiroopb said:**
> using Pidgin, the skype plugin, and a bit of time, I have been able to put gmail, yahoo, msn, and skype all in one pidgin window. 

Can you tell me more about the skype pulgin? I don't see it on the Pidgin site. How do you add it?

++++++++++++++++++++++++++++

OK, I found it here [http://myjobspace.co.nz/images/pidgin/](http://myjobspace.co.nz/images/pidgin/), but it is not installing. I'm getting a message that says: "Requires Skype to be running." Even tough I've got skype running.

---

### Post by abhiroopb on 2008-05-26
Did you install the deb? Did you add it properly in pidgin (using the add account)? Finally just restart both skype and pidgin.

---

### Post by niceguy123 on 2008-05-26
> **abhiroopb said:**
> Did you install the deb? Did you add it properly in pidgin (using the add account)? Finally just restart both skype and pidgin.

I hit the skype4pidgin.deb link on [http://myjobspace.co.nz/images/pidgin/](http://myjobspace.co.nz/images/pidgin/)
> Linux

    * skype4pidgin.deb (Debian/Ubuntu x86/x86_64) - Last update 16 May 2008
    * libskype.so (Linux x86) - Last update 16 May 2008
    * libskype64.so (Linux x86_64) - Last update 16 May 2008
    * libskype_dbus.so (Linux Finch dbus) - Last update 16 May 2008
    * libskype_dbus64.so (Linux Finch dbus x86_64) - Last update 16 May 2008
    * To install, run the deb package or copy libskype.so to the plugins directory, normally /usr/lib/purple-2/ or ~/.purple/plugins


It downloaded and ran package installer which gave me the message I wrote above.

I tried a couple of times closing both skype and pidgin and reinstalling with the same result.

---

### Post by abhiroopb on 2008-05-26
Where did you originally install skype from?

---

### Post by cudjoe on 2008-05-26
I was having the same problem, facebook account configured but no contacts.

I took the last version from [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/) and it just worked !

---

### Post by ginger_meggs on 2008-05-26
Hey guys, I couldn't help but notice that facebook chat appears to be operating on XMPP (techy term for Jabber) if you use firebug you can see the chat client ticking away sending the keep-alive packets, sending presence info etc. I just finished writing an AJAX client for a jabber server we run internally at work and so I've got a pretty good idea how these things work now.

Basically somewhere on their (facebooks) network they've got a jabber server jabbering away. If you could find the URL for this then you could hook Pidgin straight up to it without writing a single line of code as Pidgin can already connect to any XMPP service. I currently use Pidgin to test our Openfire server as it is.

The only hassle seems to be that they've got a server-side script proxying the requests to the server as opposed to binding directly to their jabber servers http-bind service. If that's the case it could be a bit tricky finding out the URL of their jabber server, it might not even be externally accessible.

---

### Post by abhiroopb on 2008-05-27
This is way to technical but basically when I started this thread I am guessing this is the kind of thing I had in mind. Similar the gtalk.

---

### Post by niceguy123 on 2008-05-27
> **abhiroopb said:**
> Where did you originally install skype from?

Not sure if I remember. Probably from their site or I copied a terminal command from this forum or from a ubuntu blog linked from this forum.

---

### Post by abhiroopb on 2008-05-27
I guess it doesn't matter all that much how you installed it :P. So when  you try to install the plugin using Deb Package manager, it tells you that skype is not running?

---

### Post by niceguy123 on 2008-05-27
> **abhiroopb said:**
> I guess it doesn't matter all that much how you installed it :P. So when  you try to install the plugin using Deb Package manager, it tells you that skype is not running?

Yes.

---

### Post by abhiroopb on 2008-05-27
I'm sorry I'm at a loss, perhaps download the .so file and copy it to the folder ~/purple/plugins.

---

### Post by abhiroopb on 2008-06-05
Just to update new version of Facebook Chat for Pidgin ([http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)) with an added .deb installer! Make sure you remove the .so file from your plugins directory before installing this! 

Thanks to eionrobb for starting this project!

---

### Post by abhiroopb on 2008-06-12
Update for facebook pidgin plugin: [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

(version 1.14)

---

### Post by abhiroopb on 2008-06-15
Update for facebook pidgin plugin: [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

(version 1.15)

---

### Post by jure1873 on 2008-07-23
I don't know why but after installing this plugin pigin started crashing occasionaly. Yesterday I couldn't even open pidgin cause it crashed as soon as I started it. Then I was quick enough to disable the fb account and now pidgin works (without fb chat). Anyone else experienced this?

---

### Post by abhiroopb on 2008-07-23
Plugin update to 1.29 [http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

According to the changelog the crashes have been fixed, but I have found that this plugin is HIGHLY unstable, and since I don't use FB chat that much its better to just keep it disabled until it is more stable.

---

### Post by dbulante on 2008-07-24
I have been getting an "authentication failure" when initiating a FB chat in Pidgin.  It was working before, then this.  It's as if it doesn't like having multiple connections into FB, i.e. connected in Firefox, and Pidgin.

---

### Post by abhiroopb on 2008-12-11
[http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

Ver 1.44

Many updates!

---

### Post by kevdog on 2008-12-15
I really dont like the defaults contained in this plugin.  If you compile from source, the makefile needs to be manually altered.  Its really a pain.  Please tell the developers to fix this.  My pidgin is located in /usr/local directory tree, and the default makefile does not include this.

---

### Post by abhiroopb on 2008-12-17
I will try and pass on the message. But to be honest, just go ahead and ask them yourself. I have no affiliation with them. I just wanted to promote the work they were doing!

---

### Post by squid68 on 2008-12-17
I saw on Ubuntu Unleashed that there is the plugin for pidgin via google. I found the deb file for installation and it said I already had it and said it reinstalled it. I am with using 2.2.1 and I do not have a Manage Accounts tab/option as the unleashed website said. In fact facebook does not even come up as a selectable option. Any ideas what is up?

---

### Post by abhiroopb on 2009-05-13
I'm sure this is known to everyone, but the pidgin-facebook chat plugin is available in the ubuntu "universe" repository.

---

