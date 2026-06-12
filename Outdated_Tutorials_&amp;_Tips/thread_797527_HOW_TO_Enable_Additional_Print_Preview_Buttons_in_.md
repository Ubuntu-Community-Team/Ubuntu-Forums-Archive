---
title: "HOW TO: Enable Additional Print Preview Buttons in Firefox"
date: 2008-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by dwitkin on 2008-05-17
Before I moved to Ubuntu, I used Firefox on Windows XP and Vista. On those platforms, when you used the Firefox print preview function, several buttons were displayed in preview mode that allowed you to perform useful functions. These functions included:
[LIST]
[*]Changing the page orientation from portrait to landscape and vice-versa
[*]"Scaling" the size of fonts on the page based on a percentage of the original size, or by using a handy "shrink-to-fit" scaling option
[*]Printing the previewed page without the need to exit the preview first.
[/LIST]

When I moved to the Hardy Heron 8.04 version of Ubuntu, I noticed that these buttons were now absent. (They may also be missing in earlier Ubuntu versions, but I can't remember.) I missed these buttons. I wanted these buttons. These buttons saved me time.

Luckily, I've located the buttons. God bless useful buttons. In any case, by consolidating info from a few posts and following a few quick and easy steps, the buttons are now available to me. In case anyone else experiences the same issue, here's a quick step-by-step tutorial on how to make these print preview buttons appear:

[LIST=1]
[*]Open Firefox. 
[*]In the URL area (i.e., the bar that displays the internet address), clear the existing text and then type: "about:config" 
[*]If propmpted, click OK to by-pass the warning. 
[*]In the Filter field near the top of the page, filter for the phrase "print.while"
[*]Find the "print.whileInPrintPreview" option -- it may be the only one displayed. Double-click on the option to set it for true
[/LIST]

Now, when you enter print preview, you should see the buttons for page scaling as well as options for landscape and portrait page orientations.

Someone may want to suggest enabling these buttons by default in a future release of Ubuntu -- I can't see a downside to showing them by default. Until then, I hope this fix helps you as it has helped me.

---

### Post by GrantsV on 2008-05-21
Great tip!  Thanks for posting this.

---

### Post by dwitkin on 2008-05-21
> **GrantsV said:**
> Great tip!  Thanks for posting this.

Glad it was helpful to you. These HowTo pages have been a great benefit in helping me move to Ubuntu. Glad I'm able to contribute...

---

### Post by kevinorourke2008 on 2010-02-09
thank you, thank you, thank you and the planet thanks you I won't waste as much paper now.
Great tip.

Cheers kev

---

### Post by AlexanderDGreat on 2010-03-17
Great work my friend, thank you so much for posting this! Searched it from Google.

However I have a problem, I'm using Jaunty. I've created a simple report from my php+mysql website. Now I want to print it so from FireFox, I go to File -> Print -> Print Preview -> then all your hidden buttons show up, thanks! Then I adjust my Paper Type: Letter, Legal or A4, no problems.

But when I adjust the Margins on these papers, I hit APPLY, boom! The settings are DISRESPECTED! They aren't applied. The Paper Type is working fine, but the Margins are a nightmare!

Do you know any solution to this? I tried this on Windows used Firefox same version, did the Page Setup, Margins = 0 on all sides then it works like a charm, no hassles! :(

Is this Ubuntu's poor Page Setup implementation?

It's very frustrating.

Not only that, so suppose I'm done with Page Setup, I will Print it now, I hit "Print" the go to Options -> Remove the URL, Date/Time, # of Pages, Title, etc... of my webpage, I print ok. But when I print the same document again, I have to REDO all the Print Options, it doesn't get saved.

It's a mess, I've been reading a lot about it, and there aren't as much people talking about this. Pls. help! Thanks for reading. :)

---

### Post by dwitkin on 2010-03-23
Alexander,

Glad it was helpful. Unfortunately, I don't have an answer for you. I've had to resort back to Windows for day-to-day OS needs because of problems w/ Ubuntu.


> **AlexanderDGreat said:**
> Great work my friend, thank you so much for posting this! Searched it from Google.

However I have a problem, I'm using Jaunty. I've created a simple report from my php+mysql website. Now I want to print it so from FireFox, I go to File -> Print -> Print Preview -> then all your hidden buttons show up, thanks! Then I adjust my Paper Type: Letter, Legal or A4, no problems.

But when I adjust the Margins on these papers, I hit APPLY, boom! The settings are DISRESPECTED! They aren't applied. The Paper Type is working fine, but the Margins are a nightmare!

Do you know any solution to this? I tried this on Windows used Firefox same version, did the Page Setup, Margins = 0 on all sides then it works like a charm, no hassles! :(

Is this Ubuntu's poor Page Setup implementation?

It's very frustrating.

Not only that, so suppose I'm done with Page Setup, I will Print it now, I hit "Print" the go to Options -> Remove the URL, Date/Time, # of Pages, Title, etc... of my webpage, I print ok. But when I print the same document again, I have to REDO all the Print Options, it doesn't get saved.

It's a mess, I've been reading a lot about it, and there aren't as much people talking about this. Pls. help! Thanks for reading. :)

---

### Post by AlexanderDGreat on 2010-03-24
I see. Thanks for that info, that's 1 point for switching to Fedora soon, OpenSUSE is also calling me to leave old Ubuntuproblematic.

---

