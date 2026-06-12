---
title: "Computer goes into sleep mode on its own."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by whoscheesemine on 2008-09-16
Okay, so I have two Sony VAIO PCV-J150's. Both computers are running Xubuntu 8.04. One machine is in my brother's room and runs fine. I never once encountered a single error on it. *Mission: Xubuntu Accomplished;)* However, the one that's currently in my room is receiving an odd error I've never encountered before. I suppose this would be a good time to ask what command to type in the terminal to bring up like a.... log report I presume? Anyways, whenever I go to certain websites, for example, the first time I run [www.ubuntuforums.org](www.ubuntuforums.org), my computer screen goes black. I see a little flashing underscore and then my computer goes into sleep mode. Whenever I awaken it everything resumes as it was, but i do that that little error that all the Laptop and Thinkpad users are getting that says: "Action forbidden: policy timeout is not valid please wait a few seconds and try again."

Now, I'm not sure what may cause this, but I will give a list of links that cause this error to occur. I would have done this ahead of time, but I had it happen while I was typing this the first time, and it logged me out of the page and I had to type this all over again, so we'll save that for an edit.

[COLOR="Red"]**Edit #1:**[/COLOR] Okay, so now I can't seem to find a page that does it. The only one's I know of are some images I was looking at earlier today that would not be appropriate for posting the links of on this forum. I would be happy to PM a link to anyone, KEEP IN MIND THIS IS STRICTLY FOR GETTING TO THE ROOT OF MY COMPUTER PROBLEM. I know that countless times I have come accross other pages, of adequate taste, that do it as well, but my memory is currently failing me. As SOON as I come accross another page that does it I will immidiatly edit.

[COLOR="Red"]**Edit #2:**[/COLOR] Okay, so I had downloaded a .rtf document from my professor as it was a quiz I had to take. It was multiple choice so I just deleted the answers that weren't right for a nice clean paper to turn into class today. I finished doing so and saved it as a new document, which caused my computer to go into sleep mode once again. As a scientist (lol), I decided to experiment a little bit with this to give the experts a little bit more data to work with. After doing so, I then tried to save the document as it was, but not as a new document. In other words rather than using "save as" as I did before I used "save". The computer did not go into sleep mode. I then tried save as again, this time just changing one character in the title, and once again it did not go into sleep mode. This leads me to beleive it may have something to do with power? I know that saving a new document uses more electricity than saving it as its own document, and I beleive, althought not certain, that it would take less electricity to save a new document of a document that had already been previously save under a new name. I hope this helps to get to the root of the problem. Once again if I come accross anything that puts it in sleep mode again, I will report. Perhaps, if I have time tonight, I'll swap the power supply with something a bit stronger to see if the error persists to further my hypothesis about the power issue. However I would like to point out that I'm pretty sure this computer is completely in stock condition from when I received it from my father. Now, he may have at one point in time put another PSU in it, but we'll find out. I suppose I could compare it with my brothers to make sure.

---

### Post by scorchgeek on 2008-09-16
Silly question: Are you sure that the problem isn't caused by power save settings?

---

### Post by whoscheesemine on 2008-09-17
No, I'm not sure at all. I'd definitely willing to give it a try though. Where can I access this at?
[B]
[COLOR="Red"]EDIT #1:[/COLOR][/B] Okay, well yesterday I looked around once I got some free time and found the power management preferences. I do know that in one of the latest updates there was either an update to this utility or this is a new one. I don't know for a fact, because I've never messed around with it except for my laptop which is running Ubuntu 8.04 and I beleive its different on there. I'd check for you if the hard drive in my laptop would show any signs of conducting electricity lol. That's another story, anyways if anyone happens to find this topic and is looking for a solution. What I did was change two things. I suppose on a scientific level I should have changed one, waited awhile and seen if that fixed it, but I'm running on limited time so this worked sufficient enough. On the "ON AC POWER" tab I changed the automatically go into sleep mode from the default of 40 min and changed it to never. On the "General" tab I changed the drop down box next to "when sleep mode button is pressed" to "Do Nothing" rather than the default of "Suspend". Now I'm no expert, but I'm assuming that what's happened is some kind of miscalculation in coding is sending a signal saying that the suspend button has been pressed when it hasn't. I'm not sure the steps to take to report this problem so that Canonical can take care of this, but I predict this issue coming up more and more. Although, it could have been alot of more simple things. Perhaps the sleep button on my keyboard has a problem with it. I suppose if I get some more free time I'll experiment a little bit and see what I can find. Tootles!

[COLOR="SeaGreen"]**PS:**[/COLOR] I haven't put this topic as solved for a reason. I don't know exactly what caused the error and if read, you'll notice I am looking for a little feedback on some subjects. If I'm violating forums rules I apologize. Just give me a lil whack on the head and say "NO!">:O

[COLOR="SeaGreen"]**PPS:**[/COLOR] Thanks scorchgeek for helping me to realize that I should always check where my first suspisions are rather than jump at the more complicated ones. I suppose when in doubt one should follow the KISS example. (Keep It Simple Stupid)

---

