---
title: "Opera browser, the ultimate paradox ?"
date: 2009-04-23
forum: Recurring Discussions
---

### Post by Guillaumeb on 2009-04-23
Hi all, happy Jaunty day :)

As I recentely learned that France was the top country in open source (via Ars), I was kind of wondering about all the arguments used by pro-open source users.

I mean look at Opera, which is not open source

They say free/open source software are more secure, which is true.Yet Opera is way more secure than Firefox, Chrome, or any browser actually. I mean it's a fact, they hardly have security breaches.

They say free/open source software lead to innovation, which again, is true. Yet Opera was the one largely responsible for implementing tabbrowsing, mouse gestures, as well as the Speed dial. All of the other have been influenced by those ideas.

Just an idea - which I welcome you to discuss - that crossed my mind...

---

### Post by 0per4t0r on 2009-04-23
Even though it's not open source, opera is great! But, I use firefox more commonly.

---

### Post by Rocket2DMn on 2009-04-23
Moved to Recurring Discussions.

---

### Post by blueshiftoverwatch on 2009-04-23
> **Guillaumeb said:**
> They say free/open source software are more secure, which is true.Yet Opera is way more secure than Firefox, Chrome, or any browser actually. I mean it's a fact, they hardly have security breaches.
The fact that Firefox has about 20% market share while Opera has about 1% might have something to do with that. The more people there are using X piece of software the more people who are going to try to exploit X piece of software.

---

### Post by Sashin on 2009-04-23
To be honest I think chrome is more innovative than opera with it's tabs as seperate processes thing.

---

### Post by Skripka on 2009-04-23
> **blueshiftoverwatch said:**
> The fact that Firefox has about 20% market share while Opera has about 1% might have something to do with that. The more people there are using X piece of software the more people who are going to try to exploit X piece of software.

So why isn't Apache plagued by malware?

---

### Post by chucky chuckaluck on 2009-04-23
opera's secure because no one dares mess with its giant toolbars.

---

### Post by kk0sse54 on 2009-04-23
> **chucky chuckaluck said:**
> opera's secure because no one dares mess with its giant toolbars.

No, opera is secure cause it's norwegian and nobody messes with vikings :p

---

### Post by p_quarles on 2009-04-24
> **Skripka said:**
> So why isn't Apache plagued by malware?

That's sort of a red herring question. "Malware" is usually taken to mean some kind of infectious third-party executable that does bad things to a computer when run with the user's privileges. In that sense, the answer would be to simply point out that the core Apache server doesn't "run" anything aside from http requests. 

Of course, an Apache server with a bad configuration (and the default configurations usually are) can easily allow people to see files you may not have intended. 

That said, the bulk of high-traffic web sites involve some degree of interactivity and content mangement that goes beyond the basic http server's abilities. So, when we talk about an Apache server, we generally mean not only the core http server, but modules for CGI scripting and data handling. This is where Apache is not at all secure "out of the box," and it's easy to find numerous stories of attackers finding vulnerabilities in server side scripting handlers, as well as managing to inject SQL commands directly into the database engine, both of which carry the potential for arbitrary code execution. 

Apache is popular because it's a solid, reliable and straightforward foundation for building a web server stack. The fact that there aren't "viruses" for Apache doesn't mean that sites running on top of it are somehow bulletproof.

---

### Post by tabibito on 2009-04-24
Have been an opera user since ver.6.xx. Now I'm eagerly waiting for ver.10's release.

:-P

---

