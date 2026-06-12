---
title: "How-To: Correct Simple Sound Problems with Ubuntu Out-of-the-Box"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Trafferth on 2008-11-19
Dear All,

I have noticed that quite a few people are having trouble getting sound to work with what should be supported drivers.  Before digging into advanced problem-solving techniques (see links at the end of this thread), a run through the following routine should eliminate anything simple.  I have had trouble myself getting and Audigy sound card on a desktop to work (the digital switch was incorrectly set) and on my laptop with Intel HDA sound (the PCM slider was muted).

So, the routine I generally suggest now is the following:

1. Double-click the volume control, select preferences, check all the boxes, go back to the volume control mixer, unmute everything, and turn all the volume controls up.

2. Look along the top of the mixer for a tab labelled 'Switches' or similar; make sure something weird like attempting to send digital sound to analogue speakers (or vice versa) isn't going on...

3. Right-click on the volume control, select preferences, and try a different playback device (there will probably be several to try).

4. Go to System > Preferences > Sound and try switching the devices shown in the drop-down boxes.

5. As a last resort, try using alsamixergui instead of alsamixer. You will need to fetch it from a terminal (open Applications > Accessories > Terminal) and type the following:

```
sudo apt-get install alsamixergui

```

(You will need to type your password here).  Then run alsamixergui

```
alsamixergui
```

Try unmuting all the channels from here.  Some people have reported that this works even though alsamixer itself does not.  Certainly worth a try.

If all the above fails, then the problem may be more complicated to solve.  I would check out the following threads:

The Comprehensive Sound Problems Solutions Guide:

[HTML]http://ubuntuforums.org/showthread.php?t=205449[/HTML]

Multiple Sound Solution:
[HTML]
http://ubuntuforums.org/showthread.php?t=843012[/HTML]

I apologise if the above information has been already posted elsewhere.  I simply noticed that people were asking the same sort of thing, even though these comprehensive guides exist on the forum.

I hope the above will be of some use.

Good luck!

Trafferth :)

---

