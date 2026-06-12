---
title: "I lost the sound on ubuntu after attempting  a change with the  &quot;Sound&quot; ap"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by Tom_Carr on 2013-08-03
I am running ubuntu 12.04.
I wanted to raise the volume for a youtube video that was hard to hear even with sound set to max and speakers turned up to max.  
I went to dash home and typed in "Sound".  There was a sound application and I opened it.
Under the Output tab, digital output, I moved the output bar at the bottom to the right of 100%.
I tried the youtube video again and there was no sound at all.  I moved the output bar at the bottom back to 100%.  Still no sound.
I tried other videos.  I tried rebooting.  There is now no sound on anything on youtube or netflix.  There is sound when I boot up, it makes the normal ubuntu boot sound when it opens the screen for me to enter a password, but that is the only sound I can get.

How can I fix this a get the sound back?

---

### Post by Vladlenin5000 on 2013-08-03
Make sure the correct output is selected in "Sound Preferences" (from your volume icon menu or in the system settings).

---

### Post by Tom_Carr on 2013-08-03
> **Vladlenin5000 said:**
> Make sure the correct output is selected in "Sound Preferences" (from your volume icon menu or in the system settings).

I did not change it.  It is set to "Digital Output (S/PDIF) Built in audio"

That was in the system settings for sound.  How do I get to the volumn icon menu?

---

### Post by Vladlenin5000 on 2013-08-03
> **Tom_Carr said:**
> I did not change it.  It is set to "Digital Output (S/PDIF) Built in audio"

That was in the system settings for sound.  How do I get to the volumn icon menu?

*Probably* that's the problem... You may need to select an analog output. How do you get to the volume icon menu? Well, maybe clicking on that icon that you must have in the top bar near the clock (if you're using the standard Ubuntu that is) and the same is available in the system settings of course.

---

### Post by Tom_Carr on 2013-08-04
> How do you get to the volume icon menu? Well, maybe clicking on that  icon that you must have in the top bar near the clock (if you're using  the standard Ubuntu that is) and the same is available in the system  settings of course.

Thanks.  I see it.  It takes me to the same sound settings I get to from the system settings menu or the Dash.

> You may need to select an analog output.

There is no analog output in the list, only "Digital Output" and "Headphones".  
If you think I should try adding an analog output I will.  How do I do that if it is not already in the list?
And remember that it was working just fine before I opened it the first  time and changed output volume at the bottom, which I have now changed  back.

---

### Post by calltheninja on 2013-08-04
I had a similar problem some years ago. Try running the command alsamixer, it could be one of your mixes is muted.

---

### Post by Tom_Carr on 2013-08-04
I did alsamixer.  I wasn't sure what I was looking at so did a screenshot.  I tried to paste it here but that didn't work.  How do I paste a screenshot into a message here?  Do I need to edit it and make it smaller?  If so, what tool do I use to do that?

---

### Post by Tom_Carr on 2013-08-04
I tried to paste in the image and got the garbage above.  How do I delete it?

---

### Post by coffeecat on 2013-08-05
> **Tom_Carr said:**
> I tried to paste in the image and got the garbage above.  How do I delete it?

You triggered a firefox bug by dragging and dropping the image into the message editor and ended up with base64 code. That's not the way to add images. Please use the "Manage Attachments" button under the advanced editor to upload your image and the forum software will create a clickable thumbnail.

Alternatively, you can upload your image to an image hosting service and paste the URL between [noparse][IMG] and [/IMG][/noparse] BBCode tags. But not too big if you do the latter please. Bear in mind those on slow internet connections.

---

### Post by Tom_Carr on 2013-08-05
coffeecat, thanks for your help.

Now back to my original sound problem.  Below is a screenshot of what I get when I run alsamixer.  Does this give any information about why I lost sound?



[ATTACH=CONFIG]245105[/ATTACH]

---

### Post by duan2 on 2013-08-06
I too have no sound at all from the getgo, I went into alsamixer and most of the things were "MM" so I changed it and rebooted and nothing.  I installed it dual boot and went into XP and had sound there so not sure what to look for

---

### Post by Tom_Carr on 2013-08-06
Do you have any idea how we could get help on this?  Apparently no one in this forum has an answer.  I had sound and lost it, so I guess I could reinstall the the operating system, but that would be a lot of trouble.  Is there any where else we could ask?  I would be willing to pay for tech support if I have to, but I am not sure how to do that.

---

### Post by Tom_Carr on 2013-08-06
I got an answer in this forum

[https://answers.launchpad.net/ubuntu/+addquestion](https://answers.launchpad.net/ubuntu/+addquestion)

The answer for my problem was:

> Try:

 killall pulseaudio; rm -r ~/.pulse*; clear; echo "Waiting 10 secs";  sleep 10; killall pulseaudio; rm -r ~/.config/pulse*; echo "Waiting 10  secs"; sleep 10; clear; echo "Reboot PC...."
 Copy it as ONE big command, when you get the reboot message, reboot when you are ready.

                                      





---

### Post by Tom_Carr on 2013-08-06
How do I mark this thread as "problem solved"?

---

