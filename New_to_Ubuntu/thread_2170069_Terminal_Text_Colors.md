---
title: "Terminal Text Colors"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by baker-quin on 2013-08-24
I'm wondering if anyone knows of a way to make the command line input a different color than the output. For instance if I wanted to see the input in bright orange so it's easy to see and track after some command comes in and a bunch of text fill the screen. I cannot see anyway to do what I would like in the profile preferences under the edit menu of terminal.

---

### Post by eternal243 on 2013-08-24
Open terminal, and enter this command.

```
nano ~/.bashrc
```

Then find the following line, and remove the **#**.

```
#force_color_prompt=yes
```

Then save the file and restart terminal. =)

---

### Post by vasa1 on 2013-08-24
I think OP wants more than just the prompt colored differently. I think OP wants the letters that make up stuff like "sudo apt-get install package_name" or "ls -al" to be colored differently than the subsequent output.

I tried to figure out how that could be done but gave up and contented myself with a colored prompt.

---

### Post by jon-zendatta on 2013-08-25
[http://ubuntuforums.org/showthread.php?t=614743](http://ubuntuforums.org/showthread.php?t=614743)

---

### Post by eternal243 on 2013-08-25
> **vasa1 said:**
> I think OP wants more than just the prompt colored differently. I think OP wants the letters that make up stuff like "sudo apt-get install package_name" or "ls -al" to be colored differently than the subsequent output.

I tried to figure out how that could be done but gave up and contented myself with a colored prompt.

Actually the command I posted earlier will give different colors for some other stuff than just the prompt, it will also color folders, files and symlinks differently, for example when you use "ls -al". 

It just activates a built in function in the Ubuntu system, it is commented out by default, but anyone can add it if they want it. Of course, if you want other colors or more things colored you could write your own function for that. Just google "colored bash prompt" and you will find some hints, I know both the arch-linux and gentoo wikis has lots of information on this topic. :)

---

### Post by vasa1 on 2013-08-25
> **eternal243 said:**
> Actually the command I posted earlier will give different colors for some other stuff than just the prompt, it will also color folders, files and symlinks differently, for example when you use "ls -al". ...
That is clear but I'm still feeling that OP wants to see that the command that is typed is colored differently. What you are referring to is the output of the command.
Anyway, OP is not clarifying so ...

---

### Post by baker-quin on 2013-08-26
Forgive me, I only saw the first comment and applied it and thought it was good enough. At first the prompt text was bright green but when I went to profile preferences I changed the Color Palette a little and got it close enough to what I wished. I also like how this changed the colors of other things too. I now have the prompt in bright orange but the input text is still standard (ie [COLOR=#000000]*sudo apt-get install package_name). When I first posted I was hoping for this to be colored the same as well but now that I have it this way I think I like it more. It has been much easier to navigate my Terminal now. This could possibly be done through here *[/COLOR][http://ubuntuforums.org/showthread.php?t=614743](http://ubuntuforums.org/showthread.php?t=614743) as Jon suggested but I am pleased with eternals fix.

---

### Post by eternal243 on 2013-08-26
> **baker-quin said:**
> Forgive me, I only saw the first comment and applied it and thought it was good enough. At first the prompt text was bright green but when I went to profile preferences I changed the Color Palette a little and got it close enough to what I wished. I also like how this changed the colors of other things too. I now have the prompt in bright orange but the input text is still standard (ie [COLOR=#000000]*sudo apt-get install package_name). When I first posted I was hoping for this to be colored the same as well but now that I have it this way I think I like it more. It has been much easier to navigate my Terminal now. This could possibly be done through here *[/COLOR][http://ubuntuforums.org/showthread.php?t=614743](http://ubuntuforums.org/showthread.php?t=614743) as Jon suggested but I am pleased with eternals fix.

Thats great then, I'm glad I could help! :)

---

