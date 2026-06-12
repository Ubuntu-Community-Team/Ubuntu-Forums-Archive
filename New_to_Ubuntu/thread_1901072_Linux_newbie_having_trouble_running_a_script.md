---
title: "Linux newbie having trouble running a script"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by Shempster on 2011-12-27
I've got a new install of Ubuntu 11.10 32 bit & I can't get a script file I downloaded to run.  The file is a Twonkyserver script file to run & install Twonkyserver. I have downloaded the file several times, so it's not a damaged file.

I am the only user on this machine & log-in automatically.  When I double-click the file gedit opens with nothing in it's window & just sets there. I have moved to the donwload folder where the file is in the terminal, logged in as root and then typed:

sh twonkymedia-i386-glibc-2.2.5-6.0.38.sh

then hit enter and I get sh: can't open twonkymedia-i386-glibc-2.2.5-6.0.38.sh

Other similar attempts through the terminal normally end up with a “file not found” among other returns.

Also, can I rename this script to something short to help reduce the chances of a syntax error?

I've emailed Twonky support, but haven't heard back from them yet. Can someone please help me get this script run?

Thanks

---

### Post by oldfred on 2011-12-27
Welcome to the forums.

I know nothing about Twonkyserver.

But you have to change permissions to make it executeable and then run it as sudo bash.

I normally use Nautilus and just check the box for execute permissions.

# cd to the folder where you have twonkyserver
chmod a+x twonkyserver
sudo bash twonkyserver

---

### Post by Shempster on 2011-12-27
> **oldfred said:**
> Welcome to the forums.

I know nothing about Twonkyserver.

But you have to change permissions to make it executeable and then run it as sudo bash.

I normally use Nautilus and just check the box for execute permissions.

# cd to the folder where you have twonkyserver
chmod a+x twonkyserver
sudo bash twonkyserver

Thanks for the reply.  I would imagine that a script is a script is a script.  I've tried the chmod stuff you mention but not the execute permission.  I'll try all this when I get back to the PC.

Thanks again.

---

