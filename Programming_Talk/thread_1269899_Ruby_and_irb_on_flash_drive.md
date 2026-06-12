---
title: "Ruby and irb on flash drive?"
date: 2009-09-18
forum: Programming Talk
---

### Post by sam191 on 2009-09-18
Hello all, 

I was wondering if there is any way that I could put Ruby and the irb on a flash drive? 

School is starting on Monday, but I don't have a laptop. So I will have to work on the school's computers in the lab. However, they only have Visual Studio (and maybe eclipse) on windows machines.

Appreciate the help :)

---

### Post by falconindy on 2009-09-18
This doesn't answer your question exactly, but have you considered configuring an SSH server so you can log on to your computer remotely and use irb there?

I've been doing this in class with PuTTY, pageant, and my ssh-key on a flash drive.

---

### Post by sam191 on 2009-09-18
That's pretty interesting. I've never used an SSH server before. I will look into that, thanks!

Now I JUST realized that we have Macs in the computer lab, and I'm pretty sure Macs come with Ruby. 

But I'm still interested to hear if it is possible to load up the environment onto a flash drive.

---

### Post by angryfirelord on 2009-09-19
Did you look at the AllInOneRuby project?

[http://www.erikveen.dds.nl/allinoneruby/]("http://www.erikveen.dds.nl/allinoneruby/")

---

### Post by sam191 on 2009-09-19
> **angryfirelord said:**
> Did you look at the AllInOneRuby project?

[http://www.erikveen.dds.nl/allinoneruby/]("http://www.erikveen.dds.nl/allinoneruby/")

This is EXACTLY what I was looking for. :D Thanks!

Although, it seems kind of dated, 2007 I believe? I am working with Ruby 1.8.7, will this still work?

---

### Post by angryfirelord on 2009-09-19
> **sam191 said:**
> This is EXACTLY what I was looking for. :D Thanks!

Although, it seems kind of dated, 2007 I believe? I am working with Ruby 1.8.7, will this still work?
Well, I'm not a ruby coder, so I couldn't give you an answer on that. But most software that increments from, say, 1.x.1 to 1.x.2 is just doing bug fixes and what not. Usually those version changes aren't going to crash your code. So this script should still work even though it was tested on 1.8.

---

### Post by sam191 on 2009-09-20
Yeah, I know what you mean. The reason I ask though, is because the book I am following explicitly states that I should use Ruby 1.8.2 and nothing before. But I totally get what you're saying about the version numbers. 

I wonder how difficult it would be to re-implement it with the latest version of ruby, since it is "free software", this could be a possibility.

Good stuff nonetheless, thanks a lot!

---

