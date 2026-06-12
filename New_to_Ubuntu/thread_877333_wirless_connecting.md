---
title: "wirless connecting"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by windows hater on 2008-08-01
hello i have set up a wireless network but every time some one connects via a ps3 in the house i get booted from both computers and ps3 both laptops are ubuntu is this an issue with the network or computers or possible the ps3

---

### Post by bobnutfield on 2008-08-01
Are you saying that when you are on the network with your computer, you knocked off the network when someone starts a PS3 connection?

Not sure I fully understand your questions.

---

### Post by windows hater on 2008-08-01
yes exactly

---

### Post by windows hater on 2008-08-01
both computers work fine up until you add a ps3 in the mix

---

### Post by phidia on 2008-08-01
I assume the PS3 is being used to play online? It may be taking your bandwidth when it does. You need to be able to monitor your network, I think, to see exactly what's happening. Maybe [this page]("https://help.ubuntu.com/community/WifiDocs") has some useful info?

---

### Post by windows hater on 2008-08-01
is there a way i could limit it or do something because i'm very tired of getting booted off all the time

---

### Post by windows hater on 2008-08-01
i'm starting to believe its the ps3 buddy just came over and connected hes 360 and both laptops worked fine

---

### Post by bobnutfield on 2008-08-01
Is your router set up with DHCP or static ip addresses?

---

### Post by windows hater on 2008-08-01
just dhcp no static

---

### Post by phidia on 2008-08-01
After the connection drops open a terminal and enter > dmesg
That should tell us something.

There is a question (unanswered) on doing what your asking bandwidth throttling [here]("http://ubuntuforums.org/showthread.php?t=785829&highlight=throttling").

---

### Post by bobnutfield on 2008-08-01
If you are using DHCP, then I blieve phidia has the answer.  I have a PS3 and when it is online, the other computers still connect, but their connection speed is halved.  I have never seen a solution to this (though one might well exist).  I simply resolved to leave the PS3 off when I need to be online.  I know that is not a solution for you, but you might take a look around Google as there is plenty of information about this type thing.

---

### Post by phidia on 2008-08-01
Note: I edited/added to my last post here-there are questions about doing throttling of bandwitdth but no real answers that I saw unfortunately.

---

