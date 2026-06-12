---
title: "Trying to figure out which web technologies to use for a web project"
date: 2011-10-28
forum: Programming Talk
---

### Post by Mezzoforte on 2011-10-28
I'm interested in creating an website that lets users create discussions and write comments. It sounds pretty simple, and indeed the first step is pretty simple, but I hope to be able to build something reasonably sophisticated. (Requirements: Large number of registered users, possibility to express how individual posts are related to other posts and display posts depending on this.) I hope I'm not being too vague.

The question is, which technologies would I do well to use? I am a programming beginner - the only language I know reasonably well is Ada (i.e., I took a university course and did pretty well). I have learnt some of the basics of PHP and MySQL (HTML and CSS aren't a problem) because it seemed to me that the straight-forward way to make my website system was to create MySQL databases, access them with PHP and then manage the output with HTML and CSS. In order to make the website more interactive, it also seems it would need a fair share of JavaScript.

It seems, however, that this might not be the most straight-forward way. I realize it will take a lot of time, but I learn quickly and should be able to make it using these technologies. But maybe it would be more efficient to use some kind of web application framework? I've heard some talk about Ruby on Rails, for example. Would that be a better option, or does it come with any serious restrictions or problems?

I'm for the moment mostly interested in creating the system in a development environment, but hopefully down the road it will lead to something that can be launched publicly.

---

### Post by moldaviax on 2011-10-28
isn't there off the shelf software you could use for this? or is it more an exercise in programming?

M.

---

### Post by CptPicard on 2011-10-28
Rails or Django depending on your language preference.

---

### Post by ofnuts on 2011-10-28
> **Mezzoforte said:**
> I'm interested in creating an website that lets users create discussions and write comments. It sounds pretty simple, and indeed the first step is pretty simple, but I hope to be able to build something reasonably sophisticated..Re-inventing PhpBB or myBB?

---

### Post by AlexDudko on 2011-10-28
Stay with PHP+MySQL+JavaScript+HTML+CSS

---

### Post by Mezzoforte on 2011-10-29
ofnuts: Fair question, but I'm not aiming to make something like that. I want to move away from thread-based, chronological discussions. I haven't tried implementing any of those myself, but I think threads and chronological discussions are the foundation of them. Please correct me if I'm mistaken.

---

### Post by Mezzoforte on 2011-10-29
> **AlexDudko said:**
> Stay with PHP+MySQL+JavaScript+HTML+CSS

It seems this option would work fine, although I have to put in quite a lot of work until I have something that works. 

What are the main differences between using, say, Rails and the combination mentioned (PHP+MySQL+JavaScript+HTML+CSS)? Any particular advantages/drawbacks?

---

### Post by juancarlospaco on 2011-10-29
Python, Bottle, HTLM5, CSS3, JS, Ninja-IDE, WebP, SVG, WebM, JQuery,
you got Free hosting to start at [https://appengine.google.com](https://appengine.google.com),
or Pay a hosting service of your choice, thats it, good luck dude!

---

### Post by gsmanners on 2011-10-29
So, you're trying to create a wiki? It's awfully hard to find a concept in web coding that hasn't been pretty thoroughly done already.

---

### Post by Mezzoforte on 2011-10-29
> **gsmanners said:**
> So, you're trying to create a wiki? It's awfully hard to find a concept in web coding that hasn't been pretty thoroughly done already.

Nope, no wiki. Wikis are good for trying to represent facts, but they're not as good for discussions that don't relate closely to facts. It's awfully hard to find an existing concept in web coding that hasn't been done well already, but there are probably innumerable new concepts that might find their place on the web (or replace old concepts).

---

### Post by maclenin on 2011-10-29
My knee-jerk is: [http://wordpress.org/](http://wordpress.org/)

---

### Post by Some Penguin on 2011-10-31
> **Mezzoforte said:**
> It seems this option would work fine, although I have to put in quite a lot of work until I have something that works. 

What are the main differences between using, say, Rails and the combination mentioned (PHP+MySQL+JavaScript+HTML+CSS)? Any particular advantages/drawbacks?

All of those are tried-and-true, and have substantial amounts of relevant code already written as well as large pools of expertise from which to draw.

---

### Post by kevinharper on 2011-10-31
> **maclenin said:**
> My knee-jerk is: [http://wordpress.org/](http://wordpress.org/)

I'm w/ Maclenin on this...

Is this something that you need up and running or are you developing this for the experience? Either way you should look at WP. You can either install it, config, and let the community grow on its own... or you can use WP as a guide/goal of what you should develop.

EDIT: PS: You will need to know HTML5 and PHP if you want to tweak it.

---

### Post by lykwydchykyn on 2011-10-31
I'd stay away from frameworks, especially if you're just starting out, if speed matters, and if you feel you have an original idea and don't want to be pushed into conventional ways of doing things.

---

### Post by Mezzoforte on 2011-11-01
Thanks for all replies.

It seems the way to go is MySQL, PHP, Javascript, HTML and CSS.

---

### Post by AlexDudko on 2011-11-01
> **Mezzoforte said:**
> Thanks for all replies.

It seems the way to go is MySQL, PHP, Javascript, HTML and CSS.

If you don't have your own server and can't configure it to your needs this seems the only sane variant because you stay dependent on companies which suggest hosting. Apache + MySQL (PostgreSQL - rarely) + PHP is the most usual configuration for the majority of them.

---

### Post by Mezzoforte on 2011-11-01
> **AlexDudko said:**
> If you don't have your own server and can't configure it to your needs this seems the only sane variant because you stay dependent on companies which suggest hosting. Apache + MySQL (PostgreSQL - rarely) + PHP is the most usual configuration for the majority of them.

Well, actually I've set up my own local Apache and MySQL servers already, so that I'll be able to try out code without having to upload it all to a web host. There is a decent chance I'll want to get a real host later though - I probably should be a little more knowledgeable about security before starting to run a server of my own open to the public. I don't know, maybe it's not a big deal configuring everything to be secure, but I'll definitely read up on it first. And learn to write secure code.

---

### Post by Mezzoforte on 2011-11-01
> **kevinharper said:**
> I'm w/ Maclenin on this...

Is this something that you need up and running or are you developing this for the experience? Either way you should look at WP. You can either install it, config, and let the community grow on its own... or you can use WP as a guide/goal of what you should develop.

EDIT: PS: You will need to know HTML5 and PHP if you want to tweak it.
Wordpress is good, and maybe it would save me more coding than it would cost changing it. However, Wordpress is a no-go to use for something with a commercial potential, and I'm not quite sure on that point yet.

---

### Post by gsmanners on 2011-11-01
If we're talking about a project with commercial potential, then I don't see what's stopping you from just starting at the bare metal with C. Make sure it's all coded the way you want it and no silliness getting in the way of functionality.

---

### Post by Mezzoforte on 2011-11-01
> **gsmanners said:**
> If we're talking about a project with commercial potential, then I don't see what's stopping you from just starting at the bare metal with C. Make sure it's all coded the way you want it and no silliness getting in the way of functionality.

Unfortunately I don't know C yet. At all. (I only know Ada reasonably well.) I'm guessing it would take a while to learn C well enough to make good use of it. PHP and MySQL seem easy enough to use, and being a little short on time I think I'll go with those. 

I like the idea though.

---

### Post by gsmanners on 2011-11-01
Yeah. C does have a bit of a learning curve. You'd want it least a month or two to spare.

---

