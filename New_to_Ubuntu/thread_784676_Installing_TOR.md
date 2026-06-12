---
title: "Installing TOR"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-06
I was going to attempt installing TOR using this as my guide:
[https://help.ubuntu.com/community/TOR]("https://help.ubuntu.com/community/TOR")
However I see that the additions for *sources.list* are for fiesty & edgy. When I go to the URL specified, there is no directory for hardy. Would I be safe installing the fiesty version? There IS, however, a "stable" directory. Should I maybe install THAT? 

I also dug up these directions:
[http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html]("http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html")
Are these any "better"? (I get nervous anytime I see the word "compile" in these things...:( )

If there's any chance I may bork my system screwing around with this, I'd rather just wait until I'm more experienced, but it seems somewhat straightforward. Any insight would be greatly appreciated.

Thanks!!!

---

### Post by tamoneya on 2008-05-06
i beleive the reason why there are no hardy sources listed on that page is because tor was added to the main repositories.  Try ```
sudo apt-get install tor
```Then continue from where it says installing privoxy

---

### Post by MedellinManDem on 2008-06-25
When I try and install Tor using the above terminal command, I get a message saying 

"E: Couldn't find package tor". 

Why is this?

---

### Post by bluepowder7 on 2008-06-25
do you have the universe repos enabled?
also, in my hardy xubuntu install, it's in synaptic so it should be dead easy to install (not that i know what it actually IS)

---

### Post by MedellinManDem on 2008-06-26
> **bluepowder7 said:**
> do you have the universe repos enabled?

Yes.

---

