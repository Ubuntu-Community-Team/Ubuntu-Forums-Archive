---
title: "Can't connect to Webmin"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by DanteDarkKnightDante on 2012-03-29
Hi all I'm a noob and I have a MILLION questions but I'll start with this one. I installed Webmin to my Ubuntu machine to possibly explore its ability to go headless with my Ubuntu server and when I type [https://[myservername]:1000/](https://[myservername]:1000/) I get the message "The server refused the connection" in my browser window. I tried connecting without the htttps just using http, no luck I've used the actual ip address, no luck. I've made sure the service is running. I don't know if I need to configure a file or firewall settings or what I'm stumped, UGH! I did mention I'm a noob didn't I? Any help would be greatly appreciated.

---

### Post by ccrs8 on 2012-03-29
Are you trying to connect from a second computer, or are you using your Ubuntu machine locally?  If you are trying to connect to webadmin from a second computer, you may need to first grant non-localhost access to webadmin.

---

### Post by Gone fishing on 2012-03-29
Try first from your local machine using the local IP address. Then if that fails are you using https or http? is Apache running is Webmin running?

---

### Post by lykwydchykyn on 2012-03-29
Don't know if you made the same mistake in the browser, but you need to connect to port 10000 (ten thousand) not 1000.

---

### Post by DanteDarkKnightDante on 2012-03-29
OK, I am totally lost now. I did make the mistake of entering 1000 instead of 10000 but when I made the correction, I still received the some error message.  I didn't know I needed Apache to run for Webmin is that true? Because I don't have Apache running. I have been trying to access Webmin from a second computer when you suggest trying it from my local machine you're talking about the Ubuntu machine correct? Ok I am able to connect from my local machine. It said something about the certificate not be trusted and asked if I wanted to proceed anyway which I did and I was able to connect. Now, what would be the problem that's keeping me from connecting from my Windows machine? Also, I installed TightVNC last night and was able to connect from my Windows computer but today I am not able to connect same goes for PuTTY. HELP!!!

---

### Post by DanteDarkKnightDante on 2012-03-29
Ok, I can now connect to Webmin from my second computer but only when I disable the firewall.  The firewall seems to be the problem with PuTTY and TightVNC also. I'm new so I just turned the firewall on last night after tinkering with Ubuntu for a week now. I had set up Samba and file shares, installed PuTTY, TightVNC and Webmin all before turning on the firewall and everything worked.  So I have now figured out how to allow the ports access through the firewall and I have access to all of the services previously mentioned. I'll mark this one SOLVED but I do have a question on how to enable a secure connection through Webmin and TightVNC i have SSH connection for PuTTY but I am not familiar with setting it up on the other two but I guess I can start another thread for that one. Thanks for all the suggestions. I'll see you guys on the next thread.

---

