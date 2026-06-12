---
title: "How to Login to All Intranet Web Applications at Once?"
date: 2006-12-15
forum: Programming Talk
---

### Post by peaceful_dragon on 2006-12-15
I'm not sure at all where to post this question, but I'll try this subforum first. :)

So I've set up a brand new server with 6.06 LTS for my little 3-person team project and have installed a ton of required apps... Internal blog, external blog, wiki, email, bugtracker, projectmanager, you name it.

Now I've got a bit of a problem because EACH of these apps require a separate login/password! So now I already have:

1) Ubuntu machine login/password
2) Internal blog login/password
3) External blog login/password
4) Wiki login/password
5) Email login/password
6) Bug Tracker login/password
7) Project Manager login/password

A ridiculous number of logins/passwords to keep track of.

Does anybody know of a way, easy or otherwise, to tie all these logins/passwords together so people only need to login once?

Thanks!

Edit: So far all applications I've installed are using PHP and MySQL, except for email, which is using "GMail For Your Domain".

---

### Post by Dan Lyke on 2006-12-15
Depending on which applications you're using, a lot of tools are starting to adopt [OpenID]("http://www.openid.net/"). I use the TravelWiki OpenID extension with MediaWiki, I believe that it's coming shortly for SMF, and it's not that hard to graft on to things. So you might consider looking that direction. They'd have to enter the same URL into all of the various apps, but at least they'd only have to remember one name and password combination.

It's also the case that many of these tools support authentication plug-ins that will, with a modicum of PHP, let you write your own login stuff. I thought at some point that Google was publishing an API for access to some of their tools that used their login system, it might be seeing if you can find an API that would at least tell you that they successfully logged in to their GMail account and what that login was, and use that as the authentication mechanism for all of the other apps.

---

### Post by peaceful_dragon on 2006-12-16
Thanks for replying Dan. I'll check into it!

---

### Post by lloyd mcclendon on 2006-12-17
we do transparent logins through LDAP

if your company has a network that you log into on your computer, you should be able to access that same server through your applications to perform authentication or better yet identification.  that way their is no password, it knows who you are by who you are logged into the network as.

basically we do something like this

```
String userName = getCurrentUserNameFromLDAP();
if (userName == null || ! setOfValidLoginNames.contains(userName))  {
    return unauthorized();
}
// person is logged in and exists in our access list so they can run this code
doSecureStuff();
```

---

