---
title: "Need modifid gedit for sending R script to R"
date: 2008-01-15
forum: Packaging and Compiling Programs
---

### Post by smurfs on 2008-01-15
Hi All
I am a ubuntu beginner, I use R([www.r-project.org](www.r-project.org)) ,the statistical software of open resource. 
since I know, there is not a good R script editor for R, but the default editor, gedit, which do support R script. the only thing is I need modified a shortcut key of gedit, which can send R script to R 

is there anybody could help me out?

thanks in advance...

---

### Post by knattlhuber on 2008-07-04
1. Go to Edit > Preferences > Plugins
2. Check off 'External Tools', select it and click on 'Configure plugin'
3. In the 'External Tools Manager' window, click on 'New' and assign a name and description to the shortcut.
4. Click in 'Shortcut Key' field and press the desired key combination for your short cut.
5. Type ```
R --vanilla --quiet
``` in the 'Command' field.
6. Select 'Current selection' under 'Input' and close the window.

Your selected keyboard shortcut will now send the current selection to R. If nothing is selected the whole file is sent.
For other options with the "R" command, please type

```
man R
```

in a Terminal window.

---

### Post by asdir on 2008-11-27
Is there any way to let gedit send commands to an already open R-console, so that the output is not in gedit but in the R-console/terminal?

---

### Post by Nikos.Alexandris on 2008-12-05
> **asdir said:**
> Is there any way to let gedit send commands to an already open R-console, so that the output is not in gedit but in the R-console/terminal?

I am also interested in this. Any R-linux expert?

---

### Post by samden on 2008-12-09
I´d like to know that too. Being able to send a one-off command to R isn´t much use, I generally want to send a series of commands to the same R console.

---

### Post by ahmatti on 2009-07-16
I just found this thread trying to find out how to do exact same thing... Unfortunately no answer here,but I'm going to look at the source code of ESS and Rkward to see how those programs accomplish this. I'll post it here if I manage to find it out...

---

### Post by danded on 2009-09-08
Hi,

I just finished a plug-in for gedit which interacts with R in this way. It basically embeds up to 3 R consoles in the bottom pane and allows you to send the current line, the selection the whole text or predefined blocks to the current R console. 

It's on sourceforge: [http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)

I hope this is what you were looking for :)....

---

### Post by knattlhuber on 2009-09-08
> **danded said:**
> Hi,
I just finished a plug-in for gedit which interacts with R in this way.


Thank you Dan! Looks great! Very useful plugin. I'm sure a lot of people will appreciate it.

---

### Post by Nikos.Alexandris on 2009-09-08
> **danded said:**
> Hi,

I just finished a plug-in for gedit which interacts with R in this way. It basically embeds up to 3 R consoles in the bottom pane and allows you to send the current line, the selection the whole text or predefined blocks to the current R console. 

It's on sourceforge: [http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)

I hope this is what you were looking for :)....

Looks very nice! I'll test it :-)

---

### Post by nico80 on 2009-11-01
Cool thanks! I was also looking for that!

And for those who use Emacs there's the ESS (Emacs speaks statistics) plugin [http://ess.r-project.org/](http://ess.r-project.org/) which also supports other languages (S, Stata, SAS etc)

---

### Post by Nikos.Alexandris on 2009-11-08
> **Nikos.Alexandris said:**
> Looks very nice! I'll test it :-)

Excellent! Thank you very much Dan :-)

---

### Post by QuimNuss on 2010-04-13
Impressive, gedit took a shift here...

The graphs are not displayed though, is that the normal (and unavoidable) behaviour? Great anyway!

(hoping somebody is still subscribed to this old post...)

---

### Post by danded on 2010-04-13
> **QuimNuss said:**
> Impressive, gedit took a shift here...

The graphs are not displayed though, is that the normal (and unavoidable) behaviour? Great anyway!

(hoping somebody is still subscribed to this old post...)

Looks like I'm still subscribed :)

Glad you like it! Now, what do you mean exactly by not seeing the graphs? Could you describe what you did and what you did not see? And what system you have as well?

Best,
Dan

---

### Post by Axolotl9250 on 2010-05-25
> **knattlhuber said:**
> 1. Go to Edit > Preferences > Plugins
2. Check off 'External Tools', select it and click on 'Configure plugin'
3. In the 'External Tools Manager' window, click on 'New' and assign a name and description to the shortcut.
4. Click in 'Shortcut Key' field and press the desired key combination for your short cut.
5. Type ```
R --vanilla --quiet
``` in the 'Command' field.
6. Select 'Current selection' under 'Input' and close the window.

Your selected keyboard shortcut will now send the current selection to R. If nothing is selected the whole file is sent.
For other options with the "R" command, please type

```
man R
```in a Terminal window.

I did as you intructed but when I try to send a few commands over to test this with:
```
data1 <-c(5,10,15,20)
data1
``` It doesn't return the values I enter if I do it line by line but if I highlight both lines then it does work. Is this right? I'm guessing that this is because it works differently to having it sent to a current console that remembers each line sent i.e. an ESS buffer?

---

### Post by Axolotl9250 on 2010-05-25
> **danded said:**
> Hi,

I just finished a plug-in for gedit which interacts with R in this way. It basically embeds up to 3 R consoles in the bottom pane and allows you to send the current line, the selection the whole text or predefined blocks to the current R console. 

It's on sourceforge: [http://sourceforge.net/projects/rgedit/](http://sourceforge.net/projects/rgedit/)

I hope this is what you were looking for :)....

Hi danded, is there a way with this to turn the echo off - so I only have the input commands in gedit but also only the output in the R consoles, the way I have it the console repeats my commands and then gives the results, which is fine EMACS and ESS does that to me as well, and the point of a text editor for me is reproducible research so the output window can be as cluttered as it likes as long as I can give people the clean and correct script file afterwards. But I was just wondering if there is a way to have only results in the console window?

It's not so much a problem more a minor query. The plug-in is still fantastic, I'm definitely sharing this with my stats tutor - thanks!

---

### Post by knattlhuber on 2010-05-25
> **Axolotl9250 said:**
> I did as you intructed but when I try to send a few commands over to test this with:
```
data1 <-c(5,10,15,20)
data1
``` It doesn't return the values I enter if I do it line by line but if I highlight both lines then it does work. Is this right? I'm guessing that this is because it works differently to having it sent to a current console that remembers each line sent i.e. an ESS buffer?

Ya, it doesn't work that great for me either.. but with danded's great plugin we don't have to worry about it anymore :)

---

### Post by danded on 2010-05-30
> **Axolotl9250 said:**
> Hi danded, is there a way with this to turn the echo off - so I only have the input commands in gedit but also only the output in the R consoles, the way I have it the console repeats my commands and then gives the results, which is fine EMACS and ESS does that to me as well, and the point of a text editor for me is reproducible research so the output window can be as cluttered as it likes as long as I can give people the clean and correct script file afterwards. But I was just wondering if there is a way to have only results in the console window?

This looks like a nice suggestions but the way rgedit works now is by embedding a true terminal with a true R session, which means that I think this would be pretty hard to do and most probably would involve an ugly hack if at all possible :(

> **Axolotl9250 said:**
> It's not so much a problem more a minor query. 

So, given the above, I will probably have to keep this suggestion for later...

> **Axolotl9250 said:**
> The plug-in is still fantastic, I'm definitely sharing this with my stats tutor - thanks!

I'm glad you like it: good luck using it! :)

---

### Post by danded on 2010-06-08
> **danded said:**
> This looks like a nice suggestions but the way rgedit works now is by embedding a true terminal with a true R session, which means that I think this would be pretty hard to do and most probably would involve an ugly hack if at all possible :(



So, given the above, I will probably have to keep this suggestion for later...



I'm glad you like it: good luck using it! :)

Actually, I just did it :p

I hope this is what you meant but basically I added a new option where you can specify that you want source() not to echo the commands you pipe through it.

I'll upload a bugfix version soon on sourceforge.

Best,
Dan

---

### Post by danded on 2010-06-08
> **Axolotl9250 said:**
> Hi danded, is there a way with this to turn the echo off - so I only have the input commands in gedit but also only the output in the R consoles, the way I have it the console repeats my commands and then gives the results, which is fine EMACS and ESS does that to me as well, and the point of a text editor for me is reproducible research so the output window can be as cluttered as it likes as long as I can give people the clean and correct script file afterwards. But I was just wondering if there is a way to have only results in the console window?

It's not so much a problem more a minor query. The plug-in is still fantastic, I'm definitely sharing this with my stats tutor - thanks!

Hi, 
as I just said above, I uploaded it (v0.7.0.1) and I would be very interested to know if this is what you had in mind.
Dan

---

### Post by vincegata on 2011-09-14
Great plugin!

THX!

---

