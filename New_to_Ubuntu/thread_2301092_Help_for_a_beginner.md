---
title: "Help for a beginner"
date: 2015-10-30
forum: New to Ubuntu
---

### Post by Dave_Daft on 2015-10-30
Hi all, and I hope you can help this beginner.
I don't (yet) have a question that is giving me problems - I am a beginner and would like to be led by the hand, either following a User Guide type of approach, or by a series of steps/ tasks that will get me started.

So far, I have loaded, explored and exited successfully, but that is all.  Eg I cannot see how to connect to my wifi network, so cannot update or explore any internet bits. Built-in help says fails to find "Gnome " (?) whatever that is!

Grateful for any suggestions
Dave

---

### Post by sandyd on 2015-10-30
Ok, lets begin with getting you some WiFi.

Can you go to the Unity Dash (Ubuntu logo on top-left), and type in the word "Terminal".
Run the following commands
```

lspci
lsusb

```

In the output of one of the commands, it should mention the Wireless Network card model and name.

Please post that here.

Also, can you connect to the internet using a wired connection?

---

### Post by grahammechanical on 2015-10-30
This might help you

[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

It is useful to us if you tell us which one of the Ubuntu family of Linux distributions you are using and which version it is. Ubuntu versions are released every six months in the April and October and are categorised by the month and the year. So, Ubuntu/Lubuntu 14.04 or 15.04 or 15.10. I was about to give some instructions appropriate to Ubuntu and then I noticed that your post was tagged Lubuntu.

It is also useful if you tell us about the computer hardware. The CPU, RAM, video adapter, wireless adapter.

Are you running the Try Lubuntu session? You may need to install a WiFi driver. Even after installation you may need to install a WiFi driver. So, do you see an icon that would represent a network in one of the panels? Perhaps 2 computer monitors linked together? If so, does it have a drop down menu?

Regards.

---

### Post by Dave_Daft on 2015-10-30
> **grahammechanical said:**
> This might help you

[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

It is useful to us if you tell us which one of the Ubuntu family of Linux distributions you are using and which version it is. Ubuntu versions are released every six months in the April and October and are categorised by the month and the year. So, Ubuntu/Lubuntu 14.04 or 15.04 or 15.10. I was about to give some instructions appropriate to Ubuntu and then I noticed that your post was tagged Lubuntu.

It is also useful if you tell us about the computer hardware. The CPU, RAM, video adapter, wireless adapter.

Are you running the Try Lubuntu session? You may need to install a WiFi driver. Even after installation you may need to install a WiFi driver. So, do you see an icon that would represent a network in one of the panels? Perhaps 2 computer monitors linked together? If so, does it have a drop down menu?

Regards.
Brilliant thanks !!
Have just spent hours checking and rechecking codes etc and wracking my brains. Then I read your post.

Its so obvious (now that I know )
- found the icon bottom right corner, and it did have a menu!  Hurrah, and my networks were all listed.  Clicked, gave password and bingo!
Thank you.  The blindingly obvious is a often a total brick wall to a beginner. (Like having to log off and on to make some changes work)

So pleased (you guessed?). Many thanks.

> **Dave_Daft said:**
> Brilliant thanks !!
Have just spent hours checking and rechecking codes etc and wracking my brains. Then I read your post.

Its so obvious (now that I know )
- found the icon bottom right corner, and it did have a menu!  Hurrah, and my networks were all listed.  Clicked, gave password and bingo!
Thank you.  The blindingly obvious is a often a total brick wall to a beginner. (Like having to log off and on to make some changes work)

So pleased (you guessed?). Many thanks.

and now I am reading these on my Lubuntu version of Firefox.  Thanks again.

---

### Post by deadflowr on 2015-10-30
Not having to run a series of terminal commands to get networking up and running always works best.

If you've found the solution given has solved the problem, please mark this thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

