---
title: "FireFox add-on annoyance"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Barney-R on 2013-02-19
Hello all. Following a clean install of 12.04, I installed the "Better Privacy" add-on (among others) in FireFox, and now the Better Privacy help screen comes up in a second tab every time I open FireFox and at intervals while browsing.

It's hardly a life-threatening situation, but I wondered whether anyone could tell me how to stop this happening. I've been through the Better Privacy settings, and there's nothing there, so perhaps I could do something using **about:config**, but I don't know what I'm looking for there.

In case it's relevant (probably not), I'm using the Gnome desktop for now.

---

### Post by arnav803 on 2013-02-19
some add-ons have this tendency i am not an expert but i think you should try to disable or remove the add-on and install it again.have you installed java run time environment(because it once helped me)?

---

### Post by Barney-R on 2013-02-19
Thanks for that arnav803. It doesn't seem to have helped, but sometimes things seem to "settle" after a while, so I can hope. Any further suggestions would be welcome though.

---

### Post by Barney-R on 2013-02-20
Still no luck getting rid of that annoying page. Does anyone know how I can block it? It's not malware (as far as I know), but it's driving me round the twist.

The "URL" shown in the address bar is

chrome://bprivacy/content/BetterPrivacy.html

There's no http:// and no www. , so does that mean the page is somewhere on my machine? If so, would I be able to delete it?

Alternatively is there something I can change in **about:config**?

Any help would be appreciated.

---

### Post by SuperFreak on 2013-02-20
I don't know about the plugin you are having problems with but I have used Ghostery for some time without issue and it blocks trackers. It can be turned off for individual sites or specific trackers and I have not had any tabs open on Firefox as you have

[http://www.ghostery.com/help/firefox]("http://www.ghostery.com/help/firefox")

---

### Post by Barney-R on 2013-02-20
Thanks for trying, SuperFreak. I use Ghostery too. It's only since the upgrade (clean install) that I've had this problem. It's (almost certainly) not malware, but it's just always there. I close it and it comes back. Sometimes it appears again even if I **haven't** closed it, so I get two copies of it at the same time.

I've just asked Mozilla about it, so I'll post any responses here, but still I'd appreciate any suggestions.

---

### Post by Barney-R on 2013-02-20
Problem solved at last!

I've had a response from the Mozilla forum telling me to check my Home Page setting. I had no idea that FireFox could have **multiple** home pages set.

As well as my preferred home page, Better Privacy had added that annoying page as well, so instead of

[https://startpage.com/](https://startpage.com/)

I had

[https://startpage.com/|chrome://bprivacy/content/BetterPrivacy.html](https://startpage.com/|chrome://bprivacy/content/BetterPrivacy.html)

(separated by a "|") so **both** pages loaded instead of just the "proper" one. I'll be keeping an eye out for tricks like that in the future, and I hope my experience will help someone else.

---

### Post by MyTinFoilHat on 2013-02-20
> **Barney-R said:**
> ...I'll be keeping an eye out for tricks like that in the future, and I hope my experience will help someone else.

Guess what? It just did! 

Interestingly enough, I have been experiencing something similar recently - but with the NoScript plug-in. Every start, my home (my preference is to start with about:blank) would open in one tab and NoScript's donate page in another tab. 

Now I know to check that out and make changes as necessary.

You've got awesome timing!

Thanks.

---

### Post by Barney-R on 2013-02-21
Happy to help, MyTinFoilHat. That's what these forums are all about. We share our problems, share the solutions and learn by them. Eventually **we** get to be the ones helping others.

---

