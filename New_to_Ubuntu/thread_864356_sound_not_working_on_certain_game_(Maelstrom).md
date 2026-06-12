---
title: "sound not working on certain game (Maelstrom)"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-07-19
Hi all,
I really like the game Maelstrom I've been been having issues with the sound that have been driving me nuts.  I can hear the sound in the background, but there is this really annoying buzzing noise in the foreground.
The strange thing is that none of my other games have this problem.
I was hoping that downloading the source and creating  a .deb package cure the problem... It didn't (see [http://www.metalshaperman.com/?p=47]("http://www.metalshaperman.com/?p=47") if anyones curious).

I posted this question once before... Apparently no one else has had this issue.  I tried emailing the guy who created the package..  No answer...
Soo... I guess my only other option is to try to isolate the code section and try figure it out from there..
I don't mind this, since I'm trying to learn C++ anyway... but life is sort of short... Does any one have any other suggestions before I start tearing into source??

I went faq to the maelstrom and found that it uses "Simple DirectMedia Layer" site which eventual pointed me here:
[https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567")
Not quite there yet but getting closer.

---

### Post by KJ55 on 2008-12-25
I know that this post is 6 months old, but the solution for anybody having this problem can be found here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I was having the exact same sound problem with the Maelstrom game on Hardy 8.04, and I followed psyke83's outstanding How-To in the above sited URL for PulseAudio Fixes & System-Wide Equalizer Support.  And, sound now works properly in Maelstrom.:)

---

### Post by Jonas thomas on 2008-12-26
> **KJ55 said:**
> I know that this post is 6 months old, but the solution for anybody having this problem can be found here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I was having the exact same sound problem with the Maelstrom game on Hardy 8.04, and I followed psyke83's outstanding How-To in the above sited URL for PulseAudio Fixes & System-Wide Equalizer Support.  And, sound now works properly in Maelstrom.:)

Well, it took care of the buzzing sound at least... Now I have no sound at all..  But at least I have somewhere to ask about how to fix that.
Thank you so much for giving me the heads up on this.  I love that game as haven't really played it since I upgraded from Feisty..

---

### Post by KJ55 on 2008-12-26
> **Jonas thomas said:**
> Well, it took care of the buzzing sound at least... Now I have no sound at all..  But at least I have somewhere to ask about how to fix that.
Thank you so much for giving me the heads up on this.  I love that game as haven't really played it since I upgraded from Feisty..

I'm sorry you're still experiencing a problem with the sound on the Maelstrom game after following the How-To I referred you to.

I, like you, was previously experiencing the annoying buzzing sound in the foreground and the barely audible game sounds in the background (on Hardy 8.04 32-bit).  I followed the referenced How-to, and the sound problem was fixed with the Maelstrom game.

I would recommend you follow the troubleshooting guidance provided in the How-to by posting the results in that thread the following:

```
$ aplay -l
```

and 

```
$ pkill pulseaudio; sleep 2; pulseaudio -vv
```

in addition, to the the problem application.


Also, try to limit the variables; e.g., use only the updated fix files for PulseAudio (for Hardy) in psyke83's PPA (Personal Package Archives).


Hopefully, you will fix the sound problem with the Maelstrom game.  Best of luck!

---

### Post by Jonas thomas on 2009-03-11
Yah know,
I ran through the link that you provided a couple of weeks ago and I for what ever reason, it works know.  My suspision is clarified intructions and fixes that have been deployed through synaptic. Program no longer appears to be a problem...

---

