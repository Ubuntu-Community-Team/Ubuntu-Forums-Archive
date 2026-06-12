---
title: "Mythtv and a Server"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by batty on 2008-08-25
I have a Ubuntu Hardy server up and running, works a treat!
I have Kubuntu on my main PC, under remote places I have a icon setup for my server.
One click and I can browse all my servers files (I was well impressed to get this working :) )

Mythtv, frontend and backend is running perfectly on my main PC, my Ubuntumyth frontend downstairs can see it .

Now the question.

How can I make my mythtv see the files on the server. I don't seem able to make mythtv have access to the server automatically.
I've tried putting IP adress of server and folder into mtyhtv file location but no success 

Dave

---

### Post by Thelasko on 2008-08-25
I'm far from a MythTV expert.  I don't even use it.  From what I do know about it, I think the backend is supposed to be on the server for it to work.

There is likely other ways to get it to work.  But that seems the easiest.

---

### Post by dannyboy79 on 2008-08-25
> **Thelasko said:**
> I'm far from a MythTV expert.  I don't even use it.  From what I do know about it, I think the backend is supposed to be on the server for it to work.

I also think you can only have one backend on your network, but you can have multiple frontends.

you can have multiple backends but one is the Master Backend and the other's a slave backends.

I am not sure what the OP is asking here. Is he saying he wants his mythtv frontend to be able to view movies and files from a server that isn't even running mythtv?

---

### Post by Thelasko on 2008-08-25
> Is he saying he wants his mythtv frontend to be able to view movies and files from a server that isn't even running mythtv?
That's how I read it.

Thanks for immortalizing my mistake by the way. :)

---

### Post by fenian on 2008-08-25
First you need to set the computer with the mythfrontend up to automount the directories on the server.Next on the frontend you will want to make links to the mounted directories in the directories you have set up for myth to look for audio or video files.

---

### Post by batty on 2008-08-25
> **fenian said:**
> First you need to set the computer with the mythfrontend up to automount the directories on the server.Next on the frontend you will want to make links to the mounted directories in the directories you have set up for myth to look for audio or video files.


Can you explain that in a little more detail.
It's the auto mounting bit I need help on.

Cheers Dave

---

### Post by dannyboy79 on 2008-08-25
> **batty said:**
> Can you explain that in a little more detail.
It's the auto mounting bit I need help on.

Cheers Dave
when you made the comment that your main computer is runnning Hardy, you're also saying that you have mythtv backend and frontend set up on it correct? well on the backend you need to enter an it's ip address instead of 127.0.0.1. then on the frontend downstairs, you need to enter the ip address of the backend you want it to look at. I use the /etc/hosts file to make all my machines have static ips, it was just easier for me instead of using a WINS or DNS server. Then you watch everything through mythtv frontend that's downstairs. here's a link for setting up a seperate frontend.
[http://www.mythtv.org/wiki/index.php/Mythfrontend](http://www.mythtv.org/wiki/index.php/Mythfrontend)
also here's an ubuntu guide for setting up mythtv
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)
then just pick Gutsy, it should be the same I would think.

---

### Post by fenian on 2008-08-25
I use cifs to mount shared volumes from my server.Instructions on setting this up can be found [here]("http://ubuntuforums.org/showpost.php?p=1686695&postcount=1")

---

