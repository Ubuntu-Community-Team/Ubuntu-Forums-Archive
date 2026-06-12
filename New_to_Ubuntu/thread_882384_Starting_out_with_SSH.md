---
title: "Starting out with SSH"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by moolcool on 2008-08-06
Hey
I'm looking to start playing with SSH. I have Hardy Heron on my laptop and XP on my laptop. I tried the tutorials to set up a server but my computer doesn't let me edit the config file. My question is how do i edit the file, how do i set up that whole public key thing and what can I do with it once its up?

---

### Post by Yuki_Nagato on 2008-08-06
I have no clue how to SSH from Linux into Windows, but if you want to SSH from Windows into Linux, you will need to use "puTTy."

_[http://www.chiark.greenend.org.uk/~sgtatham/putty/faq.html]("http://www.chiark.greenend.org.uk/~sgtatham/putty/faq.html")_

This is their FAQ.


Check out this thread.  Post #2 was a KILLER response.

_[http://ubuntuforums.org/showthread.php?t=873275]("http://ubuntuforums.org/showthread.php?t=873275")_

---

### Post by moolcool on 2008-08-06
Great help! but im still not sure as to how to set up the server on the linux end. I did the whole "sudo apt-get install ssh-server" and it worked but as for doing stuff like getting the settings in order, what port to use and how to set up the public key encryption I still need some help.

---

### Post by cozmicharlie on 2008-08-06
I found winsshd to be much easier to set up than putty. 
[HTML]http://www.bitvise.com/tunnelier
[/HTML]
It is really very easy to set up ssh in Ubuntu - this should help 
[HTML]https://help.ubuntu.com/community/SSHHowto[/HTML].

This is also a good discussion on both setting up and security.
[HTML]http://ubuntuforums.org/showthread.php?t=596917&highlight=ftp+server[/HTML]

---

