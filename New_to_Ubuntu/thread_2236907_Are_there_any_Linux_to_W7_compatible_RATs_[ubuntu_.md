---
title: "Are there any Linux to W7 compatible RATs? [ubuntu 14.04]"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by Justin.Daniels on 2014-07-29
First of all, I apologize if I am posting this in the wrong section. I couldn't find a better suited section for this post.

Okay, now to my question. I need a remote admin. tool that I can use on my ubuntu 14.04 laptop to connect to my dad's W7 PC. I am leaving town in the next few weeks to begin college, and my father, who is always having PC issues, can't afford to have his computer go down as he works from home (off of his PC). I am the only person in our household who can fix a computer when it has software issues, so we need a way I can still fix his computer from my school. If you guys know of anything that I can use to do this it would be tremendously helpful. I've done some research using google and I couldn't find anything.

Thanks so much guys,
Justin.

---

### Post by TheFu on 2014-07-29
Win7 Pro includes an RDP server - you can connect to that, but you probably want a VPN connection setup first, so nasty internet people can't hack his W7 system even more.  VNC has the same limitation (needs a VPN too) - if he's running Home or less.

There are allow commercial solutions - teamviewer seems popular with the Windows crowd.

If his system is that flakey, perhaps it is time to upgrade to Linux and only run the 1-2 specific Windows programs left over in WINE?  I did that for Mom in 2010 and it has worked out well.

---

### Post by kurt18947 on 2014-07-29
I could find myself in a similar situation.  Here are some options I've kept in mind.  I haven't tried any of them.

The first choice depends on how you feel about giving Google unfettered access to your systems.  The reviews seem like it's not 100% functional with Debian/Ubuntu.

[https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp](https://chrome.google.com/webstore/detail/chrome-remote-desktop/gbchcmhmhahfdphkhkmpfmihenigjmpp)

Another option:

[http://www.teamviewer.com/hi/download/linux.aspx](http://www.teamviewer.com/hi/download/linux.aspx)

I think these two choices may have a chance of working cross platform.  

A 3rd option that might be more secure but seems like it'd be more involved to set up would be some sort of VNC app running over an SSH or VPN connection.  There are VNC clients available for Windows as well as linux.  I assume you'd need to configure firewall(s)

I'm no expert, perhaps someone who is and who's done this will check in.  I hope I've given you some ideas to explore and do share your experiences, good or bad.  Needing to provide remote support is not all that uncommon.

---

