---
title: "run my own web anonymizer"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by cryptk on 2008-08-30
I have a friend at work that cannot access the internet without the IT people snooping all over everything that she does.  Here is what I am trying to do to help her out, I am wanting to run a web-anonymizer on a spare computer that I have here at the house so that she can surf the internet over an https connection with my computer to help and keep prying eyes out of what she is looking at.

I am looking for something similar to what [http://www.hidemyass.com](http://www.hidemyass.com) does, something with a web based front end to make it easier for her to use it (I don't feel like explaining to her how to set up a proxy on her computer).  Here are the requirements.

Https connection between her and my proxy (between my proxy and the net can be whatever)

URL cannot give away what she is looking at

Some kind of web based interface would be nice (so she can go to "https://MY_IP_ADDRESS:PORT" and get a thing requesting what site she wants to see.

I look forward to any ideas and I will check sometime tomorrow... Even if you don't have a solution, but you have some ideas that could help, then let me know.

---

### Post by nicedude on 2008-08-30
First if it is not her personal computer but one issued by her company then this might be pretty difficult because even though you may be able to setup an encrypted tunnel from her work to your house and then from there out to the Internet again, it would not matter much if they use screen capture software on all their machines or keyloggers etc as some crazy companies do now days. I have not ever attempted anything like this though as I am always concerned with my privacy to the internet only ( and rarely care about that as we don't really have privacy vs governments anymore ). 

Here are some links to look at though that are similar in nature though maybe not exactly but should give you some starting points on this

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

[http://www.hackinglinuxexposed.com/articles/20030316.html](http://www.hackinglinuxexposed.com/articles/20030316.html)

[http://www.freerepublic.com/focus/news/766058/posts](http://www.freerepublic.com/focus/news/766058/posts)

[http://www.guard-privacy-and-online-security.com/free-encrypted-tunnel-proxy.html](http://www.guard-privacy-and-online-security.com/free-encrypted-tunnel-proxy.html)

Hope that gets you started, man I might have to do this too just because it sounds so cool :-)

PS even if this works then the IT guys could see that encrypted data is leaving the building from her system that they didn't setup and this may cause problems for her as well :-)

---

### Post by cryptk on 2008-08-30
Yep, I already told her that it would still be a violation of system policy.  The thing is, the site she wants to go to is not actually filtered, but it isn't on an "authorized" list.  She is allowed one hour of "leisure" time on the company internet (basically so they can surf wherever during their lunch breaks).  She just wants a way to be able to go to that site w/o it counting towards her leisure time.

It is a web forum, and the leisure time starts whenever she go's to something not on the authorized list then ticks away, no matter if she continues to go to different sites or not, it is one hour from the first page visit.  Since this is a forum, she just wants to be able to check it a few times throughout the day instead of having to do it all in one go.

I will read those links and reply back if I find anything out.  Once I get this working, I will post something in the Tips forum explaining how to set it all up.

---

### Post by k3lt01 on 2008-08-30
This is a very interesting idea and something that I would be interested in seeing how it would work, but (there are always buts) I would think this would be deemed either illegal or unethical for both you and her so I would be very careful that it doesn't come back and bite you on the ...

---

