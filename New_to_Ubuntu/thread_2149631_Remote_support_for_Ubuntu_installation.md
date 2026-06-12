---
title: "Remote support for Ubuntu installation"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by marqrdt on 2013-05-29
Hi!
   I'm a long-time Ubuntu user and advocate and I have a technical developer/sysadmin background. About 7 years ago, I gave my father-in-law a MacBook so he could stay in touch with us. We Skype with him every day and it's kind of his lifeline to us and the rest of his world-- online news, soccer, etc. It bit the dust last week (repair cost > value). Rather than just buy him another Mac, I thought Ubuntu would be really valuable for him-- it's easy, clean and sturdy. I created a Ubuntu laptop for him on a nice Lenovo Essential (I'm posting to this forum with it). The network switches seamlessly between wireless and ethernet, as he prefers to use it as his desk. I have his wireless network already setup on it. I installed it in Romanian, as his English is limited, especially with tech terms. He's super-intelligent and can make pretty much anything using a blow-torch, a saw and a hammer. But, he doesn't have alot of computer experience.
   Here's my question: What are some techinques and strategies to make it unbreakable and to maximize his experience? I want a minimum of surprises. He needs Firefox and Skype-- that's about it. Also, any ideas on remote support (SSH, VNC or anything more user-experience related) would be really helpful. I setup an Ubuntu One account for him and thought that I could create a parallel user on my Ubuntu machine and help maintain his desktop. Anybody have any experience, yay or nay, with that?

   Bried soapbox moment: One of the really fantastic things about Ubuntu is that it can server any type of user, from developers and tech-heads to people need to read the news and communicate with family.

Thanks!

Paul

---

### Post by 2F4U on 2013-05-29
Ubuntu already comes with a remote desktop solution, which you can use:

[http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/)

There is other software available:

[http://www.liberiangeek.net/2012/04/list-of-remote-access-support-software-for-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/list-of-remote-access-support-software-for-ubuntu-12-04-precise-pangolin/)

If I were you I would also configure ssh access, just in case something goes wrong with the GUI.

---

### Post by Old_Grey_Wolf on 2013-05-29
I learned over time that I needed both VNC and SSH when I maintained the computers remotely for my three grandchildren. I put the computers together from things I had collected over the years. I did find VNC to be very slow and mostly used SSH. I only used VNC when I had to see the DE to troubleshoot a problem.

You should harden both VNC and SSH. There is an old sticky in the Ubuntu forums Security section worth reading [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).

You should also decide it you want him to be able to install software and updates. If not then don't give him admin privilege.

If he is connecting by wireless then I know he is a router/switch/modem or something similar. I assume you know you will need to configure port forwarding.

---

