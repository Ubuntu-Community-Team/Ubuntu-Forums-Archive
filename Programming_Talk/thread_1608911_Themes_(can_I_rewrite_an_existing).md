---
title: "Themes (can I rewrite an existing?)"
date: 2010-10-29
forum: Programming Talk
---

### Post by nightfoxx on 2010-10-29
:?: I'm new to Linux so please don't insult my ignorance here. 
I want to alter an existing themes "color scheme". Can I copy, rename and existing theme; then remove the original from the folder and then alter the new copy to change the html colors that exist? It sounds like it will work but I am very new at this so I need guidance. I asked a fellow Ubuntu user who thinks it will work but it was someone who's experience is limited to what is necessary for class work. I have deduced that I will have to rename the old folder by adding "old" to the file name and create the copy as the original file name. (I think).
I know this seems rudimentary to some of you but for me it's a whole new game. Thanks so much.

---

### Post by nvteighen on 2010-10-30
> **nightfoxx said:**
> :?: I'm new to Linux so please don't insult my ignorance here. 
I want to alter an existing themes "color scheme". Can I copy, rename and existing theme; then remove the original from the folder and then alter the new copy to change the html colors that exist? It sounds like it will work but I am very new at this so I need guidance. I asked a fellow Ubuntu user who thinks it will work but it was someone who's experience is limited to what is necessary for class work. I have deduced that I will have to rename the old folder by adding "old" to the file name and create the copy as the original file name. (I think).
I know this seems rudimentary to some of you but for me it's a whole new game. Thanks so much.

Hm... I'm not sure I understand your question.

If all you want is to change a theme because you don't like it, you can create a new theme off an older one and change whathever you want at the System->Preferences->Appearance menu in GNOME... Select a theme, click at "customize" and you'll create a theme "based on" the selected one. Rewriting becomes irrelevant because you choose which theme you want... and because system-wide themes are only rewritable with root-privileges, of course.

But, again, I'm not sure that's what you want.

---

### Post by nightfoxx on 2010-10-30
I am fully aware that I can change it through "point and click" method using the current interface. I want to actually alter the "terminal code" document. Basicly, in order to see exactly what the codes change. I would really like to become more familiar with using the terminal and themes seemed like a pretty harmless thing to mess with. If I mess it up it basically means I can't use that one any more or I have to download it again. 
That said, I would like to use the existing page in the theme file that tells my desktop what to show (sorry, I don't know the proper term); copy it and move the original to a new location. Then alter the copy (under the original name) to reflect the changes I want to make. 
It would be easier to do it just by clicking all the options but I want to actually see the changes in the code. The point is to learn something in the process. 
Does that explanation make more sense? If not please let me know where it's getting "muddy" so that I can try to explain further. I really want to know if this will work before I spend my time to do it. Thanks a lot.

---

### Post by JOHNNYG713 on 2010-10-30
Yes you can! copy and past the theme you want to alter to where ever you want to work on it, make your alterations, Open the index file, rename it, rename the theme itself, compress it, install it!, If you want to make any other alterations after installing, the theme can be found in, Home>Click "view" (on taskbar) show hidden files, look for .themes, make your changes log out and back in to see your new work! Good luck!

---

### Post by nightfoxx on 2010-10-30
Thank you. I appriciate the time to took to answer my question. I am really interested in learning how to use the terminal. I have not had issues with Ubuntu as of yet, and hope I don't but it is good to know how to do things in the terminal and I gotta start somewhere, so why not somewhere that won't mess up my whole system. Thanks again.

---

### Post by Vox754 on 2010-10-30
> **nightfoxx said:**
> I am fully aware that I can change it through "point and click" method using the current interface. I want to actually alter the "terminal code" document. Basicly, in order to see exactly what the codes change. I would really like to become more familiar with using the terminal and themes seemed like a pretty harmless thing to mess with. If I mess it up it basically means I can't use that one any more or I have to download it again.
 
Let me correct you. You have a wrong impression of what programming is. What you want to do has absolutely nothing to do with programming or the terminal, it's just editing, or configuring some files.

> 
That said, I would like to use the existing page in the theme file that tells my desktop what to show (sorry, I don't know the proper term); copy it and move the original to a new location. Then alter the copy (under the original name) to reflect the changes I want to make. 
It would be easier to do it just by clicking all the options but I want to actually see the changes in the code. The point is to learn something in the process. 
...
Themes are collections of Extensible Markup Language (XML) files, which are something like HTML webpages. They describe which colors to use, which icons, which sizes, etc. There is no programming involved. Why you mention the terminal is a complete mystery to me. The files are edited with any text editor.

If you want to know about themes, this is not the proper place to learn about it. You should check out the Free Desktop specifications, the GNOME documentation, and you should also download themes, and take a look at their contents. And if you have questions, you should actually ask in another subforum, such as those dealing with graphics and design. Otherwise I'm afraid you'll come back here to ask for help on things that are really not related to programming.

---

### Post by nightfoxx on 2010-11-01
Thank you Vox754 for being so condescending. This is why more people don't ask questions and want to learn more about Linux. I was somewhat intimidated about using a forum to ask questions and specifically made it clear that I was new to this. Thank you for proving how rude some people with more knowledge on the subject can be. I was genuinely interested in changing the codes using the "text editing" boxes. I didn't imply in any way that I was using the correct terminology. If you felt my question was a waste of time and lacked any merit you could have just refrained from commenting back to it. I will not be back to this forum to ask for help for fear that I will just get another reply from someone like you.

---

### Post by JOHNNYG713 on 2010-11-02
I do agree, some of the "Know it alls" are so fast to criticize and speculate on someones intentions! or focus on a noobies short comings! They seem to forget they had to start somewhere too ! A more intelligent way of addressing your request, by someone with apperently so much knowledge would have been to direct you to information via links that would help you learn and assist in the task at hand, Please don't let one poster spoil your experience here on the forum, there are many people here who will and would lend a hand, with out condescension ! Good luck my friend ! :)

---

### Post by johnl on 2010-11-02
> **JOHNNYG713 said:**
> I do agree, some of the "Know it alls" are so fast to criticize and speculate on someones intentions!  or focus on a noobies short comings! 

The original poster had (as far as I can tell) two questions:
1. how can I modify or create a GTK or Metacity theme?
2. how can I learn to use the terminal/shell?

As Vox explained, neither of these questions are particularly programming related, and there are better forums (perhaps Art and Development for the first, General/Beginner's Guide for the second?) In which they could be asked.  His response didn't even seem rude in the slightest to me, he was just correcting some misunderstandings.

> **JOHNNYG713 said:**
> 
They seem to forget they had to start somewhere too !

maybe in the correct forum? :)

> **JOHNNYG713 said:**
> 
A more intelligent way of addressing your request, by someone with apperently so much knowledge would have been to direct you to information via links that would help you learn and assist in the task at hand, Please don't let one poster spoil your experience here on the forum, there are many people here who will and would lend a hand, with out condescension ! Good luck my friend ! :)

Would you get mad if you asked a programming question in the Art and Design forum and someone told you that "hey, that's not art & design related, if you post elsewhere you might get a better, more helpful response?"  

If you aren't sure what you are asking, that's fine -- but getting angry and storming off when someone tries to help you figure out what you need to know is not an appropriate adult response.

---

### Post by iansane on 2010-11-13
What's up nightfoxx? Welcome to Ubuntu forums!

Hey you could have posted in the beginner forum like so many people do with non beginner questions and you would get tons of responses really quick like "why would you wanna do that?" (gotta love those responses). But I can see where you were thinking logically in coming to the programming forum. I've seen posts here before about people incorrectly refering to Linux in general as programming and it is something that happens a lot. When you go from a all GUI OS like Windows to one that uses terminal and many forum replies give you cryptic looking commands to run in a terminal, everything seems like programming if your not a programmer.

One of my best friends (whom you know) would quickly correct me much like vox754 did you, for using the wrong terminology. And I would call him an *** for his lack of tact. But I know he meant well (our mutual friend I mean). And I'm sure vox754 meant well too. Suggesting another forum and even giving the link would have been nice though rather than a long drawn out lecture about your incorectness.  

By the way, you can use the thread tools drop down and mark this thread as solved to keep anyone from feeling a need to comment or reply since you had your answer before vox754's reply. :-) 

Ubuntuforums.org has been the best forum I've ever been a member of and people here can be very helpful so I hope you do come back.

---

