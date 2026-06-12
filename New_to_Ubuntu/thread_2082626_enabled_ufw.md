---
title: "enabled ufw"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-11-10
i just enabled ufw firewall with gufw and terminal and status
is
active
allow outgoing
deny incoming
profile skips

does this default settings affect my youtube java applets music chats facebook etc? can i foget it and do my normal stuffs as my firewall block all incoming does that mean i cant download music etc?

---

### Post by HiImTye on 2012-11-10
the only time you have to worry about your firewall is if you want to use a server program. keep in mind this includes file/printer sharing on your network (Samba). those settings look fine otherwise

---

### Post by Lars Noodén on 2012-11-10
> **vibaviattigala said:**
> i just enabled ufw firewall with gufw and terminal and status
is
active
allow outgoing
deny incoming
profile skips

does this default settings affect my youtube java applets music chats facebook etc? can i foget it and do my normal stuffs as my firewall block all incoming does that mean i cant download music etc?

As HiImTye said, you generally only need a firewall with server applications.

But to answer your question, the firewall keeps track of the connection state.  There are four states: [new, established, related, and invalid](http://www.linode.com/wiki/index.php/Netfilter_IPTables_Mini_Howto).  So the firewall doesn't actually block all incoming connections, just ones that are new or invalid.  Connections that are created directly or indirectly from your outgoing connections are allowed back in.  That keeps the firewall from blocking YouTube, chats, and so on.  

If you want to block Facebook or one of the other sites that are awful about trying to track users visits to as many sites as possible, you need to know which nets to block. Once you have that it is easy to do in UFW:

[http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy](http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy)

---

### Post by Lars Noodén on 2012-11-10
PS: If you are going to experiment with your firewall, it is better to use REJECT instead of DROP.
[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

---

