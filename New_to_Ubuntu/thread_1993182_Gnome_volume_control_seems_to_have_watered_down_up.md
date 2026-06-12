---
title: "Gnome volume control seems to have watered down update"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by TheManno1 on 2012-06-01
I am on ubuntu lucid 32 bits and I recently did sudo update or whatever you call it in the terminal and my gnome volume control seems to have watered down. There are no options to set the volumes for different application and I can only increase the volume to a maximum of 100% rather than 150%

---

### Post by TheManno1 on 2012-06-01
I am trying to do something similar to this  [http://news.softpedia.com/news/How-to-Replace-the-Volume-Control-in-Ubuntu-9-04-with-the-PulseAudio-One-112786.shtml](http://news.softpedia.com/news/How-to-Replace-the-Volume-Control-in-Ubuntu-9-04-with-the-PulseAudio-One-112786.shtml)  except for lucid and I don't know how.

---

### Post by TheManno1 on 2012-06-03
Bump.

---

### Post by Senior_Buckethead on 2012-06-04
[http://news.softpedia.com/news/How-to-Replace-the-Volume-Control-in-Ubuntu-9-04-with-the-PulseAudio-One-112786.shtml](http://news.softpedia.com/news/How-to-Replace-the-Volume-Control-in-Ubuntu-9-04-with-the-PulseAudio-One-112786.shtml)

After reading the article and your question, So the question that you are wanting answered is how to replace the asla sound river with the pulse sound driver..?

The first things that I notice is that the instructions are for 9.04, so they are way out of date.

I don't know if this is technically possible still, I leave it upto one of the much more experienced members to help you with that.

---

### Post by TheManno1 on 2012-06-06
bump

---

### Post by blackbird34 on 2012-06-06
You are attempting to replace the ALSA sound menu (the ugly looking one) by the PulseAudio one (the nicer looking one) you had before, as far as i can tell. 
I'd suggest navigating to /usr/share/applications and looking through the list to see if you don't find something along the lines of "PulseAudio Volume Control", which should be what you're looking for.  I believe there are several sound control interfaces in Ubuntu. (don't ask why.... )

---

