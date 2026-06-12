---
title: "Ubuntu 11.10 Empathy Webcam/Voice Chat"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by Drowz0r on 2011-10-26
Hello all
 
I'm using Ubuntu 11.10 and Empathy. It logs in perfectly and seems a lot nicer than other clients. I am only using it with my MSN (windows live) account so far.
 
However, I am only able to open voice or webcam chats with certain people
 
All: Only text
Some: Text or voice
Very rarely: Text, voice or webcam
 
This seems a little odd as on MSN I was at least able to send voice or webcam to everyone (while I was on windows).
 
I find this is the same on any of the ubuntu machines I use (I have 5 machines recently formatted and 11.10 installed on them).
 
The webcam and mics work perfectly in other applications. Sometimes I am able to open a webcam chat with someone but they cannot see me but I can see my preview.
 
Any ideas guys?

---

### Post by Drowz0r on 2011-10-26
If no one has a fix are there any alternative programs that basically do what empathy does without the webcam/mic issue?

---

### Post by Drowz0r on 2011-10-29
No one had a similar problem guys?

---

### Post by CJ-1990 on 2011-11-08
G'day dood :)

I have the same problem with AMSN atmoe, it's not because of faulty soft or hardware, but of MSN not letting AMSN or any other linux MSN equivalent connect to a certain network it needs to use voice and/or video chat... And apparently it's not going to be fixed for quite a while... Your best bet is to somehow install actual MSN onto your linux computer... Though I don't know how :)

CJ

---

### Post by Drowz0r on 2011-11-08
> **CJ-1990 said:**
> G'day dood :)

I have the same problem with AMSN atmoe, it's not because of faulty soft or hardware, but of MSN not letting AMSN or any other linux MSN equivalent connect to a certain network it needs to use voice and/or video chat... And apparently it's not going to be fixed for quite a while... Your best bet is to somehow install actual MSN onto your linux computer... Though I don't know how :)

CJ

Oh darn. I does seem to randomly work with people sometimes. At the moment though, myself and others on ubuntu are unable to log into MSN at all!

I suppose getting the actual MSN on my Linux box would solve it... but this may take some fiddling.

Thanks for the feedback duuuder.

---

### Post by mtrento on 2011-12-17
Here is what i found on the empathy FAQ:

[http://live.gnome.org/Empathy/FAQ#For_which_protocols_does_Empathy_support_audio_and_video_chat.3F](http://live.gnome.org/Empathy/FAQ#For_which_protocols_does_Empathy_support_audio_and_video_chat.3F)

> Currently for SIP/XMPP/Gtalk. MSN support is currently broken due to change Microsoft has done to their server, see [this blog post]("http://kakaroto.homelinux.net/2010/03/amsn-0-98-2-to-be-released-without-audiovideo-support/") for more detail 

Microsoft forced everyone to upgrade to the latest version of Windows  Live Messenger : WLM 2009 which uses MSNP18 and has the ability to do  Audio/Video calls through a tunneled SIP (P2P SIP messages, not using an  external SIP server) and so, they realized that their SIP servers  aren’t being used anymore, so they had this great idea of shutting down  their servers… the result? aMSN can’t do Audio/Video calls because the  SIP server refuses our connections.
 Now we have two choices, either use MSNP18, or disable SIP calls  completely. Obviously, we can’t move to MSNP18 at the moment, because  MPOP support isn’t really ready yet, and because MSNP2PV2 hasn’t been  implemented, so we had to remove the Audio/Video support in aMSN SVN for  now, and only have it available for those who are brave enough to try  out MSNP18.


i am still looking for a simple solution to video/audio chat between two ubuntu pc.
cheers

---

### Post by Drowz0r on 2012-01-15
Well after some testing I can't seem to video chat in empathy through:

MSN
Facebook
Google Talk

However I could talk to these people fine with webcam from:

MSN from Windows
Skype on Ubuntu
Skype on Windows

I don't get it.

---

