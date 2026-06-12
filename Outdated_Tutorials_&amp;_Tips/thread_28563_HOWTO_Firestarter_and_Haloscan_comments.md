---
title: "HOWTO: Firestarter and Haloscan comments"
date: 2005-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-04-20
Firestarter is a nice gnome GUI for the iptables firewall.
Haloscan is used by a lot of blogs around the web to provide the ability to make comments.

Problem:
Firestarter blocks the entire 72.x.x.x range BEFORE it allows individual IP addresses.
[www.haloscan.com](www.haloscan.com) has an ip of 72.9.234.77.

Symptoms:
Any page with a haloscan comment box will time out because haloscan won't load.

Solution:
Edit /etc/firestarer/user-post and add the following text.

/sbin/iptables -I NR -p tcp -s 72.9.234.77 -j RETURN

Stop/Start your firewall.

Explanation:
72.x.x.x didn't use to be valid addresses, so anything coming from here would be spam. By inserting this rule into the firewall we can treat 72.9.234.77 (And ONLY 72.9.234.77) the same as every other IP address. An alternative would be to remove the line "72.0.0.0/8" from /etc/firestarter/non-routables, but that unblocks the entire range.

---

### Post by Jad on 2005-06-07
Thank you Curufir, Thank you from my heart man, Nobody will know how value this post is unless they had it, but you know, I never expected it could be my firewall

[http://www.easyhttp.com/jad/2005/04/error-haloscancom-and-me.html](http://www.easyhttp.com/jad/2005/04/error-haloscancom-and-me.html)

Thank you again Thank you
you really made my day! Mwwwwwwah

---

### Post by nacs on 2005-08-01
Same. Thanks.  :)

---

### Post by Ninnghizidha on 2005-08-02
I have been looking for the reason of this "bug" since 2 weeks! I'm very glad you offered me an answer ...

My Problem-Site was "codex.wordpress.org", with the IP 72.36.221.99.


Thanks a million,
Ninnghizidha

---

