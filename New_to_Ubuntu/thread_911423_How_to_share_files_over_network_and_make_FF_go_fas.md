---
title: "How to: share files over network and make FF go faster!"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by dhinderliter on 2008-09-05
I am used to IE on Vista going alot faster than this FF seems to go. It takes 2x a long to load a page and about 30-40% of the time it will load like dial up (i.e. brings up boxes instead of pictures and then loads as it goes). i mean of course its faster than dial up its just that my IE/vista never did this. it was almost instantaneous to open a browser whereas FF takes 2-4 even 6 or 7 seconds to bring up a page and load it. No i have not changed my internet at all. Is there something "trick" that ie/windows does to accelerate and this is more like true speed or what?

when i rightclick to share and installed the package and then allow users to write to folder here is the error i get

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share

i am the admin and i haven't a clue what to do! it already asked me for my password!

eta: got the shareing to work

---

### Post by jbrown96 on 2008-09-05
What versions of IE and Firefox are you using? You can find this in the help-->about of both programs. 
You can try to disable ipv6 in firefox. If you type about:config in the address bar and then search for ipv6. find the network.dns.disableipv6 line and double click on it to change the boolean value to true. restart the browser and see if this helps the speed. I can't think of another reason for the problem.

Sharing
Are you trying to share files from another computer to the Ubuntu computer or from Ubuntu to another computer?
If you are getting the files from another computer, you should be able to find them in Places-->network.
If you need to share files to other computers, you will need to find a guide to setup Samba file sharing.

---

### Post by dhinderliter on 2008-09-05
ff is 3.0.1 and i downloaded the newest IE one or 2 days ago. i think they are up to version 8 now? even on 7 on my other laptop it was alot faster though. 

is removing that file easy? 

i want to share files both ways. in my network it shows "windows network" and i click that and theres nothing there. i know the other computers have folders that are shared right now so i don't know where they are. 

i'll try searching for a samba guide.

---

### Post by HermanAB on 2008-09-05
A slow internet connection is usually due to a bad DNS configuration.  Compare /etc/resolv.conf to the WinXP settings.

Cheers,

Herman

---

### Post by plucky on 2008-09-05
> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share


This is a known problem.See this [thread for a workaround](http://ubuntuforums.org/showthread.php?t=772706)


Good Luck

---

### Post by jemate18 on 2008-09-05
for that error in that samba thingy.. I just restarted my PC and boom (after booting) it workss.....

---

### Post by dhinderliter on 2008-09-06
> **HermanAB said:**
> A slow internet connection is usually due to a bad DNS configuration.  Compare /etc/resolv.conf to the WinXP settings.

Cheers,

Herman

ummm.i don't know what that means. how do i do that? 

i had to comepletely reformat my ubuntu partition. trying to install samba through the terminal was NOT a good idea for me. I am staying away from the terminal for large tasks for quite a while now. i finally got shareing to work although i didn't DO anything except apt-get nautilus which it said it already HAD it and didn't install anything and then i logged out/in and i was able to share. ok fine with me as long as it works and no samba! :)

however i now can't figure out for the LIFE of me to get my internet to connect automatically. i can log it in manually each time i boot up pretty quick but i don't know why it won't save it. i've gone into the netowork through admin and tried to save the file but its like it doesn't remember it has until i go and try to reset it up and then just as i enter my info to get a new connection it finds the old one. :confused:

---

### Post by hyper_ch on 2008-09-06
did you disable IPv6? That's often a cause for slow internet connections.

---

### Post by hyper_ch on 2008-09-06
P.S.: It's also adviced to make seperate threads for unrelated issues. so that each one can be solved independantly.

---

### Post by dhinderliter on 2008-09-06
> **hyper_ch said:**
> did you disable IPv6? That's often a cause for slow internet connections.

uh....no i guess not. i don't know what THAT means either. :)

---

### Post by hyper_ch on 2008-09-07
> **dhinderliter said:**
> i don't know what THAT means either. :)
You can easily find out.

---

