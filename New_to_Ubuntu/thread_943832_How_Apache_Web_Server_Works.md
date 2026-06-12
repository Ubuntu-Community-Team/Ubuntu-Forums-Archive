---
title: "How Apache Web Server Works??"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by justinram22 on 2008-10-10
Hello, I'm trying to get my head around this, i was hosting with [www.000webhost.com](www.000webhost.com) but i found that they were unreliable (which i guess thats my fault with going with a free host lol) so i have a extra computer around and want to set it up with apache, im installing ubuntu hardy as i type this, and im having trouble getting my head around this, i have a domain name from godaddy and im wondering how i would go about forwarding it to my server box? i was reading some tutorials on it, and i learned that you can have a IP address to your server, but i haven't found anything on how to forward it. Also, how would i go about linking the sites together? could i go

<a href"/home/justin/Desktop/something.html">

or would i have to somehow find the web address?

Thanks for any help

---

### Post by aeiah on 2008-10-10
there are several different things at play here. once you get apache installed, your web pages will be located in /var/www/

index.htm might want to point to an image in a folder falled 'gfx', so you'd use a relative path. this is good practice anyway, rather than using an absolute path. you'd use: <img src="gfx/image.png">

once you've got your website on your server running locally, you'll need to open it up to the world by forwarding port 80 onto your server through your router's interface.

to get your domain name to point to your IP (well, your router's IP) you'll have to deal with godaddy. i dont know how they do things but i imagine its pretty simple.

if your ISP doesn't let you have a static IP address, you'll need to either pay extra for one, or use something like dyndns, or perhaps godaddy has some kind of feature you can use.

i guess you really need a tutorial with a step by step guide, or maybe some wikipedia articles on what webservers are if you really need more information.

---

### Post by justinram22 on 2008-10-10
ok, one more question, i still don't get how to link files... i finally got to forwarding my domain name to my host (that was a nightmare lol) and i still can't figure this one out... any help would be nice, a step by step tutuorial would be extra nice, thank you

---

### Post by justinram22 on 2008-10-10
Im so stupid!!! sorry, i figured it out i forgot to put words or discription after the link so

<a href="gfx/text.txt">(i forgot to put this part)test</a>

---

### Post by sokopok on 2008-10-10
Maybe you'd better search google for some webdesign/html tutorials

---

