---
title: "socket/shoutcast programming"
date: 2006-05-16
forum: Programming Talk
---

### Post by Grey on 2006-05-16
Hi everyone.  I'm trying to develop a simple internet radio client, and I'm having a great deal of difficulty.  Mainly because I've never done any audio programming before, and I've never done any network programming before... but I've been trying to wrap my head around it all.

I've been able to connect to the shoutcast stream through a little bit of packet sniffing and advice from this thread here:
[http://forums.radiotoolbox.com/viewtopic.php?t=74](http://forums.radiotoolbox.com/viewtopic.php?t=74)

As a result, I can connect to the stream, and I thought I was getting the mp3 stream... but it just plays as garbage when I try to play it with a conventional mp3 player, such as xmms.  I have attached the source code for my test applet that I sync to my main code base every now and then (I use libmad to play the MP3s).

I run it simply by running it like "./client > test.mp3".  Then I play the resulting mp3 in xmms.  At first I thought it was due to the mp3 headers not being included, but then I realized that xmms was indeed picking up the vital statistics properly (32kb/s, correct sample rate, etc)... which kind of killed that idea.  But it still plays as garbage.  Which leads me to believe that I am misunderstanding something about how sockets work... can anyone please help me?

To output the mp3 data, I am doing this:

```

    while(1) {
    	numbytes=recv(sockfd, buf, MAXDATASIZE-1, 0);
    	buf[numbytes] = '\0';
    	printf("%s", buf);
    }

```

---

### Post by Grey on 2006-05-16
Just a quick update on this...  I am currently poring over the xmms source code (anyone with a similar problem, I highly advise reading the http.c code in either the mpg123 plugin or the vorbis plugin.).  So don't stress over this too much.  :)  I'm thinking about largely rewriting my network code using wholesale copy/paste from the xmms source code rather than reinventing the wheel.  (Both are GPL, so no biggie).  As I am just learning right now, and haven't cleaned up that code too much yet anyway, it seems to be the sane solution.

Anyways, thanks for reading this anyway.  And I hope it helps you if by some strange coincidence, you are working on a similar project.  And just for the record, this is hopefully going to turn into an internet radio client for the Nintendo DS in the next few days (assuming I can work out my performance issues... TCP seems to be quite slow right now).  If you are interested, check out [my personal website](grey.homelinux.org).

If you have ever done any of this sort of programming before, I would appreciate a few words on why my solution didn't work.  (As I said, I am still learning).

---

