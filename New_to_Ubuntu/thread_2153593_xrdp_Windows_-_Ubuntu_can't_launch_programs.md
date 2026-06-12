---
title: "xrdp Windows - Ubuntu: can't launch programs"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by klintistwood on 2013-06-11
Hi all,

I recently ordered a VPS with Ubuntu 12 (64 bits) installed on it. I ordered this VPS to run remote browser based tasks.
I installed XRDP to be able to operate the server from my Windows computer. I followed the instructions, the installation went fine but I'm now facing a problem I can't solve.
When I connect to the Ubuntu workspace, I see the nice colored background, I see the icons on the left side, I can access the top menus but I can't launch any program.
If I click on Firefox, I see the icon flashing for a few seconds and then nothing happens. I have the same problem with any of the applications or features.

By Googling a bit around, I found other users in the same situation and the problem seemed to come from the desktop interface but I don't know how to force another desktop.
The full process is described here: [http://c-nergy.be/blog/?p=3518But](http://c-nergy.be/blog/?p=3518But) I can't do that as I can't execute any tasks from the desktop, I need a SSH method to do the same. The article suggest to create a .xsession file in the home folder, the problem
is that I don't see any home folder from the SSH connection and I don't know how to create a file.

Can anyone help me?

thanks
Laurent

---

### Post by klintistwood on 2013-06-11
Small update, I tried this:
echo "gnome-session --session=ubuntu-2d" > ~/.xsession 
but I don't any message from my terminal windows and when I connect through XRDP again, I see the same desktop and I have the same problem, programs don't start.

---

