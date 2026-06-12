---
title: "HOWTO: Change processor speed on the fly!"
date: 2007-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Mazza558 on 2007-05-12
If you ever have the problem of stuttering music, it might be because Ubuntu keeps switching the speed of your processor every few seconds. Here's how to be able to choose your processor speed on the fly:

1.) Right-click on your top or bottom bar, or wherever you want the applet to be.

2.) Click "add to panel" and find the "CPU Frequency Scaling Monitor". drag this onto your bar.

3.) Open up a terminal and copy and paste this into it:

```
sudo dpkg-reconfigure gnome-applets
```

4.) Press "OK", and then for the question, choose "yes".

5.) Press enter again and you'll be back at the terminal window.

6.) Left-click on your monitor and you should be able to choose the speed of your processor!

Enjoy :)

P.S - To remove the applet, simply right-click on it and click "remove from panel".

---

### Post by lroy12 on 2007-05-16
This worked nicely. I can also use it to help speed up my games in wine by making usre my processor is at full speed :)

---

### Post by Mazza558 on 2007-05-28
Yup, it's nice to get that kick out of your processor. I think it works best to stop stuttering music, most commonly found when the processor keep speeding up / slowing down.

---

### Post by WinterWeaver on 2007-05-28
Hmm... i might try this with my install. My movies are stuttering for some reason. It's not stuttering on my E17 desktop, neither did it in Edgy. But since Feisty it's been doing this.

However, this looks promising, so I'll give it a go once I get back home.

Thanks for the post ^_^

WW

---

### Post by Znupi on 2007-05-28
**CPU frequency scaling unsupported**
I get this error. My CPU(s): Intel Pentium DualCore 2.80Ghz.
The icon says it's always at 100%. Any way to fix this? It's strange because screenlets are able to read CPU usage.

---

### Post by Mazza558 on 2007-05-28
> **Znupi said:**
> **CPU frequency scaling unsupported**
I get this error. My CPU(s): Intel Pentium DualCore 2.80Ghz.
The icon says it's always at 100%. Any way to fix this? It's strange because screenlets are able to read CPU usage.

This could mean that it only works for AMD processors. Can anyone else without AMD test this out?

---

### Post by WinterWeaver on 2007-05-29
The monitor works nicely and all... but alas, my video is still stuttering. I'll keep digging :(

---

### Post by matijn on 2007-05-29
*wrong topic*

---

### Post by gorilla_king on 2007-05-29
> **Znupi said:**
> **CPU frequency scaling unsupported**
I get this error. My CPU(s): Intel Pentium DualCore 2.80Ghz.
The icon says it's always at 100%. Any way to fix this? It's strange because screenlets are able to read CPU usage.
 i have the same processor and get the same error

---

### Post by Colbrac on 2007-05-29
It might be that you don't have the drivers for changing the frequency loaded in your kernel. For a guide to enable frequency scaling, look at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features")

---

### Post by Mazza558 on 2007-10-13
A nasty surprise for me, I just found out that you can't do this in Xfce :(

---

### Post by ronnieray on 2010-06-14
I have been trying to get wow to work on ubuntu 10.04 now for over a week. Thought I follow all the directions in the posts this game still refuses to launch though it is installed. When I look into forums for help most people take it for granted that everyone that has a question knows what they are doing and the answers they give start in the middle of the actual steps needed to answer a question. On this page there isn't an answer for a neewbie like me. I don't have a clue what you are trying to tell me to do. It is as though you are speaking a different language and you actually expect me to understand. I believe the posts are correct because of the high praise they receive but they have no value for someone just leaving windows who knows nothing of what you are talking about. I have been tring to locate help to get this game going and none of the posts I follow work. Soon I will return to windows I suppose though I like the idea of linux. It is not easy to grasp this linux language and I think that perhaps many have forgot what it was like being a noob.

---

### Post by Fieldeffect on 2011-04-28
ronnieray, your expectations are not in alignment with your answer. There are many ways to start learning about linux. One way I know doesn't work is complaining to people. 

Maybe this topic is a little too in depth for you to start with, try something else like modifying the theme, and go from there. If you search google for whatever release of ubuntu you have with the question after, you will probably find something useful.

GOOD LUCK, may the linux be with you.

---

