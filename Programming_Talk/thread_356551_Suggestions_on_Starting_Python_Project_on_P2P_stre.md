---
title: "Suggestions on Starting Python Project on P2P streaming"
date: 2007-02-08
forum: Programming Talk
---

### Post by krypto_wizard on 2007-02-08
I am quite new  to python and I have done some small projects. I want to build a Peer to Peer streaming client ..something like BitTorrent. I know it is daunting but I got to start somewhere. Please come easy on me.

What I want in my client program is that client software logs on to some P2P streaming session from a list, connects to several computers using TCP connection (protocol may vary in future), obtain stream from other computers and also send stream to others and play the obtained media stream on to some media player like xmms or any music player.

My obstacles...
1.  I have very little experience in network programming ..... some tips here are very  welcome.... Please don't come hard on me.

2. I am not sure how stream content is gathered by client and sent to media player..... suggestions welcome.

3. I have not managed this big project so I am not sure about how to manage the code....suggestions welcome.

This newbie appreciates your tips. Any comments are welcome.

Thanks

---

### Post by neilp85 on 2007-02-08
> **krypto_wizard said:**
> 
1.  I have very little experience in network programming ..... some tips here are very  welcome.... Please don't come hard on me.


Start with a smaller client-server application to get the feel for things before diving right in to a P2P app. Something like a simplified HTTP server is always a good choice.

---

### Post by pmasiar on 2007-02-09
> **krypto_wizard said:**
> I am quite new  to python and I have done some small projects. I want to build a Peer to Peer streaming client ..something like BitTorrent. I know it is daunting but I got to start somewhere. Please come easy on me.

IMHO you should first become a member of existing similar project and learn the ropes. You will learn what tools and design decision they use, what works and what does not, how community works, etc.

*Then* you can dream about starting your own project and have slight chance of succeeding. Without the experience, i am afraid you will just get bogged down in details, bad design decisions, and scarce/no support from community, and will burn out.

Of course you might be genius child prodigy and you will start next bit torrent and prove me wrong. YMMV. Good luck.

---

### Post by bmf312 on 2007-02-11
Try to look at [Twisted]("http://twistedmatrix.com/trac/"). It's a good network programming framework and should make your life easier. Also, look at the examples.

*neilp85* is right, start from the client/server.
Regarding integration of your program with player. You have multiple options. One of the options - you can send the content to stdout and pipe it to the player. 
Managing code - if i understand correctly, you're talking about version control system. Try SVN.

Good luck.

---

