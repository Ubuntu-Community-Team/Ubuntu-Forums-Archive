---
title: "A doorman for my home network"
date: 2014-10-07
forum: Programming Talk
---

### Post by paign10.ln on 2014-10-07
Hello guys,

I'd like your opinion on the following matter. I have several projects running within my home network that I would like to access remotely. I have already done this, though my concern now is that they are publicly available and I'd like to keep them private.

I want to build a server that would ask for user authentication and then provide access to everything else. So, everything will be hidden behind this server. (I'd also like this to be an excuse for me to look into node.js, so any comments in this direction would be really appreciated.)

Currently I have no clue on how to approach this. Please advise. Even simple keywords for things to look for would do the job.

Regards,
Nick

---

### Post by TheFu on 2014-10-07
If your network fu is weak, as it sounds, start with ssh-tunnels.  These are easy and provided you do NOT use passwords, install fail2ban and disable all public facing services except ssh, it is highly secure.

Or ... you could setup openvpn, which is non-trivial.

Or ... you could setup x2go client/server which uses the NX protocol and remote into a desktop on your home network (using ssh tunnels) and do all the work that way.  x2go is very efficient for non-video needs. I've used it (actually FreeNX) from around the world. 

None of this has anything to do with node.js ... remote access doesn't.

---

### Post by paign10.ln on 2014-10-07
The projects I mentioned are serving web pages. And then I thought of using node.js, because I want to have a central interface to access them all.

The concept of VPN looks very appealing. Given the VPN, I guess I could have node, or whatever, serve a simple web page with just links to the individuals projects.

I don't know much to comment on any of the things you wrote, but you gave me enough information to start searching. Thank you for your answer.

---

### Post by TheFu on 2014-10-08
The main idea is to only have the ssh port open to the internet and only allow key-based authentication, not passwords.
There are many, many, many ssh how-to guides.  ssh is how UNIX admins work around the world.

If you are coming from a GUI-only background, it is hard to explain the power of ssh - it is amazing AND it is secure.

---

### Post by paign10.ln on 2014-10-08
No need to explain further. You gave me enough intuition... I'll figure things out.

Once again, thank you for your time :)

---

