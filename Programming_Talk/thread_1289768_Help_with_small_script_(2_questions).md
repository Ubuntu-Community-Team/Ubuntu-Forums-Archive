---
title: "Help with small script (2 questions)"
date: 2009-10-12
forum: Programming Talk
---

### Post by stallvalds on 2009-10-12
For now, I need to make a beep when running this script:

echo  \a "Soup menu "
echo  "============ "
echo  "(t)omato "
echo  "(b)ean "
echo  "(s)quash "
echo  "Select a soup... (q) to quit. "

I put the \a in, because it said it would make a beep in the echo man pages. It does not work, however. I will have to add if statements later to make it work, but I need to make a beep play when I run this first.

Also, I need to know how to make the program stop rinning. I will make an if statement to do so. So that when I press q, the program terminates. What do I need to add to the if statement to do this?

Sorry if this is noobish of me, but I'm just learning shell scripting. I'm using Bash by the way.
Thanks in advance

---

### Post by Gwasanaethau on 2009-10-12
I'm not sure about the second part, but for the first, you might need to change your first line to:
```
echo -e "\aSoup Menu"
```
The -e flag on echo turns on the 'C Escapes', like \a \n \e, etc.

---

### Post by stallvalds on 2009-10-12
Hmm. Just tried that ^ and still no beep. I re-read the man pages, and you are correct in that there needs to be a -e after echo. I know I'm close, but just can't figure it out.

---

### Post by Gwasanaethau on 2009-10-12
I had the same problem when I tried it before and I couldn't get it to work either – thought it would be worth a try though.

I'm afraid I can't be of any further help, sorry! :(

All the best with it, though.

---

### Post by stallvalds on 2009-10-12
Thank you for the help anyway. Much appreciated. Anybody else have any idea how the beep sound can be accomplished in my script?

---

### Post by stallvalds on 2009-10-12
My other sounds work ok, so I do not think this is a sound configuration issue. Probably just something wrong with my code. I have been at this for a couple of hours and frustration is setting in.

---

### Post by spillin_dylan on 2009-10-12
Keep in mind that

```
echo -e "\a"
```

is actually a beep from the PC internal speaker, NOT from your sound card, so there should be very little sound configuration involved.  I would check to make sure that the PC speaker is enabled and/or actually exists first.  Or maybe it beeps, but very quietly.  

I'm not exactly sure what specifically you need to look at there; I know there are posts regarding disabling the "system beep" in Ubuntu, as I did that on my laptop, but I don't have any exact references for you, though.

---

### Post by stallvalds on 2009-10-12
dylan- My computer is a laptop. A Dell Inspiron 1525. Thanks for pointing that out. I am not even sure it has a "system speaker". It has the internal speakers controlled by the sound card. Hmm..

---

### Post by kaibob on 2009-10-12
The echo command didn't work on my computer, either. There is a tiny command-line utility in the repo's called beep that beeps the pc speaker. It did work on my computer. No idea why the different results, but if nothing else works, you may want to give beep a try.

> Beep allows the user to control the pc-speaker with precision, allowing different  sounds  to indicate different events.  While it can be run quite happily on the command line, it&#8217;s intended place of residence is within shell/perl scripts, notifying  the  user  when something  interesting occurs. Of course, it has no notion of what&#8217;s interesting, but it&#8217;s real good at that notifying part.

---

### Post by stallvalds on 2009-10-12
kaibob, I will try that and report back.

---

### Post by unutbu on 2009-10-12
There is a package called beep which allows you to, um, beep.

The only problem seems to be that you need to be superuser to run it:
```

sudo beep
```

(Read the man page for an explanation why.)

Edit: Oops, kaibob beat me to it.

---

### Post by stallvalds on 2009-10-12
Kaibob and unutbu- I got the beep program from Synaptic. I run it with sudo beep and I can't hear anything. There are no errors when I run it, but it doesn't give me any kind of confirmation that it ram. It just goes back to the default command line. So, how does it run? Does it run like I described?

---

### Post by kaibob on 2009-10-12
On my computer, I simply run beep and the speaker beeps. The following command from the man page is a bit more prominent:

```
beep -f 300.7 -r 2 -d 100 -l 400
```

There is no confirmation other than the beep. The --verbose option does output some information: 

> $ beep --verbose
[DEBUG] 1 times 200 ms beeps (100 delay between, 0 delay after) @ 440.00 Hz

---

### Post by stallvalds on 2009-10-12
Kaibob- I tried the commands you gave me and nothing worked. I mean I think it worked, but I could not hear anything. I even installed a program from the reps that is supposed to transfer the beep to my main speakers and that didn't work either. I'm beginning to think there is a sound config problem. All this trouble to make one lousy beep. Probably not worth it. Having said that, I'm still open to suggestions :confused:

---

### Post by stallvalds on 2009-10-12
It says it worked when I use the --verbose argument. This is a configuration problem. Should I post this in a different forum?

---

### Post by kaibob on 2009-10-12
> **stallvalds said:**
> It says it worked when I use the --verbose argument. This is a configuration problem. Should I post this in a different forum?
You can request that the forum staff move the thread to another forum. Use the report post button if you want to do this.  

Depending on your setup, you may be able to use the aplay utility, which works through your sound card and regular speakers. To see if this will work, enter the following in a terminal window. Any WAV file will work.

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

The aplay utility is a bit overkill to simply get a beep or simple sound. Perhaps seeking configuration help in another forum would be best.

---

### Post by stallvalds on 2009-10-12
Yes kaibob, that worked. Thank you so much. I don't know if there's too much programming talk in here for the admins to move this post or not. We shall see.

---

