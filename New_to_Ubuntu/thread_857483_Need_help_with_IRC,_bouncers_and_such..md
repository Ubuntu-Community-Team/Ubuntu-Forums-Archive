---
title: "Need help with IRC, bouncers and such."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by the.FATMAN on 2008-07-12
Hello everyone, I'm not sure, but I believe this may be my first thread here.:)
First things first, I love Linux, and I love Ubuntu. The community is nice and there is a ton of support, you don't find that in too many places.
While I have had different issues with different things, the community has always been there for me and helped me out, so thank you, everybody.

Now, on to my issue and the cause of this thread. I am part of an IRC community that I love, and love hanging out with. Only one problem though, my host mask isn't very good. I know that I could use mIRC to help with that, but I'm using Konversation and I don't want to switch.

After doing a search on the web, I learned a little bit about bouncers, and one in particular called znc. Sounds very good, but I can't find a good tutorial on either. I need tutorials, lol, otherwise I can't get things going. Everything that I have learned I have taught myself, so not finding a tutorial regarding znc makes it very hard for me to get started.

So, I am reaching out to the Ubuntu community, I know there is a wizard here who can help me get this sorted out. :)
Thanks ahead of time guys.

cheers,
theFATMAN

---

### Post by -grubby on 2008-07-12
You can ask a freenode staffer to set your host to unaffiliated@yourname/something

---

### Post by TSS on 2008-07-12
If you are on FreeNode, do what the above poster suggested, and have them get you a host mask.  See: [http://freenode.net/faq.shtml#nicksetup](http://freenode.net/faq.shtml#nicksetup)

If you are not on FreeNode you have a few options.  First, see if your IRC network has a HostServ.  Use /msg hostserv help to see.  If it does, you can request a mask and one an oper approves it, you'll get it.  

Otherwise, I would suggest using a free shell to protect your privacy.  If all else fails, ask an oper on the IRC network that you use.  Explain to them your concerns, and they should be able to help you out.   That's what they are there for.

---

### Post by the.FATMAN on 2008-07-12
Hey thanks for the help guys, really good advice. :)

I'm not on freenode actually. I mean I am, but just for support, primarily.
I'm on Foreverchat, so I will check out the hostserv commands and see what happens.

Could someone elaborate a bit on free shells? I'm not too familiar with them.

---

### Post by TSS on 2008-07-12
To answer your question about free shells.

You can get one at a site like this: [http://silenceisdefeat.org/](http://silenceisdefeat.org/).  On most sites, you have to donate a dollar via Paypal, or something similar.  

Then, you would log into your free shell using ssh from Ubuntu.  After that, just use the IRC client through the free shell.  Others on the IRC network will see the IP address of the free shell provider, not your home IP address.

EDIT: A look at the Forever Chat homepage reveals that it does provide a hostserv.

---

### Post by the.FATMAN on 2008-07-12
Hey guys, i tried the hostserv request command, i'm still waiting on that, but, I'm curious, do I need to use the free shell?

---

### Post by TSS on 2008-07-12
You don't need to use a free shell if you do not want to, a host mask through hostserv should fit your needs just fine.

---

### Post by the.FATMAN on 2008-07-12
Ok guys, this really weird, my vhost request was granted, but now if a whois is done on me, my true and entire IP is displayed, whereas it wasn't before.
When I deactivate the vhost, it doesn't do that.

Whats going on with that?

---

### Post by TSS on 2008-07-12
I know, at least for me on networks where I use a vhost, that when I do a /whois on myself I can still see my IP address, even when my vHost is activated.  Others should not be able to see it though.  Activate your vHost with /msg hostserv on and ask someone else to do a WHOIS on you.

---

### Post by the.FATMAN on 2008-07-12
Ok, thanks TSS, I appreciate that.

---

