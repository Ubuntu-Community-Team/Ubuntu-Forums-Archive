---
title: "UIDs and servers"
date: 2011-08-09
forum: Programming Talk
---

### Post by mpnordland on 2011-08-09
Hi,
I have the singular necessity of getting the user identifier of the user accessing my server. I am writing this myself, it is intended to be a local server. However, I need to strictly differentiate between users, with out the users themselves being involved. Also, all of this needs to happen through a browser. I would appreciate any tips.

---

### Post by Bachstelze on 2011-08-09
Define 'accessing'.

---

### Post by karlson on 2011-08-09
> **mpnordland said:**
> Hi,
I have the singular necessity of getting the user identifier of the user accessing my server. I am writing this myself, it is intended to be a local server. However, I need to strictly differentiate between users, with out the users themselves being involved. Also, all of this needs to happen through a browser. I would appreciate any tips.

I'm kinda confused as to what exactly you are trying to do...  From what I can gather from your post you can do this easily with 
```

$ last
$ w

```
or
```

$ who

```

If you need to do this in C, C++, Perl there is a 
```

getuid()

```

function beyond this you need to be a little more specific.

---

### Post by mpnordland on 2011-08-09
Ok, time to facepalm and remind myself of how to ask programming questions.
*facepalms*
Now that we've got that out of the way, The "server" is a local proxy server that tracks internet usage. The idea is to help people break internet addictions by emailing flagged urls to their partner of choice. The thing is, is that linux is a multi-user system, hence the need to differentiate between users so that we don't have embarrassing mix ups. To help the users stay accountable, it is necessary to hide all of the authentication from the user. It is also needful to make it difficult to masquerade as another user. And, since it is a proxy server, you have to figure out who the user is from the browser. Cookies may be an option, but I'd like a more fool proof way.

---

### Post by mpnordland on 2011-08-10
bUMP

---

### Post by karlson on 2011-08-10
> **mpnordland said:**
> Ok, time to facepalm and remind myself of how to ask programming questions.
*facepalms*
Now that we've got that out of the way, The "server" is a local proxy server that tracks internet usage. The idea is to help people break internet addictions by emailing flagged urls to their partner of choice. The thing is, is that linux is a multi-user system, hence the need to differentiate between users so that we don't have embarrassing mix ups. To help the users stay accountable, it is necessary to hide all of the authentication from the user. It is also needful to make it difficult to masquerade as another user. And, since it is a proxy server, you have to figure out who the user is from the browser. Cookies may be an option, but I'd like a more fool proof way.

I have to ask what proxy server are you using?  Squid probably will give you the information you need.  I don't know if you will need more than that.

---

### Post by mpnordland on 2011-08-11
I'm writing my own for various reasons, the primary one being that I need to hand off the urls to another process. What I'm looking for is the user id, or the user name of whoever owns the browser process that is connecting to my proxy server.

---

### Post by Barrucadu on 2011-08-11
As the browser will be connecting to the proxy server via a network (even if run on the same computer), you can't just get the UID. You could differentiate between users based on their IP or user-agent (or one of the plethora of other headers).

---

### Post by mpnordland on 2011-08-11
So there is absolutely no way to figure out the user id from the browser?

---

