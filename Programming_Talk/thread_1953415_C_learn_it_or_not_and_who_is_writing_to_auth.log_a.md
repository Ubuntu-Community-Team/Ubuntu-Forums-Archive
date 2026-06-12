---
title: "C learn it or not and who is writing to auth.log and how to modify it?"
date: 2012-04-06
forum: Programming Talk
---

### Post by faifas on 2012-04-06
Hi,

I'm a developer working on web applications. I usually find myself having no knowledge of what happens on my server when I hang out with friends or develop apps. I would like to start working on my own server monitoring system so that I get to know more about servers in general.

My first goal is to decide what language should I develop with. I am really looking forward to learning C, would love to understand how Ruby or PHP works in lower level. Would like to view PHP source and understand it. Sure, it's a long process but I want to start it.

In my opinion developing with C would take more time than installing Ruby or just writing pyhon code.

I can also do stuff in php, but don't really want to.

Do you have any tips for selecting a language for server programming?

I am currently facing an issue that my server starts to have overload (load avg. 4 and more on vps with 1core cpu) because sendmail spawns multiple processes (those that I see when I use top) and my MTA has dkim-filter and dk-filter for signing emails. But when I use top I see only one instance of dk-filter and dkim-filter, so my general idea was to make a program in C (can I do in other?) that would spawn multiple instances of dk-filter and dkim-filter.

My #1 goal, dk-filters problem and article about [why learn C]("http://en.wikibooks.org/wiki/C_Programming/Why_learn_C%3F") has nearly convinced me I should start learning C.

I also need advice on auth.log issue.

Log file has lines like
```

Apr  6 14:49:53 254740 sshd[20970]: Invalid user ftpuser from 14.139.56.5
Apr  6 14:49:53 254740 sshd[20970]: pam_unix(sshd:auth): check pass; user unknown
Apr  6 14:49:53 254740 sshd[20970]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=mail.nith.ac.in 

```

what I want to do is parse this file, then add info to mysql and later display it on my www in the following format:

"1 hour ago 14.139.56.5 (mail.nith.ac.in) attempted to login with non-existent user 'ftpuser'"

Generally this is for monitoring and knowing when my friends log in my server.

I can parse it in php, nothing special, but for learning curiosity should I do it in C? And if I am doing it in C, where can I find a daemon's/processes or somebodies code who is adding info to auth.log? I think it would be much better to add some sort of hook to that so ip, host and username could be added to mysql without parsing logfile (in case it's over 1GB or something).

Sorry if my thread got too large and if I have too many questions, but if you can help me with any of questions please do it :) I'm 23 years old doing a career in web apps and think I can do more. There really is more stuff I could learn and create. If I'm getting good with C would also like to contribute to open source, such as Ubuntu.

Thanks!

---

