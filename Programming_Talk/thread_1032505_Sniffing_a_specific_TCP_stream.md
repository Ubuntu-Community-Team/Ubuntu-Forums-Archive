---
title: "Sniffing a specific TCP stream"
date: 2009-01-06
forum: Programming Talk
---

### Post by mohamedafattah on 2009-01-06
Hey all,

I was trying to sniff a specific TCP stream that is characterized by the source host and the source port.

Getting to the packets level, I reached this command:

sudo ngrep -x -d wlan0 \( tcp\ src\ port PORTNO and src\ host IP \)

But I am afraid this gets me the stream packet by packet. If anybody used Wireshark/Ethereal and tried the "Follow TCP Stream" functionality, he then knows what I need. All I need is the TCP stream itself, with the packets being in order, and with no unnecessary repeated packets (for errors). I want to have that functionality of following TCP streams in a programatically friendly way. Does anybody know any clue for this?

Thank you in advance,

---

